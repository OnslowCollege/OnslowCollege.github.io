---
title: Comments
grand_parent: 11DIT
parent: Programming
nav_order: "ac"
learning_intentions: ["Revise good commenting practices"]
success_criteria: ["You have added comment headers to ``hello.swift`` and ``paint3.swift``"]
---

An important part of programming is commenting. After all, most code is read rather than written. You'll thank yourself for writing comments when you come back to a piece of code later, having completely forgotten what it's for.

Not only that: good commenting is required for the assessment!

# Task 1: Header comments

> **Filename**: paint3.swift

## 1.1 Requirements

In this file, you are going to create a header comment for ``paint3.py``. This header comment will tell us some basic information about the program contained in the file:
	
- Who wrote it
- When they started writing it
- When it was last updated

## 1.2 Comment syntax

Remember: comments start with the ``#``. This is called a pound sign, not a hash tag.

## 1.3 Header comment example

```python
##
# Hello, student
# Created by: Erihapeti
# Created on: 25/01/2022
# Updated:    03/02/2022
```

# Task 2: Block comments

> **Filename**: paint3.py

## 2.1 Requirements

In this file, you will add the following comments:
	
1. A header comment
2. Comments above each of the following types of statement
	- ``while``
	- ``if``
    - ``input``

## 2.2 Comment syntax

For each of the block comments, give a brief, one-sentence description of what the code block does. For ``while`` and ``if`` blocks, you could also describe what the condition tests.

### Comment format

- All comments start with a capital letter.
- All comments end with a full stop.
- No comment should exceed the 79 character line limit. If the comment is too long, continue the comment on the next line instead.
	
### Things to avoid

- You don't need to write comments where it is obvious what the code does.
  - ```python
    # Asks the user to type a letter
    letter = input("Please type a letter: ")
    ```
- Comment why and what, not how.
  - ```python
    counter = 3

    # Uses a while loop to run 3 times
    while counter > 0:
        print("Beep")
        counter = counter - 1
    ```