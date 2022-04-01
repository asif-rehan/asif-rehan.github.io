---
id: 682
title: 'Three-way Partition/Sort an Array'
date: '2021-04-29T18:18:30+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/679-revision-v1/'
permalink: /679-revision-v1/
---

```
<pre class="wp-block-code">```
public class threeWayPartitionSort{
    public void sortColors(int[] nums, int a, int b) {
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