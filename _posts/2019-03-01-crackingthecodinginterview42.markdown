---
title: "tres and graphs pt.2"
layout: post
date: 2019-03-01
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
description: trees & graphs2
---

**Continuing from previous post I want to start off with finishing trees and continnue on with Graphs!**

## Binary Heaps 바이너리 힙! (min heaps and max heaps)
Max-heaps are in descending order whereas Min-heaps are in ascending order.

A min-heap is a complete binary tree (that is, totally filled other than the rightmost elements on the last level) where each node is smaller than its children. The root, is the minimum element in the tree.

## min heap
The picture of min heap is the following

<div class="side-by-side">
    <div class="tocenter">
        <img class="image" src="{{ site.url }}/{{ site.minheap }}" alt="Alt Text">
        <figcaption class="caption">Photo by jgam CREDIT: cracking the coindg interview</figcaption>
    </div>
</div>

Two operations we are going to take a look is **Insert** and **extract Minimum element**

**Insert**

1. insert the element at the rightmost spot so as to maintain the complete tree property
2. "fix" the tree by swapping the new element with its parent, until we find an appropriate spot for the leement

This gives **O(log n)** time where n is the number of nodes in the heap

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


