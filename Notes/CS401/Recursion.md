---
layout: page
title: Recursion
---

- A problem solving technique where an algorithm is defined in terms of itself
- A recursive method is a method that calls itself
- A recursive algorithm breaks down the input or the search space and applies the same logic to a smaller and smaller piece of the problem until the remaining piece is solvable without recursion.
- Sometimes called “divide and conquer”
- ***==ONLY USE RECURSION WHEN YOU CAN'T SOLVE IT WITH JUST A LOOP==***

## Recursion in Math

- Factorials:

  - n! = n * (n - 1)!

- ***ALSO*** make sure to always have a base case to stop the recursion from running, otherwise it would go on forever

  - The above definition has no base case (though it's assumed)

- ***Must ALSO*** always be getting closer to the base case with each recursion, otherwise it would be constatnly expanding

- Proper factorial definition: 

  - If n == 0, then n! is 1. Else, it's n * (n-1)

- Translated to java:

  ```java
  public static int fact (int n)
  {
      if(n==0)
          return 1;
      return n * fact(n-1);
  }
  ```

- Written as a loop instead:

  ```java
  int fact (int n)
  {
      int prod = 1;
      for(int i = 1; i <= n; i++)
          prod = prod * i;
      return prod;
  }
  ```

## Analysis

- In general, recursive algorithms are
  - more efficient
  - more readable (but occasionally quite the opposite!)
  - more “elegant”
- side effects
  - mismanagement of memory
  - “over head” costs

## Components

- Solution to the “base case” problem
  - for what values can we solve without another recursive call?’
- Reducing the input or the search space 
  - modify the value so it is closer to the base case
- The recursive call
  - Where do we make the recursive call?
  - What do we pass into that call? 

## How it Works

- When a method calls itself – it is just as if that method is calling some other method. It is just a coincidence that the method has the same name, args and code. A recursive method call creates an identical copy of the calling method and everything else behaves as usual.

- Think of the method as a rectangle containing that method’s code and data (*code is not actually stored in the call stack*), and recursion is just a layering or tiling of those rectangles with information passing to with each call and information returning from each call as the method finishes.

  

## The Call Stack

- The call stack is a pile of "actions" that the program has to complete before the program is finished executing
- The stack starts with the most fundamental actions (first calls the program, then the main method, etc) and builds up with more urgent ones
- The most recent method called is always put on the top of the stack and is pulled off first once it has completed

## Tracing Code

```java
void mystery (int n)
{
    if (n == 0)
        return;
    print(n % 10);
    mystery(n / 10);
}
```

If you call mystery(371): 

```java
If 371==0 return //---> FALSE
print(1);
mystery(37); //rounds down bc int
{
    If 37==0 return //---> FALSE
    print(7);
    mystery(3); //rounds down bc int
    {
        If 3==0 return //---> FALSE
        print(3);
        mystery(0); //rounds down bc int
        {
            if 0==0 return //---TRUE
        }
    }
}
// PRINTS 173 --> the input int printed backwards
```

==EXTRA CREDIT==

- Use recursion to return the product of two passed ints. Can't use the multiplication operator or any loops (obviously)

  ```java
  int mystery(int a, int b)
  {
      if(a==0) return b;
      return mystery(a-1, b-1);
  }
  // modify this code to make it multiply (this one adds the two ints)
  ```

  MY ANSWER:

  ```java
  static int mystery(int a, int b) 
      { 
          if (a < b)
              return mystery(b, a); 
        
          else if (b != 0) 
              return (a + mystery(a, b - 1)); 
        
          else
              return 0; 
      } 
  // This should work me thinkst
  ```

  1

==In-Class Exercise:==

- Write a recursive method to output a string in reverse, given the string and the index of the last character

  ```java
  //IN MAIN:
  System.out.println(rev("Hello", 4));
  
  //IN METHOD:
  void rev(String s, int i)
  {
      if(i<0) return;
      print(s.charAt(i));
      rev(s, i-1);
  }
  ```

==Recursive Palindrome Exercise==

- Write a recursive method to return a boolean if a passed string is a palindrome

  ```java
  //IN MAIN:
  System.out.println(isP("radar", 0, 4));
  
  //IN METHOD:
  boolean isP(String s, int lo, int hi)
  {
      if(lo>=hi) return true;
      if(s.charAt(lo) != s.charAt(hi)) return false; 
      return isP(s, lo+1, hi-1); //MUST return the recursive call if it's a non-void method
  }
  ```

==Recursive Sum of Digits Exercise==

```java
//IN MAIN
System.out.println(sumOfDigits(73248));

//IN METHOD
int sumOfDigits(int n)
{
    if(n==0) return 0;
    return(n%10 + sumOfDigits(n/10));
}
```

