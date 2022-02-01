---
title: Lesson 4 - Backpropagation and Neural Networks
date: 2022-01-20 18:12:04 +0900
categories: [CS231n]
tags: [computer_vision]    # TAG names should always be lowercase
use_math: true
---
{% raw %}

# Backpropagation and Neural Networks

- Numerical gradient is slow and approximate but easy to write
- Analytic gradient is fast and exact but easy to make mistakes
- Chain rule is used during backpropagation
- Backpropagation : Upstream gradient * local gradient

## Backpropagation example

**eg)**
<img src="/images/slides_images/cs231n_2017_lecture4_1.jpg" style="float: center;" />

<img src="/images/slides_images/cs231n_lecture4_2.png" style="float: center;">

- the gradient of the sigmoid function is $\boldsymbol{(1 - a(x)) \times a(x)}$

## Patterns in backward flow

**add** gate: gradient distributor

**max** gate: gradient router

**mul** gate: gradient switcher

<img src="/images/slides_images/cs231n_lecture4_3.png" style="float: center;">

&nbsp;

- **backpropagation** = recursive application of the chain rule along a computational graph to compute the gradients of all inputs / parameters / intermediates
- **forward** : compute result of an operation and save any intermediates needed for gradient computation in memory
- **backward** : apply the chain rule to compute the gradient of the loss funciton with respect to the inputs

## Neural Networks (without the brain stuff)

**Activation Functions**

<img src="/images/slides_images/cs231n_lecture4_4.png">

&nbsp;

**Architectures**
- the layers are fully connected

{% endraw %}