[본문 Week2](https://jiho-ml.com/weekly-nlp-2/)

- 단어가 모여 문장을 이루고, 문장이 모여 문서를 이룬다.

- 단어의 순서는 중요하다.      : 문장이 어떤 말을 하는지 정확하게 알고 싶다면
- 단어의 순서는 중요하지 않다.  : 문장이 어떤 주제를 가지는지만 알고 싶다면

- NLP에서는 해결하고자 하는 문제에 따라 문장을 표현하는 방법이 달라질 수 있음

!! 여기서는 순서가 상관 없는 문장 표현 방법을 배운다.

[bag-of-words(BoW) vector] : 단어의 순서 고려 안함
  - 여러 단어 vector(ont-hot vector)들을 단순히 합하여 문장을 표현한 것
  - 문장 안에(Nx1 매트릭스 안에) 포함되어 있는 단어가 몇 번 들어가있는지 빈도수(frequency)를 표시하는 방법
  ```python
  hello   : [0 1 0 0 0 0] +
  natural : [0 0 0 1 0 0] +
  world   : [0 0 1 0 0 0] = [0 1 1 1 0 0]
  ```

[N-gram] : 단어의 순서를 조금이라도 고려
  - 연속된 n 개의 단어 뭉치
  - machine learning 같은 phrase term도 고려할 수 있음
  - n이 크면 클수록 vocabulary의 크기가 커지기 때문에 보통 n을 2~3으로 설정
  - Ex. "I love studying machine learning"의 bi-gram(n=2)
    - [I love, love studying, studying machine, machine learning]

[Tf-idf vector] : 중요한 단어를 추출
  - term frequency - inverse document frequency
  - 단어 간 빈도 수에 따라 중요도를 계산해 고려하는 방법
    - 관사나 대명사 등을 거르기 위해서
  - 기존 BoW에서 문서 내 단어 빈도수를 고려하되, 다른 문서에도 너무 자주 나오는 건 중요도를 낮추어 점수를 계산
  - Nx1 크기의 BoW vector에서 tf 점수를 idf로 normalize 한 것

[Bow, Tf-idf의 단점]
  1. 순서가 중요한 문제에는 쓰기 힘들다. (machine translation 등)
  2. vocabulary가 커지면 커질수록 쓰기 힘들다.
  3. 단어 간의 관계를 표현하지 못한다.
      - one-hot vector는 각 단어를 각각의 index로 구별하기에 서로의 연관성을 표현할 수 없다.

[결론]
  - BoW와 tf-idf는 간단하지만 **topic classification**이나 document retrieval 같은 task에는 좋은 성능을 보여줌
    - 즉, 순서가 중요하지 않은 task
