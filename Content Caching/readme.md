# 연구 Log

## 6/26
### problem
~~1. rating. 즉 평점을 남긴 timestamp 데이터를 가지고 있음. 이를 request timestamp로 봐도 되는가?~~ 가능. 내 입맛에 꼭 맞는 데이터는 없음.  
2. rating 점수에 따라 호불호가 나타나게 되는데 이를 고려해서 추천시스템을 짜야하지 않나? 기준은 어떻게 설정하나.  
- 아이디어 : user 마다 평점의 평균,분산을 구해서 분포를 형성한 다음 z-score를 활용? -> Q1 이하의 rating 점수는 불호의 영역?  
- 추후에 고민.

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

### solution
- 128개의 movieId만 추출. 분포를 고려하여 weight 주기

## 6/29

### 문제점
~~1. 128개의 movieId만 추출 이후 1000명의 userId를 추출할 경우, movieId의 수나 userId의 수가 줄어들 수 있음.~~ 완료  
- ~~따라서 movieId 수를 고정시킴. 128로. 128개의 movieId에 대해 최소 1개씩 userId를 추출한 후 나머지(1000-128)에 대해서 userId samlping 진행~~
- ~~이때 128개의 movieId 중 요청한 user가 한명이고, 겹칠 경우 나머지가 항상(1000-128)이 아닐 수 있음.~~
- 따라서 1000-set(reamin_userIds)를 통해 movieId는 128, userId는 1000이 유지되도록 함.

2. matrix를 만들어서 png로 저장하는데 올바르게 저장되지 않는 것 같음.
- 누적 합을 계산하는 과정에서 버그가 있는 것 같은데 고민해볼 것. gpt코드라서 다시 분석해봐야함.
