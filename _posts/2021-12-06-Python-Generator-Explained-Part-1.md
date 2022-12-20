---
layout: post
title: Python Generator Explained - Part 1
description: Python Generator, Iterator Explained
date: 2021-12-30 11:12:30 -0800
tags: Python
---

The generator concept can be found in a variety of programming languages. 
However, in Python, it is a simple and powerful feature of the language.

##  So, what exactly is a generator?
Generators are a type of function that makes writing iterators easier.

### So then what are iterators?
Isn't the name self-explanatory? Yes, the iterator is an object that represents a stream of data through which we can loop through each element.

Technically we can say that an iterator is a Python object that implements the iterator protocol, 
which includes the methods `__iter__()` and `__next__()`

```
class EvenNumbers:
        """
        Class to implement an iterator
        to generate even numbers
        """

        def __init__(self, max=0):
            self.max = max
            self.number = 0

        def __iter__(self):
            return self

        def __next__(self):
            if self.number > self.max:
                raise StopIteration
            num = self.number 
            self.number+=2
            return num

    for i in EvenNumbers(10):
        print(i)  
    
    #output: 
    0
    2
    4
    6
    8
    10
```

So how to write above code using generator ?

Below is a generator function to generate even numbers

```
def even_numbers(max):
    """
    function to generate even numbers
    """
    number = 0
    while number <= max:
        yield number
        number += 2
    
for i in even_numbers(10):
    print(i)  

#output: 
0
2
4
6
8
10
```
What will happen if we use a  `iter` function on generator object ?

```
def my_gen():
    yield 1

g = my_gen()
print(g)

# output 
<generator object my_gen at 0x7f72e9070eb0>

x = iter(g)
print(x)

#output
<generator object my_gen at 0x7f72e9070eb0>

x is g #output True
```
Both `x` and `g` are same object in memory.
When we ask for a iterator from a generator object using `iter` method 
it return itself back. Because generators are iterators which can iterate over.


##  More about `Yield` statement

So if a function contain a `yield` keyword anywhere in the body it will become a generator function and it always return a generator object.

For example:
If we simply call `even_numbers(10)` it will return something like this: `<generator object even_numbers at 0x7f4071f1d820>`
That is a generator object.

```
x = even_numbers(10)
print(x)
print(type(x))

#output:
<generator object even_numbers at 0x7f4071f1d2e0>
<class 'generator'>
```

I'll say it again: If the word "yield" appears anywhere in a function's body, the function becomes a generator object.

Example:
```
def test_fn():
    if False:   
        yield 1   # this line never executed
    return 5
    
x = test_fn()
```

What will be the type of `x` ?
Since `yield` present in the body, the type of `x` is geneartor.

```
print(type(x))
<class 'generator'>
```


Like iterator, a generator can be iterable using for loop. Or we can called using the `next` method.
In each iteration yield returns a value and pauses the execution while maintaining the internal states.
We can even call function using `yield'

Example
```
def squares(num):
    return num*num

def get_squares(limit):
    for i in range(limit):
        yield squares(i)

print(list(get_squares(5)))
# output
[0, 1, 4, 9, 16]

```
## yield from

Introduced in python3.3 for refactoring generators.
We can see with an example.

### Earlier

```
def generator1():
    for i in range(5):
        yield i

def generator2():
    for j in range(5, 10):
        yield j

def generator():
    for i in generator1():
        yield i
    for j in generator2():
        yield j
```

It seems redundant to mention that we want to repeatedly iterate over generators 1 and 2 to give their values.
This is where `yield from`  enters the picture. We may rewrite generator using this new keyword:

### Now 
```
def generator():
    yield from generator1()
    yield from generator2()
```
yield from just passes control to the iterable on the right.

# StopIteration
During iteration, what happens if there are no more elements in generator object?
It raises a `StopIteration` exception.

Example:
```
def my_gen():
    yield 1
    yield 2

g = my_gen()
next(g)
1

next(g)
2

next(g)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```

Checkout Part 2 of Python Generator (/2021/12/30/Python-Generator-Explained-Part-2.html)



