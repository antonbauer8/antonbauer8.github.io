---
layout: page
title: Arrays
---

- An array is a collection of values of the same type stored consecutively in memory.

- `int arr[] = new int[5];`

  - This declaration has 2 parts: 

    - The stuff on the right of the assignment 
    - the stuff on the left

  - Let’s start with the part on the right

    - keyword **new** has two properties

      1) allocates a chunk of memory big enough for 5 ints

      2) brings back the **address** of that chunk of memory(or throw Exception if out of memory)

  - The **int arr[]** part creates a reference variable namedarr. This ref variable contains the address of the first cell in the memory chunk. **arr** contains the **address** of the [0]’th cell. That why there is an arrow coming out of arr pointing at the [0] cell. Thus **arr points to** or **references** the beginning of the array

## Array Terminology

- **arr** is the reference variablex
- The chunk of memory is the **object**
- **References** point to objects.
- Putting values into the array is easy
- Use .length to determine how many cells the array has

```java
for (int i=0 ; i<arr.length ; ++i )
	arr[i] = i*2;
```

​	now  arr: [-]---> [0] [2] [4] [6] [8]

### The `.length` Property

- Once an array has been dimensioned you can always go back and ask the array how many cells of capacity it has.

```java
int arr[] = new int[5];
println( “arr has “ + arr.length + “ cells” );
// arr.length produces the number 5
```

- Another example using a LOOP:

```java
int arr[] = new int[5];
int count=0;
while (count< arr.length )
{
	arr[count ++] = count *2;
}
// this little loop iterates through each index in the array and sets the value of it to twice the index
```

## Rules for Arrays

1) When you declare an array you should declare an int named count or such to track how many values you have put into the array

2) initialize count to 0 and then use count to represent two things:

- **the number of values** you have put into the array so far
- **the index position** of where the next value should be stored

### Passing Arrays

- When you pass an array, you must pass it to a method that is written to receive and array.

```java
public static void main( String[] args )
{	int arrCnt = 0;
	int arr[] = new int[5]
	for (arrCnt=0 ; arrCnt<arr.length ; arrCnt++)
		arr[arrCnt] = arrCnt * 2;
	printArray( arr, arrCnt);
}
private static void printArray( int[] array, int cnt )
{
	for (int i=0 ; i < cnt ; ++i
		System.out.println( array[i] );
	System.out.println();
}
```

- When you pass an array you are just passing a copy of the address where the array starts. You are not passing a copy of the data values.
- It would be very memory inefficient to make a copy of the actual array and send that to the method.
- It is much more efficient to just pass a copy of the address (reference)

### Filling an Array from a File

```java
int[] arr = new int[10];
int arrCnt= 0;
while ( infile.hasNextInt() )
	arr[arrCnt++] = infile.nextInt();
printArray( arr, arrCnt );
```

### What to do when an Array is Full

- Once an array has been defined, its .length (capacity) cannot be changed.
- We know the value stored at each individual cell is a variable and can easily be reassigned a new value with a simple statement like `arr[i] = value`, but the .length (physical capacity or number of cells) cannot be changed.
  - This creates a problem if the file you are reading contains more values than the array was dimensioned to hold. You might think you can get around that problem by choosing a huge integer to dimension your array with: `int[] arr = new int[Integer.MAX_VALUE];`
    - It shouldn't require a lot of thought to see why this a very bad workaround. Integer.MAX_VALUE is 2,147,483,647 (2 Billion!). If you start dimensioning arrays to this size you quickly run out of memory or stretch the limits of virtual memory. It's just wasteful at best.
- There is a more general solution and it simple and fairly efficient. A method that accepts a full array and returns an array twice as long that contains all the elements from the original array.

***Create upsize method:***

```java
static int[] upSizeArr( int[] fullArr )
	{
		int[] newArr = new int[fullArr.length * 2];
		for(int i=0; i<fullArr.length; i++)
		{
			newArr[i] = fullArr[i];
		}
		return newArr;
	}
```

- when looping through adding items to an array, always check that the array has space before adding that item:

  ```java
  if(count == yourArray.length)
      yourArray = upSize(yourArray);
  ```

