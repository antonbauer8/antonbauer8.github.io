---
layout: page
title: If, Else, and Loops
---

## If/Else Statements:
- Runs something only if a certain condition is met

```java
if (condition true or false){
   // executed when condition is true
}else{
   // executed when condition is false
}
```

- Else runs if the if statement is false
- Else if allows you to check for another condition only if the previous if statement wasn't met.


## While loops:
- Runs some set of statements as long as so long as the parameter is true. Once the parameter is false, it breaks the loop.

```java
	int I = 0;
	While (i<10){
		System.out.println(i);
		i++;
	//	Prints numbers 0-9
	}
```

## For Loops:
- Use a for loop when a variable runs from a starting value to an ending value with a constant increment or decrement

```
	for (initialization; condition; update){
		//statement
	}
```

- The initialization is executed once, before the loop is entered
- The condition is checked before each iteration
- The update is executed after each iteration
- Any variable declared in a loop only exists within that loop (same with if/else statements)

## String Processing Using Loops:
- Characters are actually just representations of two byte integers
- You can compare characters to other characters like you would with integers 
	- Just compares the int values of the characters

```java
public static String keepLettersOnly(String s){
	String r = "";
	for(int i=0;i<s.length();i++){
		char a = s.charAt(i);
		if((a >= 'a' && a <= 'z') || (a >= 'A' && a <= 'Z')){
			r = r + a;
		}
	}
	return r;
}
```
- Keeps only the letters by running through each character of the string and checking if that character's int value is between the values of a and z.

## Do While Loops:
- Executes some set of actions first, then checks for some condition to see if it should repeat that action

```java
Do{
Some set of actions
 
} while(some condition);
```
- Does the actions in the do loop first, then checks the while condition and, if it is met, it will run the do loop again

```java
public static void main(String[] args) {
	int number = 0;
	int theSum = 0;
	do{
		theSum += number;
		number = Integer.parseInt(
		JOptionPane.showInputDialog("Enter the next number (-1 to exit)"));
	}while(number != -1);
	
	JOptionPane.showMessageDialog(null, "The sum is " + theSum);
}
```

 

