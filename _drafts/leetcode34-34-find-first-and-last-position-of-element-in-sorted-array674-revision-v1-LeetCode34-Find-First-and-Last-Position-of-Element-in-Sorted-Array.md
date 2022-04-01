---
id: 678
title: 'LeetCode#34: Find First and Last Position of Element in Sorted Array'
date: '2021-04-29T18:15:37+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/674-revision-v1/'
permalink: /674-revision-v1/
---

This [LeetCode problem](https://leetcode.com/explore/interview/card/top-interview-questions-medium/110/sorting-and-searching/802/) is a great practice problem to implement a binary search for a value in a sorted array with duplicate values. It asks to find the indices of the first and start the occurrence of a value in the sorted array with possibly duplicate values.

It can be solved in a naive manner to search for the start and end in a linear runtime O(n). But a better solution is to use Binary Search which runs in O(logn) time.

A typical binary search method looks like this if the array has unique and sorted numbers.

```
<pre class="wp-block-code">```
private int binarySearch(int[] nums, int target, int l, int r) {
        int result = -1;
        while (l<=r){
            int mid = (l+r)/2;
            if(nums[mid]==target){
                return mid;
            } else if (nums[mid] < target) {
                l = mid + 1;
            } else {
                r = mid - 1;
            }
        }
        return result;
    }
```
```

But for this problem, the Binary Search requires a little modification because of the duplicates and also that we can design it in a way to look for not only the target value but also specifically search for the starting and ending occurrence. So check out the solution below.

```
<pre class="wp-block-code">```java
public class SearchForARange {
    public int[] searchRange(int[] nums, int target) {
        int[] res = new int[]{-1,-1};
        if (nums.length==0) return res;
        res[0] = binarySearchLeft(nums, target, 0, nums.length-1);
        if (res[0]>=0) {
            res[1] = binarySearchRight(nums, target, res[0], nums.length-1);
        }    
        return res;
    }

    private int binarySearchLeft(int[] nums, int target, int l, int r) {
        int result = -1;
        while(l<=r){
            int mid = (l+r)/2;
            if (nums[mid] == target){
                result = mid;
                r = mid-1;

            } else if (nums[mid] > target){
                r = mid - 1;
            } else {
                l = mid + 1;
            }
        } 
        return result;
    }

    private int binarySearchRight(int[] nums, int target, int l, int r) {
        int result = -1;
        while (l<=r){
            int mid = (l+r)/2;
            if(nums[mid]==target){
                result = mid;
                l = mid + 1;
            } else if (nums[mid] > target) {
                r = mid - 1;
            } else {
                l = mid + 1;
            }
        }
        return result;
    }
}
```
```

For understanding the logic, check out [this post](https://www.techiedelight.com/find-first-or-last-occurrence-of-a-given-number-sorted-array/).