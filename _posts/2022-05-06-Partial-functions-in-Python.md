---
layout: post
title: Partial functions
description: Python Partial function
date: 2022-05-06 12:04:30 -0800
tags: Python
---

Partial functions are a crucial concept in functional programming.
I'll talk about partial functions in Python, how they work, and why they're useful here.


##  Partial function
A partial function is a function that has been partially applied to some of its arguments. 
In other words, a partial function is created by taking an existing function and fixing some of its arguments to specific values, leaving the remaining arguments to be supplied later.

```
def sum(a, b, c):
    return a + b + c

```
We can create a partial function of sum by fixing the value of one or more of its arguments using the functools.partial method. 
For example, let's fix the first argument a to the value 10:

```
from functools import partial

sum_with_a_10 = partial(sum, 10)

result = sum_with_a_10(5, 7)
print(result)  # Output: 22


```
In this example, we have created a new function sum_with_a_10 by fixing the first argument of the sum function to 10. 
When we call sum_with_a_10 with two remaining arguments 5 and 7, it returns the sum of all three numbers, i.e., 10 + 5 + 7 = 22.


### Partial functions are useful in several scenarios, including:

* Simplifying function calls: When a function takes many arguments, it can be cumbersome to provide all of them every time the function is called. By creating a partial function with some of the arguments fixed, we can simplify the function call by only providing the remaining arguments.

* Reusing functions: We can create several partial functions from a single function by fixing different sets of arguments. This can be useful when we have a function with many arguments, and we need to reuse it with different subsets of arguments.

* Callback functions: Partial functions can be used as callback functions when we need to pass a function with specific arguments to another function. For example, in GUI programming, we can use partial functions to pass functions with fixed arguments to event handlers.

In conclusion, partial functions are a powerful and flexible feature of Python that can simplify function calls, reuse functions, and serve as callback functions. By using the functools.partial method, we can easily create partial functions from existing functions and enhance the flexibility and readability of our code.