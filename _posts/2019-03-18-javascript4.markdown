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

Functions that operate on other functions, either by taking them as arguments or by returning them, are called *higher-order functions.* Since we have already seen that functions are regular values, there is nothing particularly remarkable about the fact that such functions exist. The term comes from mathematics, where the distinction between functions and other values is taken more seriously.

Higher-order functions allow us to abstract over *actions*, not just values. They come in several forms. For example, we can have functions that create new functions.

```javascript
function greaterThan(n){
    return m => m > n;
}

let greaterThan10 = greaterThan(10);//function that creates new function
console.log(greaterThan10(11));//true
```

And we can have functions that change other functions.

```javascript
function noisy(f){
    return (...args) => {
        console.log("calling with", args);
        let result = f(...args);
        console.log("called with", args, ", returned", result);
        return result;
    };
}
noisy(Math.min)(3,2,1);//calling with [3,2,1]
//called with [3,2,1], returned 1
```

There is a built-in array method, forEach, that provides something like a for/of loop as a higher-order function.

```javascript
["A", "B"].forEach(l => console.log(l));
```

## Script Data Set

One area higher-order functions shine is data processing. The example data set contains some pieces of information about the 140 scripts defined in Unicode. The binding contains an array of objects, each of which describes a script.

Here is an example of binding.
```javascript
{
    name: "Coptic",
    ranges: [[994, 1008], [11392, 11508], [11513, 11520]],
    direction: "ltr",
    year: -200,
    living: false,
    link: "https://en.wikipedia.org/wiki/Coptic_alphabet"
}
```

Such an object tells us the name of the script, the Unicode ranges assigned to it, the direction in which it is written, hte origin time, whether it is still in use, and a link to more information. The direction may be "ltr" for left to right, "rtl" for right to left, or "ttb" for top to bottom.

The ranges property contains an array of Unicode character ranges, each of which is a two-element array containing a lower bound and an upper bound. Any character codes within these ranges are assigned to the script. The lower bound is inclusive (code 994 is a Coptic chatacter), and the upper bound is non-inclusive (code 1008 isn't)

## Filtering Arrays

To find the scripts in the data set that are still in use, the following function might be helpful. It filters out the elements in an array that don't pass a test.

```javascript
function filter(array, test){
    let passed = [];
    for(let element of array){
        if(test(element)){
            passed.push(element);
        }
    }
    return passed;
}

console.log(filter(SCRIPTS, script => script.living));//-> [{name: "Adlam", ...}, ...]
```

The function uses the argument named test, a function value, to fill a "gap" in the computation-the process of deciding which elements to collect.

Note how the filter function, rather than deleting elements from the existing array, builds up a new array with only the elements that pass the test. This function is pure. It does not modify the array it is given. Like forEach, filter is a standard array method. The example defined the function only to show what it does internally. From now on, we will use it like this instead:

```javascript
console.log(SCRIPTS.filter(s=> s.direction == "ttb"));
// -> [{name: "Mongolian", ...}, ...]
```

## Transforming with Map

The map method transforms an array by applying a function to all of its elements and building a new array rom the returned values. the new array will have the same length as the input array, but its content will have been mapped to a new form by the function.

Say that we wnat a SCRIPTS filtered with names only:

```javascript
function map(array, transform){
    let mapped = [];
    for (let element of array){
        mapped.push(transform(element));
    }
    return mapped;
}

let rtlScripts = SCRIPTS.filter(s => s.direction == "rtl");
console.log(map(rtlScripts, s=> s.name));
//-> ["Adlam", "Arabic", "Imperial Aramaic", ...]
```
Like forEach and filter, map is a standard array method.

## Summarizing with Reduce

Another things is to compute a single value from an array. Our recurring example, summing a collection of numbers, is an instance of this. Another example is finding the script with the most characters.

The higher-order operation that represents this pattern is called *reduce*(sometimes also called *fold*). It builds a value by repeatedly taking a single element from the array and combining it with the current value. When summing numbers, you'd start with the number zero and, for each element, add that to the sum.

The parameters to reduce are, apart from the array, a combining function and a start value. This function is a little less straightforward than filter and map, so take a close look at it:

```javascript
function reduce(array, combine, start){
    let current = start;
    for(let element of array){
        current = combine(current, element);
    }
    return current;
}

console.log(reduce([1,2,3,4], (a,b) => a+b, 0));//-> 10

```

Note that the standard array method reduce has an added convenience. If your array contains at least one element, yo uare allowed to leave off the start argument. The method will take the first element of the array as its start value and start reducing at the second element.

To use reduce (twice) to find the script with the most characters, we can write something like this:

```javascript
function characterCount(script){
    return script.ranges.reduce((count, [from, to]) => {
        return count + (to - from);
    }, 0);
}

console.log(SCRIPTS.reduce((a, b) => {
    return characterCount(a) < characterCount(b) ? b : a;
}));// -> {name: "Han"}

```

The characterCount cunction redsuces the ranges assigned to a script by summing their sizes. Note the use of destructuring in the parameter list of the reducer function. The second call to reduce then uses this to find the largest script by repeatedly comparing two scripts and returning the larger one.

The Han script has more than 89,000 characters assigned to it in the Unicode standard, making it  by far the biggest writing system in the data set. Han is a script(sometimes) used for Chinese, Japanese, and Korean text. Those languages share a lot of characters, though they tend to write them differently. The (U.S.-based) Unicode Consortium decided to treat them as a single writing system to save character codes. This is called *Han unification* and still makes some people very angry.
