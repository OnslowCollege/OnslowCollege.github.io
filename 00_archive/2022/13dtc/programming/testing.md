---
title: Testing with Pytest
grand_parent: 13DTC
parent: Complex Programming
nav_order: "cb"
learning_intentions: ["To create automated tests using Pytest"]
success_criteria: ["You have created your own test(s) using Pytest for the sample task"]
---

# Automatic testing

You can use automated tests instead of a testing table to make sure that functions and methods perform the tasks that they are expected to do, handle different inputs, and produce expected outputs.

By using automated tests, you don't need to test out different parts of your code yourself — you can let the development environment handle this for you. This is particularly useful since the program you will produce is quite a bit larger than last year.

This will also encourage your program to be modular: automated tests are best at testing individual functions/methods, which further encourages you to decompose your program. (This will come in handy with Project Management)

# How automatic tests work

The basic principle of automatic testing is to **assert** (to state categorically) that a particular bit of code should do a particular thing, return a particular value, or that another variable should be changed in a particular way.

## Assert functions

For example, you can assert that a function returns a specific value. In this case, a function that doubles a number should, if given the input of ``2, return ``4``.

```python
def double(x: int) -> int:
    return x * 2

def test_double():
    assert double(2) == 4
```

## Assert objects

You can also assert that an object's property accurately reflects the member it protects. For example, the ``Building``'s ``street_name`` property should return the same value as ``_street_name`` (which is determined when the object is created).

```python
@dataclass
class Building:
    _street_name: str

    @property
    def street_name(self) -> str:
        return self._street_name


def test_street_name():
    # You can create variables, variables, etc. in a test
    building = Building(_street_name="Burma Road")
    assert building.street_name == "Burma Road"
```

## Assert exceptions

Finally, you can also assert that a setter raises an exception in cases where something invalid occurred. This is useful to test that your class' setters perform proper validation.

In this example, we test that the street name must contain at least one letter if modified using the setter. If the new string is too short, an ``AttributeError`` is raised, and the test can detect this.

```python
@dataclass
class Building:
    _street_name: str

    @property
    def street_name(self) -> str:
        return self._street_name

    @street_name.setter
    def street_name(self, new_name: str):
        if len(new_name) >= 1:
            self._street_name = new_name
        else:
            raise AttributeError


def test_street_name_setter():
    building = Building(_street_name="Burma Road")
    raised_exception = False

    try:
        # Set the street name to "", which should
        # raise an AttributeError exception
        building.street_name = ""
    except AttributeError:
        # This only runs if the exception was raised
        raised_exception = True

    # Assert the exception was raised, since that's
    # the desired behaviour
    assert raised_exception is True
```

# What makes a good automatic test?

In general, you will want to stick to the same rules you've always known for tests:

- check input for expected values
- check input behaves appropriately on boundary values
- check input handles invalid values

## Expected

```python
# Expected output
def test_one_and_one():
    assert 1 + 1 == 2

# Expected length
def test_potato_length():
    assert len("Potato") == 6

# Expected output
def test_my_function():
    assert my_function(5) == 10

# Expected type
def test_object_member():
    my_object = SomeClass(_age=24)
    assert isinstance(my_object.age, int)
```

## Boundary

For boundary tests, you could make multiple tests:

- one for the boundary value itself
- one for one less than the boundary value
- one for one more than the boundary value

```python
# Boundary
def test_drinking_age_boundary():
    message = can_enter_bar(age=18)
    assert message == "Welcome, come on in"

# One less than the boundary
def test_drinking_age_boundary_lower():
    message = can_enter_bar(age=17)
    assert message == "Sorry, you can't come in"

# One more than boundary
def test_drinking_age_boundary_higher():
    message = can_enter_bar(age=19)
    assert message == "Welcome, come on in"
```

## Invalid

The easiest way to test for invalid data with automated tests is to check for raised exceptions:

```python
# Invalid calculation
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
        
        package/
                student.py
                staff.py

        tests/
                test_student.py  # Tests for module01
                test_staff.py  # Tests for module02
```

4. Import the filename where the code is that you wish to test
5. Create functions whose names start with ``test_``
6. In each of these functions, you will need to ``assert`` something

Ideally, you will be asserting that functions/methods that accept certain arguments (user input) output something. **Avoid testing functions that ask for user input directly**, such as ones that call ``input()``. Instead, ask for user input, then hand that input off to another function, and test the latter function.

# Example tests

This example contains a package called ``mypackage`` with a module called ``validator``. Inside this module is a function called ``validate_number``. This function checks whether or not a string (``string``) contains a valid number that is within a certain range (``min`` to ``max``).

The tests will test the ``validate_number`` to ensure that it works with expected, boundary, and invalid cases.

> **Filename**: 13dtc-assignment/mypackage/validator.py

```python
# Function that handles input
def validate_number(string: str, min: int, max: int) -> bool:
    """Checks that the string is a number and returns True if valid
    and within the range specified by min and max"""
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

> **Filename**: 13dtc-assignment/tests/test_validator.py

```python
from mypackage.validator import validate_number  # The name of the file within the package

# Expected
def test_valid_age():
    """Tests that a reasonable age is considered valid"""
    assert validate_number("14", 12, 18) is True

# Boundary
def test_lower_bound_age():
    """Tests that the youngest age is accepted, but one younger is not"""
    assert module.validate_number("12", 12, 18) is True \
        and validate_number("-11", 12, 18) is False

# Boundary
def test_upper_bound_age():
    """Tests that the oldest age is accepted, but one older is not"""
    assert validate_number("18", 12, 18) is True \
        and validate_number("19", 12, 18) is False

# Invalid
def test_invalid_age():
    """Tests that non-numerical strings are rejected"""
    assert validate_number("banana", 12, 18) is False \
        and validate_number("", 12, 18) is False
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