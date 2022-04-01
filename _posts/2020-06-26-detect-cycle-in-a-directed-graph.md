---
id: 350
title: 'Detect Cycle in a Directed Graph'
date: '2020-06-26T23:49:46+00:00'
author: 'Asif Rehan'
layout: post
guid: 'https://asifrehan.com/?p=350'
permalink: /detect-cycle-in-a-directed-graph/
categories:
    - Algorithms
---

A directed graph without any cycle is a Directed Acyclic Graph (DAG). If there is a cycle, then there will be a back edge, which goes backwards. For such edge(u,v), postorder number for *u* will be smaller than that of *v*, i.e. *post(u) &lt; post(v)*.   
So after DFS, if any edge satisfies *post(u) &lt; post(v)* , then there exists a cycle in the graph, so this is not DAG.

Time complexity *O(|V|+|E|)* + O(|V|) which finally becomes *O(|V|+|E|)*