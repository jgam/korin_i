---
title: "Linked Lists"
layout: post
date: 2019-02-26
image: /assets/images/markdown.jpg
headerImage: false
tag:
- jgam
- cracking the coding interview
- Linked Lists
- algorithm
star: true
category: blog
author: jgam
description: Linked Lists
---

## Linked Lists 링크드 리스트
A linked list is a data structure that represents a sequence of nodes. Each node points to the next node in the linked list. A doubly linked list gives each node pointers to both the next node and the previous node.

A linked list does not provide constant time access to a particular index within the list. This means that if you'd like to find the Kth element in the list, you will need to iterate through K elements.

The benefit of a lined list is that you can add and remove items from the beginning of the list in constant time.

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