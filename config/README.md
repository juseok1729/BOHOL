# configure (.cfg) file

## Settings

- **batch**  
  - 기본값 64 , 건드리지 않는다.
  
- **subdivisions**  
  - 배치 사이즈를 얼마나 쪼개서 학습할지 설정한다.  
  - 메모리 누수가 나면 16 32 등으로 조절한다.
  
- **witdh, height**  
  - 기본값 416 , 608로 변경하면 정확도가 좋아질 수 있다. (32배수로 조절한다.)
  
- **learning_rate**  
  - 기본값 0.001 , multi gpu인 경우 0.001/gpu갯수로 설정한다.  
  - 예를들어 gpu×2 , learning_rate = 0.0005  
  
- **burn_in**  
  - 기본값 1000 , multi gpu인 경우 1000 × gpu갯수로 설정한다.  
  - 예를들어 gpu×2 , burn_in = 2000  
  
- **max_batches**  
  - iteration 갯수 , class수 × 2000 + 200  
  - 예를들어 class = 16 , max_batches = 32,200  
  
- **steps**  
  - max_batches의 80%, 90%로 , class갯수 × 2000의 80%, 90%를 설정한다.  
  - 예를들어 class = 16 , steps = 25600,28800
  
- **classes**  
  - 클래수 수
  
- **filters**  
  - (클래스 수 + 5) × 3
  - 예를들어 class = 16 , filters = 63  
  - **yolo레이어 바로 위에 있는 필터만 수정한다.**
