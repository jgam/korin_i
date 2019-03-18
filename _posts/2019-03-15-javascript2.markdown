---
title: "More Javascript?"
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

Continuing from previous post...

```javascript
var name = 'zero'; // (1)변수 선언 (6)변수 대입
function wow(word) { // (2)변수 선언 (3)변수 대입
  console.log(word + ' ' + name); // (11)
}
function say () { // (4)변수 선언 (5)변수 대입
  var name = 'nero'; // (8)
  console.log(name); // (9)
  wow('hello'); // (10)
}
say(); // (7)
```
Take a quick look at this example code!

## Global Context

After global context is being created, following the steps, we have variable objects, scope chain, this coming in. The global context does not have arguments and variable is the current scope's variables.

## Function Context

At line 7, we have functino context called say function context while having global context that was previously created. Scope chain is say variable object and global variable object.

As you can see, in the function say, we have wow function and when we get to that line of statement, we knoe taht wow context is being created where the arguments is 'hello' and scope chain is wow function scope and global context scope. In more details, wow function's scope chain is not say functino context due to **lexical scoping.** However, it is wow function scope and global scope.

## Hoisting?

**Hoisting** is when you declare variables and run the program, the declaration part comes at the top. For example the following codes act as the same way:
```javascript
console.log(zero); // 에러가 아니라 undefined
sayWow(); // 정상적으로 wow
function sayWow() {
  console.log('wow');
}
var zero = 'zero';
```

Do you see why the above code runs without any problems? Take a look at this code

```javascript
function sayWow() {
  console.log('wow');
}
var zero;
console.log(zero);
sayWow();
zero = 'zero';
```

As you can see, due to the hoisting, all the declarations come top of the program.

```javascript
sayWow(); // (3)
sayYeah(); // (5) 여기서 대입되기 전에 호출해서 에러
var sayYeah = function() { // (1) 선언 (6) 대입
  console.log('yeah');
}
function sayWow() { // (2) 선언과 동시에 초기화(호이스팅)
  console.log('wow'); // (4)
}
```

This code, however, throws an error, why? In the global context, two variables exists: [{sayWow: Function}, 'sayYeah'] sayYeah is called even before it is referenced as a different way of expressing function. Therefore, it throws an error!

## Closure

The ability to treat functions as values, combined with the fact that local bindings are re-created every time a function is called, brings up an interesting questions.

What happens to local bindings when the function call that created them is no longer active?

```javascript
function wrapValue(n) {
  let local = n;
  return () => local;
}

let wrap1 = wrapValue(1);
let wrap2 = wrapValue(2);
console.log(wrap1());
// → 1
console.log(wrap2());
// → 2
```

## Recursion

Recursion is probably somewhat easy definition for most of the people. In javascript, Recursion usually takes 3 times longer than a for loop.

Why do we use recursion then?

Developers should not just look for efficiency. Also, most of the time efficiency does not matter too much since computers are just fast enough.

On top of that, the good reason is the code becomes more striaght forward and clean. Therefore we talked about recursion here and refreshed my mind a little bit.


## Chapter3 Exercises
[Chapter3 exercises](https://github.com/jgam/EloquentJavascript)

