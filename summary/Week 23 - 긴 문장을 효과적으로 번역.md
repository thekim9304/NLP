[본문 Week23](https://jiho-ml.com/weekly-nlp-23/)

# RNN
- 하나의 RNN에 모든 단어를 기억하기 때문에 초기 단어들은 잊혀질 수 있음

# Attention Mechanism
- 매 단어를 넣을 때마다 나오는 RNN hidden state를 전부 이용
![](https://jiho-ml.com/content/images/2020/05/figure-4.png)

- 하나의 setence embedding이 아닌, 여러 개의 vector가 출력됨
- weighted sum을 만들어서 averaging
  - 여기의 weight도 학습되는 model parameter임
![](https://jiho-ml.com/content/images/2020/05/figure-5.png)
![](https://jiho-ml.com/content/images/2020/05/figure-6.png)

#### phrase alignment
  - 단어끼리 어떻게 대응 되는지 관계를 찾는 것
  - attention mechanism으로 학습된 모델은 phrase alignment를 자동으로 학습
