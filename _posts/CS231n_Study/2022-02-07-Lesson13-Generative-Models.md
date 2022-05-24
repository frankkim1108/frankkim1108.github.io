---
title: Lesson 13 - Generative Models
date: 2022-02-07 23:11:02 +0900
categories: [CS231n]
tags: [computer_vision]    # TAG names should always be lowercase
use_math: true
--- 

# **Generative Models**

## **Lesson13**
- Supervised Learning
    - Data (x, y): x is data, y is label
    - Goal: Learn a function to map x → y
    - eg) classification, regression, object detection, semantic segmentation, image captioning
- Unsupervised Learning
    - Data x: just data, no label
    - Goal: Learn some underlying hidden structure of the data
    - eg) Clustering, dimensionality reduction, feature learning, density estimation
- Generatvie Models
    - it creates realistic samples
    - most popular model: PixelRNN/CNN, Variational Auto-encoder, GAN
- Pixel RNN/CNN
    - fully visible belief network
    - explicit density model
    - PixelRNN is sequentially generated so it is very slow
    - PixelCNN is faster than PixelRNN but still slow
    - Pros:
        - can explicitly compute likelihood
        - explicit likelihood of training data gives good evaluation metric
        - good samples
    - Con:
        - Sequential generation → slow
- Variational Autoencoders (VAE)
    - Input data → Encoder → Features → Decoder → Reconstructed Data → L2 Loss function
    - Encoder can be used to initialize a supervised model
    - Pros:
        - Principled approach to generative models
        - Allows inference of q(z|x), can be useful feature representation for other tasks
    - Cons:
        - Maximizes lower bound of likelihood: okay, but not as good evaluation as PixelRNN/PixelCNN
        - Samples blurrier and lower quality compared to state-of-the-art
- GANs
    - Generator network: try to fool the discriminator by generating real-looking images
    - Discriminator network: try to distinguish between real and fake images