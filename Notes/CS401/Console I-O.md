---
layout: page
title: Console I/O
---

- Console I/O is input from the standard input device and or output to the standard output device.
- The *keyboard* is the **standard input device**.
- The *screen/monitor* is the **standard output device**.
- Java gives us the *Scanner* class to to read from the keyboard (and text files).
- Java gives us `System.out.print()`, `System.out.println()` and `System.out.format()` to write text to the standard output device.

## Console Output Using `System.out.print()` and `println()`
```java
System.out.println("Hello World"); // prints Hello World and a newline
System.out.print("Hello World"); // prints Hello World without a newline

int x=10, int y=5;
System.out.println("x+y=" + x + y); // prints x+y=105 DO YOU SEE WHY?
("x+y=10" + y); // "x+y=" + 10 evals to "x+y=10"
("x+y=105"); // "x+y=10" + 5 evals to "x+y=105"
```

- The expression in the ()s must evaluate to a single value. That value will be printed as a string to the output. If there are numbers and Strings mixed around the + operator, the + operator will convert the number to a String and concatenate. The operators are evaluated \* and / first (left to right) then + and – (left to right).

```java
System.out.println("x+y=" + (x + y)); // prints x+y=15
```

- The ()s around the second x+y force it to evaluate before the first +. Nested ()s evaluate inside out.

## `System.out.format()`
- When printing numbers to the screen you can control the format width and number of decimal places of precision using the format method.

```java
double pi = 3.14159265358979323846264338; // to 26 places
// BUT only up to 15 places max can be stored

System.out.println( "pi=" + pi );
// prints 3.14159265358979323846264338

// use format() to force max width of 6 places counting dot
// with 4 coming after the dot. The 59 rounds to 6
System.out.format( "pi=%6.4f", pi ); // prints 3.1416
```

## Input from Keyboard Using Scanner

```java
// System.in is the official name of the keyboard device
Scanner kbd = new Scanner(System.in);
System.out.print("Enter your name: "); //notice I dont' write a new line
String name = kbd.next(); //stop. Wait until user types stuff and hits return
System.out.println("You entered " + name);
//BEWARE! DO NOT ENTER MORE THAN ONE TOKEN (I.e. no spaces)

System.out.print("Enter single integer: ");
int number = kbd.nextInt(); //Attempt to convert to int then assign into number
System.out.println("Number you entered was " + number);

System.out.print("Enter a double: ");
double real = kbd.nextDouble(); //Attempt to convert to double then assign into real
System.out.println("Number you entered was " + real);

System.out.print("Enter a boolean: ");
boolean bool = kbd.nextBoolean(); //must enter literal true or literal false
System.out.println("Number you entered was " + bool);
```

### Scanners vs. Buffered Readers

- **Scanners**: Reads an input and separates everything by white space.
  - Ex. "Hello, my name is Zach." is parsed as an array[Hello, my, name, is, Zach.]
- **Buffered Readers**
  - Can read more complex chunks of things, like lines, words, whole files, etc.