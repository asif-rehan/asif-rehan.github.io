---
id: 531
title: 'Entropy in Information Theory'
date: '2020-12-06T21:13:41+00:00'
author: 'Asif Rehan'
excerpt: 'Entropy is the fundamental unit of information in Information Theory and is extensively useful in Machine Learning.'
layout: revision
guid: 'https://asifrehan.com/530-revision-v1/'
permalink: /530-revision-v1/
---

Entropy is the fundamental unit of information in Information Theory and is extensively useful in Machine Learning. This is defined as below

```
<pre class="wp-block-preformatted">H(x) = P(x1)*#bits(x1) +  P(x2) * #bits(x2) + ... + P(xn)*#bits(xn) 
```

Where the variable X is a discrete variable such that it can take these values, {x1, x2,…,xn}. Now there is a nice video explaining that to help us understand the concept

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