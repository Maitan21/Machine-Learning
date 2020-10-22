# Ensemble
wisdom of the crowd(`집단지성`)

- A `group` of predictors (often better predictions than the best individual predictor)

### Types of Ensemble
- Voting Classifiers
- Bagging
- Pasting
- Random Forests
- Boosting
- Stacking

## Voting Classifiers
Training diverse classifiers

- 여러 classifer 를 각각 훈련시킨 후, 각각의 예측값을 이용해 결론값 추론

### Best option for Ensemble

- 각각 독립적일 것

- 다른 알고리즘을 사용하여 train

### Soft voting
- If all classifiers can estimate class probabilities, Then we can predic the class with the probability of the higest class
- 각 레이블의 예측 확률의 `평균`으로 최종 분류

### Hard voting
- `다수결 투표`
- 서로 다른 predictor를 동일한 데이터셋에 학습시킨 후, 각 predictor의 예측값을 모아서 다수의 투표를 득한 예측값을 출력

## Train them on different `random subsets` of training set

### Bagging
With several predictors on differnet random samples of the training set

- Training set 을 랜덤으로 뽑아 예측.
- 모델의 bias를 유지하며 variance를 줄이기 위함
- Ex:) `Random Forest` -> 다양한 데이터셋을 뽑아 학습시키기 때무에 bias는 유지, 특정 데이터에overfitting되는 것을 막고 variance를 줄일 수 있다. 노이즈에 강함
 
### Pasting
- Training set을 쪼개서 각 한번의 트레이닝 기회를 부여

## Boosting

Boosting refers to any Ensemble method that can combine several weak learners into a strong learner
- The general idea of most boosting methods is to train predictors `sequentially`, each trying to correct its predecessor.
- 둘 이상의 weak learner를 조합할 수 있게 하는 방법으로서, predictor를 연달아 학습시킨다는 개념을 포함하여, 특히 바로 이전에서 사용된 predictor를 정정하는 방향으로 predictor를 학습을 시키는 기법

### AdaBoost
<img src="https://user-images.githubusercontent.com/45276804/96753952-92802700-140b-11eb-9e02-6dd71f9dd409.png" width="80%"/>
- Pay a bit more attention to the training instances that the predecessor underfitted(Wek learner)
- 새로운 predictor는 좀 더 까다로운 case에 집중

### Gradient Boosting

- Gradient Boosting works by `sequentially` adding predictors to an emsemble, each one correcting its predecessor.
- But, Gradient Boosting tries to fit the new predictor to the `residual errors` made by the previous predictor.

## Stacking
Short for stacked generalization
`기반모델`이 예측한 값을 `메타모델`이 다시 학습하고 최종 예측하는 모델

<img src="https://user-images.githubusercontent.com/45276804/96754617-8183e580-140c-11eb-9f72-4faa649ac414.png" width="80%" />


A simple idea:
- Instead of using trivial functions (such as hard voting) to aggregate the predictions of all predictors in an ensemble, `train a model` to perform this aggregation.

- Predictions in a `multilayer stacking ensemble`
