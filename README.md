# Project-DisneyReviews
2021 Spring - Project(Disney Reviews) in Data Processing Language Class - SeoulTech, Department of Data Science

## 디즈니랜드 리뷰에 대한 EDA 및 감성분석
- Kaggle: https://www.kaggle.com/arushchillar/disneyland-reviews/tasks?taskId=3225

### dataset 설명
- 파리, 캘리포니아, 홍콩 디즈니랜드 이용객들이 Trip Advisor를 통해 남긴 약 42,000개의 리뷰 데이터
- column 설명
  - Review_ID
  - Rating: 방문객이 입력한 전반적인 평점 (불만족이면 1, 만족이면 5)
  - Year_Month: 방문 시기 (년도-월)
  - Reviewer_Location: 방문객의 국적
  - Review_Text: 리뷰 텍스트 내용
  - Disneyland_Branch: 디즈니랜드 지점 (파리, 캘리포니아, 홍콩)

### 분석 과정
1. 데이터 전처리
  - 중복, 의미없는 컬럼 제거
  - 날짜 데이터 분리 (년도, 월)
  - review text 전처리
    - Lower
    - Tokenize
    - Stemming
    - Stop word 제거
2. EDA & Visualization
  - 평점 별 비교
    - 전체 평점 분포 시각화
    - 평점 별 리뷰 wordcloud 
  - 지점 별 비교
    - 지점 별 평점 분포 시각화
    - 지점 별 리뷰 wordcloud
  - 방문객 국가 별 평점 평균 시각화
  - 지점 별 방문객 국가 top5 시각화
  - 방문 시기 별 비교
    - 년도별 시각화
    - 월별 시각화
3.  감성 분석
  - 4-5점: 긍정, 3점: 중립, 1-2점: 부정 으로 분류
  - wordcloud 로 단어 시각화
  - 새로운 감성 점수 부여 ⇒ 감성 예측
    - Vader, Affinn 감성 분류기 사용
    - 전체 리뷰 8:2로 train, test set 분류
    - multi-class classifier로 Decision Tree Classifier, Random Forest Classifier 사용 (max_depth =100)
      ⇒ Vader 감성분류기를 사용한 극성 판단이 감성 예측에 있어 더 높은 정확도를 보임

### 요약 및 한계점
- EDA & Visualization
  - 방문객이 부여한 평점별, 방문 지점별, 방문객 국적별, 방문 시기별로 나누어 진행
  - 분석 결과를 시각화
  - 한계) 결과를 통해 알 수 있는 유의미한 차이가 별로 없었고 이를 위해 추가적인 비교가 필요 
- 감성 분류기 구축
  - 긍정, 부정, 중립 리뷰를 분류하고 이를 시각화
  - 기존 텍스트 마이닝에 많이 쓰이는 감성 사전 라이브러리를 활용하여 새로운 극성점수 부여
  - 평점을 통한 극성과 감성사전을 통한 극성의 차이를 보기 위해 classification 성능 비교 → 감성사전을 통한 극성 분류가 더 정확함을 확인
  - 한계) 하나의 리뷰에는 여러가지 속성이 결합되어 있기 때문에 이를 나누어 분석, 각 속성에 맞는 감성사전을 따로 구축한다면 더 좋은 감성 분류기를 구축할 수 있음
