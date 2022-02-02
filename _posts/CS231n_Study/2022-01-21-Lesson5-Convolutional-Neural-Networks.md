---
title: Lesson 5 - Convolutional Neural Networks
date: 2022-01-21 14:57:26 +0900
categories: [CS231n]
tags: [computer_vision]    # TAG names should always be lowercase
use_math: true
---

{% raw %}

# **Convolutional Neural Networks**

## **Different Types of Layers**

### **Fully Connected Layer**

- Stretch image to 1 layer
  
### **Convolution Layer**

- preserves spatial structure
- filter is used and it always extend the full depth of the input volume
- the result is layers of activation map
- ( CONV &rarr; RELU &rarr; CONV &rarr; RELU &rarr; POOL ) X n times and at the end use fully connected layer
- Zero padding is used for keeping the Image size

<img src="/images/slides_images/cs231n_lecture5_1.jpg">

### **Pooling Layer**

- makes the representations smaller and more manageable
- downsampling

<img src="/images/slides_images/cs231n_lecture5_2.jpg">

{% endraw %}