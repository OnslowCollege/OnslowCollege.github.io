---
title: Collections Task — Morse code translator
grand_parent: 12DTC
parent: Advanced Programming
nav_order: "bi"
---

# Task

## Scenario

Your early start to university is going great until eventually, due to various circumstances, you are forced to move to online-only learning.

Except, not on the internet.

Over **telegraph machine**.

Why? … Because! That's why.

## Requirements

1. Create a program that allows you to communicate via telegraph machine by converting text to Morse Code
2. Morse code uses the format specified in [Representation](#representation)
3. You will be provided with sample text in the assignment. The results will be provided in tests
  - Make sure that your program converts the sample text to morse code correctly by ensuring that the tests pass

Feel free to print the morse code as you develop it in order to test that your code is working properly.

# Morse Code

[Morse Code](https://en.wikipedia.org/wiki/Morse_code) is a communication method where letters and numbers are converted to electronic signals — short signals called **dots** and longer signals called **dashes**.

The most common letters are represented with the shortest signals. For example, the letter E is represented with a single dot. On the other hand, the letter Y is represented by a dash, a dot, and two more dashes.

## Representation

To represent these on a computer, you will substitute the dots and dashes with text characters.

| Signal | Character | |
| --: | :-- | :-- |
| Dot | asterisk | ``*`` |
| Dash | dash | ``—`` |
| Space | new line | ``\n`` |

- Each character's signal will be separated from the ones around it by a space.
- Each character aside from the last one will be followed by a comma.

For example:

- the letter Y: ``- * - -``
- the words "onslow college":
  - ```
    - - - , - * , * * * , * - * * , - - - , * - -
    - * - * , - - - , * - * * , * - * * , * , - - * , *
    ```

## Alphabet, numbers, and symbols

| Alpha | Morse | Number | Morse |
| --: | :-- | --: | :-- |
| a | dot **DASH**  | 1 | dot **DASH**  **DASH** **DASH**  **DASH** |
| b | **DASH** dot dot dot | 2 | dot dot **DASH**  **DASH** **DASH**  |
| c | **DASH** dot **DASH** dot | 3 | dot dot dot **DASH** **DASH** |
| d | **DASH** dot dot | 4 | dot dot dot dot **DASH**  |
| e | dot | 5 | dot dot dot dot dot |
| f | dot dot **DASH** dot | 6 | **DASH** dot dot dot dot
| g | **DASH** **DASH** dot | 7 | **DASH** **DASH** dot dot dot |
| h | dot dot dot dot | 8 | **DASH** **DASH** **DASH** dot dot |
| i | dot dot | 9 | **DASH** **DASH** **DASH** **DASH** dot |
| j | dot **DASH** **DASH** **DASH**  | 0 | **DASH** **DASH** **DASH** **DASH** **DASH**  |
| k | **DASH** dot **DASH**  | full stop | dot **DASH** dot **DASH** dot **DASH**  |
| l | dot **DASH** dot dot | comma | **DASH** **DASH** dot dot **DASH** **DASH** |
| m | **DASH** **DASH** | question mark | dot dot **DASH** **DASH** dot dot |
| n | **DASH** dot | apostrophe | dot **DASH** **DASH** **DASH** **DASH** dot |
| o | **DASH** **DASH** **DASH**  | exclamation mark | **DASH** dot **DASH** dot **DASH** **DASH** |
| p | dot **DASH** **DASH** dot | left parenthesis | **DASH** dot **DASH** **DASH** dot |
| q | **DASH** **DASH** dot **DASH**  | right parenthesis | **DASH** dot **DASH** **DASH** dot **DASH**  |
| r | dot **DASH** dot | colon | **DASH** **DASH** **DASH** dot dot dot |
| s | dot dot dot | plus | dot **DASH** dot **DASH** dot |
| t | **DASH**  | minus | **DASH** dot dot dot dot **DASH**  |
| u | dot dot **DASH**  | double quote | dot **DASH** dot dot **DASH** dot |
| v | dot dot dot **DASH**  | dollar sign | dot dot dot **DASH** dot dot **DASH**  |
| w | dot **DASH** **DASH** | at sign | dot **DASH** **DASH** dot **DASH** dot |
| x | **DASH** dot dot **DASH**  | 
| y | **DASH** dot **DASH** **DASH** |
| z | **DASH** **DASH** dot dot |

{% include task.html task_code="9q7OopVJ" %}
