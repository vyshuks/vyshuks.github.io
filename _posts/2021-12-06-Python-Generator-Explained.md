---
layout: post
title: Python Generator Explained
description: Python Generator, Iterator Explained
date: 2021-12-30 11:12:30 -0800
tags: Python Generator Iterator
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

So if a function contain a `yield` keyword anywhere in the body it will become a generator function and it always return a generator object.

For example:
If we simply call `even_numbers(10)` it will return something like this: `<generator object even_numbers at 0x7f4071f1d820>`
That is a generator object.

```
x = even_numbers(10)
print(x)
print(type(x))

#output:
<generator object even_numbers at 0x7f4071f1d2e0>; 
<class 'generator'>
```

Like iterator, a generator can be iterable using for loop. Or we can called using the `next` method.

In each iteration yield returns a value and pauses the execution while maintaining the internal states.

