---
layout: page
title: Sorting and Searching
---

**Lexical Sorting** - Sorting strings by which word would appear later in a dictionary

- What it references when you compare strings, like `if(stringA > stringB)`
  - In this case, the 'greater' string is one which would come later in the dicitonary
  - If lengths differ, the longer word comes out on top
  - If lengths are the same, whichever starts with the letter further down the alphabet

### `insertInOrder()` Method

- Method Structure: `insertInOrder(array, key)`
  - Passes an array and an object/value that you want to insert into the array in the correct spot in order

## Binary Search Algorithm

- **Array must be sorted first!!!**

- Then loops through cutting the array in half and checking if its too high or too low, then takes the right half accordingly and starts the loop over

- Computation speed: O(Log<sub>2</sub>N)

  ```java
  While (lo<=hi)
  	Guess = (lo+hi)/2 *with truncation* - rounds down //REWRITE THIS WHERE IT DOESNT OVERFLOW. Dont do lo/2+hi/2
  	If guess is too low, move low to guess + 1
      Else if guess is too high, move high to guess - 1
      Else return guess
      
  If nothing gets returned, index of the number wasnt found. The index where a not found element SHOULD BE belongs at lo+1. Return the index of where it belongs plus one and negated. Then, when the method is called, check if the returned value is a negative. If so, remove the negative and subtract by 1.
  ```

- It's a versatile algorithm, as if the number you're looking for exists, it will return the index of that number. If the number *doesn't* exist, it will return the index of where that number *should* be

