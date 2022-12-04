---
title: Lists Task
grand_parent: 12DTC
parent: Advanced Programming
nav_order: "bg"
---

# Task

## Scenario

You're starting university a whole two years early! You've said goodbye to mum and dad, packed your things, and shifted into a new flat. Life is good.

However, a few months in, you can't help but notice that your flatmates are a little less than forthcoming about helping with the chores. Your flat goes from your first taste of paradise to a pig sty before your very eyes.

You've had enough. It's time to create…

…a chores roster!

## Requirements

Create a program that randomly assigns chores to your flatmates to create a chore roster for the week.

### Flatmates

1. **You** (use your own name)
2. Henare
3. Banjeet
4. Tomoko
5. Loimata

### Chores

1. vacuuming the lounge
2. vacuuming the hallways
3. sweeping the porch
4. sorting the recycling from rubbish
5. putting out the bins
6. cleaning the kitchen
7. scrubbing the shower
8. mowing the lawn
9. watering the vegetable garden
10. shared grocery shopping
11. cooking shared dinner on Sunday night
12. taking Rover for a walk

### To complete a roster

1. We need to make sure it gets assigned to one of your flatmates
2. Not all of the flatmates are as available as each other
    - Henare works nights and can't commit to as many chores as everybody else
    - Banjeet has the most spare time and is happy to take the most chores
    - Loimata can take more chores than Henare but fewer than Banjeet
    - You and Tomoko will share the rest, but it must be fewer than Loimata
3. If not all of the chores are allocated for a given week's roster, you must remake the roster

### How to generate the roster

You need to generate a roster for the next 6 months, so 26 weeks.

For each week:

1. Generate a list of numbers — 1 to 12 — to represent the chores
2. Distribute the random numbers to the flatmates based on how busy they are
3. Print out the chores in the following format

```
WEEK 1 - BY FLATMATE
You: vacuuming the lounge, vacuuming the hallways
Henare: sweeping the porch
Banjeet: sorting the recycling from rubbish, putting out the bins, cleaning the kitchen, scrubbing the shower
Tomoko: mowing the lawn, watering the vegetable garden
Loimata: shared grocery shopping, cooking shared dinner on Sunday night, taking Rover for a walk

WEEK 1 - BY CHORE
Vacuuming the lounge: You
Vacuuming the hallways: You
Sweeping the porch: Henare
Sorting the recycling from rubbish: Banjeet
Putting out the bins: Banjeet
Cleaning the kitchen: Banjeet
Scrubbing the shower: Banjeet
Mowing the lawn: Tomoko
Watering the vegetable garden: Tomoko
Shared grocery shopping: Loimata
Cooking shared dinner on Sunday night: Loimata
Taking Rover for a walk: Loimata
```

## Extension

Make it so that a flatmate never has to repeat the same chore as they did last week.

{% include task.html task_code="y1qhFMEn" %}