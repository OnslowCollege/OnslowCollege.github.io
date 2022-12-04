---
title: Intro to Lists
grand_parent: 11DIT
parent: Programming
nav_order: "ba"
learning_intentions: ["To store multiple items in a single variable", "To access an item stored in a list"]
success_criteria: ["You have successfully declared and populated a list", "You access the first, last, and any other item in the list", "You have printed a list item"]
---

# Lists

Think of a list like a variable — except it stores multiple values, not just one. For example, you might have a variable that stores one name but a list that stores many names.

```python
# Single name
trainer_name = "Red"

# Multiple names
leader_names = ["Brock", "Misty", "Lt. Surge", "Erika", "Sabrina", "Koga", "Blaine", "Giovanni"]
```

## How to declare a list

To make a list:

```python
[item1, item2, item3, item4, item5]
```

1. Start with a left square bracket ``[``
2. Add in the items you want, separated by commas
3. Finish with a right square bracket ``]``

You can create **homogenous** lists where all the data has the same type. For example, a list of only ``int`` numbers:

```python
prime_numbers = [2, 3, 5, 7, 11, 13, 17, 19]
```

However, you can also create **heterogenous** lists where the list items have different types:

```python
# str, int, float, str
perfect_numbers = ["six", 28, 496.0, "8128"]
```

## When to use a list

It's best to use a list to contain data of the same type, usually related to the same thing. For example:

- a list of names
- a list of favourite colours
- a list of pets

# Task 1: My first lists

> **Filename**: lists1.py

## 1.1 Requirements

Create **four** lists, stored in variables, that contain the following data:

1. any five colours (as strings)
2. any six animals (as strings)
3. any seven **even** numbers (as ``int`` numbers)
4. any eight multiples of ten (as ``int`` numbers)

# Task 2 Access list items

> **Filename**: lists2.py

## 2.1 Requirements

Copy the lists from ``lists1.py`` into ``lists2.py``, then add the following features:

1. From the colours list, print the first item
2. From the animals list, print the last item
3. From the even numbers list, print the third item
4. From the multiples-of-ten list, print the second item

## 2.2 An index, many indices

When you want to work with one particular item in the list, such as to ``print`` it out, you must first work out the item's **index**.

An index describes the position of an item within a list. The plural of index is **indices** (in-duh-seez).

In Python, list indices always start with ``0`` — this means that the first item is in the zeroth position.

For example, if we have a list of students like this:

```python
students = ["Ash", "Misty", "Brock", "Tracey", "May", "Dawn"]
```

… then the indices are as follows:

| 0 | 1 | 2 | 3 | 4 | 5 |
| :-: | :-: | :-: | :-: | :-: | :-: |
| Ash | Misty | Brock | Tracey | May | Dawn|

## 2.3 Access the first item in a list

Let's print out the first name in a list of students:

```python
students = ["Ash", "Misty", "Brock", "Tracey", "May", "Dawn"]
ash = students[0]
print(ash) # Ash
```

As you can see, we access the ``students`` variable and then access index ``0`` in square brackets. This is called a **subscript**.

## 2.4 How to write a subscript

To retrieve an item from a list using a subscript:

```python
my_list[index]
```

1. Enter the variable of the list you wish to access
2. After the variable, type a left square bracket ``[``
3. Enter the index you wish to access as a number
4. Type a right square bracket ``]``

## 2.5 Common indices

- The first item is **always** located at the zeroth index. ``[0]``
- The last item can be quickly located using the following index: ``[-1]``
  - You can also work out the second-to-last item with ``[-2]``, third-to-last with ``[-3]``, etc.

# Task 3: List lengths

> **Filename**: lists3.py

## 3.1 Requirements

Copy the lists from ``lists1.py`` to ``lists3.py``, then add the following features:

1. Print the length of all of the lists
2. If a list has **six or more** items, print the first item
3. Otherwise, print the last item

## 3.2 Determine the length of a list

You can determine how long a list is using the ``len(x)`` function, replacing ``x`` with the list to examine.

```python
pets = ["Pikachu", "Butterfree", "Grimer", "Mankey"]
number_of_pets = len(pets)
print(number_of_pets) # 4
```

Since the length of a list is a number, we can use this to perform some maths. For example:

```python
pets = ["Pikachu", "Butterfree", "Grimer", "Mankey"]
number_of_pets = len(pets)

# A person may only have six pets
if number_of_pets > 6:
  print("You need to store some pets in your PC")
else:
  print("Have a nice day with your pets!")
```