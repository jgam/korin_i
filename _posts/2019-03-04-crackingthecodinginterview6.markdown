---
title: "Math and Logic Puzzles"
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
The Sieve of Eratosthenes is highly efficient way to generate a list of primes. It works by recognizing that all non-prime numbers are divisible by a prime number. We start with a list of all the number up through some value max.

1. cross of all numbers divisible by 2
2. look for the next prime(the next non-crossed off number(
3. croos off all numbers divisible by it))

```python
#list of primes
def list_of_primes(num_list):
	start = 4
	ret_list = [2,3]
	# start off with finding the number
	for i in range(start, num_list):
		#even number should be jumped
		if i % 2 == 0:
			continue
		else:
			#we know that the non-prime number is a divisible number by prime number
			for v in ret_list[1:]:
				print(i,v)
				if i % v != 0:
					if v == ret_list[-1]:
						ret_list.append(i)
					continue
				else:
					break
	return ret_list
```

##  Brainteaser
Including the primes and probabilities, we will always face brainteasers. What do we need to do when we face brainteasers?
### Develop Rules and Patterns
We have to find the ways to come up with the answers and it is totally due to the practices.
However, more importantly, we have to think about worst-case shifting.  A useful technique is to try to balance the worst case. If an early decision results in a skewing of the worst case, we can sometimes change the decision to balance out the worst case.

## Interview Questions
[Here is the answers of interview questions!](https://github.com/jgam/crackingthecoding/tree/master/chpt6)