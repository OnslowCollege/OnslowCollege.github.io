---
title: Assessment Practice — Feedback
grand_parent: 11DIT
parent: Programming
nav_order: "zb"
---

# Issues that prevented Achieved

If you did not receive Achieved, this may have been due to one of the following issues:

1. Your testing table was incomplete
2. Your program had a severe crash or bug that prevented it from performing the specified task
3. Your program did not contain at least **two** (2) types of data (text, number, Boolean, etc.)
4. Your program did not contain **and use** at least **two** (2) lists and/or functions
5. Your program did not contain sufficient comments

## Incomplete testing table

Your testing table may have been deemed incomplete if:

1. It did not contain a sufficient number of expected cases to cover the entire program
    - For example, you may have only accounted for a single input (such as the main menu), and no other inputs (jeans sizes, shoe sizes, friend selection, etc.)
2. Your expected input was empty or not descriptive enough
3. Your actual results showed a crash or bug but did not show any evidence that you had fixed it in a subsequent test
4. Your comments or notes on what to fix were not specific enough

## Severe crash or bug

If the program was not able to perform the specified task, then your assessment would not have been able to receive an Achieved grade.

In some cases, the program would crash when trying to perform a certain task (such as printing shoe sizes) but would work fine when performing other tasks (such as printing jeans sizes).

In other cases, the program had a major bug which would cause unexpected output, such as incorrect calculations.

## Did not contain at least two different types of data

Many people only used strings in their program. Even if the strings contained numerical or Boolean values, they are still strings — this only constitutes **one** (1) type of data. The minimum is two.

Other types of data could have included:

1. numbers (``int`` or ``float``)
    - the sizes of the jeans and shoes could have been stored as numbers or lists of numbers
      - ```python
        # JEANS_SIZES = ["1", "2", "3", "4", "5"]
        JEANS_SIZES = [1, 2, 3, 4, 5]
        ```
    - the friends sizes could have been stored as numbers, lists of numbers, or ranges of numbers
      - ```python
        # MAIA_JEANS_SIZES = ["1", "2"]
        MAIA_JEANS_SIZES = [1, 2]
        MAIA_SHOE_SIZE = 8
        # or
        MAIA_JEANS_SIZES = range(1, 3)
        ```
    - these sizes could have been stored as ``int`` or ``float``
      - ``int`` is most appropriate, although ``float`` could work if there are half sizes (such as size 10.5 shoes)
2. Booleans
    - many of you used strings like Booleans, by storing values such as ``"true"`` or ``"false"``
    - real Python booleans do not have quotation marks and begin with capital letters
      - ``True``
      - ``False``

Although lists are technically a type, we don't count these as data types for the purpose of the assessment.

## Lacking or improperly using lists

If your program did not contain at least **two** (2) lists, you could not receive an Achieved grade. The exception is if your program contained at least two functions.

Lists are essential for the program since you have multiple collections of data: many shoe sizes, many jeans sizes, the sizes for each of the friends, etc.

Your lists should also contain data in a way that is useful. Storing a list of strings that say things like ``"2x pairs of size 28 jeans"`` isn't useful because you can't perform calculations, another requirement of the task, using these.

Here are two approaches that use lists in a more useful manner:

First, you could store the sizes in a single list. Repeat each item as many times as needed — these can be counted later with a for loop.

```python
# 2x pairs of size 28
# 4x pairs of size 30
# 1x pair of size 32

JEANS_SIZES = [28, 28, 30, 30, 30, 30, 32]

input_size = 30
counter = 0

for size in JEANS_SIZES:
    if size == input_size:
        counter = counter + 1

print(counter)  # 4
```

Below is another valid but less-recommended approach. The sizes are already counted and stored in a separate list.

However, if a particular size ever needs to be removed (i.e. Maia threw them away), that size's details have to be removed from two separate lists instead of one.

```python
# 2x pairs of size 28
# 4x pairs of size 30
# 1x pair of size 32

JEANS_SIZES = [28, 30, 32]
JEANS_SIZES_COUNT = [2, 4, 1]
```

## Insufficient commenting

Comments are required for Achieved in the programming standard. Some of you did not include enough comments; a few didn't include any at all.

Please take a look at the [comments course](comments.md) for information on good commenting practice.

# Issues that prevented Merit

If you did not receive Merit, this may have been due to one of the following issues:

1. Your testing table was incomplete
2. Your program did not contain constants
3. Your program's variables and/or constants had non-specific or ambiguous names
4. Your program did not contain sufficiently detailed comments
5. Your program did not conform to PEP-8

## Incomplete testing table

Your testing table may have been deemed incomplete if:

1. It did not contain a sufficient number of **boundary** cases to cover the entire program
    - For example, you may have only accounted for a single input (such as the main menu), and no other inputs (jeans sizes, shoe sizes, friend selection, etc.)
2. It did not contain tests for either side of the boundary
    - Boundary testing must include values on both the **valid** and **invalid** side of the boundary
    - For example, if the lowest value allowed for an input is ``1``, you should also test ``0`` and ``2``

## Lack of constants

For Merit, your program should contain constants — these are like variables except that the values never change in the lifetime of the program.

Suitable candidates for constants include the clothing inventory sizes, friends' fitting sizes, and menu items (if you stored them in a list).

Most of you did have this information but stored them as variables. To change them to constants, use ``ALL_UPPER_CASE`` naming instead of ``all_lower_case``.

```python
# jeans_sizes = [1, 2, 3]
JEANS_SIZES = [1, 2, 3]
```

## Variable and constant names

Your variable and constant names need to be descriptive. You may have had some variables with generic or confusing names such as ``x``, ``loop``, etc.

Where possible, use names that describe what the variable or constant is expected to contain. Be as verbose as necessary.

Avoid the following:

1. Single-letter variable or constant names
2. Mixed case names
    - variables are ``all_lower_case``, not ``Mixed_Case``
    - variables are in ``snake_case``, not ``camelCase``
    - constants are in ``ALL_UPPER_CASE``

```python
# valid = False
valid_size = False

# size = input("What size? ")
user_size = input("What size? ")

# JEANS = [1, 2, 3]
JEANS_SIZES = [1, 2, 3]
```

## Insufficient commenting

At Achieved, comments just need to briefly describe what the block of code does. However, the step-up for Merit is to describe code function and behaviour.

This means that you should explain your choices with each code block. For example:
- why do you do a particular conditional check?
- why must a certain condition be satisfied before the program continues?
- why does the loop repeat a certain number of times?
- why do you call a particular function?

### Achieved example

```python
# Prints message if none found
if jeans_counter == 0:
    print("Sorry, no items were found in that size")
```

### Merit example

```python
# If no items are found, print a separate message
# that tells the user no such items exist in the
# inventory — instead of just printing '0x pairs of jeans'
if jeans_counter == 0:
    print("Sorry, no items were found in that size")
```

# Issues that prevented Excellence

If you did not receive Excellence, this may have been due to one of the following issues:

1. Your testing table was incomplete
2. Your program was not flexible
3. Your program was not robust

## Incomplete testing table

Your testing table may have been deemed incomplete if:

1. It did not contain a sufficient number of **invalid** cases to cover the entire program
    - For example, you may have only accounted for a single input (such as the main menu), and no other inputs (jeans sizes, shoe sizes, friend selection, etc.)
2. It did not contain tests for either side of the boundary

## Program is not flexible

Your program is not flexible. The main causes of lack of flexibility come from:

1. hard-coded values
2. unnecessary repetition

### Hard-coded values

This occurs when your code contains numbers or values within ``if`` statements or function calls rather than using a constant.

```python
# if size >= 26 and size <= 28:
if size >= MAIA_JEANS_MIN and size <= MAIA_JEANS_MAX:
```

### Unnecessary repetition

If you have blocks of code that do roughly the same thing, you could consolidate that into a single block of code that behaves more flexible.

The most common issue was code for the jeans and shoes sections that were more-or-less identical, or code for each of the three friends that were also the same except for the names.

You could use ``if`` statements to check what is being searched and printed (jeans vs. shoes; Maia vs Bill vs Trent), set new variables to the value being checked, and have code that you only write once.

```python
# if clothing_choice == 1:
#   print("You have x pairs of jeans")
# elif clothing_choice == 2:
#   print("You have x pairs of shoes")
CLOTHING = ["jeans", "shoes"]
print("You have x pairs of " + CLOTHING[clothing_choice - 1])
```

```python
# if user_choice == 1:
#   print("Maia can fit " + …)
# elif user_choice == 2:
#   print("Trent can fit " + …)
# elif user_choice == 3:
#   print("Bill can fit " + …)

FRIENDS = ["Maia", "Trent", "Bill"]
print(FRIENDS[user_choice - 1] + " can fit " + …)
```

## Program is not robust

Your program experienced a crash or could not perform part or all of the specified task. At this grade, your program is expected not to crash in any circumstance.

The major causes of crashes at this level:

- you have not completed your testing to a sufficient degree
- you have not used conditional statements (``if``/``elif``/``else``) to check boundaries
- you have not used ``try``/``except`` to catch errors, or have not caught all possible errors