---
id: 300
title: 'Finding x in an Infinite Array'
date: '2020-06-23T04:16:20+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/296-revision-v1/'
permalink: /296-revision-v1/
---

This is a programming problem where the given array *A* is of infinite length and we have to find the position of a value *x* in it. The first *n* values are sorted and after *n-th* number, all remaining values in the array are None. For example: *A= \[1, 3, 5, 100, 102, 1050, 1061, None, None, None, …\]*. But the catch is that we do not know the value of *n* here to directly run binary search in an *O(log n)* time complexity. This is an interesting [Divide and Conquer](https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm) problem.

So in my solution below, I gradually take a wider step up from checking just one element from the beginning of this infinite array and check if the last value in that window is big enough to capture *x*, which indicates we have covered enough length to capture the first *n-th* values. At each step, I double the window size.   
  
Then when we have found the window withing which either *x* should reside, or we hit None, we run binary search within A\[i,j\]. The example below assumes x is guaranteed to be in the array.

```
<pre class="wp-block-code">```
 def binary_search(i, j, x):    
     mid = int((i+j) / 2)
     mid_val = A[mid]
      
     ind = None

     if mid_val == x:
         ind = mid    
     elif mid_val is None or mid_val > x:
         ind = binary_search(i, mid, x) 
     elif mid_val < x:
         ind = binary_search(mid, j, x)
     return ind
        
def find_x_in_infinite_array(A, x):
    i = 0
    k = 0
    while True:
        j = i + 2 ** k
        j_val = A[j]
        
        if j_val is None or j_val > x:
            index = binary_search(i, j, x)
            break
        i = j
        k = k + 1    
```
```