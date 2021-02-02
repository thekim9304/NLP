[본문 Week25](https://jiho-ml.com/weekly-nlp-25/)
[논문](https://arxiv.org/pdf/1706.03762.pdf)

- BERT, GPT의 기반이 되는 모델

# RNN은 한 방향 밖에 보지 못한다.
> 반바지를 입고 아이스크림을 들고 있던 아이는 그것을 금방 다 먹었다.

![](https://jiho-ml.com/content/images/2020/06/figure1.png)
- 모델이 "그것"이 가리키는 것이 "아이스크림"이라는 것을 이해하기 위해서는 "먹는다"까지 고려해야함
- 하지만, 순차적인 처리 구조 때문에 불가능

## 이 문제를 해결하기 위해 bi-directional RNN 등장
- forward RNN, backword RNN 두 개의 hidden state output을 엮어서 함께 보는 방식
![](https://jiho-ml.com/content/images/2020/06/figure2.png)
  - 하지만 backword에서는 아이스크림을 보지 못했음

# Attention Is All You Need
- Attention Mechanism은 번역 문장(target)을 생성할 때 원본 문장(source)의 여러 부분을 한꺼번에 참고하기 위해 만들어진 구조
- Transformer는 RNN 제거하고 Attention만 남김
  - Attention mechanism으로 문장 앞 뒤 모두 다 볼 수 있음
![](https://jiho-ml.com/content/images/2020/06/figure4.png)

- 여기서 Word embedding에 추가로 **Positional Embedding**이라는 것이 추가로 붙음
  - RNN을 제거하면서 단어의 위치 정보를 추가해야함
  - 단순히 위치 값을 첨부하는게 아닌 sin, cos 함수를 합성하여 나타낸 vector로 표현함(논문 참고)

# Transformer가 좋은 성능을 보여주는 이유
- 정확한 내용은 본문으로
## 1) Self-Attention
- 여러 가지의 단어 조합을 한 번에 관심에 넣을 수 있음
- 그래서 더 복잡하고 많은 파라미터를 보유

## 2) Multi-headed Attention
- Encoder를 여러 개 쌓아올려 단어 조합의 조합, 조합의 조합의 조합까지 고려할 수 있음

## 3) Parallelization
- RNN과 달리 각 위치에서 문장을 통채로 보기 때문에 따로 계산이 가능
  - 따라서 분산 컴퓨팅이 가능함
