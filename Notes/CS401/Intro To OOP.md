---
layout: page
title: Intro to OOP
---

- The use of objects to combine variables and methods in a single unit of abstraction
- More concretely, OOP is the writing and use of classes
  - A class in Java is simply a definition of a data type where that description weds variables and methods which in turn manipulate those variables

## Classes

- contain the blueprint of how to build an object
- class files are written and defined by programmers

__Example:__

```java
public class Guitar{
    String color;
    int nStrings;
    boolean hasTremolo;
}

Car (brand, color, licensePlate, mileage)
public class Car{
    String brand;
    String color;
    String licensePlate;`
    double mileage;

}

Person (name, age, race, gender)
public class Person{
    String name;
    int age;
    String race;
    char gender;
}

Book (title, author, number of pages, editor, year of publishing)
public class Book{
    String title;
    String author;
    int numberOfPages;
    String editor;
    int yearOfPublishing;
}
```

_**- Make sure the class file name is exactly the same as the class name**_

### Unified Modeling Language(UML) Diagrams

-Used to describe object-oriented software

**UML Class diagram is for specifying classes**

- A rectangle, text centered, with the name of the class
- A rectangle, text top-left aligned with the list of properties
- Each property is specified as name : type

| Car           |        |
| ------------- | ------ |
| brand:        | String |
| color:        | String |
| licensePlate: | String |
| mileage:      | double |

*-Putting a (-) before the properties indicates that they're private, while (+) shows that they're public*

### Class Visibility

**Visibility** properties can be:

**public** – visible to other classes

**private** – visible only to their own class

**protected** - visible only to its own package

_**You generally want to make all of your classes private so no one else can access them**_

## Objects

-Objects are data structures together with their associated processing routines
-Objects exist only once the program is run

- Properties `//descriptions` *(characteristics, attributes, features)*
- Methods `//actions` *(fuctions, procedures, behaviors)*

### Object Instanciation

- Creation of objects

```java
Car myCar = new Car();
```

-The operator `new` is who allocate memory enough for storing a `new Car` object
-*Laymans terms:* creates a new object called `myCar` that uses the class `Car` as the structure to input data about `myCar`.

__EXAMPLE:__

```java
public class Guitar{
    String color;
    int nStrings;
    boolean hasTremolo;
    //This is this generic guitar class that is going ot be used to 
    //apply to other specific guitars
}

public class guitarTest
//general test class to test the Guitar class on a specific guitar
	public static public static void main(String[] args) {
		Guitar g1 = new Guitar();

		g1.color = "black";
		g1.nStrings = 6;
		g1.hasTremolo = false;

		Guitar g2 = new Guitar();

		g1.color = "brown";
		g1.nStrings = 8;
		g1.hasTremolo = true;


	}
```

- Classes are useful because it allows you to use multiple separate instances of variables that don't overwrite each other. The variables are specific to only the object it's applied to

## Object Methods

- Methods are also part of the class
- We can define methods that change and/or retrieve the value of the properties
- We define methods as public
  **-Now our methods are NOT going to be static**

```java
	public return-type methodName(parameters){
		...
	}
```

### Encapsulation

- One of the four fundamentals of OOP 
- Refers to data hiding
- Prevents unauthorized parties from direct access to object’s properties
- Getter and setter methods used to access private properties

### Get and set methods:

- Since private varaibles are inaccessible by other classes, we have to use set and get methods to make them accessible:

```java
public class Car {
	   private String brand;
	   private String color;
	   private String licensePlate;
	   private double mileage;

    public void setBrand(String newBrand){
        brand = newBrand;
    }

    public String getBrand(){
        return(brand);
    }
}

```

- The `setBrand` method takes some input string from another class that calls the setBrand method and sets it equal to the brand in the private class, essentially making it accessible to any other class whenever the call it. 
- The `getBrand` method does the same thing, except simply returns whatever the brand variable is, rather than setting that variable equal to something else.



