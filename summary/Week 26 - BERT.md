[본문 Week26](https://jiho-ml.com/weekly-nlp-26/)

![](https://jiho-ml.com/content/images/2020/07/fig1.png)
BERT의 기본 구조 http://jalammar.github.io/illustrated-bert/
- Bidirectional : 양 방향의 (bi-directional RNN 같은)
- Encoder : 문장을 하나의 vector로 암호화
- Representation : 모델이 학습한 후의 결과물
- Transformer
  - self-attention을 통해 하나의 단어를 이해하기 위해 문장 내의 다른 단어들과의 관계, 조합을 본다.
  - 그렇기 때문에 앞만 바라보는 RNN과는 달리 Transformer는 앞뒤를 전부 다 볼 수 있다(bidirectional)
  - Attention 위에 Ateention을 쌓은 Multi-beaded ateetion을 통해 더 복잡한 단어 간의 관계를 모델링한다.
  - 이 모든 정보를 하나의 vector로 압축하여 표현한다.

# BERT의 구조
![](https://jiho-ml.com/content/images/2020/07/fig2.png)
- BERT의 내부는 그냥 Transformer와 다를게 없음
  1. 하나의 문장이 여러 개의 단어로 나뉘고 (Tokenization)
  2. word embedding되어 입력되고
  3. 각 단어마다 output vector가 나옴

# BERT의 차별점
1. LM을 학습하는 방식이 다름
    - 기존 LM은 앞의 단어들을 보고 다음 단어를 예측하는 방식으로 학습됨
    ###
    - BERT에서는 중간 단어를 가리고 예측하는 **Masked Language Model(MLM)** 방식으로 학습
      ![](https://jiho-ml.com/content/images/2020/07/fig3.png)
    - MLM은 좀 더 다양한 방식으로 문장을 학습할 수 있음
      - 그래서 모델이 문장과 단어들에 대한 좀 더 복합적인 이해 능력을 가질 수 있음
    - 주어진 단어들의 15% 정도를 가리고(마스크 씌우고), 원래 단어가 뭔지 예측하는 방식으로 학습

2. 두 문장 간의 관계를 배우는 Two sentence Task
    - 두 개의 문장이 주어졌을 때 이어지는 문장들인지 예측하는 것
      ![](https://jiho-ml.com/content/images/2020/07/fig4-1.png)

# 학습 데이터
- word2vec이나 다른 LM 처럼 BERT 역시 따로 labeling이 필요 없이 아무런 텍스트 데이터만 있다면 바로 학습할 수 있음
  - 문장에다가 마스크를 씌우고, 아무 글의 두 문장을 가져다 이어지는지 아닌지 예측하도록 하면되니까
- 오픈된 pre-trained models
  [Google-research/bert](https://github.com/google-research/bert)
  [huggingface/transformers](https://github.com/huggingface/transformers)
  [SKTBrain/KoBERT](https://github.com/SKTBrain/KoBERT)
