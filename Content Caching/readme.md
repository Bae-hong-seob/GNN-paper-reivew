# 연구 Log

## 6/27

### 업데이트
~~1. x,y position 기반 labeling 완료~~  
~~2. 이에 따른 labeling(mecs)당 Request된 movieId matrix 생성.~~  
~~3. 결국 하나의 hitmap 제작완료.~~  
### 추가해야할 점
~~1. 다음 step 진행 시 x,y position 변화 -> labeling 변환~~  
~~2. hitmap 변화.~~  
~~3. hitmap을 이미지 형태로 폴더 내에 저장하는 코드 생성.~~


## 6/28

### 문제점
1. hitmap 생성 시 row는 mecs, column은 movieId.
- 이때 matrix 형태가 너무 이상하지 않나 ? 그리고 모든 movieId에 대한 정보를 가지기도 힘들고 매번 movieId가 가변적이라면 이미지를 학습하는데 의미가 없음
