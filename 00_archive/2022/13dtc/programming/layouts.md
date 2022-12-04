---
title: Layouts
grand_parent: 13DTC
parent: Complex Programming
nav_order: "db"
learning_intentions: ["Learn to lay out widgets on an interface"]
success_criteria: ["You can create a complex layout in your window"]
---

# Laying out widgets

So far, you have created a window with a single widget. In the course, you created a label. If you tried the additional tasks, you will also have created some other widgets.

However, it would be useful to have more than one widget on screen. To achieve this, Qt has the concept of **layout objects**.

## Horizontal layout

Let's start with a basic Qt application template.

```python
from PySide6 import QtWidgets

app = QtWidgets.QApplication()
main_window = QtWidgets.QMainWindow()
main_window.setWindowTitle("Layouts Exercise")
main_window.resize(640, 480)

main_window.show()

app.exec()
```

**Before** the ``main_window.show()`` line, let's add a blank ``QWidget`` as the window's central widget. Because it's blank, we can add other widgets to it — this allows us to have more than one widget.

```python
main_window.setCentralWidget(QtWidgets.QWidget())
```

This creates a new ``QWidget`` object and sets it as the central widget. We can now modify this central widget by referring to the ``main_window`` object's ``centralWidget`` method.

```python
main_window.centralWidget()
```

> By the way, did you notice that Qt doesn't follow PEP-8 conventions? It has camelCase properties and methods instead of snake_case properties. This is because Qt was originally written for C++ and, for the sake of simplicity, Python uses the same method names as C++. Don't worry, you won't get marked down for not using snake_case!

Now, let's add a **layout object** to the central widget. To do this:

1. create a ``QHBoxLayout`` object and store it in a variable
2. set the central widget's layout to our new layout object variable
3. create two ``QLabel`` objects and store them in variables
4. add the two label objects to the layout object

```python
# 1
hbox_layout = QtWidgets.QHBoxLayout()

# 2
main_window.centralWidget().setLayout(hbox_layout)

# 3
left_label = QtWidgets.QLabel("Hello")
right_label = QtWidgets.QLabel("World")

# 4
hbox_layout.addWidget(left_label)
hbox_layout.addWidget(right_label)
```

``QHBoxLayout`` creates a horizontal box layout. This means that any widgets added to it will be added in its own box from left to right. You should see something like this:

![QHBoxLayout](img/layouts_hbox.png)

## Vertical layout

Instead of ``QHBoxLayout`` (horizontal), try using ``QVBoxLayout`` (vertical) to lay out the widgets from top to bottom. In our existing code, changing to a vertical layout will move the "Hello" label to the top of the window and the "World" label to the bottom.

```python
main_window.setCentralWidget(QtWidgets.QWidget())
vbox_layout = QtWidgets.QVBoxLayout()
main_window.centralWidget().setLayout(vbox_layout)

vbox_layout.addWidget(QtWidgets.QLabel("Hello"))
vbox_layout.addWidget(QtWidgets.QLabel("world!"))
```

![QVBoxLayout](img/layouts_vbox.png)

## Embed layouts in layouts

Using layouts grants a certain level of flexibility. If you want to position a widget next to another widget, you can use a horizontal box layout; for stacking widgets one atop the other, vertical box layouts are preferable.

However, you may need to design more complicated layouts. For example, you may wish to display:

1. one widget at the left, such as a side bar
2. a widget to the right of the side bar
3. another widget below widget #2

```
.________.__________.
|        |          |
|        | widget 2 |
| widget |----------|
|   1    | widget 3 |
|________|__________|
```

To do this, you can **embed layouts in other layouts**.

To achieve this particular layout, you would:

1. a horizontal box layout for the central widget
2. add a widget to the horizontal box layout
3. add a blank ``QWidget`` to the horizontal box layout
4. add a vertical box layout to the widget from the previous step
5. Add the top widget to the vertical box layout
6. Add the bottom widget to the vertical box layout

```python
# 1
hbox_layout = QtWidgets.QHBoxLayout()
main_window.centralWidget().setLayout(hbox_layout)

# 2
left_widget = QtWidgets.QLabel("Widget 1")
hbox_layout.addWidget(left_widget)

# 3
right_widget = QtWidgets.QWidget()
hbox_layout.addWidget(right_widget)

# 4
vbox_layout = QtWidgets.QVBoxLayout()
right_widget.setLayout(vbox_layout)

# 5
top_widget = QtWidgets.QLabel("Widget 2")
vbox_layout.addWidget(top_widget)

# 6
bottom_widget = QtWidgets.QLabel("Widget 3")
vbox_layout.addWidget(bottom_widget)
```

![Complex layout](img/layouts_complex.png)

# Task

Try to recreate the following layouts using embedded layout objects.

**Hint**: you should create separate ``QWidget``, ``QHBoxLayout``, and ``QVBoxLayout`` objects stored in their own variables for each side.

For example, the example below might involve variables named:
- ``hbox_layout``
- ``left_widget``
- ``left_vbox_layout``
- ``top_left_label``
- ``bottom_left_label``
- ``right_label``

### First layout

```
.__________.________.
|          |        |
| widget 1 |        |
|----------| widget |
| widget 2 |    3   |
|__________|________|
```

### Second layout

```
.____.____._______.
|    |    |       |
| 1  |  2 |   4   |
|----|----|-------|
|    3    |   5   |
|_________|_______|
```

### Third layout

```
.____.____._______.
|    |    |    5  |
| 1  |  2 |       |
|    |    |-------|
|----|----|    6  |
| 3  |  4 |-------|
|    |    |    7  |
|____|____|_______|
```