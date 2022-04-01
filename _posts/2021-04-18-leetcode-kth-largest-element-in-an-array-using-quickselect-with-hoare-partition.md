---
id: 649
title: 'LeetCode: Kth Largest Element in an Array using QuickSelect with Hoare Partition'
date: '2021-04-18T16:35:06+00:00'
author: 'Asif Rehan'
layout: post
guid: 'https://asifrehan.com/?p=649'
permalink: /leetcode-kth-largest-element-in-an-array-using-quickselect-with-hoare-partition/
categories:
    - Algorithms
---

Find Kth Largest Element in an Array is a problem which can be solved using e.g. QuickSort in O(nlogn) time and then pick the k-th element in the sorted array. Another way is to sort it using QuickSelect in O(n) times. The solution below beats 100% Java submissions on LeetCode for runtime.

## QuickSelect

QuickSelect is a sorting algorithm that uses partitioning scheme like Hoare’s or Lomuto’s. It finds the k-th smallest value in O(n) time. It uses divide and conquer technique. It divides the space using partition function and then recursively sorts the left or right part until it finds the partition.

```
<pre class="wp-block-code">```java
private void quickSelect(int left, int right){
    if (left < right) {
        int p = partition(left, right);
        if (kSmallest <= p) quickSelect(left, p);
        else {
          quickSelect(p+1, right);
        }    
    }
}
```
```

Notice if (kSmallest &lt;= p), then we know the `nums` array is partitioned from `left to p` which has values smaller than the values on the right portion from indices `p+1 to right`. So we only recursively sort the left.

If that is not the case, then we can sort on the right. But we cannot stop if p==kSmallest like in Lomuto’s partition because Hoare’s does not ensure that the value at the partition is the final position of the number.

## Hoare’s Partitioning Scheme

Hoare’s partitioning is shown below. This partitioning scheme is much faster than Lomuto’s. There are plenty of online resources on this most of them are confusing in the one on Wikipedia. [I wrote piece here on QuickSort](https://asifrehan.com/quick-sort-draft/) that could help.

```
<pre class="wp-block-code">```java
private int partition(int left, int right){

        int p = (left+right)/2;
        int pVal = nums[p];
        int i = left - 1;
        int j = right + 1;
        while(true){
            do {
                i++;
            } while( nums[i] < pVal);
            do {
                j--;
            } while (nums[j] > pVal);
            if(i<j){
                swap(i,j);
            } else{
                return j;
            }
        }
    }
```
```

## Solution: [Kth Largest Element in an Array](https://leetcode.com/explore/interview/card/top-interview-questions-medium/110/sorting-and-searching/800/)

The solution below beats 100% Java submissions on LeetCode for runtime.

```
<pre class="wp-block-code">```java
public class KthLargestElement {
    int kSmallest;
    int[] nums;

    public int findKthLargest(int[] nums, int k) {
        this.nums = nums;
        this.kSmallest = nums.length-k;
        quickSelect(0, nums.length-1);
        return nums[kSmallest];
    }

    private void quickSelect(int left, int right){
        if (left < right) {
            int p = partition(left, right);
            
            if (kSmallest <= p) quickSelect(left, p);
            else {
                quickSelect(p+1, right);
            }    
        }
    }
    private int partition(int left, int right){

        int p = (left+right)/2;
        int pVal = nums[p];
        int i = left - 1;
        int j = right + 1;
        while(true){
            do {
                i++;
            } while( nums[i] < pVal);
            do {
                j--;
            } while (nums[j] > pVal);
            if(i<j){
                swap(i,j);
            } else{
                return j;
            }
        }
    }

    private void swap(int i, int j){
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```
```