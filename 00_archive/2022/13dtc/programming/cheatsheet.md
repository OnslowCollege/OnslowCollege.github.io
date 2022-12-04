---
title: Cheat Sheet
grand_parent: 13DTC
parent: Complex Programming
---

# Object Oriented Programming

## Dataclass

```python
from dataclasses import dataclass

@dataclass
class MyDataclass:
    """
    Docstring that explains what MyClass is about.
    """

    # Members
    _my_protected_string: str
    _my_protected_number: int
    _my_protected_bool: bool
```

## Properties

### Getter for a member

```python
@property
def my_string(self) -> str:
    return self._my_protected_string
```

See also [Accessing object data](#accessing-object-data)

### Getter that does not represent a member

```python
@property
def half_price(self) -> float:
    return self._my_protected_number / 2
```

See also [Accessing object data](#accessing-object-data)

### Setter (no validation)

```python
@my_string.setter
def my_string(self, new_string: str):
    self._my_protected_string = new_string
```

See also [Updating object data](#updating-object-data)

### Setter (with validation)

```python
@my_string.setter
def my_string(self, new_string: str):
    """
    Docstring that explains the validation.
    i.e. Sets the string if it has at least 1 character.
    """

    # Checks that new_string has at least 1 character.
    # Otherwise, raises a ValueError
    if len(new_string) > 0:
        self._my_protected_string = new_string
    else:
        raise ValueError("String must contain at least 1 character")
```

See also [Updating object data](#updating-object-data)

## Methods

### Instance method

```python
@dataclass
class MyClass:
    _my_protected_string: str

    def my_method(self, arg1: int, arg2: SomeClass) -> bool:
        """
        Docstring that explains what the function does, what each argument
        is for, and what the returned value represents.

        Arguments:
        - arg1 (int): a very fancy number
        - arg2 (SomeClass): an object of SomeClass

        Returns:
        - True if arg1 is above 0 or some_property is present in arg2
        - Otherwise, False
        """
        if arg1 > 0:
            return True
        elif arg2.some_property:
            return True
        else:
            return False
```

See also [calling an instance method](#calling-an-instance-method)

## Creating an object

### Storing one object in a variable

```python
my_object = MyClass("Hello", 23, False)
```

### Storing multiple objects in a list

```python
my_objects = [
    MyClass("Hello", 23, False),
    MyClass("Goodbye", 27, True),
    MyClass("42", 42, True)
]
```

### Generating multiple objects using a loop

```python
my_objects = []
for i in range(0, 10):
    my_objects.append(MyClass("Hello", i, False))
```

### Generating multiple objects using a list comprehension

```python
my_objects = [MyClass("Hello", i, False) for i in range(0, 10)]
```

## Working with object data

### Accessing data from a single object

```python
print(my_object.string)
```

### Accessing data from multiple objects using a loop

```python
strings = []
for each_object in my_objects:
    strings.append(each_object.string)
print(strings)
```

### Accessing data from multiple objects using a list

```python
strings = [each_object.string for each_object in my_objects]
print(strings)
```

# Graphical User Interfaces

## Basic template

```python
from PySide6.QtWidgets import *

app = QApplication()
main_window = QMainWindow()
main_window.setWindowTitle("Title Goes Here")
main_window.resize(1280, 720)

# Set up main window's widget
main_widget = QWidget()
main_vbox = QHBoxLayout()
main_widget.setLayout(main_vbox)

# Set up widgets
label = QLabel("Label text")
text_field = QLineEdit("Default text")
button = QPushButton("Button Text")

# Add widgets to main layout
main_vbox.addWidget(label)
main_vbox.addWidget(text_field)
main_vbox.addWidget(button)

# Run the program
main_window.show()
# main_window.showFullScreen()
app.exec()
```

## Embedded layouts

```python
# Main layout — left to right
outer_hbox = QHBoxLayout()

# Left side
left_widget = QWidget()
left_vbox = QVBoxLayout()

# Left widgets
left_label_01 = QLabel("01")
left_label_02 = QLabel("02")
left_label_03 = QLabel("03")

# Left layout
left_vbox.addWidget(left_label_01)
left_vbox.addWidget(left_label_02)
left_vbox.addWidget(left_label_03)

# Centre
centre_widget = QWidget()
centre_vbox = QVBoxLayout()

# Centre widgets
centre_label_01 = QLabel("01")
centre_label_02 = QLabel("02")
centre_label_03 = QLabel("03")

# Centre layout
centre_vbox.addWidget(centre_label_01)
centre_vbox.addWidget(centre_label_02)
centre_vbox.addWidget(centre_label_03)

# Right side
right_widget = QWidget()
right_vbox = QVBoxLayout()

# Right widgets
right_label_01 = QLabel("01")
right_label_02 = QLabel("02")
right_label_03 = QLabel("03")

# Right layout
right_vbox.addWidget(right_label_01)
right_vbox.addWidget(right_label_02)
right_vbox.addWidget(right_label_03)

# Add the three columns to the main layout
outer_hbox.addWidget(left_widget)
outer_hbox.addWidget(centre_widget)
outer_hbox.addWidget(right_widget)
```

## QComboBox

### Signals

| Event | Signal |
| :-- | :-- |
| User clicks a different menu item | ``currentIndexChanged(index: int)`` |
| User clicks a different menu item (returns item text) | ``currentTextChanged(text: str)`` |
| User clicks a menu item, including the one already selected | ``activated(index: int)`` |
| User clicks a menu item, including the one already selected (returns item text) | ``textActivated(text: str)`` |
| User highlights a menu item | ``highlighted(index: int)`` |
| User highlights a menu item (returns item text) | ``textHighlighted(text: str)`` |
| User edits text (requires user to set ``setEditable`` to ``True``) | ``editTextChanged(text: str)`` |

### Instantiation

```python
my_combo_box = QComboBox()
```

### Add items to the menu

```python
# Single item
my_combo_box.addItem("A string")

# Multiple items
my_combo_box.addItems(["Item 1", "Item 2", "Item 3"])
```

### Make combo box editable

This makes the ``QComboBox`` behave like [``QLineEdit``](#qlineedit), but the menu can still appear by clicking the arrow.

```python
my_combo_box.setEditable(True)
```

## QLabel

### Instantiation

```python
my_label = QLabel("Label text")
```

### Change the label text

```python
my_label.setText("New label text")
```

## QLineEdit

### Signals

| Event | Signal |
| :-- | :-- |
| Text is edited by the user | ``textEdited(text: str)`` |
| Text is changed, including by program code | ``textChanged(text: str)`` |
| User moves the text insertion cursor | ``cursorPositionChanged(old_position: int, new_position: int)`` |
| User presses Enter/Return | ``returnPressed()`` |
| Line edit loses focus **and** the text changed since the line edit took focus | ``editingFinished()`` |

### Instantiation

```python
my_line_edit = QLineEdit()
# my_line_edit = QLineEdit("Default text")
```

### Get the user's text

```python
text = my_line_edit.text()
```

### Change the text

```python
old_text = my_line_edit.text()
my_line_edit.setText("New text")
```

## QListWidget

### Signals

| Event | Signal |
| :-- | :-- |
| User clicks a different row | ``currentRowChanged(row: int)`` |
| User clicks a different row | ``currentItemChanged(current: QListWidgetItem, previous: QListWidgetItem)`` |
| Row item is clicked once | ``itemClicked(item: QListWidgetItem)`` |
| Row item is double-clicked | ``itemDoubleClicked(item: QListWidgetItem)`` |
| Row item is interacted with using *any* mouse button | ``itemPressed(QListWidgetItem)`` |
| Row item is activated (clicked, user pressed Enter/Return, or macOS user pressed Cmd-O) | ``itemActivated(item: QListWidgetItem)`` |

### Instantiation

```python
my_list_widget = QListWidget()
```

### Adding items to the list

```python
# Single item
my_list_widget.addItem("A string")

# Multiple items
my_list_widget.addItem(["String 1", "String 2", "String 3"])
```

### Clearing the list

```python
my_list_widget.clear()
```

## QPushbutton

### Signals

| Event | Signal |
| :-- | :-- |
| When the button is clicked | ``clicked(bool)`` |

### Instantiation

```python
my_button = QPushButton("Button text")
```

### Change the text

```python
old_text = my_button.text()
my_button.setText("New text")
```