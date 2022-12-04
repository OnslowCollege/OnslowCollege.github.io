---
title: Introduction to Complexity & Tractability
grand_parent: 12DTC
parent: L2 Computer Science
nav_order: "ba"
---

There are many problems that are too complex for a computer to solve in reasonable time. Some would take hundreds, maybe even billions, of years.

It's not even a question of using a faster computer; even if it were a hundred times faster, certain problems would take million of years would only reduce down to hundreds of years.

Determining the **complexity** of a problem is one of the issues that computer scientists deal with — what kinds of problems are computers not suited to solving?

# What is tractability?

The area of **tractability** explores problems and algorithms that can take an impossible amount of computation to solve, except perhaps for very small examples of the problem.

<iframe src="https://player.vimeo.com/video/203039205?h=cd7738a03a&color=ffffff&title=0&byline=0&portrait=0" width="640" height="360" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>
<p><a href="https://vimeo.com/203039205">Computer Science Field Guide: Tractability</a> from <a href="https://vimeo.com/uccser">UC CS Education Research Group</a> on <a href="https://vimeo.com">Vimeo</a>.</p>

{% include shout.html side="left" emote="📕" markdown="A basic definition of a **tractable problem** is one that a computer problem could solve in a reasonable amount of time. If it is intractable, it is too complex." %}

> In that sense, complexity leads to intractability. However, that doesn't mean all complex programs are intractable!

A computer scientist needs to be able to recognise when a problem is intractable in order to try other approaches (and not waste time!).

A very common approach is to give up on getting a *perfect* answer and settle for a usable, *approximate* answer. There are a variety of techniques for getting good approximate answers to hard problems; a way of getting an answer that isn't guaranteed to give the exact correct answer is sometimes referred to as a *heuristic*.

## Example of an intractable problem

A well-known example of an intractable problem is the Travelling Salesment Problem (TSP). You've seen it in the video above: if you have a collection of places you need to visit, and you kno the distance to travel between each pair of places, what's the shortest route that visits all of the places exactly once?

This is a very practical problem that comes up in the real world: couriers choosing routes to deliver parcel,s rock bands planning tours, or a taxi driver dropping multiple passengers off after an event.

{% include shout.html side="right" emote="🛫" markdown="In fact, the measurement between places doesn't have to be distance: it could be the dollar cost to travel between two places. For instance, if you needed to visit Queenstown, Christchurch, Wellington, and Auckland one after the other and you knew the airfare prices in advance, you could work out the cheapest way to fly between each of them. This is still an example of the TSP." %}

## Benefits of intractability

Of course, there are situations where intractable problems are helpful — most security and cryptography algorithms are based on them. The codes are only breakable after billions of years of computing, so the effort would be futile.

In fact, if anybody every finds a fast algorithm for solving such problems, a lot of computer security systems would stop being secure overnight! Therefore, one of the jobs of computer scientists is to be confident that such solutions *don't* exist.

# What is complexity?

**Complexity** is an important concept with problems and the algorithms that solve them.

Generally speaking, complexity is the time it takes to solve a problem. However, the way we measure "time" can differ depending on the problem. Of course, you can actually measure the amount of time elapses from the time a program starts to the time it finishes.

However, it can be helpful to get a rough idea of the inherent behaviour of an algorithm in advance.

Computer scientists often start by estimating the number of steps the algorithm will take for ***n*** items; ***n*** represents how many items are in a collection (such as a list, set, etc.). For example:

- a linear search can end up checking each of ***n*** items to be searched, so the algorithm will take ***n*** steps
- an algorithm that compares every pair of values in a list of ***n*** items will have to make ***n<sup>2</sup>*** comparisons so it will take ***n<sup>2</sup>*** steps

Having a rough idea of the complexity of a problem helps to estimate how long it is likely to take, rather than actually have to spend a lot of time waiting.

For example, if you write a program and run it with a simple input, but it doesn't finish after 10 minutes, you must decide: should you quit or wait for it to finish? If you can estimate the number of steps it needs to make, you can extrapolate (deduce based on the time it takes other, similar programs to do a similar task).

{% include shout.html side="right" emote="⏰" markdown="Use this [Algorithm Timer](https://www.csfieldguide.org.nz/en/interactives/algorithm-timer/) to find out how long complex algorithms will take to compute." %}

## The Towers of Hanoi

The Towers of Hanoi problem is a challenge where you have a stack of disks of increasing size on one peg, and two empty pegs. The challenge is to move all the disks from one peg to another, but you may not put a larger disk on top of a smaller one. There's a description of it at [Wikipedia](https://en.wikipedia.org/wiki/Towers_of_Hanoi).

{% include shout.html side="left" emote="🎮" markdown="[Play Towers of Hanoi](https://www.mathsisfun.com/games/towerofhanoi.html)" %}

This problem cannot be solved in fewer than ***2<sup>n</sup> − 1*** moves, so it's an intractable problem (a computer program that lists all the moves to make would use at least ***2<sup>n</sup> − 1*** steps). For six disks, it only needs 63 moves, but for 50 disks this would be 1,125,899,906,842,623 moves.

We usually characterise a problem like this as having a complexity of ***2<sup>n</sup>***, as subtracting one to get a precise value makes almost no difference, and the shorter expression is simpler to communicate to others.

The Towers of Hanoi is one problem where we know for sure that it will take exponential time. There are many intractable problems where this isn't the case – we don't have tractable solutions for them, but we don't know for sure if they don't exist. Plus this isn't a real problem – it's just a game (although there is a backup system based on it). But it is a nice example of an exponential time algorithm, where adding one disk will double the number of steps required to produce a solution.

For more information, check out [FreeCodeCamp's illustrated algorithm guide](https://www.freecodecamp.org/news/analyzing-the-algorithm-to-solve-the-tower-of-hanoi-problem-686685f032e3/) for this problem.

# Task

Answer the following questions in a Word document or OneNote page:

1. in your own words, explain the difference between complexity and tractability
2. try the Towers of Hanoi game. Work out how many steps would be needed for 20 disks