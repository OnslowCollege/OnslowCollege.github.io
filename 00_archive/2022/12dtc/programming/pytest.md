---
title: Testing with Pytest
grand_parent: 12DTC
parent: Advanced Programming
learning_intentions: ["To create automated tests using Pytest"]
success_criteria: ["You have created your own test(s) using Pytest for the sample task"]
---

# Automatic testing

You can use automated tests instead of a testing table to make sure that functions and methods perform the tasks that they are expected to do, handle different inputs, and produce expected outputs.

By using automated tests, you don't need to test out different parts of your code yourself — you can let the development environment handle this for you. This is particularly useful since the program you will produce is quite a bit larger than last year.

This will also encourage your program to be modular: automated tests are best at testing individual functions/methods, which further encourages you to decompose your program. (This will come in handy with Project Management)

## How automatic tests work

The basic principle of automatic testing is to **assert** (to state categorically) that a particular bit of code should do a particular thing, return a particular value, or that another variable should be changed in a particular way.

## What makes a good automatic test?

In general, you will want to stick to the same rules you've always known for tests:

- check input for expected values
- check input behaves appropriately on boundary values
- check input handles invalid values

For example:

```python
# Asserts that one and one make two
def test_one_and_one():
    assert 1 + 1 == 2

# Asserts that "Potato" is 6 characters long
def test_potato_length():
    assert len("Potato") == 6

# Asserts that a function, given the arg of 5, returns 10
def test_my_function():
    assert my_function(5) == 10

# Asserts that an object's member is of a certain type
def test_object_member():
    my_object = SomeClass(_age=24)
    assert isinstance(my_object.age, int)

# Asserts that certain code will raise an Exception
def test_raises_exception():
    raised_exception = False
    try:
        print(25 / 0)
    except:
        raised_exception = True
    assert raised_exception is True
```

# How to write a Pytest

1. In the root directory (top-level folder) of your project, add an empty file named ``conftest.py``
2. Create a folder in your project called ``tests``
3. In the ``tests`` folder, add files for different tests. For example: ``test_student.py``

```
13dtc-assignment/
        conftest.py  # Empty file needed for tests to be found
        
        student.py
        staff.py

        tests/
                test_student.py
                test_staff.py
```

4. Import the filename where the code is that you wish to test
5. Create functions whose names start with ``test_``
6. In each of these functions, you will need to ``assert`` something

Ideally, you will be asserting that functions/methods that accept certain arguments (user input) output something. **Avoid testing functions that ask for user input directly**, such as ones that call ``input()``. Instead, ask for user input, then hand that input off to another function, and test the latter function.

# Example tests

> **Filename**: 12dtc-assignment/validator.py

```python
# Function that handles input
def validate_number(string, min, max) -> bool:
    """Checks that the string is a number, and returns True if valid"""
    try:
        number = int(string)
        if number >= min and number <= max:
            return True
        else:
            return False
    except ValueError:
        return False

# Get user input, then call the function
age = input("Type your age in years: ")
age_is_valid = validate_number(age, 12, 18)
```

> **Filename**: 12dtc-assignment/tests/test_validator.py

```python
import validator

def test_valid_age():
    """Tests that a reasonable age is considered valid"""
    assert validator.validate_number("14", 12, 18) is True


def test_lower_bound_age():
    """Tests that the youngest age is accepted, but one younger is not"""
    assert validator.validate_number("12", 12, 18) is True \
        and validator.validate_number("-11", 12, 18) is False


def test_upper_bound_age():
    """Tests that the oldest age is accepted, but one older is not"""
    assert validator.validate_number("18", 12, 18) is True \
        and validator.validate_number("19", 12, 18) is False


def test_invalid_age():
    """Tests that non-numerical strings are rejected"""
    assert validator.validate_number("banana", 12, 18) is False \
        and validator.validate_number("", 12, 18) is False
```

# How to run **your** Pytests

The procedure for running your own Pytests is very like running the ones defined in the assignments. In Visual Studio Code, you can use the ![Testing](../../img/beaker.svg) Testing tab to run your tests.

However, since your test files should be located in a folder called ``tests``, make sure to select that folder (instead of root directory) when asked where to locate the tests.

## If you chose the wrong folder

If you choose the wrong folder, you can delete the following files/folders within your project to start from scratch:

- ``__pycache__``
- ``.pytest_cache``
- ``.vscode/settings.json``

You can delete these in Visual Studio Code using the ![Explorer](../../img/files.svg) Explorer tab.

{% include task.html task_code="RmSS0yii" %}