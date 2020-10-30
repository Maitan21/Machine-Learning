# Perceptron
- 신경망의 가장 간단한 구조
- 신경망을 통해 출력
- Inputs -(Weights)>`Step function` -> Output

- Threshold logic unit(TLU)
- TLU computes a `weighted sum of inputs`

##Perceptron : the limit
- XOR problem

### Solution?
- 차원 변환 (좌표측 변환, 좌표평면 변환)
- Multi-layer perceptron(MLP)

## MLP
은닉층 (Hidden layer) 
입력 층 -`(가중합)`> 은닉 층 -`(활성화 함수)`> 출력 층

### Back-propagation (BP)

- 신경망 성능의 비결 : 오차 (오류) 역전파 알고리즘
  - 신경망 내부의 가중치는 오차 역전파 방법을 사용해 수정함(학습함)
  - 오차 역전파는 `경사 하강법`의 확장 개념
- How?
  - 가중치를 구하는 방법은 경사 하강법을 그대로 이용
  - 임의의 가중치를 선언하고 결과값을 이용해 오차를 구한 뒤 이 오차가 최소인 지점으로 계속해서 조금씩 이동
  - 이 오차가 최소가 되는 점(`미분했을 떄 기울기가 0이 되는 지점)을 찾으면 그것이 바로 우리가 알고자 하는 답임

### BP for MLP

BP for Perceptron
- 처음 W는 initialized value -> 이후 BP통해 W수정

BP for Multi-layer Perceptron
- 실제 값과 비교 
- 출력층 가중치 수정
- 은닉충 가중치 변경

- Every layer except output is `fully connected` to next layer
### 오차 역전파 구동 방식
1. 임의의 초기 가중치(W)를 준 뒤 결과를 계산
2. 계산 결과와 우리가 원하는 값 사이의 오차를 구함
3. 경사 하강법을 이용해 바로 앞 가중치를 오차가 작아지는 방향으로 업데이트함
4. 위 과정을 더이상 오차가 줄어들지 않을 떄까지 `반복`함

- 새 가중치는 현 가중치에서 `가중치에 대한 기울기`를 뺀 값

### 신경망 학습 과정
<img src="https://user-images.githubusercontent.com/45276804/97250101-91eef280-1848-11eb-8dd0-34c6d7ddc95c.png" />

## MLP in detail
- Two layers(input and output)
- Here. We call
  - `Fully connected layer`
  - or `Dense layer`
- Bias neuron:
  - outputs # all the time


### How is Perceptron trained?
- Perceptron learning rule reinforces connectins that help `reduce the error`
  - Perceptron learning rule (weight update)

## Backpropagation training algorithm

- It can find out how each `connection weight` and each bias term should be `tweaked` in order to `reduce the error.`

- Once it has these gradients, it just performs a regular Gradient Descent step, and the whole process is `repeated` until the network converges to the solution.

### Backpropagation (in detail)

- It handles one `mini-batch` at a time, and it goes through the full trainingset multiple times.
  - Each pass is called an `epoch`
  
- `Forward pass`
  - Each mini-batch is passed to the network's input layer,  which sens it to the first hidden layer.
  - The result is passed on to the next layer, its output is computed and passed to the next layer, and so on until we get the output of the last layer, the output layer/.
  - It is exactly like making predictions, except all intermediate results are preserved since they are needed for the backward pass

- The algorithm measure the `nework's output error`
  - 에러만큼 그 이전레이어로 가서 어떤 모드가 에러가 크게 기여했는지 파악
- It computes how much `each ouput connection` contributed to the `error`

- The algorithm then measure hgow much of pthese error contributions came from each connection in the layer below, workding `backward` until the algorithm reaches the input layer.

- Finally, the algorithm performs a `Gradient Descent step` to tweak all the connection weights in the network, using the error gradients just computed.

## BP in summary

- For each training instance, the backpropagation algorithm first maekds a prediction (forward pass)
- And measure the error,
- Then goes through each layer in reverse to measure the error contribution from each connection(reverse pass)
- And finally tweaks the  connection weights to reduce the error (Gradient Descent step).

### But for BP

- For this algorithm to work properly, we need key change to the MLP's architecture
- This was essential because the step functioni contains only flat segments, so there is no gradient to work with(Gradient Descent cannot move on a flat surface)
- In fact, the backpropagation algorithm works well with many other `activation functions`

