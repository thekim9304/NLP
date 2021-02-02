[본문 Week19](https://jiho-ml.com/weekly-nlp-19/)

# Neural LM을 평가하는 방법
- LM은 perplexity(당혹감)이라는 evaluation metric을 학습에 쓰이지 않은 데이터(hel-out test data)에 계산하여 평가함
  - perplexity는 2^entropy로 계산하고 낮은게 더 좋은 metric
    - 다음 단어를 예측할 때 불확실성이 크다면 entropy가 높아짐

# Text Generation
-
