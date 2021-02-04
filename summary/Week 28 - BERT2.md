[본문 Week28](https://jiho-ml.com/weekly-nlp-28/)

# BERT로 풀 수 있는 문제 유형
- BERT를 사용할 수 있는 4가지 유형
#### 1) 문장 한 개 분류(Single Sentence Classification)
- 문장이 주어졌을 때 어떤한 라벨인지 예측하는 문제

![](https://jiho-ml.com/content/images/2020/08/figure1-2.png)

#### 2) 문장 두 개의 관계 분류(Sentence Pair Classification)
- 문장 두 개가 주어졌을 때 라벨을 예측하는 문제
- 대표적인 문제는 의역 예측(paraphrase detection) // paraphrase : 다른 말로 바꾸어 표현하다.
  - 두 문장이 다른 단어로 쓰였지만 같은 뜻을 가지고 있는지 (글들을 묶어주는 등)

![](https://jiho-ml.com/content/images/2020/08/figure2-2.png)

#### 3) 문장 내 단어 라벨링(Single Sentence Tagging Task)
- 한 문장 내 들어있는 단어에 대한 레이블을 예측하는 문제
- 대표적인 예는 개체명 인식(named entity recognition)
- 품사 태깅(Part-of-Speech Tagging)

![](https://jiho-ml.com/content/images/2020/08/figure3-1.png)

#### 4) 묻고 답하기(Question & Answering)
- 질문과 본문이 주어졌을 때, 본문 속에 답이 있는 부분을 예측

![](https://jiho-ml.com/content/images/2020/08/figure4-1.png)

# BERT에 쓰이는 Transfer Learning 기법 2가지
#### 1) 피쳐 뽑기(Feature Extraction)
- BERT를 블랙박스 함수라고 생각하고 BERT가 내뱉는 vector를 다른 머신러닝 모델의 input으로 사용
- BERT의 파라미터는 고정, 새 모델만 학습
![](https://jiho-ml.com/content/images/2020/08/figure5.png)

#### 2) 재학습(finetuning)
- 데이터가 충분할때
- back-propagation이 가능한 모델이 붙을때만 가능
![](https://jiho-ml.com/content/images/2020/08/figure6.png)

##

- BERT의 약점은 다른 LM처럼 텍스트를 생성하기 힘들다는 것
  - 다음 단어가 아니라 중간에 있는 단어를 예측하는 방식으로 학습이 됐기 때문
