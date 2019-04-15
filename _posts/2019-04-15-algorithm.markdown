---
title: "GCD & LCM"
layout: post
date: 2019-04-15
image: /assets/images/markdown.jpg
headerImage: false
tag:
- jgam
- mathematics
- algorithm
- GCD
- LCM
category: blog
author: jgam
description: algorithm
---

## Greatest Common Divisor and Least Common Factor

One of the very basic mathematical terms people across is GCD and LCF. My written version of getting the GCD is to divide two numbers with prime numbers until the two numbers are no longer divisible. Then, multiply all those prime numbers to get the GCD. Getting LCF, however, is not that clear other than check if the two numbers have common factors and keep multiplying until the number is both divisible by two numbers.

## LCF

However, the formula for getting a Least common factor is to multiply two numbers and divide that number by GCD. this makes sense because in order to get LCF, we divide the two numbers wiht prime until they are not divisble and multiply all the prime numbers we used to divide each number and the numbers that are not divisble anymore. Simply put, this is just primenumbers * divisible numbers. We know that multiplying prime numbers to that number again will be just a multiplication of the two numbers.

The formula is now clear:

```javascript
LCF = (a * b) / gcd(a,b);
```

## GCD

Let's first represent easier way of getting GCD which is the brute force way.

```javascript
while(num < Math.min(a,b)){
    if (a % num == 0 && b % num == 0){
        max = num
    }
    num += 1;
}

return num;
```

The number returned there is simply a number that both divides a and b which becomes the Greatest Common Divisor. Any smarter way to do it?

## Euclidean Algorithm

Previously, we are looping through the minimum number of (a,b). Now we are going to loop through log(min(a,b)) with Eucledian Algorithm

Suppose that we have a and b and if a mod b (where we say b is smaller number of (a,b)), is eqaul to 0, we simply return b which becomes GCD. If a mod b is not equal to 0, we run b mod (a mod b) until we find the case where larger_number mod smaller_number is equal to 0. This way, we are emerely going through (b, a mod b, (a mod b)mod b), ...) This gives the complexity of O(log(N)).

[here is the link to Euclidean code!][https://github.com/jgam/javascript_web/fundamentals/HTML/]