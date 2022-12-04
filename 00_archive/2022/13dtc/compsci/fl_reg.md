---
title: Regular vs Context-Free
grand_parent: 13DTC
parent: L3 Computer Science
nav_order: "ad"
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/5lXAjh4mdnY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


# Regular

A **regular** language can be defined by a regular expression. A regular language is a context-free language, but not all context-free languages are regular languages.

## Regular expression

Just like in maths, an expression is evaluated: the result is all of the valid strings for that expression. For example, the regex ``[A-Z]{3}[0-9]{3}`` describes all possible valid strings (AAA000, AAA001, AAA002, etc.); these form the language.

> Of course, a computer doesn't need to *actually* generate all of these strings (although it could if you wanted it to). Rather, regular expressions are mostly used to search for valid substrings (parts of a string) within a string **or** validating that a string is in the correct format.

## Always in order

Regular expressions are always evaluated in order, either left-to-right or right-to-left. So, the above example always generates three letters followed by three digits; there is no ambiguity to the order.

Even with metacharacters such as ``.`` (representing any character) or ``*``/``?`` (representing one or none-to-many of a character or expression), these are evaluated in order. Therefore, for the regex ``[A-Z]{3}.{3}``, ABC!@# is valid within the language but !@#ABC can never be.

Therefore, the production rules for a regular language are restricted in the following way:

- a single non-terminal character at the left must transform to:
  - a single terminal character, or
  - a single terminal character followed/preceded by (but not both in the same language) a single non-terminal character

``A → cB``, ``A → c``, ``A → є`` (this symbol means 'none')

These production rules mean that the language can only generate/match in one direction, since any generated non-terminal characters must always be in the same position (either before or after a terminal character, but not both directions in the same language).

# Context-Free

A **context-free** language can be defined by a context-free grammar. A regular language is a context-free language, but not all context-free languages are regular languages.

The major difference is that while regular expressions are always evaluated in order from left-to-right (or right-to-left), context-free grammars can be a bit more ambiguous. Non-terminal characters can transform to other non-terminal characters, to a non-terminal followed by a terminal, to a terminal followed by a non-terminal, or any combination.

Specifically, "context-free" means that a non-terminal character can transform regardless of its *context* (the characters that surround it). Therefore, a rule such as ``A -> B`` (non-terminal to non-terminal) is possible — A can become B, regardless of surrounding characters. Therefore, these are all possible:

- ``A -> B``
- ``xA -> xB``
- ``ZAX -> ZBX``
- ``xyzAxyz -> xyzBxyz``
- ``Aflyingmonkeys -> Bflyingmonkeys``

The flexibility of context-free languages implies that context-free languages have memory: characters can be stored and retrieved again later as a non-terminal character, making them effectively variables. This is because, unlike a regular language, generation can happen in both directions within the same language.

In this way, a context-free grammar can parse or generate a palindrome: a word or phrase that is spelt the same in one direction as the other. For example, "bob", "12321", or even the phrase "rats live on no evil star".

A regular language cannot handle this since it parses only in one direction — since they only parse in one direction, a regular expression cannot go "back" to inspect a previous character, therefore is unable to detect whether the characters at either end (either of the whole string or parts within a string) match.

# Why have both regular and context-free languages?

Due to the difference between these languages, they solve two different problems. Therefore, even though a regular language may seem cruder or more restrictive, they do have a purpose.

Specifically, the way that regular languages work only in one direction makes them suitable for quickly searching for text. Regular expressions are performant because they do not need to consider previous characters in a string. For example, when parsing an email address, this can be done left to right:

1. at least one alphanumerical character
2. any number of alphanumerical characters and/or specific punctuation characters
3. an at symbol
4. any number of
   1. alphanumerical characters followed by a dot
5. any number of alphanumerical characters

At no point in the process would one need to consider characters that have already been parsed nor any characters on either side. This means that an algorithm that implements search or validation based on these principles can be, and usually are, very performant.

On the other hand, context-free languages are suited to more complex kinds of parsing, such as detecting if a programmer's code conforms to the rules of a language; after all, individual words alone do not a programming language make! Rather, a keyword or variable is understood within a broader scope — within brackets, quote marks, blocks, before this, after that, etc.

While a regular expression could search for the presence of ``while`` loops, it could not validate that the while loop is valid. In the case of Python, you would also need fairly complex rules to validate that the condition is valid, the whitespace (both before and after) are the correct number of spaces/tabs, and that the loop body contains valid statements/expressions. If a while loop were indented by four spaces, then only a context-free language would be able to bear in mind:

1. how many spaces preceded the ``while`` keyword:
2. how many spaces are needed for each succeeding line of code in the loop body