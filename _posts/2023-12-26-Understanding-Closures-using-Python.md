---
layout: post
title: Understanding Closure Using Python
description: Understanding Closure Using Python
date: 2023-12-26 20:12:30 -0800
tags: Closure
---

# Introduction
Closure is a general concept not specific to a programming language.
So what exactly is a closure?

I will try to explain closure using python programming language.

```
def foo():
    x = "hello"

print(x)

```
If we access variable `x` outside function `foo`  error will occur.
Because `x` is local to the function `foo` right?

## nested functions

We know that function are first class objects in python. It means that functions can be treated like any other object. They can be assigned to variables, passed as arguments to other functions, and returned from functions.

so lets write a inner function inside `foo`.

```
def foo():
    x = 'hello'
    def inner(name):
        print(x + name)
    return inner
```

So here we write a inner function inside `foo` and return inner function object.

so when we call `foo` we get inner function object. 
Using this we can access the enclosing scope variable `x` outside function `foo`.

```
inr = foo()
print(inr("John")) # helloJohn
```

## free variable

So what happen after executing the function `foo` ? All of its local variables go away right?
Here it is variable `x` only. But it doesn't go away because there is another reference to it from the 
`inner` function object.
This non-local variable is called `free variable`.


So when we considering inner function we are looking at 2 things:
inner function `inner` and free variable `x`. 

```
Basically a closure is a function plus extended scope that contain free variables.
```

Python provide attribute to function object to inspect these things.

```
inr.__code__.co_freevars  # to get free variables of function object
inr.__closure__ # return a cell object corresponding to each free variable

```

You can explore more like these.

In other post I will explain applications of closure.



