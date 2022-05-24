---
title: Lesson 6 - Training Neural Networks Part 1
date: 2022-01-22 13:12:04 +0900
categories: [CS231n]
tags: [computer_vision]    # TAG names should always be lowercase
use_math: true
--- 

{% raw %}

# **Training Neural Networks Part 1**

## **Overview**

1. One time setup
   - activation functions, preprocessing, weight initialization, regularization, gradient checking
2. Training dynamics
   - babysitting the learning process, parameter updates, hyperparameter optimization
3. Evaluation
   - model ensembles

## **Activation Functions**

<img src="/assets/img/slides_images/cs231n_lecture6_1.png">

### **Sigmoid**

$\displaystyle \boldsymbol{\sigma(x)=1/(1+e^{-x})}$

- squashes numbers to range [0, 1]

**3 problems:**

1. Saturated neurons kill the gradient
2. Sigmoid outputs are not zero-centered
3. exp() is a bit compute expensive

### **tanh(x)**

- squashes numbers to range [-1, 1]
- zero centered
- however still kills gradients when saturated

### **ReLU**

- does not saturate in + regions
- very computationally efficient
- converges faster than sigmoid and tanh

**Problems**

- not zero-centered output
- it might die and never activate

### **Leaky ReLU**

- does not saturae
- computationally efficient
- will not "die"

### **Exponential Linear Units (ELU)**

- all benefits of ReLU
- closer to zero mean outputs
- negative saturation regime compared with Leaky ReLU
- adds some robustness to noise

**Problems**

- Computation requires exp() which is expensive

## **Data Preprocessing**

- make the data zero-centered
- normalize the data

## **Weight Initialization**

- First idea: Small random numbers
  - works okay for small networks but problems with deeper networks
  - the gradient will get smaller and smaller
- **Xavier initialization**
  - tries to match the weight by input size's variance
  - this is used a lot 

## **Batch Normalization**

1. compute the empirical mean and variance independently for each dimenstion
2. Normalize

- usually inserted after Fully Connected or Concolutional layers and before nonlinearity

$\displaystyle \boldsymbol{\hat{x}^k = {x^k - E[x^k]\over \sqrt{Var[x^k]}}}$

- improves gradient flow
- allows higher learning rates
- reduce strong dependence on initialization
- act as a form of regularization

## **Babysitting the Learning Process**

1. **Preprocess the data**
2. **Choose the architecture**

- double check that the loss is reasonable
  - train on a small data and try to overfit
  - if loss is not going down: learning rate is too low
  - if loss is exploding: learning rate too high

## **Hyper Parameter Optimization**

- coarse &rarr; fine
- First Stage: only a few epochs to get rough idea of what params work
- Second Stage: longer running time, finer search
- change parameters in log space when appropriate

{% endraw %}
