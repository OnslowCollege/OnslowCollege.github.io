---
title: 2D Lists
grand_parent: 12DTC
parent: Advanced Programming
nav_order: "be"
learning_intentions: ["Learn how to store lists inside lists", "Access values inside lists … inside lists"]
success_criteria: ["You have added at least two lists inside another list", "You have accessed a list inside a list", "You have accessed an item inside a list … inside another list"]
---

# 6.1 Two-dimensional lists

A powerful feature of lists in Python is that they can store anything. This includes other lists. We call this **2D lists**.

Normal lists are 1D, or one-dimensional, because the items can be represented in a single line.

| | Index 0 | Index 1 | Index 2 |
| --: | :-: | :-: | :-: |
| **List 1** | Hubert | Dewford | Llewellyn |

See how the items move only across from left to right?

2D lists can be represented across and up-down.

| | Index 0 | Index 1 | Index 2 |
| --: | :-: | :-: | :-: |
| **List 1** | Hubert | Dewford | Llewellyn |
| **List 2** | Webbigail | Lena | Violet |
| **List 3** | Scrooge | Donald | Della |

# 6.2 How to declare a 2D List

To put a list inside another list, simply write the lists like normal but with each list embedded in a list that wraps the rest.

```python
duck_groups = [["Hubert", "Dewford", "Llewellyn"], ["Webbigail", "Lena", "Violet"], ["Scrooge", "Donald", "Della"]]
```

See how each indivdual list is contained within another set of ``[`` and ``]``? This is a list of lists!

# 6.3 Accessing lists in a list

You access list within a 2D list the same as accessing items within a 1D list.

For example, to get the first list containing ``Hubert``, ``Dewford``, and ``Llewellyn``:

```python
print(duck_groups[0]) # ['Hubert', 'Dewford', 'Llewellyn']
```

# 6.4 Accessing items in 2D lists

To access the *items* within a 2D list, you first access the inner list, and then access the item as usual.

For example, to access ``Llewellyn`` from ``duck_groups``:

```python
# 0 for the first list
# 2 for the third item in the first list
print(duck_groups[0][2]) # Llewellyn
```

# 6.5 List functions in 2D

All of the functions you learnt in [List Functions](lists-03-functions.md) work exactly the same, both for modifying lists within lists **and** for modifying items.

## 6.5.1 Appending and removing a list

```python
# Appending a list
duck_groups.append(["Magica", "Flintheart", "John"])

# Removing the list
duck_groups.pop(-1)
```

## 6.5.2 Appending and removing items in inner lists

```python
# Appending to the first inner list
duck_groups[0].append("Gene")

# Removing the item from the first inner list
duck_groups[0].pop(0)
```

## 6.5.3 Merging lists

```python
# Note that the added list is also a 2D list
duck_groups = duck_groups + [["Magica", "Flintheart", "John"]]
```

## 6.5.4 Merging items into inner lists

```python
# Add items to the last inner list
duck_groups = duck_groups[-1] + ["Ma Beagle", "Mark Beaks"]
```

{% include task.html task_code="ir1H3vH8" %}