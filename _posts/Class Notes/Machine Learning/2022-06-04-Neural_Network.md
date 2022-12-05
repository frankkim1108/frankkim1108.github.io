---
title: Neural Network
date: 2022-06-04 17:05:32 +0900
categories: [Machine Learning]
tags: [study]    # TAG names should always be lowercase
use_math: true
---

# Deep Learning

- XOR 문제 해결
- Perceptron : 신경망의 최소 단위
    - Input → weighted sum → activation function → output

## Back propagation (오차 역전파)

1. 가중치 초기화 (Random initialize)
2. 순전파를 통한 출력값 계산
3. 비용 함수 (cost function) 정의 및 1차 미분식 구하기
4. 역전파를 통한 1차 미분값 구하기
5. 파라미터 (Parameter) 없데이트
6. (2) ~ (6) 과정 반복

### 3. 비용함수 정의 및 1차 미분식 구하기

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1e344470-030e-4631-9954-a8adb8ce60bb/Untitled.png)

- $1 \over 2$가 들어가는 이유는 미분 할 때 의 편의성을 위해서 추가됐다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0b7167ef-3fa2-4769-bbcc-1ab58025960e/Untitled.png)

- Sigmoid 함수는 계산의 편의성을 준다

### 4. 역전파를 통한 1차 미분값 구하기

- 역전파에서는 가중치나 편향이 변했을 때의 출력값의 변화를 구하기 위해서 미분을 한다

### 5. 파라미터 업데이트

- 학습률
    - Hyperparameter

### 경사 하강법 (Gradient Decent)

- 최소 제곱법을 사용해서 정답과 예측 사이의 거리를 줄였었다
- 머신러닝에서의 최적화 문제
- 최적화 목적 함수인 손실 함수의 미분값을 이용하는 방법
1. 초기 모델 파라미터 $\theta_1$에 해당하는 목적함수 $J(\theta_1)$의 미분값을 구한다
2. 1에서 구한 미분값의 반대 방향으로 $\theta_1$을 $\nabla J(\theta_1)$ 만큼 이동시킨다 (학습률 적용)
$\theta_{t+1} = \theta_{t} + \Delta\theta_{t} \\ \\ \Delta\theta_{t} = -\eta \nabla J(\theta_{t})$

3. 1, 2 단계를 반복한다
- 모든 데이터를 확인해서 경사 하강법을 계산하기 때문에 데이터가 클 수록 학습 시간이 길어짐

### 확률적 경사 하강법 (Stochastic Gradient Decent)

- 일반적인 배치 경사하강법은 데이터 증가에 따라 최적해를 찾는 시간이 길어진다
- 확률적 경사 하강법: 경사 하강법의 샘플링 기법, 전체 데이터에서 추출한 샘플 트레이닝 데이터를 사용해 최적해를 찾음
- 모든 데이터를 다루는게 아니기 때문에 학습률이 잘못될수도 있다

코드 퀴즈 예제)

cross validation의 장단점

cross validation을 극복하기 위한 방법
