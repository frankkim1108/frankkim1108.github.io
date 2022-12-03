---
title: Lesson 13 - Generative Models
date: 2022-02-13 22:08:02 +0900
categories: [CS231n]
tags: [computer_vision]    # TAG names should always be lowercase
use_math: true
--- 

# **Reinforcement Learning**

### **What is Reinforcement Learning?**

Reinforcement learning (RL) is an area of machine learning concerned with how intelligent agents ought to take actions in an environment in order to maximize the notion of cumulative reward.

Agent: 
Agent does action in an environemnt. The agent's purpose is to get as much reward with an action. 

Enviornment:
The environment gives a state to the agent.

Process of Reinforcement Learning

1. Agent receives a State from the Environment
2. Agent that has a state does an action
3. Agent gets a reward from the action
4. Then the agent gets a new agent

With Reinforcement Learning we can solve vairous problems

1. Cart-Pole Problem
2. Robot Locomotion
3. Atari Games
4. Go

### **Markov Decision Processes**

**Markov Decision Processes**는 강화 학습 방법을 수식화 하는 것을 말한다

**Markov Property**는 현재 상태로 전체 상태를 나타내는 것을 말한다

**Bellman Equation**

Bellman Equation is a relation equation between current state value function and next state value function

If State S is given, let's say that Q* is known from Q-Value function

Q* is the maximum reward you can get from an action. Therefore, knowing this we can find the best path at the next state S'

Intuitively, knowing Q* will allow us to get the best reward on the next state S'

**Value iteration algorithm**

We can gradually optimize the value of Q* with Bellman Equation by constantly updating it

**Q-Learning**

Let's find out about how to approximate Q(s,a) with Neural Network.

![](https://user-images.githubusercontent.com/41863759/93012151-ce3bfb80-f5d8-11ea-97a2-1302ff38a3f9.png)

Loss function calculates the difference between Q(s,a) and  Objective function ($\displaystyle \boldsymbol{y_i}$)

($\displaystyle \boldsymbol{y_i}$) is the answer function satisfying Bellman equation

During the Backward Pass process ($\displaystyle \boldsymbol{\theta}$) 

### **Policy Gradients**

There is also a problem with Q-learning
The problem is that the function is too complicated!

The Q - value value must exist for all states.
However, in the case of the example we saw earlier, the number of states were relatively small in four directions.

For example, if you solve the problem of robots picking up objects with reinforcement learning,
The state dimension is very high.

So a new method has been proposed which is learning the policy itself rather than learning the Q-value values according to the state that is suggested.

The method explained above is called Policy Gradients.
