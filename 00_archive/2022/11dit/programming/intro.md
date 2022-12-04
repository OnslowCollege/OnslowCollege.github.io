---
title: (Re)Intro to Python
grand_parent: 11DIT
parent: Programming
nav_order: "aa"
learning_intentions: ["To assign and use data stored in variables", "Printing text and getting user input", "Converting strings to numbers and back"]
success_criteria: ["You have created the 'Hello, student!' program, tested it, and shown your teacher that it works", "You have created the basic wall calculator program"]
---

If you took 10DIT at Onslow College last year, then welcome back! It's time to get our minds back into programming. Hopefully you haven't forgotten all your Python — if you have, don't worry, it's just like riding a bike! (and if you haven't been on a bike before, don't worry, it'll all come back just the same!)

# Task 1: Hello, student!

> **Filename**: hello.py

## 1.1 Requirements

In this task, you will be asked to make a **very** simple program. Using Python, you will:
-   Ask the user for their name.
-   Greet the user by their name.

## 1.2 First steps

In order to create the program:
- Open Visual Studio Code
- Click Open Folder and select the 11DIT Python folder in your OneDrive
- At the top of the Explorer pane (top-left), click the New File button
- Create a new file called **Hello.py**
- Write your code on the right
- Run your code by clicking the Run Python File at the top-right

## 1.3 Statements to use

- ``print()``
  - This function will 'print' the text that is contained within the brackets and quotation marks to the screen
  - ```python
    print("Hello, world!")
    ```
- ``input()``
  - This function will 'print' the text that is contained within the brackets and quotation marks to the screen
  - The user then types something, presses Enter/Return, and whatever they entered is stored in a variable
  - ```python
    age = input("How old are you?")
    ```

## 1.4 Example output

```
Please type your name: Bob
Hello, Bob!
```

# Task 2: Wall paint calculator

> **Filename**: paint1.py

## 2.1 Requirements

In this task, you will do some simple maths to calculate how many litres of paint will be required to coat a wall. Using Python, you will:

-   Ask the user for the width in metres of the wall
-   Ask the user for the height in metres of the wall
-   Tell the user how much paint is required in litres

For every square metre, the user will need 2 L of paint.

(Yes, this is excessive, but it's an exercise, go with it)

## 2.2 Statements to use

This task will involve casting. This means you will convert a variable from a string to an integer. To do this, make use of the ``int()`` function:

- ``int()``
  - This function converts strings representing a valid integer to a number type. You should store this in a variable
  - ```python
    age = int("14")
    ```
  - ```python
    age = int(input("How old are you?"))
    ```
- Math operations
  - ``+`` to add two numbers together
  - ``-`` to subtract the right-hand side from the left-hand side
  - ``*`` to multiply two numbers together
  - ``/`` to divide the left-hand side by the right-hand side
  - ```python
    age_in_10_years = age + 10
    age_last_year = age - 1
    double_age = age * 2
    age_squared = age * age
    half_age = age / 2
    ```

## 2.3 Hint

If maths isn't your strong point, don't worry. The formula for determining how much paint is needed for the wall is simple:
```
width * height * paint_per_litre
```

## 2.4 Example output

```
Please type the wall width in metres: 4
Please type the wall height in metres: 3

You will need 12 L of paint.
```

##### When you are finished, move on to [Next Steps](next-steps.md)