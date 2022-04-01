---
id: 584
title: 'Neural Network Differentiation'
date: '2021-01-16T01:09:29+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/583-revision-v1/'
permalink: /583-revision-v1/
---

To differentiate the loss function in a Neural Network, there are four options

1. **Manual differentiation**: It is labor intensive and often it is hard to calculate the closed form solution especially for complex function
2. **Symbolic differentiation:** Like manual, it is also hard for complex function
3. **Numerical differentiation**: Can handle complex function but may cause numerical issues
4. **Automatic differentiation**: In Deep Learning, most libraries use automatic differentiation