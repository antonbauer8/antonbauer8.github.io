---
layout: page
title: Interfaces
---

- In C++ a class definition can inherit from multiple parents. This is multiple inheritance and it is not directly supported in Java.  Java does however have the **interface** keyword which provides a way to inherite the interface from more than one parent.

<u>An interface is like an abstract class except:</u>

1. abstract keyword is used to create an abstract class and it can be used with methods also whereas interface keyword is used to create interface and it can’t be used with methods.
2. ubclasses use extends keyword to extend an abstract class and they need to provide implementation of all the declared methods in the abstract class unless the subclass is also an abstract class whereas subclasses use implements keyword to implement interfaces and should provide implementation for all the methods declared in the interface.
3. Abstract classes can have methods with implementation whereas interface provides absolute abstraction and can’t have any method implementations.
4. Abstract classes can have constructors but interfaces can’t have constructors.
5. Abstract class have all the features of a normal java class except that we can’t instantiate it. We can use abstract keyword to make a class abstract but interfaces are a completely different type and can have only public static final constants and method declarations.
6. Abstract classes methods can have access modifiers as public, private, protected, static but interface methods are implicitly public and abstract, we can’t use any other access modifiers with interface methods.
7. A subclass can extend only one abstract class but it can implement multiple interfaces.
8. Abstract classes can extend other class and implement interfaces but interface can only extend other interfaces.
9. We can run an abstract class if it has main() method but we can’t run an interface because they can’t have main method implementation.
10. Interfaces are used to define contract for the subclasses whereas abstract class also define contract but it can provide other methods implementations for subclasses to use.

A class can implement multiple interfaces.

```java
/* TestDrawable.java
   define an inteface and implement that interface in a class
*/

interface Drawable
{
	public final static int BLUE = 1, RED = 2;
	void setColor(int c);
	void setPosition(double x, double y);
	void draw();
} //END interface Drawable


// by implementing Drawable we are required to define the code bodies for
// setColor, setPosition, and draw inside this class

class DrawableCircle extends Circle implements Drawable
{
	private int color;
	private double xpos, ypos;
	public DrawableCircle(int radius)
	{
		super(radius); // just called our Parent (Circle's) C'Tor
		System.out.println("Just constructed Drawable Circle");
	}
	public void setColor(int c)
	{
		color = c;
		System.out.println("set Color");
	}

	public void setPosition(double x, double y)
	{
		xpos = x; ypos = y;
		System.out.println("Set Position");
	}

	public void draw()
	{
		System.out.println("Draw");
	}

} // END DrawableCircle class

// ================ App with Main method ==================

public class TestDrawable
{
  public static void main(String args[])
  {
	DrawableCircle c = new DrawableCircle(5);
	System.out.println(c.area());
	System.out.println(c.perimeter());
	c.setColor(Drawable.BLUE);
	c.setPosition(1.5, 2.5);
	c.draw();
  }
}
```

