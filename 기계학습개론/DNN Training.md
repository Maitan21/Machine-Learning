# Vanishing gradients problem
- Gradients often get smaller and smaller as the algorithm progresses down to the lower layers.

- As a result, the Gradient Descent update leaves the lower layer's connection weights virtually unchanged.
  - Training never converges to a good solution

## Occur saturation
- extremely close to 0 - > backpropagation 해도 소용없음
- So there is really nothing left for the lower layers
 -  Solution : 세큐레이션되는 액션 함수
 - softplus 와  rectifier

### Solution - > `ReLU`
Rectified Linear Unit
- It does not saturate for positive values.
- And it is fast to compute

### 문제점
dying ReLU -> 0만 출력하게되버림


### Leaky ReLU
LeakyReLU(Z) = max(`az`,z)
a값을 통해 값의 수렴을 통제

### Parametric Leaky ReLU
a 의 최적의 값을 찾아 수정

### Exponential linear Unit
양수는 선형
음수는 exp
- 죽는 노드가 없다.

### Scaled ELU (SELU)
- 각층의 아웃풋 값이 최대한 0을 취하면서 표준편차는 1을 취하도록 학습
- 훨씬 성능이 좋다
- 단점은 몇가지 조건이 필요한다
  - 표준화가 되어있는가
  - 은닉층의 가중치를 LeCun normal initialization 해야한다
  - 연속적이여야한다.

### Batch Normalization (BN)
- input 정규화하고 scaled 함
- 2개의 파라미터 벡터
  - scaling / shifting
- 비슷한 값으로 정규화
- `Zero-centered` and `normalized input`

