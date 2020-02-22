---
layout: page
title: Matrices
---

- A 2D array is really just a 1 dimensional array of arrays
- `int matrix[][];`
  - Here is what gets created in memory 
  - `matrix: [null] // ref var allocated with a null in it`
  - The reference variable indicates it’s a ref var for a 2D array by having a double set of brackets `[] []` in its declaration. 
    - Note that the above declaration of a ref var does not create any array yet.
- `matrix = new int[5][3];`
  - Now we have actually created a 5 row by 3 col array of int. 
  - The address of where that array lives gets assigned into the ref var.

- We usually visualize the array as just the grid part but in fact a 2D array is an array of arrays. Each row of the array is itself a 1D array. You could also say a 2D array is an array of references to 1D arrays 

## Properties of Matrices

\*\*Referring to the matrix shown above\*\*

- `matrix.length` is 5
- `matrix[0]` is the ref to the first array.
- `matrix[0].length` is 3
- To find out how many rows in the entire matrix use `matrix.length`
- To find the length of a specific row use `matrix[row].length`

- To access individual elements of the matrix use this syntax:
  - `matrix[3][2] = 7` —> puts a 7 in array 3, element 2



- Rather than plinking individual values into a matrix with hardcoded indices in solitary assignment statements, arrays and matrices are generally initialized using loops.

- Use `matrix.length` to produce the number of rows. Use `matrix[row].length` to produce the number of columns in that row:

  ```java
  int[][] matrix = new int[5][3];
  
  for (int row=0 ; row < matrix.length ; row++ )
  	for (int col = 0 ; col < matrix[row].length ; col++)
  		matrix[row][col] = row+col;
  ```

  *Outputs this:*

  | 0    | 1    | 2    |
  | ---- | ---- | ---- |
  | 1    | 2    | 3    |
  | 2    | 3    | 4    |
  | 3    | 4    | 5    |
  | 4    | 5    | 6    |

  - Each element is the sum of its row value and its column value

    - ==NOTE==: Rows and columns both start at 0

      

- Figure out the code to produce this output:

  | 0    |      |      |
  | ---- | ---- | ---- |
  |      | 1    |      |
  |      |      | 2    |

  ```java
  int[][] matrix = new int[3][3];
  
  for (int row=0 ; row < matrix.length ; row++ )
  	for (int col = 0 ; col < matrix[row].length ; col++)
  		if(row==col)
          	matrix[row][col] = row;
  ```



==Traversal Pattern:==

- Visits every cell in the grid

```java
for (int row=0 ; row < grid.length ; row++ )
	for (int col = 0 ; col < grid[row].length ; col++)
        grid[row][col] = something;
```

## The Maze Puzzle

### Version 1: Simple

- Try to escape a grid maze where only some elements are safe to traverse on

| x    | x    | x            | x     | x    | x    | x    |
| ---- | ---- | ------------ | ----- | ---- | ---- | ---- |
| x    |      | **<u>1</u>** |       |      |      | x    |
| x    |      |              | 1     |      |      | x    |
| x    |      |              |       | 1    |      | x    |
| x    |      |              |       |      | 1    | x    |
| x    |      |              |       | 1    |      | x    |
| x    | x    | x            | ==1== | x    | x    | x    |

- In this example, you start at R1, C2
- Can only move one step at a time
- Can only move to spaces with a 1 in them

```java
while(not on edge of swamp) //checks this if row or column is equal to 0 or length-1
    if(North is in bounds && North is a 1) //coord of North is r-1,c
        change value at r,c to 2 to indicate youve already been there
        change r,c to coordinates of North
    else if(NE is in bounds && NE is a 1) //coord of NE is r-1,c+1
        change value at r,c to 2 to indicate youve already been there
        change r,c to coordinates of NE
    else if for every other cardinal direction
	else
		break; //dont output anything if no escape path
```

- Problem with this method is that it doesn't account for retracing your steps if you hit a dead end or finding multiple paths

- ==Project requires you to output all the coordinates for every possible path out of the maze.== 

### Version 2: Introducing Dead Ends

```java
10 2 3 
0 0 0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0 1 0
0 0 0 1 0 0 0 1 0 0
0 0 0 1 0 1 1 0 0 0
0 0 1 0 1 0 0 0 0 0
0 1 0 0 1 0 0 0 0 0
1 0 0 0 1 0 0 0 0 0
0 0 0 1 0 1 0 0 0 0
0 0 1 0 0 0 1 0 0 0
0 0 0 0 0 0 0 0 0 0
```

- Now that there isn't only one clear path, we have to account for when the program hits a dead end and has to go back to the last crossroad

- This time, DONT make them `else if` statements, make them just `if` statements. Have the program try every direction and, for every direction that it can move to, recurse the method and keep following a path until it either finds an escape and prints that out, or hits a dead end. In either case, it will stop recursing and look for a different path and do the same thing again. 

```java
public static void dfs(int r, int c, String path, int[][] swamp) //path is an empty string
//can also delcare swamp as a global variable above main instead of passing it in the method
{
    path += parameter coordinates [r,c] ex. [2,3];
    if onEdge(r, c) //method that checks if the coordinates are on the edge of the matrix
    {
        System.out.println(path);
        return;
    }
    if swamp[r-1][c] is a 1 //north case
        mark current r,c as 2 //shows weve been there before
        dfs(r-1, c, path, swamp) //(dont actually pass swamp, make it global))
        unmark [r][c] back to 1 so it can use that path in another recursion
            
    if (NE) //fill in the same series of commands for every direction
    
    else //if no other moves are available, just return
        return;
}
```

