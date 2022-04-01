---
id: 347
title: 'Connected Components in Graphs'
date: '2020-06-26T23:30:06+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/339-revision-v1/'
permalink: /339-revision-v1/
---

There can be three types of graphs here.

## 1. Undirected Graph

For undirected graphs, we can use Depth First Search (DFS) to find the connected component number for each vertex. The runtime is *O(|V|+|E|)*.

## 2. Directed Graph

Directed graphs can be of two types. Directed Acyclic Graphs (DAG) and General Directed Graphs. DAGs’s do not have cycles. In general directed graphs, cycles may exist.

So, for directed graph what we need to find is called **Strongly Connected Component**. In order to find it, first create a new graph where original edges are in reverse direction.

Next, run DFS on this reverse graph to find postorder numbers and order vertices in descending order. This first node is guranteed to be in a source SCC in the original graph.  
  
Next, starting from the first node above, run DFS and assign component number to each nodes. When all the connected nodes are visited from the first node, move to the second node.

Thus after two rounds of DFS, we can find SCC for a general directed graph.

Based on the DFS, the runtime is *O(|V|+|E|*).