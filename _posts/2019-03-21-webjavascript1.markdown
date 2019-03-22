---
title: "Web javascript"
layout: post
date: 2019-03-21
image: /assets/images/markdown.jpg
headerImage: false
tag:
- jgam
- javscript
- webdevelopment
- mdn
- basics
category: blog
author: jgam
description: Javascript Web
---

## 변수란?

```javascript
<button>Press me</button>

var button = document.querySelector('button');

button.onclick = function(){
    var name = prompt("What is your name?");
    alert("Hello " + name + ", nice to see you!");
}
```

보다 싶이, var name이라는 것을 통해 name이라는 변수를 생성해주고, 우리는 이것은 그냥 alert() 안에 pass in만 해주게 되면, 다이너믹하게 출력값이 바뀌는 것을 확인한다. 만약 변수가 없었다면? 이 세상에 존재하는 이름들을 전부가져와서 if & else 로 케이스를 만들어야 되지 않았을까?

그러면 이제, 변수의 종류에 대해서 얘기를 해볼려고 한다. 종류는 굉장히 심플하게 boolean, string, integer 그리고 array등이 있다. 이 부분은 너무 직관적이라 넘어 갈려고 한다.

## 지정되지 않은 타입

javascript는 loosely typed language 이다. 다른 언어와 달리 변수에 포함할 데이터의 유형을 지정할 필요가 없다. 예를 보자

```javascript
var myString = "Hello";
var intString = "123";
var realInt = 123;
```

보다 싶이, 숫자라도 double / single quotation marks로 string type이 되는것을 확인했다.

## arrays?

Creating an array goes like this:

```javascript
var shopping = ['bread', 'milk', 'cheese', 'hummus', 'noodle']
shopping;
```

Using this array is similar to pythonic grammar.

## Project Brief

The project Brief does the following:

1. Generate a silly story when the "Generate random story" button is pressed
2. Replaces the default name "Bob" in the story with a custon name, only if a custon name is entered into the "Enter custon name" text field before the generate button is pressed.
3. Converts the default US weight and temperature quantities and units in the story into UK equivalents if the UK radio button is checked before the generate button is pressed.
4. Will generate another random silly story if you press the button again( and again...)

The link is here!
[Project Brief](https://github.com/jgam/EloquentJavascript/)