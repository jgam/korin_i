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

# Data Structures: Objects and arrays

Objects and arrays are coming in handy because we want to group data.

## Arrays

We know what arrays are. And Javascript format of arrays are the following:

```javascript
let listOfNumbers = [2,3,5,7,11];
console.log(listOfNumbers[2]);//5
```

## Properties

Some expressions such as myString.length and Math.max are called **properties** For the first case, we accessed the length property of the value in myString. In the second case, we accessed the property named max in the Math object. (which is a collection of mathematics-related constants and functions.)

Almost all JavaScript values have properties. The exceptions are null and undefined. You will get an error when accessing a proprty of these values.

```javascript
null.length;//TypeError: null has no properties
```

## Methods

Both string and array objects contain, in addition to the length property, a number of properties that hold function values.

```javascript
let doh = "Doh";
console.log(typeof doh.toUpperCase);//-> function
console.log(doh.toUpperCase());//-> DOH
```

Every string has a toUpperCase property. When called, it will return a copy of the string in which all letters have been converted to uppercase. There exists toLowerCase, which acts in vice-versa.

Properties that contain functions are generally called **methods** of the value they belong to, as in "toUpperCase is a method of a string." The example below demonstrates two methods you can use to manipulate arrays:

```javascript
let sequence = [1, 2, 3];
sequence.push(4);
sequence.push(5);
console.log(sequence.pop());//->5
console.log(sequence)// -> [1,2,3,4]
```

These methods represent how to represent one of the data structures called, **"stack."**

## Objects

Values of the type object are arbitrary collections of properties. One way to create an object is by using braces as an expression.
```javascript
let day1 ={
    squirrel: false,
    events: ["work", "touched tree", "pizza", "running"]
};
console.log(day1.squirrel);//-> false
console.log(day1.wolf);//-> undefined
day1.wolf = false;
console.log(day1.wolf);//-> false
```

Inside the braces, there is a list of properties separated by commas. Each property has a name followed by a colon and a value. When an object is written over multiple lines, indenting it like in the example helps with readability. properties whose names aren't valid binding names or valid numbers have to be quoted.

```javascript
let descriptions = {
    work: "Went to work",
    "touched tree": "Touched a tree"
};

```

This means that braces have two meanings in javascrip. At the start of a statement, they start a block of statements. In any other position, they describe an object. Fortunately, it is rarely useful to start a statement with an object in braces, so the ambiguity between these two is not much of a problem.

Briefly, objects grasp values but other bindings and properties might be holding onto those same values. You may think of objects as octopuses with any number of tentacles, each of which has a name tattooed on it.

## Mutability

We saw that object values can be modified. The types of values such as numbers, strings, and booleans, are all immutable-it is impossible to change values of those types. You can combine them and derive new values from them, but when you take a specific string value, that value will always remain the same. The text inside it cannot be changed. If you have a string that contains "cat", it is not possible for other code to change a character in your string to make it spell "rat".

Objects, however, are mutable, causing a single object value to have different content at different times.

When we have two numbers, 120 and 120, we cna consider them precisely the same number, whether or not they refer to the same physical bits. With objects, there is a difference between having two references to the smae object and having two different objects that contain the same properties. Consider the following code:
```javascript
let object1 = {value: 10};
let object2 = object1;
let object3 = {value: 10};

console.log(object1 == object2);//true
console.log(object1 == object3);//false

object1.value = 15;
console.log(object2.value);//-> 15
console.log(object3.value);//->10
```

The object1 and object2 bindings grasp the same object, which is why changing object1 also changes the value of object2. They are said to have the same identity. The binding object3 points to a different object, which initially contains the same properties as object1 but lives a separate life.

When comparing objects with JavaScript's == operator, it compares by identity: it will produce true only if both objects are precisely the same value. Comparing different objects will return false, even if they have identitcal properties. There is no "deep" comparison operation built into JavaScript, which compares objects by contents.

## The Lycanthrope's Log
