---
title: "bit manipulation"
layout: post
date: 2019-03-04
image: /assets/images/markdown.jpg
headerImage: false
tag:
- jgam
- cracking the coding interview
- bit manipulation
- bit
- algorithm
star: true
category: blog
author: jgam
description: bit manipulation
---

## Bit Manipulation
Two's complement and negative numbers represent some of the important concepts. Computers typically store integers in two's complement representation. A positive number is represented as itself while a negative number is represented as the two's complement of its absolute value (with a 1 in its sign bit to indicate that a negative value.)

The binary representation of -K (negative K) as a N-bit number is '1'+str(2^(N-1)-K).

Simply, the first number in two's complement represents 0 - positive & 1 - negative.

## Arithmetic and logical right shift
Arithmetic right shift essentially divides by two since we shift all the values to the right by filling the first bit by the original sign value (same sign).

Logical right shift shifts all the values to the right while the filling the first bit by the opposite (either 0 or 1) value of the original sign value.

##Interview Questions
[Here is the answers of interview questions!](https://github.com/jgam/crackingthecoding/tree/master/chpt5)