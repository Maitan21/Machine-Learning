# DNN

## Faster Optimizers

### Momentum Optimization
- Momentum optimization cares a great deal about `what previous gradients were`
- 그전 벡터를 다 기억하고 처리


### Adam
momentum + RMSSprop
- tracking 하면서 최적의 그라디언트를 추적


## Avoiding Overfitting by Regularization
- DNN 에서도  L1 과 ㅣ2 norm을 쓸 수 있다.
- loss를 계산하여 자유도를 제한시키고 오버피팅을 방지 -> 일반화의 성능을 높임

### Dropoout
- 한번 트레이닝을 반복할때 랜덤 subset(특정노드집합)을 무시(dropped out) -> 의미가 없게 만듬

- 랜덤하게 꺼버림으로써 다른 노드에 가중치에 힘이 분산 할수 있음
- 단 성능은 떨어질 수 있으나 일반회에는 좋음

### Early stopping
- 테스트셋의 값이 갑자기 올라갈때 오버피팅가능성을 판단하여 중단