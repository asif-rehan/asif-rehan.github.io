---
id: 475
title: 'Binary Tree Traversal'
date: '2020-11-25T22:26:55+00:00'
author: 'Asif Rehan'
layout: post
guid: 'https://asifrehan.com/?p=475'
permalink: /binary-tree-traversal/
categories:
    - Algorithms
---

A binary tree is one where each of its nodes has maximum two children nodes. These children are mostly known as Left and Right child.

<figure class="wp-block-image">![](https://upload.wikimedia.org/wikipedia/commons/thumb/3/38/Max-Heap.svg/240px-Max-Heap.svg.png)<figcaption>Figure: Binary Tree example from [Wikipedia](https://en.wikipedia.org/wiki/Binary_heap#Heap_operations)</figcaption></figure>## 1. In-order Traversal 

It goes from left child then current node then right child  
So for the given tree above it will be: `[2,17,7,19,3,100,25,36,1]`

```
<pre class="wp-block-syntaxhighlighter-code">public void inOrder(Node node){
   if (node==null) return;
   inOrder(node.left);  # repeat this on the left node
   visit(node);         # do something at current node
   inOrder(node.right); # now work on right node
}
```

## 2. Pre-order Traversal 

It first deals with current node and goes from left child then right child. So the pre-order traversal is: `[100,19,17,2,7,3,36,25,1] `

```
<pre class="wp-block-syntaxhighlighter-code">public void preOrder(Node node){
    if (node==null) return;
    visit(node);         # do something at current node
    preOrder(node.left);  # repeat this on the left node
    preOrder(node.right); # now work on right node
 }
```

## 3. Post-order Traversal 

 It recursively visit left child then right child, and only then the current node in the tree. So for this: `[2,7,17,3,19,25,1,36,100] `

```
<pre class="wp-block-syntaxhighlighter-code">public void postOrder(Node node){
    if (node==null) return;
    postOrder(node.left);  # repeat this on the left node
    postOrder(node.right); # now work on right node
    visit(node);           # do something at current node
 }
```

## Bonus: Level-order Traversal

Level-order traversal basically is Breadth-First Search (BFS) traversal of a tree. For a BFS, a queue data structure is useful. See the [queue implementation here](https://asifrehan.com/queue-data-structure/)

```
<pre class="wp-block-syntaxhighlighter-code">public ArrayList<Node> traverse(){		 
    ArrayList<Node> closed = new ArrayList<>();
    Queue<Node> open = new LinkedList<Node>();
    open.add(this.startNode);
    while (open.isEmpty() == false) {
	Node currentNode = open.poll();
	if (currentNode != null) {
	for (Node child : currentNode.getChildren()) {
	    if (child != null) open.add(child);
	} 
	closed.add(currentNode);			
    }
			
   }
return closed;
}
```