# Generative Adversarial Network(GAN)
- GAN
- Generator
- Discriminator

## GAN

### Key concepts
- Genrative Adversarial Networks(생성적 적대 신경망, 적대적 생성 신경망)
- 생성자가 만든것을 판별자가 진위여부를 판별, 이런 진위여부 판별을 생성자가 반복해서 검증을 받는 신경망(즉, 진짜같은 가짜 네트워크)

- similar with AEs
  - learn dense representations
  - can be used as generatvie models

- GAN applications:
  - super resolution(없는 것을 만듬), colorization(흑백을 칼러로), image editing,
  - predicting the next frames in a video
  - augmenting a dataset
  - generating other types of data
  - identifying the weaknesses in other models and strengthening them


### Generator (생성자, 가짜 제조 공장)
- 생성장(Generator) :
  - 가상의 이미지를 만들어 내는 공장임

- 작동 방식
  - 처음엔 `랜덤한` 픽셀 값으로 채워진 가짜 이미지로 시작
  - 판별자의 판별 결과에 따라 지속적으로 업데이트
  - 점차 원하는 이미지를 만들어 감

### Discriminator(판별자, 진위 판별 장치)
- 판별자(discriminator):
  - 생성자에서 넘어온 이미지가 가짜인지 진짜인지를 판별해 주는 장치
  - 진짜(1) 아니면 가자(0), 둘중 하나를 결정하는 문제

- 작동 방식
  - 많이 쓰던 CNN 구조를 그대로 가지고 와도 됨.
  - 왜?
    - 컨볼루션 신경망이란 게 원래 무언가를(예를 들면 개와 고양이 사진을) 구별하는 데에 최적화된 알고리즘이기 때문에 그 목적 그대로 사용하면 됨

 <img src="https://user-images.githubusercontent.com/45276804/100497614-f67ed380-319f-11eb-8da6-d6bea61d69f3.png" width=100%/>

### Differneces between AE & GAN
- `Autoencoders` 는 단순히 그들의 input 과 output 이 같아지는 것을 목표
- `GAN`는 similar 하게 만드는 것이 목적이지만 + 판별자를 통한 fake / true 판별
- `GAN` 은 경쟁을 통해 진위여부를 판별해 나감

<img src="https://user-images.githubusercontent.com/45276804/100497760-d69bdf80-31a0-11eb-926c-624dfd49932d.png" width=100%>

## Generative Adversarial Network
- Solution : make neural networks `compete against each other in the hope that this competititon will push them to excel.
- 뉴럴 네트워크로 하여금 서로서로 경쟁하도록 하고 이러한 과정을 통해 서로가 더욱 더 성능을 향상시킴

<img src="https://user-images.githubusercontent.com/45276804/100497856-62ae0700-31a1-11eb-8719-fefd7ec28e9d.png"/>

- Discriminator -> Goal : tell fake from real
- 하지만 큰 틀에서는 fake 가 왔을 떄 real 같다고 잘못 판단하게 하는것이 목적
- 그러면 좀 더 진짜같은 real 를 만들어 낼 수 있다.

### GAN : how to train
- Training with two phases.
  - `First` : train the dicriminator
    - 1) Sample a batch from the training set - real images(label:1)
    - 2) Sample the `same number of the batch` from fake images, `produced by the generator`
  - `Second` : train the generator
    - 1) Make another sample batch from `fake images` produced by generator
      - In this batch, `we do not add real images`, but all the labels are set to 1(real)
      - fake 이미지를 real 이라고 labeling 한다.
    - 2) Again the `discriminator` is used to tell whether the images are fake or real
      - Let the generator to produce images that the discriminator will(wrongly) believe to be real.
    - 중요한 것은 discriminator는 사용만 할 뿐이지 갱신하면 안된다.
    - BP 는 따라서 generator의 가중치에서 영향을 주고  discriminator에는 영향을 주지 않는다.


### The Difficulties of Training GANs
- Fundamental problem:
  - During training, the generator and the discriminator constantly try to outsmart each other, in a `zero-sum game`

- The biggest difficulty is called `mode collapse.`
  - The generator's outputs gradually become `less diverse`
  - generator 의  output 이 다양해 지지 않는 문제

- 게다가, generator 를 수정하면 discriminiator 도 변경되고 즉, `unstable` 하다.

### Solution
- mini-batch discrimination
  -  batch들중 선택하여 mode collapse의 찬스를 줄임


