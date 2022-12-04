---
title: Functions
grand_parent: 12DTC
parent: Advanced Programming
nav_order: "ca"
learning_intentions: ["Reduce repeated code with functions", "Define a function", "Call a function", "Modify a global value"]
success_criteria: ["You have defined a function", "You have called the function", "Calling the function has modified a global value"]
---

# Functions

There are times when your code becomes repetitive. For example, if you ask the user multiple times throughout the program for text, you will find yourself:

1. checking that the user has typed in something
2. checking that what the user entered is valid
3. doing some calculations or running some logic based on what the user entered
4. doing it all over again later in the program!

# How to declare a function

```python
def my_wonderful_function():
    # Code goes here
```

1. Start the line with ``def``. This means function **def**inition
2. Give the function a name. Make it descriptive, all lowercase, and in ``snake_case`` (underscores, no spaces)
3. Add a left parenthesis, right parenthesis, and a colon ``():``
4. Indented to the right, you can write as much code as you want

## Modifying variables declared outside the function

To be able to change variables that are defined outside the function, you need to declare the variable as **global** so that the function is able to access and modify it.

To do that, add the following line to your function's code:

```python
global variable_name
```

You **DON'T** need to declare variables as global if:
- they are declared outside the function **but** you don't modify them
- they are declared inside the function

For example, a function that prints a menu and asks the user to choose an item:

```python
# Defined outside the function
choice = ""

def get_user_menu_choice():
    # Make choice global
    global choice
    print("Choose an option:")
    print("(1): Add an item")
    print("(2): Delete an item")
    print("(3): List all items")

    # Update choice
    while choice == "":
        choice = input("Type a number: ")
```

## Calling a function

You can **call** a function that you have defined in your code at any time. To do this, you specify the name of the function including the parentheses.

For example, to call the function defined above:

```python
choice = ""

# Call the function
get_user_menu_choice()

if choice == "1":
    # do this
elif choice == "2":
    # do that
else:
    # do the other
```

# Documenting the function

Documenting functions is the same as any other Python code in that it requires using comments. Unlike other comments, function make use of a specific type of comment: **docstrings**.

To write a docstring, create a multi-line string (starting and ending with three quotation marks) directly under the function signature:

```python
def my_wonderful_function():
    """
    This is my wonderful docstring
    """
```

Your docstrings should briefly explain what the function does. You do not need to explain *how* it does it; for this, you can continue to use normal comments inside the function.

```python
def get_user_menu_choice():
    """
    Gets the user's menu choice
    """

    # Make choice global
    global choice
    print("Choose an option:")
    print("(1): Add an item")
    print("(2): Delete an item")
    print("(3): List all items")

    # Update choice
    while choice == "":
        choice = input("Type a number: ")
```

Any place where you call one of your functions, hover your mouse cursor over the function name. The docstring will appear as a tool tip.

![Function's documentation](img/function-tool-tip.png)

{% include task.html task_code="a34KgLdS" %}