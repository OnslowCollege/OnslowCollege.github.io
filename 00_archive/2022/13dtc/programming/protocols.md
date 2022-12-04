---
title: Protocols
grand_parent: 13DTC
parent: Complex Programming
nav_order: "be"
learning_intentions: ["What a protocol is", "When to use a protocol", "How to declare a protocol class", "How to declare that a class conforms to a protocol"]
success_criteria: ["You have declared a protocol class", "You have declared at least two classes that conform to the protocol by implementing the necessary methods"]
---

# Protocols

**Protocols** allow you to define a set of methods inside a *protocol class*.

Protocol classes contain a series of methods that:
- state if they return a value, and what type (i.e. ``def my_method() -> str`` returns a string)
- contains no implementation — the only thing they do is ``pass``

## Why use protocols?

The purpose of a protocol class is to act as a **contract**. The contract states:

- any class that **conforms** to the protocol will **implement** these methods
  - that is to say, the functions will do something, not just ``pass``
- any class that conforms to the protocol will return values with the same types

This helps to enforce an old adage: if it walks like a duck and it quacks like a duck, then it must be a duck.

# Declaring a protocol

Let's declare a protocol. This involves:

1. importing ``Protocol`` from the ``typing`` module
2. defining the protocol class' name
3. declaring that the protocol class [inherits](inheritance.md) from the ``Protocol`` class
4. defining the method names, types, and making them all ``pass``

```python
from typing import Protocol

class AlarmRingable(Protocol):
	def ring_alarm(self) -> None:
		pass

	@property
	def alarm_sound(self) -> str:
		pass
```

Above, we have declared a protocol class called ``AlarmRingable``. It has two methods. Currently, neither do anything.

# Conforming to a protocol

We then create another class that *conforms* to the protocol. In this case, let's add a school building.

To conform to a protocol:

1. Add the protocol name within brackets next to the class name
2. Copy the protocol class' methods
3. Remove ``pass`` and add code to each of the functions

```python
@dataclass
class TableMountainBuilding(AlarmRingable):
	def ring_alarm(self) -> None:
		print(self.alarm_sound * 5)

	@property
	def alarm_sound(self) -> str:
		return "DING"

room_62 = TableMountainBuilding()
room_62.ring_alarm() # DINGDINGDINGDINGDING
```

# The power of protocols

When we know that a class conforms to a protocol, we know exactly methods can be called on it without having to look at each individual method in it. This "contract" becomes even more flexible when:

- multiple classes in your code conform to the same protocol
- classes conform to multiple protocols at once

## Multiple classes conforming to the same protocol

In the following example, multiple classes conform to ``AlarmRingable``. This is our contract that guarantees that all of these buildings have alarms installed. When each class implements the protocol methods, they can define their own separate alarm sounds and behaviours.

```python
@dataclass
class TableMountainBuilding(AlarmRingable):
	def ring_alarm(self) -> None:
		print(self.alarm_sound * 5)

	@property
	def alarm_sound(self) -> str:
		return "DING"

@dataclass
class OfficeBuilding(AlarmRingable):
	def ring_alarm(self) -> None:
		print(self.alarm_sound)

	@property
	def alarm_sound(self) -> str:
		return "WOOOOOOOOOOOOOOOOOOOOOOOOOO"

@dataclass
class GymBuilding(AlarmRingable):
	def ring_alarm(self) -> None:
		print(self.alarm_sound * 10)

	@property
	def alarm_sound(self) -> str:
		return "DKK"

room_62 = TableMountainBuilding()
office = OfficeBuilding()
gym = GymBuilding()

buildings = [room_62, office, gym]

for building in builds:
	# Ringing the fire alarm in each building.
	# We only know that we can call ring_fire_alarm() on them
	# because we know the classes conform to AlarmRingable
	building.ring_alarm()

# DINGDINGDINGDINGDING
# WOOOOOOOOOOOOOOOOOOOOOOOOOO
# DKKDKKDKKDKKDKK
```

### Checking if a class conforms to a Protocol

Sometimes, you might be dealing with a class where it's not clear whether or not it conforms to a Protocol. Perhaps it has a similar name to conformant classes — but you still aren't sure.

You can check if a class conforms to a protocol using an ``is`` check:

```python
class CaretakerShed:
	# This class does NOT conform to AlarmRingable
	pass

room_62 = TableMountainBuilding()
office = OfficeBuilding()
caretaker_shed = CaretakerShed()
gym = GymBuilding()

buildings = [room_62, office, caretaker_shed, gym]

for building in buildings:
	# Check if the building conforms to the protocol
	if building is AlarmRingable:
		building.ring_alarm()
	else:
		# Does not conform
		print("We're all gonna die!")

# DINGDINGDINGDINGDING
# WOOOOOOOOOOOOOOOOOOOOOOOOOO
# DKKDKKDKKDKKDKK
# We're all gonna die!
```

## Classes conforming to multiple protocols

In the following example, we create another class that conforms to another protocol.

To do this:
1. when defining the class, add all the protocols to which it conforms inside brackets next to the class name
2. separate the protocols by a comma and space

We will create a protocol called ``SelfLockable`` that designates that a building can lock itself in case of a fire. Let's make the office able to lock its own doors in case of a lockdown:

```python
class SelfLockable(Protocol):
	def self_lock(self) -> None:
		pass

@dataclass
class OfficeBuilding(AlarmRingable, SelfLockable):
	doors: list

	# AlarmRingable
	def ring_alarm(self) -> None:
		self.self_lock()
		print(self.fire_alarm_sound)

	@property
	def alarm_sound(self) -> str:
		return "WOOOOOOOOOOOOOOOOOOOOOOOOOO"

	# SelfLockable
	def self_lock(self) -> None:
		for door in self.doors:
			door.lock()
```

{% include task.html task_code="AWAHBFd3" %}
