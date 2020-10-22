# Dimensionality And PCA

## 표현학습
- 각 레벨(다차원)의 특징을 쉽게 추출

### Curse of Dimensionality
- 데이터 차원이 너무 고차원일 때 극도로 문제를 해결하는게 어려워 질 수 있다.
- 고차원으로 갈수록 관련성이 떨어 질 수도 있음(희소해짐) --> 데이터 분석이 복잡해짐

### Curse of Dimensionality 해결법
- 모든 공간을 꽉채우기 위해서는 너무 많은 데이터가 필요됨 -> 차라리 차원을 줄인다.

## Way to Curse of Dimensionality

### Projection
- 언제나 좋은 것은 아님 -> 오히려 더 겹치는 경우 (`Swiss roll`)

### Manifold Learning
- `d`보다 큰 `n` 차원에서의 일부로 맵핑하는 것.
- `Locally resemble(지역적으로 닮은 모양)` 이 되는 d차원의 hyperplane을 만드는 것
- 'Mainfold' 한다는 것은 `training instances`가 그 manifold에 적절하게 맵핑 될때

## 차원 축소 알고리즘 : PCA (projection or manifold) : Principal Component Analysis
- 가장 가까운 것에 맵핑 할 수 있는 hyperplane을 찾는 것
- 그 데이터를 방금 찾은 데이터에 project 하는 것

- Amount of variance 가 최대(최소) 되는 축 - `C1`
- 그 상태에서 `C1`축과 직교하는 축 - `C2`

### Nonlinear 차원축소 (LLE : Locally Linear Embedding)
- LLE 는 다른 차원 축소기법으로  manifold 기법에 기반한 알고리즘
- 단순한 projecting이 아닌 지역적으로 이웃(거리가 가까운)것의 거리를 유지 -> 각 데이터의 연관성을 살릴 수 있는 t-SNE
- 비슷한 것은 가깝게 비슷하지 않은 것은 멀리 맵핑 하는ㅁ 것
- 시각화에서 효과적


### PCA
- 전처리 단계 : 데이터를 원점 중심으로 옮기는 전처리를 먼저 수행
- 가정 : 데이터들이 원점을 중심으로 분포되었다고 추정하는 변환 공간이 있다고 가정한다.

### Purpose of PCA
- 손실을 최소화하면서 저차원으로 변환
- 주성분 분석은 변환된 훈련집합의 분산이 클수록 정보 손실이 적다고 판단

### 주성분 분석의 학습 알고리즘
- 공분산 행렬
- 고유값과 고유벡터를 구한다.

### PCA최적화 문제
- 비선형에서 선형벡터로 피팅하기 어려움 -> `Kernel PCA`

`Kernel PCA : 메모리 기반`
- 커널함수는 써서 새로운 샘플 데이터가 와도 Afit을 구할 수 있다.

-kPCA 값을 찾는 함수 `GridSearchCV`


