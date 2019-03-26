---
title: "Sorting?"
layout: post
date: 2019-03-09
image: /assets/images/markdown.jpg
headerImage: false
python: true
tag:
- jgam
- cracking the coding interview
- python
- algorithm
- sorting
category: python
author: jgam
description: sorting
---

## Sorting ?
정렬은 (개인적으로) 알고리즘 중에 가장 큰 부분을 차지하는 알고리즘 기법 중 하나이다. 필자가 python을 주 언어로 쓰면서, 느꼈던 점이 array라는 data type을 굉장히 유연하게 사용한다는 점이다.

활용 기법도, 여러가지로 다양한데, 이를테면 array를 이용해서 hash map을 간편하게 생성한다 던지, array에 값들을 넣고 빼기에 아주 적합하고, 원하는 부분만 fetch하기에도 매우 용이하다.

이러한 점들이 python으로 하게끔 data science에서 제일 적합한 언어로 부각되어 지는 것 같다. 이번 블로그에서는, 기본적인 sorting algorithm을 훑어 볼려고 한다. 특히 이 시간에는 필자가 이미지외에

짤(?)들을 넣어볼 시도를 할 것이다. (frontend 실력(?)도 키워볼겸)

## bubble sort

* easiest algorithm
* Don't use it that often due to performance issues
* when arr[i] > arr[j](i < j), switch the position of both for each index

```python
def bubbleSort(alist):
    for loop_count in range(len(alist)-1, 0, -1):
        for idx in range(loop_count):
            if alist[idx] > alist[idx+1]:
                tmp = alist[idx]
                alist[idx] = alist[idx+1]
                alist[idx+1] = tmp
    return alist
```
* time complexity: O(N), O(N^2), O(N^2)
* space complexity: O(N)
  
## selection sort

* similar to bubble sort
* finding the largest value and place it at the end of the arr

```python
def selsectionSort(alist):
    for offset in range(0,len(alist)-1):

```
* time complexity: O(N^2), O(N^2), O(N^2)
* space complexity: O(N)

## Insertion Sort

* from 1 to N, set the index and go through index to place the value at right position less than index
```python
def insertinoSort(alist):
	start = time.time()
	for index in range(1, len(alist)):
		currentvalue = alist[index]
		position = index

		while position > 0 and alist[position-1] > currentvalue:
			alist[position]=alist[position-1]
			position = position - 1
	alist[position] = currentvalue
	curr_time = time.time() - start
	return alist, curr_time
```
* time complexity : O(N), O(N^2), O(N^2)

## Heap Sort

* Heap sort is a comparison based sorting technique based on Binary Heap data structure, similar to selection sort when we find the maximum element and place the maximum element at the end.
### What is binary heap?
Complete Binary Tree is a binary tree in which every level, except possibly the last, is completely filled, and all nodes are as far left as possible.

A Binary Heap is a complete binary tree where items are sorted in a special order such that value in a parent node is greater(or smaller) than the values in its two children nodes. The former is called as max heap and the latter is called min heap. The heap can be represented by binary tree or array.
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