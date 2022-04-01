---
id: 412
title: 'How To Compute Reconstruction Error for Random Projection'
date: '2020-10-30T03:28:19+00:00'
author: 'Asif Rehan'
layout: post
guid: 'https://asifrehan.com/?p=412'
permalink: /how-to-compute-reconstruction-error-for-random-projection/
categories:
    - Algorithms
    - OMSCS
tags:
    - algorithms
    - 'Artificial Intelligence'
    - 'Dimensionality Reduction'
    - 'Machine Learning'
    - Python
---

[Random Projection](https://en.wikipedia.org/wiki/Random_projection) is an interesting Dimensionality Reduction technique. You may choose to create a random projection for 1,2,3,..,n dimensional projections. Now how to tell which one is best?

So you would need to calculate loss of data due to this reduction in data size.

```
<pre class="wp-block-preformatted"># data has this shape:  row, col = 4898, 11 
random_projection = SparseRandomProjection(n_components=5)

random_projection.fit(data)
components =  random_projection.components_.toarray() # shape=(5, 11) 
p_inverse = np.linalg.pinv(components.T) # shape=(5, 11) 

#now get the transformed data using the projection components
reduced_data = random_projection.transform(data) #shape=(4898, 5) 
reconstructed= reduced_data.dot(p_inverse)  #shape=(4898, 11) 
assert  reduced_data.shape ==  reconstructed.shape
error = mean_squared_error(data, reconstructed)
```