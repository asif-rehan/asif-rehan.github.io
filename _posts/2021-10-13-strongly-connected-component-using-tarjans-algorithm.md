---
id: 709
title: 'Strongly Connected Component using Tarjan&#8217;s Algorithm'
date: '2021-10-13T03:57:31+00:00'
author: 'Asif Rehan'
layout: post
guid: 'https://asifrehan.com/?p=709'
permalink: /strongly-connected-component-using-tarjans-algorithm/
categories:
    - Algorithms
tags:
    - algorithms
    - 'directed graph'
    - graph
    - Java
    - 'strongly connected component'
---

## Kosaraju’s vs Tarjan’s

Kosaraju’s algorithm finds the Topological Sorting of the original directed graph. For this, it uses DFS. Next it reverses the graph and runs DFS on the topologically sorted vertices. So it takes two DFS though the time complexity is O(|V|+|E|).

Tarjan’s algorithm, on the other hand, only uses one DFS but uses some extra tracking variables to maintain a stack. This stack helps find loops which for SCC.

## Tarjan’s Algorithm:

First, watch this video by [William Fiset](https://www.youtube.com/watch?v=wUgWX0nc4NY). Then check out Wikipedia pseudocode [here](https://en.wikipedia.org/wiki/Tarjan%27s_strongly_connected_components_algorithm#The_algorithm_in_pseudocode).

The following code implements it in Java.

```
<pre class="wp-block-code">```
import java.util.*;

public class TarjanSCC {
    List<Integer>[] g;
    boolean[] visited;
    int[] low;
    int[] index;
    Stack<Integer> stack;
    boolean[] onStack;
    private int count;
    List<List<Integer>> allSCC;

    private List<List<Integer>> SCC(List<Integer>[] graph){
        this.g = graph;
        allSCC = new ArrayList<>();
        low = new int[graph.length];
        index = new int[graph.length];
        stack = new Stack<>();
        onStack = new boolean[graph.length];
        visited = new boolean[graph.length];

        for (int i=0; i<graph.length; i++) {
            if (!visited[i]) {
                DFS(i);
            }
        }
        return allSCC;

    }
    void DFS(int v) {
        low[v] = index[v] = count++;
        visited[v] = true;
        onStack[v] = true;
        stack.push(v);
        for (Integer w: g[v]) {
            if (!visited[w]) {
                DFS(w);
                low[v] = Math.min(low[v], low[w]);
            } else if (onStack[w]) {
                low[v] = Math.min(low[v], index[w]);
            }
        }
        if (low[v] == index[v]) {
            List<Integer> scc = new ArrayList<>();
            int x;
            do {
                x =  stack.pop();
                onStack[x] = false;
                scc.add(x);
            } while (x != v);
            System.out.println(scc);
            this.allSCC.add(scc);
        }
    }
    public static void main(String[] args) {
        List<Integer>[] g = new List[8];
        g[0] = Arrays.asList(new Integer[]{1});
        g[1] = Arrays.asList(new Integer[]{2});
        g[2] = Arrays.asList(new Integer[]{0});
        g[3] = Arrays.asList(new Integer[]{4,7});
        g[4] = Arrays.asList(new Integer[]{5});
        g[5] = Arrays.asList(new Integer[]{0,6});
        g[6] = Arrays.asList(new Integer[]{0,2,4});
        g[7] = Arrays.asList(new Integer[]{3,5});
        TarjanSCC tarjanSCC = new TarjanSCC();
        System.out.println(tarjanSCC.SCC(g));

    }

}
```
```

## Result: 

There are three SCC’s as below:

```
<pre class="wp-block-code">```
[[2, 1, 0], [6, 5, 4], [7, 3]]
```
```