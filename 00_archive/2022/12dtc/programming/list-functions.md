---
title: List functions
grand_parent: 12DTC
parent: Advanced Programming
nav_order: "bc"
learning_intentions: ["Foramtting the printed output of a list", "Sorting items in a list"]
success_criteria: ["You have printed a list with custom formatting for each item", "You have printed a list slice with custom formatting", "You have sorted the items in a list in order", "You have reversed the order of items in a list"]
---

# 4.1 Joining a list into a string

You can join all the items of a list into a single string. This will let you format the items in the list for printing.

## 4.1.1 Without ``join()``

```python
insects = ["Beetle", "Cockroach", "Fly", "Grasshopper"]
print(insects)
```

If you print the list directly like this, the result is:

```
['Beetle', 'Cockroach', 'Fly', 'Grasshopper']
```

While this is indeed a textual representation of the list object, it isn't very user-friendly. We can't expect users to understand what the brackets and quotation marks are for.

However, you can format the list items using a string's ``join()`` function.

## 4.1.2 With ``join()``

```python
insects = ["Beetle", "Cockroach", "Fly", "Grasshopper"]
joined = ", ".join(insects)
print(joined)
```

This will show: 

```
Beetle, Cockroach, Fly, Grasshopper
```

You could even use a sentence.

```python
joined = "-*quack*-".join(insects)
```

This would result in:

```
Beetle-*quack*-Cockroach-*quack*-Fly-*quack*-Grasshopper
```

# 4.2 Sorting items

There are times when you need items in a particular order, say:

- lowest value to highest value
- alphabetical order
- reversed
- random order

Rather than rewrite the list, you can take advantage of two several built-in functions, the most versatile of which is ``sort()``.

## 4.2.1 sort()

The ``sort()`` function is used to arrange a list in order, either in ascending order (lowest value to highest, or alphabetically for strings) or descending order (highest value to lowest, or reverse alphabetical order for strings).

By default, ``sort()`` will sort a list in ascending order. To sort a list in ascending order, call the ``x.sort()``, replacing ``x`` with the list to sort. For example:

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
ducks.sort()

print(", ".join(ducks)) # Dewford, Hubert, Lena, Llewellyn, Violet, Webbigail
```

However, it is possible to specify that the ``sort()`` function should sort in descending order. To do this, specify ``reverse=True`` as an argument to the ``sort()`` function:

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
ducks.sort(reverse=True)

print(", ".join(ducks)) # Webbigail, Violet, Llewellyn, Lena, Hubert, Dewford
```

## 4.2.3 Advanced sort()

You can also sort according to the result of a function. This is called the **sort key**.

When you specify ``key=x``, replacing ``x`` with a function that accepts one argument and returns a value, the sorting is performed based on the returned value of the function.

For example, you could use the ``len()`` function as the key by specifying ``sort=len`` as an argument to the ``sort()`` function:

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
ducks.sort(key=len)

print(", ".join(ducks)) # Lena, Hubert, Violet, Dewford, Llewellyn, Webbigail
```

## 4.2.4 To avoid sorting the original list

If it is important for you to maintain the order of the items, perhaps to use that order later in the program, you can use ``sorted(x)``, replacing ``x`` with the list to sort. ``sorted()`` returns a new list which you can store in a variable or use within another function.

Also, ``sorted()`` respects the same ``reverse=`` and ``key=`` arguments as ``sort()``

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
sorted_ducks = sorted(ducks, reverse=True, key=len)

print(", ".join(sorted_ducks)) # Webbigail, Llewellyn, Dewford, Violet, Hubert, Lena
```

# 4.3 Reversing the order of items in a list

It is also possible to reverse the order of the items in a list without sorting first. This makes use of the ``x.reverse()`` function, replacing ``x`` with the list to reverse.

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
ducks.reverse()

print(", ".join(ducks)) # Violet, Lena, Webbigail, Llewellyn, Dewford, Hubert
```

## 4.3.1 Reversing without modifying

Just as with sorting, it's possible to reverse a list without modifying the original. Instead, use ``list(reversed(x))``, replacing ``x`` with the list to reverse.

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
reversed_ducks = list(reversed(ducks))

print(", ".join(reversed_ducks)) # Violet, Lena, Webbigail, Llewellyn, Dewford, Hubert
```

> **Note**: don't forget the ``list()`` function surrounding the ``reversed()`` function. Technically, ``reversed()`` does not return a list so the surrounding ``list()`` is important to cast to a list.

{% include task.html task_code="daSE-R9P" %}