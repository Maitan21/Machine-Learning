# Auto-Encoder(AE)

## Key concept: `Autoencoder(AE)`
- Autoencoders are NNs capable of `learning dense representaitions` of the input data, called latent representations (잠대된 /내재된 표현)
- `without any supervision` (감독, 지도)
- AE applications:
  - dimensionality reduction, feature detectors (좀 더 낮은 차원으로)
  - generative models (generating new data that looks very similar to the training data)
  - 즉 핵심적인 부분을 압축하여 좀 더 낮은 차원으로!
- Autoencoder simplay learn to copy their inputs to their output (input == output 비슷하게)


## Simple Autoencoder (no hidden Layer)
- an autoencoder typically has the same architecture as a `Multi-Layer Perceptron`(MLP)
- input 과 아웃풋이 비슷한 MLPT 구현

- Undercomplete AE
  - input(3)->Encoder(2)->Decoder(3)
  - 정보의 손실 있지만 압축
  - 완전하게 input과 output 이 같은 것이 아님
  - 즉, input 에서 가장 중요한 특징만 배우도록 압축
- Undercomplete Linear Autoencoder -> performing PCA
- Simple linear autoencoder to perform PCA on a 3D dataset, projecting it to 2D
### Review : PCA
- `Identify the hyperplane` that lies closeast to the data
- `Project` the data onto it (투영)

### Note : 
- Two subcomponents: the encoder and the decoder.
- The autoencoder's `numver of ouputs is equal to the number of inputs`
- We do not use any activatino function.
 ```{.python}
histoy = autoencoder.fit(X_train,X_train, epochs=20)
# fit(input,output,epochs) input == output
```
- It look likes PCA

## Stacked Autoencoders (A.K.A Deep Encoder)
Having multiple `hidden layers` (like other NNs)

Adding more layers? -> Then, the AE learn more complex codings.
 - But, must be careful not to make the autoencdoer `too powerful` -> Overfitting
 - 덜 input과 ouput이 비슷하도록

- Stacked AE is typically symmetrical w.r.t the central hidden layer.
- input - hidden(encoder) - ouput(decoder)

## Overcomplete AE
노이즈를 제거하는 인코더

## Denoising Autoencoders(DAE)
- input 에 일부러 노이즈를 추가
- 이를 오리지널 input 값을 복원하도록 학습 

#  Different from all the autoencoders (VAE)
- Differnt from all the autoencoders in ways:
  - They are `probabilistic(확률)` autoencoders,
  - Most inportantly, they are generavtive `autoencoders,`

- Variational autoenceoders perform vartiational Bayesian inference

