---
id: 548
title: 'Introduction to Reinforcement Learning: Key Terminologies'
date: '2020-12-07T02:23:44+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/254-revision-v1/'
permalink: /254-revision-v1/
---

An important Machine Learning concept is [Reinforcement Learning](https://en.wikipedia.org/wiki/Reinforcement_learninghttps://en.wikipedia.org/wiki/Reinforcement_learning) which is different from the more common [Supervised](https://en.wikipedia.org/wiki/Supervised_learning) or [Unsupervised Learning](https://en.wikipedia.org/wiki/Unsupervised_learning) models. In Supervised learning, you have the labels for training, in Unsupervised learning, there is no labeled data. Reinforcement Learning falls in between the two because it does not have a label but it learns from the feedback it receives which is kind of like the label.

In Reinforcement Learning (RL), there are some key concepts. Let us introduce them through the Hello World example for RL. Imagine you have a robot which does not know how to navigate through a maze. We call this robot an **agent**. The maze is divided into grids.

<div class="wp-block-image"><figure class="aligncenter size-large">![](https://pxt.azureedge.net/blob/0b9ace70b7cc48419a39c23253970318d7f191f0/static/lessons/maze-ai.png)<figcaption>Source: <https://minecraft.makecode.com/lessons/maze-ai-part1> </figcaption></figure></div>Your robot can be located in any of the grids at a time. We call these grids **“states”**. The robot takes an “**action**” at a time which makes it move from grid (state) to another grid. The movement is called “**transition**“. Through this transition it receives some sense of how much it is close to the goal. This is what we call as the “**reward**“. The objective of a RL agent is to accomplish the task so that the rewards are maximum.

Since your robot does not know the task of how to navigate through the maze and reach the goal which is getting out of the maze, so it needs to learn the best **“policy”** which is basically which decision it should take at every state.

That’s all for now. We covered the key terms in RL:

1. Agent
2. State
3. Action
4. Transition
5. Rewards
6. Policy

A problem with such structure can be modeled as a [Markov Decision Process (MDP)](https://en.wikipedia.org/wiki/Markov_decision_process) There are awesome RL algorithms that helps us find the best policies to take at every state to help us plan! So, next, checkout this [follow up post in this Reinforcement Learning series](https://asifrehan.com/reinforcement-learning-policy-iteration-value-iteration-and-q-learning/) where you get introduced to the famous Bellman Equation, Policy Iteration, Value Iteration, and the model-free Q-Learning algorithm!