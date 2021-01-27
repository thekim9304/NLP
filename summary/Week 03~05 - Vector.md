[본문 Week3](https://jiho-ml.com/weekly-nlp-3/)
[본문 Week4](https://jiho-ml.com/weekly-nlp-4/)
[본문 Week5](https://jiho-ml.com/weekly-nlp-5/)

Week3 - Vector의 기초 개념을 다룬다.
Week4 - 단어를 또다른 방식의 vector로 표현한 word embedding
Week5 - vector 간의 비슷함과 거리감을 계산하는 방법

## Week3
####Scalar
  - 크기만 있는 scalar는 우리가 주로 익숙한 숫자를 의미한다.
  - 한 사람의 몸무게나 키, 컵에 들어있는 물의 양, 음식에 포함된 칼로리의 양을 나타내는 숫자 모두 scalar이다.

####Vector
  - Scalar에서 방향도 포함된 것
  - 예를들어, 한 사람에서 특징 10가지를 뽑으면 10차원 vector가 되는 것이다.

## Week4
- 단어 간의 관계를 학습해 vector에 저장하는 word embedding을 공부함
#### Distributional Hypothesis
단어는 주변 단어들에 의해 정의된다.

- Stanford의 GloVe와 Google의 word2vec을 이용해 Distributional Hypothesis를 machine learning 모델로 만듦

#### Word Embedding(word vector)란?
- 이전까지 공부한 one-hot vector는 비효율적 데이터가 클수록 단어의 개수가 몇 천 또는 몇 만으로 커질 수 있다. (차원의 저주)
- word2vec과 GloVe 둘 다 하나의 단어를 몇 천, 몇 만 차원에서 몇 십, 몇 백 차원으로 낮추는게 목표
- embed : "단단하게 박다"라는 뜻
- sparse(듬성듬성하다)의 반대말인 desne(빡빡하다)라는 단어도 같이 많이 쓰인다.
  - word embedding의 모든 row는 0이 아닌 실수로 채워져서

#### Glove
간단한 counting을 이용

- 같은 문장에 한 단어가 어떤 근처 단어들과 몇 번 같이 나오는지 세보는 것
  - 이것을 co-occurrence matrix라고 한다.
- 세 개의 문장을 가진 corpus를 예시로 설명 (corpus : NLP에서는 가지고 있는 텍스트 데이터를 corpus라고 부름)
  ```python
  "I enjoy flying"
  "I like NLP"
  "I like deep learning"
  ```
  ![](https://jiho-ml.com/content/images/2019/11/oJEie.png)

##### 단점
- 너무나 큰 sparse matrix이다.
  - 만약 전체 corpus에 40,000개의 단어가 있다면 40,000 x 40,000 매트릭스가 생성됨

##### 해결법 (dimensionality reduction)
- 차원을 줄여주는 알고리즘
- 40,000 x 40,000을 300 x 40,000으로 압축시켜줌
- GloVe에서는 **SVD(Singular Value Decomposition)** 라는 알고리즘 사용
  - 자매품으로 PCA(Principle Component Analysis)
- 300 x 40,000 행열로 압축이 되면 각 열(300x1)이 하나의 단어를 대표하게 되는것
- 각 단어가 dense한 vector로 압축되어, 한 단어(예를 들어 crawling)를 300개의 숫자로 표현할 수 있게 되는 것

#### word2vec (neural network)
- word2vec은 continuous bag-of-words(CBOW) 또는 skipgram 알고리즘을 통해 학습시킬 수 있다.
- 주변 단어와 타깃 단어의 관계를 예측 문제(classification)로 바꿈
  (1) CBOW - 주변 단어들을 모두 합쳐서 본 후 타깃 단어를 맞추기
  (2) skipgram - 타깃 단어를 보고 주변 단어를 맞추기

## Week5
- 두 vector 간의 거리를 계산하는 방법

#### NLP에서 Vector의 역할은?
- 문장, 문서, 그리고 단어를 숫자들로 이루어진 vector로 만들어 N 차원의 공간에 하나의 점으로 바꾸어 표현

#### Eucliedian Distance : 두 개의 vector 사이의 거리를 재보자
- 두 점 사이의 거리
![](https://jiho-ml.com/content/images/2020/05/eucliedean.png)

#### Cosine Similarity : 두 개의 vector 사이의 각을 재보자
- 두 개의 vector들 사이의 각도를 계산
- 크기(magnitude)는 무시되고, 방향의 차이만 계산
![](https://jiho-ml.com/content/images/2020/01/cosine-similarity2.png)
  - 같은 방향(각도 0)이면 1,
  - 완전히 반대 방향(180)이면 -1,
  - 서로 독립적(90)이면 0.

#### Cosine Distance : 1 - Cosine Similarity
- 같은 방향이면 1,
- 완전히 반대 방향이면 2,
- 서로 독립적이면 1.

#### 주로 Cosine Similarity가 사용됨
  - vector를 단어의 빈도 수로 계산하는 경우가 많기 때문에
  - 어느 단어가 몇 번 등장하냐는 글 길이에 영향을 많이 받고, 데이터 안 모든 글이 같은 단어 수를 갖기는 힘들다.
    - 예를 들어, 어느 긴 글에 "bank"라는 단어가 100번 등장 하고, 어느 짧은 글에는 20번 등장한다 했을 때, 이 두글이 경제라는 비슷한 주제라는 것을 알아 내려면, 절대적 거리는 계산하는 euclidean distance보다는 각도를 계산하는 cosine similarity를 쓰는게 더 적합하다.
  - 목적에 맞게 적절히 사용

?? cosine distance는 vector들 간의 유사성을 계산하기 위해 사용된다는데, 아직 설명이 부족함
