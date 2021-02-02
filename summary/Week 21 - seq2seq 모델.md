[본문 Week21](https://jiho-ml.com/weekly-nlp-21/)

- NMT(neural machine transplation)의 기본에 대해 공부

# 1) 번역과 language modelling의 관계, conditional language modelling
- 번역이란 한 언어 (source language; x)에서 다른 언어 (target language; y)로 변환되는 과정
  - x가 주어졌을 때 y의 확률 (조건부 확률(conditional probability), 앞 단어 몇 개가 주어졌을 때, 다음 단어가 나올 단어는?)
  - conditional LM을 학습하려면 parallel corpus가 필요함

# 2) 번역을 noisy channel model로 본다면?, encoder-decoder model.
- 음성 메시지에 포함된 소음들을 걷어내고 메시지의 내용을 알아내야함 (noisy channel model)
- noisy channel model을 encoder-decoder 모델이라고 부르기도함
  - 암호화되는 부분과 해석하는 부분이 나뉘어 있기 때문
  ![](https://jiho-ml.com/content/images/2020/04/figure2.png)

# 문장에서 문장으로 seq2seq 모델
1. conditional language modelling +
2. encoder-decoder model +
3. RNN을 이용한 neural LM
= seq2seq 모델
  ![](https://jiho-ml.com/content/images/2020/04/figure3-1.png)
    - seq2seq 모델 구조
    - Encoder RNN + Decoder RNN
    - Decoder RNN에서 Encoder RNN의 마지막 hidden state를 계속 참고함
