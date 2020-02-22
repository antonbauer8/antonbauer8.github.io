---
layout: page
title: Coupling, Cohesion, and Abstraction
---

## Coupling:
- Strength of elements connection, knowledge of, and/or dependence to/on
each other 

Problem:

- How to reduce the impact of change? 

Solution:

- Assign responsibilities to minimize coupling between objects 
- Simple chain of command


**TLDR**

- Try to reduce interconnectedness (ex. object instantiation) so when a change is made to something, it only messes up as little as possible.

Benefits of Low Coupling:

- Easier to reuse
- Easier to understand
- Easier to maintain
- Coupling to class libraries is more acceptable 
	- Such as Java libraries (more stable)

## High Cohesion:

Cohesion:

- measure of how functionally related the operation of the software elements are

Problem:
- How to keep objects focused, understandable, and maintainable?

Solution:
- Make sure that an object’s responsibilities (methods) are closely related

## Abstraction:
- Objects are “black boxes.“ The underlying implementations of objects are hidden from those that use the object.
- All but the relevant information about the object is hidden

## Public Interfaces:
- The String class declares many other methods besides the length and toUpperCase methods.
- Collectively, the methods form the public interface of the class.
• The public interface of a class specifies what you can do with its objects.
- The hidden implementation describes how these actions are carried out.

## Encapsulation vs. Abstraction:

*Encapsulation:*

- Information hiding

*Abstraction:*

- Focuses on the outside view of an object (i.e. the public interface) 
- Working on a higher level, not worrying about the internal details - Objects as “black boxes”