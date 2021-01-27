[본문 Week6](https://jiho-ml.com/weekly-nlp-6/)

- NLP 분야에서 문서를 주제별로 분류하는 것을 document(text) classification이라고 한다.

## Binary Classification
- Linear Regression(회귀)에 sigmoid 함수 적용 (즉, Logistic regression classifier)
- 이런 logistic regression 모델을 학습하기 위해서는 입력 feature가 n 차원의 vector여야한다. (string이 아닌)
  - Week2에서 공부한 tf-idf, BoW 등으로 string을 vector로 변환

## Feature importance
  - 모델을 학습시켰을 때, 모델이 가장 중요하게 보는 단어들이 어떤 것인지 알아볼 수 있는것
  - 주로 Y 예측 값을 계산할 때 X에서 각 행(각 feature)들에게 주는 가중치(weight)를 계산한 것을 보면 된다.
  ![](https://jiho-ml.com/content/images/2020/05/feature_importance-1.png)
