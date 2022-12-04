---
title: Members & Properties
grand_parent: 13DTC
parent: Complex Programming
nav_order: "bb"
learning_intentions: ["What a class member is and how to declare one", "How to protect members", "How to expose a member as a property", "How to make properties immutable (non-editable)"]
success_criteria: ["You have declared members for a class", "You have exposed members as properties", "You have marked some properties as mutable and others as immutable"]
---

# Members

In object-oriented programming, a **member** is a value stored in a class or object. Members include variables, constants, and [properties](##what-is-a-property).

In Python, these can be defined easily using a ``@dataclass``.

For example, the following ``Document`` class has a few members defining who wrote the document, when it was created, when it was last updated, and the text content of the document.

```python
from dataclasses import dataclass

@dataclass
class Document:
    # The following are members
    creator_name: str
    created_date: int
    modified_date: int
    text_content: str
```

When creating a ``Document`` object, the members can be accessed using [dot notation](https://www.askpython.com/python/built-in-methods/dot-notation) — the object, a dot, then the name of the member.

```python
my_document = Document("RJA", 20220212, 20220214, "Hello, world!")
my_document.text_content = "Bonjour, tout le monde !"
print(my_document.text_content)
```

# Properties

<div style='max-width: 1280px'><div style='position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;'><iframe width="1280" height="720" src="https://web.microsoftstream.com/embed/video/127b1648-f3b4-4db8-88c6-ac91f41179ea?autoplay=false&showinfo=true&amp;st=481" allowfullscreen style="border:none; position: absolute; top: 0; left: 0; right: 0; bottom: 0; height: 100%; max-width: 100%;"></iframe></div></div>

[If you can't watch the video above, watch it on Microsoft Stream](https://web.microsoftstream.com/video/127b1648-f3b4-4db8-88c6-ac91f41179ea?st=481)

After creating a class, we can restrict what actions can be performed on its members — for example, we could disallow changing a member's value, ensure that only certain values can be entered, or even make it so that getting a value returns it in a specific format.

A strong benefit of this is that we fully understand what happens when a class' data is changed, how, and even why. In the example below, we modify the ``Document`` class to validate the following:

1. When changing ``creator_name``, the new string must contain at least one character
2. When updating ``modified_date``, the new date be after the existing ``modified_date`` value

```python
from dataclasses import dataclass, field

@dataclass
class Document:
    # Protected Members
    _creator_name: str
    _created_date: int
    _modified_date: int

    @property
    def creator_name(self) -> str:
        return self._creator_name

    @creator_name.setter
    def creator_name(self, new_name: str):
        # Validates that the name is non-empty
        # else raises an error
        if len(new_name) > 0:
            self._creator_name = new_name
        else:
            raise ValueError("Name must contain at least one character")

    # Two properties below cannot be changed as the setter is not defined
    @property
    def created_date(self) -> int:
        return self._created_date

    @property
    def modified_date(self) -> int:
        return self._modified_date

    @modified_date.setter
    def modified_date(self, new_date: int):
        # Validates that the date is within the correct range
        # else raises an error
        if new_date > self._modified_date:
            self._modified_date = new_date
        else:
            raise ValueError("Modified date must not precede last modification date")
```

## What's in a property?

As you can see, we create methods that do the following:

1. Protect the ``_creator_name`` and ``_modified_date`` variables from being accessed directly
2. Allow accessing the ``_creator_name`` and ``_modified_date`` safely through ``creator_name()`` and ``modified_date()`` methods
3. Allow changing the ``_creator_name`` and ``_modified_date`` **with validation** through the setter methods

But how does it actually do it?

## Protect the variables

To start with, we modify the names of the members to include an underscore at the front. You will notice that ``creator_name`` and ``modified_date`` have become ``_creator_name`` and ``_modified_date``.

The underscore at the front is a signal to other Python developers that the variable should not be accessed directly; rather, fetching the value and changing it should be done through the use of a property.

# Getters

In order to validate the data when it is changed, we first need to define a special function that returns the value of the variable. This is called a **getter**: it *gets* the variable!

```python
@property
def creator_name(self):
    return self._creator_name
```

When dealing with objects, you don't need to call the getter like a function; it behaves like a variable or constant.

```python
document = Document("Alan Partridge", 20220214, 20220216, "A-ha!")
print(document.creator_name) # Alan Partridge
```

It's also possible to have getters perform custom behaviours. Say we store names with normal casing but want to easily retrieve the name in all upper case letters:

```python
@property
def uppercase_creator_name(self):
    return self._creator_name.upper()
```

```python
document = Document("Alan Partridge", 20220214, 20220216, "A-ha!")
print(document.uppercase_creator_name) # ALAN PARTRIDGE
```

# Setters

The true magic happens in **setters**. Using setters, you can validate or run custom code when a variable's value is changed.

For instance, the following examples:

1. Validate that the name contains at least one character
2. Transforms all spaces to underscores
3. All of the above

```python
@creator_name.setter
def creator_name(self, new_name: str):
    if len(new_name) > 0:
        self._name = new_name
    else:
        raise ValueError("Name must contain at least one character")
```

```python
@creator_name.setter
def creator_name(self, new_name: str):
    self._name = new_name.replace(" ", "_")
```

```python
@creator_name.setter
def creator_name(self, new_name: str):
    if len(new_name) > 0:
        self._name = new_name.replace(" ", "_")
    else:
        raise ValueError("Name must contain at least one character")
```

## Immutable properties

If you wish for a value to **never** change after it is defined, you can make the property immutable by defining a getter but not defining a setter.

If you try to change the value of a member with no @setter, an ``AttributeError`` is raised.

```python
my_document.created_date = 20220218
# AttributeError raised, program crashes
```

{% include task.html task_code="69l4F6hG" %}
