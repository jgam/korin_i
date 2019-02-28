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

Queue is useful in breadth-first search or in implementing a cache. For example, we used a queue to sort a list of note nodes that we need to process. Each time we process a node, we add its adjacent nodes to the back of the queue. This allows us to process nodes in the order in which they are viewed.

### graph
We have weighted graph and unweighted graph. Weighted means there exists directions whereas the unweighted graph exists no directions.

As the graph is undirected each edge is stored in both incident node adjacent sets. Here is the code followed by:
```python
graph = {'A': set(['B','C']),
        'B': set(['A','D','E']),
        'C': set(['A', 'F']),
        'D': set(['B']),
        'E': set(['B','F']),
        'F': set(['C','E'])}
```
The picture form of the above code is the following:

### Depth-First Search
it explores vertices down each branch before backtracking. This property allows the algorithm to be implemented succintly in both interactive and recursive forms.
```python
def dfs(graph, start):
    visited, stack = set(), [start]
    while stack:
        vertex = stack.pop()
        if vertex not in visited:
            visited.add(vertex)
            stack.extend(graph[vertex] - visited)
    return visited

dfs(graph, 'A')#{E,D,F,A,C,B}
```

###Breadth First Search
Before taking details of BFS and DFS, one of the data structures called graph needs to be gone over.

Now BFS uses Queue which is a FIFO.

```python
def bfs(graph, start):
    visited, queue = set(), [start]
    while queue:
        vertex = queue.pop(0)
        if vertex not in visited:
            visited.add(vertex)
            queue.extend(graph[vertex] - visited)
    return visited

bfs(graph, 'A') # {'B', 'C', 'A', 'F', 'D', 'E'}
```
##Interview Questions
[Here is the answers of interview questions!](https://github.com/jgam/crackingthecoding/tree/master/chpt2)