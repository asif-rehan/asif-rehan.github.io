---
id: 679
title: 'LeetCode#75: Sort Color using Three-way Partitioning'
date: '2021-04-28T20:15:00+00:00'
author: 'Asif Rehan'
layout: post
guid: 'https://asifrehan.com/?p=679'
permalink: /three-way-partion-sort-an-array/
categories:
    - Algorithms
tags:
    - algorithms
    - Java
    - LeetCode
---

The Sort Color problem expects to sort the array with values {0, 1, 2}. This can be done in a typical sorting algorithm in O(nlogn) time.   
A better approach is to use three-way partitioning of the array.

## Generic three-way partitioning

Below the threeWayPartitionSort() method splits the given an array, `[3,2,0,2,1,1,0,-1]`, into three parts, where values equal to or 0 come first, in the last part, values equal to or greater than 2 show up. Anything in between stays in between. So the final result is `[-1,0,0,   1,1,   2,2,3]`

```
<pre class="wp-block-code">```
public class threeWayPartitionSort{
    public void threeWayPartitionSort(int[] nums, int a, int b) {
        int l = 0;
        int r = nums.length - 1;
        int i = 0;
        while(i<=r){
            if (nums[i]<=a) {
                swap(nums, i++, l++);
            } else if (nums[i]>=b){
                swap(nums, i, r--);
            } else {
                i++;
            }
        
        }
    }
    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
    public static void main(String[] args) {
        nums = new int[]{3,2,0,2,1,1,0,-1};
        sortColors.sortColors(nums, 0, 2);
        System.out.println(Arrays.toString(nums));
    }
}
```
```

```
<pre class="wp-block-code">```java
Output: [-1, 0, 0, 1, 1, 2, 2, 3]
```
```

Notice, that there are three pointers, `i` for looping through the the array until it hits the right side marker `r`, and the left side marker `l`. Until `i` hits `r`, we keep looping, and each time a value below a is met it is swapped with left marker and both `l` and `i` are incremented. If a value greater than or equal to b is found, value at`r` and `i` are swapped, but only `r` is decremented, showing that the ride side is already partitioned. For value in between, just increment `i`. This expects, that if we move the larger values to the right region and smaller values in the left region, then every value in between should fall in the right middle region.

## Solution for Sort Color

Using the above approach the solution for the [Sort Color](https://leetcode.com/problems/sort-colors/) problem is below. This approach takes O(n) times.

```
<pre class="wp-block-code">```
class Solution {
        public void sortColors(int[] nums) {
        int l = 0;
        int r = nums.length - 1;
        int i = 0;
        while(i<=r){
            if (nums[i]==0) {
                swap(nums, i++, l++);
            } else if (nums[i]==2){
                swap(nums, i, r--);
            } else {
                i++;
            }
        
        }
    }
    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```
```