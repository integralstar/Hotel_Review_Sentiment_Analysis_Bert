# Hotel_Review_Sentiment_Analysis_Bert

### 목적
고객이 호텔 이용 후기를 작성했을 때 감정분석을 이용하여 사용자 만족도를 평가하고 관리한다.

#### 데이터 수집
호텔 평가 리뷰 84123개 수집 (실사용 데이터 : 82860개)

#### 전처리
1. 특수 문자들 제거
2. 자음 모음 단독 사용 문자들 제거
3. 이모티콘 문자들 제거
4. 네이버 맞춤법 검사 시도 (중간에 차단됨 : 8091/84123) - 0.5초 delay줘도 대략 하루가 소요됨;;
5. 다른 사이트에서 맞춤법 검사 시도 중 (delay 사용으로 처리에 3일 이상 예상 됨)
6. 평점이 7.0 이상인 경우 긍정 리뷰로 그 이하인 경우 부정 리뷰로 레이블링
7. EDA를 통한 data parameter 설정

![WordCloud](https://github.com/integralstar/Hotel_Review_Sentiment_Analysis_Bert/blob/main/wordcloud_hotel.png) 

#### BERT를 이용하여 Fine-Tuning
accuracy: 0.9213

#### 중간평가 & 개선사항 정리
1. 3분위 값을 Max length로 설정하였는데 적절한 리뷰를 반영하려면 더 많은 글자를 반영하여 넣어야 할 것 같다. (실용성 개선)
2. 두 카테고리 데이터 비율이 10배 가량 차이남.
3. 데이터 비율 개선을 위해 층화 학습법 테스트 해 보기
4. 맞춤법 검사를 통한 데이터 정제 필요
5. albert를 이용한 모델 개선 및 성능 높이기
6. LIME 같은 XAI 기법 도입하여 테스트 하기
7. 더 많은 Reviwe 데이터들 수집하기
