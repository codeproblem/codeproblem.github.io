---
layout: post
title:  "Codewars 'List Filtering' in JavaScript"
date:   2020-06-01 12:08:20 +0100
categories: codewars javascript fundamentals arrays
permalink:  'codewars/javascript/list-filtering'
---

> In this kata you will create a function that takes a list of non-negative integers and strings and returns a new list with the strings filtered out.
>
> #### Examples
>
> ```
filter_list([1,2,'a','b']) == [1,2]
filter_list([1,'a','b',0,15]) == [1,0,15]
filter_list([1,2,'aasf','1','123',123]) == [1,2,123]
```

[List Filtering challenge from Codewars](https://www.codewars.com/kata/53dbd5315a3c69eed20002dd/train/javascript)

### Explanation

This problem involves iterating over a list of elements and filtering out the ones that are not strings.

#### 1. Using JS filter to remove strings

Using JavaScript's `filter` method, this problem becomes very simple. `filter` takes a callback function that gets called for each element in the array. If the callback function returns true, the element gets included in the resulting array. If not, it gets discarded.

All we need to do is check if the element is a string. In the callback function, we can use `typeof`. If the element is a string then our function should return false:

```javascript
return l.filter((e) => {
  return typeof e !== 'string'
})
```

### Solution

Here's the complete solution:

```javascript
function filter_list(l) {
  return l.filter((e) => {
    return typeof e !== 'string'
  })
}
```

For bonus points, the solution can be re-written as one line of code. I can single line the function inside `filter`, remove the curly braces and remove the `return`:

```javascript
function filter_list(l) {
  return l.filter(e => typeof e !== 'string')
}
```