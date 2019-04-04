---
title: "Higher-order functions?: Part2"
layout: post
date: 2019-04-04
image: /assets/images/markdown.jpg
headerImage: false
tag:
- jgam
- Review
- Javascript
- full stack
- backend
category: blog
author: jgam
description: javascript
---

## Defining a function

A function definition is a regular binding where the value of the binding is a function. Functions have a set of parameters (in this case, only x) and a body, which contains the statements that are to be executed when the function is called. The function body of a function created this way must always be wrapped in braces, even when it consists of only a single statement.

```javascript
const power = function(base, exponent){
    let result = 1;
    for(let count = 0; count < exponent; count++){
        result *= base;
    }
    return result;
}

console.log(power(2,10));
// -> 1024
```

This is regular way of declaring functions and as you can see the function takes in two parameters and whenever we call that function within two values, those automatically become parameters.

Now, the function can either return a value or not. Those functions that do not return anything are marked as undefined. Parameters to a function behave like regular binings, but their initial values are given by the *caller* of the function, not the code in the functino itself.

## Bindings and Scopes

Each binding has a scope, which is the part of the program in which the binding is visible. For bindings defined outside of any function or block, the scope is the whole program-you can refer to such bindings wherever you want.

```javascript
let a = 3
const b = 4
```

What is the difference of above two declarations? The difference is that const data types can be accessed anywhere while let can be accessed, following the rules of scopes.


## Back to functions

In javascript there are three ways to define functions.
```javascript
//regular function declaration
const hello = function(input){console.log("hello"+input);}

//shorter way of function declaration
function hello(input){
    console.log("hello"+input);
}

//arrow functions
input => {console.log("hello"+input)}

```

These 3 ways of declaring functions. One thing to note is that, second way of declaring function is the original way of declaration personally. Since I use lots of python. The first case, we set a variable "hello" equal to the function. What is the type of hello?

Interestingly, the type of hello is function. What does this refer to? The functions as values are allowed in javascript.

Another note is the last way, arrow functions. The arrow functions indicate that the variable is passed in as a parameter and if we have multiples, we need parenthesis wrapping around the list of inputs. What about a function without a parameter? we can just pass in empty list which is ().

## The Call Stack

```javascript
function greet(who){
    console.log("hello " + who);
}
greet("Harry");
console.log("Bye");

```

Let's look at the call stack. (It is very simple.) The control of the code starts at the first line but it is a mere declaration so moves on to greet("Harry"). Here the control sees the function call and looks for the function declaration and go inside, taking the parameter, does its actions and returns to wherever it was called. Now the greet("Harry") is completed and move to the next console.log("Bye").

not in function
   in greet
        in console.log
   in greet
not in function
   in console.log
not in function

This is an example of the calls tack and it is important to keep up with the call stack due to avoid errors such as "stack overflow."

## Closure

Being able to reference a specific instance of a local binding in an enclosing scope -- is called *closure*. A function that references bindings from local scopes around it is called a closure.

```javascript
function multiplier(factor) {
  return number => number * factor;
}

let twice = multiplier(2);
console.log(twice(5));
// → 10
```

What I said earlier is probably very **abstract**. It is fine because that definition is literally a book definition. What I understand closure is to reference local bindings even if the function of those bindings had been called. Let's break that exaple into parts.
```javascript
let twice = multiplier(2);
```

twice is a variable, a type of function and the function taking 2 as its input. what is the function multiplier? it is a function that takes in one input and returns **another function** as the following:
```javascript
return number => number * factor
```

After return, this is a arrow function which is the third way of declaring function so the function multiplier returns function that passes factor as that returned function's outer scope's variable. Now getting back to the declaration above, twice is a new function as following:
```javascript
number => number * 2
```

Now going back to the whole example, we are finally calling console.log() on twice, passing in 5 as its input.
```javascript
5 => 5 * 2
```

Now the return value should be 10 and this is what is happening. Summing up, what is the closure in this? The closure is how when console.log(twice(5)) is called, the ability to access factor which is 2 and previously called. This is a closure and is very helpful because it not only frees people from having to worry about lifetimes of bindings but also makes it possible to use function values in some creative ways.



