[본문 Week8](https://jiho-ml.com/weekly-nlp-8/)

- 스팸을 걸러낼 수 있는 감지 모델 (spam detection)
- 기본적인 통계 모델인 Naive Bayes Classifier를 사용

## binary classification을 사용하려면?
- 스팸이냐?(true, 1), 아니냐?(false, 0)
- 당연히 data와 label이 필요하다
#### 데이터 구축 방법
1. labeling : supervised
  - 노가다
2. anomaly detection(변칙 검출) : unsupervised
  - 데이터 전체를 보았을 때 다른 데이터 포인트들과 아주 동떨어진 데이터를 찾는것

## Multinomial Naive Bayes classifier
#### 베이즈 정리
  - probability(사전 확률)와 posterior probability(사후 확률)의 관계를 나타내는 정리
    [베이즈 정리 참고](https://junpyopark.github.io/bayes/)
  ![](https://jiho-ml.com/content/images/2020/04/eq1-1.png)
  - 어떤 이메일(d)이 주어졌을 때, 이 이메일이 스팸인지 아닌지 (c=0?, c=1?) 각각 확률 계산
  - 둘 중 더 큰 확률을 갖는 쪽이 c(hat)에 입력
  ![](https://jiho-ml.com/content/images/2020/04/eq2.png)
  ![](https://jiho-ml.com/content/images/2020/04/eq3.png)
  ![](https://jiho-ml.com/content/images/2020/04/eq4.png)
    - P(c) : prior probability(사전 확률)
      - classifier가 선택할 수 있는 class의 확률
      - 즉, 주어진 학습 데이터내에서 해당 class의 비율
    - P(d|c) : likelihood(가능도)
      - 어떤 이메일(d)이 스팸 class에서 등장할 가능성을 계산한 숫자
      - c = 스팸이라고 주어졌을 때, 이 이메일이 작성될 확률
      - 이미 스팸이라는 가정을 하고 이메일이 쓰여졌다면 얼마나 그럴듯 하냐
        - 이메일에 들어가있는 단어 하나하나를 살펴보는 것
        - 아마 스팸이라 판단될 단어가 1도 없다면 확률은 0이겠지
      - 학습 데이터 중 스팸 이메일들에 들어있는 단어들에 대한 통계를 확률로 계산
        - Ex, "보험"이라는 단어가 100개 중에 90개는 스팸 이메일에, 10개는 보통 이메일에 있다고 하면 P("보험"|spam) = 90/100 = 0.9, P("보험"|not_spam) = 10/100 = 0.1 로 계산됨
#### naive하게 단어들의 joint probability(결합 확률) 계산 (순서 무시)
  ![](https://jiho-ml.com/content/images/2020/08/ep6.png)
    - w1, w2, w3, ..., wn은 문서내의 단어들을 의미함
  - 원래 joint probability를 계산하려면 단어의 순서가 중요
    - naive bayes classifier에서는 순서를 무시하고 각 단어들이 독립적이라고 가정
      - 하나의 단어가 발생할 확률이 다른 단어의 영향을 받지 않는다는 것
  - naive bayes classifier는 좋은 모델인데 일반화 성능은 zero (예측하려는 이메일의 단어가 학습 데이터에 등장하지 않으면 확률이 0이되기 때문에 무시됨)
  - "보험 판매 오늘 당장" (확률은 예시로)
  ![](https://jiho-ml.com/content/images/2020/06/eq7.png)
  ![](https://jiho-ml.com/content/images/2020/04/eq8.png)
