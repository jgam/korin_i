---
title: "math and logic puzzles"
layout: post
date: 2019-03-04
image: /assets/images/markdown.jpg
headerImage: false
tag:
- jgam
- cracking the coding interview
- logic puzzles
- math
- algorithm
star: true
category: blog
author: jgam
description: math and logic puzzles
---

## Checking if number is primes?
Rather than iterating up to the number N, we can iterate up to a square root of number N, to find any roots.
```python
for number in range(int(sqrt(N))):
	if N % number == 0:
		return False
return True
```

This lessens the number of loops that the logic has to go through.

## Generating a list of primes?