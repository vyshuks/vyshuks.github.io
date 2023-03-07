---
layout: post
title: Python Descriptors
description: Python Descriptors
date: 2022-06-12 01:04:30 -0800
tags: Python
---

## What is a Descriptor?
A descriptor is an object that defines the behavior of an attribute of a class. It allows developers to customize how the attribute is accessed and modified. In Python, there are three types of descriptors:

* Data descriptors
* Non-data descriptors
* Property descriptors

### Data Descriptors
A data descriptor is a descriptor that defines both the get and set methods. These methods define how an attribute is accessed and modified. Data descriptors are used to implement properties, which are attributes that are accessed and modified like normal attributes, but have custom behavior.

### Non-data Descriptors
A non-data descriptor is a descriptor that defines only the get method. This method is used to define how an attribute is accessed. Non-data descriptors are used to implement methods that act like properties but are read-only.

### Property Descriptors
A property descriptor is a descriptor that defines a read-only attribute. It allows developers to define attributes that are accessed like properties but cannot be modified.


## How Descriptors Work
Descriptors work by intercepting attribute access on a class. When an attribute is accessed or modified on a class that has a descriptor, the descriptor's get or set method is called instead of the normal attribute access.

Descriptors are defined as class-level attributes. They are instantiated when the class is created and are shared by all instances of the class. This allows developers to define custom behavior for attributes that is shared by all instances of the class.


## How to Use Descriptors
To use a descriptor, you define a class-level attribute that is an instance of the descriptor. You can then use this attribute to define the behavior of the attribute it is attached to. Here's an example:


```
class Descriptor:
    def __get__(self, instance, owner):
        print("getting attribute")
        return instance._value

    def __set__(self, instance, value):
        print("setting attribute")
        instance._value = value

class MyClass:
    attribute = Descriptor()

    def __init__(self, value):
        self._value = value

my_instance = MyClass(10)
my_instance.attribute = 20 # prints "setting attribute"
print(my_instance.attribute) # prints "getting attribute" and 20

```

In this example, we define a descriptor called Descriptor. We then define a class called MyClass that has an attribute called attribute that is an instance of the Descriptor class. We define the __init__ method of MyClass to initialize the _value attribute.

When we create an instance of MyClass, we pass in a value of 10. We can then access and modify the attribute attribute on the instance of MyClass. When we set the value of attribute to 20, the __set__ method of the Descriptor class is called, which prints "setting attribute". When we print the value of attribute, the __get__ method of the Descriptor class is called, which prints "getting attribute" and returns the value of _value, which is 20.

## Conclusion
Descriptors are a powerful feature of Python that allow developers to customize the behavior of attributes in a class. They can be used to implement properties, read-only attributes, and custom attribute behavior. 
