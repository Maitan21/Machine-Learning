## Convolutional Layer
- 특정 지역적인 부분만 보고 변환을 시켜 더 높은 차원으로 특징을 변환시키는 레이어

### Padding
- Connections between layers and zero padding (=add zeros around the inputs)
- 딱 맞아 떨어지도록 패딩을 줘 사이즈를 키움
### Conveolution filter
- 이 필터로써 의미있는 정보의 고차원 정보를 추출할 수 있다.
- 각 필터에 해당하는 MAP을 만들 수 있다.
  - Convolutional layers with multiple feature maps
- 필터가 많을 수록 시간이 오래 걸림


## Pooling Layer
Goal : to `subsample` the input image
- 일부만 샘플링
- 복잡한 로드, 메모리 사용. 파라미터 수 제한 가능
- It can limit the risk of overfitting

### Pros
- Max Pooling layer also introduces some level of `invariance(불변성)` to small translations 
- 평행이동 / 병진
  - 실제 output 은 동일
  - 너무 detail이 중요한곳에서는 비추천
  
### Cons
- Very destructive 
  - E.g. 2*2 kernel with a stride 2 -> it drops 75% of inputs
  - 정보가 손실이 크므로 detail이 중요한 애플리케이션에서는 좋지 않음
- Applications may not want invariance
  - E.g. semantic segmentation (classifying each pixel in image)
  - 각 픽셀을 세세하게 / 명확하게 분리 해야하는 경우 detail 중요하므로 원하지 않음

### Pooling Layers VS. Conv.Layers

#### Same
- Each neuron in a layer is connected to the outputs of a limited number of neurons in the previous layer, located within a small rectangular receptive filed.
- You must define its size, the stride, and the padding type.

#### Different
- Polling neuron has `no weights`
- All it does is `aggregate the inputs` using an aggregation function such as the max or mean
  - 최대값 또는 평균값 같은 대표값으로 하나의 값으로 취합 (Pooling)