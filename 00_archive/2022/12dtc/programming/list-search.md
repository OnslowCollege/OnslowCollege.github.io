---
title: Lists
grand_parent: 12DTC
parent: Advanced Programming
nav_order: "ba"
learning_intentions: ["Search for specific items/ranges within a list", "Get a range of items in a list"]
success_criteria: ["You have checked if an item is in a list", "You have determined the index of an item in the list", "You have created a list subsection containing the specified items"]
---

# 2.1 Searching for list items

You can check if an item exists in a list by using ``if x in y`` statement. In this, you replace ``x`` with the item you're searching for and ``y`` with the list.

For example:

```python
insects = ["Beetle", "Cockroach", "Fly", "Grasshopper"]
item = "Fly"
if item in insects:
    print("Yes, it's there")
else:
    print("Sorry, it's not there")
```

You could also ask the user what to search for:

```python
numbers = [4, 3, 2, 5, 24, 1]
num = int(input(What number would you like to check for?: ))
if num in numbers:
    print("Yes, it's there")
else:
    print("Sorry, it's not there")
```

# 2.2 Creating a list slice

If you only need a certain range of items from a list, you can create a **slice** of the list — it will only contain the items in the selected range.

For example, imagine you have the following list:

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
```

| ``ducks`` | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
| :-- | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| | "Hubert" | "Dewford" | "Llewellyn" | "Webbigail" | "Lena" | "Violet" | "Scrooge" |

## 2.2.1 Slicing a range

If we wanted to create new lists containing only the boy and girl ducks, we can create a slice using the ``list[x:y]`` statement subscript statement, replacing ``x`` with the start index and ``y`` with the end index.

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
boys = ducks[0:3]
girls = ducks[3:6]
print(", ".join(boys))  # Hubert, Dewford, Llewellyn
print(", ".join(girls)) # Webbigail, Lena, Violet
```

This takes the following items from ``ducks``:

| ``ducks`` | **0** | **1** | **2** | 3 | 4 | 5 | 6 |
| :-- | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| | **"Hubert"** | **"Dewford"** | **"Llewellyn"** | | | | |

| ``ducks`` | 0 | 1 | 2 | **3** | **4** | **5** | 6 |
| :-- | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| | | | | **"Webbigail"** | **"Lena"** | **"Violet"** | |

And creates a two new lists called ``boys`` and ``girls`` containing the following items:

| ``boys`` | 0 | 1 | 2 |
| :-- | :-: | :-: | :-: |
| | "Hubert" | "Dewford" | "Llewellyn" |

| ``girls`` | 0 | 1 | 2 |
| :-- | :-: | :-: | :-: |
| | "Webbigail" | "Lena" | "Violet" |

Note that the end index is actually one higher than the index of the last item you will use.

## 2.2.2 Slicing from the beginning

To create a slice from the beginning of the list to a specified index, remove the first number from the subscript. For example:

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
first_four = ducks[:4]
```

| ``first_four`` | 0 | 1 | 2 | 3 |
| :-- | :-: | :-: | :-: | :-: |
| | "Hubert" | "Dewford" | "Llewellyn" | "Webbigail" |

## 2.2.3 Slicing to the end

To create a slice from a specified index to the end of a list, remove the second number from the subscript. For example:

```python
ducks = ["Hubert", "Dewford", "Llewellyn", "Webbigail", "Lena", "Violet"]
last_four = ducks[2:]
```

| ``last_four`` | 0 | 1 | 2 | 3 |
| :-- | :-: | :-: | :-: | :-: |
| | "Llewellyn" | "Webbigail" | "Lena" | "Violet" |

{% include task.html task_code="JUXCXzyE" %}