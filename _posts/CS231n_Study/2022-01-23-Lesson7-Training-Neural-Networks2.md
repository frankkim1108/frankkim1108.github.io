---
title: Lesson 7 - Training Neural Networks Part 2
date: 2022-01-23 19:53:32 +0900
categories: [CS231n]
tags: [computer_vision]    # TAG names should always be lowercase
use_math: true
--- 

# **Training Neural Networks Part 2**

## **Optimization**

### **Problems with SGD**

- if loss changes quickly in one direction and slowly in another

**Very slow progress along shallow dimension, jitter along steep direction**

<img src="/assets/img/slides_images/cs231n_lecture7_1.png">

- if the loss function has a local minima or saddle point
  - Zero gradient, gradient descent gets stuck

### **SGD + Momentum**

- build up "velocity" as a running mean of gradients
- Rho gives "friction", typically rho - 0.9 or 0.99

$\displaystyle \boldsymbol{v_{t + 1} = \rho v_t + \nabla f(x_t)}$

$\displaystyle \boldsymbol{x_{t+1} = x_t - \alpha v_{t+1}}$

### **Nesterov Momentum**

$\displaystyle \boldsymbol{v_{t + 1} = \rho v_t - \alpha \nabla f(x_t + \rho v_t)}$

$\displaystyle \boldsymbol{x_{t+1} = x_t + v_{t+1}}$

### **AdaGrad**

- added elemeny-wise scaling of the gradient based on the historical sum of squares in each dimension

### **RMSProp**

- add decay rate to AdaGrad

<img src="/assets/img/slides_images/cs231n_lecture7_2.png">

### **Adam**

- Momentum, Bias Correction, AdaGrad/ RMSProp is include

### **Regularization**

- Common use:
  - L2 Regularization
  - L1 Regularization
  - Elastic net (L1 + L2)

- Dropout
  - in each forward pass, randomly set some neurons to zero

- Data Augmentation
  - Horizontal Flips
  - Random crops and scales
  - Color Jitter

### **Transfer Learning**

<img src="/assets/img/slides_images/cs231n_lecture7_3.png">
