---
title: "Arrays and Strings"
layout: post
date: 2019-02-25
image: /assets/images/markdown.jpg
headerImage: false
tag:
- jgam
- cracking the coding interview
- arrays
- strings
star: true
category: blog
author: jgam
description: Arrays and Strings
---

## 해쉬 테이블 Hash Tables
A datastructure that maps keys to values for highly efficient lookup. To retrive the value pair by its key, you find the key then compute the run time to find the value in a key(if it is a list, the runtime is N.)

**Worst Case Runtime** O(N)

**average Runtime** O(1)

## ArrayList & Resizable Arrays
I use python and in python, the size of array is automatically resized whereas in Java, arrays are fixed length. **The size is defined when you create the array**
Let's take a look at details of the resizing!

When the array is full, the array doubles in size is the conventional way of resizing. This doubling takes O(n) time, but happens so rarely that its amortized inserition time is still O(1)

**Why amortized insertion gives O(1) rather than O(n)?**

For example, after resized, we have an array of size N. Let's see how this array became to have a size of N

final capacity increaes -> n/2 elements to copy

previous capacity increase -> n/4 elements to copy

previous capacity increase -> n/8 elements to copy

.

.

.

second capacity increase -> 2 elements to copy

first capacity increase -> 1 element to copy


Therefore, we only have 1 + 2 + ... + N/4 + N/2 which is less than N.


This is less than O(N)

**worst case runtime** O(N)

**average case runtime** O(1)


## Interview Questions
[Here is the answers of interview questions!](https://github.com/jgam/crackingthecoding/tree/master/chpt1)