---
title: Assessment opportunity ONE
grand_parent: 13DTC
parent: Complex Programming
nav_order: "za"
---

# Assessment task

| Standard | Name | Level | Int/Ext | Credits |
| :-- | :-- | :-: | :-: | :-: |
| [AS91906](https://www.nzqa.govt.nz/nqfdocs/ncea-resource/achievements/2019/as91906.pdf) | Use complex programming techniques to develop a computer program | 3 | Internal | 6 |

# Explanation from the standard

| Achievement | Achievement with Merit | Achievement with Excellence |
| :-- | :-: | --: |
| Use complex programming techniques to develop a computer program | Use complex programming techniques to develop an informed computer program | Use complex programming techniques to develop a refined computer program |

# Task

In these years impacted by COVID-19, it is important for students to be able to manage their time. Though an assortment of tools exist, such as calendars and reminders apps, it would be ideal to have a tool suited to the needs of Onslow College's year 13 cohort.

You must create a graphical program to help students keep track of what classes they have during this pandemic year.

You program will let you:

1. select a day of the week (Monday-Friday), and it will list your classes.
    - **clarification**: use your own timetable. It does not need to be editable by the user.
        - however, for Excellence, your design should still be flexible enough to accommodate changes to the timetable without requiring significant changes to the code
    - this includes Ako classes and study spells
    - study spells still require attendance to be filled out
    - you do not need to include interval and lunch time
2. select a class, and it will list:
    - the full name of the course
    - the teacher's code
    - the teacher's full name (i.e. Miss Voropaeva/Whaea Tina)
    - the times the class starts and ends
3. mark if spell 5 has been cancelled for the week
    - if so, remove spell 5 from the GUI **OR** change it to say "cancelled", etc.
    - you should be able to undo this in case you made a mistake (that is, all the spell 5 classes will show again as normal)
4. mark your own attendance by entering an attendance code for each class
    - how the user enters the code is up to you
    - codes are:
        - P for present
        - L for late
        - ? for absent
        - M for medical
        - F for cancelled classes

# Assessment Requirements

## Achieved

For Achieved, you must:

- store data in at least **two** (2) types of data (text, number, boolean, class, etc.)
- uses conditional statements and/or loops
- get input from the user
- set out code clearly and document the code with comments
- test your program, in an organised way, to ensure the program works with expected cases ([view sample testing table](sample_testing.docx))

You must also use at least **two** (2) of the following complex techniques:

- programming or writing code for a graphical user interface (GUI)
- reading from, or writing to, files or other persistent storage
- object-oriented programming using class(es) and objects defined by the student
- using types defined by the student **(note: in Python, this implies the use of object-oriented programming)**
- using third party or non-core API, library or framework
- using complex data structures (e.g. stacks, queues, trees)

## Achieved with Merit

For Achieved with Merit, you must:

- follow conventions from the programming language (e.g. PEP-8)
- document the code's function and behaviour in an organised way
    - this includes docstrings for classes, functions, and methods
- use appropriate and meaningful variable, constant, class, function, and method names
- test your program, in an organised way, to ensure the program works with both expected cases and relevant boundary cases ([view sample testing table](sample_testing.docx))

## Achieved with Excellence

For Achieved with Excellence, you must:

- ensure that your program is flexible and robust
  - it should reduce repeated code througout your program
      - move repeated code into functions, methods, or properties
  - it must behave in an expected manner
  - it must not crash
- test your program, in an organised way, to ensure the program works with expected and boundary cases, and correctly handles invalid cases ([view sample testing table](sample_testing.docx))

# Restrictions

You must:
- use a suitable, text-based programming language
  - You will be expected to use Python unless you have consulted with your teacher
  - the program must be **graphical**
      - if you use Python, you are recommended but not limited to using PySide6

You may:
- consult this website's notes
- consult your previous work
- consult with other students for advice and ideas

However, you may **not**:
- copy other students' work, even with modifications
- copy code online without proper attribution
- ask other students to fix errors for you
- present any content you did not create as your own work

To properly attribute code, add a comment explaining where the code comes from. For example:

```python
# Code to format as price from https://some.website.com/
price_string = f"${price:.2f}"
```

```python
def format_price_as_string(price: float) -> str:
    """
    Formats the price using a dollar sign and two decimal points.
    Code from https://some.website.com/
    """
    return f"${price:.2f}"
```

# Time allowance

You will have until the end of Term 2 Week 10 to complete this task.

You **may** work on this task in your own time.

# Submission

- You should continually commit and push your code to GitHub
- The work to be marked will be either:
    - the final commit to your GitHub repository before the due date
    - code submitted to Microsoft Teams before the due date

If you choose to perform testing using the supplied testing table, be sure to stage the testing document as part of each commit. **You should be testing as you go, not just at the end!**

If you have problems committing and pushing before the due date, zip your folder and submit it to Teams.

{% include task.html task_code="4qUZKYF1" %}