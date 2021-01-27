[본문 Week9](https://jiho-ml.com/weekly-nlp-9/)

- 한 문장을 그림처럼 본다

## 글을 어떻게 그림처럼 보지?
#### Word embedding을 쌓아서 그림처럼
- 한 문장의 모든 단어들의 word embedding들을 전부 쌓으면
![](https://jiho-ml.com/content/images/2020/04/figure1-8.png)
  - 2차원 매트릭스가됨
##### word embedding을 쌓아서 heatmap 이미지처럼 표현
![](https://jiho-ml.com/content/images/2019/11/journal.pone.0184544.g009.PNG)


## NLP에서 convolution
- 단어를 보는 CNN(Word CNN)에서는 1D 필터를 사용함
- 하나의 축만 고려하는 1D 필터
  - 2D 필터(vision)는 x, y축의 공간 관계 고려
![](https://jiho-ml.com/content/images/2020/07/conv_maxpooling_steps.gif)

## Pretrained word embedding (transfer learning)
- word2vec, GloVe가 대표적인 word embedding
  - 데이터의 단어 정보들을 vector로 변형하는 모델
- **Pretrained embedding**은 엄청나게 많은 데이터로 학습한 결과물들임
  - Google, Stanford, Facebook 등에서 공개
- 왠만하면 가져다 쓰는게 이득인듯

1. [word2vec](https://code.google.com/archive/p/word2vec/)
2. [GloVe](https://nlp.stanford.edu/projects/glove/)
3. [FastText](https://fasttext.cc/)
