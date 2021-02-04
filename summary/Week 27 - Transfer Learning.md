[본문 Week27](https://jiho-ml.com/weekly-nlp-27/)

- Transfer Learning의 핵심은 각 문제 간의 유사성

# 데이터가 적을 때는 무조건 TL
- 데이터가 적을때는 유사한 데이터로 미리 학습된 모델인 Pretrained Model을 사용

# NLP에서의 TL은?
## 1) Word Embedding
- 각 주변 단어들을 이용해서 한 단어의 문법적, 의미적 정보를 하나의 Vector에 담아 내는 Word Embedding
- NLP에서 가장 기초적인 TL 방법

## 2) Language Model
- 단어 한 개를 1개의 vector로 표현하는 것 => word embedding
- 문장 전체를 1개의 vector로 표현하는 것 => sentence embedding
- ELMO, BERT 같은 모델들은 Sentence Embedding을 계산할 수 있기 때문에 TL 가능
