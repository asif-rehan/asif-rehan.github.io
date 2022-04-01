---
id: 500
title: 'Quick Sort (Draft)'
date: '2020-11-29T17:31:53+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/490-revision-v1/'
permalink: /490-revision-v1/
---

This class implements a QuickSort algorithm using Hoare Paritioning scheme. This partitionining scheme is slightly harder to implement but is more efficient than the Lamuto partitioning scheme.

- Avg Time-Complexity: O(nlogn)
- Worst Time-Complexity: O(n^2)
- Space complexity: O(1)

## Implementation in Java 

```
<pre class="wp-block-code">```java
import java.util.ArrayList;

public class QuickSort {
	
        public void sort(ArrayList<Integer> A){
		sort(A, 0, A.size()-1);
	}

	private void sort(ArrayList<Integer> A, int i, int j) {
		if (i < j) { 	
			int p = partition(A, i, j);
			sort(A, i, p-1);
			sort(A, p+1, j);	
		}
	}

	private int partition(ArrayList<Integer> A, int i, int j) {
		
		int pivot_index = i + (j-i)/2; 	
		Integer pivot_value = A.get(pivot_index);	
		
		while (i < j) {		
			
			while (A.get(i) <  pivot_value) i++;
			
			while (A.get(j) > pivot_value ) j--;	
		        Integer temp = A.get(i);
     		        A.set(i, A.get(j));
		        A.set(j, temp);	
		}
		return i;
	}
}
```
```

## Testing

Now test a few cases and see if the implementation passes all of them

```
<pre class="wp-block-code">```java
import static org.junit.jupiter.api.Assertions.*;

import java.util.ArrayList;
import java.util.Arrays;

import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

class QuickSortTest {
	@BeforeEach
	void setUp() throws Exception {
	}
	
	
	@Test
	void testSort() {
		ArrayList<Integer> testArray = new ArrayList<>(Arrays.asList(100,10,1,5,50));
		
		QuickSort qs = new QuickSort();
		qs.sort(testArray);
		assertTrue(testArray.equals(new ArrayList<>(Arrays.asList(1,5,10,50,100) )));
	}
	
	@Test
	void testSortNoArray() {
		ArrayList<Integer> testArray = new ArrayList<>();
		QuickSort qs = new QuickSort();
		qs.sort(testArray);
		assertTrue(testArray.equals(new ArrayList<>()));
	}
	
	@Test
	void testSortBigArray() {
		ArrayList<Integer> testArray = new ArrayList<>(Arrays.asList(0, 50, Integer.MIN_VALUE, Integer.MAX_VALUE));
		QuickSort qs = new QuickSort();
		qs.sort(testArray);
		assertTrue(testArray.equals(new ArrayList<>(Arrays.asList(Integer.MIN_VALUE, 0, 50, Integer.MAX_VALUE))));
		
	}
	@Test
	void testSortSameArray() {
		int[] arr = new int[] {0, 50, 50,50,Integer.MIN_VALUE, Integer.MAX_VALUE};
		MergeSort ms = new MergeSort();
		ms.sort(arr);
		assertTrue(Arrays.equals(arr, new int[] {Integer.MIN_VALUE, 0, 50, 50, 50, Integer.MAX_VALUE}));
	}
}

```
```

## Resources

 A good reference is [here by Michael Cotterell](https://gist.github.com/mepcotterell/4065154#:~:text=QuickSort%20Algorithm&text=Determine%20the%20midpoint%20of%20your,%2C%20lo%2C%20hi)%20).)