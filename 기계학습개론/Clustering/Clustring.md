# Clustering (군집합)
A task of `identifying similar instances` and `assigning them to clusters(e.g., a set of objects), or groups of similar instances.

클러스터의 정의는 다양함.
## K-Means
### algorithm
1. start by placing the `centroids randomly`
2. Then label the instances, update the centroids.
3. if the centroids is moved
 -> go back to step 2
 -> Otherwise (centroids stop moving), terminate it
4. The end. 

### Problem 1
- Suboptimal solutions due to unlucky centroid initalizations
- To find which is the best model, we need a `metric` to compare.
--> Ineria : the mean suared distance between each instace and its closest `centroid` (하나의 평가 지표)

### Problem 2
- Complexity issue
--> Time : K-Means needs to use the full dataset at each iteration during training.
--> Memory to store all sets.
: when `clusters go huge`, theses issues bcome more critical!
- `Soulution` : Using `mini-batches` during training!

### The Other problems
- Needs
: Run the algorithm `several times` to avoid suboptimal soutions, `Specify` the number of clusters, which can be quite a hassle
- More:
: K-Means does ne behave very well when the clusters have `varying sizes`(다양한 사이즈) / `different densities`(다른 밀도)/ `nonspherical shapes` (구 형태x)

## Where to use?
1. Preprocessing (전처리)
- As a preporcessing step before a supervised learning algorithm
- Can be an efficient approach to dimensionality reduction!
- Exapmple : MNIST - like dataset (8x8 image with 0 to 9 digits)

```{.python}
from sklearn.datasets import load_digits
x_digits, y_digits =load_digits(return_X-y=True)
log_reg = LogisticRegression(multi_class="ovr", solver="lbfgs", max_iter=5000,
log_reg.fit(X_train, y_train)
log_req.score(X_test, y_test)
```
Result : `0.96888888889`

- Clustering for `Semi-supervised Learn.`

### Reference
Kyungpook National University.
Department of Computer Science, IT University
(Introduction to Machine Learning)

경북대학교
ITEC417 IT대학 컴퓨터학부 데이터과학전공
(기계학습개론)


