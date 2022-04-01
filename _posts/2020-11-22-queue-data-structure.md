---
id: 460
title: 'Queue Data Structure'
date: '2020-11-22T23:52:32+00:00'
author: 'Asif Rehan'
excerpt: 'Discussion on the implementation of queue data structure'
layout: post
guid: 'https://asifrehan.com/?p=460'
permalink: /queue-data-structure/
categories:
    - Algorithms
tags:
    - 'Data Structure'
    - Queue
---

The common data Queue is an intuitive simple data structure. While multiple implementation techniques are suitable for this, LinkedList based implementation is probably the simplest. It should have an internal Node object which will form the nodes in the queue. Also the Queue class should have a few methods:

1. addToEnd or Enqueue
2. removeFromFirst or dequeue
3. peek
4. isEmpty

You can find the [implementation here in GitHub](https://github.com/asif-rehan/data-structure-and-algorithms/blob/master/src/StackQueue/QueueImplementation.java)

```
<pre class="wp-block-code">```
package practiceJava;

import java.util.NoSuchElementException;

public class QueueImplementation<T> {
	private static class QueueNode<T>{
		private T data;
		private QueueNode<T> next;
		
		public QueueNode(T data) {
			this.data = data;
		}
	}
	private QueueNode<T> first;
	private QueueNode<T> last;
	
	public void addToQueue(T data) {
		QueueNode<T> node = new QueueNode<T>(data);
		//add to end of queue
		if (this.last != null) {
			this.last.next = node;
		}
		last = node; //update last pointer
		//now check if queue was empty so this is the first one 
		if (first == null) {
			first = last;
		}
	}

	public T removeFromFirst() {
		if (first == null) throw new NoSuchElementException();
		T firstData = this.first.data;	//return from first for FIFO
		//fix the first
		first = first.next;
		//now also fix the last pointer
		if (first==null) {
			this.last = null;
		}
		return firstData;	
	}
	
	public T peek() {
		if (this.first == null) throw new NoSuchElementException();
		return first.data;
	}

}

```
```