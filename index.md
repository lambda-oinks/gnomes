---
title: Infinite Gnomes and the Axiom of Choice
date: 2014-04-03
author: Oinkina
mathjax: on
published: true
---

Axioms are the building blocks of mathematics, with which all proofs and theorems are constructed. They are the only aspect of math that is considered to require faith. Change the axioms and you might get an entirely different self-consistent and beautiful system. For example, whole new systems of geometry, known as [spherical] and [hyperbolic geometry], grew out of challenging Euclid's Fifth Postulate on parallel lines[^parallel], which was considered an essential axiom of geometry for thousands of years.

[spherical]:http://en.wikipedia.org/wiki/Spherical_geometry
[hyperbolic geometry]:http://en.wikipedia.org/wiki/Hyperbolic_geometry

[^parallel]: Euclid's Fifth Postulate: "If a line segment intersects two straight lines forming two interior angles on the same side that sum to less than two right angles, then the two lines, if extended indefinitely, meet on that side on which the angles sum to less than two right angles" ([Wikipedia]).

[Wikipedia]: http://en.wikipedia.org/wiki/Parallel_postulate 

The [axiom of choice] causes really intreresting things to happen. An informal definition is:

[axiom of choice]:http://en.wikipedia.org/wiki/Axiom_of_choice

> If you have an infinite number of sets of arbitrary sizes, there exists a deterministic chioce function which will choose one element from each set.

Seemingly innocuous, right? I was hanging out at Stanford with some friends and Benjamin Cosman, the Benevolent Dictator for Life of the Caltech Puzzle Club when this topic came up in conversation. Ben gave me the following puzzle whose solution relies on the axiom of choice to see what sort of craziness it causes.[^ack] 

[^ack]: Thanks to Ben for also editing this post.

The Infinite Gnomes with Hats Puzzle[^2]
---

[^2]: [Tanya Khovanova] has a nice blog post about this that I stumbled across when I was trying to make sure I'd understood it correctly.

[Tanya Khovanova]: http://blog.tanyakhovanova.com/?p=157

There is a crowd of a countably infinite number of gnomes (with infinite vision and memory), such that each is randomly assigned, independently of the others, to have a black or white hat. They will all be asked to write down what hat they think they are wearing, and can confer before hat assignments. The gnomes will win if they as a whole have an infinite success rate, with only a finite number of gnomes guessing incorrectly. What should their strategy be? This is solvable, if you believe in the axiom of choice.

The Solution
------

### Codes and Buckets

Let's start with a small detour: think of code-strings being transmitted. Two codes are identical if each indexed element in one is the same as the element in the other at the same index. There are occasionally errors, with a 0 transmitted as a 1 or vice versa, so it is useful to define a notion of how different two given codes are. If you compare code X to code Y of equal length, error(X, Y) is defined as the number of digits that would have to be point-wise changed for the codes to be identical. For example, if A=1001011, B=1000011, and C=1001101, error(A, B) = 1, error(A, C) = 2, and error(B, C) = 3.

The set of all infinitely long codes can be divided into infinitely many "buckets,"[^partition] such that each bucket contains all the codes that have a finite error between each other. This notion of finite error is transitive: if error(A, B) is finite, and error(B, C) is finite, error(A, C) is also finite, because it is at most error(A, C) + error(B, C). Thus the bucket can alternatively be considered to contain all the codes that have a finite error relative to any given code from that bucket, so the bucket can be referred to by an arbitrary representative code.

[^partition]: Dividing splitting up the set into "buckets" is more formally known as [partitioning the set](http://en.wikipedia.org/wiki/Partition_of_a_set) into "blocks" or "cells." The buckets must be disjoint sets that union to the entire set of all codes.

For example, one bucket might contain all the infinite codes that have the form: a finite number of 0s and 1s interspersed in whatever which way, followed by an infinite number of 0s. Any code would have an error relative to others in that bucket of *at most* the length of the first part of this form of interspersed 0s and 1s, which is finite. We could consider this the "1000... bucket" and computer errors relative to it, or the "11000... bucket," or the "101101000... bucket," and the errors would be finite regardless.

### Axiom of Choice

You might be wondering how errors and buckets and 0s and 1s have anything to do with gnomes and hats (and no, flipping buckets upside-down does not constitute hats). The gnomes are very clever and have realized that the space of all their possible fates can be organized this way. Treat a white hat as 0 and a black one as 1, and line up and read hats off from back to front as the code.

Here's where the axiom of choice plays in. The gnomes need to pick an arbitrary representative code from each of the infinitely many buckets. We cannot construct a function by which to deterministically pick an element from each of an infinite number of sets, but if you believe in the axiom of choice, this does indeed exist. So the gnomes now know infinitely many representative codes that each correspond to a particular bucket.

When a gnome looks at all the gnomes in front of them, they know which bucket they must be in by matching it to the representative code of colors-turned-numbers. All the gnomes will agree on which bucket they're in. Then they'll each guess that their hat color is the color it would be if it were actually matching the representative code, at the same index.

Because the bucket is defined as the set of all codes with a finite error from the representative code of that bucket, regardless of what the representative code is, the accuracy of any individual gnome does not mattter. The code composed of all the gnomes' hat assignments is in the same bucket as the representative code, which is the code composed of their guesses, and so the guesses code can only have a finite error relative to the assignments code. Following this algorithm, only a finite number of gnomes will guess incorrectly, corresponding to the errors, and so they will have an infinite success rate and win.

Apparent Paradox
------

This solution feels paradoxical because each gnome's guess relies on no information about the gnome hats behind them and is determined seemingly arbitrarily from the pattern of hats in front of them---and yet the gnomes as a whole have an infinite success rate. Inspecting the algorithm we used, the only questionable step is when we invoked the axiom of choice. If we don't believe in it, the solution does not work, but believing in it gives us this elegant algorithm.