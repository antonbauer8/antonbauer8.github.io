---
layout: page
title: Common Sorting Algorithms
---

## Bucket Sort

- Sort an array of positive integers {3,11,2,9,1,5}
- Find the maximum element of given array → in this example it is 11
- Create an array of size 12 (the size = value of maximum element + 1)
- Go through the input array and place integer 3 into a second array at index 3, integer 11 at index 11 and so on. 
- We will end up with a sorted list in the second array
- Problem with it is that it wastes a lot of space on empty array elements

## Bubble Sort

- Compares each item in the list with the item next to it, and swapping them if required
- The largest element “bubbles” to the top of the array
- The algorithm repeats this process until it makes a pass all the way through the list without swapping any items

## Selection Sort

- The algorithm works by selecting the smallest unsorted item and then swapping it with the item in the next position to be filled
- Look through the entire array for the smallest element
- Once you find it you swap it (the smallest element) with the first element of the array
- Look for the smallest element in the remaining array (an array without the first element) and swap it with the second element. 
- Look for the smallest element in the remaining array (an array without first and second elements) and swap it with the third element, and so on.


## Linear Search

- Searching a list that isn’t sorted requires a Linear Search 
- Linear Search requires to check the entire list (N accesses)
- Question: can the search stop once it finds the element it is looking for?
	- Maybe. No, if the list can have repeated values. Yes, if there's only one of each value.

## Binary Search

- Binary search (half-interval search) algorithm finds the position of a specified input value (the search "key") within a list sorted by key value.
- For binary search, the list should be arranged in ascending or descending order. 
- In each step, the algorithm compares the search key value with the key value of the middle element of the list. 
- If the keys match, then a matching element has been found and its index, or position, is returned. 
- If the search key is less than the middle element's key, then the algorithm repeats its action on the sub-list to the left of the middle element.
- If the search key is greater than the middle element's key, then the algorithm repeats its action on the sub-list to the right of the middle element.
- If the remaining list to be searched is empty, then the key cannot be found in the array and a special "not found" indication is returned.
- With a sorted list, a Binary Search has log2 N block accesses.
- Since the data is sorted, the rest of the table doesn’t need to be searched for duplicate values, once a higher value is found. 
- The performance increase is substantial.

