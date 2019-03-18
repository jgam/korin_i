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

