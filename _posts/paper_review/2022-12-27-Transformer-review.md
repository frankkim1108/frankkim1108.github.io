---
title: Transformer(NIPS 2017)
date: 2022-12-27 14:00:12 +0900
categories: [Paper Review]
tags: [deeplearning]    # TAG names should always be lowercase
use_math: true
---

# Transformer

## Development of Machine Translation based on Deep Learning

- Since 2021, new models are based on Transformer architecture
  - GPT: Based on Transformer's Decoder
  - BERT: Based on Transformer's Encoder

## The limit of Seq2Seq models

- Information of source sentences are compressed into context vector $v$
  - This results in bottleneck and decreases the performance of the model

**Problem :** Having a fixed contextz vector that includes all the information about the source sentences reduced the model performance

**Solution :** Inputting each output of the source sentences could solve the problem because the GPU has a large memory and has a capability to calculate parellely

## Seq2Seq with Attention

- Uses an attention mechanism with Seq2Seq model
  - each hidden state is saved and later used in decoder

### Decoder 

<img src="/assets/img/paper_img/transformer_1.png">

### Attention

- As said in the title 'Attention Is All You Need' transformer doesn't need RNN or CNN
  - instead it uses Positional Encoding (Where the word is placed)
- 3 inputs required
  - Query
  - Key
  - Value
- Multi-Head Attention

## Embedding

- Before input goes into the model, each word is embedded
- To not use the RNN model, Position Encoding needs to used
- Then it is inputted into Multi-head Attention
- For performance, Residual Learning is used


<img src="/assets/img/paper_img/transformer_2.png">
