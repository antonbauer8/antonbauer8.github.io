---
layout: page
title: Basic Syntax
---

## Variables and Operations

- Store information needed by the program

- Must have a TYPE
	- `int` - can only store a number without a fractional part
	- `float`, `double` - can store any number, with or without a fractional part (double has more precision)
	- `char` – individual character (letter,digit,punctuation etc.)
	- `String` - text data
	- `boolean` – store value true or false
	- More later on values of true/false

- Must have a VALUE, the value can change as the program runs
	- if you don’t provide an initial value, the compiler will supply one for you.  That initial value is zero for the primitive types, null for strings.

### Literal Values
- Every primitive type (and Strings) can be initialized using a literal of the type. Here are examples of literal values:

| Type    | Literal Value | Example Initialization           |
|:------- |:------------- |:-------------------------------- |
| String  | "Hello World" | String greeting = “Hello World”; |
| char    | 'A'           | char letter = ‘A’;               |
| boolean | true          | boolean flag = true;             |
| int     | 1024          | int kilo = 1024;                 |
| double  | 3.154159      | double pi = 3.14159;             |

- Note the difference between a char literal and a String literal. A char literal is in single quotes while a String literal is in double quotes. A String may consist of only one character but a char cannot consist of multiple characters.
- `String s = “A”;  // LEGAL`
- `char c = ‘AB’;   // ILLEGAL`

### Naming Variables
- Must have a NAME
	- the name must start with an alphabetic (or “\_” )
	- the name may include alphabetics, digits, and underscores
	- the name should indicate the purpose of the variable in the overall design and purpose of the program
		- lousy variable names - larry, moe, curly, ah67, gh\_78
		- reasonable variable names - width, fileName, cursorPosition, count, response
- You should not have a program that consists entirely of single letter variables names.  It is too hard to read. When code is being explained in class I may however use single letter variable names, not because it is good programming style but because I don’t have a lot of room on the slides.
- Java strongly encourages variables to be named all lower case except as noted below:
- If your variable name is a multi-word name then make the first word of the name lowercase and subsequent words start with a capitol.
- Examples of  multi-word variable names:
	- fileName
	- remoteUserAddress
	- phoneBook

### Assignment
- the = operator assigns
	- the value on the right to the variable on the left WARNING! Not to be confused with the == operator which compares (asks “are they equal?”).
- it is extremely counter-intuitive because it assigns from the right to the left and we read from the left to the right.
- the left hand side MUST be a variable
- the right hand side can be a variable or an expression

`int x = 0, y = 3, z = 4;`

```java
z = 10;		// z is given the value of 10
x = y + 5;    // x is given the value of y + 5 (i.e. 8)
x = x + 1;    // takes the current value of x and increments it by one
```

- at the end of these 3 statements, what are the values of x, y, and z?

```java
10 = z;		// WRONG , can’t have number on left hand side of =
3 + y = y;	// WRONG, can’t have expression (3 + y) on left hand side
```

### Named Constants
- A magic number is a numeric constant that appears in your code without explanation.
- e.g.
	- `answer = rate * 1.67;   // what is the significance of 1.67?`
- instead make a named constant using keyword final

```
// this is the scheduled rate increase
final float RATE_INCREASE = 1.67;
answer = rate * RATE_INCREASE ;
```
- The value of a named constant cannot be assigned another value.
- *Java strongly encourages use of ALL CAPS for constants. Multi word constant names can have an UNDERSCORE between words*

### Variable Conversion
- When doing operations with different variable types (assuming they are compatible), the more precise of the two types is how the result will be stored
	- 5 + 13.5 = 18.5
	- 5 + 8 = 13
	- 3.0 / 4 = 0.75
	- 3 / 4 = 0 \<--- always *truncates* (rounds to lower value)
	- 3 / 4 \* 10 = 0 \<--- order of operations (/ first then \*)

### Some Operation Shortcuts

| This         | Same as | This                      |
|:------------ |:------- |:------------------------- |
| `x = x + 5`  | Same as | `x += 5`                  |
| `x = x * 10` | Same as | `x *=10`                  |
| `x = x - 9`  | Same as | `x -=9`                   |
| `x = x % 3`  | Same as | `x %= 3`                  |
| `x = x + 1`  | Same as | `x++` OR `++x` OR `x +=1` |

#### ++x vs. x++
- `++x` increments x *before* its value is returned
- `x++` increments x *after* its value is returned

---
## Booleans
- Recall that Java provides a data type boolean which can take on only one of two values: **true** or **false**.
- `boolean b = true;  // stores the truth value true in b`
- `b = false; // overwrites b with the value false`
- There are other ways to create boolean values and assign them into boolean variables besides a simplistic direct assignment of a boolean literal into a variable. Boolean operators produce true/false values.
- For example let’s assume this declaration:  `int i = 10;`
- We can assign a truth value into variable b using boolean operators like this:  `b = i < 20;`
- The expression i \< 20 is true since I contains the number 10. The value true is then assigned into the variable b.

### Boolean Operators

| Operator    | Result                                                                        |
|:----------- |:----------------------------------------------------------------------------- |
| &&          | Both x & y must be true to return true *ex. true && false = false*            |
| double line | Either x or y must be true to return true *ex. true double line false = true* |
| !           | Returns the opposite boolean *ex. !false = true*                              |

### Boolean variables
- boolean variables can have the value true or false.  That’s it.

```java
boolean minor, foo;
int age = 21;

foo = true;
minor = ( age < 18 );  // (age<18) produces either true or false
```
- What value is now in the variable minor?
	- False (`21 !< 18`, so returns false)

### DeMorgan's Law
**DeMorgans Law** - any expression can be equivalently expressed by multiplying a NOT through the boolean expression and changing || to && or changing && to ||

- The negation of a conjunction is the disjunction of the negations
	- !(p && q)  --\>  !p || !q

- The negation of a disjunction is the conjunction of the negations
	-  !(p || q)  --\>  !p && !q

## If Statements
- **Simple conditional:** use if

```java
if ( age < 21 )
{
	System.out.println(“too young to drink :=( ”);
}
```
- **Two way branch:** use if else

```java
if ( age < 18 )
{
	 System.out.println(“too young to drink :=( ”);
}
else
{
	System.out.println(“Draft or bottle?”);
}
```

- **Three way branch:** use an if else/if else

```java
if ( age < 18 )
{
	 System.out.println(“too young to drink :=( ”);
}
else if ( age < 70 )
{
	System.out.println(“Draft or bottle?”);
}
else
{
	System.out.println(“How about some Geritol instead?”);
}
```

### Good Usage of the If Test
- You may have your if structured like this:

```java
if ( <boolean expression here>)
{
	// nothing in the if part
}
else
  do something
```

- In that case negate the test and put the action under the if instead of the else

```java
if ( !<boolean expression here> )
	   do something
```
- *Now you don’t need the else*


