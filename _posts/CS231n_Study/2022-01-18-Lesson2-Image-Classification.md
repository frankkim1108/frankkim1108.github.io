---
title: Lesson 2 - Image Classification
date: 2022-01-18 17:35:00 +0900
categories: [CS231n]
tags: [computer_vision]    # TAG names should always be lowercase
use_math: true
---

# **Lesson 2 - Image Classification Pipeline**

## **Data-Driven Approach**

1. Collect a dataset of images and labels
2. Use Machine Learning to train a classifier
3. Evaluate the classifier on new images

&nbsp;

## **Nearest Neighbor**

- **Train** function memorize all data and labels
- **Predict** function predicts the label of the most similar training image

- With N examples, how fast are training and prediction?
  - Train is O(1)
  - Predict is O(n)

  &rarr; This is bad because we want fast predictions

&nbsp;

### **Distance Metric**

#### **L1 distance**

pixel-wise absolute value differences

$\displaystyle
d_1(I_1, I_2) = \sum_{p}\vert I_1^p - I_2^p\vert
$

#### **L2 (Euclidean) distance**

$\displaystyle
d_2(I_1, I_2) = \sqrt{\sum_{p}(I_1^p - I_2^p)^2}
$

### **Setting Hyperparameters**

- Choose approperiate hyperparameters
- Split data into **train, val,** and **test**
- Cross-Validation: Split data into folds

## **Linear Classification**

$
f(x, W) = Wx + b
$

$W$ :  parameters or weights

$x$ : input image

$b$ : bias
