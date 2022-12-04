---
title: Try/Except
grand_parent: 11DIT
parent: Programming
nav_order: "ca"
learning_intentions: ["Prevent crashes in your program my handling errors and exceptions"]
success_criteria: ["Prevent a crash when trying to convert a string to a number", "Prevent a crash when trying to access a list item that does not exist"]
---

# Try/Except

When an error occurs, or **exception** as we call it, Python with **raise an exception** — this will print out an error message and then crash your program.

We can **handle** the exceptions to prevent crashes from occuring. This makes use of **try**/**except** blocks.

```python
try:
    # Code that could raise an Exception
except:
    # Code that happens if an Exception is raised
    # If no Exception is raised, this code will not run
```

For example, you could print a message out:

```python
try:
    x = 1 / 0
    print(x)
except:
    print("Cannot divide by zero")
```

# Task 1: First try/except

> **Filename**: tryexcept1.py

## 1.1 Requirements

1. Add ``try``/``except`` to the following code:
   - ```python
     a = int(input('Which floor do you live on?'))
     if a > 6:
         print("Wow, you live above me!")
     elif a < 6 and a > 0:
         print("What's it like down there?")
     elif a < 0:
         print("You live in the basement?")
     else:
         print("Hey, we're neighbours!")
     ```
2. Fix the ``if`` statements so that entering floor number ``0`` says ``"Uh, you live in the lobby?"``
3. Test that your exception handler works by:
   - Typing the floor number ``potato``
   - Typing the floor number ``12``
   - Typing the floor number ``-1``
   - Typing the floor number ``6``
   - Typing the floor number ``0``

# Task 2: try/except for specified Exceptions

> **Filename**: tryexcept2.py

## 2.1 Requirements

1. Add ``try``/``except`` to the following code:
   - ```python
     a = int(input('Divide by how much?'))
     print(b) # ⛔️ DO NOT CHANGE THIS LINE
     ```
2. Handle ``ValueError`` separately from other errors
   - This means you will have **two** ``except`` blocks
3. Test that your exception handlers work by:
   1. Typing the index ``potato``
   2. Typing the index ``-1``
   3. Typing the index ``5``

## 2.2 Exception types

There are many different types of ``Exception``s. Each type is raised in response to a different error.

For example:

- ``AttributeError`` is raised when you try changing data that cannot be changed
- ``IndexError`` is raised when you try to access a list index that does not exist
- ``NameError`` is raised when you try to access a variable or constant that does not exist
- ``ValueError`` is raised when a function or statement is given the incorrect type of data
- ``ZeroDivisionError`` is raised when trying to divide a number by zero

[You can see a list of other common ``Exceptions`` here.](https://www.tutorialsteacher.com/python/error-types-in-python)

## 2.3 Handling specific Exceptions

You can handle specific errors by putting the ``Exception`` name after the ``except`` keyword.

```python
try:
    # Code that could raise an Exception
except NameError:
    # Code that happens if NameError exception is raised
except:
    # Code that happens if any other exception is raised
```

# Task 3: try/except in context

## 3.1 Requirements

> **Filename**: tryexcept3.py

1. Add ``try``/``except`` to the following code:

   - ```python
     ##
     # enrolment.py
     # Enrols a student in ONE course

     VALID_COURSES = ['MAT', 'ENG', 'SCI', 'DIT', 'ART', 'FRE', 'SPA', 'JPN']

     # Welcome the user to the school and get their name
     print("Welcome to Onslow College.")
     name = input("Please enter your name: ")

     # Ask for the student's age
     print("You need to be aged between 12 and 19 to enrol.")
     age = int(input('How old are you?'))
     print("Great! You are " + str(age) + "years old.")

     # Ask what course to join
     finished = False
     while finished == False:
         course = input('Please enter the three letter code for the course: ')
         if i in range(0, len(VALID_COURSES)):
             print("You are now enrolled in" + VALID_COURSES[i].upper() + ', ' + name + ". Have a nice day!")
         else:
             print("Sorry, there is no such course. Try again.")
      ```
2. Handle all of the errors separately
   - You **must** specify the ``Exception`` after the ``except`` keyword
3. Add code to ensure that the age is between 12 and 19
4. Test that your exception handlers work by:
    - Typing the age ``potato``
    - Typing the age ``-1``
    - Typing the age ``12``
    - Typing the age ``15``
    - Typing the age ``19``
    - Typing the age ``100``

# Task 4: try/except in your own code

> **Filename**: password_tryexcept.py

## 4.1 Requirements

- Copy your Password Checker code into ``password_tryexcept.py``
- Add ``try``/``except`` to handle all ``Exceptions``

----

# Examples of try/except

## When a performing maths using a string

```python
try:
    age = 20
    age_next_year = age + "1"
except:
    print("Cannot add a string to a number")
```

## When converting a number using invalid data

```python
try:
    age = input("How old are you?") # User types "fourteen" instead of 14
    age = int(age)
except:
    print("You must type a number, not a word")
```

## When attempting to divide by zero

```python
try:
    no_of_pizzas = 3
    no_of_slices = input("Cut the pizza into how many slices?") # User types 0
    no_of_slices = int(no_of_slices)
    pizza_slice_count = no_of_pizzas / no_of_slices
except ValueError:
    # User tried to convert text to a number
    print("You must type a number, not a word")
except ZeroDivisionError:
    # User tried to divide pizza by zero
    print("Cannot divide a pizza into zero slices")
```
   