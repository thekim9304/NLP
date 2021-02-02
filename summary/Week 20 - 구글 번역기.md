[본문 Week20](https://jiho-ml.com/weekly-nlp-20/)

- 기계번역(Machine Translate, MT)
- MT가 NLP에서 굉장히 중요한 분야인 이유
    1. NLP에서 가장 확실한 응용 분야
    2. MT에서 나온 새로운 모델, 방법론이 다른 NLP 분야에서 이용

# 번역을 하기 위해 필요한 데이터: Parallel Corpora
- 새로운 언어를 공부할 때, 모국어를 기준으로 새로운 언어를 배움
  - "야, 나 공부 정말 열심히 하고 있어." (source)
  - "Hey, I am studying very hard" (target)
- 위 데이터를 parallel corpora라고 부름

# 문장을 잘라서 생각해보자: Phrase-based MT
- 문장을 구절 여러 개로 나누어 각각을 번역하는 방식
- 대략적인 과정
  1. 구절 또는 단어간 대응 되는 사전을 만든다.
  2. 사전에 수록된 어휘에 따라 문장을 나눈다.
  3. 나눈 부분을 번역한 후 순서를 알맞게 바꿔준다.

## 여기서도 딥러닝이 갑 (neural MT)
