---
title: Packages and Modules
grand_parent: 13DTC
parent: Complex Programming
nav_order: "ca"
learning_intentions: ["Split your single-file projects into multiple files", "Import your code from one file into another", "Use packages and modules to separate classes, functions, etc."]
success_criteria: ["Moved code across multiple files", "Created your own package and modules"]
---

# Organising your code into packages and modules

As your projects start to grow in complexity, having all your code in a single file becomes untenable. You spend all your time jumping back and forth in longer and longer files, especially with object-oriented code.

Currently, your file organisation looks like this:

```
13dtc-assignment/
        task.py       # Contains ALL your code
        task_test.py
```

At a basic level, you can split your code into several files. For example, you could have file per class. You can further organise your files into a **package**; each file is then considered to be a **module**.

This allows us to also separate the code that uses your classes into its own file, such as ``task.py``.

```
13dtc-assignment/
        task.py       # Uses code from virtualpet
        task_test.py  # Tests

        virtualpet/   # virtualpet package (folder)
            pet.py    # pet module, containing Pet class
            cake.py   # cake module, containing Cake class
```

# Import your package's code in other files

When you move your code into separate files, you need to **import** your classes/functions/constants from the file where they are contained.

Remember:

- the **package** is the **folder**
- the **module** is the **filename** (minus ``.py``)
## Import a module

```python
from package import module

object = module.Class()
```

## Import a class

```python
from package.module import Class

object = Class()
```

## Import a function (not in a class)

```python
from package.module import my_function

my_function()
```

{% include task.html task_code="rgbMf-Nf" %}