---
title: Introduction to Formal Languages
grand_parent: 13DTC
parent: L3 Computer Science
nav_order: "aa"
learning_intentions: ["Learn what a formal language is", "Give examples of what formal languages are used for"]
attribution: Based on the [Computer Science Field Guide](https://www.csfieldguide.org.nz/en/chapters/formal-languages/), adapted under the terms of the [Creative Commons Attribution-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/) license.
---

# What is a formal language?

**Formal languages** are definitions of the rules relating to input. In this case, input can mean:

- programming code
- text
- numbers
- mathematical formulae

The rules are a program's guide to checking that the inputs are valid. For instance, take this programming code:

{% capture right_markdown %}
```python
x = (a+b) * (c+d)
```
{% endcapture %}
{% include half.html right_markdown="✅ All correct" markdown=right_markdown %}
but you accidentally left out one of the brackets:
{% capture right_markdown %}
```python
x = (a+b) * c+d)
```
{% endcapture %}
{% include half.html right_markdown="❌ Missing `(`" markdown=right_markdown %}

In the case of the above code, the commands and calls you make in a programming language such as Python are read by another program called a *compiler* (for compiled languages, such as C, C++, C#, Java, Rust, Swift, etc.) or *interpreter* (for interpreted languages, such as JavaScript, PHP, Python, Ruby, etc.).

In order for the compiler/interpreter to understand your program, you must write your code according to strict rules called a **formal grammar**.

If the grammar for the above code states that all brackets must be balanced (i.e. a ``(`` paren should be paired with a ``)`` paren), then the second code snippet fails to meet the requirements of the grammar — it doesn't follow the rules — so the compiler/interpreter rejects the code.

This means that the code cannot be converted to a program until the code is adjusted to follow the grammar properly.

## Not just for programming languages

Formal languages can be used for a lot of different purposes, so long as there is input to check, rules for validating the input, and grammar to verify the input against.

{% capture right_markdown %}
For example:

- detecting telephone numbers
- checking that a date, given as a string, is valid
- making sure an email address contains an ``@`` and top-level domain
- validating text submitted to a form
- determining whether or not a mathematical formula can be evaluated
{% endcapture %}

{% include shout.html emote="☎️" side="right" markdown=right_markdown %}

Some advanced concepts in formal languages are even used to explore limits of what can be computed.

# Next steps

{%include shout.html emote="➡️" side="left" markdown="To better understand formal languages, let's take a look at the valid states of a program or process (i.e. when the input is valid). This is covered in [Finite-State Machines](fl_fsm)." %}