---
title: Dictionaries
grand_parent: 12DTC
parent: Advanced Programming
nav_order: "bf"
learning_intentions: ["Learn how to store data with a string index using dictionaries", "Access values inside dictionaries"]
success_criteria: ["You have stored data in a dictionary", "You have accessed data from within a dictionary"]
---

# Dictionaries

A standard data structure in Computer Science is the associative array which are also known as hashes or maps. In Python this is called the dictionary. 

Like lists, dictionaries can easily be changed, shrunk and grown at run time. Dictionaries can be contained in lists and vice versa.

Unlike lists, which are ordered sets of objects, dictionaries are **un**ordered sets. The main difference is that items in dictionaries are accessed via keys and not via their position.

When you have key-value-pairs, the **key** of the dictionary is associated (or mapped) to a **value**. Keys are usually strings, while values can be any Python data type.

# How to create a dictionary

Let's create a dictionary of countries and their national food. In Python you declare a dictionary using a brace (curly bracket) and separate each item using a comma.

```python
national_foods = {"Italy": "Pizza", "Japan": "Sashimi", "Spain": "Paella", "Samoa": "Panipopo"}
```

The line above has declared a dictionary called countries with 4 pieces of data.

## Storing different types of data

Python is flexible. You can use all kinds of data types for both keys and values. You are free to mix and match data to suit your needs. For example, the dictionary below contains the population of each country stored as an integer:

```python
national_population = {"Italy": 60314896, "Japan": 125837638, "Spain": 46784706, "Samoa": 200593}
```

## Storing other collections

You can treat dictionaries like a sort of 2D collection, similar to a 2D list. Dictionaries can contain lists and even other dictionaries as their values. Lists can also contain dictionaries.

```python
# Dictionary of lists
ducks = {"boys": ["Hubert", "Dewford", "Llewellyn"], "girls": ["Webbigail", "Lena", "Violet"]}

# Dictionary of dictionaries
boys = {"huey": {"long_name": "Hubert", "short_name": "Huey"}, "dewey": {"long_name": "Dewford", "short_name": "Dewey"}, "louie": {"long_name": "Llewellyn", "short_name": "Louie"}}

# List of dictionaries
girls = [{"long_name": "Webbigail", "short_name": "Webby"}]
```

## Converting two lists to a dictionary

You can use the ``zip()`` and ``dict()`` functions to convert two lists to a dictionary.

```python
countries = ["Italy", "Japan", "Spain", "Samoa"]
foods = ["Pizza", "Sashimi", "Paella", "Panipopo"]

national_foods = dict(zip(countries, foods))
```

## Merge two dictionaries

You can merge two dictionaries with the ``update()`` function.

```python
dict1 = {'a': 10, 'b': 8}
dict2 = {'d': 6, 'c': 4}

both_dicts = dict2.update(dict1)
```

# Accessing dictionary items

You can access dictionary items using the key instead of the index. For example:

```python
print(national_foods["Japan"]) # Sashimi

for country in national_populations:
    print(national_populations["country"])
```

# Dictionary functions

The following functions work with dictionaries:

- ``len()``
- ``for item in dictionary``
- ``for index in range(len(dictionary))``
- ``if item in dictionary``

The following functions do **NOT** work with dictionaries:

- ``sort()`` — dictionaries do not have a linear order and cannot be sorted
- ``reverse()`` — dictionaries do not have a linear order and cannot be reversed

{% include task.html task_code="-r4ZWFMa" %}