[본문 Week16](https://jiho-ml.com/weekly-nlp-16/)

- acoustic model (AM)
  - 주어진 음성(waveform)을 연속된 phoneme으로 변환하는 모델

- AM에서 예측된 phoneme 들을 LM과 연계하여 우리가 읽을 수 있는 단어로 바꿔주는 것이 ASR의 마지막 단계

## End-to-end(E2E) ASR
- 여러 문제/모델로 나누지 않고 한 번에 해결할 수 있는 큰 모델을 만들자는 머신러닝의 방법론 중 하나
- ASR에서는 음성과 이 음성에 대한 테그트만 있는 데이터를 갖고 모델을 학습

- E2E ASR의 단점은 엄청나게 많은 데이터가 필요하다는 것

## ASR의 성능 측정
- Word Error Rate(WER)로 계산
  - 말한 단어 중에 몇 퍼센트의 단어를 틀리게 알아들었냐
