[국어사전에서 언어 정의]
  - 생각, 느낌 다위를 나타내거나 전달하는 데에 쓰는 음성, 문자 따위의 수단
  - 또는 그 음성이나 문자 따위의 사회 관습적인 체계

[vocabulary]
  - 단어를 숫자로 표현하기 위해서 만들어진 알고 있는 모든 단어들의 명단
  ex)index    1        2         3          4            5
          ["hello", "world", "natural", "language", "processing"]

[vocabulary를 vector로 표현]
  - vocabulary를 Nx1 matrix(Column vector) one-hot encoding

[word frequency를 이용한 vocabulary 구성]
  - 대부분의 NLP task는 아는 단어를 모아 vocabulary를 구성하는 것부터 시작
    - NLP에서는 이 데이터를 corpus라고 부름
      - corpus가 크면 클수록 구별되는 단어의 개수가 늘어남
  - 주로 vocabulary를 구성할 때에는 각 단어의 빈도수(word frequency)를 살펴봄 (때에 따라 다름)
    1. corpus의 사이즈에 따라 최소 빈도수(minimum frequency)를 정해 몇 번 이상 나오는 단어만 사용하거나
    2. 총 vocabulary size를 정하고 빈도 수가 큰 단어부터 포함시키는 식으로 vocabulary 구성
