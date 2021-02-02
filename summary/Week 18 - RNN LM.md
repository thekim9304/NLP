[본문 Week18](https://jiho-ml.com/weekly-nlp-18/)

# RNN
- RNN은 기억을 저장하는 네트워크임
- RNN은 input 여러 개가 순차적으로 들어가고 output이 하나씩 생성됨
  - 여기서 output은 각 timestep의 예측 값
- 각 timestep마다 hidden state(h)가 연속적으로 이어짐
  - 이 h는 여태까지 들어온 input들 간의 상관관계를 저장하는 메모리의 역할을 함
  - 이 h는 각 timestep마다 조금씩 변화함
    - 왜냐하면 새로 들어온 input에 따라 메모리 역시 변화해야 하기 때문

![](https://jiho-ml.com/content/images/2020/08/figure-1-1.png)
  - 입력 vector(word embedding)와 출력 vector(hidden state)의 크기(차원)가 다를 수 있음

- 아래와 같은 방식(chain rule)으로 문장이 그럴듯할 확률을 풀어쓸 수 있음

![](https://jiho-ml.com/content/images/2020/08/eq1-2.png)
  - "I Love"가 이미 있을 때, "you"가 올 확률
  - "I"가 이미 있을 때, "you"가 올 확률
  - "I"가 문장 처음에 쓰일 확률

- n-gram LM은 이 chain relu을 단순화함
- 하지만 RNN은 문장 끝까지 봄
  - **hidden state라는 메모리 안에 여태까지 본 단어들의 정보가 모두 압축되어 들어가 있기 떄문 (이론상으론)**

![](https://jiho-ml.com/content/images/2020/08/figure-2.png)

# RNN을 학습시키는 방법?
- hidden state를 가지고 다음 단어를 예측하게 하는 것
  - 가지고 있는 학습 데이터를 가지고 하나하나 가르치면 됨
- 하습 데이터에 존재하는 단어들, 그 중 빈도수가 어느 정도 되는 단어들을 가지고 **vocabulary** 리스트를 만듦
  - 빈도수가 부족한 단어는 unknown token으로 퉁치고
- classification 모델
- softmax
- cross-entropy function (cost function)
- 만약 "I love you"와 "This is a sentence"라는 두 문장이 있다면:
  - (input x, output y) # x가 주어졌을 때, y를 예측하기
  - ([], "I")
  - (["I"], "love")
  - (["I", "love"], "you")
  - ([], "This")
  - (["This"], "is")
  - (["This", "is"], "a")
  - (["This", "is", "a"], "sentence")
  - 이러게 7개의 학습 데이터가 만들어질 수 있음

### 실제로는 LSTM이나 GRU를 더 많이 사용함
