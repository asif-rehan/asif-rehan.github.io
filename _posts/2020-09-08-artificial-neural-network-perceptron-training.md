---
id: 382
title: 'Artificial Neural Network: Perceptron Training'
date: '2020-09-08T07:25:00+00:00'
author: 'Asif Rehan'
layout: post
guid: 'https://asifrehan.com/?p=382'
permalink: /artificial-neural-network-perceptron-training/
categories:
    - Algorithms
    - OMSCS
tags:
    - 'Artificial Neural Network'
    - 'Machine Learning'
    - Perceptron
---

There could be two types of training algorithms for the weights for a neuron.

First is to minimize the error between predicted y\_hat and y. Here y\_hat = boolean(activation &gt;= threshold). This type of perceptron-based learning

- works best for linearly separable data and
- guarantees finite iterations.

Second type is Gradient Descent algorithm which minimizes the error between the activation function value, . It has the similar nature as Least Square Regression. It is robust because it uses calculus. We need to differentiate based on activation function, because it has weights which makes it differentiable. On the other hand, perceptron-based error function is not differentiable w.r.t. weights. This is why we need to use a beautiful function like sigmoid function which looks like a step function, continuously differentiable with a nice differential form.