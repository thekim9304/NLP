[본문 Week10](https://jiho-ml.com/weekly-nlp-10/)

만약 cnn에 한 문단을 넣는다면?
어떤 문장은 30개의 단어로 이루어져 있고, 어떤 문장은 2개의 단어만으로 이루어져 있다면?
- NLP에서 CNN은 input의 길이가 너무 길거나 input들의 길이가 다양하다면 효율적으로 처리하기 어렵다는 단점을 갖고있다.
##

- 그래서 문장의 단어들을 사람이 읽듯이 순차적으로 처리하는 방법으로 **RNN(Recurrent Neural Network)**이 있다.

## RNN, Time series modelling의 강자
- RNN은 NLP 이외의 time series modelling에 굉장히 많이 쓰이는 모델
  - time series data : 각 시간마다 바뀌는 값이 있는 데이터
- input 간의 상관간계를 고려하는 network
![](https://jiho-ml.com/content/images/2019/11/Recurrent_neural_network_unfold.svg)
  - input 여러 개(x)가 순차적으로 입력
  - output(o)이 하나씩 생성
    - 이 output이 각 시간(timestep)의 예측 값을 의미
  - 기억을 저장하는(internal hidden state)
    - 각 timestep마다 hidden state가 연속적으로 이어짐

## 문장을 time series로 본다면?
![](https://jiho-ml.com/content/images/2020/06/figure1-3.png)
- 각 단어들(['I', 'love', 'you'])은 각자 vector로 변환(word embedding)되어 rnn에 순차적으로 입력
- 목적에 따라서 vector 하나가 들어갈 때마다 output이 나올 수 있고, 마지막에 하나의 결과물이 나올 수도 있음

## RNN의 종류
- original rnn을 Simple RNN이라 부름
- 이 초기 버전의 단점을 해결하기위한 모델들
  - vanishing gradient

#### LSTM (Long Short Term Memory)
- 현재 RNN 모델을 사용한다고 하면 거의 대부분 LSTM을 뜻한다함
- 모델 안에 여러 개의 gate를 추가하여 input, output 그리고 memory간 흐르는 정보를 좀 더 섬세하게 제어함
- input gate, output gate, forget gate, update gate를 통해 어떤 정보를 받아들이고, 내보내고, 잊어버리고, 저장할지를 학습하는 수학 모델
