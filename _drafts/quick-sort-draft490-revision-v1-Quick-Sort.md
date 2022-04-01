---
id: 646
title: 'Quick Sort'
date: '2021-04-18T17:22:31+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/490-revision-v1/'
permalink: /490-revision-v1/
---

This class implements a QuickSort algorithm using Hoare Paritioning scheme. This partitionining scheme is slightly harder to implement but is more efficient than the Lamuto partitioning scheme as it does three times fewer swaps on average \[[Wikipedia](https://en.wikipedia.org/wiki/Quicksort)\].

- Avg Time-Complexity: O(nlogn)
- Worst Time-Complexity: O(n^2)
- Space complexity: O(1)

## Understanding Hoare Partition Intuitively

After spending quite some on the two, this StackExchange post nailed the key idea of Hoare Partition. [Kartikey Gupta wrote](https://cs.stackexchange.com/questions/81045/how-does-hoares-quicksort-work-even-if-the-final-position-of-the-pivot-after-p),

> “Lomuto divides the array into *three* parts; elements smaller than the pivot, the pivot, elements greater than the pivot. I think Hoare looks at things differently. He divides the array into *two* parts; elements smaller than the pivot, **elements equal to or greater than the pivot**. One of the traps that I fell into was that Lomuto’s partition returns the final position of the pivot, whereas Hoare’s partition **returns the position just before the final position of the pivot.** This is why Lomuto then quick sorts from `lo` to `p-1`, whereas Hoare quick sorts from `lo` to `p`. Another inference that can be drawn is that if Hoare’s `partition` returned `i` instead of `j`, we’d then divide the array into two parts- from `lo` to `i-1` and from `i+1` to `hi`, just like Lomuto did. And it only took me 4 hours to understand that.” \[[cs.stackexchange.com](https://cs.stackexchange.com/questions/81045/how-does-hoares-quicksort-work-even-if-the-final-position-of-the-pivot-after-p)\]

## Implementation in Java 

```
<pre class="wp-block-code">```java
public class QuickSortHoare{

    int[] arr;
    public QuickSortHoare(int[] arr){
        this.arr = arr;
    }

    private void sort(int i, int j) {
		if (i < j) { 	
			int p = partition(i, j);
			sort(i, p);
			sort(p+1, j);
		}
	}
    private void sort(){
        sort(0, arr.length-1);
    }
    
    private int partition(int left, int right) {
        int pivot = (left+right)/2;
        int pivotValue = arr[pivot];
        int i = left-1;
        int j = right+1;
        while(true){
            do {
                i++;
            } while( arr[i] < pivotValue);
            do {
                j--;
            } while( arr[j] > pivotValue );

            if (i<j) {
                swap(i, j);
            } else {
                return j;
            }
        }
    }
    private void swap(int i, int j){
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
```
```

## Resources

A good reference is [here by Michael Cotterell](https://gist.github.com/mepcotterell/4065154#:~:text=QuickSort%20Algorithm&text=Determine%20the%20midpoint%20of%20your,%2C%20lo%2C%20hi)%20).) however it returns the low pointer from the partitioning which is requires that the recursive sorting is done on \[low: partition-1\] and \[partition+1: high\]