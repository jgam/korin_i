---
title: "python: call by reference or value?"
layout: post
date: 2019-03-09
image: /assets/images/markdown.jpg
headerImage: false
tag:
- jgam
- cracking the coding interview
- python
- values
- reference
star: true
category: blog
author: jgam
description: python: call by reference or value
---

## Is Python a call by reference or value?
To answer this question, I want to briefly go over the definitions of call by reference and value.

Examples will make images in your head!

# Call by value
```python
a = 3

def example(a):
	a += 1

example()
print(a)
```
What is a, when we print it?
-> a = 3

This is an example of call by value because, we are not changing the value of a and merely call by a's value.

# Call by reference
```python
a= [1,2,3]

def example(a):
	a.append(4)

example(a)
print(a)
```
What is a, when we print it?
->a = [1, 2, 3, 4]

This is an example of call by reference because we are writing over what has been written in memory reference. As you see, **a** was originally [1,2,3] and inside the function, we appended 4 to it and that memory reference has been re-written. THerefore, when we print a we are calling for the reference of a.

# Conclusion
So what is python then? Simply python has attributes of both call by reference and call by value. Why? Python has evolved from other low-level languages such as c++ or Java and thses complex OS interactinv theories hae been fixed due to more human-friendly language politics. This, while being more human-friendly, actually lessens the OS memory and other efficiencies. (There always exists ups and downs!)

Therefore, we call python as call by objects. There exists **objects** in python and these objects are classified with different attributes called mutability. For example, as you saw in example, the integer value called a is immutable which means it can't be changed through other scope of functions. However, the list called a is immutable and can be changed any scope in the program.

This difference makes python so special but then alleviates efficiencies.