---
layout: page
title: Arrays
---

## Arrays

- **Arrays** are *sequential* lists of values of the same data type
- Items stored in arrays are called **elements**
- All elements stored in an array must have the ***same*** data type

### Declaring Arrays:
```java
    double[] values; //(Square brackets indicate an array) 
```

### Initializing Arrays:
```java    
    double[] values = new double[10]; 

    int[] numbers = new int[15];

    String[] names = new String[5];

```
- In the first example, `double[] values` declares that there is going to be a double array called values
- `new double[10]` initializes the double array with length 10
- When declaring number-based arrays without inputting values, the values in each element are defaulted to 0
	- Non-number-based arrays must have some data in it in order to be used

### Initializing Arrays with Values:
```java
    double[] values = {32, 54, 67.5, 29, 44.5, 100, 65}; 

    int[] numbers = {0, 1, 1, 2, 3, 5, 8, 13, 21};

    String[] names = {“John”, “Mary”, “Chris”, “Jane”, “Amanda”};
```

### Accessing Array Elements:

- Indexes in an array start at 0, like strings

```java
    int[] numbers = {0,  1,  1,  2,  3,  5,  8,  13,  21};
```

- To access the first element of this array:
	- `int firstElement = numbers[0];`

- To access the fifth element of this array:
	- `int fifthElement = numbers[4];`

### Changing Values of Array Elements:
```java
    int[] numbers = {0,  1,  1,  2,  3,  5,  8,  13,  21};
```

- To update the value of the first element of this array:
	- `numbers[0] = 10;`

- To update the value of the fifth element of this array:
	- `numbers[4] = 15;`

### Bound Errors:
- Occurs when you supply an invalid array index (when index is outside of array length)

### Array Length:
```java
double[] values = new double[10];
System.out.println(values.length);
```
- ***NOTE***: 
	- `.length` has no parenthesis, unlike when dealing with Strings
	- Length without parenthesis is a property, while length with is a method

### Looping through Arrays:
```java
int[] scores = { 10, 9, 7, 10, 5, 20, 74 };
for(int i = 0; i < scores.length; i++){
System.out.println(scores[i]);
}
```
- Prints each element in array scores

### Using Arrays with Methods:
- Arrays can occur as method arguments and return values.
- An array as a method argument

```java
public int addScores(int[] values){
int totalScore = 0;
for (int i = 0; i < values.length; i++){
    totalScore = totalScore + values[i];
}
return totalScore;
}
```
- Returns the int value totalScore
- Inputs the int array values as a parameter

To call the method:

```java
int[] scores = { 10, 9, 7, 10 };
int total = addScores(scores);
```

Returning an array:

```java
public int[] getScores(){
int[] scores = { 10, 9, 7, 10 };
return scores;
}
```
- Returns int array scores

### "Enhanced" For Loop:
- You can use the enhanced for loop to visit all elements of an array

```java
double[] values = { 23, 43, 67, 6.3, 56 };
double total = 0;

for (double element : values) {
	total = total + element;
}
```
- The loop body is executed for each element in the array values.
- Read the loop as for each element in values.
- `double element` is created to hold an element of an array. Must be of the same data type as the array
- `values` is the name of the array referenced

#### Notes about the Enhanced Loop:
- Not suitable for all array algorithms.
- Does not allow you to modify the contents of an array.
- The following loop does not fill an array with zeros:

```java
for (double element : values)
{
   element = 0;     // ERROR: this assignment 
            	   //does not modify array elements
}
```

## Array Lists:
- `import java.util.ArrayList;`
- An ArrayList object can grow and shrink as needed
- ArrayList class supplies methods for many common tasks, such as inserting and removing elements
- An array list expands to hold as many elements as needed
- **Array lists cannot work with primitive data types. Only objects**
- Array lists can also work with multiple types of data

### Declaring Array Lists:
- To declare an array list of strings:

```java
ArrayList<String> names = new ArrayList<String>();
```

- To declare an array list of Dice:

```java
ArrayList<Dice> dices = new ArrayList<Dice>();
```

### Using Array Lists:
- `ArrayList<String>` is first constructed, it has size 0
- Use the `add` method to add an object to the end of the array list: 

```java
ArrayList<String> names = new ArrayList<String>();
names.add("Emily"); // Now names has size 1 and element "Emily”
names.add("Bob"); // Now names has size 2 and elements "Emily", "Bob”
names.add("Cindy"); // names has size 3 and elements "Emily", "Bob", and "Cindy"
```

#### Get Method
- To obtain an array list element, use the `get` method
	- Index starts at 0
- To retrieve the name with index 2:

```java
String name = names.get(2); // gets the 3rd element 
```

#### Set Method
- Setting an ArrayList Element to a New Value:

```java
names.set(2, "Carolyn");
```

#### Add Method
- How to add a new element in the middle:

```java
names.add(1, "Ann");
```
- This statement adds a new element at position 1 and moves all elements with index 1 or larger by one position.

#### Remove Method:
- removes the element at a given position
- moves all elements after the removed element down by one position
- and reduces the size of the array list by 1.

```java
names.remove(1);
```

### Enhanced for Loop with Array Lists:
```java
ArrayList<String> names = new ArrayList<String>();
names.add("Emily"); 
names.add("Bob"); 
names.add("Cindy"); 
        
for (String name : names) {
   System.out.println(name);
}
```

### Copying Array Lists:
- To make a copy of an array list, construct the copy and pass the original list into the constructor

```java
ArrayList<String> names = new ArrayList<String>();
        
names.add("Emily");
names.add("Bob");
names.add("Cindy");
        
ArrayList<String> newNames = new ArrayList<String>(names);
```

## Array Lists vs. Arrays
- For most programming tasks, array lists are easier to use than arrays.
	- ArrayList can grow and shrink.
	- Arrays have a nicer syntax.
- Recommendations
	- If the size of a collection never changes, use an array.
	- If you collect a long sequence of primitive type values and you are concerned about efficiency, use an array.
	- Otherwise, use an array list.

