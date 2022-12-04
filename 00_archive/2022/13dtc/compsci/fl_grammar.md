---
title: Formal Grammars & Parsing
grand_parent: 13DTC
parent: L3 Computer Science
nav_order: "ac"
---

# What is a formal grammar?

{% include shout.html side="left" emote="📓" markdown="As with spoken and written languages, formal languages contain a **grammar** that describes the rules of the language — what constitutes valid input. The grammar describes how the language's **alphabet**, or list of the smallest inputs that might trigger a transition." %}

For example, in the [number parsing task](fl_fsm#task-2) in [Finite State Machines](fl_fsm), the alphabet was:

| --- | --- | --- | --- | --- | --- |
| 0 | 1 | 2 | 3 | 4 | 5 |
| 6 | 7 | 8 | 9 | . |   |

By joining these characters in various ways, you can create valid numbers according to the rules of our finite state machine.

## What's in a grammar?

The alphabet in a formal language is manipulated according to the language's rules, the grammar. A grammar consists of:

1. a finite alphabet, or list of acceptable strings, called ``∑`` (sigma). The alphabet can be letters, numbers, symbols, or even words.
2. a finite set of non-terminal symbols, called ``N``. These symbols are acceptable input but will not figure in the output.
3. a start symbol called ``S``. It is also a non-terminal symbol, but we treat it separately.
4. a finite set of rules, called ``R``.  Rules accept a left-hand side (LHS), which starts with ``S``, that is transformed to a result called the right-hand side (RHS).
    - If the RHS contains non-terminal symbols (from ``N``), it becomes the LHS for another rule. These rules are applied **recursively**.
    - If the RHS contains only symbols from ``∑``, the input is valid and the RHS is the output.

## Example 1: currency string builder

For example, let's add a new feature to our number parser: let's add a currency symbol (``$``, dollar sign) to the front to build a currency string.

The number parser has the following specifications:

- it is a valid currency string only if it contains 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, a decimal point, or a dollar sign
- there can only be one (1) decimal point
- the decimal point must have numbers on either side
- there can be any number of digits before the decimal point
- there must only be two (2) digits after the decimal point
- there must be one (1) dollar sign at the front of the input

These rules are expressible with the following grammar:

- ``∑`` is ``{0, 1, 2, 3, 4, 5, 6, 7, 8, 9, $, .}``
- ``N`` is ``{S, n, d}``
  - ``S`` also represents our start symbol
  - ``n`` represents any string of numbers
  - ``d`` represents a single digit
- ``R`` is:
    1. ``S -> $n.dd``
    2. ``n -> d``
    3. ``n -> dn``
    4. ``d -> 0``
    5. ``d -> 1``
    6. ``d -> 2``
    7. ``d -> 3``
    8. ``d -> 4``
    9. ``d -> 5``
    10. ``d -> 6``
    11. ``d -> 7``
    12. ``d -> 8``
    13. ``d -> 9``

Let's examine each piece in detail.

### ∑: the alphabet

{% include shout.html side="left" emote="∑" markdown="This is the alphabet or list of valid characters/words. Not only are these the only allowed characters/words, these are the only valid output resulting from ``R``." %}

### N: the non-terminal symbols

{% include shout.html side="left" emote="N" markdown="These are the non-terminal symbols. Each of these symbols represents a placeholder within the string as the input is transformed by ``R``. None of them are part of ``∑``, so none of them is part of a valid output." %}

### S: the start symbol

{% include shout.html side="left" emote="S" markdown="In this case, ``S`` is represented by ``S`` — this is the whole input string, hence why it's the start symbol — we begin with this input, parse it, validate it, and output it." %}

### R: the rules

{% include shout.html side="left" emote="R" markdown="Each of these rules tells us how to transform the input at each stage in the process. For example, rule 1 tells us that ``S`` LHS should be transformable to ``$n. dd`` RHS." %}

For instance, given a string ``$2.34``, the rules could be applied like so:

1. rule 1
    - rule: ``S -> $n.dd``
    - output: ``$n.dd``
    - because this is the start, therefore we use ``S`` which is our ``S``. There is only one rule that can be applied to ``S``, which is rule 1.
2. rule 2
    - rule: ``n -> d``
    - output: ``$d.dd``
    - because ``n`` is the only non-terminal symbol (from ``N``) left to parse; the applicable rule is 2, since there is only one digit between the dollar sign and the decimal point.
3. rule 6 
    - rule: ``d -> 2``
    - output: ``$2.nn``
4. rule 7
    - rule: ``d -> 3``
    - output: ``$2.3n``
5. rule 8
    - rule: ``d -> 4``
    - output: ``$2.34``

Because no more rules can be applied, the input is considered valid according to the grammar — the output is ``$2.34``, same as the input.

# Task 1: 1 to A, 2 to B

Create a state transition table for an FSM that can transform integer numbers from numbers to letters and vice-versa.

- each digit ``N`` is transformable to the letter at ``N`` position in the alphabet. For instance, ``1`` is ``A``, ``2`` is ``B``, etc.
  - ``0`` is transformable to ``J``
- on the other hand, each letter is transformable back to the number value. For instance, ``C`` is ``3``, ``D`` is ``4``, etc.
- letters can only be upper cased
- input can contain a mix of numbers and letters
- the string can be any length

Here are some examples of valid inputs:

| Valid | Reason for validity |
| :-: | :-- |
| ``1`` | Contains a digit, which will transform to ``a`` |
| ``A`` | Contains a letter, which will transform to ``1`` |
| ``BABE`` | Contains letters which will transform to ``2125`` |
| ``0145`` | Contains digits which will transform to ``JADE`` |
| ``43EGA6`` | Contains a mixture of digits and letters which will transform to ``DC571F`` |

And here are some invalid inputs:

| Invalid | Reason for invalidity |
| :-: | :-- |
| ``0.1`` | ``.`` cannot be transformed |
| ``XYZ`` | These letters cannot be transformed |
| ``abc`` | Letters must be upper cased |

# Task 2: grammar table

Based on your understanding of how this FSM works, let's define the formal language to express the rules for determining if input is valid and what the output should be.

As a class, we'll fill out this table together. Create a copy for yourself (in a Word document or on paper) so that you have a version to use for Task 3.

| | | |
| :-- | :-- | --: |
| **∑** | alphabet | |
| **N** | non-terminal symbols | |
| **S** | start symbol | |
| **R** | rules | |

# Task 3: complex numbers

Using the grammar (``∑``, ``N``, ``S``, and ``R``) you've come up with, determine the following for the listed inputs:

- show the steps (and which rule applies to each step)
- whether the input is valid

1. `1234`
2. `JADE`
3. `ACCP`
4. `1B3D`
5. `75Z4`

In a Word document or on paper, show the steps in the following format (this example is for the currency parser, **do your task for the number-letter converter**):

| Input | Rule | Output |
| :-- | :-: | :-- |
| `$128.39` | 1 | `$n.dd` |
| `$n.dd` | | |

# Task 4: create your own grammar

Create a formal grammar for a program that **creates** a sentence.

{% include shout.html emote="⚠️" side="left" markdown="This grammar does not accept input. Instead, it will only create output. Bear that in mind as you create the alphabet." %}

This program has the following specifications:

- the sentence must start with 'A' or 'The'
- the second word must be one of the following adjectives:
  - big
  - small
  - furry
  - squishy
  - wet
  - dry
- the third word must be one of the following nouns:
  - cat
  - dog
  - cheese
  - cloud
  - student
- the fourth word must be one of the following verbs:
  - runs
  - eats
  - sits
  - wobbles
  - shakes
- the last word must be one of the following adverbs:
  - quickly
  - hastily
  - disturbingly
  - awfully
  - pleasantly
- Finally, the end of the sentence must have an exclamation mark

For example, the program could output: `The big cat runs quickly!`