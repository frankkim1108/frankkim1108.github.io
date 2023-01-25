---
title: DALL-E Paper Review
date: 2022-12-20 21:19:04 +0900
categories: [Paper Review]
tags: [computer_vision]    # TAG names should always be lowercase
use_math: true
---

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
- A language model can generate new text by iteratively sampling $\displaystyle \boldsymbol{\hat{x}_{i+1}}$

    $\displaystyle\boldsymbol{\hat{x}_{i+1}\sim f_\theta(x_{i+1}|x_1,x_2, ..., x_i)}$

and then feeding sampling 
$\displaystyle \boldsymbol{\hat{x}_{i+1}}$ back into the model to sample 
$\displaystyle \boldsymbol{\hat{x}_{i+2}}$

$\displaystyle\boldsymbol{\hat{x}_{i+2}\sim f_\theta(x_{i+2}|x_1,x_2, ..., x_{i+1})}$

- This process is repeated until the desired stopping criterion is reached
  - Variation of the smapling methods: "greedy" sampling, top-n sampling, ...

### Auto-Encoder
- This neural network can effectively train data encoding
  - During training, input data and output data are set as same
  - All of the input image is turned into latent vector and return back to its normal state
    - The advantages of it is that input images can turn into conpressed latent code

### Variational Auto-Encoder(VAE)
- VAE's decoder assume the latent code to be in a Gaussian distribution