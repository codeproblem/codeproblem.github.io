---
layout: post
title:  "Codewars 'Exes and Ohs' in Python"
date:   2020-06-05 11:41:00 +0100
categories: codewars python fundamentals
permalink:  'codewars/python/exes-and-ohs'
---

> Check to see if a string has the same amount of 'x's and 'o's. The method must return a boolean and be case insensitive. The string can contain any char.
>
> #### Examples input/output:

[Exes and Ohs challenge from Codewars](https://www.codewars.com/kata/55908aad6620c066bc00002a/train/python)

This problem involves iterating over the characters of a string, counting the 'x' and 'o' characters and comparing the results.

### 1. Split the string into an array of chars

The first step is to split the string parameter into individual characters. We can do that by casting the string to a list, using `list(s)`:

For example:

```python
list('hello')
```
returns:

```python
['h', 'e', 'l', 'l', 'o']
```

### 2. Iterate over the list of chars and check for 'x' and 'o'

Next we need to iterate over the list of chars. For each iteration we will check whether the char is an 'x' or 'o':

```python
chars = list(s)

for c in chars:
    if c == 'x':
        # do something
    elif c == 'o':
        # do something
```

### 3. Count 'x' and 'o' occurrences

In order to complete the problem we need to count the number of 'x' and 'o' chars. To do that we can use two counter variables and update the counter in the respective if/else blocks:

```python
chars = list(s)
x_count = 0
o_count = 0

for c in chars:
    if c == 'x':
        x_count += 1
    elif c == 'o':
        o_count += 1
```

### 4. Lowercase chars

One of the caveats in this exercise is that it should be 'case insensitive'. To do that we need to lowercase each char, before checking whether it's an 'x' or 'o':

```python
chars = list(s)
x_count = 0
o_count = 0

for c in chars:
    if c.lower() == 'x':
        x_count += 1
    elif c.lower() == 'o':
        o_count += 1
```

### 5. Compare the counters

The last thing we need to do is compare the total count of 'x' chars with the total number of 'o' chars. If they are the same we return true, otherwise we return false:

```python
return x_count == o_count
```

### Solution

Here's the complete solution:

```python
def xo(s):
    chars = list(s)
    x_count = 0
    o_count = 0

    for c in chars:
        if c.lower() == 'x':
            x_count += 1
        elif c.lower() == 'o':
            o_count += 1

    return x_count == o_count
```

### Bonus points

The solution above is a bit verbose, with the counters and iteration. We can use some Python features to simplify the code.

### 1. Lowercase the whole string

Python's `lower()` function can be called on a string to lowercase the whole thing:

```python
s = s.lower()
```

### 2. Count the occurrences in a string and compare the results

Python has a `count()` function that searches a string for occurrences of a sub string. We can use that to count the number of occurrences of a char in the input string. If we do that for both 'x' and 'o', we can compare the results all in one line:

```python
return s.count('x') == s.count('o')
```

### Simplified Solution

This code does the same as above but with a much smaller footprint:

```python
def xo(s):
    s = s.lower()
    return s.count('x') == s.count('o')
```