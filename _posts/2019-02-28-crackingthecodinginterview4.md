---
title: "tres and graphs"
layout: post
date: 2019-02-28
image: /assets/images/markdown.jpg
headerImage: false
tag:
- jgam
- cracking the coding interview
- trees
- graphs
- algorithm
star: true
category: blog
author: jgam
description: trees & graphs
---

## Trees
* tree is a datastructure composed of nodes
* The root node has zero or more child nodes
* Each child node has zero or more child nodes, and so on
* A node is called a "leaf" node if it has no children
---

## Binary Tree
A binary tree is a tree in which each node has up to two children. Not all trees are binary trees.

## Binary Search Tree
* A binary search tree is a binary tree in which every node fits a specific ordering property: **All left descendaents <= n < all right descendents**
* It is common that people assume when asked a tree question, the tree is a binary search tree

## Balanced Vs Unbalanced
Balanced tree really means something more like "not terribly imbalanced." It's balanced enough to ensure O(log n) times for insert and find, but it's not necessarily as balanced as it could be.
**balaced Tree examples: Red-black trees and AVL trees**

## Complete Binary Trees
A binary tree in which every level of the tree is fully filled, except for perhaps the last level. To the extent that the last level is filled, it is filled left to right


<div class="side-by-side">
    <div class="tocenter">
        <img class="image" src="{{ site.url }}/{{ site.bst }}" alt="Alt Text">
        <figcaption class="caption">Photo by jgam CREDIT: cracking the coindg interview</figcaption>
    </div>
</div>

## Full Binary Trees
A full binary tree is a binary tree in which every node has either zero or two children. No nodes have **only one** child.

<div class="side-by-side">
    <div class="tocenter">
        <img class="image" src="{{ site.url }}/{{ site.fbt }}" alt="Alt Text">
        <figcaption class="caption">Photo by jgam CREDIT: cracking the coindg interview</figcaption>
    </div>
</div>

## Perfect Binary Trees
A perfect binary tree is one that is both full and complete. All leaf nodes will be at the same level, and this level has the maximum number of nodes

<div class="side-by-side">
    <div class="tocenter">
        <img class="image" src="{{ site.url }}/{{ site.pbt }}" alt="Alt Text">
        <figcaption class="caption">Photo by jgam CREDIT: cracking the coindg interview</figcaption>
    </div>
</div>

## Binary Tree Traversal
Let us be comfortable implementing in-order, post-order, and pre-order traversal. the most common of these is in-order traversal.

```python

#Use this instead , a simple recursion ::

class Node:
    def __init__(self,key):
        self.left = None
        self.right = None
        self.val = key

def printInorder(root):
    if root:
        printInorder(root.left)
        print(root.val)
        printInorder(root.right)

def printPostorder(root):
    if root:
        printPostorder(root.left)
        printPostorder(root.right)
        print(root.val)

def printPreorder(root):
    if root:
        print(root.val)
        printPreorder(root.left)
        printPreorder(root.right)

# Driver code
root = Node(1)
root.left      = Node(2)
root.right     = Node(3)
root.left.left  = Node(4)
root.left.right  = Node(5)
print "Preorder traversal of binary tree is"
printPreorder(root)

print "\nInorder traversal of binary tree is"
printInorder(root)

print "\nPostorder traversal of binary tree is"
printPostorder(root)
```

##In order Traversal
This means to "visit"the left branch, then the current node, and finally, the right branch.

##Pre-Order Traversal
It visits the current node before its child nodes(hence the name "pre-order".)

##Post-Order Traversal
It visits the current node after its child nodes


This is the end of the first part of Trees and Graphs since as a python user, I do not have much exposure exploring this data structure and want to explore more graphs in details in the following part of Trees and Graphs
