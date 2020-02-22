---
layout: page
title: Class Relations and Inheritance
---

## Association:
- Represents a general relationship that describes an activity between two classes. 
- Usually represented as a data field (property) in the class.
- But the relationship is not **strong**, meaning the classes are not strongly dependent of each other.
	- (a Student exist even when the course does not) 
- Associations may exist between different instances of the same class.  
	- For example, an employee of type “software developer” can be the “project manager” of other software developer

## Aggregation and Composition:
- **Aggregation**: Ownership relationship between two classes
	- Ex. a patient has a phone
- **Composition**: Much stronger relationship where an object is *exclusively* owned by an aggregate object
	- The object does not exist independently of the aggregate object
	- Ex. a human has a brain

# Inheritance

- Many real-life objects are related in a **hierarchical** fashion
- Lower-levels of hierarchy **inherit** characteristics of the upper levels
- Classification of objects generate different levels of **abstraction** (classes)

## Class Hierarchy/Taxonomy:
- Breaking classes down into more specific and specific classes 
- Abstract --> Specific
- Ex. Vehicle --> Motor Vehicle --> Car --> Luxury Car --> Etc.
	- ***Note*** singular naming of classes not plural. IMPORTANT
- These hierarchies are always acyclic, meaning they only go one way (down)
- The topmost class of the tree is the **root class**
	- The root class for *all* classes is called the **Object** class

### Object Root Class:
- Provides the following capabilities to all Java objects:
	- Event Handling
	- Cloning
	- Finalization
	- Equality checking
	- Runtime error handling

### Inheritance Terminology:
- Root class 
	- class at the top of the hierarchy tree.
- Derived (child) class
	- a class that inherits characteristics of another class.  Also called “subclass”.
- Base (parent) class
	- a class from which characteristics and behaviors are inherited by other classes. 
	- Also called “superclass”

## Extending Classes:
- No special coding is required to designate a base class (superclass):
	- `public class Vehicle {...}`
- A derived class (subclass) must specifically declare the base class from which it is derived:
	- `public class MotorVehicle extends Vehicle {...}`
	- The MotorVehicle class *inherits* all the properties and methods from the Vehicle class
	- Objects of extended classes also inherit broader class properties

## Inheritance and Constructors:
- Constructors are not inherited
- If superclass have a default constructor, then no special consideration is needed in the subclass
- If superclass has a constructor, subclass **MUST** call it by:

```java
public class Person{
	String name;
	public Person(String name){
		this.name = name;
	}
}
public class Student extends Person{
	public Student(String name){
		super(name);
	}
}
public static void main(String[] args) {
	Student me = new Student("Zach");
}
```
- The keyword `super` refers to the class immediately above it (class it extends from)
	- ***NOTE:*** Must be called in the first line of the constructor
	- If there are no parameter to pass to superclass constructor, the super call can be omitted 

- In the above chunk of code, the Student class constructor calls the Person class constructor using `super` and follows it with a parameter name, which is a parameter for an object of the student class.
	- This would set the String name to Zach.

## Inheritance and Visibility:
- Private components of a class (attributes or methods) are ONLY accessible from the same class
	- So a Student object can not access his/her own name!! (unless they use the get method)
- Private properties and methods of a superclass cannot be accessed by a subclass
- If you need a subclass to access private members of the superclass, you need to change their access level to protected
	- **NOTE:** Protected means it can only be accessed by anything within the same package

## Method Overriding:
- Not to be confused with method overloading!
- When a member of a derived class has the same name as a member of a base class the derived class member is said to override the base class member.
- Simple Explanation:
	- Say a superclass Person has a generic move method for people
	- But we have a subclass called handicapped that moves differently
	- So, we create a new move method in the handicapped class with the exact same signature, but a different movement system
	- When an object of the handicapped class is called and the move method is used, the subclass handicapped overrides the person superclass
- Reference `super` can be used to explicitly refer to methods as implemented in the superclass
	- `super.move()` references move from the person superclass

### Override Directive:
- `@Override` directive asks the compiler to make sure that the parent class (superclass) actually has the method that you are attempting to override

```java
@Override
public void deposit(double amount){
	super.balance += amount;
	super.balance *= 0.01;
}
```

### Overriding toString():
- Class Object, the superclass of all classes, has methods we can override. For example the method
	- `String toString()`
- toString() is originally implemented to return a String containing the memory address of the object and the name of the class it belongs to
- toString() is automatically called when we want to print an object
	- `Person me = new Person("Eric");`
    - `System.out.println(me);`

- Now, lets override toString():

```java
public class Person{
    private String name;
    
    public Person(String name){
        this.name = name;
    }
        
    
    @Override
    public String toString(){
        return name;
    }
}
```
- Now, when we do `System.out.println(me);`, it will return name rather than the memory location of me

## Abstract Classes
- A base class can be declared with the keyword abstract
	- `abstract class Account {...}`
- Abstract classes cannot be instantiated. The following statement will generate an error if Account class is declared as abstract. 
	- `Account account = new Account();`
- Used to set a common root for a hierachy of classes
- Used to implement a set of methods inherited by the subclasses and save coding
- An abstract class can have abstract methods

## Final Classes
- A class can be declared with the keyword final
	- `final class Account {...}`
- A final class cannot be extended – no other class can inherit from it






