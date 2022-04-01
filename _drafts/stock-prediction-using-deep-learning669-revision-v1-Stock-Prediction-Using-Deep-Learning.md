---
id: 670
title: 'Stock Prediction Using Deep Learning'
date: '2021-04-23T19:04:35+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/669-revision-v1/'
permalink: /669-revision-v1/
---

Recently have been looking into some stock market prediction libraries and repositories for our group project for [CS7643 Deep Learning](https://www.cc.gatech.edu/classes/AY2020/cs7643_fall/) at Georgia Tech. Previously I worked on traditional Machine Learning algorithms and Q-Learning algorithm from Reinforcement Learning for [CS7646: Machine Learning for Trading](https://omscs.gatech.edu/cs-7646-machine-learning-trading) commonly known as the “ML4T course”. My codes for ML4T is locked in this [private GitHub repo](https://github.com/asif-rehan/ML4T_Spring2020). But here I am sharing the research findings for applications of Deep Learning for stock prediction.

## Approaches

Traditional stock prediction can be seen as a time series regression problem where many many algorithms already exist. A naive approach could be classification/regression but time series is more robust approach.

However, for a regression stock prediction model, one needs to map the predicted stock price to BUY / SELL / HOLD action space. So classification probably makes more sense. But Reinforcement Learning really helps a lot because it can optimize the total gains.

## PyTorch Implementations

1. **Generic RNN, LSTM:** many resources available online
2. **Transformer+Attention:** This [Medium article](https://towardsdatascience.com/stock-predictions-with-state-of-the-art-transformer-and-time-embeddings-3a4485237de6) and its corresponding [GitHub repo](https://github.com/JanSchm/CapMarket/blob/master/bot_experiments/IBM_Transformer%2BTimeEmbedding.ipynb) applies Transformer and time embeddings which seems quite interesting
3. **Dual-stage Attention -RNN (DA-RNN):** The paper is here <https://arxiv.org/pdf/1704.02971.pdf> and the implemented model is available here in [this GitHub](https://github.com/ysn2233/attentioned-dual-stage-stock-prediction). A similar implementation in PyTorch is available here by [KurochkinAlexey](https://github.com/KurochkinAlexey/DA-RNN/blob/master/DARNN_NASDAQ.ipynb)
4. **Deep Reinforcement Learning:** Finally, this [FinRL](http://finrl.org/guide/overview.html) is an excellent library for applying Deep RL on stock prediction with demo and code examples to help you get started.

This is a work-in-progress note. So will update this as needed.