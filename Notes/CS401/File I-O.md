---
layout: page
title: File I/O
---

### Reading a text file using BufferedReader

- use **BufferedReader** to read a text file line by line.

- use .ready() in the while test. Don't test for EOF condition.

- use .readLine() to read the entire line into a String.

- Buffered Reader is more efficient (faster) than Scanner because it does not convert the Strings to number etc.

- On very large files you will see a significant speedup using BufferedReader over Scanner.

- ```java
  	BufferedReader infile = new BufferedReader( new FileReader(args[0]) );
    	while ( infile.ready() )
    	{
    		String line = infile.readLine();
    	}
    	infile.close();
  ```

  	### Reading a text file using Scanner
  	
- use **Scanner** to read individual tokens rather than the entire line.

- Scanner reads tokens from a file and converts them to numbers or other types exaclty as it does from the keyboard.

- use the same Scanner methods next(), nextDouble(), nextInt() etc just like you do for the keyboartd.

- Assume your input file looks like this:

  ```java
  hoffmant  3.141  1991  true
  janedoe 4.00  2010  false
  ```

  and you want to read these values from the file into variables in your program, you can do it as below if you are sure the values are formatted correctly.

  ```java
  Scanner infile = new Scanner (new File( args[0] ));
  while (infile.hasNext() )  // while there is something left in the file to read (we ASSUME the file is formatted correctly)
  {
  	String name = infile.next(); // grabs the next token treats as String
  	double gpa = infile.nextDouble();
  	double yrGrad = infile.nextInt();
  	boolean faculty = infile.nextBoolean();
  }
  infile.close();
  ```

------

### Writing a text using PrintWriter

- **Use PrintWriter** to write to a text file. Use ..print() and .println() just the way you write to the screen.

  ```java
  	PrintWriter outfile = new PrintWriter( new File(args[0]) );
  	int x = 235;
  	outfile.println("Hello World");
  	outfile.println("The value of x is: " + x );
  	outfile.close();
  ```

- **Use Scanner** to read values other than entire lines of text from a file. If the text file contains various types of data then use the Scanner just as you would to read from the keyboard, but instantiate the Scanner on a text file instead of the System.in device (keyboard). Assume your input file looks like this:

  ```java
  hoffmant  3.141  1991  true
  janedoe 4.00  2010  false
  ```

  and you want to read these values from the file into variables in your program.

  ```java
  Scanner infile = new Scanner (new File( args[0] ));
  while (infile.hasNext() )  // while there is something left in the file to read (we ASSUME the file is formatted correctly)
  {
  	String name = infile.next(); // grabs the next token and leaves it as a String
  	double gpa = infile.nextDouble(); // grabs the next token and converts to double
  	double yrGrad = infile.nextInt(); // grabs the next token and converts to int
  	boolean faculty = infile.nextBoolean(); // grabs the next token and converts to boolean
  }
  infile.close();
  ```