---
title: for loops
nav_exclude: true
learning_intentions: ["To loop over list items with a for loop"]
success_criteria: ["You have used a for loop to print every item in a list, one at a time", "You have added some special logic to your loops to only print certain items"]
---

In 10DIT, you learnt about ``while`` loops and have practiced using them so far. These are useful because they help us repeat code a certain number of times or until a condition fails to be met.

However, if you are wanting to loop over the items in a list, there is a much more efficient loop called a **for loop**.

## How to write a for loop

Instead of using the ``while`` keyword, use the ``for`` keyword. Also, instead of managing a certain condition, specify the name of the list.

```python
teas = ["Oolong", "Yerba Mate", "Chamomile", "Rooibos"]
for tea in teas:
    print(tea)
```

1. Start with the ``for`` keyword
2. Next, declare a variable that will be used to represent each individual item in a list
    - In the example above, the variable is called ``tea``
3. Add the word ``in``
4. Finish with the name of the list to loop over

# Task 1: First for loops

> **Filename**: for_loops1.py

## 1.1 Requirements

1. Copy the following list into ``for_loops1.py``:

```python
primes = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47]
```

2. Use a for loop to print each number on its own line

## 1.2 Example output

```
2
3
5
7
11
13
17
19
23
29
31
37
41
43
47
```

# Task 2: For loops with maths

> **Filename**: for_loops2.py

## 2.1 Requirements

1. Copy the **animal** list you created from ``lists1.py`` into ``for_loops2.py``
2. Use a for loop to print each animal with "crackers in my soup" added afterwards

## 2.2 Example output

```
Monkey crackers in my soup
Rabbit crackers in my soup
Lion crackers in my soup
Tiger crackers in my soup
Walrus crackers in my soup
```

# Task 3: For loops with indices

> **Filename**: for_loops3.py

## 3.1 Requirements

1. Copy the **colour** list you created from ``lists1.py`` into ``for_loops3.py``
2. Use a for loop to print the index and colour, separated by a dash
3. Adjust the *printed* index so that the list starts at 1 instead of 0
   - You must still print **all five** items

## 3.2 How to use for loops with indices

If you need to work with the indices of a list, you can loop over the indices of the list instead of the list items themselves.

```python
teas = ["Oolong", "Yerba Mate", "Chamomile", "Rooibos"]
teas_length = len(teas)
for i in range(teas_length):
    print(teas[index])
```

1. Instead of creating a variable for each list item, create a variable for the index. Suggested names: ``i``, ``k``, ``index``, etc.
2. Instead of the name of the list, use the ``range(x)`` function, replacing ``x`` with the length of the list
    - In the above example, the length of the list is in a separate variable called ``teas_length``, therefore ``range(teas_length)``
    - However, you could also do ``range(len(teas))``
3. Inside the loop, you will need to use the list index (i.e. ``i``) rather than the variable (i.e. ``tea``)
    - You can perform maths with the index
    - To access list items, use ``trains[index]``

## 3.3 Example output

```
1 - Red
2 - Yellow
3 - Green
4 - Blue
5 - Purple
```

# Task 4: Extension

> **Filename**: for_loops4.py

## 4.1 Requirements

You're organising a party and you have invited 10 people to come. You will need some drinks, snacks, and decorations. Instead of providing them yourself, you've asked each person to bring something to contribute.

You don't mind what they bring, so long as they bring something.

1. Create a list of **ten** guests (make up the names)
2. Copy the following lists into ``for_loops4.py``

```python
snacks = ["chips", "pretzels", "popcorn", "sausage rolls", "pies", "pizzas", "jet planes", "milk bottles", "lollipops", "fruit jubes"]
drinks = ["sparkling water", "orange juice", "cranberry juice", "iced tea", "aloe drink"]
decorations = ["balloons", "streamers", "bunting", "tinsel", "party hats", "gift crackers", "baubles"]
```

3. Print an invitation to each guest, asking them to bring:
   - a random number of bottles a randomly-chosen drink
   - a random number of packets of a randomly-chosen snack
   - a random decoration

## 4.2 Example output

```
Rose is bringing 3 bottles of orange juice, 2 packets of chips, and tinsel
Mickey is bringing 2 bottles of iced tea, 4 packets of jet planes, and bunting
Jackie is bringing 5 bottles of sparkling water, 3 packets of pretzels, and balloons
```

You will have ten guests, not just three.

## How to generate a random number

1. At the top of your Python file, add this line:
```python
from random import randint
```
2. Use the ``randint(x)`` function, replacing ``x`` with the maximum number to generate **or** the length of the list (if you generating a random index)