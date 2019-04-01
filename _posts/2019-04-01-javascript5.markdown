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

Above function called "repeatLog" is an abstraction of calling something N times. Now, what if we want to do something other than printing numbers? Because doing something can be represented as a function(data type) and funtions are just values, we can pass our action as a function value.

```javascript
function repeat(n, action){
    for (let i = 0; i < n; i++){
        action(i);
    }
}

repeat(3, console.log);
//0
//1
//2
```

Here we passed in console.log as an action but we can simply create a function with a different way of writing function!

```javascript
let labels = [];
repeat(5, i => labels.push('Unit ${i+1}'));// this is calling the function and a variation from repeat(3, console.log); from above.
```

This is structured a little like a for loop - it first describes the kind of loop and then provides a body. However, the body is now written as a function value, which is wrapped in the parenthese of the call to repeat. This is why it has to be closed with the closing brace and closing parenthesis. In cases like this example, where the body is a single small expression, you could also omit the braces and write the loop on a single line.

## Higher-Order Functions

Functions that operate on other functions, either by taking them as arguments or by returning them, are called *higher order functions*. Since we have already seen that functions are regular values, there is nothing particularly remarkable about the fact that such functions exist. The term comes from mathemtacis, where the distinction between functions and other values is taken more seriously.

Higher order functions allow us to abstract over actions, not just values. They come in several forms. For example, we can have functions that create new functions. This is different from abstractions because in abstractions, we merely changed the values, *kinds* of functions such as console.log. Now, we can change the actions which is not the abstraction function itself but the actual actions of those functions. (basically, creating new functions as our tastes.)

```javascript
function greterThan(n){
    return m => m>n;// here is the HOF where we created new action of comparing m to n where m is the input of the function.
}
let greaterThan10 = greaterThan(10);
console.log(greaterThan10(11));
// -> true
```

Now, we can have functions that change other functions.

```javascript
function noisy(f){
    return (...args) => {
        console.log("calling with", args);
        let result = f(...args);
        console.log("called with", args, ", returned", result);
        return result;
    };
}

noisy(Math.min)(3,2,1);
// -> calling with [3,2,1]
// -> called with [3,2,1], returned 1
```

What happened with this part of code? We know that Math.min returns the minimum of object which is a group of numbers. However, we got other nice logs with Math.min. This is what Higher order functions play in. Because, noisy wraps math.min with the input(object), we can write new functions with ...args and add any other actions while applying the original actions on the ...args. Now, let's take a look at new types of control flow!

```javascript
function unless(test, then){
    if (!test) then();
}

repeat(3, n => {
    unless(n%2 == 1, () => {
        console.log(n, "is even");
    });
});

//-> 0 is even
//-> 2 is even
```

The repeat function was declared earlier and was simply looping over number(first argument) of times and does actions(second argument). When calling repeat, we called new function called unless which checks for the condition and runs the second argument (function).

Another simple note is that there exists a built-in array method, **forEach**, that provides something like a for/of loop as a higher-order function.

```javascript
["A", "B"].forEach(l => console.log(l));
// -> A
// -> B
```

## Filtering Arrays

To find the scripts in the data set that are still in use, the following function might be helpful. It filters out the elements in an array that don't pass a test.

```javascript
function filter(array, test){
    let passed = [];
    for (let element of array){
        if(test(element)){
            passed.push(element);
        }
    }
    return passed;
}

console.log(filter(SCRIPTS, script => script.living));

```

The function uses the argument named test, a function value, to fill a "gap" in the computation-the process of deciding which elements to collect.

Note how the filter function, rather than deleting elements from the existing array, builds up a new array with only the elements that pass the test. This function is pure. It does not modify the array it is given. Likf forEach, filter is a standard array method. The example defined the function only to show what it does internally. From now on, we will use it like this instead:

```javascript
console.log(SCRIPTS.filter(s => s.direction == "ttb"))//this creates a new array that has its direction is equal to "ttb"
```