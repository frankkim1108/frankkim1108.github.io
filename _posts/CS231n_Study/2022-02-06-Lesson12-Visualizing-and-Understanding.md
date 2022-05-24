---
title: Lesson 12 - Visualizing and Understanding
date: 2022-02-06 20:40:06 +0900
categories: [CS231n]
tags: [computer_vision]    # TAG names should always be lowercase
use_math: true
---

# **Visualizing and Understanding**

## **Lecture 12**

- Viusalize layers
    - visualizing the first Convolution Layer
    - visualizing the last Fully Connected Layer with t-SNE
        - it converts the last layer output into 2 dimension
- Occlusion Experiments
    - cover up the input image to see which part of the image was critical for classifying
    - Draw heatmap of probability at each mask location
- Saliency Maps
    - How to tell which pixels matter for classification
    - Can be used for segmentation
- Intermediate features via (guided) backprop
    - compute gradient of neuron value with respect to image pixels
    - only backprop positive gradients
- Gradient ascent
- Deep Dream
    - Amplify existing features
- Neural Style Transfer
    - Style transfer requires many forward