---
title: "Higher-order functions?: Part2"
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

## Reduce

What do we do when computing a single value from the array? Summing a collection of numbers, is an instance of this. Another example is finding the script with the most characters.

The higher-order operation that represents this pattern is called *reduce*(sometimes also called fold). It builds a value by repeatedly taking a single element from the array and combining it with the current value. When summing numbers, you'd start with the number zero and, for each element, add that to the sum.

The parameters to *reduce* are, apart from the array, a combining function and a start value. This function is a little less straightforward than *filter* and *map*, so take a close look at it:

```javascript
function reduce(array, combine, start){
    let current = start;
    for (let element of array){
        current = combine(current, element);
    }
}

console.log(reduce([1,2,3,4], (a,b)=> a+b, 0));
// -> 10
```

The standard array method reduce, which of course corresponds to this function, has an added convenience. If your array contains at least one element, you are allowed to leave off the start argument. Here is the example:

```javascript
console.log([1,2,3,4].reduce((a,b) => a+b));//here a is always the total number and b is each element
```

Using reduce to find the script with the most characters, we can write something like this:

```javascript
function characterCount(script){
    return script.ranges.reduce((count, [from, to]) => {//same thing, count is 0 to begin with and it adds the diffence of the array consistantly until the end of the array and starts from 0 index
        return count + (to - from);
    }, 0);//0 doesn't have to be here?
}

console.log(SCRIPTS.reduce((a,b) => {
    return characterCount(a) < characterCount(b) ? b : a;
}));
//-> {name: "Han", ...}
```

The code above probably was the hardest concept for me to understand. Let's look at the first function, characterCount(script).

First of all what is script? script was an input object that contained name, rnages, directions, and etc. Basically the information about specific scripts Now this function specifically finds ranges...why? Because it wants to count the number of characters in those specific scripts. Now, the return in the function uses reduce(). Here we have count and [from, to]. These two things are input to the function "=>" in parenthesis. Of course, count starts from 0 (this was tough to guess) and keeps adding "to - from" which is the difference, the number of characters in ranges. The reduce function's second argument is 0 which demonstrates the index it starts from.

Now, we know that characterCount is the function that counts a character by lokking at ranges of script. In console.log, we use reduce to SCRIPTS and taking a,b as scripts. This makes sense since we are comparing ranges in characterCount. In the return, we have if characterCount of latter is bigger, return b, else return a. Again, a is the current and b is each index.

A little note about reduce!

**Reduce** takes four arguments:

1. Accumulator(acc)
2. Current Value(cur)
3. Current Index(idx)
4. Source Array (src)

Note that other factors are default values (0 or start) when aren't passed in.