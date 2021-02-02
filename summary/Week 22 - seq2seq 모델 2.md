[본문 Week22](https://jiho-ml.com/weekly-nlp-22/)

- seq2seq 모델의 학습 방법
- seq2seq 모델의 문장 생성 방법
- seq2seq 모델 평가 방법

# 모델 구성
## Encoder RNN: input 문장 읽고 이해하기
- 모든 단어를 순차적으로 동일한 RNN에 입력
- 모든 단어를 다 입력하고나면 최종 hidden state가 남음
  - 이는 word embedding 처럼 Nx1 vector로 표현됨
  - 번역해야 할 문장에 대한 모든 정보가 들어있기 때문에, 문장 임베딩(sentence embedding)이라고 표현
  ![](https://jiho-ml.com/content/images/2020/04/figure2-1.png)

## Decoder RNN: 한 단어씩 출력하기
- RNN은 다음 단어를 예측하는 확률을 예측하고 단어를 하나씩 생성할 수 있는 능력이 있음
  - 여기서 모든 단어(vocabulary)에 대한 확률을 생성하는 함수는 softmax function

- RNN LM과 다른 두 가지
#### 1) input sentence embedding도 같이 input으로 넣는다.
- conditional language model 개념을 실제로 구현한 것
#### 2) 랜덤으로 샘플링 하지 않고 확률이 높은 단어를 고른다.
- 가능한 모든 단어 중에 가장 높은 확률 점수를 받은 단어를 고름

# 학습
- 기존 방법과 마찬가지로 softmax layer가 생성하는 확률 점수와 현재 생성되야하는 단어(정답)를 갖고 cross-entropy loss를 계산함
  ![](https://jiho-ml.com/content/images/2020/04/figure4.png)
- Back-Propagation 방식으로 학습

### 첫 단어를 고르는 방법 (Top-K Beam Search)
- 확률이 가장 높은 단어 한 개만 고르는게 아닌 K 개까지 고르는 것 (K는 hyperparameter)
- K가 높을수록 연산량 증가

# 평가
- BLEU score
  - 얼마나 정답과 단어간의 공통 단어가 많은지로 계산함
