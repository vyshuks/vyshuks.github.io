---
layout: post
title: Facade Pattern
description: Brief outline of Facade Design Pattern
date: 2023-04-06 20:12:30 -0800
tags: Design Pattern
---

# Introduction

The Facade design pattern is a structural design pattern that provides a smoother interface to a complex system of classes, libraries, or frameworks. It is also referred to as the `wrapper` pattern. The pattern encapsulates a collection of objects and provides them with a unified interface.

In a nutshell, the Facade pattern creates a single, simplified interface to a complex system. It protects clients from the system's complexity and makes it easier to use.

# Example

For example, we can turn on a computer by simply pressing a button, but this involves numerous procedures and operations (e.g. loading programmes from disc to memory etc). In this case, the button acts as a unified interface to all of the underlying procedures for turning on a computer.

```
# Complex computer parts
class CPU:
    """
    Simple CPU representation.
    """
    def freeze(self):
        print("Freezing processor.")

    def jump(self, position):
        print("Jumping to:", position)

    def execute(self):
        print("Executing.")


class Memory:
    """
    Simple memory representation.
    """
    def load(self, position, data):
        print("Loading from {0} data: '{1}'.".format(position, data))


class SolidStateDrive:
    """
    Simple solid state drive representation.
    """
    def read(self, lba, size):
        return "Some data from sector {0} with size {1}".format(lba, size)


class ComputerFacade:
    """
    Represents a facade for various computer parts.
    """
    def __init__(self):
        self.cpu = CPU()
        self.memory = Memory()
        self.ssd = SolidStateDrive()

    def start(self):
        self.cpu.freeze()
        self.memory.load("0x00", self.ssd.read("100", "1024"))
        self.cpu.jump("0x00")
        self.cpu.execute()

def main():
    """
    main function
    """

    computer_facade = ComputerFacade()
    computer_facade.start()

>>> main()
Freezing processor.
Loading from 0x00 data: 'Some data from sector 100 with size 1024'.
Jumping to: 0x00
Executing.
```