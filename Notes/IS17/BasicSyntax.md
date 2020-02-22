---
layout: page
layout: page
title: Basic Syntax
---

Variables are spaces in memory where values can be stored

- The value can change, so it is variable
- Every variable has a type
- A variable cannot change its type
- Some types:
	- int: integer
	- double: number with decimal
	- String: text
	- boolean: true or false value
	- char: single character (always in single quotation marks)

- Declaration: set type, creates a variable (allocates it in space)
	- `int x // (declaration) = 5 // (initialization)`

- Declaration and initialization done in one line
- Initialization: assigns initial value to a variable

```java
	int x; // (declaration)
	x = 5; // (initialization)
```

- Declaration and initialization done in two separate lines
- NOTE: Equals sign (=) ASSIGNS a value to a variable. It does not involve equality.
	- Comparing values uses a double equals sign (==)

## Variable Naming Conventions:
- Single word variables are written in all lowercase
	- `int x`
	- `int product`
	- `double age`
- Multi word variables are written with first word lowercase and subsequent words capitalized
	- `String firstName`
	- `int numberOfDoors`

## Constants:
- Variables that cannot be changed after they are declared and initialized
- Done by writing final  before declaring the variable
	- Ex. `final double pi = 3.14159`

- Constant names are capitalized
	- `final double SCORE`

- Multi word constants are separated by an underscore
	- `final double TOTAL_SCORE` 

## Basic arithmetic Operators:
- Basic operators:
	- Addition: +
	- Subtraction: -
	- Multiplication: *
	- Division: /
	- Modulus: % 
- Calculates the remainder of division
- Often used to determine if number is odd or even
- A combination of operators, values, and variables is an expression (always terminated with a semi-colon)
- Order of operations : uses basic PEMDAS principles
- NOTE: mixing integer and floating-point values in an operation always results in a floating-point value
	- `int x = 5;`
	- `double y =2.5;`
	- `(double) result = 12.5;`

- *CAREFUL:* `double average = (1+1)/3` **WILL COMPUTE 0**
	- It treats the right side separately as integers because they are integers
	- Fix by assigning numbers as doubles first or writing (1.0+1.0)/3.0
	- The result will be a floating point so long as at least one number in the calculation is a floating point

- Shortcut: ++ increments variable by one and --decrements variable by one
	- `int counter = 0;`
	- `counter++;`

- Shortcut: += # and -= # increases or decreases a value by a given number
	- int number = 0;
	- number += 5;

- **Integer Division:**
	If both numbers in an equation are integers, the result will be an integer and the remainder will be discarded
	- 7 /4 evaluates to 1

## Math Operators:
- You can use the Math class for common mathematical operations

```java
	double x = Math.pow(2,8);   //takes 2 to the 8th power
	double y = Math.sqrt(4);   //takes square root of 4
	long r = Math.round(x/y);   //rounds the division up or down if higher/lower than .5
```

##Typecasting:
- Explicitly converting one data type to another
- Do so by putting the type you want to convert it to in parenthesis before the variable

```java
		double balance = 175.05;
		int dollars = (int) balance;
```

## Strings:
- A sequence of characters
- String variables hold a string
	- `String name = "Jack";`

- Note capital String not lowercase
- The length method takes the length of a string
	- `System.out.println(name.length());`

- A string of length 0 is an empty string, written as "" and initialized as String name = "";
- Concatenating strings links two strings together to form a longer string
	- `String firstName = "Walter";`
	- `String lastName = "White";`
	- `String fullName = firstName + " " + lastName;`

- Strings are made up of a sequence of characters
- String positions start counting at 0 and go up by 1 each character
- The `string.charAt(#)` method returns a char value from a string at a chosen position

## Escape Sequences:
- To type quotation marks within a string, enclose the quotation marks you want to keep with `\`'s
- To include `\`'s in a string, use `\\`'s instead
- To move a part of a string to a new line when printed, put `\n` before what you want on a new line
- To move a part of a string a tab over when printed, put `\t` before what you want tabbed

## Basic Input and Output:
- Data can be inputted from console, dialog box, text file, databases, etc.
*Output to console:*
	
```java
	System.out.println("Hello"); //prints and starts new line
	System.out.print("Hello"); //prints and stays on same line
```

*Input/output dialog box:*

```java
Import javax.swing.JOptionPane; 
	// (or type JOpt… and autocomplete)
	// Show output in dialog box:
JOptionPane.showMessageDialog(null, "Message");
	// Set an input:
String input = JOptionPane.showInputDialog("What is your name?");
```
## Converting Strings and Numbers:
- Number --> String

```java
String n = "" + int;
String n = String.ValueOf(int);
```

- String --> Number
	- Use special classes
	- `int integerInput= Integer.parseInt(inputInteger);`
	- `double doubleInput = Double.parseDouble(inputDouble);`
	- `long longInput = Long.parseLong(inputLong);`
