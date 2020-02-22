---
layout: page
title: Methods
---

- Organize programs into sections
- Allow sections of one program to be re-used in another program
- Enhance the readability of a program
- Methods can be called from anywhere



==**Methods can take parameters**==

- Parameters allow you to pass data to the function
- Parameters must have a name & data type

```java
public static void main(String args[] ) 
{
  String message = “Hello World”;
  printMsg( message );    // Go DO the method CALL
}

private static void printMsg( String msg ) // method DEFINITION
{
  System.out.println( msg );
}
```

### Return Statements

- transfer a value back from a function

- you can only send back ONE piece of information

- can only be used with functions that are non-void

- e.g. private static float distance(int x1, int y1, int x2, int y2);

- private static int taxcode(float salary);

## Scope

- You can have variables with the same name in different methods.

```java
public static void main()
{
	int a = 4, b = 6, c;
	int a = 15, c = 9;  // ILLEGAL can’t re-declare in same scope
}

private static void meth1(int x, int y){
 	int a = 7, b = 5; // OK: different block i.e. {}
}

private static void meth2(int a, int b) // OK: different a & b 
{
	int c; // OK: different c than main’s
}

```

- Actual and Formal parameter names do NOT have to match
  - the values map by POSITION 

```java
public static void main() 
{
	int g = 50, h = 90, k;

	k = meth3(g, h);
	System.out.println( k ); 
	k = meth3(h, g);
	System.out.println( k );
	k = meth3(h, h);
	System.out.println( k );
}

private static int meth3(int g, int h) 
{
	return g - h;
}
```

