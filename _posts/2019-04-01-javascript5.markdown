---
title: "Higher-order functions?"
layout: post
date: 2019-04-01
image: /assets/images/markdown.jpg
headerImage: false
tag:
- jgam
- higher-order functions
- Javascript
- full stack
- backend
category: blog
author: jgam
description: javascript
---

## Higher-Order Functions

First of all, lets take a look at these two sample codes!

```javascript
let total = 0, count = 1;
while (count <= 10){
    total += count;
    count += 1;
}
console.log(total);
```

```javascript
console.log(sum(range(1, 10)));
```

Which one is more likely to contain a bug? The second code seems to be fit more to the CRUD theory and less lkely to geterate errors because the code is intuitively very understandable. For example, sum and range determine that this is to get the sum of numbers from 1 to 10. These kinds of vocabularies are called **abstractions** and they *hide details and give users the ability to talk about problems at a higher(or more abstract) level.*

Now, lets move onto a real example with Abstract Repetition.

## Abstracting Repetition

It is common for a program to do something a given number of times and you can write a for loop for that, like this:
```javascript
for (let i = 0; i < 10; i ++){
    console.log(i)
}
```

Can we abstract "doing something N times" as a function? Well, it's easy to write a function that calls *console.log* N times.

```javascript
function repeatLog(N){
    for(let i = 0; i < n; i++){
        console.log(i)
    }
}
```

Above function called "repeatLog" is an abstraction of calling something N times.