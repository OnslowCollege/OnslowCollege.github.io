---
title: Introduction to programming
nav_exclude: true
learning_intentions: ["Determine a program's requirements", "Break those requirements into a series of steps", "Write a comment for each step", "Write your first program in Python based on your comments"]
success_criteria: ["You have created your first program in Python"]
---

Welcome to the programming course. In this first lesson, we will look at a problem, break it down into a series of steps, then write code for each step one-at-a-time.

Every lesson will begin with a problem statement. By the end of the lesson, you will solve the problem by learning new programming skills. Let's check out our first problem statement.

# Problem statement

{% include shout.html side="left" emote="💬" markdown="At Onslow College, the year 9 dean would like a program that can automatically generate new students' email addresses based on their first and last name. They will enter a student's full name and the email address will be generated, with a dot between the names and ending in ``@student.onslow.school.nz``." %}

## Step 1: Determine the requirements

First, you need to work out the **requirements** of the program: what does it need to do?

1. Ask the user for the student's first name
2. Ask the user for the student's last name
3. Join the student's names together with a dot
4. Add the ``@student.onslow.school.nz`` portion to the end

## Step 2: Let's write some comments

The first code you will write will be **comments**.

{% include shout.html side="right" emote="💭" markdown="Comments help you to know what Python code you need to write. They are also useful for anybody else who reads your code." %}

To write a comment, start a line with a pound symbol (``#``).

```python
# This is an example of a comment
```

Let's write some comments to describe the requirements of the program. Put two empty lines between each comment where you will write the code.

```python
# Ask the user for the student's first name


# Ask the user for the student's last name


# Join the student's names together with a dot


# Add the ``@student.onslow.school.nz`` portion to the end


```

## Step 3: Write the code!

Underneath each comment, let's write the code to fulfil the requirements.

### variable = value

First, let's learn about **variables**.

{% include shout.html side="right" emote="📦" markdown="A variable is a piece of information, a **value**, that we want to store for safe keeping later on. At some later part in the program, we can re-use that value — as part of an equation, an [expression](/programming/glossary#expression), or to show the user." %}

To create a variable, write the name that you would like to store the value in, an equals sign, and then the value.

For example, if you want to store a student's first name, you could write the following:

```python
first_name = "roimata"
```

{% include shout.html emote="🚨" markdown='**(Please note that because the value is text, it is contained in ``"``quotation marks``"``)**' %}

Variable names must respect the following rules:

- they are all lower case (no capital letters)
- they do not contain spaces; use underscores (``_``) instead
- they are descriptive
- they contain full words, not abbreviations

### Getting user input

Next, let's learn about the ``input()`` function.

A [function](/programming/glossary#function) is a section of code that can be run as many times as you want by [calling](/programming/glossary#call) it. We are going to call the ``input()`` function in order to do something.

{% include shout.html side="right" emote="🙋" markdown="The ``input()`` function allows you to ask a question. The user can then type in a reply to the question. You can then store the user's reply in a variable." %}

For example, to ask the user's first_name, you could write the following:

```python
first_name = input("Please enter your first name: ")
```

### Joining text

Next, let's join some text together.

{% include shout.html side="right" emote="🖇" markdown="You can use the ``+`` symbol between two [string](/programming/glossary#string) [literals](/programming/glossary#literal) (text surrounded by quotation marks) or variables containing a string value to join them together." %}

The joined text can then be stored in a variable, including one that already exists.

```python
first_name = input("Please enter your first name: ")
last_name = input("Please enter your last name: ")
full_name = first_name + "." + last_name
email = full_name + "@student.onslow.school.nz"
```

### Printing text to the screen

Finally, let's learn about the ``print()`` function.

{% include shout.html side="right" emote="🖨️" markdown="The ``print()`` function allows you to show the user a string." %}

For example, to print the user's email, you could write the following:

```python
print("Generated the following email:")
print(email)
```

{% capture right_markdown %}```
Generated the following email:
roimata.davis@student.onslow.school.nz
```{% endcapture %}
{% include half.html markdown="The user will see:" right_markdown=right_markdown %}

You could also join the strings together inside the ``print()`` function call:

```python
print("Generated the following email: " + email)
```

{% capture right_markdown %}```
Generated the following email: roimata.davis@student.onslow.school.nz
```{% endcapture %}
{% include half.html markdown="The user will see:" right_markdown=right_markdown %}

## Step 4: Put it all together

If you have followed this guide, the final code will be:

{% capture markdown %}```python
# Ask the user for the student's first name
first_name = input("Please enter the student's first name: ")

# Ask the user for the student's last name
last_name = input("Please enter the student's last name: ")

# Join the student's names together with a dot
full_name = first_name + "." + last_name

# Add the ``@student.onslow.school.nz`` portion to the end
email = full_name + "@student.onslow.school.nz"
print("Generated the following email:")
print(email)
```{% endcapture %}

{%include half.html markdown=markdown image="img/01-example.png" %}