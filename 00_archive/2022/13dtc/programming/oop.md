---
title: Introduction to object-oriented programming
grand_parent: 13DTC
parent: Complex Programming
nav_order: "ba"
learning_intentions: ["What benefits object-oriented programming can provide", "How to define a class", "How to instantiate a class to create an object"]
success_criteria: ["You have completed the Intro to OOP task"]
---
 
# What is object-oriented programming?

<div style='max-width: 1280px'><div style='position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;'><iframe width="1280" height="720" src="https://web.microsoftstream.com/embed/video/127b1648-f3b4-4db8-88c6-ac91f41179ea?autoplay=false&showinfo=true" allowfullscreen style="border:none; position: absolute; top: 0; left: 0; right: 0; bottom: 0; height: 100%; max-width: 100%;"></iframe></div></div>

[If you can't load the video above, watch it on Microsoft Stream](https://web.microsoftstream.com/video/127b1648-f3b4-4db8-88c6-ac91f41179ea)

In year 13, you will be expected to use object-oriented programming techniques as part of the computer program standard.

Object-oriented programming offers two benefits: **encapsulation** and **composition, inheritance, and delegation**. To begin with, let's look at encapsulation.

## Encapsulation

So far, you've written programs as a series of steps one after the other — variables get declared, some code might update the values, and so on until the program closes. You can declare variables and functions, but there is no explicit link between them.

This means that a variable's value may change at some point and, short of printing a statement every time any variable's value changes, we can't be entirely sure what variables have changed or what piece of code caused the change — there is no link between when the data is changed and what part of code caused it to happen.

Encapsulation gathers the data and functions into a single place: an **object**.

But first, to create an object, we must define what data and functions the object will contain. This is done with classes.

# Classes and objects

## Classes

In object-oriented programming, **classes** allow us to collect related data and functions into an object. In terms of the data, we can also decide what information we want to expose to the rest of the program or even to the programmer.

For example, we can create a class that keeps the information for a student in one place:

```python
from dataclasses import dataclass

@dataclass
class Student:
    """Personal information for a student"""
    name: str
    age: int
```

Just like this, we ensure that the name and age are in one place.

With some additional work, we can also prevent code outside of the class from modifying the data. This is done in conjuction with methods.

## Objects

This is all great but how do we actually *use* the class? To actually use the ``Student`` class, we *instantiate* it: this means that we create an **object** based on the class.

Remember: if the class is a blueprint for something, the object is the actual thing!

```python
from dataclasses import dataclass

# Create a class called Student
@dataclass
class Student:
    """Personal information for a student"""
    name: str
    age: int

# Create a Student object called student1
student1 = Student(name="Alan", age=17)

# Print the student1 object's age and name
print(student1.age) # 17
print(student1.name) # Alan

# Change the student1 object's value
student1.name = "Zack"

# Print the student1 object's age and name after change
print(student1.age) # 17
print(student1.name) # Zack
```

{% include task.html task_code="UirLo6m3" %}

[^1]: Adapted from [Object-oriented programming](https://simple.wikipedia.org/wiki/Object-oriented_programming), Simple English Wikipedia (retrieved 15/11/2021, emphasis added).
