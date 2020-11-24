# LSTM and GRU

## Unstable gradients problem
### problem in handling Long sequences

- 장기 문맥 의존성 : 관련된 요소가 멀리 떨어진 상황

- 문제점
    - 그레이디언트 소멸(W요소가 1보다 작을때) 또는 그레이디언트 폭발(W요소가 1보다 클때)
    - RNN은  DMLP나 CNN보다 더 심각함
      - `긴 입력 샘플`이 자주 발생하기 때문
      - `가중치 공유` 때문에 같은 값을 계속 곱함

### Handling Long Sequnces
- To train an RNN on long sequences, we must run it over `many time steps`
- When an RNN process a `long sequence,
  - It may suffer from the unstable gradients problem.
  - It will gradully `forget`the `first input` in the sequence.

- RNN 에서 RelU는 좋지 않음
- Using Layer Normalization

### Tacking short-term memory problem
- When traversing an RNN, `some information is lost` at each time step.
- After a while, the RNN's state contains virtually `no trace of the first inputs
  - One facoums solution is `long short-term memory(LSTM)`

## LSTM 
- The Long Short-Term Memory(LSTM)
  - What to `store in long-term`
  - What to `throw away`
  - what to `read`

### Gate Controllers
- `forget gate` controls which parts of the long-term state should be erased.
- `input gate` controls which parts of `g` should be added to the long-term state.
- `output gate` conrols which parts of the long-term state should be read and output at this time step, both to `h` and to `y`

## GRU cells
- Gated Recurrent Unit(GRU)
  - Simplified ver of LSTM
  - Short term and long-term in LSTM are merged.

### 여전히...
- Long term 은 제약되어있고, 아직 정말 긴 데이터를 처리하기에는 문제가 있다.
- 이처럼 100 time steps 이상인 경우 input 자체를 줄이는 방법이 고안
- 이것이 `1D Convolutional layer`

