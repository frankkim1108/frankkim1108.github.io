---
title: ResNet Paper Review
date: 2022-02-04 13:12:04 +0900
categories: [Paper Review]
tags: [computer_vision]    # TAG names should always be lowercase
use_math: true
--- 

# ResNet : Deep Residual Learning for Imgae Recognition

## Big Picture

Theoretically the deeper the network the better the performance.

However, before ResNet was released the performance got worse as the network got deeper.

ResNet solved this problem.

Before ResNet, VGG Network had the best performance. It has a small 3 x 3 convolutional filter, which makes a deep layer with a lot of channels.

## Summary

ResNet uses **residual block** to reduce the difficulty of optimization.

$\displaystyle \boldsymbol{F = W_2\sigma(W_1x)}$

&darr;

$\displaystyle \boldsymbol{y = F(x, {W_i}) + W_sx}$

## Paper Review

### Abstract

- reformulated the layers as learning residual functions with reference to the layer inputs instead of learning unreferenced functions
- residual networks are easier to optimize and can gain accuracy from considerably increased depth

### Introduction

- Very deep models had a problem of vanishing/exploding gradients
- Formally $\displaystyle \boldsymbol{H(x)}$ was used for training
- Instead of using $\displaystyle \boldsymbol{H(x)}$, stacking nonlinear layers called $\displaystyle \boldsymbol{F(x): H(x) - x}$ is used
- $\displaystyle\boldsymbol{F(x)}$ is later recasted into $\displaystyle\boldsymbol{F(x)+x}$
- ResNet had better accuracy as the layers got deeper

### Residual Learning

- Identity mapping = Shorcut connection
- Instead of training with identity mapping, adding it is much simpler
- uses much less parameters
- makes optimization easier
