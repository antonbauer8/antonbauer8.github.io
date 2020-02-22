---
layout: page
title: Inheritance
---

- Inheritence is probably the most important OOP concept. Creating a new type that is a descendant of another type is the foundation of the Java class hierarchy.

- To set up our intoduction to inheritence, we introduce another commonly seen OOP technique, *composition*, which looks similar to inheritence. Once composition is seen and understood the contrast between it and inheritence becomes clear.

  ```java
  
  // Account class:  stripped down version, no setters
  public class Account
  {
  	private String name;
  	private double balance;
  	public Account(String name, double balance)
  	{
  		this.name = name;
  		this.balance = balance;
  	}
  	public String getName()
  	{
  		return name;
  	}
  	public double getBalance()
  	{
  		return balance;
   	}
  	public void deposit(double amount)
  	{
  		balance += amount;
  	}
  	public void withdrawal(double amount)
  	{
  		if (balance >= amount)
  			balance -= amount;
  		// else handle NSF condition
  	}
  	// transfers funds OUT of this account To another account
  	public void transferTo( Account other, double amount )
  	{
  		if (balance >= amount)
  		{
  			withdrawal( amount );     // (attempt) withdrawal from this account
  			other.deposit( amount ); // deposit into other account
  
  		}
  		// else handle NSF condition
  	}
  
  	public String toString()
  	{
  		return name + " $" + balance ;
  	}
  }
  ```

- Inheritance is the real payoff of OOP. It allow reuse of code by allowing one class to extend the definition of a previous class. Typically the existing class is called the **parent** class, and the derived or extended class is called the **child** class.

```java
public class SpecialAccountTest
{
	public static void main(String args[])
	{
		SpecialAccount cust1 = new SpecialAccount("J",100.00,.10);
		System.out.println(cust1.getName());
		cust1.deposit(100.00);
		System.out.println(cust1.getBalance());
		System.out.println(cust1.getPercent());
    	}
}

class SpecialAccount extends Account
{
	double percent;
	public SpecialAccount(String name,double balance,double percent)
	{
		super(name,balance); // calling parent constructor MUST CALL PARENT 
		this.percent = percent;
	}
	public double getPercent()
	{
		return percent;
	}
}
```

It is the keyword **<u>extends</u>** that causes the new child class to inherit everything the parent has. The keyword **<u>super</u>** calls the parent's constructor. Just like the keyword call  `this(..)` to call a sibling constructor, `super(..)` must be the first line in the child class' constructor if you want to call your parent's constructor.

If you want to prevent your class from being extended use the keyword final before the word class.

```java
public final MyClass  // no one can extend this class
{
  // ....
}
```

## Polymorphism

- Inheritance has more advantages than just code re-use.  Inheritance allows binding of overwritten methods to be resolved dynamically at run-time.

```java
/* Polytest.java - demonstrates Polymorphism by deriving child and grandchild
   classes, then overloading print method of child and grandchild.
*/
public class PolyTest // Polytest is out main Appp
{
	public static void main(String args[])
	{
		A a[] = { new A(), new B(), new C() }; 
    	//you can put child objects in an array of parent objects
		for (int i = 0; i < 3; i++)
		a[i].print();
	}
} // END PolyTest app

//------------------------------------------------------------------------
// We combine our class definitions in same file as main App to save space

class A
{
	A() { }
	void print(){System.out.println("A"); }
}
class B extends A
{
	B( ){ }
	void print(){ System.out.println("B"); } 
		//overwrites print method from A to print B instead
}
class C extends B
{
	C(){}
	void print(){ System.out.println("C");}
  //overwrites print method from B to print C instead
}
```

- You may be looking at the above example and wondering "Why do we need polymorphism? " After all you could have just declared 3 totally unrelated classes, given them all print method and then invoked the print of each class.  The convenience of Polymorphism is that all the classes share the is-a relationship to the base class. As such we can declare an array of these classes. Note, you can't declare an array of different types. Thus every element in the array is-a Type A object. It is not until it is referenced at runtime that the object is distinguished to be an A ,B or C object and the proper print method resolved.
- The advantages are numerous. You can pass a reference to any of the types into a method expecting the base type.

## The Object Class

- The Object class is the ancestor of all classes in Java. Every class in Java or every class you write, it is as if you wrote **extends Object** after every class prototype.

- Since all classes descend from Object, there are a few notable methods that all classes inherit from Object. The first two inherited methods need to be overwritten by your class definition if they are to have any functionality. The last one is implemented generically
  - `public boolean equals( Object o)`
  - `public String toString()`
  - `public final native Class getClass()`

- To overwrite equals and toString you simple write our own version of those those two methods in your class. definition.

## Abstract Classes

derived classes will implement in their own special way.  A **Shape** class could describe behavior for various different kinds of shapes, and each derived class such as **Circle,** **Square** and **Rectangle** would provide specific different methods to implement the behaviors. 

**An Abstract class provides a base class that is suitable for derivation but cannot be directly instantiated.**

```java
` abstract class Shape { 	public abstract double area(); 	public abstract double perimeter(); } `
```

Notice now that our abstract class also has abstract methods declared inside. This means that any class designer than derives from Shape must also override area() and perimeter(). Not every abstract class need have all its methods be abstract but should have at least one. Those abstract methods must be over written with fully coded vesions in the extended class' source file.

```java
` Shape s = new Shape();  // ILLEGAL! Can't instantiate an abstract class `
```

```java

/* TestShapes.java defines an abstract Shape class then defines Circle and Square
   classes based on Shape.
*/

public class TestShapes
{
	public static void main(String args[])
	{
		Circle c = new Circle( 3.0 );
		System.out.println("Circle C has area: " + c.area() );
		System.out.println("Circle C has perimeter: " + c.perimeter() );
		Square s = new Square( 10.0 );
		System.out.println("Square S has area: " + s.area() );
		System.out.println("Square S has perimeter: " + s.perimeter() );
	} // END main
} // END TestShapes

// ----------------------------------------------------------------------------------
// We define our Shape, Circle & Square classes in the same file as our App
// ----------------------------------------------------------------------------------

// ..................................................................................
abstract class Shape
{
	public abstract double area();
	public abstract double perimeter();
}

//...................................................................................
class Circle extends Shape  // OK - we derive from Shape
{
	double radius;  // we added this data member to our abstract base defintion - OK
	Circle( double radius )
	{
		this.radius = radius;
	}
	public double area() //  REQURIED  override of abstract parent's area
	{
		return( Math.PI * radius*radius );
	}
	public double perimeter()  // REQUIRED override of  abstract parent's perimeter
	{
		return( 2.0 * Math.PI * radius );
	}
}

// ..................................................................................
class Square extends Shape  // OK - we derive from Shape
{
	private double side;  // we added this data member to our abstract base defintion - OK
	Square( double side )
	{
		this.side = side;
	}
	public double area() //  REQURIED  override of abstract parent's area
	{
		return( side * side );
	}
	public double perimeter()  // REQUIRED override of  abstract parent's perimeter
	{
		return( 4.0 * side );
	}
}
```

