---
id: 593
title: 'Easy explanation of  Convolution vs Cross-Correlation in Convolutional Neural Networ (CNN)'
date: '2021-02-23T02:30:27+00:00'
author: 'Asif Rehan'
excerpt: "Convolution layer for CNN is explained in simple words\n"
layout: revision
guid: 'https://asifrehan.com/590-revision-v1/'
permalink: /590-revision-v1/
---

Convolution layer in Convolutional Neural Network (CNN) requires convolving the 2D image pixels in possibly 3 channels (RGB). But instead of convolving the image pixel with the kernel, it is more convenient to apply cross-correlation which is essentially a convolving with the kernel flipped by 180 degree. Why? Because convolution requires flipping the kernel and that leads to a complicated mathematical formula. However, if we apply cross-correlation instead, the formula is nicer, and intuitive.   
  
So essentially they are almost the same thing except the gradients of the kernels will still remain flipped!  
  
But that little difference does not matter! Because no matter which way the kernel is flipped, it can still learn the best kernel values for the operation. So turns out we can enjoy the little mathematical convenience without any issue!  
  
But there is more to that! It turns out, the derivative of the cross-correlation is the convolution!!! So it is going to be very useful in the backward pass of the CNN because we know how to convolve!! If we instead used convolution in the forward pass, the backward will be cross-correlation!  
  
Math is amazing!