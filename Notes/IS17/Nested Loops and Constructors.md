---
layout: page
title: Nested Loops and Constructors
---

## Nested Loops:
- Loops inside of loops

```java
public static void main(String[] args) {
	for(int i=1;i<4;i++){

		for(int j=1;j<4;j++){
			
			System.out.println(i+" x "+j+" = "+(i*j));
		}
	}
}

```

## Class Constructors:
- The very first method called in an object
***but a constructor is not a method***
- Used to initialize the state of the object
	- Sets initial values to the properties
- Constrcutors must have the **exact** same name as the class
- Constructors basically allow you to override the value of a variable in a class when a parameter is given when the class is called

```Dice myDice = new Dice() <-- This is a *constructor*```


### Default constructors:
- If we dont explicitly create a constructor, the default constructor is automatically created
- Default constructor has no parameter

```Dice myDice = new Dice();```

- When a constructor is created, the default constructor is disabled

Example

```java
public class Dice {
	private int sides;
	
	public Dice(){ 
		sides = 6;
	//THIS IS A DEFAULT CONSTRUCTOR. It initializes 
	//the state of sides without any parameter
	}
	
	public int roll(int times){
		int score = 
					(int)Math.round(sides*Math.random() + 1);
		return score;
	}
}
```

### Defining your own constructors:
- To pass initial values for properties as parameters in the constructor
- To implement checking or constraints necessary for avoiding the "impossible object" problem
- We can define parameters in the constructor:

```java
public Dice(int s){
	sides = s;
}
```
- This allows you to input a desired number of sides (`int s`) that overrides the original number of sides

## Overloading:
### Constructor overloading
- A constuctor is overloaded when there are multiple constructors with the same name
- A class can have multiple constructors with the exact same name
- They are distinguished by the parameters called in the constructor

```java
	public Dice(int s){
		if(s<2) s=6;
		sides = s;
	}

	public Dice(){
		sides = 6;
	}
```
- The first constructor requires an `int s` parameter, while the second requires no parameters
- Ex. If the class is called and it inputs an integer in its parameter, the program will run the first constructor

### Method overloading
- Methods can be also overload
- 2 or more methods with the same name but different parameters

## Rules about overloading
- Overloaded methods are differentiated by the number, the type, and the order of the arguments passed. 
- You **CANNOT** declare more than one method/constructor with the same name and the same number and type of parameters, because the compiler cannot tell them apart.
- The compiler does not consider return type when differentiating methods/constructors, so you cannot declare two methods/constructors with the same signature even if they have a different return type.

## *This* Reference
- The *`This`* code references the object/class itself
Example:

```java
public class Dice {
	private int sides;
	
	public Dice(int sides){
		if(sides<2) sides=6;
		this.sides = sides;
	}

	public Dice(){
		this(6);
	}
	
	public int roll(int times){
		//some code here
	}
}
```
- In the first constructor, `this.sides` refers to the int sides initialized at this beginning of the class, not the sides parameter in the constructor.
- In the second constructor, `this(6)` plugs in 6 as a parameter in the Dice class, which would plug 6 into the first constructor.
