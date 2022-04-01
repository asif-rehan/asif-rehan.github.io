---
id: 471
title: "LeetCode#94:\t Binary Tree Inorder Traversal"
date: '2020-11-24T20:11:00+00:00'
author: 'Asif Rehan'
layout: post
guid: 'https://asifrehan.com/?p=471'
permalink: /leetcode94-binary-tree-inorder-traversal/
categories:
    - Algorithms
tags:
    - algorithms
    - 'BInary Tree'
    - 'Binary Tree Traversal'
    - Inorder
    - 'Inorder Traversal'
    - LC
    - LeetCode
    - Traversal
    - Tree
---

First check out the [problem description here on LeetCode](https://leetcode.com/problems/binary-tree-inorder-traversal/).

## The Solution

This is marked as a medium difficult problem. However if you know what in-order traversal does, it is a very simple problem. Here I just added a helper `traverse()` method.

All the trick is done in the few lines inside the function. It checks if the current node is null, then it skips. Else it runs the same method recursively on the left child first, then it actually adds the current node’s value to the list called `result`. Then it proceeds to the right child just like left one.

```
<pre class="wp-block-syntaxhighlighter-code">class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        return traverse(root, new ArrayList<Integer>()); 
    }

    private List<Integer> traverse(TreeNode node, List<Integer> result){
        if (node==null) return result;        
        traverse(node.left, result);        
        result.add(node.val);        
        traverse(node.right, result);
        

        
        return result;
        
    }
}
```

## Result

This solution beats 100% of the previous solutions by runtime and 99.62% by memory! Wooho!

<figure class="wp-block-image size-large">![](https://asifrehan.com/wp-content/uploads/2020/11/image-2-1024x415.png)</figure>