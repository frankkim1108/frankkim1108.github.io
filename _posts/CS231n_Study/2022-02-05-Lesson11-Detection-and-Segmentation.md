---
title: Lesson 11 - Detection and Segmentation
date: 2022-02-05 22:33:11 +0900
categories: [CS231n]
tags: [computer_vision]    # TAG names should always be lowercase
use_math: true
--- 

# **Detection and Segmentation**

## **Lesson 11**

- Sementic Segmentation
    - every pixel in the image is categorized
    - downsides: don’t differentiate instances
    - Sliding Window
        - very inefficient, not really used
    - Fully Convolutional
        - stack multiple convolutional layers to preserve all pixels
        - design network as a bunch of convolutional layers with downsampling and upsampling inside the network
    - Transpose Convolution
        - learnable upsampling
        - input gives weight for filter
        - stride gives ratio between movement in output and input
        - the overlapping region is added
- Classification + Localization
    - two fully connected layer for classification and box coordinates
    - two loss for classification and box coordinates
    - Softmax loss for classification, L2 loss for bounding box coordinates
- Object Detection
    - using Sliding Window is a bad idea
    - Region Proposals (RCNN)
        - look for blobby regions and give candidates of the bounding boxes
        - the regions will have different sizes so must be warped to a fixed size for ConvNet
        - Problems
            - computationally expensive
            - training slow + inference is slow
            - Ad hoc traning objectives
    - Fast R-CNN
        - first run the input to ConvNet rather than running each region proposals to the ConvNet
        - ROI is extracted from the output from ConvNet (feature map of image)
        - Problem
            - The computing the region proposal bottlenecks the model
            - Computing 2000 region proposal takes about 2seconds
            - Test time takes less than 1 second
    - Faster R-CNN
        - Region Proposal Network is used to predict proposals from features
    - YOLO / SSD
- Instance Segmentation
    - Mask R-CNN
        - CNN → ROI → CONV → CONV → a segmentation mask for each classes
                             → Classification scores, Box Coordinates