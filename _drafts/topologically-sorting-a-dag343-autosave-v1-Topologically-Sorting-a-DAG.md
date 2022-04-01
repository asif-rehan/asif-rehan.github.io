---
id: 346
title: 'Topologically Sorting a DAG'
date: '2020-06-26T23:23:30+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/343-autosave-v1/'
permalink: /343-autosave-v1/
---

In Directed Acyclic Graphs (DAG), there are no cycles. So it is simple to find the connected components just by sorting the vertices by post-order visit number in decreasing order after one run of DFS. The run time for DFS is again *O(|V|+|E|)*