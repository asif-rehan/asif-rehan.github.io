---
id: 527
title: 'Merge Sort (Draft)'
date: '2020-12-03T21:07:54+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/482-autosave-v1/'
permalink: /482-autosave-v1/
---

```
<pre class="wp-block-code">```java
public class MergeSort{
	
	public void sort(int[] a){
		sort(a, 0, a.length -1); 
	}

	private void sort(int[] a, int i, int j) {
		if (i < j) {
			int pivot_point = i + (j-i)/2;
			sort(a, i, pivot_point);
			sort(a, pivot_point+1, j);
			merge(a, i, pivot_point, j);
		}		
	}

	private void merge(int[] a, int leftStart, int leftEnd, int rightEnd) {
		//Arrays merged =new ArrayList<Integer>();
		int leftIndex = leftStart;
		int rightIndex = leftEnd+1;
		int tempIndex = 0;
		//create a new storage location for the values to copy
		int[] temp = new int[rightEnd-leftStart+1]; 
		// Compare from the beginning of the two parts, pick the smaller between 
		// left and right components. Stop when either the end of left or right is reached 
		while (leftIndex <= leftEnd && rightIndex <= rightEnd) {
			if (a[leftIndex] <= a[rightIndex]) {
				temp[tempIndex++] = a[leftIndex++];
			} else {
				temp[tempIndex++] = a[rightIndex++];
			}
		}
		// if more items left in left part, right was smaller, then copy them over
		while (leftIndex <= leftEnd) {
			temp[tempIndex++] = a[leftIndex++];
		}
		//do the same but for the right part
		while (rightIndex <= rightEnd) {
			temp[tempIndex++] = a[rightIndex++];
		}
		//now copy the temp storage into the original array
		for (int i = 0; i < temp.length; i++) {
			a[leftStart++] = temp[i]; 
		}
				
	}
}
```
```