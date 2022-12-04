---
title: Practice assessment feedback
grand_parent: 12DTC
parent: Advanced Programming
nav_order: "zb"
---

# Issues that prevented Achieved

If you did not receive Achieved, this may have been due to one of the following issues:

1. Your testing table was incomplete
2. Your program had a severe crash or bug that prevented it from performing the specified task
3. Your program lacked sufficient use of advanced techniques
4. Your program did not contain sufficient comments

## Incomplete testing table

Your testing table may have been deemed incomplete if:

1. It did not contain a sufficient number of expected cases to cover the entire program
    - For example, you may have only accounted for a single input (such as the main menu), and no other inputs (submenus, valid title lengths, valid durations, second-to-HH:mm conversion, etc.)
2. Your expected input was empty or not descriptive enough
3. Your actual results showed a crash or bug but did not show any evidence that you had fixed it in a subsequent test
4. Your comments or notes on what to fix were not specific enough

## Severe crash or bug

If the program was not able to perform the specified task, then your assessment would not have been able to receive an Achieved grade.

In some cases, the program would crash when trying to perform a certain task (such as showing movie durations with the List command) but would work fine when performing other tasks (such as showing movie durations after adding a movie or editing an existing movie's duration).

In other cases, the program had a major bug which would cause unexpected output, such as incorrect calculations.

## Insufficient advanced techniques

Your program must have contained any of the following:

- **modifying** (not just storing, but also being able to modify) data stored in **TWO** (2) collections
- storing multidimensional data in collections, including:
    - lists of lists (2D lists)
    - lists of dictionaries
    - dictionaries containing a list as an item/value
    - dictionaries containing other dictionaries as an item/value
- functions that **either** accepted parameters, returned values, or both
    - functions that did not use either of those features do not count

## Insufficient commenting

Comments are required for Achieved in the programming standard. Some of you did not include enough comments; a few didn't include any at all.

Please take a look at the [11DIT comments course](/00_archive/2022/11dit/programming/comments.md) for information on good commenting practice.

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
    - For example, you may have only accounted for a single input (such as the main menu), and no other inputs (submenus, valid title lengths, valid durations, second-to-HH:mm conversion, etc.)
2. It did not contain tests for either side of the boundary
    - Boundary testing must include values on both the **valid** and **invalid** side of the boundary
    - For example, if the lowest value allowed for an input is ``1``, you should also test ``0`` and ``2``

## Lack of constants

For Merit, your program should contain constants — these are like variables except that the values never change in the lifetime of the program.

Suitable candidates for constants include the minimum and maximum length of a movie title, and the minimum and maximum duration for a movie.

Most of you did have this information but stored them as variables. To change them to constants, use ``ALL_UPPER_CASE`` naming instead of ``all_lower_case``.

```python
# minimum_duration = 1
MINIMUM_DURATION = 1
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
# min = 1
minimum_duration = 1

# d = input("How long? ")
duration = input("What size? ")

# icons = ["🏔", "🎥", "🗑"]
MENU_ICONS = ["🏔", "🎥", "🗑"]
```

## Insufficient commenting

At Achieved, comments just need to briefly describe what the block of code does. However, the step-up for Merit is to describe code function and behaviour.

This means that you should explain your choices with each code block. For example:
- why do you do a particular conditional check?
- why must a certain condition be satisfied before the program continues?
- why does the loop repeat a certain number of times?
- why do you call a particular function?

Furthermore, your comments should have been commented using docstrings. This is also required for compliance with Python conventions. This is documented in all of the functions course: [1](functions-basic.md#documenting-the-function), [2](functions-return.md#documenting-the-return-type), and [3](functions-args.md).

This also includes annotating the type of the returned value as well as each parameter's type.

### Achieved example

```python
def check_duration(duration):
    # Prints message if movie is too long
    if duration >= MAXIMUM_DURATION:
        print("Sorry, the duration must be 5999 seconds or fewer. Please try again.")
        return False
    else:
        return True
```

### Merit example

```python
def check_duration(duration: int) -> bool:
    """
    Returns True if the duration is valid in length
    (less than or equal to 5999 seconds)
    """
    # Checks that the user enters a valid duration. If it is too long,
    # inform the user of the maximum duration and ask them to try again.
    if duration >= MAXIMUM_DURATION:
        print("Sorry, the duration must be 5999 seconds or fewer. Please try again.")
        return False
    else:
        return True
```

# Issues that prevented Excellence

If you did not receive Excellence, this may have been due to one of the following issues:

1. Your testing table was incomplete
2. Your program was not flexible
3. Your program was not robust

## Incomplete testing table

Your testing table may have been deemed incomplete if:

1. It did not contain a sufficient number of **invalid** cases to cover the entire program
    - For example, you may have only accounted for a single input (such as the main menu), and no other inputs (submenus, valid title lengths, valid durations, second-to-HH:mm conversion, etc.)
2. It did not contain tests for either side of the boundary

## Program is not flexible

Your program is not flexible. The main causes of lack of flexibility come from:

1. hard-coded values
2. unnecessary repetition

### Hard-coded values

This occurs when your code contains numbers or values within ``if`` statements or function calls rather than using a constant.

```python
# if duration >= 1 and duration <= 5999:
if duration >= MINIMUM_DURATION and duration >= MAXIMUM_DURATION:
```

### Unnecessary repetition

If you have blocks of code that do roughly the same thing, you could consolidate that into a single block of code that behaves more flexible.

A common issue was code that was repeated between the adding and editing sections of your program. For example, you may have copy-pasted the code to convert the movie's seconds into the HH:mm timestapm, rather than put that code into a function and call that function multiple times.

## Program is not robust

Your program experienced a crash or could not perform part or all of the specified task. At this grade, your program is expected not to crash in any circumstance.

The major causes of crashes at this level:

- you have not completed your testing to a sufficient degree
- you have not used conditional statements (``if``/``elif``/``else``) to check boundaries
- you have not used ``try``/``except`` to catch errors, or have not caught all possible errors