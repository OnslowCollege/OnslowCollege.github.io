---
title: List modification
grand_parent: 12DTC
parent: Advanced Programming
nav_order: "bb"
learning_intentions: ["Adding and removing items from an established list"]
success_criteria: ["You have added an item to the end, start, and specified position in an established list", "You have removed a specified item from an established list"]
---
 
# 3.1 Modifying the list items

You can modify the list after it has been created. This makes the list *mutable*, meaning it can be modified.

## 3.1.1 Add an item to the end of the list

You can add an item to the end of a list using the ``x.append(y)`` function, replacing ``x`` with the list and ``y`` with the item to add to the list.

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
ducks.append("Scrooge")
print(", ".join(ducks))
# Hubert, Dewford, Llewellyn, Webbigail, Lena, Violet, Scrooge
```

You can also join two lists together with the ``+`` operator. This is another useful way to add an item to a list — however, you need to wrap that item in a list. For example:

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
more_ducks = ducks + ["Scrooge"]
print(", ".join(more_ducks))
# Hubert, Dewford, Llewellyn, Webbigail, Lena, Violet, Scrooge
```

Note that ``"Scrooge"`` is contained within another list. You can use this method to add multiple items at once by putting multiple items in the new list.

## 3.1.2 Add an item to the front of the list

Add items to the front of the list by using the ``+`` operator. Instead of putting the new items in a list after the ``+``, put the new list before the ``+``.

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
more_ducks = ["Scrooge"] + ducks
print(", ".join(more_ducks))
# Scrooge, Hubert, Dewford, Llewellyn, Webbigail, Lena, Violet
```

## 3.1.3 Add an item at a specified index

You can add an item at a specified index using the ``x.insert(y, z)`` function. To do this, replace the following:

- ``x`` with the list
- ``y`` with the index where the item will be inserted
- ``z`` with the item to insert

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
ducks.insert(2, "Scrooge")
print(", ".join(ducks))
# Hubert, Dewford, Llewellyn, Scrooge, Webbigail, Lena, Violet
```

# 3.2 Removing an item from the list

To remove an item from the list, you need to decide if you wish to use the removed item before it is deleted.

## 3.2.1 Using the item before it is deleted

You can assign the item to a variable and remove it from the list using the ``x.pop(y)`` function, replacing ``x`` with the list and ``y`` with the index of the item to remove.

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
dewey = ducks.pop(1)
print(dewey)
print(", ".join(ducks))
# Dewford
# Hubert, Llewellyn, Scrooge, Webbigail, Lena, Violet
```

## 3.2.2 Removing the item immediately

If you do not need to use the item before it is removed, you can set the value of the list item to ``None`` using a subscript.

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
ducks[1] = None
print(", ".join(ducks))
# Hubert, Llewellyn, Scrooge, Webbigail, Lena, Violet
```

You can also use ``pop()`` without specifying a variable

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
ducks.pop(1)
print(", ".join(ducks))
# Hubert, Llewellyn, Scrooge, Webbigail, Lena, Violet
```

# 3.3 Joining lists together

Just like adding an item to a list using another single-item list, you can join lists together using the ``+`` operator.

```python
boys = ["Hubert", "Dewford", "Llewellyn"]
girls = ["Webbigail", "Lena", "Violet"]
ducks = boys + girls
```

{% include task.html task_code="0nOwXzRd" %}