# Gaussian Mixture
A Gaussian mixture model(GMM) is a `probabilistic` model that assumes
- that the instances wre generated from a mixture of serveral Gaussian distributions whose parameter are unknow
  (파라미터를 모르는 혼재된 가우시안 분포에서 발생된 인스턴스) 

  
### Why we need a mixture of Gaussians?

- To density estimation task (밀도 추정 문제)

### How to find GM
- Expectation-Maximization (EM) algorithm
--> EM 알고리즘을 이용한 식 풀이
--> 세타를 모르므로 난수로 설정하고 출발

- 가우시안으로 샘플의 소속 정보 개선(E단계) -> 샘플의 소속 정보로 가우시안 개선(M단계) -> 가우시안으로 샘플의 소속정보 개선(E단계) -> 샘플의 소속 정보로 가우시안 개선(M)
- 궁극적으로 `반복적으로 학습`을 통해서 궁극적으로 `세타가 최대화 되는 값`을 구하는 것이 가우시안 믹스쳐

### GM
A `graphical representation` of a Gaussian mixture model,
- Its parameter,
- random variables,
- conditional dependencies

## Anomaly Detection
Anomaly detection(also called `outlier detection`) is the task of `detecting` instances that deviate Strongly from the norm
* `outlier` : 어떤 정상적인 군집으로 부터 매우 떨어져있거나 거리가 먼 특이한
Anomaly detection is usuful in a wide variety of applications,
- Fraud detection(사기)
- detecting defective products in manufacturing,
- removing outliers from a dataset before training another model

### Anomaly Detection using GM
GM 확률값을 출력 -> 어떤 인스턴스가 Raw -> Anomaly

Using a Gauusian mixture model for anomaly detection
- any instance locate d in a low-density region can be considered an annomaly.

In practice:
- You must define what `density threshold` you want to use.

### Others for Anomaly Detection
PCA
- If you compare the reconstruction error of a noramal instance with the reconstruction error of an anomaly, the latter will usually be much larger

Isolation Forest 
- Random Forest in which each Decision Tree is grown randomly.
- All instances end up isolated from the other instaces.(고립된 인스턴스)
- 고립되었지만 루트와 가까운 리프

## Summary
GMM
- Seems like generalized K-Means 
- 단, 확률을 통해 좀 더 일반화 (non-superviesd)