---
title: Next steps
grand_parent: 11DIT
parent: Programming
nav_order: "ab"
learning_intentions: ["Use loops to repeat code", "Convert numbers to floating point values (numbers with decimals)", "Use conditional statements (such as ``if``, ``else``, and ``elif``) to apply logic"]
success_criteria: ["Added new features to the wall paint calculator according to the new specifications"]
---

If you've finished the recap tasks in 1.0, well done! If not, you'll need to go back and finish the wall paint calculator before you move on to these tasks. Don't worry if it takes you a bit longer — it's important that you revise fully rather than race through the activities.
	
In this lesson, you will use floating point numbers, loops, and conditional statements. You've already used integers so this will only require a minor change. Some of the other constructions, such as loops and conditional statements, might need a bit of revision.

# Task 1: Improved wall paint calculator

> **Filename**: paint2.py

## 1.1 Requirements

In this task, you will improve the wall paint calculator to match the following new specifications:

1. Instead of 1 L of paint per square metre, the walls now require 0.8 L of paint per square metre
2. After you have told the user how much paint they need, ask for the next wall.

## 1.2 Statements to use

- ``float()``
  - This function converts strings representing a valid decimal number to a number type. You should store this in a variable
  - ```python
    meaning_of_life = float(42.0)
    ```
- ``while``
  - This block causes code contained within it to repeat
  - After the ``while`` keyword, a condition must be given
  - If the condition is equal to ``True``, the code will run again
  - ```python
    i = 0
    while i < 10:
        print("Beep")
        i = i + 1
    ```
  - ```python
    answer = ""
    while answer == "":
        answer = input("Should we continue? ")
    ```

## 1.3 Example output

```
Please type the wall width in metres: 4
Please type the wall height in metres: 3

You will need 9.6 L of paint.

Please type the wall width in metres: 6
Please type the wall height in metres: 3.4

You will need 16.32 L of paint.
```

# Task 2: Refined wall paint calculator

> **Filename**: paint3.py

## 2.1 Requirements

In this task, you will improve the wall paint calculator (again) to match the following new specifications:
	
1. After each wall's paint is calculated, ask the user if they would like to calculate the next wall.
2. If they answer yes, ask for the next wall.
3. If they answer no, calculate the total litres of paint needed for all the walls that was calculated, print it, and then close the program.

## 2.2 Statements to use

- ``if``
  - This block will only cause the code contained within it to run if the condition evaluates to True
  - Otherwise, the code will be skipped
  - ```python
    if my_variable == 1:
        print("One")
    ```
- ``elif``
  - This block must come after the ``if`` block
  - It allows you to specify a different condition and different code to run
  - You can add as many ``elif`` blocks as you need
  - ```python
    if my_value == 1:
        print("One")
    elif my_value == 2:
        print("Two")
    ```
- ``else``
  - This block must come at the end of a chain of conditional statements: after the last ``elif`` block, or after the if block when there are not ``elif`` blocks)
  - This specifies the code that should be run if none of the conditional statements above evaluate to ``True``
  - ```python
    if my_value == 1:
        print("One")
    elif my_value == 2:
        print("Two")
    elif my_value == 3:
        print("Three")
    else:
        print(my_value)
    ```

## 2.3 Example output

```
Please type the wall width in metres: 4
Please type the wall height in metres: 3
You will need 9.6 L of paint.

Do you want to calculate another wall: yes

Please type the wall width in metres: 6
Please type the wall height in metres: 3.4
You will need 16.32 L of paint.

Do you want to calculate another wall: no

You will need 25.92 L of paint.
```
