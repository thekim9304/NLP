# Week 13 - 언어를 모델링한다? Language Model Basics
[본문 Week13](https://jiho-ml.com/weekly-nlp-13/)

## Language Modeling
- 언어의 likeliness(그럴듯함)을 판단하는 모델

## statistical language modeling (통계학적 언어 모델링)
- LM은 문장을 단어의 연속으로 보는것
  - NLP에서 문장을 이해하고 표현하는 것과 같음

![](https://jiho-ml.com/content/images/2020/07/equation1.png)
  - S(Sentence) : 단어 n개가 들어가 연속으로 들어 았는 리스트
  - w : 문장에 들어있는 단어
  - D : N개의 문장이 포함된 데이터
  - V : 가능한 모든 단어들의 리스트인 vocabulary

- 한 문장의 그럴듯함은 **joint probability (동시 확률분포)**로 계산
  - 4개의 단어가 있다면 4개의 단어가 함께 발생할 확률을 계산하는 것
  - 가지고 있는 데이터를 가지고 계산
![](https://jiho-ml.com/content/images/2020/07/equation2.png)
- 데이터에 있는 단어들을 하나하나 다 세봐서 확률 계산
  - 총 빈도수 / 전체 데이터 수
- 전체 문장을 한 번에 봄
- 아예 새로운 문장은 확률이 무조건 0이됨

# Week 14 - N-gram language model
[본문 Week14](https://jiho-ml.com/weekly-nlp-14/)

## unigram LM
- 문장에 있는 단어를 개별적으로 생각
![](https://jiho-ml.com/content/images/2020/02/equation3.png)
  - unigram model
  - 각 단어별 빈도수 / 전체 단어 수
- 단어의 순서를 고려하지 않음

## bigram LM
![](https://jiho-ml.com/content/images/2020/02/equation4.png)
  - bigram
  - Conditional probability P(w2|w1) : w1이 주어졌을 때 w2가 올 확률
    - w1 다음에 w2가 올 확률 (P("name"|"My") = "My" 다음에 "name"일 확률)

## n-gram LM
- 한 번에 n개의 연속된 단어를 묶어서 생각
- n=3이면 P(w3|w2, w1)을 계산하는 식
###

- n이 늘어날수록 계산해야 하는 항목도 늘어나기 때문에 보통 1-gram, 2-gram, 3-gram을 섞어서 통계 모델을 만듦

# Week 15 - Automatic Speech Recognition, ASR
- LM(Language Model)의 가장 성공적인 적용 사례
![](https://jiho-ml.com/content/images/2020/02/figure2.png)

## Noisy Channel Model이란?
- 음성 신호를 최대한 원본과 가깝게 decoding하는 모델
- ASR 기술은 이 noisy channel model을 이용해 음성(sound signal)을 텍스트로 변환하는 모델을 만드는 것임

## Bayes theorem
- ASR 모델은 bayes theorem을 통해 두 가지 모델로 분리되어 이루어져 있음
  - 하나는 소리 모델(acoustic model), 언어 모델(language model)
###

![](https://jiho-ml.com/content/images/2020/02/eq1.png)
  - P(W|X) : 소리 X가 주어졌을 때, 텍스트 W는 무엇인지
  - P(X)와 W는 상관이 없기 때문에 argmax에서 버려져도 상관 없음
![](https://jiho-ml.com/content/images/2020/02/eq2.png)
  - 가장 확률이 높은 W를 고르는 것 (argmax)
  - P(X|W) : 텍스트 W가 주어졌을 때, 소리 X는 무엇인지
  - P(W) : 텍스트 W의 확률
    - 즉, 문장의 그럴듯함을 의미하는 LM
