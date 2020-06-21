---
layout: post
title:  "Codewars 'Sort array by string length' in Python"
date:   2020-06-21 08:31:00 +0100
categories: codewars python fundamentals
permalink:  'codewars/python/sort-array-by-string-length'
---

> Write a function that takes an array of strings as an argument and returns a sorted array containing the same strings, ordered from shortest to longest.
>
> For example, if this array were passed as an argument:
>
> ```python
["Telescopes", "Glasses", "Eyes", "Monocles"]
```
>
> Your function would return the following array:
>
> ```python
["Eyes", "Glasses", "Monocles", "Telescopes"]
```
>
> All of the strings in the array passed to your function will be different lengths, so you will not have to decide how to order multiple strings of the same length.

[Sort array by string length challenge from Codewars](https://www.codewars.com/kata/57ea5b0b75ae11d1e800006c/train/python)

This problem can be solved with a single Python function, `sorted()`:

```python
def sort_by_length(arr):
    return sorted(arr, key=len)
```

`sorted()` take a list as a parameter and builds a new sorted list. The function can also take a `key` parameter, which gets used on each element before sorting. In this case, we're sorting by the length of the string. Each element gets sorted smallest to largest. You can read a more detailed explanation on the [developer.google.com Python Sorting guide](https://developers.google.com/edu/python/sorting#custom-sorting-with-key=).