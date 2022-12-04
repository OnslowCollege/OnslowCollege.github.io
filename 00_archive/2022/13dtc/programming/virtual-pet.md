---
title: OOP Task — Virtual Pet
grand_parent: 13DTC
parent: Complex Programming
nav_order: "fb"
---

# Task

## Scenario

It's time to put your knowledge of object-oriented programming to the test — we are going to bring a virtual pet **TO LIFE!** ⚡️⚡️⚡️

How long can you keep your creations **alive**!? Muahaha!

<iframe width="720" height="405" src="https://www.youtube.com/embed/0VkrUG3OrPc?start=2" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Pet requirements

### Members and properties

**READ ALL THE REQUIREMENTS BEFORE YOU START**

1. Create a class called ``Pet`` with the following members/properties:
   
    | Name | Type | Description | Has property | Has setter |
    | :-- | :-- | :-- | :-: | :-: |
    | ``boredom`` | int | The pet's boredom level. When it gets too high, the pet gets bored, it also gets hungry faster | ✅ | ✅ |
    | ``hunger`` | int | The pet's level of hunger. When it gets too high, the pet's health starts to go down | ✅ | ✅ |
    | ``sounds`` | list | The list of sounds the pet knows | ✅ | |
    | ``health`` | int | The pet's health, from 0 to 100 | ✅ | ✅ |
    | ``boredom_limit`` | int | The threshold for the pet's boredom; beyond this point, they start to get hungrier | ✅ | |
    | ``hunger_limit`` | int | The threshold for the pet's hunger; beyond this point, the pet starts to lose health from starvation | ✅ | |

2. Add default values to the following members:

    | Name | Value |
    | :-- | :-- |
    | ``health`` | 100 |
    | ``boredom_limit`` | a random number between 50 and 90 (inclusive) |
    | ``hunger_limit`` | 80 |

    To do this, write the default values after the member names and an equals sign:

    ```python
    @dataclass
    class Pet:
      # Other members ...
      health: int = 100
    ```

3. Protect the members and make sure the properties and setters work

### Methods

**READ ALL THE REQUIREMENTS BEFORE YOU START**

1. Add an instance method called ``tick`` which takes no arguments (still requires ``self``)
    - The method increases the pet's boredom by its boredom rate (see point 4), and its hunger by its hunger rate (see point 5)
      - The boredom and hunger levels should never exceed the maximum (for ``Pet``, 100)
    - When hunger exceeds the hunger limit, the method also decreases the pet's health by half of the hunger rate
      - Health never drops below 0
2. Add an method called ``feed`` that accepts a ``Cake`` (or any ``Cake`` subclass; see below) and replenishes hunger or health (see the Cake requirements section below)
3. Add a method called ``train`` that accepts a string
    - This will add the specified string to the pet's repertoire of ``sound``s and reduce their boredom by 50 (boredom never drops below 0)
    - However, the effort of training makes the pet's hunger go up by 25
    - A pet can only know 5 sounds at a time
4. Add a property method called ``boredom_rate``
    - Normally, the boredom rate is 4
    - The boredom rate is doubled to 8 if the pet's boredom level excees the boredom limit
5. Add a property method called ``hunger_rate``
    - Normally, the hunger rate is 4
    - When the pet's health drops to 25 or below, the hunger rate drops to 2
    - The hunger rate is doubled if the pet is bored (beyond the boredom limit)
      - Therefore, 8 if the pet's health is above 25
      - 4 if the pet's health is at or below 25
    - The hunger rate is quadrupled if the pet is angry (at or over 90 boredom)
      - Therefore, 16 if the pet's health is above 25
      - 8 if the pet's health is at or below 25
6.  Add a property method called ``mood`` which returns a list of strings
    - Health
      - If the pet's health is between 80 and 100, return "fighting fit"
      - If the pet's health is between 1 and 20, return "sick"
      - if the pet's health is at 0, return "dead",
      - Otherwise, return "ok"
    - Hunger
      - If the pet's hunger is between 50 and the hunger limit, return "hungry"
      - If the pet's hunger is at or exceeds the hunger limit, return "starving"
      - If the pet's hunger is below 50, return "full"
    - Boredom
      - If the pet's boredom is between 0 and the boredom limit, return "happy"
      - If the pet's boredom is at or exceeds the boredom limit, return "bored"
      - If the pet's boredom is at or over 90, return "angry"
    - Example: ``["ok", "full", "happy"]``

## Cake requirements

**READ ALL THE REQUIREMENTS BEFORE YOU START**

1. Create a base class called ``Cake`` with the following **properties**:
   
    | Name | Type | Description | Has property | Has setter |
    | :-- | :-- | :-- | :-: | :-: |
    | ``hunger`` | int | How much hunger the cake replenishes | ✅ | |
    | ``health`` | int | How much health the cake replenishes | ✅ | |
    | ``cost`` | int | How much the cake costs | ✅ | |

2. Create instances of ``Cake`` with the following details:

    | Cake | Hunger replenishment | Health replenishment | Cost |
    | :-- | :-: | :-: | :-: |
    | cake | 2 | 0 | 0 |
    | berry | 10 | 5 | 5 |
    | banana | 15 | 2 | 10 |
    | peach | 20 | 0 | 20 |
    | pea | 5 | 10 | 10 |
    | bean | 2 | 15 | 25 |
    | pod | 0 | 20 | 40 |

## Program requirements

**READ ALL THE REQUIREMENTS BEFORE YOU START**

### Set up

1. Create a variable called ``tick_count`` with a value of 0
2. Create a variable called ``wallet`` with a value of 100
3. Create a dictionary containing 3 pets
    - The key is the pet's name
    - The value is the pet object
4. Create a while loop that ends when all the pets in the list are dead
    - (*editor's note: oof, harsh*)

**READ ALL THE REQUIREMENTS BEFORE YOU START**

### Tick loop

5. For each run of the loop, print then increment the ``tick_counter``
6. Call the ``tick()`` method on each of the pets
7. Print out the pet's current status (derived from the result of the ``mood()`` method)
8. For each pet: if the pet is happy, 1 coin is added to the wallet
    - If you have three happy pets, you get 3 coins for this tick
9. Ask the user for input
    - The user can only enter one command per loop, so they must choose carefully what to do
    - If the user presses Enter/Return (i.e. no text entered), move to the next tick
    - If the user types any of the following commands, call the appropriate command on the specified pet:
        1. ``feed petname cake``: feeds the pet the specified cake, reducing their hunger or increasing their health (depending on the cake)
            - Feeding the pet deducts money, to the value of the cost of the cake, from the wallet
            - You can't feed the pet(s) if you have no money to buy cakes
        2. ``teach petname sound``: teaches the pet the specified sound
        3. ``sounds petname``: lists all available sounds that a pet knows
        4. ``cakes``: lists all the available cakes and their effects
    - Examples:
      - ``feed spot berry``
        - ``Fed Spot the berry_cake. Spot gained 5 health!``
        - ``You can't afford pod_cake.``
      - ``teach rover burrrrrp``
        - ``Taught Rover burrrrp. Rover lost 50 boredom and gained 25 hunger!``
      - ``sounds fido``
        - ``Fido knows how to say: "meow", "woof", "wan wan", "dood", and "screech"``
      - ``cakes``
        - ```
          Cake: costs 0, restores 5 hunger
          BerryCake: costs 5, restores 10 hunger and 5 health
          BananaCake: costs 10, restores 15 hunger and 2 health
          etc.
          ```
    - Invalid commands (such as typos) count as wasted time — don't ask for another command
10. ~~When~~ If your pets die, remove them from the list of pets.
11. Memorialise all your pets at the end of the program, showing how many ticks they lived.

# Extension

1. Create a subclass of ``Pet`` that has a lower health limit (less than 100, so a potentially shorter life) but set the boredom limit to 100 (so it stays happy — until it isn't)
2. Create a subclass of ``Pet`` that has a higher health limit (between 101 and 200, so it lives longer) but a higher hunger rate (so it gets hungry faster)
3. Create a ``Cake`` object that fully restores health to the pet's maximum and reduces hunger to 0 — but costs 200
4. Show each pet's statics with a status bar every run
5. Make it so that you can only run a command every 5 ticks
6. Make it so that a pet can't eat two cakes in a row

{% include task.html task_code="ewoheeAD" %}