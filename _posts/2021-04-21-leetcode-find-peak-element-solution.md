---
id: 661
title: 'LeetCode: Find Peak Element Solution'
date: '2021-04-21T19:57:13+00:00'
author: 'Asif Rehan'
layout: post
guid: 'https://asifrehan.com/?p=661'
permalink: /leetcode-find-peak-element-solution/
categories:
    - Algorithms
tags:
    - 100%
    - 'Binary Search'
    - Complexity
    - 'Find Peak Element'
    - Iterative
    - Java
    - LeetCode
    - Linear
    - Logarithmic
    - Programming
    - 'Programming Solution'
    - Recursive
    - Runtime
    - Space
    - Time
---

The Find Peak Element problem can be solved using a linear search in O(n) time and O(1) space. but it can be even better to solve it by binary search in O(log n) time complexity. But there can be two cases for binary search solution, the recursive solution creates stacks for each call and thus takes O(log n) space. On the other hand, the iterative solution takes O(1) space. So the iterative binary search solution is the best approach.

## Recursive Solution 

```
<pre class="wp-block-code">```java
public class FindPeakElement {
    int[] nums;
    public int findPeakElement(int[] nums){
        this.nums = nums;
        return search(0, this.nums.length-1);

    }
    private int search(int l, int r) {
        if(l==r) return l;
        int mid = (l+r)/2;
        if (nums[mid]>nums[mid+1]){
            return search(l, mid);
        } else return search(mid+1, r);
    }
}
```
```

## Iterative Solution

```
<pre class="wp-block-code">```java
public class FindPeakElement {
    int[] nums;
    public int findPeakElement(int[] nums){
        this.nums = nums;
        return searchIterative(0, this.nums.length-1);
    }

    private int searchIterative(int l, int r){
        while(l<r){
            int mid = (l+r)/2;
            if (nums[mid]>nums[mid+1]){
                r = mid;
            } else {
                l = mid+1;
            }
        }
        return l;
    }
```
```