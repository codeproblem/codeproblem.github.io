---
layout: post
title:  "Codewars 'Money, Money, Money' in Python"
date:   2020-05-23 13:59:20 +0100
categories: codewars python fundamentals
permalink:  'codewars/python/money-money-money'
---

> Mr. Scrooge has a sum of money 'P' that wants to invest, and he wants to know how many years 'Y' this sum has to be kept in the bank in order for this sum of money to amount to 'D'.
>
> The sum is kept for 'Y' years in the bank where interest 'I' is paid yearly, and the new sum is re-invested yearly after paying tax 'T' on the interests that were just gained (and only on the interests part).
>
> #### Example:
>
> ```
Let P be the Principal = 1000.00
Let I be the Interest Rate = 0.05
Let T be the Tax Rate = 0.18
Let D be the Desired Sum = 1100.00
>
After 1st Year -->
  P = 1041.00
After 2nd Year -->
  P = 1083.86
After 3rd Year -->
  P = 1128.30
```
>
> Thus Mr. Scrooge has to wait for 3 years for the initial pricipal to ammount to the desired sum.
>
> Your task is to complete the method provided and return the number of years 'Y' as a whole in order for Mr. Scrooge to get the desired sum.
>
> Assumptions : Assume that Desired Principal 'D' is always greater than the initial principal, however it is best to take into consideration that if the Desired Principal 'D' is equal to Principal 'P' this should return 0 Years.

[Money, Money, Money challenge from Codewars](https://www.codewars.com/kata/563f037412e5ada593000114/train/python)

### Explanation

### 1. Iterate until desired sum is reached

The first step to solving this problem is to iterate until the desired sum is reached. The `while` loop is perfect for this:

```python
def calculate_years(principal, interest, tax, desired):
    while principal < desired:
        # do something
```

### 2. Calculate total interest

The next step is to calculate the interest and add it to the principal on each iteration. The interest amount can be calculated by `principal * interest`:

```python
def calculate_years(principal, interest, tax, desired):
    while principal < desired:
        total_interest = principal * interest
        principal = principal + total_interest
```

### 3. Account for tax

The problem also includes tax. The amount of total interest generated on each iteration needs to have tax deducted. To calculate the tax on `total_interest` we can do `total_interest * tax`. We then have to change the `principal` calculation to subtract `interest_tax` from `total_interest`:

```python
def calculate_years(principal, interest, tax, desired):
    while principal < desired:
        total_interest = principal * interest
        interest_tax = total_interest * tax
        principal = principal + (total_interest - interest_tax)
```

Now we have a function that calculates interest payments and stops when the principal reaches the desired amount.

### 4. Return the number of years

The last step is to return the number of years. Let's add a new variable, `years`, and initialize it to 0. In each iteration we'll increment `years` by 1. At the end of the function, after the while loop has finished `years` will be returned:

### Solution

Here's the complete solution:

```python
def calculate_years(principal, interest, tax, desired):
    years = 0

    while principal < desired:
        years = years + 1
        total_interest = principal * interest
        interest_tax = total_interest * tax
        principal = principal + (total_interest - interest_tax)

    return years
```