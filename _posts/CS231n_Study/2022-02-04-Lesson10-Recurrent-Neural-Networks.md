---
title: Lesson 10 - Recurrent Neural Networks
date: 2022-02-04 21:48:23 +0900
categories: [CS231n]
tags: [computer_vision]    # TAG names should always be lowercase
use_math: true
--- 

# **Recurrent Neural Networks**

## **Lecture 10**

- Recurrent Neural Network
    - Has a hidden state that feeds back every time step
    - hidden state updates when an input comes in
    - Back propagation might take forever if data is big
        
        → Truncated back propagation can be used to solve this problem
        
- LSTM (Long Short Term Memory)
    - two hidden state (hidden state, cell state)
    - Cell State
        - it has 4 gates (i, f, o, g)
        - i : input gate, whether to write to cell
        - f : forget gate, wheter to erase cell
        - g: how much to write to cell
        - o : how much to reveal cell