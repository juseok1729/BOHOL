# mAP(mean Average Precision) 이란?
Object detection 에서는 모델의 성능(정확도)을 주로 mean Average Precision(mAP)를 통해 확인한다.  
**∴mAP가 놓을수록 정확하고, 작을수록 부정확하다.**

## **Precision (정밀도)**
- 모든 검출 결과 중 옳게 검출한 비율
- Precision은 모델의 출력이 얼마나 정확한지를 측정하는 것
- 즉, 모델이 예측한 결과의 Positive 결과가 얼마나 정확한지를 나타내는 값

## **Recall (재현율)**
- 검출해내야하는 물체들 중에서 제대로 검출된 것의 비율
- Recall은 모델의 출력이 얼마나 Positive 값들을 잘 찾는지를 측정하는 것
#
## **Threshold(하이퍼파라미터)**
detector는 수많은 후보 경계박스를 제안하는데  
이중, 가장 좋은 후보들을 2번에 걸쳐 선별한다.  

**1차 : 기준 이상의 confidence 값을 갖는 후보를 선별한다. (score threshold)**  
**2차 : NMS를 통해 중복되는 confidence가 낮은 후보들을 제거한다. (iou threshold)**  

이 과정에서 사용되는 기준(Threshold) 하이퍼파라미터를 결정해야 하는데,  

- 1차 Confidence Threshold (기준 신뢰도, objectness) = **score threshold**  
- 2차 IOU(Intersection Over Union) Threshold = **iou threshold**  

보통, Confidence Threshold 값은 0.5로 해서 그 이하의 경계박스후보는 배경으로 간주해서 제거한다.  
IOU Threshold는 Yolo의 경우 0.45인데    

Confidence Threshold(= score threshold) 가 변하면 Recall 과 Precision 이 크게 변한다.  
score threshold = 0.1 인 경우, 영상 전체에서 후보 박스가 가득 나타나게 된다.  
score threshold = 0.99 인 경우, 오브젝트가 있는게 확실한 후보만 남는다.  
#
## 결과
**score threshold 가 크면 총 후보의 수가 줄어들고 확실한 후보만 남는다.**  
후보의 수가 줄어들었으므로 성능면에서 Recall은 낮아지며, 확실한 후보들은 정답일 확률이 높으므로 Precision 이 높아진다.  

**score threshold 가 낮으면 총 후보 경계박스들이 많이 남는다.**  
성능면에서 후보가 많으므로 Recall 은 높아지며, 확실하지 않은 후보가 많기 때문에 Precision 은 낮다.  

**∴ score threshold 는 Recall 에 반비례하며 Precision 에 비례한다.**  
