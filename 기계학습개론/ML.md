# What is machine learning?
- 명시적인 규칙이나 프로그램 `없이` 데이터로부터 학습하는 능력을 갖는 것

## Type of ML
### 지도학습 (Supervised learning)
- 특정 벡터 x(data)와 목표값 Y(label)가 모두 주어진 상황 (`Classification`,`Regression`)

### 비지도학습 (Unsupervised learning) 
- 특정 벡터 X는 주어지는데 목표값 Y가 주어지지 않은 상황.
- 즉, 정답이 없음.(비슷한걸 찾아냄) (`Clustering`,`Dimensionality reduction`, `anomaly detection`)

### 준지도학습 (Semi-supervised learning) 
- 일부는 X와 Y를 모두 가지지만, 나머지는 X만 가진 상황
- X의 수집은 쉽지만, Y는 수작업이 필요한 경우 유용함

### 강화학습 (Reinforcement learning) 
- 단계별 정책을 정함 / 정답을 알지 못함
- 목표를 위한 단계. 학습목표로 갈 정책을 알려줌
- Ex : 알파고 (상태가 있고 짝을 찾음 -> 이런 정책에 따르면 좋아)

<img src="https://user-images.githubusercontent.com/45276804/96473616-d688f580-126c-11eb-8ed2-aeb0b2e4365a.png" width="100%"/>

## Feature of ML

트레이닝 과정이 필요 -> 고성능 하드웨어 /대량의 데이터
통계와는 다르게 대용량의 복잡한 데이터셋을 다룸

## 기계학습의 최적화

- 단지 훈련집합이 주어지고, 훈련집합에 따라 정해지는 목적함수의 최저점을 찾아야함
-> 데이터로 미분하는 과정 필요 -> 오류 역전파 알고리즘
-> 주로 확률적 경사하강법 (Stochastic Gradient Descent) 사용

- 분별(discriminative)모델과 생성(generative)모델
- 분별 모델은 분류 예측에만 관심. 즉 P(y|x)의 추정에 관심
- 생성 모델은 P(x) 또는 P(x|y)를 추정


# Deep Learning

- 심층 신경망을 정보가 `연속된 필터(filter)를 통과`하면서 순도 높게(즉, 어떤 작업에 대해서 유용하게) 정제되는 다단계 정보 `추출작업`으로 생각할 수 있음.

- 데이터로부터 `층(깊이) 심층학습`으로 핵심적인 특징을 새롭게 표현하는 과정 (다단계 처리학습 / Representation learning)

- 데이터로부터 모델을 만드는 데 `얼마나 많은 층`을 사용했는지가 그 모델의 깊이가 됨. 따라서 , 다르게 부르면 층 기반 `표현학습(layered representations learning)` 또는 `계층적 표현 학습(hierarchical representations learning)`이 될 수 있음

- 목표 : 가중치의 정확한 값을 찾는 것 -> 가중치 -> 층(데이터변환) -> 예측




