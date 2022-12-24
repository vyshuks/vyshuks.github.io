---
layout: post
title: Python Generator Explained - Part 2
description: Python Generator, Generator Expression
date: 2021-12-30 11:12:30 -0800
tags: Python
---

[Checkout Part 1 of Python Generator](/2021/12/30/Python-Generator-Explained-Part-1.html)

# Generator Expression
Generator expression is an inline expression of an generator function.
It is somewhat similar to list comprehension. But insted of returning a list it return a generator object.

```
squares1 = [n**n for n in range(10)]  # list comprehension ; return new list

squares2 = (n**n for n in range(10))  # generator expression ; return a generator object

print(type(squares2))

#output:
<class 'generator'>
```

# Generators are for one time use

Yes, we can iterate or loop over a generator object only once. After finishing looping first time its values will exhausted.

Example:
```
squares = (n**n for n in range(10)) 
print(list(squares)) # output: [1, 1, 4, 27, 256, 3125, 46656, 823543, 16777216, 387420489]
print(list(squares)) # output: []  ; generator exhausted
```

## Generator is Memory Efficient
We can look this through by an example

```
import sys

lst = [i for i in range(100)]
gen = (i for i in range(100))

print(sys.getsizeof(lst)) # 904
print(sys.getsizeof(gen)) # 112

lst = [i for i in range(10000)]
gen = (i for i in range(10000))

print(sys.getsizeof(lst)) # 824456
print(sys.getsizeof(gen)) # 112
```

The code above displays the memory size (in bytes) required for the generator expression and list comprehension examples.

When a generator is instantiated, it does not compute the value of each item. They only compute it if you request it. 
This is referred to as lazy evaluation.
In contrast, a normal sequence type allocates memory based on its entire content.




