---
id: 735
title: 'Union-Find (aka Disjoint Set) Data Structure'
date: '2021-12-09T20:28:00+00:00'
author: 'Asif Rehan'
excerpt: 'Very quick summary of Union-Find or  Disjoint Set data structure'
layout: post
guid: 'https://asifrehan.com/?p=735'
permalink: /union-find-aka-disjoint-set-data-structure/
categories:
    - Algorithms
tags:
    - algorithms
    - 'Data Structure'
    - Programming
---

If you are already not familiar with the Union-Find data structure, check out this [simple tutorial](https://leetcode.com/discuss/general-discussion/1072418/Disjoint-Set-Union-(DSU)Union-Find-A-Complete-Guide) to understand the data structure. The images help a lot.

## Naive Implementation without Optimizations

The worst time complexity for `find()` or `union()` is O(n) since it may need to run through the whole chain of parents. So in the worst case, m operations can take O(mn) time.

## Optimizations

#### **Union-by-size**

Modify `union()` to make the worst-case time of Θ(log n).

#### **Path compression**

`find()` has an amortized time nearly Θ(1)

#### **With both Union-by-size + Path compression**

Worst-case time complexity is **Θ(m α(m, n))**. for m&gt;n operations, where n is the number of elements in the Union-Find tree.

Now, **α(m, n)** is constant when amortized over a big number of operations. So this turns the time complexity of m operations is just **O(m)** so each union or find operation is just O(1) on average!