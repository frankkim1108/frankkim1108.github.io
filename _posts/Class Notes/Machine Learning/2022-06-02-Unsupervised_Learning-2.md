---
title: Unsupervised Learning - 2
date: 2022-06-02 15:21:46 +0900
categories: [Machine Learning]
tags: [study]    # TAG names should always be lowercase
use_math: true
---

### Kernel

- 함수는 내적으로 표현이 가능하다
- 차원 확대가 가능하다

### 독립 성분 분석 (Independent Component Analysis, ICA)

- Cocktail party problem을 해결 할 때 사용되는 알고리즘이다

$$
x = As \\ s = A ^ {-1} x = Wx \\ s = source \space , \space x = recorded \space sound
$$

- A: 혼합 행렬
- A를 알아내기 위해 Independent Component Analysis를 한다
- **중심극한정리** : n개의 확률변수들의 선형결합으로 만들어진 확률변수는 가우시안 분포를 따른다
( n → 무한대 ) 이면 더욱더 가우시안을 따른다
대우명제: 정규분포를 따르지 않는 n개의 확률분포들이 independent(non-gaussian) 하다
- ICA는 정규분포화 되어있는 것을 서로 다른 독립된 확률 변수로 나누려고 한다
- 역행렬구하는 계산은 매우 어렵다 —> 역행렬을 없애려고 해야한다

### Non-negative Matrix Factorization (NMF)

Non negative 의 장점

- 역행렬 계산시 편리함
- 이미지 데이터 처리 시 음영 표시가 편리함
- 0 ~ $\infty$  필요없는 데이터를 0으로 보낸다

### t-SNE (Stochastic Neighbor Embedding)

- t 분포 (가우시안 분포 아님)
    - 가우시안 분포 보다 t 분포 기울기가 더 낮기 때문에 error가 줄어든다
- Neighbor Embedding : 고차원에서 저차원으로 Data를 보낼 때 유사성 유지
- Stochastic한 이유 : 기준점을 random으로 잡기 때문
