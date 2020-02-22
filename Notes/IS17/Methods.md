---
layout: page
title: Methods
---

- Methods are like small programs within programs
- Receives input data and outputs other data based on the instructions within the method

## Method Signature:

```java
Public static int addNumbers(int num1, int num2)
```

*Return type: int*

- what type of data you want the method to output


*Method name: addNumbers*

- the name of the method that you reference elsewhere in the program


*Parameters: int num1 and int num2*

- The variables involved in the method  

- Inside the method, it does some specified function and always ends with `return variable`; (some desired result variable)
- Methods can only work with variables assigned within the method. It doesn’t know that variables outside the function even exist

## Void Methods:
- If you don’t want your method to return any value, you can use void instead of a normal return type
- Doing this omits the need for a return statement

```java
public static void greet(String name) {
   System.out.println("Hi " + name + ", how are you today ?");
}
```

