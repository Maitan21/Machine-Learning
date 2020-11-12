# Famous CNN Archeitectures


## Conventional CNN Archi.
The most widely known CNN architecture for MNIST

가장 전통적이고 널리 알려진 방법

### LeNet-5
- Input layer adds zero padding
- Other layers do not use padding.
- Avg pooling is more complex than usual.
   - This requires more weights/bias
   - != recent avg pooling
- Output layer computes `Euclidian distance`

### AlexNet, 2012

#### Characteristics
- `ReLU` for activation function
  - 첫 CNN에서의 ReLu 사용
- Local response `normalization` scheme
  -  요즘은 batch 이용
- Overlapping Pooling : Kernel size > stride
  - With `max pooling`

### Note:
- To reduce `overfitting` , Used two `reqularization techniques`.
    - Dropout : fully connected type에 적용
        - 이걸 안하면 overfitting이 심하게 일어남
    - Data augmentation 
        - 트레이닝할 데이터가 한정 -> 데이터를 조금 변형(회전, 평행 이동 등)
- 이를 통해 트레이닝 셋이 커지고 더 학습할 가능성이 증가하고 일반화에 좀더 유용

### VGGNet, 2014
- 가장 큰 장점은 심플하다
  -  이해하기 쉽다
  -  구현하기 쉽다
  -  2 or 3 conv layers + pooling layer <- repeat this pattern
  


## Network in Network
key : Inception module

### GoogLeNet , 2014
10배나 적은 파라미터를 가지지만 네트워크는 더 깊어짐

#### Inception module
- 3 x 3 + 1(S) means that the layer uses a 3 x 3 kernel, stride 1, and "same" padding
- outputs all have the same height and width as their inputs
    - 인풋과 아웃풋의 해상도는 같다.
    - So, we can concatenate all outputs along differnet conv layers (레이어들 최종적으로 합쳐서 아웃풋함)

- Why we need 1x1+1 conv layer?
  - Can capture pattern(depth dimension)  
  - Can output `fewer feaure map` inputs -> C개의 feaure map이 하나로 출력됨 (`bottleneck layer)
  - 정보손실은 일어나지만 핵심만 걸러냄
  - reduced complexity

#### 핵심 원리
- 연속된 Convolution을 하나의smart layer로 취급
- intercetion module
  - 필터맵(채널) 숫자는 증가하고 레이어가 깊어짐
  - con이 연달아 나오다가 pooling이 나옴
  - Global avg pool 은 모아 하나의 대표적인 값으로 표현
    - 공간적인 정보가 축소
    - pooling 과 stride를 통해 파라미터 제한
      - `limits overfitting`
      - `Sparese net` 희소하다
- Last 과정으로는 Dripout, Dense , Softmax


## Residual Learning 
나머지값, 잔차, 잔여차이

### ResNet ,2015
- more layers than googLeNet
- It confirmed the `general trend`
- models are getting deeper and depper, `with fewer` and fewer parameter

- Key : `residual learning` by `skipping connections`
- f(X) = h(x) - x : 목표에서 input 값을 뺀 차이값(`Residual`)
- 이 residual를 학습하는것이 residual learning 

#### Note :
- 우리가 일반적으로 reqular neural network를 초기화할때 각 가중치를  0에 가까운 수로 지정 -> 이러면 ouput의 값도 0에 가까워 질 수 있음
- If you add a skip coneection.
  - input 값이 처음 output의 값
  - Target function 이 identity function 과 매우 close 해야할때, 이 방법이 트레이닝 스피드를 효과적으로 올릴 수 있다.
- 일반적인 딥뉴럴네트워크에서는 학습하기위해 밑으로 내려갈때 학습을 할 수 없음
- 그러나 residual network는 동시에 다른 학습을 진행 할 수 있다. -> 속도가 빠름 / banaishing problem 해결
- It can be seen as a `stack` of resiudal units(RUs)

### Inception-v4, 2016
Residual connections을 이용한 GoogLeNet
- Computational cost를 줄임
- 기본 1 Conv를 1x1 Convolution으로 변경

## Squeeze + Excitation
Excitation : 에너지가 높은 준위로 옮아가는 현상

### SENet
inception 과 ResNet을 좀더 확장함

- SE block을 이용함
- feature map recalibration (재측정)
- An SE block focuses exclusively on the `depth dimension`
- And it learns which feature are usually most `active together`
- 흰것은 더 희게 검은것은 더 검게
<img src="https://user-images.githubusercontent.com/45276804/98899078-48620100-24f2-11eb-85a8-b1e313a8c508.png" width 50%>