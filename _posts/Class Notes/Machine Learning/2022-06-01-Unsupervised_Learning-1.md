---
title: Unsupervised Learning - 1
date: 2022-06-01 12:04:04 +0900
categories: [Machine Learning]
tags: [study]    # TAG names should always be lowercase
use_math: true
---

## **K-Means Clustering**

1. 무작위로 K개의 클러스터 중심을 정함
2. 각 샘플에서 가장 가까운 클러스터 중심을 찾아 해당 클러스터의 샘플로 지정
3. 클러스터에 속한 샘플의 평균값으로 클러스터 중심을 변경함
4. 클러스터 중심이 변화가 없을 때 까지 2번으로 돌아간다

- 최적의 k 찾기
    - 엘보우 (elbow 방법을 사용해서 최적의 K 찾음)
- K-평균: 클래스별 클러스터의 중심을 반복적으로 계산 하면서, 최적의 클러스터를 구성하는 알고리즘
- 클러스터 중심: K-means algorithm을 통해 만들어진 클러스터에 속한 샘플의 특성 평균값
- 엘보우 방법: 최적의 클러스터 개수를 정하는 방법 중 하나

```python
from sklearn.cluster import KMeans
km = KMeans(n_clusters = 3, random_state, init='random', max_iter=100)
km.fit(X,y)

label_km = kmc.labels_
print(kmc.labels_)

# km_inertia_ : inertia value 계산
# inertia = 클러스터 중심과 샘플 사이 거리의 제곱함

```

## **차원 축소 알고리즘**

- 차원을 축소하는 이유: 데이터에는 중요한 부분과 중요하지 않은 부분이 존재
    - 차원 축소: 데이터의 중요하지 않은 부분을 제거
- 차원의 저주
    - 데이터의 차원이 커질수록 해당 차원을 표현하기 위해 필요한 데이터가 기하급수적으로 많아짐

### **주성분 분석 (Principal Component Analysis)**

- 행렬이 주어짐 → 무언가 특별함을 찾고싶다 → 고유값 고유벡터 구해야함
- 여러 특성이 통계적으로 서로 상관 관계가 없도록 변환
- 데이터에 있는 분산이 큰 방향을 찾는 것 (데이터를 잘 표현하는 벡터)
- 공분산 행렬에서 고유값과 고유벡터가 중요하다

$$
\begin{bmatrix} x축 & x \cdot y \\ x \cdot y & y축 \end{bmatrix}
$$

- 고유값은 분산의 크기, 고유벡터는 분산의 방향

1. 데이터 셋 준비
2. Normalize by each features
3. 특성 데이터의 공분산 행렬 구하기
4. 3에서 구한 공분산 행렬의 고유값, 고유 벡터 구하기
5. 고유값을 큰 순서대로 내림차순 정렬
6. d 차원으로 줄이고 싶은 겨우, 크기 순서대로 d 개의 고유값 선정
7. 6에서 선정한 고유값에 대응하는 고유벡터로 새로운 행렬 생성
8. 1에서 준비한 데이터 7에서 만든 새로운 공간으로 투영

### PCA

```python
from sklearn.decomposition import PCA
pca = PCA(n_components = 50)
pca.fit(fruits_2d)

print(pca.components_.shape)
# (50, 10000)

fruits_pca = pca.transform(fruits_2d)
print(fruits_pca.shape)
# (300, 50)
```

설명된 분산(Explained Variance)

- 주성분이 원본 데이터의 분산을 얼마나 잘 나타내는 지 기록한 값
- 아무리 고차원의 데이터여도 적은 차원으로 데이터가 표현이 가능하다

### **커널 PCA**

- 기존 PCA를 일반화한 방법으로 비선형적으로 수행하는 방법
- Input space 를 커널을 통해 고차원으로 mapping해서 linear하게 seperable 하게 만들어준다
- Kernel : 저차원의 data를 고차원으로 mapping 하는 것

### KernelPCA

```python
from sklearn.preprocessing import StandardScaler
std_scale = StandardScaler()
std_scale.fit(X_tn)
X_tn_std = std_scale.transform(X_tn)
X_te_std = std_scale.transform(X_te)

from sklearn.decomposition import KernelPCA
k_pca = KernelPCA(n_componenets=2, kernel = 'poly')
k_pca.fit(X_tn_std)
X_tn_kpca = k_pca.transform(X_tn_std)
X_te_kpca = k_pca.transform(X_te_std)
```

### PCA + LogisticRegression
## **K-Means Clustering**

1. 무작위로 K개의 클러스터 중심을 정함
2. 각 샘플에서 가장 가까운 클러스터 중심을 찾아 해당 클러스터의 샘플로 지정
3. 클러스터에 속한 샘플의 평균값으로 클러스터 중심을 변경함
4. 클러스터 중심이 변화가 없을 때 까지 2번으로 돌아간다

- 최적의 k 찾기
    - 엘보우 (elbow 방법을 사용해서 최적의 K 찾음)
- K-평균: 클래스별 클러스터의 중심을 반복적으로 계산 하면서, 최적의 클러스터를 구성하는 알고리즘
- 클러스터 중심: K-means algorithm을 통해 만들어진 클러스터에 속한 샘플의 특성 평균값
- 엘보우 방법: 최적의 클러스터 개수를 정하는 방법 중 하나

```python
from sklearn.cluster import KMeans
km = KMeans(n_clusters = 3, random_state, init='random', max_iter=100)
km.fit(X,y)

label_km = kmc.labels_
print(kmc.labels_)

# km_inertia_ : inertia value 계산
# inertia = 클러스터 중심과 샘플 사이 거리의 제곱함

```

## **차원 축소 알고리즘**

- 차원을 축소하는 이유: 데이터에는 중요한 부분과 중요하지 않은 부분이 존재
    - 차원 축소: 데이터의 중요하지 않은 부분을 제거
- 차원의 저주
    - 데이터의 차원이 커질수록 해당 차원을 표현하기 위해 필요한 데이터가 기하급수적으로 많아짐

### **주성분 분석 (Principal Component Analysis)**

- 행렬이 주어짐 → 무언가 특별함을 찾고싶다 → 고유값 고유벡터 구해야함
- 여러 특성이 통계적으로 서로 상관 관계가 없도록 변환
- 데이터에 있는 분산이 큰 방향을 찾는 것 (데이터를 잘 표현하는 벡터)
- 공분산 행렬에서 고유값과 고유벡터가 중요하다

$$
\begin{bmatrix} x축 & x \cdot y \\ x \cdot y & y축 \end{bmatrix}
$$

- 고유값은 분산의 크기, 고유벡터는 분산의 방향

1. 데이터 셋 준비
2. Normalize by each features
3. 특성 데이터의 공분산 행렬 구하기
4. 3에서 구한 공분산 행렬의 고유값, 고유 벡터 구하기
5. 고유값을 큰 순서대로 내림차순 정렬
6. d 차원으로 줄이고 싶은 겨우, 크기 순서대로 d 개의 고유값 선정
7. 6에서 선정한 고유값에 대응하는 고유벡터로 새로운 행렬 생성
8. 1에서 준비한 데이터 7에서 만든 새로운 공간으로 투영

### PCA

```python
from sklearn.decomposition import PCA
pca = PCA(n_components = 50)
pca.fit(fruits_2d)

print(pca.components_.shape)
# (50, 10000)

fruits_pca = pca.transform(fruits_2d)
print(fruits_pca.shape)
# (300, 50)
```

설명된 분산(Explained Variance)

- 주성분이 원본 데이터의 분산을 얼마나 잘 나타내는 지 기록한 값
- 아무리 고차원의 데이터여도 적은 차원으로 데이터가 표현이 가능하다

### **커널 PCA**

- 기존 PCA를 일반화한 방법으로 비선형적으로 수행하는 방법
- Input space 를 커널을 통해 고차원으로 mapping해서 linear하게 seperable 하게 만들어준다
- Kernel : 저차원의 data를 고차원으로 mapping 하는 것

### KernelPCA

```python
from sklearn.preprocessing import StandardScaler
std_scale = StandardScaler()
std_scale.fit(X_tn)
X_tn_std = std_scale.transform(X_tn)
X_te_std = std_scale.transform(X_te)

from sklearn.decomposition import KernelPCA
k_pca = KernelPCA(n_componenets=2, kernel = 'poly')
k_pca.fit(X_tn_std)
X_tn_kpca = k_pca.transform(X_tn_std)
X_te_kpca = k_pca.transform(X_te_std)
```

### PCA + LogisticRegression
## **K-Means Clustering**

1. 무작위로 K개의 클러스터 중심을 정함
2. 각 샘플에서 가장 가까운 클러스터 중심을 찾아 해당 클러스터의 샘플로 지정
3. 클러스터에 속한 샘플의 평균값으로 클러스터 중심을 변경함
4. 클러스터 중심이 변화가 없을 때 까지 2번으로 돌아간다

- 최적의 k 찾기
    - 엘보우 (elbow 방법을 사용해서 최적의 K 찾음)
- K-평균: 클래스별 클러스터의 중심을 반복적으로 계산 하면서, 최적의 클러스터를 구성하는 알고리즘
- 클러스터 중심: K-means algorithm을 통해 만들어진 클러스터에 속한 샘플의 특성 평균값
- 엘보우 방법: 최적의 클러스터 개수를 정하는 방법 중 하나

```python
from sklearn.cluster import KMeans
km = KMeans(n_clusters = 3, random_state, init='random', max_iter=100)
km.fit(X,y)

label_km = kmc.labels_
print(kmc.labels_)

# km_inertia_ : inertia value 계산
# inertia = 클러스터 중심과 샘플 사이 거리의 제곱함

```

## **차원 축소 알고리즘**

- 차원을 축소하는 이유: 데이터에는 중요한 부분과 중요하지 않은 부분이 존재
    - 차원 축소: 데이터의 중요하지 않은 부분을 제거
- 차원의 저주
    - 데이터의 차원이 커질수록 해당 차원을 표현하기 위해 필요한 데이터가 기하급수적으로 많아짐

### **주성분 분석 (Principal Component Analysis)**

- 행렬이 주어짐 → 무언가 특별함을 찾고싶다 → 고유값 고유벡터 구해야함
- 여러 특성이 통계적으로 서로 상관 관계가 없도록 변환
- 데이터에 있는 분산이 큰 방향을 찾는 것 (데이터를 잘 표현하는 벡터)
- 공분산 행렬에서 고유값과 고유벡터가 중요하다

$$
\begin{bmatrix} x축 & x \cdot y \\ x \cdot y & y축 \end{bmatrix}
$$

- 고유값은 분산의 크기, 고유벡터는 분산의 방향

1. 데이터 셋 준비
2. Normalize by each features
3. 특성 데이터의 공분산 행렬 구하기
4. 3에서 구한 공분산 행렬의 고유값, 고유 벡터 구하기
5. 고유값을 큰 순서대로 내림차순 정렬
6. d 차원으로 줄이고 싶은 겨우, 크기 순서대로 d 개의 고유값 선정
7. 6에서 선정한 고유값에 대응하는 고유벡터로 새로운 행렬 생성
8. 1에서 준비한 데이터 7에서 만든 새로운 공간으로 투영

### PCA

```python
from sklearn.decomposition import PCA
pca = PCA(n_components = 50)
pca.fit(fruits_2d)

print(pca.components_.shape)
# (50, 10000)

fruits_pca = pca.transform(fruits_2d)
print(fruits_pca.shape)
# (300, 50)
```

설명된 분산(Explained Variance)

- 주성분이 원본 데이터의 분산을 얼마나 잘 나타내는 지 기록한 값
- 아무리 고차원의 데이터여도 적은 차원으로 데이터가 표현이 가능하다

### **커널 PCA**

- 기존 PCA를 일반화한 방법으로 비선형적으로 수행하는 방법
- Input space 를 커널을 통해 고차원으로 mapping해서 linear하게 seperable 하게 만들어준다
- Kernel : 저차원의 data를 고차원으로 mapping 하는 것

### KernelPCA

```python
from sklearn.preprocessing import StandardScaler
std_scale = StandardScaler()
std_scale.fit(X_tn)
X_tn_std = std_scale.transform(X_tn)
X_te_std = std_scale.transform(X_te)

from sklearn.decomposition import KernelPCA
k_pca = KernelPCA(n_componenets=2, kernel = 'poly')
k_pca.fit(X_tn_std)
X_tn_kpca = k_pca.transform(X_tn_std)
X_te_kpca = k_pca.transform(X_te_std)
```

### PCA + LogisticRegression

```python
from sklearn.linear_model import LogisticRegression
lr = LogisticRegression(I)

target = np.array([0] * 100 + [1] * 100 + [2] * 100)

pca = PCA(n_components=0.5)
pca.fit(fruits_2d)
print(pca.n_components_)
# 2

fruits_pca = pca.transform(fruits_2d)

scores = cross_validate(lr, fruits_pca, target)

from skelarn.cluster import KMeans
km = KMeans(n_clusters = 3, random_state = 42)
km.fit(fruits_pca)
print(np.unique(km.labels_, return_counts = True))
```

