---
title: Inheritance
grand_parent: 13DTC
parent: Complex Programming
nav_order: "bd"
learning_intentions: ["What inheritance is", "When to use inheritance", "What base classes, superclasses, and superclasses are", "How to declare a base class", "How to declare a subclass which inherits from a base class or superclass"]
success_criteria: ["You have declared a base class (A)", "You have declared two subclasses (B, C) that inherit from the base class (A)", "You have declared two more subclasses (D, E), one each inheriting from the already-defined subclasses (D inherits from B, E inherits from C)"]
---

Inheritance

**Inheritance** works very similarly to using [protocols](04.protocols.md).

Just as classes *conform* to protocols, classes can also *inherit* from other classes — however, this means getting not just the original class' methods but also its members.

## Base classes, superclasses, subclasses

As the name implies, inheritance works by a hierarchy: something receives the data and methods from something else, and it might pass that data and methods on to yet another thing.

In this hierarchy, consider three levels:

- Base classes
- Superclasses
- Subclasses

![Hierarchy graph of base class A, superclasses B and E which inherit from A, subclasses C and D which inherit from B, and subclass E which inherits from E](img/classes.jpg)

## Base classes

A base class in Python is one which does not inherit from any other class (technically, all classes inherit from a class called Object — but that isn't important).

**In all the previous lessons, we created base classes.**

Take this base class defining the features of a building: the street number and street name.

```python
from dataclasses import dataclass

@dataclass
class Building:
    _street_number: int
    _street_name: str

    @property
    def address(self) -> str:
        return f"{self._street_number} {self._street_name}"
```

## Superclasses and subclasses

Of course, different types of buildings need different kinds of information. We can create **subclasses** that inherit from the ``Building`` class. For each of these subclasses, ``Building`` will be the **superclass**.

To declare a subclass, you specify the superclass in brackets directly after the name of the class, like so:

```python
class MySubclass(Superclass):
```

You can also override a superclass' function with a new implementation, similar to conforming to a protocol. Just write the new implementation using the same function name.

For example, let's create an a ``House`` and an ``Apartment`` class.

```python
@dataclass
class House(Building):
    _street_letter: str

    # Overriding the original address property's behaviour
    @property
    def address(self):
        return f"{self._street_letter}{self._street_number} {self._street_name}"
```

You can also use the superclass' version of the function within the subclass, even as part of overriding it. In the following example, we use the original superclass' ``address`` property as part of the apartment address.

```python
@dataclass
class Apartment(Building):
    _suite_number: int
    _suite_letter: str

    @property
    def address(self) -> str:
        return f"Suite {self._suite_number}{self._suite_letter}\n{super().address}"
```

## Creating subclass objects

Subclasses are turned into objects in the exact same way as the base classes we've made before.

For example, the following works:

```python
building = Building(42, "Wallaby Way")
house = House(742, "Evergreen Terrace", "A")
apartment = Apartment(495, "Grove Street", 20, "")

print(building.address)  # 42 Wallaby Way

print(house.address)     # 742A Evergreen Terrace

print(apartment.address) # Suite 20
                         # 495 Grove Street
```

{% include task.html task_code="8oc5dlvS" %}