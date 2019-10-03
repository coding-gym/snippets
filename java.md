---
title: "Java"
---

## Premise

The needed imports should be already provided, in any case be sure to include:

```java
import java.io.*; // for BufferedWriter
import java.util.*; // for Scanner
```





## Reading values

For reading we can use the `java.util.Scanner` class. We can create it in the `main` method. 
Remember to close it at the end.

```java
public static void main(String[] args){
    Scanner scanner = new Scanner(System.in);
    //data reading code
    scanner.close();
}
```

We can use this class to read full lines or single values

```java
String s = scanner.nextLine();
int i = scanner.nextInt();
double d = scanner.nextDouble();
byte b = scanner.nextByte();
```

## Reading an array of N elements

The first line contains `N`, the number of elements.

The next line contains `N` space-separated integers.

We can read data either in an array or a list.

Read to array:
```java
int lenght = scanner.nextInt();
int[] arr = new int[lenght];
for (int i= 0; i < lenght; i++){
    arr[i] = scanner.nextInt();
}
```

Read to List:
```java
scanner.nextLine(); //Skip the first line, we do not need length info.
List list = new ArrayList<Integer>();
while (scanner.hasNextInt()){
    list.add(scanner.nextInt());
}
```

## Output

To print data to output we can use the `java.io.bufferedWriter` class

```java
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));
        bufferedWriter.write(String.valueOf(result));
        bufferedWriter.newLine();
        bufferedWriter.close();
```

## Full snippet

Full snippet to read a single line and print a result.

```java
import java.io.BufferedWriter;
import java.io.FileWriter;
import java.util.Scanner;

public class Solution {


    private static String doStuff(String param){
        //Do your things here!
        return  param;
    }

    public static void main(String[] args) throws Exception {
        Scanner scanner = new Scanner("my test string");
        String param = scanner.nextLine();

        String result = doStuff(param);

        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));
        bufferedWriter.write(String.valueOf(result));
        bufferedWriter.newLine();
        bufferedWriter.close();

        scanner.close();
    }
    
}
```



