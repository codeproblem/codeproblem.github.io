---
layout: post
title:  "Codewars 'Testing 1-2-3' in JavaScript"
date:   2020-05-12 07:08:20 +0100
categories: codewars javascript fundamentals arrays iterators
permalink:  'codewars/javascript/testing-1-2-3'
---

> Your team is writing a fancy new text editor and you've been tasked with implementing the line numbering.
>
>Write a function which takes a list of strings and returns each line pretended by the correct number.
>
>The numbering starts at 1. The format is n: string. Notice the colon and space in between.
>
> #### Examples
>
> ```
number([]) // => []
number(["a", "b", "c"]) // => ["1: a", "2: b", "3: c"]
```

[Testing 1-2-3 challenge from Codewars](https://www.codewars.com/kata/54bf85e3d5b56c7a05000cf9/train/javascript)

### Explanation

This problem involves iterating over an array of strings and modifying them, for that I can use JavaScript's `map` function. I need to add a 'line number' to each element, I can do that using an index. `map` can receive an optional argument to serve as an index.

Watch the screencast or read the explanation below:

<iframe width="560" height="315" src="https://www.youtube.com/embed/lsxyIgSBGok" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

#### 1. Mapping over the array

Mapping over the array is fairly straight forward. `array.map` takes a function with a `line` argument that represents each element in the array:

```javascript
return array.map((line) => {
  return line
});
```

This code will return the array unmodified: `["a", "b", "c"]`.

#### 2. Adding the line number using an index

To get an index, I'll add a second argument to the function passed into `array.map`. I'll then use template literals to combine `index` and `line` into a single string in the correct format for the Codewars problem. I need to do `index + 1` because the index starts at 0 but the problem specifies that line numbers start with 1.

```javascript
return array.map((line, index) => {
  return `${index + 1}: ${line}`
});
```

This will return: `["1: a", "2: b", "3: c"]`.

### Solution

Here's the final solution:

```javascript
var number=function(array){
  return array.map((line, index) => {
    return `${index + 1}: ${line}`
  });
}
```

For bonus points, the solution can be re-written as one line of code. I can single line the function inside `array.map`, remove the curly braces and remove the `return`:

```javascript
var number=function(array){
  return array.map((line, index) => `${index + 1}: ${line}`);
}
```