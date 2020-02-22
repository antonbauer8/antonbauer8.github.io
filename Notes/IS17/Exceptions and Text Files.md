---
layout: page
title: Exceptions and Text Files
---

## Exceptions:
- Exceptions are errors
- Exception handling: exceptions can be handled using Try/Catch blocks
- When an error occurs an Exception is thrown
- Exceptions are objects

### Exception Handling
- Some methods are known to be risky
	- Transform a number
	- Access a file
- Programmers make those methods to throw Exceptions when errors occur
- Risky methods can be handled by catching the Exceptions

### Try/Catch Method:
```java
public class ExceptionExample {
    public static void main(String[] args) {
        String str = "A";
        try{
            double number = Double.parseDouble(str);
        }catch(Exception e){
            System.out.println("Failed to convert the number!");
        }
    }
}
```
- When it passes through the try block and it works, it runs that code normally
- When it passes throguh the try block and fails, it goes to the catch block and prints an error message

## Using Text Files:
### Input/Output with text files
- We create input and output streams to and from our program
- We will use `FileReader` and `FileWriter` classes
- Use filters mounted in top of the streams to facilitate the string processing:
    - BufferedReader
    - BufferedWriter
- Imports:

```java
import java.io.FileReader;
import java.io.FileWriter;
import java.io.BufferedReader;
import java.io.BufferedWriter;
```

### Reading From a Text File:
```java
try {
    FileReader fr = new FileReader("data/phrases.txt"); //creates file reader fr for txt at path
    BufferedReader br = new BufferedReader(fr); //creates bufferedreader br for  file fr
    String line = br.readLine(); //reads first line from br and stores them in String line
    System.out.println(line);
    br.close(); //closes the bufferedreader
    fr.close(); //closes the filereader
} catch (IOException e) {
    System.out.println(e.getMessage());
}
```

### Writing To a Text File:
```java
try {
    FileWriter fw = new FileWriter("data/simpletext.txt"); //creates filewriter fw for txt at path
    BufferedWriter bw = new BufferedWriter(fw); //creates bufferedwriter bw for file fw
    bw.write("This is a text file"); //writes text to bw
    bw.write("\n"); //writes new line to bw
    bw.write("This is a the second line"); //writes second line to bw
    bw.close(); //closes bufferedwriter
    fw.close(); //closesfilewriter
} catch (IOException e) {
            System.out.println(e.getMessage());
}
```

### Reading all lines from a text file:
```java
try {
        FileReader fr = new FileReader(filename);  //creates filereader fr from path
        BufferedReader br = new BufferedReader(fr); //creates bufferedreader for file fr
        String line = null; //initially sets line to empty
        while ((line = br.readLine()) != null) { //checks that each line its reading isn't empty
            System.out.println(line); //prints each line until the line it reads is empty
        }
        br.close(); //closes bufferedreader
        fr.close(); //closes filereader
} catch (IOException e) {
            System.out.println(e.getMessage());
}
```

### Considerations when Dealing with Text Files:
- BufferedReader reads sequentially. You can not return previous lines
- You can always close the BufferedReader and open it again, or have 2 BufferedReader objects.
- There are other classes for reading and writing files in a more flexible way (example: RandomAccessFile)





