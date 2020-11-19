# RNN

## 시간성 데이터 (Time series data)
- 특징이 `순서`를 가지므로 순차 데이터라 부름
- 이전에 다룬 데이터는 어느 한 순간에 취득한 정적인 데이터이고 고정 길이임
- 순차 데이터는 동적(dynamic)이며 보통 가변 길이김

## Recurrent Neuron (순환 뉴런)
- MLP ,CNN 은 `Feedforward` NN 이라 불림
- RNN 은 `backward` 연결을 가짐
- 출력값이 다시 입력으로 순환
  
- MLP 와 비슷하게 입력층, 은닉층, 출력층을 가짐
- 순환 에지는 t-1 순간에 발생한 정보를 `t 순간으로 전달하는 역할`

### Note : 
- The concept of `Memory`
- 이전 타임에서의 값이 가장 영향력이 있음
- memory cell -> learning only short patterns (최근겂의 패턴 기억)

### Types
- 모든 타팀에서의 input/output이 존재
- TL : Sequence-to-sequence
- TR : Sequence-to-vector
- BL : Vector-to-sequence
- BR : Encoder-Decoder

## How can we train RNN
- 우선 시간에 따라 펼칠 필요가 있음
- 그 다음 일반적인 `backpropagation`을 적용

### Training RNNs
1) forward pass on unrolled net(dashed arrows)
2) evaluate output sequence using cose function C()
3) Propagate gradients backward(sollid arrows)
4) Update model parameters

- 앞의 추적내용이 반드시 필요하지 않음
- Same W and b are used at each time step!
- 모두 동일한 weight bias 값이 사용
- input 과 output 이 다를뿐

### Deep RNNS
- By stacking multiple `layers` of cells

### Forecasting More Time Steps?
- Option
   - to train an RNN to predict all 10next values `at once`
   - But note that we first need to change the targets to be vetors contating the next 10 values

- But We can still do better
    - instead of training the model to forecast next 10 values `only at the very last time step`
    - train it to forecast the next 10 values `at each and every time step.`
    - turn `sequence-to-vetor` RNN into `sequence-to-sequence` RNN




