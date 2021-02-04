[본문 Week29](https://jiho-ml.com/weekly-nlp-29/)

![](https://jiho-ml.com/content/images/2020/09/figure5.png)

# GPT는 또 하나의 언어 모델(Language Model)이다
![](https://jiho-ml.com/content/images/2020/09/figure1.jpg)
- LM은 여태까지 나온 단어들을 토대로 다음 단어를 예측하는 것
  - 수 많은 텍스트 데이터를 통해 통계학적인 모델을 학습시키는 방식
- 전체 문장을 다 보고 중간에 들어가는 단어를 예측하는 BERT와 달리, GPT는 기존의 언어 모델과 같이 다음 단어를 예측해야 하기 때문에 Transfer Decoder를 사용함

# 잘 학습된 LM은 그럴듯한 글을 생성할 수 있다
![](https://jiho-ml.com/content/images/2020/09/figure4.png)
GPT2를 이용해 글을 생성 (SKT에서 공개)

# GPT1,2,3의 차이는?
[GPT1](https://openai.com/blog/language-unsupervised/)
[GPT2](https://openai.com/blog/better-language-models/)
[GPT3](https://arxiv.org/abs/2005.14165)

- 기본적인 모델 구조나 학습 원리는 모두 같음
- 차이는 트랜스포머의 사이즈 + 학습 데이터의 양
  - GPT2 : 1.5B parameters
  - GPT3 : 175B parameters
