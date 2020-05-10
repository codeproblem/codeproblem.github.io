---
layout: post
title:  "Codewars 'Reverse words' in Python"
date:   2020-05-11 07:08:20 +0100
categories: codewars python fundamentals strings
permalink:  'codewars/python/reverse-words'
---

> Complete the function that accepts a string parameter, and reverses each word in the string. All spaces in the string should be retained.
>
> #### Examples
>
> ```
"This is an example!" ==> "sihT si na !elpmaxe"
"double  spaces"      ==> "elbuod  secaps"
```

[Reverse words challenge from Codewars](https://www.codewars.com/kata/5259b20d6021e9e14c0010d4/train/python)

### Explanation

Solving this problem consists of four parts.

#### 1. Splitting the string into an array of words

The first step is to split the string using a space as the delimiter:

```python
words = text.split(' ')
````

#### 2. Iterating over the array of words

The next step is to iterate over the array of words:

```python
for word in words:
    word
```

#### 3. Reversing the word

With the iteration working, I need to reverse the words. I can do that using slicing. I can create a slice that starts with the length of the string, and ends at index 0:

```python
for word in words:
    word[len(word)::-1]
```

This syntax works by starting at the end of the string and working towards the first, taking each element.

Python has a shorthand for this which means I can write it without specifying the string length:

```python
for word in words:
    word[::-1]
```

Now I just need to add these reversed words to an array, to use later in the code:

```python
reversed_words = []

for word in words:
    reversed_words.append(word[::-1])
```

#### 4. Joining the array of reversed words into a single string

The last thing I need to do is join the array of reversed words into a single string and return the result. I'll join the `reversed_words` using a `' '` delimiter:

```python
return ' '.join(reversed_words)
```

### Solution

Here is the final solution:

```python
def reverse_words(text):
    words = text.split(' ')

    reversed_words = []

    for word in words:
        reversed_words.append(word[::-1])

    return ' '.join(reversed_words)
```

For bonus points, the solution can be re-written as a single line of code:

```python
def reverse_words(text):
    return ' '.join(word[::-1] for word in text.split(' '))
```