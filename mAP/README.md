# mAP(mean Average Precision) 이란?
Object detection 에서는 모델의 성능(정확도)을 주로 [mean Average Precision(mAP)](https://github.com/Cartucho/mAP)를 통해 확인한다.  
**∴mAP가 놓을수록 정확하고, 작을수록 부정확하다.**

## **Precision (정밀도)**
- 모든 검출 결과 중 옳게 검출한 비율
- Precision은 모델의 출력이 얼마나 정확한지를 측정하는 것
- 즉, 모델이 예측한 결과의 Positive 결과가 얼마나 정확한지를 나타내는 값

## **Recall (재현율)**
- 검출해내야하는 물체들 중에서 제대로 검출된 것의 비율
- Recall은 모델의 출력이 얼마나 Positive 값들을 잘 찾는지를 측정하는 것
#
## **Precision과 Recall의 수학적 정의**
<table class="tg">
  <thead>
    <tr>
      <th class="tg-c3ow" rowspan="2">실측 정보<br>(ground truth)</th>
      <th class="tg-c3ow" colspan="4">예측 결과 (predict result)</th>
    </tr>
    <tr>
      <center>
        <th class="tg-c3ow" colspan="2">Positive</td>
        <th class="tg-c3ow" colspan="2">Negative</td>
      </center>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th class="tg-c3ow">Positive</td>
      <th class="tg-c3ow" colspan="2">TP<br><span style="font-weight:bold">옳은 검출</span></td>
      <th class="tg-c3ow" colspan="2">FN<br><span style="font-weight:bold">검출되야 할 것이</span><br><span style="font-weight:bold">검출되지않음</span></td>
    </tr>
    <tr>
      <th class="tg-c3ow">Negative</td>
      <th class="tg-c3ow" colspan="2">FP<br><span style="font-weight:bold">틀린 검출</span></td>
      <th class="tg-c3ow" colspan="2">TN<br><span style="font-weight:bold">검출되지 말아야 할 것이</span><br><span style="font-weight:bold">검출되지 않음</span></td>
    </tr>
  </tbody>
</table>

- 암 진단의 경우, Precision과 Recall은 다음과 같이 정의 된다.
  ```
  TP : 실제 암 세포들의 개수
  TP + FP : 암세포라고 판단 된 결과
  TP + FN : 전체 암 세포들의 개수
  ```
  - Precision = TP / (TP + FP)  
  - Recall = TP / (TP + FN)
    
- Object detection의 관점에서 보면, Precision과 Recall은 다음과 같이 정의 된다.
  - Precision = True detections / whole detections of an algorithm
  - Recall = detected TRUE / total number of existing TRUE

#
## **Threshold(하이퍼파라미터)**
detector는 수많은 후보 경계박스를 제안하는데  
이중, 가장 좋은 후보들을 2번에 걸쳐 선별한다.  

**1차 : 기준 이상의 confidence 값을 갖는 후보를 선별한다. (score threshold)**  
**2차 : NMS를 통해 중복되는 confidence가 낮은 후보들을 제거한다. (iou threshold)**  

이 과정에서 사용되는 기준(Threshold) 하이퍼파라미터를 결정해야 하는데,  

1. Confidence Threshold (기준 신뢰도, objectness) = **score threshold**  
2. IOU(Intersection Over Union) Threshold = **iou threshold**  

보통, Confidence Threshold 값은 0.5로 해서 그 이하의 경계박스후보는 배경으로 간주해서 제거한다.     

Confidence Threshold(= score threshold) 가 변하면 Recall 과 Precision 이 크게 변한다.  
score threshold = 0.1 인 경우, 영상 전체에서 후보 박스가 가득 나타나게 된다.  
score threshold = 0.99 인 경우, 오브젝트가 있는게 확실한 후보만 남는다.  
#
## 결과
#### 1. score threshold 가 크면 총 후보의 수가 줄어들고 확실한 후보만 남는다.  
후보의 수가 줄어들었으므로 성능면에서 Recall은 낮아지며,  
확실한 후보들은 정답일 확률이 높으므로 Precision 이 높아진다.    

#### 2. score threshold 가 낮으면 총 후보 경계박스들이 많이 남는다.  
성능면에서 후보가 많으므로 Recall 은 높아지며,  
확실하지 않은 후보가 많기 때문에 Precision 은 낮다.  

**∴ score threshold 는 Recall 에 반비례하며 Precision 에 비례한다.**  
