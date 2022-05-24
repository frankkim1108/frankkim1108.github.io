---
title: Lesson 9 - CNN Architectures
date: 2022-02-02 13:21:04 +0900
categories: [CS231n]
tags: [computer_vision]    # TAG names should always be lowercase
use_math: true
--- 
# **CNN Architectures**

## **Lecture 9**

- LeNet-5
    - first Conv-net
- AlexNet
    - first large scale CNN
    - conv → pool → normalization → fc
- VGGNet
    - small filters, deeper networks
        - stacking three 3 x 3 conv layers which will have the same effective receptive field as one 7 x 7 conv layer
- GoogLeNet
    - deeper layer: 22 layers
    - “Inception module”
        - Apply parallel filter operations on the input from previous layer
        - Concatenate all filter outputs together depth-wise
        - Very expensive compute
        - Pooling layer preserves feature depth → depth increases uncontrollably
    - Solution for very large depth from inception module
        - “bottleneck” layer
        - 1 x 1 conv layer for reducing depth dimension
    - Auxiliary Classification outputs
        - allows to inject additional gradient at lower layers
    - No FC layers
- ResNet
    - Hypothesis: deeper models are harder to optimize
        
        → Solution: Use network layers to fit a residual mapping instead of directly trying to fit a desired underlying mapping
        
    - Very deep networks using residual connections
- Network in Network (NiN)