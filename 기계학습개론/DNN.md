# Deep Neural Network (DNN)
- DNN for classification
- DNN for regression
- DNN using keras
  - Building an image classifier

### 출력층
- binary decision classifier
- 노드는 하나
- 출력값을 하나로 정해서 보여 줘야 하므로
- 계단함수는 딱딱한 의삭결성
- Logistic `sigmoid`는 부드러운 의사결정

오차 함수 : MSE 계열과 `cross-entropy`계열
- MSE계열의 함수는 수렴하기까지 속도가 많이 걸린다는 담점 
  - Regression에 유리 (오차 작을 경우에)
  
### 교차 엔트로피 (cross entropy)
- 출력 값에 로그를 취함
  - 오차가 커지면 수렴 속도가 빨라지고
  - 오차가 작아지면 수렴 속도가 감사하게끔 만든 것
- 주로 분류 문제에서 많이 사용
- 특별히 예측 값이 참과 거짓 둘 주 하나인 형식일떄 `binary_crossentropy`를 씀

## DNN 다중 분류문제
cf.) 03_iris_Multi_Classification

### Iris 분류
- 상관도 그래프
  - Seaborn의 pairplot() 활용
  
### Loss

DDN는 loss의 최소화를 목표로 함
 - 단, overfitting의 위험성 있음
 
## DNN 회귀문제
cf.) 13_Boston.ipsynd

- 회귀는 마지막에 참과 거짓을 구분할 필요가 없음
  - 출력층에 활성화 함수를 지정할 필요도 없음

## DNN 영상 분류문제
Building an Image Classifier Using the `Sequential API`

