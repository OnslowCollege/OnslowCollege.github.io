---
title: List comprehensions
grand_parent: 12DTC
parent: Advanced Programming
nav_order: "bd"
learning_intentions: ["Learn what a list comprehension can do", "Quickly create a new list based on an existing list using a comprehension", "Transform the values in a list and store them in a new list"]
success_criteria: ["You have created a new list based on an existing list using a comprehension", "You have transformed values in a list using a comprehension"]
---

# 5.1 List comprehensions

List comprehensions are the [Pythonic](https://realpython.com/learning-paths/writing-pythonic-code/) way of transforming values in a list and storing the value in another list. In other languages, this might be expressed using a ``map()`` function. However, it's a first-class language feature in Python.

If you're unsure what that means, think of it like a fancy ``for`` loop — we iterate over all the items in a list, make a change to each value, and store them in a new list.

## 5.1.1 Syntax

Basic comprehensions are written like this:

```python
[expression for item in list]
```

1. Comprehensions start with a left square bracket, like a list
2. First, an expression; you perform any modifications to the ``item`` here
3. Next comes syntax similar to a ``for`` loop
4. Finally, close the comprehension with a right square bracket

You can use list comprehensions just like lists. Make sure to store the new list in a variable or constant.

As stated, the change you make happens at the start. For example, to make some names uppercase:

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
shouting_ducks = [name.uppercase() for name in ducks]

print(", ".join(shouting_ducks)) # HUBERT, DEWFORD, LLEWELLYN, WEBBIGAIL, LENA, VIOLET
```

Another example, multiplying a list of numbers by ten:

```python
numbers = [1, 2, 3, 4, 5]
big_numbers = [x * 10 for x in numbers]

print(", ".join(big_numbers)) # 10, 20, 30, 40, 50
```

## 5.1.2 Restrictions

The expression at the start of a list comprehensions must **return a value**. General rule: if you could not store the result of the expression in a variable, it cannot be used.

For example, you cannot use a ``print()`` statement as an expression because it does not return a value. 

```python
[print(x) for x in y]
# This would not run because print(x) does not return a value
```

# 5.2 Filtering items

You can use an ``if`` statement within the list comprehension to only transform certain values. Any values that don't meet the condition are not evaluated and therefore are left out of the list.

```python
[expression for item in list if condition]
```

For example, only selecting numbers that are greater than 10 — with no change in the data.

```python
numbers = [23, 7, 49, 10, 6, 9, 12]
greater_than_ten = [x for x in numbers if x > 10]

print(", ".join(greater_than_ten)) # 23, 49, 12
```

Another example, only uppercasing names that have six or fewer characters:

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
shouting_ducks = [name.uppercase() for name in ducks if len(name) <= 6]

print(", ".join(shouting_ducks)) # HUBERT, LENA, VIOLET
```

Another example, only multiplying **even** numbers in a list by ten:

```python
numbers = [1, 2, 3, 4, 5]
big_numbers = [x * 10 for x in numbers if x % 2 == 0]

print(", ".join(big_numbers)) # 20, 40
```

# 5.3 Ternary operations

In addition to filtering, you can also make a choice between whether to include one item or another based on a condition. This is called a **ternary operation**. Ternary means "relating to the number three", and three things are involved in such an operation:

- the original value
- two potential values

In the case of a list comprehension, the original value is whatever is in the first list. The potential values are two possible values that could take that item's place in the new list.

For example, adding ``True`` or ``False`` to a list depending on whether a number is less than 50:

```python
numbers = [10, 95, 25, 80, 30, 75, 45, 60, 50]
under_50 = [True if x < 50 else False for x in numbers]
```

Another example, assigning Team 1 in a list if a duck's name starts with a letter between A and M, or Team 2 if it starts with a letter between N and Z.

```python
TEAM_1_LETTERS = ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M"]
TEAM_2_LETTERS = ["N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z"]

ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]

duck_teams = [1 if duck[0] in TEAM_1_LETTERS else 2 for duck in ducks]
print(", ".join(duck_teams)) # 1, 1, 1, 2, 1, 2
```

{% include task.html task_code="LUToAm78" %}

Hint: you can reverse a string with ``str(reversed(my_string))``