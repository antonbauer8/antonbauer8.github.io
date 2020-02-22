---
layout: page
title: Scope and Loops
---

## Block/Scope
- Variables defined within a block are only usable from within that block or nested blocks within it.

- Blocks can be nested to an arbitrary depth. Variable names cannot be re-used in a
nested block but can be re-used in unrelated blocks. Analogy: You don’t name two kids in the same family with the same name *but* two different families can have
kids whose names are identical.

- **Rule of usage:** Never declare a variable to have wider scope that needed to accomplish its purpose. Our val variable is only
needed inside the accumulation loop. Thus we don’t declare it at same level as sum.

## Loops
- Used to repeat an action
- Must have a STOP condition
- Three flavors - `for`, `while`, `do/while`

### While Loops
- The test is checked at the very beginning and then again each time
after the *after the entire loop body* has been executed
- The test is NOT checked in the middle of the loop body
- This is true for all the loops (for, while, and do/while), not just
the while loop
- A while is just an if statement that keeps going back to the test and
quits looping at first failure of test

### Do While Loops

- Do loop is a variant of the while that waits till the bottom to make the test. There are some very good uses for the do form of the while loop	
  - Such as error checking

```java
final int MAX = 10, MIN = 5;
int number;
do
{
	System.out.print(“Enter # between “ + “5 and 10 inclusive: “);
	number = kbd.nextInt();
	if (number < MIN || number > MAX)
		System.out.println(“:=( Try again”);
} while (number < MIN || number > MAX);

System.out.print(“The user entered “ + number );
```

- Do While Loops always run through the loop once, *then*checks for a condition and deicdes if it should loop again

### For Loops

1. exec the init
2. exec the test
3. when the test is *true*
   - exec the body
   - exec the update
   - go back to step 2

3. when the test is *false*
   - exit the loop

```java
int cnt;
for (cnt = 5; cnt <= 13; cnt += 3)
{
	System.out.print(“*“);
}
System.out.println(“done“);
```

### Nested For Loops

- For loop *within*a for loop
- ALWAYS use different for loop variables (i & j in this example) for
  nested loops

```java
int i,j;
for ( i=0; i <= 5; ++i )
{
	for (j=0; j <= 3; ++j )
	{
		System.out.print( “i: ” + i + “, j: “ + j";
	}
	System.out.println();
}
System.out.print(“After loops i= “ + i + “, j= “ + j );
// Why did we declare i and j outside (before) the loops?
```

