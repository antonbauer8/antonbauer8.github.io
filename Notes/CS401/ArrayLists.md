---
layout: page
title: ArrayLists
---

- A box containing just an object of type T pointing to an array, but also contains a ton of methods 
  - The raw data of an arraylist is a *private* array, meaning that you do not have direct access to the data in the arraylist, you can only use the predefined public methods for it
- ***Cannot*** make an arraylist of primitives (int, float, bool, etc.)
- `ArrayList<String> wordList = new ArrayList<String>();`

## ArrayList Methods (public)

- `.add` - adds an item to the arraylist
  - `wordList.add("foo");`
- `.get` - returns the value at a given index
  - `wordList.get(i)`

## Project 4

- For every word in jumbles.txt, find every permutation in dictionary.txt and list them out sorted left to right lexically like so:

  - Sopt opst post pots spot stop tops

  | jumbles.txt | dictionary.txt |
  | ----------- | -------------- |
  | sopt        | post           |
  |             | pots           |
  |             | spot           |
  |             | stop           |
  |             | tops           |
  |             | opts           |

- Read dictionary into arraylist
- Read jumbles into arraylist
- Test for equivalence NOT `.equals`

  - Equivalence means a permutation of: contains same letters AND same number of letters

- ***==DO NOT DO THIS==***

  - Generate every permutation of the jumbled word and do an equals test against the entire dictionary for each permutation

- ***==DO THIS==***

  - Convert every word in dictionary.txt and jumbled.txt to its "canonical" (sorted alphabetically) form

    - Create a new arraylist of canonicized dictionary words and one of canonicized jumbled words

  - Then, you'll only ever have to do one `.equals()` test for every string in dictionary to the jumbled word

  - **How to return a string that is a letter sorted copy of a given string:**

    ```java
    String toCanonical(String s)
    {
        char[] letters = s.toCharArray(); //built in string method
        Arrays.sort(letters);
        return new String(letters);
    }
    ```

## Enhanced For Loop

```java
for(String s : wordList)
	print(s + " " + toCanonical(s));
```

- Indexes through every string (assigned as s) in the arraylist of strings and does the command you write in the for loop
  - For every string in the arraylist, it prints the string s and its alphabetically sorted counterpart

## Jumbles Project Strategy

