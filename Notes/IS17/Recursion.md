---
layout: page
title: Recursion
---

- **Recursion** the process of repeating items in a self-similar way
	- Ex. two mirrors facing each other have nested images, creating an infinite recursion

- Recursion algorithms have (**KNOW THIS**)
	- A method that **calls itself**
	- When *calling* itself, parameters change (**recursive condition**)
	- A condition to stop (**base condition**)

- Uses of recursions:
	- Problems where a large task can be broken down into repetitive sub-tasks
	- Because a recursive routine calls itself to perform those sub-tasks, eventually the routine will come across a sub-task that it can handle without calling itself
		- This is known as a **base case** - and it is needed to prevent the routine from calling itself over and over again without stopping
		- The **recursive case** is when the routine is able to call itself with a new parameter

## Stacks:
- A type of data structure in which the principal (or only) operations are the addition of an entity to the collection (push) and the removal of an entity (pop)
- The relation between the push and pop operations is such that the stack is a last-in-first-out (LIFO) data structure
- In this, the last element added to the structure must be the first one to be removed

### Stacks in Java:
```java
Stack<String> sampleStack = new Stack<String>;
sampleStack.push("TestItem1");
sampleStack.push("TestItem2");
sampleStack.push("TestItem3");

System.out.println(sampleStack.pop());
System.out.println(sampleStack.pop());
System.out.println(sampleStack.pop());
```

## Call Stacks, Recursion, and Stack Frames
- A call stack is a data structure used by the program to store infromation about the active subroutines in a program
- The program can keep track of where a subroutine should return control to once it finishes executing

