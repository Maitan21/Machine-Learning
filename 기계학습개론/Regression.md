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
  - 한 번의 epoch step 동안에 모든 training set에 대한 cost의 `평균 gradient`를 계산하는 방식.
  
- Stochastic gradient Descent 배치보다 빠르다. Stochastic->random 어느 시점에서 멈출 지 필요함
  - 멈춤 시점이 최적의 코스트라는 보장은 할 수 없음. -> 러닝 레이스를 high -> low (점진적으로 줄이도록) 해결책 중 하나
  - `한 샘플마다` gradient를 계산

- Mini-batch Gradient Descent
  - 풀 배치를 계산하는 것(Batch)도 아니고 하나의 샘풀에 대해서만 계산하는 것(Stochastic)은 아니고 작은 단위의 배치로 계산
  하드웨어가 받쳐주면 미니배치가 병렬작업으로 인해 더욱 빠르다.
  
### Overfitting And Underfitting
1. Overfitting(과대 적합)
- 어려운 가짜 패턴을 포착해 정확한 예측을 할 수 없게 됨
- 일반화가 어렵다 -> 오버피팅

2. Underfitting(과소 적합)
- 패턴을 포착하지 못해서 정확한 예측을 할 수 없게 됨

## Logistic Regression
- 50% 확률로 넘나 안넘나 분류를 하는 것 (`binary classifier`)
- The Logistic Regression model can be generalized to support multiple classes directly
  - without having to train and combine multiple binary classifiers. This called `softmax Regression`
  - 점수(`score`)를 통해 확률을 추론
- Logistic Regresiion 모델을 하나의 클래스 분류 뿐 아니라 다른 클래스 분류 문제에도 적용가능하도록 일반화 할 수 있다.
- `Logistic function`의 output은 `sigmold`함수의 `S-모양`을 나타내는 0에서 1사이 실수값이며, 이 function을 사용하는  Logistic Regression model은 확률값을 추정하는 모델이므로 0에서 1사이 값을 갖는다.

## Polynomial Regression model
- 다항회긔 고차원 -> 저차원으로. 하지만 여전히 선형
- 어느 규칙이 있을 때 좋음
### How to reduce overfitting

- `Regularize the model`(e.g., fewer degrees of freedom)
- Add regularization term `to the cost function` (L1 norm, Lasso; L2 norm, Ridge)
- `Stop` training when val_error reaches a minimum

- 단순히 degree of freedom(예컨대 polynomial degree를 줄인다.)
- Regularization term으로서 L1 norm 을 cost function 에 추가한다.
- Regularization term으로서 L2 norm 을 cost function 에 추가한다.
- 다항회귀의 경우, 모델의 자유도를 줄임으로서 모델을 제한한다.

Sol.1 `Early stopping`
- 트레이닝하다가 validation error 가 최소일때 딱 스탑 
- 규제화 정규화에 특화

Sol.2 `Add regularized term`

Sol.3 `Bagging`

- training set 을 임의로 섞은 후 subset으로 나누어 학습시킨다.  이 때, 동일한 샘플이 각 subset에 반복해서 들어갈 수 있는 가능성을 열어둔다.

## Decision Tree
- 여러 `feature`에 대해 분기하는 것

- 파라미터를 통해 모델 정확도를 조절 할 수 있다.

- Decision tree 학습은 훈련방식에 따라 나누면 지도학습의 한 종류라 할 수 있다.

- Decision tree는 leaf node에서 어떠한 class인지를 구별해주는 분류문제 뿐 아니라 하나의 값으로 수렴하는 회귀문제에도 사용가능하다.

- 조건적 제어문을 포함하는 알고리즘이다.

- Decision tree는 통계관점에서 보면 non-parametric method (no any given probability distribution)
  - 즉, data의 parametric model을 활용하지는 않음.
 
### Q&A
- 이러한 decision tree로 예측모델을 만들 떄, `깊이(depth)`를 한정해주지 않는 방식을 통해서 최대한의 깊이를 확보하는 방식.(즉, 각 샘플들에 대한 다양한 조건문을 최대한 추가하여 분기무의 경우의 수를 늘리는 방식)이 학습데이터 뿐 아니라 새로운 데이터에도 적합한 방식인가?
--> NO!!!!!!!

### 약점
- `Overfitting` to training data.

### 장점
- 데이터 특성을 자세히 알지 못해도 적용 가능하다는 장점
- Easy to implement
- Little data preparation (preprocessing)
- classification 문제와 regression 문제 모두에 자유롭게 적용 가능
- 다양한 파라미터를 사용하여 Tree 모델을 제한하거나 특정 할 수 있다.
- 학습데이터의 확률분포 특성을 사전에 알지 못해도 모델링이 가능하다

 
