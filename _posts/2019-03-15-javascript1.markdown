---
title: "Javascript?"
layout: post
date: 2019-03-15
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

## Code Chrysalis
It is very **important decision** in my life

## Javascript

### several concepts
1. type coercion - type automatically gets changed
2. Environment - the collection of bindings when a program starts. （also referred as a language standard)
3. control flow - when program runs, the statements are executed as if they are a story, from top to bottom.

### Functions
* Each binding has a **scope**, which is the part of the program in which the binding is visible. There are types of scope : global, local
* Even if global and local variables have same variable names, they are considered **different.**
*  In a relationship with local and global scopes, we have a concept called, **scope chain.** Inner functions can access variables outside of the inner functions but the vice-versa can't be allowed. Expanding on this concept, the inner functions keep looking at outer scope to find the variable and this happening is called **scope chain.**
*  Scope is created not only when the functions are called but when **declared.** Lexical scoping is when declaring the functions for the first time, the variables within functions will refer the places that are near the scope to them. Example is the following
```javascript
var name = 'zero';
function log() {
  console.log(name);
}

function wrapper() {
  var name = 'nero';
  log();
}
wrapper();
```
-> this prints out 'zero' instead of 'nero'. What is the reason? Because when function log was declared, the closest variable called name was var name = 'zero' and even if it looks that the closest name variable is 'nero' within function wrapper, it is not. Physically closest to the function declaration is the key.If you want to make 'nero' to be printed, you need to change the global variable name by removing var in front of 'nero'.

## Call Stack
```javascript
function greet(who) {
  console.log("Hello " + who);
}
greet("Harry");
console.log("Bye");
```

A run through this program goes roughly, the call the greet causes control to jump to the start of that function(line 1) The function calls console.log, which takes control, does its job, and then returns control to line 2. There it reaches the end of the greet function, so it returns to the place that called it, which is line 4. The line after that calls console.log again. After that returns, the program reaches its end.

The place where the computer stores this context is the **call stack.** In the following example, the call stack is at line 4. The current stack is stored on top of this stack and when function returns, it removes the top context from the stack and uses that context to continue execution.

When the stack grows too big, the computer will return messages like "out of stack space" or "too much recursion." 

## Optional Arguments

Javascript is extremely broad-minded about the number of arguments you pass to a function. If you pass too many, the extra ones are ignored. If you pass too few, the missing parameters get assigned the value undefined.

The downside of this is that it is possible-likely, even-that you will accidentally pass the wrong number of arguments to functions. And no one will tell you about it.

The upside is that this behavior can be used to allow a function to be called with different numbers of arguments. For example, this minus function tries to imitate the - operator by acting on either one or two arguments.

## Execution Context

When you run a program, global context is crteated and this **global context** is an environment that takes care of all the other contexts and it is closed when the program ends.

There is a **function context** which is created whenever the functions are called.

There are four rules of context.
1. global context is created then function context is created every time the funcion is called
2. when context is being created, variable objects(arguments, variables, scope chain, this) are created
3. After context is being created, the function gets executed. The variables used by functions find their values within the functions and outer side of scopes following the **scope chain**.
4. After the function exection is finished, the specific context vanishes(except for closures.) When page ends, the global context vanishes.

Let's explore more on contexts and closure in the following post!


## Chapter1 Exercises
[Chapter1 exercises](https://github.com/jgam/EloquentJavascript)