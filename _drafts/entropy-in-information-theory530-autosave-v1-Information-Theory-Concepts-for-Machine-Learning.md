---
id: 537
title: 'Information Theory Concepts for Machine Learning'
date: '2020-12-06T21:49:24+00:00'
author: 'Asif Rehan'
excerpt: 'Entropy is the fundamental unit of information in Information Theory and is extensively useful in Machine Learning. Let us introduce the concepts: Entropy, Joint Entropy, Mutual Information. '
layout: revision
guid: 'https://asifrehan.com/530-autosave-v1/'
permalink: /530-autosave-v1/
---

<figure class="wp-block-image size-large is-resized">![](https://upload.wikimedia.org/wikipedia/commons/1/15/Coin_Toss_%283635981474%29.jpg)<figcaption>ICMA Photos, CC BY-SA 2.0 <https://creativecommons.org/licenses/by-sa/2.0>, via Wikimedia Commons</figcaption></figure>Entropy is the fundamental unit of information in Information Theory and is extensively useful in Machine Learning. Let us introduce the concepts: Entropy, Joint Entropy, Mutual Information.

## Entropy

This is defined as below

```
<pre class="wp-block-preformatted">H(x) = P(x1)*#bits(x1) +  P(x2) * #bits(x2) + ... + P(xn)*#bits(xn) 
```

Where the variable X is a discrete variable such that it can take these values, {x1, x2,…,xn}. Now there is a nice video by Puskar Kolhe explaining to help us understand the concept

<figure class="wp-block-embed-youtube wp-block-embed is-type-video is-provider-youtube wp-embed-aspect-16-9 wp-has-aspect-ratio"><div class="wp-block-embed__wrapper"><iframe allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" frameborder="0" height="326" src="https://www.youtube.com/embed/QNua92rpp2Q?feature=oembed" title="Expected size of the message Quiz Solution - Georgia Tech - Machine Learning" width="580"></iframe></div></figure>Now again, the ones with higher probability may get a smaller bits assigned because we can reduce the data size by reducing the overall size, so the

```
<pre class="wp-block-preformatted"> P(xi)  = 1 / 2^(#bits(xi))
```

Which leads to,

```
<pre class="wp-block-preformatted">   #bits(xi)  =  logBase2(1/P(xi)) 
=> #bits(xi)  = -logBase2(P(xi))
```

This is how, the entropy definition becomes

```
<pre class="wp-block-preformatted">H(x) = SumOver_i[  -P(xi) * log(P(xi)) ]
```

## Joint Entropy

This measures the information contained in two discrete variables X, and Y

```
<pre class="wp-block-preformatted">H(X,Y) = SumOver_ij[  -P(xi,yj) * log(P(xi,yj)) ]
```

Here, `P(xi,yj)` is the joint probability of the variables X, Y. If the X,Y variables are independent, then the joint entropy becomes just the sum of the individual entropies as below since they do not tell anything when combined together!

```
<pre class="wp-block-preformatted">H(X,Y) = H(X) + H(Y)
```

## Conditional Entropy

This measures the additional information one gets when one of the variables, X is already known. Just swap the last portion with `P(yj|xi)`

```
<pre class="wp-block-preformatted">H(Y|X) = SumOver_ij[  -P(xi,yj) * log(P(xi|yj)) ]
```

If the X,Y variables are independent, then `H(Y|X)=H(Y)` because knowing X does not help figure out the distribution of Y.

## Mutual Information

This is probably the most useful metric to measure information between variables. The formula is below

```
<pre class="wp-block-preformatted">I(X,Y) = H(Y) - H(Y|X)
```

It tells that, what extra information is there from Y if we already know the conditional entropy of Y given X.

It is important to remember, for two independent variables X,Y, the mutual information `I(X,Y)=0`. If there is any dependency, then `I(X,Y)>0`