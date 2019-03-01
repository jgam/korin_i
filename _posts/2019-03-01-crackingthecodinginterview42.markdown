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

<div class="side-by-side">
    <div class="tocenter">
        <img class="image" src="{{ site.url }}/{{ site.minheap2 }}" alt="Alt Text">
        <figcaption class="caption">Photo by jgam CREDIT: cracking the coindg interview</figcaption>
    </div>
</div>

This gives **O(log n)** time where n is the number of nodes in the heap

**Extracting minimum element**

1. remove the minimum element and swap it with the last element in the heap
2. bubble down this element, swapping it with one of its children until the min-heap property is restored

<div class="side-by-side">
    <div class="tocenter">
        <img class="image" src="{{ site.url }}/{{ site.minheap3}}" alt="Alt Text">
        <figcaption class="caption">Photo by jgam CREDIT: cracking the coindg interview</figcaption>
    </div>
</div>

This gives **O(log n)** time where n is the number of nodes

##Graphs 그래프 (finally!)
A tree is actually a type of graph, but not all graphs are trees. Simply put, a tree is a connected graph without cycles. A graph is simply a collectino of nodes with edges between them.

Several rules of Graph
1. Graphs can be either directed or undirected. Directed edges are one way street and undirected edges are two-way street.
2. The graph might consist of multiple isolated subgraphs. If there exists a path between every pair of vertices, it is called a "connected graph."
3. The graph can also contain cycles. An "acyclic graph" is one without cycles.

<div class="side-by-side">
    <div class="tocenter">
        <img class="image" src="{{ site.url }}/{{ site.graph }}" alt="Alt Text">
        <figcaption class="caption">Photo by jgam CREDIT: cracking the coindg interview</figcaption>
    </div>
</div>

Now how to represent these graphs in programming language?

## Adjacency List
Every vertex stores a list of adjacent vertices. In an undirected graph, an edge like (a, b) would be stored twice: once in a's adjacent vertices and once in b's adjacent vertices.

## Adjacency Matrices
An adjacency matrix is an NxN boolean matrix ( where N is the number of nodes), where a true value at matrix[i][j] indicates an edge from node i to node j.(you can also use an integer matrix with 0s and 1s.)

In an undirected graph, an adjacency matrix will be symmetric since there is no directions and they are all considered in bounds and out bounds while a directed graph may not be.

It is general to say that Adjacency matrixes are less efficient because they have to go through all the nodes to identify a node's neighbors.

## Graph Search
Finally, we came to ways to methods (algorithms) of searching graph. There are **depth-first-search** and **breadth-first-search**. Simple implementation is described in the following picture.

<div class="side-by-side">
    <div class="tocenter">
        <img class="image" src="{{ site.url }}/{{ site.graph2 }}" alt="Alt Text">
        <figcaption class="caption">Photo by jgam CREDIT: cracking the coindg interview</figcaption>
    </div>
</div>

Let's compare them into a deeper level.

DFS is often preerred if we want to visit every node in the graph because DFS is a bit simpler. However, if we want to find the shortest path(or just any path) between two nodes, BFS is generally better. Consider representing all the friendships in the entire world in a graph and trying to find a path of frendhips between Ash and Vanessa.

Using BFS, we want to stay close to Ash as long as possible rather than going farther from Ash in case of DFS. Because these two algorithms are very important, I want to explore more on these two algorithms.

## DFS
We visit a node a and then iterate throuh each of a's neighbors. When visiting a node b that is a neighbor of a, we visit all of b's neighbors before going on to a's other neighbors. That is a exhaustively searches b's branch before any of its other neighbors.

## BFS
BFS is a bit less intuitive, and many interviewees struggle with the implmentation unless they are already familiar with it. The main tripping point is the assumption that BFS is recursive. It's not. Instead it uses a queue.

In BFS, node a visits each of a's neighbors before visiting any of their neighbors. You can think of this as searching level by level out from a. An iterative solution involving a queue usually works best.

## Bidirectional Search
It is used to find the shortest path between a source and destination node. It operates by essentially running two simultaneous breadth-first searches, one from each node. When their searches collide, we have found a path.

<div class="side-by-side">
    <div class="tocenter">
        <img class="image" src="{{ site.url }}/{{ site.graph2 }}" alt="Alt Text">
        <figcaption class="caption">Photo by jgam CREDIT: cracking the coindg interview</figcaption>
    </div>
</div>

The picture explains well with how to reduce the run time when we run two BFS from opposite directions. In traditional BFS, we want to find k nodes by the levels of the graph. This gives you run time of **O(2 ^ d)** where d is the number of levels.

Because we are doing this from two different points (the points for finding the shortest path), the run time reduces by number of levels by 2. Let's say for finding the shortest path between a and b, the levels we need to explore are 10. Since we are implementing BFS from each point, the run time is half of the level difference which is 5. Similarly, we are merely reducing the number of d(number of levels) by 2 which, in turn, gives **O(2^(d/2))**

##Interview Questions
[Here is the answers of interview questions!](https://github.com/jgam/crackingthecoding/tree/master/chpt4)