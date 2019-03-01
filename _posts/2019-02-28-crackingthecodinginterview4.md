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
        <figcaption class="caption">Photo by John Doe</figcaption>
    </div>
</div>


## Lists

### Ordered list

1. Item 1
2. A second item
3. Number 3

{% highlight raw %}
1. Item 1
2. A second item
3. Number 3
{% endhighlight %}

### Unordered list

* An item
* Another item
* Yet another item
* And there's more...

{% highlight raw %}
* An item
* Another item
* Yet another item
* And there's more...
{% endhighlight %}