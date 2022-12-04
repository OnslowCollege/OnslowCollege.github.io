---
title: Functions
nav_exclude: true
learning_intentions: ["Reduce repeated code with functions", "Define a function", "Make the function return a value"]
success_criteria: ["You have defined a function", "You have made the function return a value"]
---

# Functions

There are times when your code becomes repetitive. For example, if you ask the user multiple times throughout the program for text, you will find yourself:

1. checking that the user has typed in something
2. checking that what the user entered is valid
3. doing some calculations or running some logic based on what the user entered
4. doing it all over again later in the program!

## How to write a function

```python
def function_no_args():
    # Code goes here
```

1. Start the line with ``def``. This means function **def**inition
2. Give the function a name. Make it descriptive, all lowercase, and in ``snake_case`` (underscores, no spaces)
3. Add a left parenthesis, right parenthesis, and a colon ``():``
4. Indented to the right, you can write as much code as you want

## Using variables from outside the function

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
    global choice
    print("Choose an option:")
    print("(1): Add an item")
    print("(2): Delete an item")
    print("(3): List all items")
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

# Task 1: First function

> **Filename**: function1.py

## 1.1 Requirements

Define a function that prints out the text ``"Hello, world!"``, and then call it.

## 1.2 Example output

```
Hello, world!
```

# Task 2: x-ponential growth

> **Filename**: functions2.py

## 2.1 Requirements

1. Create a variable called ``x`` with a value of ``2``
2. Define a function called ``exponentialise``
3. In the first line of the function, add the following line:
   ```python
   global x
   ```
4. Starting from the next line, add code in the function that will modify the value of ``x`` by multiplying ``x`` by itself
5. Write code in the function to print the value of ``x``
6. Call the function five times

## 2.2 Example output

```
4
16
256
65536
4294967296
```

# Task 3 Function that returns a value

> **Filename**: functions3.py

## 3.1 Requirements

1. Define a function called ``non_empty_input``
2. Write code in the function to ask the user for their name
3. If the user provided an empty string, ask again
4. Otherwise, return the value
5. Call the ``non_empty_input`` function and store the returned value in a variable called ``name``
6. Greet the user by their name

## 3.2 Example output

```
Please enter your name:
Please enter your name: Bob
Hello, Bob
```

## 3.3 How to return values in function

Instead of making all the variables you want to modify into globals, it's sometimes more useful to return a value instead. This means that the value that is returned can be stored in a variable.

To return a value, add ``return`` to 


For example, we can change the ``get_user_menu_choice()`` function to return the value rather than modify the ``choice`` variable.

```python
def get_user_menu_choice():
    print("Choose an option:")
    print("(1): Add an item")
    print("(2): Delete an item")
    print("(3): List all items")
    new_choice = input("Type a number: ")
    return new_choice

choice = get_user_menu_choice()
```

# Task 3 Extension

> **Filename**: functions4.py

## 3.1 Requirements

Copy the code from ``functions2.py`` into ``functions4.py``, then add the following features:

1. Instead of using a ``global`` variable, return the new value
2. Delete the ``print()`` statement inside the function
3. When you call the ``exponentialise`` function, store the returned value in the ``x`` variable
4. After each call, print ``x``