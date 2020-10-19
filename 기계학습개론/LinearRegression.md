# Linear Regression

- `x`값이 변함에 따라 `y`도 변한다

- `선형 회긔` : 독립 변수 x를 사용해 종속 변수 y의 움직임을 예측하고 설명하는 작업을 말함
## Def of Linear Regression 
- 독립 변수 : `x값이 변함에 따라 y값도 변한다`는 이 정의 안에서, 독립적으로 변할 수 있는 x값

- 종속 변수 : `독립변수` 에 따라 종속적으로 변하는 값


## Type of Linear Regression

### Gradient Descent
- The general idea of Gradient Descent is `to tweak parameters iteratively`in order `to minimize a cost function.`
( 오차함수를 최소화하기 위하여 파라미터를 반복적으로 수정하는 것이다. )

- Batch Gradient Descent
  - 한 스탭의 배치로서 트레이닝 데이터셋을 통째로 가지고 있어야 한다. 트레이닝 셋이 큰 경우 느리다.
  
- Stochastic gradient Descent 배치보다 빠르다. Stochastic->random 어느 시점에서 멈출 지 필요함
  - 멈춤 시점이 최적의 코스트라는 보장은 할 수 없음. -> 러닝 레이스를 high -> low (점진적으로 줄이도록) 해결책 중 하나

- Mini-batch Gradient Descent
  - 풀 배치를 계산하는 것(Batch)도 아니고 하나의 샘풀에 대해서만 계산하는 것(Stochastic)은 아니고 작은 단위의 배치로 계산
  하드웨어가 받쳐주면 미니배치가 병렬작업으로 인해 더욱 빠르다.

