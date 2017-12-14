---
layout: single
title: "Implement a Queue"
excerpt: "Create an efficient Queue<T> data structure."
tags: [interview,algorithm, data structure]
share: true
comments: true
---

## Problem

Write an efficient `Queue<T>` a FIFO datastructure offers `Enqueue` and `Dequeue` operations.

### Example

    var q = new Queue<int>();
    q.Enqueue(10);
    q.Enqueue(3);
    q.Dequeue();
    q.Enqueue(4);
    q.Enqueue(5);


## Analysis

**Queue** is a `FIFO` data structure; items added and removed in first-in0first-out order. In different word insertion and deletion happens on two different ends.

There are several methods to implement queues, each with different Time and Space Complexity. assuming that the data structure will support two main operations `Enqueue` and `Dequeue`

{% highlight csharp %}
    public interface IQueue<T>
    {
        void Enqueue(T item);
        T Dequeue();
    }
{% endhighlight %}

### Method 1 - Array based Queue

In this approach, we will use a fixed length array to store the queue elements, and two pointers, `head` to point at the first item in queue to be removed on calling `Dequeue` and `tail` pointing at the next empty position in the queue. with Every enqueue operation we will move the tail pointer to next empty position, and with every dequeue we will decrement the head pointor to point at the next item in line. we will also keep a size varible to assist in determinig if the queue is full by comparing to initial capacity.

{% gist 59cd0ec96819032369b9cd5d904d10f0 %}


| Operation | Time Complexity |
| --------- | --------------- |
| Enqueue   |       O(1)      |
| Dequeue   |       O(1)      |
| Remove    |       n/a       |

**Note** Arrays are fixed length data structure, dequeuing items from the queue will leave empty spots in the array not utilized which will lead to wasted space, a more efficient approach is to build a circular array, wraps around to the first position. The `Size` variable will be key in this approach since it will be used to determine if there are space left in the array to wrap around .
{: .notice--warning}

### Method 2 - LinkedList based Queue

**Linked List** is a very efficient and flexiable data structure, it will gives time complexity of `O(1)` for both adding and removing just like arrays. and also will enable us to change the queue items in the middle (although not usually needed operation).

**Note** Theoritically Arrays and LinkedLists will give you `O(1) head and tail inserts and deletes which in turns works very well for implementing a queue. But practically the overhead of an array is much less than linkedlist. Array is much more efficient data structure in memroy than a linkedlist.
{: .notice--warning}


{% gist f56acaa71ee416eea22c7fdc1a336677 %}

**Notice** using LinkedList to store data internally for the queue, enabled me to implmement `Remove(T item)` method, the method will run in O(K) where k number of elements iterated until match found.
{: .notice--warning}

| Operation | Time Complexity |
| --------- | --------------- |
| Enqueue   |       O(1)      |
| Dequeue   |       O(1)      |
| Remove    |       O(k)      |

### Bouns - Implement a Queue using two stacks

This is not a usual method to implement queues since it's not efficent for both Time and Space Complexity! but it's a fun problem to play with. if we are given two `Stack<T>` how can we implement a queue. `Stack` is the oppsite data strucuture of queue. Last-in-First-Out or **LIFO** 

We will use one Stack for `Enqueue` operation, which will be very fast operation `O(1)` , and we will use the other stack to handle `Dequeue` this will make the operation more costly in terms of time complexity. here are the steps:

* If enqueue and dequeue stacks are emtpy then queue is empty return `default(T)`
* If dequeue stack has values then `pop` value from dequeue stack and return it.
* if dequeue stack has no values
  * while enqueue stack is not empty, `pop` items from enqueue stack and `push` to dequeue stack
* `pop` item from dequeue stack

{% gist b0a37afebc57bf6bc7aaa37cb3ea41eb %}

| Operation | Time Complexity |
| --------- | --------------- |
| Enqueue   |       O(1)      |
| Dequeue   |       O(k)      |
| Remove    |       n/a       |


_Happy Coding!_