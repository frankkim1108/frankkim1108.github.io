---
title: DALL-E Paper Review
date: 2022-12-20 21:19:04 +0900
categories: [Paper Review]
tags: [computer_vision]    # TAG names should always be lowercase
use_math: true
---

{% raw %}

# What is DALL-E

DALL-E is a GPT-3 based model that has has 12 billion parameters and is trained with 250 million data
- Personifying object is possible, combining two different concept which are unrelated is possible
- It shows great performance without complex architecture or additional label info
- Well trained DALL-E shows a great performance even in zero-shot situations

## Background Info

### Transformer: Attention is All You Need (NIPS 2017)
- In traditional transformer the output of the last encoder layer is inputted into all the decoder layer

### GPT-2: Language Models are Unsupervised Multitask Learners(OpenAI 2019)
- GPT-2 architecture is based on transformer's decoder
- It is a large languange model trained with large data set
- The GPT-2 autoregressively models the text token as a single stream of data
- A sequence of tokens are inputted and the output is added to the back of the sequence which will later be inputted again

### How text is created with a Language Model
- A language model can generate new text by iteratively sampling 
$\displaystyle \boldsymbol{\hat{x}_{i+1}}$

$$\displaystyle \boldsymbol{\hat{x}_{i+1}\sim f_\theta(x_{i+1}|x_1,x_2,\ldots,x_i)}$$

and then feeding sampling $\displaystyle \boldsymbol{\hat{x}_{i+1}}$

back into the model to sample $\displaystyle \boldsymbol{\hat{x}_{i+2}}$

Equation: 
$\displaystyle \boldsymbol{\hat{x}_{i+2}\sim f_\theta(x_{i+2}|x_1,x_2,\ldots, x_{i+1})}$

- This process is repeated until the desired stopping criterion is reached
  - Variation of the smapling methods: "greedy" sampling, top-n sampling, ...

### Auto-Encoder
- This neural network can effectively train data encoding
  - During training, input data and output data are set as same
  - All of the input image is turned into latent vector and return back to its normal state
    - The advantages of it is that input images can turn into conpressed latent code

### Variational Auto-Encoder(VAE)
- VAE's decoder assume the latent code to be in a Gaussian distribution
- The AE made as distint as possible from each other, this leads to gaps between data points
- On the right plots, the VAE represents the two core mean values on the graph x-y axes
  - Each mean-pair can generate many representations
- The goal of VAE is to maximize the lower bound which is $\displaystyle \boldsymbol{\log{p(x)}}$  also known as ELBO(Evidence of Lower Bound)

## Motivation
- Recent large-scale generative models based on auto-regressive transformer is doing an outstanding job 
  - Generative Pre-training from Pixels (NIPS 2020)
  - GPT-2: Language Models are Unsupervised Multitask Learners (OpenAI 2019)
  - Jukebox: A Generative Model for Music (OpenAI 2020)
- However Text-to-image translation is not researched enought compared to the model shown above
  - currently text-to-image translation studies are using small datasets such as MS-COCO or CUB-200
- In this research large datasets were used for increase in performance

## DALL-E Training Process
- It has a two-satge training procedure like VQ-VAE-2
  1. 256 x 256 image is compressed into 32 x 32 imgae token grid (Each token is assigned from one of 8192 tokens)
     - by doing this it can reduce the context size of the transformer to 8 x 8 x 3 withought quality lose
     - It is more effective than creating consecutive pixels
  2. 256 BPE-encoded text tokens and 1024 image tokens can be inputted consecutively
     - Autoregressive transformer is trained to model joint distribution of text tokens and image tokens
- First maximum of 256 text token in inputted, then maxiimum of 1024 image tokens are inputted

## STAGE ONE: Learning the Visual Codebook
- First dVAE encoder and DVAE decoder is trained with transformer being fixed
  - At this moment prior transformer is set to uniform categorical distribution
- DALL-E solves the discrete problem using gumbel softmax relaxation
- Simply choosing one index from the codebook vector using argmax prevents calculating the gradient
  - softmax has to be used instead of argmax
- In the end sampled latent vector z is used for training instead of argax

## STAGE TWO: Learning the Prior
- Then dVAE encoder and dVAE decoder is fixed and the prior distribution (transformer) is trained
- Image token goes through argmax sampling from dVAE encoder's results which are logits.
- Vairous types of attention mask is used for giving attention to all text tokens
s
## Image Analyze Result
- After training, number of N images are made according to a text
- In this paper the N value was 512

{% endraw %}