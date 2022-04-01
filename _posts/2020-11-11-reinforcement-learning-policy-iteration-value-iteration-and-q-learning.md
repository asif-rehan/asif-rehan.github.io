---
id: 422
title: 'Policy Iteration, Value Iteration, and Q-Learning'
date: '2020-11-11T04:26:57+00:00'
author: 'Asif Rehan'
excerpt: 'Quick introduction to basic Reinforcement Learning algorithms including Bellman Equation, Policy Iteration, Value Iteration, and Q-Learning '
layout: post
guid: 'https://asifrehan.com/?p=422'
permalink: /reinforcement-learning-policy-iteration-value-iteration-and-q-learning/
image: /wp-content/uploads/2018/08/admin-ajax-1.png
categories:
    - Algorithms
    - 'Data Science'
tags:
    - algorithms
    - 'Reinforce Learning'
---

For the introduction to background information on Reinforcement Learning, please check out the [previous article here](https://asifrehan.com/introduction-to-reinforcement-learning-key-terminologies/).

## Bellman Equation

MDP is a mathematical framework to model discrete-time stochastic systems. MDP consists of some States (S), Actions (A) to be taken while at each state, Transitions (T) from a state, s, to another state, s’, by taking an action with a probability T(s,a,s’). At each state, the agent who is interacting with the system, collects a reward R(s), or R(s,a), R(s,a,s’), depending on the stochasticity of the system.

<figure class="wp-block-image">![ V(s) := \sum_{s'} P_{\pi(s)} (s,s') \left( R_{\pi(s)} (s,s') + \gamma V(s') \right) ](https://wikimedia.org/api/rest_v1/media/math/render/svg/9774acab787cd166e43d70ec03797b73d5e4469e)<figcaption>Equation (1): Bellman Equation showing Recursive Value function</figcaption></figure>A MDP is solved when the best policy, π(s) is identified for every state. Policy means the action the agent decides to take when at a state so the probability of the total reward in the first equation below is maximized as shown in the second equation below.

<figure class="wp-block-image size-large">![](https://wikimedia.org/api/rest_v1/media/math/render/svg/0174e4387a5d3f71b495b6f4557b49bc8d860cf2)<figcaption>Equation(2): Finding Optimal Policy by Taking the Best Action for Each State</figcaption></figure>## Policy Iteration

<figure class="wp-block-gallery columns-1 is-cropped">- <figure>![](https://asifrehan.com/wp-content/uploads/2020/11/Screenshot_20201110-2312122.png)</figure>

</figure>Policy Iteration (PI) algorithm needs the T and R matrices. It starts with a policy to and updates the Value function as in Eq(1) and then finds the best policy from Eq(2) until the new and previous policies are the same. This is a straightforward iterative process.

## Value Iteration

<figure class="wp-block-image size-large">![](https://asifrehan.com/wp-content/uploads/2020/11/Screenshot_20201110-2249442.png)<figcaption>  
Value Iteration algorithm</figcaption></figure>VI also needs T and R matrices. But it can bypass the need to find the policy in each iteration. It initializes a random V(s) matrix with random Bellman function value for each state. Then for each state it finds the best action and updates the V(s) until all the V(s) are stable. This way it can quickly find the best policies for each state that stabilizes the V-matrix, instead of having to explicitly find the policy and then compute V(s) as in PI. It might be faster than PI for same iteration but may often take more iterations.

## Model-free Q-Learning 

<figure class="wp-block-gallery columns-1 is-cropped">- <figure>![](https://asifrehan.com/wp-content/uploads/2020/11/Screenshot_20201110-2305363-1.png)</figure>

</figure>Unlike PI and VI, QL is realistic that often the actual T and R matrices are not known in a real world problem. Instead an agent can only interact with the environment and try to update its impression about the system by updating its T and R matrix.

In QL, at each state, the agent takes a random action or the best action that maximizes the V(s). This is known as EXPLORATION vs EXPLOITATION controlled by a based on a parameter ε which determines whether the agent chooses to randomly explore a new action or take the best action from what is has seen**.** The agent takes random actions for probability ε and greedy action for probability (1-ε) If it does not explore in the beginning then it keeps taking the same decision based on its first action and gets stuck. So initially, more exploration is useful to make a rich experience of the environment. As the agent explores and takes random actions over and over, it can gradually become confident about its experience and may not need to explore as much. So, the parameter ε can be reduced gradually.

The Learning Rate parameter 0&lt; helps update the previous Q(s,a) value with the new value. Lower value makes convergence slow and too high of a alpha value makes it fluctuate the V(s) a lot.

## Dyna Q-Learning

Dyna is a variant to Q-Learning with intermediate hallucination step between each iteration. In Dyna, the previously learned Q matrix is used to replay the memory to take steps and accordinlgly learn/update the image of the system in the Q-matrix. Below is the algorithm from CS 7646 Machine Learning for Trading class from Georgia Tech.

<figure class="wp-block-image size-large">![](https://asifrehan.com/wp-content/uploads/2021/08/Screenshot-from-2021-08-27-15-24-09-1024x856.png)</figure>#### References: 

**Bellman Equation:** https://en.m.wikipedia.org/wiki/Markov\_decision\_process

**Policy Iteration and Value Iteration:** Mihaela van der Schaar, Reinforcement Learning: A brief introduction

**Q-Learning**: Sargur N. Srihari, University of Buffalo