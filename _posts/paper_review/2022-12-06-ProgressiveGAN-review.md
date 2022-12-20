---
title: Progressive GAN Paper Review
date: 2022-11-7 21:19:04 +0900
categories: [Paper Review]
tags: [computer_vision]    # TAG names should always be lowercase
use_math: true
---

# **Progressive Growing of GANs For Improved Quality, Stability and Variation**

## **1. Abstract**
### **1. Problem**
   
PGGAN(Progressive Growing of GANs) became a big issue when it was first introduced in 2017 Nvidia's paper.

On a typical GAN model, creating a high resolution image can cause some problems.
- Creating a high resolution image is very hard. Because as the image resolution gets higher, discriminator has a hard time distinguishing the fake image created by thre generator
- Eventhough if it can create a high resolution, because of the memory limit, the batch size has to become smaller. Smaller batch sizes result in unstable traingin process.

### **2. Approach**
   
The keypoint proposed in this paper is to **gradually develop Generators and Discriminators**. The layer is gradually added to from low resolution to high resolution. Through this gradual process of adding layers and training, high resolution images are gradually created (this paper shows 1024 x 1024 images were generated in this way).

## **2. Progressive Growing of GANs**
### **1. What are the advantages of gradually adding layers to train?**

Image Distribution helps us first discover the Large Scale structure. In other words, the keypoint of the paper is "to train by gradually stacking the models of Generators and Discriminators." At first, we trained the overall contents of a person's face by looking at the large scale, which is a feature that can only be seen in low-resolutions, and as we gradually build up the layer, we train to look at detailed features such as eyes noes mouth and more. 

In this paper it says that when adding a layer to the model, the new layer is added smooth and fades in. This means that it prevents having a sudden shock for other layers of the previous steps that have already been well trained.

The method of training by gradually stacking layers has the advantage of being stable during training.

In addition, the method of gradually stacking layers and generating a high resolution image has the advantage of training with latent vector being mapped according to othe resolution. Therefore, it can create a high resolution image stably.

### **2. Training Methods**

**UpScaling**

For easy understanding I'll give you an example. When you watch TV, if you watch a normal video on a UHD screen, the screen will look blurry because it cannot fill all horizontal and vertical pixels. It can be solved with upscaling. Upscaling fills in missing pixels and makes the image more clear.

**Fade In**

During transition(Up Scaling in G, Down Scaling in D), weight is controlled by alpha to stabilize its increase from 0 to 1. Therefore, the weight increases linearly from 0 to 1 while the layer is completely trained.

**Normalization in Generator and Discriminator**

In general GAN model has a escalation of signal magnitudes due to unnecessary competition between Generator and Discriminator. To suppress this, the Batch Normalization method was used, which was introduced to eliminate the convolutional shift phenomenon. However, they didn't use Batch Norm in this paper because they didn't see any problem with the Covariate shift. Then you might wonder what normalization they used here, but they solved the escalation of signal magnities problem using Pixelwise feature vector normalization, which is summarized right below.

**Pixelwise Feature Vector Normalization**

One of the normalization methods used in deep learning is Batch Normalization. However, it is said in this paper that batch normalization is not effective. Instead Pixelwise normalization was used. Pixelwise normalization is where the Feature Vector for each pixel is normalized for each unit of lenght and applied to the last end of each layer.

So why use Pixelwise Normalization instead of Batch Normalization?

It is said to be a technique used by Generator and Discriminator to prevent Magnitude from getting out of control as a result of competition./

In more detail, each convolution layer is normalized with Pixelwise for the Feature layer, and local response normalization is modified and implemented.

Althogh the method does not significantly change the outcome, it is known to effectively prevent escalation of signal magnitudes during training.

**Down Scaling**

It can be seen as a procedure for inferring information of a high resolutipon from a low resolution.

Here are the steps of the training process.

[Step 1]

Downscale the real images according to the current resolution of the network. Then the image becomes a low resolution image but it still has all the information

[Step 2]

In the process of Resolution Transition, interpolation is performed between two resolutions of the Real image. In this paper, the process is explained as a **Fade In** process.

**Equalized Learning Rate (runtime weight scaling)**

The autor said that in order to ensure a healthy competition between Generator and Discriminator, learning at a similar rate is essential and Equalized Learning Rate is suggested approach in this paper. First of all, this method initializes the weight to a value with a range of 0 to 1 in Gaussian Distribution.

For all weights, set a same Dynamic range. The reason for doing this is to update the Gradient regardless of the scale of the parameter. When the dynamic range is different for each parameter, it takes a lot of time to adjust the value. Therefore, the author used the Equalized Learning Rate approach to ensure the same learning speed by having the same dynamic range for the parameters of different layers.

