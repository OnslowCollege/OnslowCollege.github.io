---
title: Functions that Accept Parameters/Arguments
grand_parent: 12DTC
parent: Advanced Programming
nav_order: "cc"
learning_intentions: ["Specify parameters, the values that functions can accept", "Provide arguments to functions that accept values", "Use the arguments in your function code"]
success_criteria: ["You have defined paramaters, including their types", "You have called a function with arguments", "You have created a function that accepts parameters **and** returns a function"]
---

# Parameters and Arguments

When you write functions and procedures, you can specify that they should accept one or more values. These values are called **parameters**. You specify the parameter names and types in the brackets after the function name.

When you call a function that accepts parameters, you will pass in **arguments**. These are the actual values.

For example, this function accepts a person's name (a string) in order to return a nickname:

```python
def create_nickname(name: str) -> str:
    """
    Returns a string containing a nickname.

    If the name ends in vowels, remove the vowels so that
    the name can end in -ums (i.e. {Name} -> {Nam}ums).

    However, if removing the vowels causes the name to be
    empty, returning {Name} Mc{Name}ington instead.

    name (str): the name to change to a nickname
    """
    FINAL_VOWELS = ["a", "e", "i", "o", "u", "y"]
    nick = name

    # Remove final vowels. Stop when a consonant is found.
    while nick[-1] in FINAL_VOWELS:
        nick = nick[0:-1] # Slice all but the last letter.

    if len(nick) > 0:
        return nick + "ums"
    else:
        return name + " Mc" + name + "ington"

print(create_nickname("Minogue"))
print(create_nickname("O'Leary"))
print(create_nickname("Iaia"))
```

| Parameter | Type | Argument
| :-- | :-- | :-- |
| name | str (string) | ``"Minogue"`` |
| | | ``"O'Leary"`` |
| | | ``"Maaka"`` |

This should result in the following output:

```
Minogums
O'Learums
Iaia McIaiaington
```

# Multiple parameters

Functions can accept multiple parameters. To do this, separate the parameters with a comma and a space. For example:

```python
def multiply(lhs: int, rhs: int) -> int:
    """
    Multiplies the left-hand side by the right-hand side.
    
    lhs (int): the left-hand side
    rhs (int): the right-hand side
    """
    return lhs * rhs

print(multiply(7, 8))
```

| Parameter | Type | Argument
| :-- | :-- | :-- |
| lhs | int | ``7`` |
| rhs | int | ``8`` |

This should result in the following output:

```
56
```

## Parameters with default values

You can specify that a parameter has a default value. This means that if you don't call the function with that value specified, one will be provided automatically.

To provide a default value, put an equals sign ``=`` after the parameter's type, then provide the value.

For example, this function can multiply by 2 if the user does not specify a ``rhs`` argument:

```python
def multiply(lhs: int, rhs: int = 2) -> int:
    """
    Multiplies the left-hand side by the right-hand side.

    lhs (int): the left-hand side
    rhs (int): the right-hand side (default: 2)
    """
    return lhs * rhs

print(multiply(256)) # Notice: only one argument supplied
```

| Parameter | Type | Argument
| :-- | :-- | :-- |
| lhs | int | ``256`` |
| rhs | int | none specified |

This should result in the following output:

```
512
```

As you can see, even though the call to ``multiply()`` only provided the left-hand side argument, the function could use the default value of ``2`` and still correctly work.

## Default value placement

Parameters with default values must come at the **end** of the parameter list. In the above example, ``rhs`` was the last parameter and thus came at the end of the list.

You can have multiple parameters with default values, but they must come at the end.

For example, the following function plots the points of a rectangle — by default, the top-left-most point starts at the coordinates (0, 0). However, this function is **not** valid.

```python
def draw_shape(top_x: int = 0, top_y: int = 0, bottom_x: int, bottom_y: int):
    pass
```

The default values must be specified at the end, so ``top_x`` and ``top_y`` become the last parameters in the brackets:

```python
def draw_shape(bottom_x: int, bottom_y: int, top_x: int = 0, top_y: int = 0):
    pass
```

# Calling the function with parameter names

When you call the function, you can specify the names of the parameters. If you do this, you can also specify the arguments in any order — they will match up with the name.

To specify the names, prefix each argument with the name of the parameter and an equals sign ``=``.

**Note**: do not put a space around the equals sign. This goes against PEP-8.

This can often help make the purpose clearer, especially when calling functions that may take a lot of parameters.

For example:

```python
# Unclear what each argument means, especially since the top-left
# coordinate is specified *last*
draw_shape(200, 400, 0, 0)

# Much clearer, in a more logical order
draw_shape(top_x=0, top_y=0, bottom_x=200, bottom_y=400)
```

{% include task.html task_code="J-Fj0Wmm" %}