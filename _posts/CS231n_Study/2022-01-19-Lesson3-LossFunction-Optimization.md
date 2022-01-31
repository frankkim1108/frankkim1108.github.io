---
title: Lesson 3 - Loss Fucntion and Optimization
date: 2022-01-19 19:32:23 +0900
categories: [CS231n]
tags: [computer_vision]    # TAG names should always be lowercase
use_math: true
---
{% raw %}
# Lesson 3 - Loss Function and Optimization

- Define a loss function that quantifies our unhappiness with the scores across the training data
- Come up with a way of efficiently finding the parameters that minimize the loss function which is optimization

## **Loss Function**

- it tells us how good our current classifier is
- loss over the dataset is a sum of loss over examples

&nbsp;
general loss function is shown below

$\displaystyle
\boldsymbol {L = {1 \over  N} \sum L_i (f(x_i, W), y_i)}
0$

&nbsp;

### **Multiclass SVM Loss**

$\displaystyle
\boldsymbol {L_i = \sum_{j\neq y} max(0, s_j - s_{y_i} + 1)}
$

&nbsp;

### **Regularization**

$\displaystyle
\boldsymbol{\lambda R(W)}
$

$\boldsymbol \lambda$ = regularization strength (hyperparameter)

In common use:
5
- L2 regularization : $\displaystyle \boldsymbol{R(W) = \sum_k \sum_l W_{k,l}^2} $
- L1 regularization : $\displaystyle \boldsymbol{R(W) = \sum_k \sum_l \vert W_{k,l} \vert} $
- Elastic net (L1 + L2) : $\displaystyle \boldsymbol{ R(W) = \sum_k \sum_l \beta W_{k,l}^2 + \vert W_{k,l} \vert} $
- Batch normalization, stochastic depth

L2 is often used for weight decay

L1 is often used to pick out features

&nbsp;

### **Softmax Classifier**

&rarr; Multinominal Logistic Gregression

- scores : unnormalized log probabilities of the classes
- Softmax function
  - $\displaystyle \boldsymbol{e^sk \over \sum_j{e^sj}}$
- trys to minimized the negative log likelihood of the correct class 

Loss function:

$\displaystyle \boldsymbol{L_i = -\log P(Y = y_i \vert X = x_i)}$

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$\displaystyle \boldsymbol{= - \log ({e^sk \over \sum_j{e^sj}})} $


## **Optimization**

Different strategies to optimize

1. Random search:
   - very bad idea
2. Follow the slope:

   $\displaystyle \boldsymbol{{df(x)\over dx} = \lim_{h\to0}{f(x+h) - f(x)\over h}}$
   - in 1-dimnsion the derivative of a function
   - in multiple dimensions the gradient is the vector of along each dimension
   - the slope in any direction is the dot product of the direction with the gradient
   - the direction of steepest descent is the negative gradient
   - however numerical gradient is not usefull instead using analytic gradient is recommended
3. Stochastic Gradient Descent (SGD)
  - traditionally adding all the losses can be a very expensive calculation when N is large!
  - instead of traditionally adding all the losses from the whole dataset, using a minibatch to approximate the sum of losses is used

{% endraw %}