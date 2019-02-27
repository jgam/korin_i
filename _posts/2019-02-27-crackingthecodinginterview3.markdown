---
title: "Stacks and queues"
layout: post
date: 2019-02-27
image: /assets/images/markdown.jpg
headerImage: false
tag:
- jgam
- cracking the coding interview
- stacks
- queues
- algorithm
star: true
category: blog
author: jgam
description: Stacks & queues
---

## Stacks and Queues 스택 과 큐
The stack data structure is precisely what it sounds like: a stack of data and uses LIFO(last in first out) ordering.

Stacks are useful in recursive algorithms.

The queue in other hands, uses FIFO (First in First out) ordering. Items are removed in a same order that they re added.

Queue is useful in breadth-first search or in implementing a cache. For example, we used a queue to sotre a list of note nodes that we need to process. Each time we process a node, we add its adjacent nodes to the back of the queue. This allows us to process nodesi n the order in which they are viewed.

#simple Breadth First Search
Before taking details of BFS and DFS, one of the data structures called graph needs to be gone over.

We have weighted graph and unweighted graph. Weighted means there exists directions whereas the unweighted graph exists no directions.

Now BFS uses Queue which means,
#simple s

#Creating a Linked List

```python
class Node:
    def __init__(self, dataval=None):
        self.dataval = dataval
        self.nextval = None

class SLinkedList:
    def __init__(self):
        self.headval = None

list1 = SLinkedList()
list1.headval = Node("Mon")
e2 = Node("Tue")
e3 = Node("Wed")
# Link first Node to second node
list1.headval.nextval = e2

# Link second Node to third node
e2.nextval = e3
```
As you can see, after inserting data to a node, we created an arrow that connects current node to the nexto ne.

#Deleting a Node from a Singly Linked List

```python

# Function to remove node
    def RemoveNode(self, Removekey):

        HeadVal = self.head

        if (HeadVal is not None):
            if (HeadVal.data == Removekey):
                self.head = HeadVal.next
                HeadVal = None
                return

        while (HeadVal is not None):
            if HeadVal.data == Removekey:
                break
            prev = HeadVal
            HeadVal = HeadVal.next

        if (HeadVal == None):
            return

        prev.next = HeadVal.next

        HeadVal = None

```

Not only deleting the data of a node, we need to connect the arrows so that list is connected smoothly.

#Runner Technique!
input
a1 -> a2 -> ... -> an -> b1 -> b2 -> b3 ... -> bn
output
a1 -> b1 -> a2 -> b2 -> a3 -> b3 .... -> an -> bn

You play with two pointers in a linked list. One pointer p1 move every two element while p2 moves every single element. Once P1 reaches the end of the list, p2 is at half of the linked list and move p1 to the front and start "weaving" the elements to get the likely output.

##Interview Questions
[Here is the answers of interview questions!](https://github.com/jgam/crackingthecoding/tree/master/chpt2)