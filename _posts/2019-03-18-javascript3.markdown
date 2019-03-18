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

Correlation is a measure of dependence between statistical variables. A statistical variable is not quite the same as a programming variable. In statistics you typically have a set of measurements, and each variable is measured for every measurement. Correlation between variables is usually expressed as a value that ranges from -1 to 1. Zero correlation means the variables are not related. Positive one means they are identical and negative one means they are opposites. However, both cases demonstrate perfectly relevent cases.(one is true while the other is false.)

To compute the measure of correlation between two Boolean variables, we can use the *phi coefficient.* This is a formula whose input is a frequency table containing the number of times the different combinations of the variables were observed. The output of the formula is a number between -1 and 1 that describes the correlation.

<div class="side-by-side">
    <div class="tocenter">
        <img class="image" src="{{ site.url }}/{{ site.formula}}" alt="Alt Text">
        <figcaption class="caption">Photo by jgam CREDIT: Eloquent Javascript</figcaption>
    </div>
</div>

Using this formula, we can safely say that because the phi coefficient is about 0.069, eating pizza does not appear to have influence on the transformations. (this was an example)

```javascript
function tableFor(event, journal){
    let table = [0,0,0,0];
    for (let i = 0; i < journal.length; i++){
        let entry = jounrnal[i], index = 0;
        if (entry.events.includes(event)) index += 1;
        if (entry.squirrel) index += 2;
        table[index] += 1;
    }
    return table;
}

console.log(tableFor("pizza", JOURNAL));
```

## Array Loops

Simpler form of looping the array is the following:

```javascript
for (let entry of JOURNAL){
    console.log('${entry.events.length} events.');
}
```
When a for loop looks like this, with the word of after a variable definition, it will loop over the elements of the value given after of. This works not only for arrays but also for strings and some other data structures.

## Further Arrayology

The corresponding methods for adding and removing things at the start of an array are called *unshift* and *shift.*

```javascript
let todoList = [];
function remember(task){
    todoList.push(task);
}
function getTask(){
    return todoList.shift();
}
function rememberUrgently(task){
    todoList.unshift(task);
}

console.log([0,1,2,3,4].indexOf(2));//-> 1
console.log([1,2,3,2,1].lastIndexOf(2));//-> 3
console.log([0,1,2,3,4].slice(2,4));//-> [2,3]
console.log([0,1,2,3,4].slice(2));//->[2,3,4]

function remove(array, index){
    return array.slice(0, index).concat(array.slice(index+1));
}
console.log(remove([1,2,3,4,5],2)); //-> [1,2,4,5]
```

## Strings and their properties

Take a look at the following code:

```javascript
let kim = "kim";
kim.age = 88;
console.log(kim.age);//-> undefined
```

The error occurs because values of type string, number, and Boolean are not objects, and though the language doesn't complain if you try to set new properties on them, it doesn't actually store those properties. As mentioned earlier, such values are immutable and cannot be changed.

### Several built-in properties and their methods
1. string.slice(4,7) -> returns string's 5th character to 7th character
2. string.indexOf("a") -> returns integer index of character "a" in string.
3. string.trim() -> removes whitespaces(spaces, newlines, tabs, and similar characters) from the start and end of a string.
4. String(6).padStart(3, "0"); -> "006"
5. string.split(" ") -> splits a string by spaces and make a list
6. array.join(". "); ->join the list as a single string replacing separators as ". "
7. string.repeat(3); -> stringstringstring


## Rest Parameters

It can be useful for a function to accept any number of arguments. For example, Math.max computes the maximum of all the arguments it is given.

To write such a function, you put three dots before the function's last parameter.

```javascript
function max(...numbers){
    let results = -Infinity;
    for (let number of numbers){
        if (number > result) result = number;
    }
    return result;
}
console.log(max(4,1,9,-2));//9
```

*Rest parameter* is bount to an array containing all further arguments. If there are other parameters before it, their values aren't part of that array. When, as in max, it is the only parameter, it will hold all arguments.

You can also spread out the array into the function call, passing its elements as seaprate arguments.

```javascript
let numbers = [5,1,7];
console.log(max(...numbers));//-> console.log(max(5,1,7));
```

## Finishing

Objects and arrays provide ways to group several values into a single value. Most values in JavaScript have properties, the exceptions being null and undefgined. There are some named properties in arrays, such as length and a number of methods. There existss a different way of looping the array or objects(personally similar to python.)

## Chapter4 Exercises
[Chapter4 exercises](https://github.com/jgam/EloquentJavascript)