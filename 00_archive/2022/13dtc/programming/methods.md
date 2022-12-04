---
title: Methods
grand_parent: 13DTC
parent: Complex Programming
nav_order: "bc"
learning_intentions: ["What a method is", "How to declare an instance method"]
success_criteria: ["You have declared an instance method in a class", "You have called a method on an object"]
---

# What is a method?

In object-oriented programming, a **method** is a function that is part of an object. Typically, methods work with the members stored in the object.

These are different to the functions you have already made in the following ways:

- they are declared inside a class
- they must be called on a class or object
- instance methods always contain ``self``

Just the same as functions, methods can:
- modify the value of variables
- accept arguments
- return values

# How to write a method

Writing a method is just like writing a function, except that it must be written as part of a the class.

Also, all methods (with exceptions listed below) must have ``self`` as the first argument.

```python
@dataclass
class Building:
    street_number: int
    street_name: int

    def ring_fire_alarm(self):
        print("DING DING DING DING!")
```

To use this method, we first need to have an object on which to call it:

```python
brady_house = Building(4222, "Clinton Way")
brady_house.ring_fire_alarm() # DING DING DING DING!
```
# Properties are methods

[Properties](02.members-and-properties.md) are also methods. This is because they can do certain things when accessed or modified. Let's protect the ``Building`` class' members and add properties — using methods!

```python
@dataclass
class Building:
    _street_number: int
    _street_name: int

    @property
    def street_number(self) -> int:
        return self._street_number

    @street_number.setter
    def street_number(self, new_number):
        if new_number > 0:
            self._street_number = new_number
        else:
            raise ValueError("Street numbers begin at 1")

    @property
    def street_name(self) -> int:
        return self._street_name

    @street_name.setter
    def street_name(self, new_name):
        name_length = len(new_name)
        if name_length > 0 and name_length <= 50:
            self._street_name = new_name
        else:
            raise ValueError("Street name must be between 1 and 50 characters")

```

# Static methods

There is one type of method you can write that does **not** require ``self``. This is because the function is called on the class itself, not on objects. This is called a **static method**.

Static methods:

- are used to perform tasks that are related to the class
- are not related to any individual object
  - (i.e. buildings in general, but not a specific building)
- do not use access or modify any of the members
- start with ``@staticmethod``

For example, ``Building`` could have a static method that generates a 5 digit serial code for the building to be used in building consent documents:

```python
@dataclass
class Building:
    # Members and properties here
    # ...

    @staticmethod
    def generate_serial() -> str:
        serial = ""
        for i in range(5):
            serial = serial + str(randint(0, 10))
        return serial

# Call to static method — notice, it is called
# on Building directly, not on an object such as school_house
serial = Building.generate_serial()

print(serial) # 41930 (for example)
```

{% include task.html task_code="ntrQNfgF" %}