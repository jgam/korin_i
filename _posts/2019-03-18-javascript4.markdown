---
title: "Objects and arrays?"
layout: post
date: 2019-03-18
image: /assets/images/markdown.jpg
headerImage: false
tag:
- jgam
- Linux
- Java script
- full stack
- Low level
category: blog
author: jgam
description: javascript
---

# Higher Order Functions

```javascript
console.log(sum(range(10,10)));
```

When looking at the above code, one can easily guess what each of those methods do. (Ofcourse, it will take some time to compute the actual number unless you are genius!)

The defintion of this vocabulary (the functions sum and range) will still involve loops, counters, and other incidental details. But because they are expressing simpler concepts than the program as a whole, they are easier to get right.

## Abstraction

In the context of programming, these kinds of vocabularies are called *abstractions.* Abstractions hide details and give us the ability to talk about problems at a higher level. When programming, we can't rely on all the words we need to be waiting for us in the dictionary. Thus, we might fall into the pattern of the first recipe-work out the precise steps the computer has to perform, one by one, blind to the higher-level concepts that they express.

It is useful skill, in programming, to notice when you are working at too low a level of abstraction.

## Abstracting Repetition

Plain functions, as we've seen them so far, are a good way to build abstractions. It is common for a program to do something a given number of times.
```javascript
for (let i = 0; i < 10; i++){
    console.log(i)
}
```

Can we abstract "doing something N times" as a function? Well, it's easy to write a function that calls console.log N times.

```javascript
function repeatLog(n){
    for(let i = 0; i < n; i++){
        console.log(i);
    }
}
```

**BUT** what if we do something other than loggin the numbers? since doing something can be represented as a function and functions are just values, we can pass our action as a function value.

```javascript
function repeat(n, action){
    for(let i =0; i < n; i ++){
        action(i);
    }
}


repeat(3, console.log);
// ->0
// ->1
// ->2
```

Similar to this, we don't have to pass a predefined function to repeat. Often, it is easier to create a funtion value on the spot instead.

```javascript
let labels = [];
repeat(5, i=>{//this part is creating a function value on the spot!
    labels.push('Unit ${i+1}');//function value
});
console.log(labels);// -> ["unit 1", "unit 2", "unit 3", "unit 4", "unit 5"]
```

Above is: it describes the kind of loop and then provides a body. However, the body is now written as a function value, which is wrapped in the parentheses of the call to repeat. This is why it has to be closed with the closing brace and closing parenthesis.

## HIGER - ORDER FUNCTIONS

The reason I bolded this part is because it is integral concept in javascript and I am still having troubles understanding them :(

