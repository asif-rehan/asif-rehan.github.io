---
id: 343
title: 'Topologically Sorting a DAG'
date: '2020-06-26T23:23:17+00:00'
author: 'Asif Rehan'
layout: post
guid: 'https://asifrehan.com/?p=343'
permalink: /topologically-sorting-a-dag/
categories:
    - Algorithms
---

In Directed Acyclic Graphs (DAG), there are no cycles. So it is simple to find the connected components just by sorting the vertices by post-order visit number in decreasing order after one run of DFS. The run time for DFS is again *O(|V|+|E|)*