[본문 Week17](https://jiho-ml.com/weekly-nlp-17/)

- n-gram LM 모델의 한계에 대한 이야기
- 다음 단어를 더 잘 예측하기 위해서 어떻게 LM이 발전하였는지 공부

# LM 여태까지 한 것 정리
1. LM 이란?
    - 어떤 문장이 주어졌을 때, 이 문장의 그럴듯함을 확률로 계산하는 모델
2. LM은 어떻게 학습하는가?
    - 큰 텍스트 데이터 셋(corpus)을 학습 데이터로 사용하여 통계 모델을 구축함
3. N-gram LM이란?
    - 데이터 셋에 나오는 단어 또는 연속되는 단어들의 빈도를 계산하여 LM을 만든 모델
4. LM은 무엇을 할 수 있는가?
    - 여러 가지 문장이 주어졌을 때 가장 그럴듯한 문장을 뽑을 수 있음
    - 문장의 앞부분이 주어졌을 때 다음 단어를 예측할 수 있음

# n-gram LM의 첫 번째 한계: 못 본 단어 조합은?
- 일반화 성능이 zero
- 이러한 한계가 생기는 이유는 n-gram LM에서 각 단어를 전부 독립적인 상관 없는 feaeture로 보기 때
##

- 이러한 한계를 해결하기 위해 word embedding 모델을 사용
- word embedding 모델은 각 단어들을 vector로 바꾸어 vector space에서 적당한 위치에 배치할 수 있도록 학습됨
  - 비슷한 뜻을 가진 단어들은 모여 있게 만들고, vecotr를 더하거나 빼보면서 문법(syntactic) 그리고 의미적(semantic) 관계도 보여줄 수 있다는 것을 의미

# n-gram LM의 두 번째 한계: 기억력이 안좋다
- "In Korea, more than half of all the residents speak _____." 이런 문장에서 3-gram을 사용한다면 residents와 speak만 가지고 밑 줄을 예측해야함
  - 근데 실제로는 맨 앞의 In Korea를 보고 예측하는게 맞음
- 이처럼 n-gram의 n의 수를 5 이상으로 설정하는것이 연산량 측면에서 어려움이 있기 때문에 정확한 예측이 불가능
  - 이러한 문제를 long term dependency라고함
##

- 이러한 한계를 해결하기 위해 RNN(Recurrent Neural Network) 사용
