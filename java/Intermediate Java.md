# Input and Output

## Input and Output

### Introduction
In this lesson, we will learn about some of the built-in [classes](https://www.codecademy.com/resources/docs/java/classes) that are useful for completing these tasks, specifically, reading and writing text to a file.

|Class|Definition|
|---|---|
|[`System.out`](https://docs.oracle.com/javase/9/docs/api/java/lang/System.html#out)|A class that holds functions to display out in a terminal or command prompt application.|
|[`Scanner`](https://www.codecademy.com/courses/learn-intermediate-java/lessons/java-input-and-output/exercises/link)|A class used to read input passed into a Java program.|
|[`FileWriter`](https://docs.oracle.com/javase/9/docs/api/java/io/FileWriter.html)|A class that holds functions to convert byte data into readable text files.|
|[`FileReader`](https://docs.oracle.com/javase/9/docs/api/java/io/FileReader.html)|A class that has functions that convert input from files to byte data for a Java program to use.|

### Review: Printing with System.out
- [`System`](https://docs.oracle.com/javase/9/docs/api/java/lang/System.html) is a class in the `lang` package that part of every Java install. It contains several properties and [methods](https://www.codecademy.com/resources/docs/java/methods) to interface with various high-level aspects of the computer environment.
- `out` is an instance of a `PrintStream`, included as part of the `System` class, that is already open and provides [output](https://www.codecademy.com/resources/docs/java/output) to the user’s default console or display.

`System.out.print()` prints into the same line when a program is running.

`System.out.println()` prints output to a new line.

`System.out.printf()` allows us to output strings that are formatted in the code using [_format specifiers_](https://docs.oracle.com/javase/9/docs/api/java/util/Formatter.html#syntax). Format specifiers begin with the ‘%’ sign, followed by the type of variable we want to print. Some examples include `%s` for a string,`%c` for a character, and `%d` for an integer.

Notice that variables in our print statement are stated in the order that the format specifiers appear.

```java
String world = "World";
int day = 1;
System.out.printf("Hello %s! Today is Day: %d of your Intermediate Java course!", world, day); 
```

### The Scanner Class
Just like `System`, the `Scanner` class is predefined and built into Java for your use. It’s used to read [user input](https://www.codecademy.com/resources/docs/java/user-input) in a Java program. When we declare a scanner we need to tell it what type of input we are going to be scanning, this gets passed into the constructor we initialize it.

The Scanner class comes with Java in the package `java.util`, therefore before we can use the Scanner class in our own code we must import it from that package, which you can do using the following:

```java
import java.util.Scanner;
```

**Note:** Everything that is contained in the [`java.lang`](https://docs.oracle.com/javase/9/docs/api/java/lang/package-summary.html) package is automatically imported into every Java program. Every Java SDK installation comes with everything in the `java.base` module, a [collection](https://www.codecademy.com/resources/docs/java/collection) of resources that make Java what it is. The other packages contained in [`java.base`](https://docs.oracle.com/javase/9/docs/api/java.base-summary.html) such as [`java.util`](https://docs.oracle.com/javase/9/docs/api/java/util/package-summary.html) and [`java.io`](https://docs.oracle.com/javase/9/docs/api/java/io/package-summary.html) provide helper functionality that isn’t necessary to every program, but is used in special circumstances, such as when we need a `Scanner`. We access these extra [classes](https://www.codecademy.com/resources/docs/java/classes) by importing them into out program, this tells the [compiler](https://www.codecademy.com/resources/docs/java/compiler) to go to those packages and make sure the resource is available for use when we build our programs. You may ask why we don’t include everything into all Java programs? If we did that, our programs would be huge when we compiled them, including many many [files](https://www.codecademy.com/resources/docs/java/files) we will never use. Importing specific classes from these packages keeps our software lean and efficient.

Now that we have access to the Scanner class, let’s begin by declaring the `Scanner` class as an instance variable that we will call `input`:

```java
Scanner input = new Scanner(System.in);
```

Notice how we have placed `System.in` within the brackets in our declaration. This is what will allow our program to read user input from the console. Similar to how the `out` property of System was a `PrintStream`, the `in` property is an instance of an `InputStream`, read more about it [here](https://docs.oracle.com/javase/9/docs/api/java/lang/System.html#in).

The `Scanner` class can also read input from a file.

### Scanner Functionality
The first thing to know about the Scanner class is that it breaks up its input using a defined delimiter and by default that delimiter is set to whitespace. This means every time there is a space or a new line in our input, the Scanner will recognize it as a new piece of the input, in fact, it can do its best to search the input for the specific type of information you are looking for, whether that be an integer, a word, or a character.

The next most important piece of the Scanner class is that is blocking, that means that if the Scanner is waiting on [user input](https://www.codecademy.com/resources/docs/java/user-input) from the terminal, it will block continued execution of the program until it gets its input.

The list below outlines some (but not all) the different [methods](https://www.codecademy.com/resources/docs/java/methods) associated with the Scanner class that allow us to read the next piece of information we are looking for.

|Variable|Code|
|---|---|
|String|`String myString = input.next();`|
|Int|`int num = input.nextInt();`|
|Double|`double numDouble = input.nextDouble();`|
|Byte|`byte numByte = input.nextByte();`|
|Boolean|`boolean isTrue = input.nextBoolean();`|
|Long|`long numLong = input.nextLong();`|
|Short|`short numShort = input.nextShort();`|

The `Scanner` class has several additional methods that help support data validation and control flow, we can use these to make sure that we don’t try to process data that doesn’t exist and thereby run into [errors](https://www.codecademy.com/resources/docs/java/errors) in our program, also known as exceptions.

|Code|Function|
|---|---|
|`input.hasNext()`|This function returns a boolean that indicates if there is another token left to process|
|`input.hasNextLine()`|This function returns a boolean that indicates if there is another line in the input of the defined scanner.|
|`input.hasNextInt()`|This function returns a boolean that validates if there is another int in the input of the defined scanner.|
|`input.useDelimiter(",")`:|This function helps us specify what delimiters we want to use. A _delimiter_ is used to separate data units. This `,` delimiter can be especially useful when a program is required to read csv (comma separated values) [files](https://www.codecademy.com/resources/docs/java/files).|


```java
import java.util.Scanner;

public class Introduction {
  public static void main(String[] args) {
    Scanner input = new Scanner(System.in);
    
    // Add code below:
    System.out.println("What's your name?");
    String userName = input.next();
    System.out.printf("Hello %s! It's nice to meet you.", userName);
  }
}
```

### FileReader
[`FileReader`](https://docs.oracle.com/javase/9/docs/api/java/io/FileReader.html) and [`FileWriter`](https://docs.oracle.com/javase/9/docs/api/java/io/FileWriter.html) are two of Java’s built-in input stream [classes](https://www.codecademy.com/resources/docs/java/classes) and can be extremely useful when your program is working with external [files](https://www.codecademy.com/resources/docs/java/files) when those files contain text information. Both of these classes are specifically made to write character information to and from files.

As with `Scanner`, we will need to import these classes in order to use them in our program. They both reside in the `java.io` package. Unlike with Scanner however, these classes throw a specific type of exception, an `IOException`, if something goes wrong during the read/write process. This `IOException` also needs to be imported from the same package. We’ll dive into how exceptions work later in the lesson, for now we’ll add a line to our main method declaration that simply throws the `IOException` out of the program.

```java
public static void main (String[] args) throws IOException {}
```

#### Step 1: Declare and initialize your FileReader
As with nearly all Java objects, we follow the pattern `ObjectClass objectName = new ObjectClass();`

```java
FileReader reader = new FileReader(filePath);
```

You will notice here in the constructor that we are passing in a `filePath`, this is a String that represents the path of the file to be read.

- An example of how an absolute path may look is `FileReader input = new FileReader("C:/SampleFolder/input.txt")`
- An example of how a relative path may look is `FileReader input = new FileReader("../documents/SampleFolder/input.txt")`

Alternatively, you may choose to create an object of the variable type `File` to pass into the `FileReader`. This is useful if you plan to have the user pass in a path to the input file.

```java
//Option 1: Pass file path/name directly to FileReader
FileReader input1 = new FileReader("input.txt");
 
// Option 2: Use File object to pass file info to FileReader
// Save file path that has been passed in by the user into a string variable.
String fileName = args[0];
// Pass path to File object
File inputFile = new File(fileName);
// Pass File object to FileReader
FileReader input2 = new FileReader(inputFile);
```

#### Step 2: Read your file
Also much like `Scanner`, `FileReader` has [methods](https://www.codecademy.com/resources/docs/java/methods) to validate content and read contents, these are `.ready()` and `.read()`. The `.ready()` method makes sure that there is content to read and the `.read()` method reads the file one character at a time. The following code shows how to print each character in the file, which will effectively print the contents of the file as written.

```java
while (reader.ready()) {
  System.out.print((char) reader.read());
}
```

#### Step 3: Wrapping Up Loose Ends
It is critically important to close resources such as files and input streams. These can tie up memory on the processor and in some file systems only one asset can access a file at a time, essentially blocking all access to the file from other sources. These resources can either be manually closed like we will do here, or automatically closed with a `try-with-resources` block like we will implement in future exercises.

Closing `FileReader` also has the added benefit of `flushing` the stream as well, making sure that any information that is still in the `FileReader`‘s buffer is written to the console.

```java
input.close();
```

```java
import java.io.FileReader;
import java.io.IOException;

public class Introduction {
  public static void main(String[] args) throws IOException {
    String path = "./input.txt";
    FileReader input = new FileReader(path);
    int counter = 0;
    while ((counter = input.read()) != -1) {
      System.out.print((char)counter);
    }
    input.close();
  }
}
```

### FileWriter
As the name suggests, `FileWriter` is used to [output](https://www.codecademy.com/resources/docs/java/output) data, specifically text or character data, from a program into a file. Like `FileReader`, `FileWriter` writes to the file using the standard character encoding (this is set by your computer and locale).

`FileWriter` also is contained in the `java.io` package and needs to be imported so we can use it.

```java
import java.io.FileWriter;
```

#### Step 1: Declare your output stream
The statement `FileWriter output = new FileWriter("output.txt")` will create a file named **output.txt** in the same folder where your Java program is saved. You may also choose to place an absolute or relative file path in the brackets. Creating a file this way WILL NOT create directories (folders), only the file. If the directories don’t exist, you will end up with a [`FileNotFoundException`](https://www.codecademy.com/resources/docs/java/errors/filenotfoundexception) being thrown, which is a subclass of `IOException`.

Alternatively, you may choose to create an object of the variable type `File` to pass into the `FileWriter`. This is useful if you plan to have the user pass in a path where they want to store the output or if you want to test if it’s a viable file before writing to it:

```java
//Option 1: Pass file path/name directly to FileWriter
FileWriter output1 = new FileWriter("output.txt");
 
// Option 2: Use File object to pass file info to FileWriter
// Save file path that has been passed in by the user into a string variable.
String fileName = args[0];
// Pass path to File object
File outputFile = new File(fileName);
// Pass File object to FileWriter
FileWriter output2 = new FileWriter(outputFile);
```

#### Step 2: Write to your file
This is achieved using the `.write()` function. Since `FileWriter` is specifically tailored to writing text and character data to an output file, the `.write()` function accepts a string as an argument.

```java
// Declare FileWriter
FileWriter output = new FileWriter("output.txt");
 
// Declare statement
String statement = "Hello World!";
 
// Option 1:
// Write all contents to file
output.write(statement);
 
// Option 2:
// If you want to write specific portions of a string to a file you may choose to use the following statement
// output.write(String str, int offset, int length);
output.write(statement, 0, 5);
// Writes only "Hello" to the file
```

#### Step 3: Close the file
It is important we close a file once we are done writing to it. To do this, we use the `close()` method.

```java
output.close();
```

In Java, most [classes](https://www.codecademy.com/resources/docs/java/classes) that write output use a buffer-style memory, you can think of it as a middleman between the information you want to write and the file. The information gets loaded into the buffer and as it gets full, it comes out the other side and into the file. One way to make sure the information makes it out of the buffer and into the file is to it `.flush()` out. If we are done with the `FileWriter` we can simply `close` it, which will flush the stream, destroy the internal memory holdings of the `FileWriter` and free up the file for use elsewhere.

### IOExceptions
[_Errors_](https://www.codecademy.com/resources/docs/java/errors) are unwanted issues that occur in a program that cannot be handled by a program. They may even result in a program crashing. _Exceptions_ are issues that may occur when a program is running that can be foreseen, or caught by the program. For example, if a user passes an incorrect file path in the arguments of a Java program.

There are two types of exceptions: _checked_ and _unchecked_. Checked exceptions are exceptions that are thrown when a program is compiling and unchecked exceptions typically occur during runtime. A developer can check if a block of code is going to throw an exception by using a `try-catch` block, essentially trying some code out to see if an exception occurs or not, and then catching the exception and running a separate block of code in those situations. This allows us to prevent the Exception (unless we want it to) from being thrown out of our `main` method and crashing the program.

`IOExceptions` are exceptions that are related to input and/or [output](https://www.codecademy.com/resources/docs/java/output) in a program and are classified as checked exceptions.

Some examples of when `IOExceptions` occur include:

- Failed attempts at trying to access a file.
- The end of a file has been reached.
- The file a program is attempting to access cannot be found.
- An input/output operation has been interrupted.

We can code our program to handle `IOExceptions` in areas of our code where we are dealing with input and output. To start off we must first import the `IOExceptions` class into our program using `import java.io.IOException.`

When we catch exceptions in this manner, we no longer have to declare that our method `throws` the exception, since we’ve handled it at this level. There are many ways we may choose to handle an exception. We may choose to print an error using `System.out.println()` or run a new instance of the program.

```java
String statement = "Hello World!";
 
try {
  FileWriter output = new FileWriter("output.txt");
  output.write(statementBytes);
  output.close();
} catch (IOException e) {
  // Handle exception
  System.out.println("There has been an IO exception");
  System.out.println(e); // Prints the actual exception
}
```

### Conclusion
- Printing [output](https://www.codecademy.com/resources/docs/java/output) in a Java program can be done using the following three commands: `System.out.print()`, `System.out.println()`, and `System.out.printf()`
- The `Scanner` class is built into Java and is useful for reading input from different sources including [user input](https://www.codecademy.com/resources/docs/java/user-input), and text [files](https://www.codecademy.com/resources/docs/java/files).
- `FileWriter` is used to output data from a program into a file on your computer, and `FileReader` is used to read from a file. They both are specifically tailored to reading and writing character/text data to files.
- `IOExceptions` are exceptions related to input or output that a program may encounter. They can be handled by a programmer using try-catch blocks.
- Java programs must initially be compiled into Java byte code before they can be run using a terminal or command prompt. When running a Java program, a user can pass in multiple arguments through the command line.


## Java and the Command Line

### Downloading Java
You more than likely have already interacted with a version of Java on your computer as many programs use it to operate. This version of Java, the version that is used simply to run programs, is called the _**Java Runtime Environment**_, and essentially takes the compiled Java byte code and allows those generic files to be run specifically on your type of computer.

As a developer though, you need the _**Java Development Kit**_, or JDK, which allows you access to the classes and interfaces of the core Java language that you use here on Codecademy such as `System.out.println()`.

Java’s JDK is available (for free) through Oracle’s website. There are several types, each with a specific purpose and you can explore these use cases on Oracle’s website, the vast majority of Java development though, occurs in the _**SE or Standard Edition**_ of the JDK. You can find the most recent version of the JDK [here](https://www.oracle.com/java/technologies/downloads/), and older versions of Java, such as Java 9 like we are using [here](https://www.oracle.com/java/technologies/downloads/archive/).

### Compiling Java
Before you can run the program from the command line, you must compile it. Open your terminal or command prompt (depending on OS), and navigate to the directory where the file you want to run is located. Once there, use `javac` and the filename to compile:

```sh
javac MyClass.java
```

This creates the `.class` file that can be executed. However, if there are any bugs found in your program, they will be flagged at this point, and the executable `.class` file will not be created. You won’t be able to run the file until it compiles with no issues.

### Running Java
Once you have your executable file, use `java` and the name of the class to run it:

```sh
java MyClass
```

**Note:** Do _not_ include the `.java` or `.class` suffixes, only use the name of the class.

### main Method Parameters
`args` is an array of `String`s that is passed to the program when it’s run. We don’t _need_ to pass anything in, but we can if we want to.

Note that we access the elements of the `args` array the same way we would access the elements of any other array.

Two extra takes aways from the `main` method:

- All arguments passed via the command line, like `Batman` is above, are passed in as Strings. So if we have a program that asks the user to input their name and age via the command line, we have to treat the age as a String until we parse (convert it from a String) the age into an integer.
- A Java program, in fact, most Java programs, is made up of many, many files. Some of these files will have `main` methods and others will not, when we use the `java` command, we are specifying which Java class inside the program that we should look for the `main` method in.


## Running Java Programs

### Running Complex Java Programs
Note: Often, you will find that the Java file which holds the main method follows the naming convention `**_____Driver.java**`. This is because this is the class that “drives,” or carries out, the tasks of the program. This practice stems from C++ programming which divides its files into more complex `header` files and `implementation` files.

#### Compilation Method 1
Once we have saved the following files in the same directory, our first step will be to compile all the files using the following commands:

```sh
javac TransportBike.java
javac TransportCar.java
javac TransportationDriver.java
```

#### Compilation Method 2
You may also choose to compile all files in the same line:

```sh
javac TransportBike.java TransportCar.java TransportationDriver.java
```

#### Compilation Method 3
Since these files all start with the same title, you may also choose to compile them using a regex as follows:

```sh
javac Transport*.java
```

#### Compilation Method 4
One more way to compile these files is by calling the `javac` command on the file that holds the main method:

```sh
javac TransportationDriver.java
```

This works because as the compiler reaches a definition that is unknown to it, such as the first instance of `TransportBike`, it will search the current folder for any `.class` files that match that signature. If no `.class` files are found, it will look for `.java` files and then attempt to compile them so that it knows how to represent the `TransportBike` object.

### Running the Program
The next step after compiling is running the program. For the example we are using, you will enter the following into the command prompt to tell the JVM (Java Virtual Machine) which file has the `main` method that you want to run:

```sh
java TransportationDriver
```

### Passing Multiple Arguments

#### Method 1: From the command line
Once we have compiled our files, we will run this program using the following command:

```sh
java TransportationDriver Customer1 Customer2
```

Note: A space between the variables we pass acts as a delimiter. It lets the program know that these are two separate arguments that are being passed in.

#### Method 2: Input file
You may also choose to pass input into a program using a text file. Let’s first save the following text to a file:

```
Customer1 Customer2
```

The code in **TransportationDriver.java** will also have to be modified to use the Scanner class. The scanner class is what will help the program read our **.txt** file.

```java
import java.io.*;
import java.util.Scanner;
public class TransportationDriver {
  public static void main(String[] args) {
    TransportBike harley = new TransportBike();
    TransportCar toyota = new TransportCar();
    String fileName = args[0];
    Scanner input = new Scanner(fileName);
    String person1 = input.next();
    String person2 = input.next();
    harley.wheels();
    toyota.wheels();
 
    System.out.println(person1 + " and " + person2 + " want to purchase a bike.");
    System.out.println(person2 + " wants to purchase a car.");
  }
}
```

Once we have saved our text file to the same directory and compiled our Java files, we will run this program using the following command:

```sh
java TranportationDriver input.txt
```


# Serialization

## What is Serialization?
One of the benefits of using objects is the ability for them to encapsulate state (or data) to use within our program, but what if we wanted to store an object’s state in a file or send it over a network? As a matter of fact, we can do this by _serializing_ our objects.

Serialization describes the process of taking an object’s state and transforming it into a _stream_ of _bytes_.

- A stream is an abstract definition of a sequence of data that is made available over time.
- A byte is an 8 bit (0s or 1s) group of data.
- A stream of bytes is a sequence of bytes that is made available over time.

To serialize an object, its fields and their types are stored in the form of bytes. These bytes are then able to be written to memory, a file, a database, or sent over a network with all the information necessary to recreate the object.

### Deserialization
Deserialization as the name suggests, does the opposite of serialization and converts a stream of bytes back into an object. Using both serialization and deserialization gives us the flexibility to persist our objects and get them back when needed.

There are a couple of important details to note about serialization and deserialization:

- The stream of bytes created by serialization only includes the member variables of an object and not its methods.
- Deserialization creates a copy of the original object. This copy shares the same state but is an entirely new object in memory.

Many programming languages like Java, C++, etc. support serialization and deserialization but differ in how they implement the process. Ultimately, this gives us the flexibility to work with the objects in, say Java, and also be able to work with a copy of that object in C++.

## Serialization

### Introduction
Often when creating Java applications and working with objects, we find the need to persist them. Specifically, we need to be able to store an object’s state (member fields) in [files](https://www.codecademy.com/resources/docs/java/files), in memory, or in a database. Java provides the `Serializable` interface to do just that.

Remember that an interface describes the behavior a class should have and by having our class implement `Serializable` it can be serialized by the Java Virtual Machine (JVM).

Let’s look at how this is done:

```java
public class Person implements Serializable {
  private String name;
  private int age;
} 
```

In the example above we’ve defined a `Person` class that implements `Serializable`. By implementing `Serializable`, the JVM will know how and what to do when a `Person` object needs to be serialized.

Notice that we didn’t need to override a method and implement it for us to be able to serialize a `Person` object. This is because `Serializable` is a _marker_ interface. A marker interface provides run time information to the JVM about the class and does not have any [methods](https://www.codecademy.com/resources/docs/java/methods) associated with it.

### Serializable Interface
In Java, the JVM defines a default way for [classes](https://www.codecademy.com/resources/docs/java/classes) that implement `Serializable` to have their objects serialized. The interface provides run-time information about the object field’s type and value for serialization and it takes care of converting it into a stream of bytes.

Although there is no need to implement any methods for serialization, it is important for the implementing class to provide a `serialVersionUID`:

```java
public class Person implements Serializable {
  private String name;
  private int age;
  private static final long serialVersionUID = 1L; 
} 
```

Recall that a `long` type’s value must end with an `L` like, `long myLong = 24L;`

In the example above, the `serialVersionUID`, a `static final long` type number, acts as an identifier for the JVM to choose the proper class to convert a stream of bytes back into an object. Our serializable class can get a `serialVersionUID` in one of the following ways:

- You can have the JVM define one for you. This is not ideal because, depending on the JVM you have, you’ll get a different value and this may cause deserialization to fail.
- You can have your IDE generate one for you. This is better than the first option but you’ll need to ensure that your IDE has this feature.
- You can define the `serialVersionUID` explicitly in the class. This is the preferred option because you don’t need to rely on the JVM or your IDE to ensure proper deserialization.

Although the JVM uses the `serialVersionUID` to locate the proper class, it does not store the class file as part of the serialization. We need to ensure we load the class file into our program (if it’s not there already). With a default process of serializing objects and the `serialVersionUID`, Java makes serialization easy to implement.

### Serializing Objects to a File
To do this we’ll need to use the helper [classes](https://www.codecademy.com/resources/docs/java/classes), `FileOutputStream`, which will help us write to a file, and `ObjectOutputStream`, which will help us write a serializable object to an [output](https://www.codecademy.com/resources/docs/java/output) stream.

```java
public class Person implements Serializable {
  private String name;
  private int age;
  private static final long serialVersionUID = 1L; 
 
  public Person(String name, int age) {
    this.name = name;
    this.age = age;
  }  
 
  public static void main(String[] args) throws FileNotFoundException, IOException{
    Person michael = new Person("Michael", 26);
    Person peter = new Person("Peter", 37);
 
    FileOutputStream fileOutputStream = new FileOutputStream("persons.txt");
    ObjectOutputStream objectOutputStream = new ObjectOutputStream(fileOutputStream);
 
    objectOutputStream.writeObject(michael);
    objectOutputStream.writeObject(peter);    
  }
} 
```

In the example above we:

- Initialized a `FileOutputStream` object in `main()` which will create and write a stream of bytes to a file named _persons.txt_.
- Initialized an `ObjectOutputStream` object in `main()` which will help serialize an object to a specified output stream.
- Used `objectOutputStream.writeObject()` in `main()` to serialize the `michael` and `peter` objects to a file.

After the execution of the above program, the _persons.txt_ will contain a stream of bytes that has the type and value information of the fields for the `michael` and `peter` objects respectively.

### Deserializing an Object to a File
As the name suggests, deserialization does the opposite of serialization and transforms a stream of bytes into a Java object.

Like with serialization, we’ll make use of helper [classes](https://www.codecademy.com/resources/docs/java/classes) `FileInputStream`, which helps us read a file, and `ObjectInputStream` which helps us read a serialized stream of bytes.

Assuming we have the file **persons.txt** we created in the last exercise, let’s understand how to do this by looking at some code:

```java
public class Person implements Serializable {
  public static void main(String[] args) throws FileNotFoundException, IOException, ClassNotFoundException {
 
    FileInputStream fileInputStream = new FileInputStream("persons.txt");
    ObjectInputStream objectInputStream = new ObjectInputStream(fileInputStream);
 
    Person michaelCopy = (Person) objectInputStream.readObject();
    Person peterCopy = (Person) objectInputStream.readObject();
  }
}
```

In the example above we:

- Initialized `FileInputStream` and `ObjectInputStream` in `main()` which will read a file and transform a stream of bytes into a Java object.
- Created a `Person` object named `michaelCopy` by using `objectInputStream.readObject()` to read a serialized object.

It’s important to note that deserialization creates a _copy_ of the original object. This means that the deserialized object shares the same field values as the original object but is located in a different place in memory. Also, The deserialized objects will be in the order that they were serialized in and we need to explicitly typecast the `readObject()` return value back into the type of object we serialized.

The JVM ensures it deserializes the object using the correct class file by comparing the `serialVersionUID` in the class file with the one in the serialized object. If a match is not found an [`InvalidClassException`](https://www.codecademy.com/resources/docs/java/errors/invalidclassexception) is thrown. Also, `readObject()` throws a `ClassNotFoundException` when the `class` of the serialized object cannot be found.

### Serializable Fields
When serializing objects, we often need to handle static class fields or exclude non-static fields in the serialization. Recall that the JVM defines a default way of serializing objects; this default includes ignoring static class fields, which belong to a class and not an object. The JVM also serializes all fields in an object, even those marked `private` and `final`.

Although the JVM implicitly serializes non-static fields, we can instruct the JVM to ignore them using the `transient` keyword. A field marked as `transient` will have its value ignored during serialization and instead receive the default value for that type of field.

```java
public class Person implements Serializable {
  private String name;
  private int age;
  private static int numberOfPeople = 10;
  private transient int yearBorn;  
} 
```

In the example above, we defined a `static` field called `numberOfPeople` with a value of `10`. Since it belongs to the class, it will not be included in the serialization process. We also defined a `transient` field called `yearBorn` of type `int`. The JVM will ignore the initialized value of this field and instead serialize the field with its default value for its type (`0` in this case).

Let’s discuss some interesting aspects of deserializing objects with `transient` and `static` fields:

- The deserialized (copy) object will not get the default value for a `static` field (in our example the value `0`). Since a `static` field belongs to the class and not the object, a deserialized `static` field will receive the value it corresponds to in the current class.
- A constructor is not called during deserialization for the deserialized type object. Object fields are set using _reflection_.
- A constructor is only called for the first non-serializable class in the parent hierarchy of the deserialized object.

We often want to serialize all non-static fields in an object. However, sometimes we may need to serialize `transient` fields if a field’s value is dependent on other fields or, more importantly, if we have a reference field that is not serializable.

### Serializing Associated Fields
For reference types to be serializable, they must also implement the `Serializable` interface, which the `String` class does. If the reference type did not implement `Serializable`, then we would get a `NotSerializableException` thrown. When the JVM encounters a reference type, it will try to serialize the reference type first before trying to serialize the encapsulating object.

Let’s look at class definitions and go through the steps of serializing a `Person` object:

```java
public class Address implements Serializable{
  private String streetName;
}
 
public class Person implements Serializable{
  private Address address;
}
```

In the example above, when serializing a `Person` object the JVM will:

- Check that the `Person` object is serializable and try to serialize the `Address` type.
- Check that the `Address` object is serializable and try to serialize the `String` type.
- Check that the `String` object is serializable and serialize the value.
- Finish serializing the `Address` object after serializing `streetName`.
- Finish serializing the `Person` object after serializing `address`.

Our serializable [classes](https://www.codecademy.com/resources/docs/java/classes) will often have a combination of reference and primitives types, but the JVM will perform the same steps as above. If an exception were to be thrown at any point while serializing a reference type, a `NotSerializableException` would be thrown and propagated up.

### Custom Serialization
As we’ve learned about serialization, we’ve discussed how the JVM defines a default way to serialize objects when their [classes](https://www.codecademy.com/resources/docs/java/classes) implement the `Serializable` interface. Can we modify this default process? We can by implementing the [methods](https://www.codecademy.com/resources/docs/java/methods) `readObject()` and `writeObject()` in our class!

```java
public class DateOfBirth {
  private int month;
  private int day;
  private int year;
 
  // constructors and getters
}
 
public class Person implements Serializable {
  private String name;
  private DateOfBirth dateOfBirth;
 
  private void writeObject(java.io.ObjectOutputStream stream) throws IOException{
    stream.writeObject(this.name);
    stream.writeInt(this.dateOfBirth.getMonth());
    stream.writeInt(this.dateOfBirth.getDay());
    stream.writeInt(this.dateOfBirth.getYear());
  }
 
  private void readObject(java.io.ObjectInputStream stream) throws IOException, ClassNotFoundException{
    this.name = (String) stream.readObject();
    int month = (int) stream.readInt();
    int day = (int) stream.readInt();
    int year = (int) stream.readInt();
    this.dateOfBirth = new DateOfBirth(month, day, year);
  }    
}
```

In the example above:

- We have two classes: `Person` which implements `Serializable` and `DateOfBirth` which does not.
- `Person` has a reference field of type `DateOfBirth`.
- If we were to use the default serialization process, we would get a `NotSeriliazableException` because `DateOfBirth` does not implement `Serializable`.
- We implement `writeObject()`, which must throw `IOException`, to serialize a `DateOfBirth` object by manually serializing all of its fields separately. We also serialize the serializable `String` field.
- We implement `readObject()`, which must throw `IOException` and `ClassNotFoundException`, to deserialize a `Person` object by reading the `int` fields that are a part of `DateOfBirth` and creating a new `DateOfBirth` object with the provided constructor. This new object is used to set the `dateOfBirth` field in `Person`.

Often, the default process of serialization is enough as long as all references implement `Serializable`. The implementation of `readObject()` and `writeObject()` is useful when we have a reference field that does not or cannot implement `Serializable`. We could also potentially handle `static` field values if we needed to persist them. This, however, is not good practice as a `static` field should belong to a class and not an object.

### Review
- Java makes serialization easy using the `Serializable` interface.
- The `Serializable` interface is a _marker_ interface and requires no [methods](https://www.codecademy.com/resources/docs/java/methods) to be implemented.
- To use `FileOutputStream` and `ObjectOutputStream` to serialize objects to a file.
- To use `FileInputStream` and `ObjectInputStream` to deserialize objects from a file.
- `static` and `transient` fields are not serializable.
- The JVM handles serializing objects with reference type fields.
- To implement `writeObject()` to customize the serialization of an object to handle non-serializable fields.
- To implement `readObject()` to customize the deserialization of an object with non-serializable fields.

# Generics and Collections

## Generics

### Introduction
When using Java, we often write [classes](https://www.codecademy.com/resources/docs/java/classes) and algorithms that work around certain [data types](https://www.codecademy.com/resources/docs/java/data-types). Let’s look at the following `class` as an example:

```java
public class StringBox {
  public String myString;
} 
```

In the example above, we have a `StringBox` class which represents a real-world box of words. This class’s [methods](https://www.codecademy.com/resources/docs/java/methods) perform all of their computations with regards to the `String myString` field. What if we wanted a box of `int`s? We could create a new class:

```java
public class IntegerBox {
  public int myInt;    
} 
```

Generics, like the name implies, allow us to create generic classes and methods by specifying a type parameter. We can make `StringBox` and `IntegerBox` into a generic `Box` class like so:

```java
public class Box<T> {
  private T data;
}
```

In the example above, we created a generic `Box` class with a type parameter `T`. All class methods perform their computation around the `T`-type parameter We can now specify that we want a `String`, `Integer`, or any other type of `Box` by specifying a type argument.

### Classes
Previously, we saw how [generics](https://www.codecademy.com/resources/docs/java/generics) can help make our code more manageable and flexible for future needs. We created the following generic class:

```java
public class Box <T> {
  private T data;
 
  public Box(T data) {
    this.data = data; 
  }
 
  public T getData() {
    return this.data;
  }  
}
```

- The type parameter must be specified within the diamond operator (`<>`) after the `class` name.
- The type parameter, `T`, is similar to a method parameter but instead receives a `class` or `interface` type as an argument as opposed to a reference or primitive type.
- The constructor accepts a `T`-type parameter to initialize `data`.
- The getter method returns the type parameter `T` when returning `data`.

Creating generic [classes](https://www.codecademy.com/resources/docs/java/classes) is great, but we also need to be able to create instantiations of them in our programs:

```java
Box<String> myStringBox = new Box<>("Apple");
```

In the example above, the object `myStringBox` is created like a non-generic object, but differs in:

- Needing the diamond operator with the `class` or `interface` type argument, `<String>` in this example, after the `class` name.
- Needing the empty diamond operator before calling the constructor `new Box<>("Apple")`.

When defining type parameters, although not being a hard requirement, it’s best practice to make them single, uppercase letters to easily distinguish them from the names of classes or [variables](https://www.codecademy.com/resources/docs/java/variables). By convention, type parameters are `E` (Elements), `K` (Key), `N` (Number), `T` (Type), `V` (Value), and `S` (or `U` or `V`) for multiple type parameters.

One last thing to note is that before Java 7, generic references had to be created like this:

```java
Box<String> myStringBox = new Box<String>("Apple");
```

In the example above, the `<String>` type argument also needed to be specified prior to calling the constructor. This is no longer necessary due to Java’s _type inference_ where the [compiler](https://www.codecademy.com/resources/docs/java/compiler) can infer the `<String>` type argument in the constructor from the context of the reference definition `Box<String>`.

### Wrapper Classes
[Generics](https://www.codecademy.com/resources/docs/java/generics) allow our programs to adapt to different data type needs but one issue with them is that we cannot use primitive types (`int`, `double`, `boolean`, etc) as arguments to generic type parameters. For example, we cannot create a `Box` of integers this way:

```java
Box<int> intBox = new Box<>(56);
```

Fortunately, Java provides _wrapper classes_ to allow us to create objects of primitive types and use them as type parameters. We can now create a `Box` of integers this way:

```java
Box<Integer> intBox = new Box<>(56);
```

In the example above, the `Integer` wrapper class is used in place of `int` to work as a type argument. Also, notice that we are able to pass `56` as the argument to the constructor and this is because of _autoboxing_.

Autoboxing allows wrapper [classes](https://www.codecademy.com/resources/docs/java/classes) to take primitive values and convert them to their corresponding wrapper object by automatically calling the `valueOf()` method. For example, the following statements are equivalent when creating a `Box<Integer>`:

```java
Integer a = 56;  // Autoboxing, automatic call to `valueOf()`
Box<Integer> intBox1 = new Box<>(a);
Box<Integer> intBox2 = new Box<>(56);  // Autoboxing, automatic call to `valueOf()`
Box<Integer> intBox3 = new Box<>(Integer.valueOf(56));
```

We can also take the wrapper object and convert it back to its primitive value using one of the wrapper object’s `Value()` [methods](https://www.codecademy.com/resources/docs/java/methods). This process is also automated for us and is known as _unboxing_.

```java
Integer a = 56;
int aPrimitive1 = a.intValue();  // Return primitive `int` value from `Integer` object
int aPrimitive2 = a;  // Unboxing, automatic call to `intValue()`
```

### Interfaces
We’ve seen how to create a generic class, but we can also create a generic interface.

```java
public interface Replacer<T> {
  void replace(T data);
}
```

The generic interface `Replacer` is created like a generic class where the type parameter `<T>` must be appended to the interface name. Interface method declarations are similar to non-generic [interfaces](https://www.codecademy.com/resources/docs/java/interfaces) and can include non-generic [methods](https://www.codecademy.com/resources/docs/java/methods) as well.

A generic interface can be implemented by a generic class and its generic type parameter can be used as the argument to the interface type parameter.

```java
public class Box <T> implements Replacer<T> {
  private T data;
 
  @Override
  void replace(T data) {
    this.data = data; 
  }
}
```

In the example above, the `Box` type parameter `<T>` will be used as the type argument for the `Replacer` type parameter `<T>`.

We can also have a non-generic class implement a generic interface by specifying the type argument to the interface.

```java
public class StringBag implements Replacer<String> {
  private String data;
 
  @Override
  void replace(String data) {
    this.data = data; 
  }
}
```

In the example above, the `StringBag` is a non-generic `class` that implements `Replacer` and provides `String` as the argument to the type parameter. Notice that the `replace()` parameter `data` has a `String` type as opposed to the generic `T` in the previous example.

Now let’s create `interface` type references similarly to how we created generic `class` references:

```java
Replacer<Integer> boxReplacer = new Box<>();  // Using generic `Box` implementation
Replacer<String> bagReplacer = new StringBag();  // Using non-generic `StringBag` implementation
```

In the example above we created two `Replacer` references. The `Box` implementation can be of any type but the `StringBag` implementation needs to be a `<String>` type because of the non-generic class implementation.

### Methods
We’ve covered generic [classes](https://www.codecademy.com/resources/docs/java/classes) and [interfaces](https://www.codecademy.com/resources/docs/java/interfaces), but what can we do if we want one of our [methods](https://www.codecademy.com/resources/docs/java/methods) to be generic and not the whole class or interface? We can create generic methods to do just that.

```java
public class StringBox {
  private String data;
 
  public <T> boolean isString(T item) {
    return item instanceof String; 
  }
}
 
StringBox box = new StringBox();
box.isString(5); // Returns false
```

It’s important to note that generic methods need to include the type parameter, `<T>` in our example, before the return type, even if the return type is `void`.

We can also do this with `static` methods. Their signatures have the same requirements except for also needing the `static` keyword.

```java
public class StringBox {
  private String data;
 
  public static <T> boolean isString(T item) {
    return item instanceof String; 
  }
}
StringBox.isString(5);  // Returns false
```

### Benefits
We can get away with not providing a type argument to a generic class or interface. This is known as using a _raw type_ and they were prevalent before the introduction of generics in Java 5.

```java
public class Box <T> {
  private T data;
 
  public Box(T data) {
    this.data = data; 
  }
 
  public T getData() {
    return this.data;
  }  
}
 
Box box = new Box<>("My String");  // Raw type box
String s2 = (String) box.getData();  // No incompatible type error
String s1 = box.getData();  // Incompatible type error
```

We get an `Incompatible type` error as `getData()` returns an `Object` type and we are trying to implicitly downcast to a `String`.

Raw types should be avoided because generics:

- Avoid “incompatible type” [errors](https://www.codecademy.com/resources/docs/java/errors) when retrieving data from raw types.
- Avoid a potential runtime `ClassCastException` error when explicitly typecasting.
- Give us compile-time type checking, which helps detect bugs before our code runs.
- Help when the JVM applies _type erasure_

When using generics, type erasure is applied by the JVM and will cause all type parameters to be replaced by `Object` or their type bounds. The type erasure will also apply any necessary type casting to ensure our code is type-safe and that the final byte code produced has non-generic types.

### Multiple Type Parameters
As of now, our generic [classes](https://www.codecademy.com/resources/docs/java/classes), [interfaces](https://www.codecademy.com/resources/docs/java/interfaces), and [methods](https://www.codecademy.com/resources/docs/java/methods) have all taken a single parameter type. But what if our program needed to specify two or more parameter types? Java [generics](https://www.codecademy.com/resources/docs/java/generics) allow us to do that as well.

```java
public class Box<T, S> {
  private T item1;
  private S item2;
  // Constructors, getters, and setters
}
Box<String, Integer> wordAndIntegerBox = new Box<>("Hello", 5);
```

This can also be done for interfaces and methods.

```java
public class Util {
  public static <T, S> boolean areNumbers(T item1, S item2) {
    return item1 instanceof Number && item2 instanceof Number; 
  }
}
 
boolean areNums = Util.areNumbers("Hello", 34);  // false
```

A cool thing about the example is if it weren’t for Java’s type inferences, the above method would have to be called like this:

```java
Boolean areNums = Util.<String, Integer>areNumbers("Hello", 34);  // false
```

### Upper Bounds
What if we needed to restrict what class or interface could be used as a type argument? We can accomplish this by assigning an _upper bound_. An upper bound will restrict a generic type to be a specific type or any type that `extends` it.

```java
public class Box <T extends Number> {
  private T data; 
}
```

The `extends` in this example means that `T` can be a `Number` or any of its subclasses (or interfaces).

We can create references to `Box` as follows:

```java
Box<Integer> intBox = new Box<>(2);  // Valid type argument
Box<Double> doubleBox = new Box<>(2.5);  // Valid type argument
Box<String> stringBox = new Box<>("hello");  // Error
```

We can also add upper bounds to generic methods as follows:

```java
public static <T extends Number> boolean isZero(T data) {
  return data.equals(0);
}
```

Java also allows us to create a type parameter with multiple bounds.

```java
public class Box <T extends Number & Comparable<T>> {
  private T data; 
}
```

It’s important to note that when defining multiple bounds, any upper bound that is a `class` (in our example `Number`) must come first followed by any interfaces (in our example `Comparable<T>`).

### Wildcards
We can make our code even more general when we don’t need the more strict type checking of using type parameters by using _wildcards_. A wildcard, denoted by the `?` symbol, represents an unknown type when used with generic [methods](https://www.codecademy.com/resources/docs/java/methods).

```java
public class Util {
  public static void printBag(Bag<?> bag) {
    System.out.println(bag.toString()); 
  }
}
Bag<String> myBag1 = new Bag("Hello");
Bag<Integer> myBag2 = new Bag(23);
Util.printBag(myBag1);  // Hello
Util.printBag(myBag2);  // 23
```

You may be thinking how this is different than using a type parameter because we could write the above method as:

```java
public static <T> void printBag(Bag<T> bag) {
  System.out.println(bag.toString()); 
}
```

This implementation makes no difference, but you may notice that the wildcard version is better as it does not need the extra `<T>` before the return type making the signature easier to read.

In general, we should use type parameters, when we have a relationship between the type of arguments and the return type.

```java
public static <T> Bag<T> getBag(Bag<T> bag) {
  return bag;
}
```

This use of type parameters maintains strong type checking throughout our code.

We can also create upper bounds and lower bounds when using wildcards.

```java
public static void printBag(Bag<? extends Number> bag) {
  System.out.println(bag.toString()); 
}
```

### Wildcard Lower Bounds
We can also provide a _lower bound_ when working with wildcards. A lower bound wildcard restricts the wildcard to a class or interface and any of its parent types.

```java
public class Util {
  public static void getBag(Bag<? super Integer> bag) {
    return bag;
  }
}
```

In the example above, we used the `super` keyword to restrict the argument to `getBag()` to be a `Bag` of `Integer`, `Number`, or `Object`. If a call to `getBag()` with `Bag<Double>` is made, it would result in an error because `Double` is not an `Integer` or one of its parents.

Some important things to note about lower bounds are:

- They cannot be used with generic type parameters, only wildcards.
- A wildcard cannot have both a lower bound and an upper bound. In this case, it’s best to use a generic type parameter.

There are some general guidelines provided by Java as to when to use what type of wildcard:

- An upper bound wildcard should be used when the variable is being used to serve some type of data to our code.
- A lower bound wildcard should be used when the variable is receiving data and holding it for later use.
- When a variable that serves data is used and only uses `Object` [methods](https://www.codecademy.com/resources/docs/java/methods), an unbounded wildcard is preferred.
- When a variable needs to serve data and store data for later use, a wildcard should not be used (use a type parameter instead).

### Review
- [Generics](https://www.codecademy.com/resources/docs/java/generics) help us make generic, scalable code.
- The diamond operator (`<>`) is used to define generic [classes](https://www.codecademy.com/resources/docs/java/classes), [interfaces](https://www.codecademy.com/resources/docs/java/interfaces), or [methods](https://www.codecademy.com/resources/docs/java/methods).
- Generics provide compile-time type safety and bug detection as opposed to raw types.
- We can create multiple bound generic classes, interfaces, and methods.
- Wildcards are used to define unknown types.
- To Add upper bounds to type parameters and wildcards.
- To Add lower bounds to wildcards.


## Collections

### Introduction
The [collections](https://www.codecademy.com/resources/docs/java/collections) framework provides data structures (through [interfaces](https://www.codecademy.com/resources/docs/java/interfaces) and implementing classes) and algorithms, which perform common tasks on collections. The collections framework allows us to focus on the important parts of our program and not on low-level implementation details (like needing to implement a dynamic sizing collection).

The collections framework provides a hierarchical relationship between its interfaces, making the various implementations compatible with each other and thus making our code scalable and flexible. All the interfaces in the collections framework are generic, which allows us to use optimized and tested “plumbing” for our specific [data types](https://www.codecademy.com/resources/docs/java/data-types).

### List
The [collections](https://www.codecademy.com/resources/docs/java/collections) framework provides a core set of [interfaces](https://www.codecademy.com/resources/docs/java/interfaces) to define different collection behaviors. One of the core interfaces is the `List` interface. A `List` is a collection where elements are ordered in a sequence. `List`s allow us to have duplicate elements and fine-grain control over where elements are inserted in the sequence. Like [arrays](https://www.codecademy.com/resources/docs/java/arrays), the position of a `List` is known as the _index_ and is `0` based. Unlike arrays, which have a static size, `List`s are dynamically sized.

The collections framework provides many `List` implementations, but we’ll focus on the [`ArrayList`](https://www.codecademy.com/resources/docs/java/array-list?page_ref=catalog) and `LinkedList`. The `ArrayList` is the overall preferred implementation for most use cases but the `LinkedList` performs better than an `ArrayList` if your program mostly inserts and deletes elements at the beginning or end of a list.

Let’s create a `List` using an `ArrayList` as its implementation and see some operations:

```java
List<Integer> intList = new ArrayList<>(); // Empty `List`
intList.add(4); // 4
intList.add(6); // 4, 6
intList.add(3); // 4, 6, 3
intList.set(1, 3); // 4, 3, 3
 
int a = intList.get(2); // a = 3
int b = intList.indexOf(3); // b = 1
 
List<Integer> subIntList = intList.subList(1,3); // subIntList -> 3, 3
```

We can iterate through a `List` using the enhanced `for-loop`.

```java
// Assuming `intList` has elements -> 1, 5, 2, 6, 1
for (Integer number: intList) {
  System.out.println(number);  
}
// OUTPUT TERMINAL: 1 5 2 6 1
```

Note that we use the `int` wrapper class `Integer` to iterate through the elements in `intList`. However, we could have also used an ‘int’.

### Set
Another core interface provided by the [collections](https://www.codecademy.com/resources/docs/java/collections) framework is the [`Set`](https://www.codecademy.com/resources/docs/java/set?page_ref=catalog) interface. A `Set` is a collection of unique elements and all of its [methods](https://www.codecademy.com/resources/docs/java/methods) ensure this stays true.

The [`HashSet`](https://www.codecademy.com/resources/docs/java/hashset?page_ref=catalog) implementation has the best performance when retrieving or inserting elements but cannot guarantee any ordering among them.

The `TreeSet` implementation does not perform as well on insertion and deletion of elements but does keep the elements stored in order based on their values (this can be customized).

The `LinkedHashSet` implementation has a slightly slower performance on insertion and deletion of elements than a `HashSet` but keeps elements in insertion order.

```java
Set<Integer> intSet = new HashSet<>();  // Empty set
intSet.add(6);  // true - 6  
intSet.add(0);  //  true - 0, 6 (no guaranteed ordering)
intSet.add(6);  //  false - 0, 6 (no change, no guaranteed ordering)
 
boolean isNineInSet = intSet.contains(9);  // false
boolean isZeroInSet = intSet.contains(0);  // true
```

All of these methods work for other `Set` implementations too.

We can iterate through a `Set` using the enhanced `for-loop` and notice that we can’t guarantee the ordering of elements looped.

```java
// Assuming `intSet` has elements -> 1, 5, 9, 0, 23
for (Integer number: intSet) {
  System.out.println(number);
}
// OUTPUT TERMINAL: 5 0 23 9 1
```

### Queue
The [`Queue`](https://www.codecademy.com/resources/docs/java/queue?page_ref=catalog) core interface in the [collections](https://www.codecademy.com/resources/docs/java/collections) framework is a collection that implements the Queue data structure. A `Queue` is a First In First Out (FIFO) data structure in which elements are inserted at the _tail_ (back) of the collection and removed from the _head_ (front). Think of it like a line (queue) of people waiting to make a purchase: the first people that arrive on the line (queue) will be the first ones to be able to make a purchase.

A `Queue` has two types of access [methods](https://www.codecademy.com/resources/docs/java/methods) for inserting, removing, and getting (but not removing) the element at the head of the `Queue`.

The following methods throw an exception when:

- `add()` - there is no space for the element
- `remove()` - there are no elements to remove
- `element()` - there are no elements to get

The following methods `return` a special value:

- `offer()` - `false` there is no space for the element
- `poll()` - `null` there are no elements to remove
- `peek()` - `null` there are no elements to get

The methods that return a special value should be used when working with a statically sized `Queue` and the exception throwing methods when using a dynamic `Queue`.

Like the other collections framework [interfaces](https://www.codecademy.com/resources/docs/java/interfaces), `Queue` has many implementations. We’ll focus on `LinkedList` and [`PriorityQueue`](https://www.codecademy.com/resources/docs/java/priorityqueue?page_ref=catalog). We’ve seen `LinkedList` be used as a `List` implementation, but it’s also perfect when needing a basic `Queue` implementation. Being able to use a `LinkedList` as both a `List` and a `Queue` is a perfect example of the compatibility within the collections framework. The `PriorityQueue` ensures the top element is the smallest relative to the data type’s natural ordering (or some custom ordering policy you provide).

```java
Queue<String> stringQueue = new LinkedList<>();
stringQueue.add("Mike"); // true - state of queue -> "Mike"
stringQueue.offer("Jeff"); // true - state of queue -> "Mike", "Jeff" 
 
String a = stringQueue.remove() // Returns "Mike" - state of queue -> 1
String b = stringQueue.poll() // Returns "Jeff" - state of queue -> empty
String c = stringQueue.peek() // Returns null
String d = stringQueue.element() // Throws NoSuchElementException
```

We can iterate through a `Queue` using the enhanced `for-loop`.

```java
// Assuming `stringQueue` has elements -> "Mike", "Jack", "John"
for (String name: stringQueue) {
  System.out.println(name);
}
// OUTPUT TERMINAL: "Mike", "Jack", "John"
```

One thing to note about a `PriorityQueue` is that an enhanced `for-loop` (or [`Iterator`](https://www.codecademy.com/resources/docs/java/iterator)) makes no guarantee in the ordering of elements after the head.

### Deque
The last of the core [interfaces](https://www.codecademy.com/resources/docs/java/interfaces) in the [collections](https://www.codecademy.com/resources/docs/java/collections) framework is the `Deque` interface (pronounced “Deck”). A deque (short for “double-ended queue”) is a type of queue that allows us to access elements from the front and the back of the queue.

The `Deque` interface has two types of [methods](https://www.codecademy.com/resources/docs/java/methods) for manipulating the front and back of the collection.

The following are some of the available methods and the exceptions they throw:

- `addFirst()`, `addLast()` - there is no space to add an element.
- `removeFirst()`, `removeLast()` - there is no element to remove.
- `getFirst()`, `getLast()` - there is no element to get.

The following methods return a special value:

- `offerFirst()`, `offerLast()` - `false` when there is no space to add an element.
- `pollFirst()`, `pollLast()` - `null` when there is no element to remove.
- `peekFirst()`, `peekLast()` - `null` when there is no element to get.

A `Deque` has many implementations, but we’ll focus on the `LinkedList` and `ArrayDeque` implementations. The `LinkedList`, although not the most optimized, is flexible enough to not only be used as a `List` and [`Queue`](https://www.codecademy.com/resources/docs/java/queue?page_ref=catalog), but also a `Deque`. The `ArrayDeque` is the preferred implementation when needing to manipulate elements at the front and back of a collection.

```java
Deque<String> stringDeque = new ArrayDeque<>();
stringDeque.addFirst("A"); // Front -> "A" <- end
stringDeque.offerFirst("B"); // Return `true` - front -> "B", "A" <- end
stringDeque.offerLast("Z"); // Returns `true` - front -> "B", "A", "Z" <- end
 
String a = stringDeque.removeFirst()  // Returns "B" - front -> "A", "Z"
String b = stringDeque.pollLast()  // Returns "Z" - front -> "A" <- back
String c = stringDeque.removeLast()  // Returns "A" - empty deque
 
String d = stringDeque.peekFirst()  // Returns null
String e = stringDeque.getLast() // Throws NoSuchElementException
```

Note that the `offer()` methods return a boolean.

If we iterate through a `Deque` using an enhanced for-loop, the elements would be processed from front to back like a standard `Queue`. However, we can also iterate through a `Deque` from front to back by using an [`Iterator`](https://www.codecademy.com/resources/docs/java/iterator?page_ref=catalog) from the `descendingIterator()` method and a while-loop like so:

```java
// Assuming `stringDeque` has elements front -> "Mike", "Jack", "John" <- back
 
Deque<String> stringDeque = new ArrayDeque<>();
stringDeque.addLast("Mike");
stringDeque.addLast("Jack");
stringDeque.addLast("John");
 
Iterator<String> iterator = stringDeque.descendingIterator();
 
while(iterator.hasNext()) {
  System.out.println(iterator.next());
}
// OUTPUT TERMINAL:  "John", "Jack", "Mike"
```

### Collection
We’ve discussed the core [interfaces](https://www.codecademy.com/resources/docs/java/interfaces) and their implementations, but the thing that keeps the [collections](https://www.codecademy.com/resources/docs/java/collections) framework polymorphic (compatible) is the [`Collection`](https://www.codecademy.com/resources/docs/java/collection?page_ref=catalog) interface. The `Collection` interface provides a generic, general-purpose API when our program needs a collection of elements and doesn’t care about what type of collection it is.

Implementing [classes](https://www.codecademy.com/resources/docs/java/classes) may implement `Collection` [methods](https://www.codecademy.com/resources/docs/java/methods) and add restrictions to them like a [`Set`](https://www.codecademy.com/resources/docs/java/set?page_ref=catalog) does to only contain unique elements. Also, implementing classes or extending interfaces do not need to implement all methods and instead will throw an `UnsupportOperationException` when a `Collection` method is not implemented correctly.

We’ve seen `add()` and `remove()`, but some other methods `Collection` defines are:

- [`addAll()`](https://www.codecademy.com/resources/docs/java/collection?page_ref=catalog) - receives a `Collection` argument and adds all the elements.
- [`isEmpty()`](https://www.codecademy.com/resources/docs/java/collection?page_ref=catalog) - returns `true` if the collection is empty, `false` otherwise.
- `iterator()` - returns an [`Iterator`](https://www.codecademy.com/resources/docs/java/iterator?page_ref=catalog) over the collection.
- [`size()`](https://www.codecademy.com/resources/docs/java/collection?page_ref=catalog) - returns the number of elements in the collection.
- `stream()` - returns a `Stream` over the elements in the collection.
- [`toArray()`](https://www.codecademy.com/resources/docs/java/collection?page_ref=catalog) - returns an array with all elements in the collection.

```java
Collection<Integer> collection = new ArrayList<>();
collection.add(4);
collection.add(8);
 
boolean isEmpty = collection.isEmpty(); // false
int collectionSize = collection.size(); // 2
 
Integer[] collectionArray = collection.toArray(new Integer[0]);
```

Note the `new Integer[0]` argument that specifies the type of array we want returned.

We can iterate through a `Collection` with an enhanced `for-loop` as we’ve seen with the other core interfaces.

### Algorithms
What should we do when we need to sort a collection or get some statistic like the maximum or minimum element in the collection? The collections framework provides the [`Collections`](https://www.codecademy.com/resources/docs/java/collections?page_ref=catalog) class that has many `static` [methods](https://www.codecademy.com/resources/docs/java/methods) that perform these types of operations for us.

Here are some of the methods provided by the `Collections` class:

- `binarySearch()`: Performs [binary search](https://www.codecademy.com/learn/fscp-22-search-graph-search-algorithms/modules/wdcp-22-binary-search-and-search-trees/cheatsheet) over a `List` to find the specified object and returns the index if found. This method is overloaded to also accept a [`Comparator`](https://www.codecademy.com/resources/docs/java/comparator) to define a custom ordering policy. Note: this method only provides the correct value if the elements in the `List` are sorted.
- [`max()`](https://www.codecademy.com/resources/docs/java/collections/max?page_ref=catalog): Returns the maximum element in the [`Collection`](https://www.codecademy.com/resources/docs/java/collection?page_ref=catalog). This method is overloaded to also accept a `Comparator` to define a custom ordering policy.
- [`min()`](https://www.codecademy.com/resources/docs/java/collections/min?page_ref=catalog): Returns the minimum element in the `Collection`. This method is overloaded to also accept a `Comparator` to define a custom ordering policy.
- [`reverse()`](https://www.codecademy.com/resources/docs/java/collections/reverse?page_ref=catalog): Reverses the order of elements in the `List` passed in as an argument.
- [`sort()`](https://www.codecademy.com/resources/docs/java/collections/sort?page_ref=catalog): Sorts the `List` passed in as an argument. This method is overloaded to also accept a `Comparator` to define a custom ordering policy.

### Map
[`Map`](https://www.codecademy.com/resources/docs/java/map?page_ref=catalog) defines a generic interface for an object that holds key-value pairs as elements. The _key_ is used to retrieve some value (like the index in an array or `List`). A key must be unique and map to exactly one value. There are many implementations of `Map`, but we’ll focus on the [`HashMap`](https://www.codecademy.com/resources/docs/java/hashmap?page_ref=catalog) implementation.

The `HashMap` defines no specific ordering for the keys and is the most optimized implementation for retrieving values. This is Java’s implementation of a [hash table](https://www.codecademy.com/resources/docs/general/data-structures/hash-table?page_ref=catalog).

A `Map` has the following [methods](https://www.codecademy.com/resources/docs/java/methods) for accessing its elements:

`put()`: Sets the value that a key maps to. Note that this method replaces the value a key mapped to if the key was already present in the `Map`.

`get()`: Gets, but does not remove, the value the provided key argument points to if it exists. This method returns `null` if the key is not in the `Map`.

```java
Map<String, String> myMap = new HashMap<>();
 
myMap.put("Hello", "World") // { "Hello" -> "World" }
myMap.put("Name", "John") //   { "Hello" -> "World" }, { "Name" -> "John" }
 
String result = myMap.get("Hello") // returns "World" 
String noResult = myMap.get("Jack") // return `null`
```

Note that a `Map` needs a type argument for the key and value.

We can iterate over a `Map` with an enhanced `for-loop` like so:

```java
// Given a map, `myMap`, with the following key-value pairs { "Hello" -> "World" }, { "Name" -> "John"}
for (String s: myMap.keySet()){
  System.out.println("key: "+s+", value: "+myMap.get(s));
}
// OUTPUT TERMINAL:
// key: Name, value: John
// key: Hello, value: World
```

### Aggregate Operations
As we’ve worked with different types of [`Collection`](https://www.codecademy.com/resources/docs/java/collection?page_ref=catalog)s and [`Map`](https://www.codecademy.com/resources/docs/java/map?page_ref=catalog)s, we’ve seen how important and verbose `for-loops` can get. For example, this code will produce a new `Integer List` where even numbers are doubled:

```java
// Given `intList` with the following elements: 5, 4, 1, 3, 7, 8
List<Integer> evenList = new ArrayList<>();
for(Integer i: intList) {
  if(i % 2 == 0) {
    evenList.add(i*2);
  }
}
// evenList will have elements 8, 16
```

We can perform the same operation using `Stream`s. A `Stream` is a sequence of elements created from a `Collection` source. A Stream can be used as input to a _pipeline_, which defines a set of _aggregate operations_ (methods that apply transformations to a `Stream` of data). The [output](https://www.codecademy.com/resources/docs/java/output) of an aggregate operation serves as the input of the next operation (these are known as _intermediate operations_) until we reach a _terminal operation_, which is the final operation in a pipeline that produces some non-`Stream` output.

Before we continue, we need a brief understanding of _lambda functions_ in Java. A lambda eliminates the need to create (extremely verbose) anonymous [classes](https://www.codecademy.com/resources/docs/java/classes) to implement [methods](https://www.codecademy.com/resources/docs/java/methods). With lambdas, we can define the method with its parameter(s) and its return value in a small block of code. Let’s look at the example above rewritten using aggregate operations.

```java
List<Integer> evenList = intList.stream()
  .filter((number) -> {return number % 2 == 0;})
  .map(evenNum -> evenNum*2)
  .collect(Collectors.toList());
```

In the example above, we:

- Called `stream()` which returns a sequential `Stream` with elements from `intList`.
- Created a (small) pipeline with a single intermediate operation `filter()` and the terminal operation `collect()`.
- Called `filter()` which returns a `Stream` with elements that pass some filter condition. An element passes a filter condition by returning `true` when called on the filter method. We defined the filter method to return `true` if the number is even.
- Defined a lambda to provide the filter method to `filter()`. The lambda defines all the parameters before the arrow (`->`) symbol and defines the function’s body after.
- Called `map()` which will return a new `Stream` with elements that have had some method applied to them.
- Defined the `map()` method using a lambda where we have `evenNum` as a parameter and return the result of multiplying `evenNum` by 2. You can omit the parameter parentheses `()` when there is only one parameter and omit the curly braces `{}` and `return` when the lambda body is one line.
- Called `collect()` (terminal operation), which takes the `Stream` and collects the elements back into some Container (we use a `List`). Java provides a `Collectors` class with `static` utility methods to use as an argument to `collect()`.

```java
import java.util.List;
import java.util.ArrayList;
import java.util.stream.Collectors;

public class Main {
  public static void main(String[] args) {
    List<String> words = new ArrayList<>();
    words.add("Tree");
    words.add("Hello");
    words.add("World");
    words.add("Race");
    words.add("Game");
    words.add("Numbers");
    words.add("Ride");

    List<String> specialWordsWithForLoop = getSpecialWordsWithForLoop(words);

    List<String> specialWordsWithPipeline = getSpecialWordsWithPipeline(words);

    System.out.println("Special Words retrieved from for loop: "+ specialWordsWithForLoop);

    System.out.println("Special Words retrieved from pipeline: "+ specialWordsWithPipeline);

  }

  public static List<String> getSpecialWordsWithForLoop(List<String> words){
    List<String> specialWords = new ArrayList<>();

    for(String word: words) {
      if (word.length() == 4) {
        String upperCaseWord = word.toUpperCase();
        specialWords.add(upperCaseWord);
      }
    }
    return specialWords;
  }

  public static List<String> getSpecialWordsWithPipeline(List<String> words){
    List<String> specialWords = words.stream().filter(word -> word.length() == 4).map(word -> word.toUpperCase()).collect(Collectors.toList());

    return specialWords;
  }
}
```

### Review
- The collection framework hierarchy and its core [interfaces](https://www.codecademy.com/resources/docs/java/interfaces).
- The root [`Collection`](https://www.codecademy.com/resources/docs/java/collection?page_ref=catalog) interface of the hierarchy.
- The `List` interface and its [`ArrayList`](https://www.codecademy.com/resources/docs/java/array-list?page_ref=catalog) and `LinkedList` implementations.
- The [`Set`](https://www.codecademy.com/resources/docs/java/set?page_ref=catalog) interface and its [`HashSet`](https://www.codecademy.com/resources/docs/java/hashset?page_ref=catalog), `LinkedHashSet`, and `TreeSet` implementations.
- The [`Queue`](https://www.codecademy.com/resources/docs/java/queue?page_ref=catalog) interface and its `LinkedList` and [`PriorityQueue`](https://www.codecademy.com/resources/docs/java/priorityqueue?page_ref=catalog) implementations.
- The `Deque` interface and its `LinkedList` and `ArrayDeque` implementations.
- The [`Map`](https://www.codecademy.com/resources/docs/java/map?page_ref=catalog) interface and its [`HashMap`](https://www.codecademy.com/resources/docs/java/hashmap?page_ref=catalog), `LinkedHashMap`, and [`TreeMap`](https://www.codecademy.com/resources/docs/java/treemap?page_ref=catalog) implementations.
- The `Collections` utility algorithm `static` [methods](https://www.codecademy.com/resources/docs/java/methods) like [`sort()`](https://www.codecademy.com/resources/docs/java/collections/sort?page_ref=catalog), `binarySearch()`, [`max()`](https://www.codecademy.com/resources/docs/java/collections/max?page_ref=catalog), [`min()`](https://www.codecademy.com/resources/docs/java/collections/min?page_ref=catalog), and [`reverse()`](https://www.codecademy.com/resources/docs/java/collections/reverse?page_ref=catalog).
- Collection stream pipelines and aggregate operations with lambdas.


# Nested Classes

## Nested Classes

### Introduction
A _nested class_ is a [class](https://www.codecademy.com/resources/docs/java/classes?page_ref=catalog) that can be found within another class. The process of a class being enclosed in another is known as _encapsulation_. Nested classes allow programmers to rationally organize and group classes that may be closely related in a Java program.

There are two main types of nested classes: _non-static_ (also known as _inner_) nested classes, and _static_ nested classes. The type of nested class determines whether it has access to other elements (static and non-static) within its encapsulating class.

One significant benefit of implementing nested classes is that they provide an extra level of security by giving programmers the power to control the amount of access one class may have to another class and its [methods](https://www.codecademy.com/resources/docs/java/methods).

### Non-Static vs. Static

#### Non-static(inner)
Non-static nested classes can have access to both static and non-static members of the class that it is declared within. They are also known as inner classes. A non-static nested class is closely associated with the class enclosing it. So to reference a non-static nested class outside its scope, a programmer would have to also reference its encompassing class.

#### Static
A static nested class is not the same as an inner class because a static nested class cannot access all classes, [variables](https://www.codecademy.com/resources/docs/java/variables), and [methods](https://www.codecademy.com/resources/docs/java/methods) of the enclosing class. They can only access other static members of their encompassing class. Static nested classes also don’t have access to non-static members of the Java program. Unlike non-static nested classes, static nested classes don’t need to be referenced with the association of their encompassing class.

### Implementing Non-Static Nested Classes
To declare a non-static nested class within an outer class, you may use the following code:

```java
class Outer {
  String outer;
  // Assign values using constructor
  public Outer(String name) {
    this.outer = name;
  }
 
  // private method
  private String getName() {
    return this.outer;
  }
 
  // Non-static nested class
  class Inner {
    String inner;
    String outer;
  }
}
```

Notice how the `Inner` class does not have the keyword `static` preceding it. It is also important that we review what the keyword _`this`_ means in Java code. `this` is a keyword that a class uses to reference itself.

To instantiate a non-static nested class that can access other members of the outer class, first, we need to instantiate an object of the outer class:

```java
Outer outer = new Outer();
```

Next, we can instantiate an inner class object:

```java
Outer.Inner inner = outer.new Inner();
```

Note that we use the `outer` object along with the keyword `new` to create an instance of the inner class.

This step shows us an example of how a non-static class can access other static and non-static classes from the outer class. In the code below, take a look at a modified version of the Inner class from our previous example:

```java
// Non-static nested class
class Inner {
  String inner;
  String outer; 
  public String getOuter() {
  // Instantiate outer class to use its method
  outer = Outer.this.getName();
}
```

```java
class Lib {
  String objType;
  String objName;

  // Assign values using constructor
  public Lib(String type, String name) {
    this.objType = type;
    this.objName = name;
  }

  // private method
  private String getObjName() {
    return this.objName;
  }

  // Inner class
  class Book {
    String description;

    void setDescription() {
      if(Lib.this.objType.equals("book")) {
        if(Lib.this.getObjName().equals("nonfiction")) {
          this.description = "Factual stories/accounts based on true events.";
        } else {
          this.description = "Literature that is imaginary.";
        }
      } else {
        this.description = "Not a book!";
        }
    }
    String getDescription() {
      return this.description;
    }
  }
}

public class Main {
  public static void main(String[] args) {
    Lib fiction = new Lib("book", "fiction");
    Lib.Book book = fiction.new Book();
    Lib nonFiction = new Lib("book", "nonfiction");
    Lib.Book nonBook = nonFiction.new Book();

    book.setDescription();
    System.out.println("Fiction Book Description = " + book.getDescription());

    nonBook.setDescription();
    System.out.println("Non-fiction Book Description = " + nonBook.getDescription());
  }
}
```

### Implementing Static Nested Classes
A static nested class is a class that belongs to its enclosing class in the same way that a static variable belongs to its enclosing class. Static nested [classes](https://www.codecademy.com/resources/docs/java/classes) are helpful because they allow related classes to be grouped under an enclosing class. To illustrate this concept, we will use a toolbox as an example. A toolbox contains many tools that a person can use such as a hammer, a tape measure, a wrench, and others. We can implement the concept of a toolbox in Java using static nested classes like so:

```java
class Toolbox{  
  public static String toolboxName = "Awesome Toolbox";
  public String ownerName;
 
  static class Saw{
    public void cut(){
      System.out.println("Cutting...");
    }
  }
 
  static class TapeMeasure{
    public void measure(){
      System.out.println("Measuring...");
    }
  }
 
  static class Wrench{
    public void tighten(){
      System.out.println("Tightening...");
    }
 
    public void loosen(){
      System.out.println("Loosening...");
    }
  }
}
```

We can use the “toolbox” like so:

```java
public class Main{
  public static void main(String[] args) {
    Toolbox.Saw petersSaw = new Toolbox.Saw();
    Toolbox.MeasuringTape amysMeasuringTape = new Toolbox.MeasuringTape();
    Toolbox.Wrench randomWrench = new Toolbox.Wrench();
 
    petersSaw.cut(); // output: Cutting...
    amysMeasuringTape.measure(); // output: Measuring...
    randomWrench.tighten(); // output: Tightening...
}
```

Static nested classes can access static [variables](https://www.codecademy.com/resources/docs/java/variables) of the enclosing class, but cannot access non-static variables because non-static variables belong to an instance of the class and not the class itself. Modifying `Saw` in `Toolbox` like so is okay:

```java
static class Saw{
  public void cut(){
    System.out.println("Cutting...");
  }
  public void printName(){
    System.out.println(toolboxName); // When called, this will print "Awsome Toolbox"
  }
}
```

Modifying `Saw` like this will cause a [compiler](https://www.codecademy.com/resources/docs/java/compiler) error:

```java
static class Saw{
  public void cut(){
    System.out.println("Cutting...");
  }
  public void printName(){
    System.out.println(ownerName); // This will not compile!
  }
}
```

### Shadowing
Shadowing allows for overlapping scopes of members with the same name and type to exist in both a nested class and the enclosing class simultaneously. The value of the variable will depend on which object we use to call it.

```java
class Outer {
  String name = "Outer";
 
  // Nested inner class
  class Inner {
    String name = "Inner";
 
    public void printTypeMethod() {
      System.out.println(name);
      System.out.println(Outer.this.name);
    }
  }
}
 
class Main {
  // Main driver method
  public static void main(String[] args) {
    Outer outerObj = new Outer();
    Outer.Inner innerObj  = outerObj.new Inner();
    innerObj.printTypeMethod();
  }
}
```

The code above will [output](https://www.codecademy.com/resources/docs/java/output) the following:

```
Inner
Outer
```

If we take a closer look at the method `printTypeMethod()`, the keyword `this` is used in the second print statement. Using the keyword `this` along with the class name `Outer`, allows us to overlap the variable `name` with the contents of the outer class.

### Review
- There are two main types of nested classes: _non-static_ (also known as _inner_) nested [classes](https://www.codecademy.com/resources/docs/java/classes), and _static_ nested classes
- Nested classes provide an extra level of security by giving programmers the power to control the amount of access one class may have to another class and its [methods](https://www.codecademy.com/resources/docs/java/methods).
- Non-static (inner) nested classes have the capability of accessing other static and non-static members whereas static nested classes may only access other static members of their enclosing class.
- Shadowing refers to the practice of having [variables](https://www.codecademy.com/resources/docs/java/variables) and methods of the same name exist within nested classes. Shadowing results in overlap, and is managed using the keyword `this` to determine which version of the variable or method is being used.


# Threading

## What is Threading?

### Introduction
For most applications, a primary requirement is that they be _fast_ and _efficient_. To help meet this goal, we have to implement **concurrent programs**. These types of programs can support multiple flows of execution at the same time. This capability can help a programmer write code that completes two or more tasks at the same time!

### What is a thread?
The building blocks of concurrent programs or processes are **threads**. Like sequential programs, a single thread has a beginning and an end, and only a single point of execution. However, multiple threads can run at the same time! A program or process usually has multiple threads running simultaneously, leveraging the context of the program, acting on shared resources between other threads, and ensuring that any one thread does not impede the other threads from completing a task.

We can see that a process can start and execute multiple threads. By default, a process has a single thread of execution called the **main thread**. From that initial thread, we can create more threads to launch different independent tasks. We don’t consider the process to be complete until _all_ of the threads that it has started are finished. When a thread completes its execution, we say that it **joins** back into the main thread.

### When to use threads
Suppose you’re buying some clothes in an online store. When you click a button to add a shirt to your cart, several tasks may need to be performed before it lands there. This might include:

- checking the store’s inventory for that shirt
- making a record in a database to reserve that shirt for you
- seeing if there are any active sales or promotions
- finding other recommended clothing based on your purchase
- and potentially even more tasks!

While all of these are being performed, you would still want to be able to browse the rest of the site, and maybe start your next purchase for a pair of socks too!

Without threading, you would have to wait for all of those tasks to be completed sequentially before being able to perform any other actions on the site. Using a multithreaded program, however, the online store can create and track independent tasks for each of the actions required to add the shirt to the cart, while still allowing you to browse the remainder of the store.

As illustrated by the online store scenario, it is best to use threading when your program has tasks that need to be performed in parallel, and you do not wish for your program’s main thread to become unresponsive or unusable while the tasks are being performed. When a program has the ability to perform more tasks in less time, we say that threading has increased its **throughput**.

### Context of a thread
For a program to execute properly, it needs to have several things in its **context**. A program’s context includes variables, function names, a history of function calls (the “call stack”), and more. A thread that runs within a program has its own context so that it can run independently without impacting other threads.

Sometimes, we have to share some information (a context) between threads as well. For example, in the online store example, each of the threads for the inventory-check task, the recommender task, and the reservation task need to know the product ID number for the shirt. Since all of the threads are launched from the same main thread (starting from when you clicked the “Add to Cart” button), they all have access to the product ID that was present in that main thread’s context.

When reading shared information in a multi-threaded program, there’s usually nothing to worry about in terms of _managing shared state_. However, when multiple threads are _writing_ to the same resource, and manipulating its state, we can run into issues where multiple threads are changing a value based on a potentially out-of-date previous state. The solution to this issue is called thread **synchronization**.


## Threading

### Introduction
Threading can solve problems where there is a lot of waiting to be done. When one task is in a “waiting” or “blocked” state, another one can start. This is useful for programs in which a long-running computation needs to be done, or when a task must wait on a response from an external source such as fetching an image from a server.

### Extending the Thread Class
There are multiple ways to implement [threading](https://www.codecademy.com/resources/docs/java/threading?page_ref=catalog) in Java. The first that we will try involves extending the `Thread` class. In Java, there is a built-in class that handles threads: `java.lang.Thread`. To create a thread, we create a class that extends the built-in `Thread` class and then overrides its `public void run()` method. Beyond these two requirements, the rest of our class can have anything we want in it!

The `public void run()` method that we override performs the actual work that our thread should be responsible for. This may be performing a long-running computation, calling out to another application or service, or other tasks that involve some waiting.

Notice that the `run()` method is a `void` and accepts no parameters. Every `run()` method must be of this signature. If `run()` requires some external information, that information must be a field declared in the class and initialized in the constructor. However, be very careful of using external information as this may present some synchronization issues.

When we defined our class in this way, we can then create an instance of our class in any other part of our program and call `start()` on the instance to trigger the thread’s execution.

Here’s an example of a sequential program in Java that computes the meaning of life:

```java
public class HugeProblemSolver{
 
  public HugeProblemSolver(){
    // Required constructor used for passing information to the start() method.
  }
 
  private static void solveComputation(){
    // Solves random computation
    // Takes anywhere from 1 second to 10 minutes
    System.out.println("The answer is: 42");
  }
 
  public static void main(String[] args){
    HugeProblemSolver.solveComputation();
    HugeProblemSolver.solveComputation();
  }
}
```

In this program, we will only see the answer to the second question _**after**_ the first question has been answered. A threaded solution would allow us to start the computations at the same time, and receive the answers as soon as they are available.

```java
public class HugeProblemSolver extends Thread{
 
  public HugeProblemSolver(){
    // Required constructor used for passing information to the start() method.
  }
 
  private static void solveComputation(){
    // Solves random computation
    // Takes anywhere from 1 second to 10 minutes
  }
 
  @Override
  public void run(){
    solveComputation();
    System.out.println("The answer is: 42");
  }
 
  public static void main(String[] args){
    HugeProblemSolver m1 = new HugeProblemSolver();
    HugeProblemSolver m2 = new HugeProblemSolver();
    m1.start();
    m2.start();
  }
}
```

Now, you can see that all that changed was:

- Extended the `Thread` Class.
- Created and Overrode the `run()` method from `Thread`.
- Instantiated `HugeProblemSolver` and called `start()` which starts a new thread and searches in the class for the `run()` method to execute.

Now, both `Thread`s we created are working on solving their own problems simultaneously. Whichever one finishes first will print to the console first. There is no need to wait on sequential order.

### Implementing the Runnable Interface
In the previous exercise, you learned that we can convert a class to run as a thread by extending the `Thread` class. We can also create threaded [classes](https://www.codecademy.com/resources/docs/java/classes) in Java by implementing the `Runnable` interface.

This approach is preferred because we are only allowed to extend one class, and wasting it on `Thread` might not be beneficial to our program. Here, rather than extending the capability of the built-in `Thread` class, we just want to use its [threading](https://www.codecademy.com/resources/docs/java/threading) capability. Because of this, implementing the `Runnable` interface (which is what the `Thread` class does anyway) and passing in the object into a new `Thread` object is the preferred way of implementing multithreading.

```java
public class Factorial implements Runnable {
 private int n;
 
 public Factorial(int n) {
   this.n = n;
 }
 
 public int compute(int n) {
   // ... the code to compute factorials
 }
 
 public void run() {
   System.out.print("Factorial of " + String.valueOf(this.n) + ":")
   System.out.println(this.compute(this.n));
 }
 
 public static void main(String[] args) {
   Factorial f = new Factorial(25);
   Factorial g = new Factorial(10);
   Thread t1 = new Thread(f);
   Thread t2 = new Thread(f);
   t1.start();
   t2.start();
 }
}
```

A more succinct way of using the `Runnable` interface is to use _lambda expressions_. This is a more modern syntax that allows us to define the `run()` method we want to use inline without requiring the class to implement `Runnable` or extend `Thread`.

```java
public class Factorial {
 public int compute(int n) {
   // ... the code to compute factorials
 }
 
 public static void main(String[] args) {
   Factorial f = new Factorial();
 
   // the lambda function replacing the run method
   new Thread(() -> {
     System.out.println(f.compute(25));
   }).start();
 
   // the lambda function replacing the run method
   new Thread(() -> {
     System.out.println(f.compute(10));
   }).start();
 }
}
```

Behind the scenes, this syntax is still using the `Runnable` interface. This is because Java will translate this _lambda_ syntax into something like this:

```java
new Thread(new Runnable() {
 void run() {
   System.out.println(f.compute(25));
 }
}).start();
```

This syntax has several benefits:

- Our class no longer needs to extend `Thread` OR implement `Runnable`. We can make a thread from anything!
- Our class no longer needs a constructor to store arguments! Since we can pass an argument directly into the compute function when we create our thread, we no longer need to create a separate instance of our object any time we want to perform a threaded task with it.
- Our class is easier to read! The lambda syntax makes it so that people reading our code can immediately identify what task is being performed in our thread without having to read our class first to find the `run()` method.

**Note:** Sometimes you will see developers specifically import the Thread and Runnable classes from `java.lang`. This is not necessary since all Java programs naturally import the `java.lang` package anyway. It is often used to help with readability or remind an author to add a specific feature.

### Supervising a Thread
Sometimes, we want to be able to see the status of threads during their execution. In Java, the best pattern for doing so is to use a **supervisor thread**. This is a pattern where the main thread (or another thread) is able to watch and check on the progress of another thread, as long as it has access to the corresponding `Thread` instance. This kind of thread is implemented just like other threads. Supervisor threads are often used for updating the user of our program on the progress of an ongoing task.

One `Thread` method that a supervisor thread may use to monitor another thread is `isAlive()`. This method returns `true` if the thread is still running, and `false` if it has terminated. A supervisor might continuously poll this value (check it at a fixed interval) until it changes, and then notify the user that the thread has changed state.

```java
import java.time.Instant;
import java.time.Duration;
 
public class Factorial{
 public int compute(int n){
   // the existing method to compute factorials
 }
 
 // utility method to create a supervisor thread
 public static Thread createSupervisor(Thread t){
   Thread supervisor = new Thread(() -> {
     Instant startTime = Instant.now();
     // supervisor is polling for t's status
     while (t.isAlive()) {
       System.out.println(Thread.currentThread().getName() + " - Computation still running...");
       Thread.sleep(1000);
     }
   });
 
   // setting a custom name for the supervisor thread
   supervisor.setName("supervisor");
   return supervisor;
 
 }
 
 public static void main(String[] args){
   Factorial f = new Factorial();
 
   Thread t1 = new Thread(() -> {
     System.out.println("25 factorial is...");
     System.out.println(f.compute(25));
   });
 
 
   Thread supervisor = createSupervisor(t1);
 
   t1.start();
   supervisor.start();
 
   System.out.println("Supervisor " + supervisor.getName() + " watching worker " + t1.getName());
 }
}
```

The thread labeled `supervisor` here is polling the status of `t1` (a “worker” thread) continuously at an interval of 1000 milliseconds (one second). The supervisor checks the status of `t1` using the `isAlive()` method in a `while` loop.

Additionally, the `getName()` method will return a unique name for a thread in the current context. This comes in handy when debugging multi-threaded programs: the programmer can better understand which thread is performing a certain task at a given moment. We can also name a thread ourselves, using the `setName()` method of the `Thread` class.

```java
import java.util.Random;

public class CrystalBall {

  /* Instance Methods */
  public void ask(Question question) {
    System.out.println(Thread.currentThread().getName() + " - Good question! You asked: " + question.getQuestion());
    this.think(question);
    System.out.println(Thread.currentThread().getName() + " - Answer: " + this.answer());
  }

  private void think(Question question) {
    System.out.println(Thread.currentThread().getName() + " - Hmm... Thinking");
    try {
      Thread.sleep(this.getSleepTimeInMs(question.getDifficulty()));
    } catch (Exception e) {
      System.out.println(e);
    }
    System.out.println(Thread.currentThread().getName() + " - Done!");
  }

  private String answer() {
    String[] answers = {
        "Signs point to yes!",
        "Certainly!",
        "No opinion",
        "Answer is a little cloudy. Try again.",
        "Surely.",
        "No.",
        "Signs point to no.",
        "It could very well be!"
    };
    return answers[new Random().nextInt(answers.length)];
  }

  private int getSleepTimeInMs(Question.Difficulty difficulty) {
    switch (difficulty) {
      case EASY:
        return 1000;
      case MEDIUM:
        return 2000;
      case HARD:
        return 3000;
      default:
        return 500;
    }
  }
}
```

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class FortuneTeller {
  
  public static void main(String[] args) {

    List<Question> questions = Arrays.asList(
        new Question(Question.Difficulty.EASY, "Am I a good coder?"),
        new Question(Question.Difficulty.MEDIUM, "Will I be able to finish this course?"),
        new Question(Question.Difficulty.EASY, "Will it rain tomorrow?"),
        new Question(Question.Difficulty.EASY, "Will it snow today?"),
        new Question(Question.Difficulty.HARD, "Are you really all-knowing?"),
        new Question(Question.Difficulty.HARD, "Do I have any hidden talents?"),
        new Question(Question.Difficulty.HARD, "Will I live to be greater than 100 years old?"),
        new Question(Question.Difficulty.MEDIUM, "Will I be rich one day?"),
        new Question(Question.Difficulty.MEDIUM, "Should I clean my room?")
    );

    CrystalBall c = new CrystalBall();
    List<Thread> threads = questions.stream().map(q -> {
      Thread t = new Thread(() -> {
        c.ask(q);
      });
      return t;
    }).collect(Collectors.toList());

    Thread supervisor = createSupervisor(threads);
    threads.stream().forEach(t -> t.start());
    supervisor.start();
  }

  public static Thread createSupervisor(List<Thread> threads) {

    Thread supervisor = new Thread(() -> {
      while (true) {
        List<String> runningThreads = threads.stream().filter(t -> t.isAlive()).map(t -> t.getName()).collect(Collectors.toList());
        System.out.println(Thread.currentThread().getName() + " - Currently running threads: " + runningThreads);
        if (runningThreads.isEmpty()) {
          break;
        }
        try {
          Thread.sleep(1000);
        } catch (InterruptedException e) {
          System.out.println(e);
        }
      }
      System.out.println(Thread.currentThread().getName() + " - All threads completed!");
    });

    // Set the name here...
    supervisor.setName("Supervisor");

    return supervisor;
  };
}
```

### Waiting for Thread Completion
Another common scenario in multi-threaded programs is to wait for a thread to complete before proceeding in a path of execution.

In other languages, this concept is called “awaiting” or “blocking”. In Java, we say that we wait for the thread to **join**.

When a thread joins, it means that the thread’s task is complete and the process that was initially forked off has been “joined” back into the main thread.

This is useful when we can only perform a specific task once several prerequisite tasks have been completed. Take a look at **BurgerMaker.java** in the editor, which describes the process of preparing a cheeseburger. A cheeseburger is generally prepared in the following way:

1. Grill hamburger patty.
2. Once the patty is properly cooked, add cheese on top to melt it.
3. Toast the burger buns.
4. Fry onions.
5. Once all ingredients are ready, assemble the burger.

Many of these steps can be done concurrently. However, notice that some of the steps are dependent on the completion of other steps. Step 2 requires the patty to be grilled before melting cheese on top of it. Step 5 requires all other steps to be completed before it can start (we can’t assemble a burger until everything is ready).

In `BurgerMaker`, we can see how `join()` is used to enforce dependencies between different tasks. By using `start()` and `join()` properly, we can ensure that tasks that can be performed concurrently are started. Still, tasks with dependencies are not started until all dependencies have been joined.

```java
import java.lang.Thread;
public class BurgerMaker {
 
 public void toastBuns() {
   try {
     System.out.println("Toasting buns...");
     Thread.sleep(2000);
   } catch (InterruptedException e) {
     System.out.println(e);
   }
 }

 public void grillPatty() {
   System.out.println("Grilling patty...");
   Thread.sleep(1500);
 }

 public void meltCheese() {
   System.out.println("Melting cheese...");
   Thread.sleep(800);
 }

 public void fryOnions() {
   System.out.println("Frying onions...");
   Thread.sleep(1000);
 }

 public void assembleBurger() {
   System.out.println("Assembling burger...");
   Thread.sleep(1500);
 }

 public static void main(String[] args) {
   BurgerMaker burgerMaker = new BurgerMaker();
   Thread t1 = new Thread(() -> burgerMaker.toastBuns());
   Thread t2 = new Thread(() -> burgerMaker.grillPatty());
   Thread t3 = new Thread(() -> burgerMaker.meltCheese());
   Thread t4 = new Thread(() -> burgerMaker.fryOnions());
   Thread t5 = new Thread(() -> burgerMaker.assembleBurger());
 
   t1.start();
   t2.start();
   t4.start();
   t2.join(); // must grill patty before melting cheese on it
   t3.start(); // ready to melt cheese
   t1.join();
   t3.join();
   t4.join();
   // must complete all other steps before assembling burger
   t5.start();
   t5.join(); // waiting for the burger assembly task to complete
   System.out.println("Burger complete!");
 }
 
}
```

### Thread Synchronization
Another important scenario when working with multi-threaded programs is _managing shared resources_ between threads.

When we access the same data from two different threads, we may cause a _race condition_. A race condition occurs when some inconsistency is caused by two threads trying to access the same shared data at the same time. Consider this example where two threads are attempting to increment a value simultaneously:

```java
class IntegerMapper{
  public int[] array = {1, 2, 3, 4, 5};    
  public void incrementElement(int i, int j){
    array[i] += j;
  }   
}
public class Main{
  public static void main(String args[]) throws InterruptedException{
    IntegerMapper iMapper = new IntegerMapper();
    Thread thread1 = new Thread(() -> {
      for(int i = 0; i < 100; i++){
        iMapper.incrementElement(2, 4);
        try{
          Thread.sleep(10);
        }
        catch(InterruptedException exception){
          System.out.println("Error!");
        }
      }
 
    });
    Thread thread2 = new Thread(() -> {
      for(int i = 0; i < 100; i++){
        iMapper.incrementElement(2, 3);
        try{
          Thread.sleep(10);
        }
        catch(InterruptedException exception){
          System.out.println("Error!");
        }
      }
    });
 
    thread1.start();
    thread2.start();
 
    thread1.join();
    thread2.join();
 
    System.out.println(iMapper.array[2]);
  }
}
```

If we run this program multiple times, we will get a different [output](https://www.codecademy.com/resources/docs/java/output) each time! This is because `thread1` and `thread2` conflict in their access of `array[2]`. To update the value in the `incrementElement()` method, the value must be read, incremented, then saved. One thread could be reading the value while the other thread is incrementing it, leading to inconsistencies.

We can prevent race conditions on shared data by using the `synchronized` keyword in Java. In a threaded program, when we add `synchronized` to the definition of a function, it will ensure that for a given instance of a class, only one thread can run that method at a time. We can fix `incrementElement()` by making it `synchronized` like so:

```java
public synchronized void incrementElement(int i, int j){
    array[i] += j;
}
```

Now, each time the program is run, it will output the same value.

### Communicating Between Threads
Previously, we learned how to block thread execution using `join()`. However, this is only to block thread execution from the context where the thread was started. For example, if a thread was created and started in the main thread, we can only call `join()` on it from the main thread and wait on its completion from there.

In Java, to control thread execution from within other threads, we can use the `wait()`, `notify()`, and `notifyAll()` [methods](https://www.codecademy.com/resources/docs/java/methods). These are primarily used to protect shared resources from being used by two threads at the same time or to wait until some condition has changed in a thread.

When using `wait()` and `notifyAll()`, it is important to do so in a `synchronized(this)` block. When we create a `synchronized(this)` block, we are telling Java that we want it to be the only thread accessing the fields of the class at a given moment. In the `synchronized(this)` block, we must:

1. Check the condition on which to wait.
2. Decide whether to `wait()` (block the execution of the current thread) or `notifyAll()` (allow other threads to check their condition again and proceed)

```java
import java.lang.Thread;
 
public class OrderDinnerProcess {
 private boolean foodArrived = false;
 
 private void printTask(String task) { 
   System.out.println(Thread.currentThread().getName() + " - " + task);
 }
 
 public void eatFood() {
   printTask("Wow, I am starving!");
   try {
     synchronized (this) {
       while (!this.foodArrived) {
         printTask("Waiting for the food to arrive...");
         wait();
       }
     }
   } catch (InterruptedException e) {
     System.out.println(e);
   }
   printTask("Finally! Yum yum yum!!!");
 }
 
 public void deliverFood() {
   printTask("Driving food over...");
   try {
     Thread.sleep(5000);
     synchronized (this) {
       this.foodArrived = true;
       printTask("Arrived!");
       notifyAll();
     }
   } catch (InterruptedException e) {
     System.out.println(e);
   }
 }
 
 public static void main(String[] args) {
   OrderDinnerProcess p = new OrderDinnerProcess();
   try {
     for (int i = 0; i < 5; i++) {
       Thread eatFood = new Thread(() -> p.eatFood());
       eatFood.start();
     }
     Thread.sleep(1000);
     Thread delivery = new Thread(() -> p.deliverFood());
     delivery.start();
   } catch (InterruptedException e) {
     System.out.println(e);
   }
 }
}
```

In the example, we are simulating a family of five eager to eat some dinner! However, they can’t eat until the food has arrived. We could have controlled this behavior before by defining, starting, and joining the `delivery` thread before the five `eatFood()` threads began. However, using `wait()` and `notifyAll()`, we can start them in any order, and each `eatFood()` thread will `wait()` until a call to `notifyAll()` by another thread tells them to proceed to check again.

The `synchronized` block is used here to tell Java that only one thread should be able to read from and write to the `foodArrived()` field at a time.

The `wait()` function is used to pause execution for a thread until a call has been made to `notifyAll()`, which triggers another check of the condition.

The `notifyAll()` function is used to tell all threads that are currently waiting that they may now proceed.

In addition to being used to coordinate thread execution, we can use the `synchronized(this)` block, `wait()`, and `notifyAll()` to control access to shared resources. If a resource is currently in use, a thread should `wait()` until a call to `notifyAll()` is made, which indicates that the shared resource _may_ have been released and is ready for use.
### Review
So far, you have:

- created threads in three different ways:
    - extending the `Thread` class
    - implementing the `Runnable` class
    - using the in-line, lambda expression syntax
- started threads with `.start()`
- paused the execution of threads using `Thread.sleep(long millis)`
- observed thread execution using the _supervisor pattern_
- blocked on thread completion with [`.join()`](https://www.codecademy.com/resources/docs/java/strings/join)
- synchronized access to shared resources from threads with the `synchronized` keyword
- communicated between threads with `.wait()` and `.notify()`


# Regular Expressions

## Regular Expressions

### Introduction to Regex
A regex is a pattern represented by a sequence of characters. They’re used in search engines, word processors, text editors, and many other places due to their general use cases and base functionality. Many programming languages provide regex capabilities either from libraries or built straight into the language. Java is one such language that has an entire package dedicated to regex.

In the simplest sense, regex can be used to perform text search and text replace operations. It’s always first represented as a _search pattern_, which is used to define what exactly is being searched for when scanning text. In all regards, search patterns put an emphasis on precision despite the “catch-all” genericness it has to consider.

Regex can be broken into the following categories:

- Character [Classes](https://www.codecademy.com/resources/docs/java/classes) and Capture Groups
- Escaped Characters
- Quantifiers
- Alternation

Java doesn’t have a built-in regex class, so we import a `java.util.regex` package to work with [regular expressions](https://www.codecademy.com/resources/docs/java/regular-expressions).

### The Pattern Class
Java’s `java.util.regex` package contains two vital classes:

- `Pattern` Class
- `Matcher` Class

We’ll start with the `Pattern` class which is what we use to define a pattern we want to find in a string. We create a `Pattern` like so:

```java
Pattern pattern = Pattern.compile("Codecademy");
Pattern pattern = Pattern.compile("codecademy", Pattern.CASE_INSENSITIVE);
```

This method compiles a pattern object in such a way as to designate a given string as the pattern to be used to perform regex operations.

Note the second parameter. It’s optional but contains some useful flags we can set that affect how the regex search is performed. Some examples include:

- `Pattern.CASE_INSENSITIVE` - The case of letters will be ignored when performing a search.
- `Pattern.LITERAL` - Special characters in the pattern will not have any special meaning and will be treated as ordinary characters when performing a search.
- `Pattern.UNICODE_CASE` - Use it together with the `CASE_INSENSITIVE` flag to also ignore the case of letters outside of the English alphabet.

To match a string against a pattern, we need to use the `Matcher` class.

### The Matcher Class
The `Matcher` class is Java’s “search” feature, allowing it to take a regular expression defined by the `Pattern` class and perform a search based on a compiled pattern. The syntax for the `Matcher` class is as follows:

```java
Pattern pattern = Pattern.compile("Codecademy"); 
 
// String to match: "Welcome to Codecademy!"
Matcher matcher = pattern.matcher("Welcome to Codecademy!"); 
```

Note that the `Pattern` object is called when using the `matcher()` method.

The `matcher()` method used by a `Pattern` object returns a `Matcher` object with information about the search. We can then use this `Matcher` object to sift through that information in various ways, with many [methods](https://www.codecademy.com/resources/docs/java/methods) within the `Matcher` class at our disposal. We’ll start by talking about the two most useful methods:

```java
boolean matchFind = matcher.find();
boolean matchExact = matcher.matches();
```

In the above two methods, `find()` searches the string for the next match based on the pattern and returns `true` if it finds an occurrence of it. For example, if the string is “Codecademy” and the pattern is “cad”, `find()` will return `true`. The `find()` function retains a pointer to indicate where it should start searching in the text. The pointer initially starts at the beginning of the text and stops at the next character after matching. If `Matcher` is not reset, the next time `find()` is called it will start searching where it left off. Example:

```java
Pattern pattern = Pattern.compile("ABC"); 
Matcher matcher = pattern.matcher("ABCdefgABCdefAB");
 
matcher.find() // Starting at index 0 - return true
matcher.find() // Starting at index 4 - return true 
matcher.find() // Starting at index 11 - return false
```

This is useful if we are trying to count the number of occurrences of a substring.

The `matches()` function returns `true` if the string matches exactly the pattern with no other characters in the string. Note: this does not necessarily mean that the [strings](https://www.codecademy.com/resources/docs/java/strings) must be the same.

The `Matcher` class also includes methods to find and replace text, create search regions, append text, display how the matcher is interpreting the pattern, and many more functional and very useful utilities.

### Character Classes
Character [classes](https://www.codecademy.com/resources/docs/java/classes) are one of the primary means of “grouping” characters in a regex pattern without necessarily enforcing an order to those characters. For instance, a character class marks the difference between searching for a specific word and searching for any occurrence of any characters found in that word.

A **character class** matches a character from a specific set, including predefined character classes and custom user-defined sets. The following are examples of how character classes are used (note that any references to “abc” are just examples. These are user-defined, so anything can be used):

|Character Class|Description|
|---|---|
|`[abc]`|Includes any of the contained characters|
|`[^abc]`|Excludes all of the contained characters|
|`[a-z]`|Includes any of the contained characters across a range|
|`.`|Any character except newline|
|`\w`|Any word character (alphanumeric and underscore)|
|`\d`|Any digit [0-9]|
|`\s`|Whitespace (spaces, tabs, line breaks)|

These can all be defined as or included in a regex search pattern. Let’s go over a quick example using a character class. Suppose the following is your search pattern:

```java
Pattern pattern = Pattern.compile("[ABCDQ]");
```

The above pattern first creates a character class that checks for any letters from the set {A, B, C, D, Q}.

To see this in action, consider the example of counting the total number of occurrences of characters “B”, “C” and “N” in the string “A BANANA CAN FLY BETTER THAN A BIRD”:

```java
import java.util.regex.*;
public class Main {
  public static void main(String args[]){
    Pattern pattern = Pattern.compile("[BCN]");
    Matcher matcher = pattern.matcher("A BANANA CAN FLY BETTER THAN A BIRD");                                                                                                        
    int count = 0;
    while(matcher.find())count++;
    System.out.println(count); 
  }
}
```

The [output](https://www.codecademy.com/resources/docs/java/output) of this program will be 8.

### Capture Groups and Escaped Characters
Capture groups maintain the order but allow you to section the pattern and allow for substring searching.

The following is known as a capture group (note the “aab” here is user-defined, so anything can be used):

|Capture Group|Description|
|---|---|
|(aab)|Groups tokens together and creates a capture group|

Grouped tokens can be used for extracting a substring.

```java
Pattern pattern = Pattern.compile("(co)+");
```

Here, the “+” is known as a quantifier (these are covered in a later exercise). The “+” means “occurring 1 or more times”.

The above regex pattern matches any text that contains the character combination “co” one or more times. What this will actually match could look like “co” but it would also match with the following: “coco”, “cococo”, “cocococo”, etc.

Character classes and capture groups may look a little similar but just remember: `[]` denotes character class and `()` denotes capture group.

The `\` is called an **escape character**, which when used in this manner, helps define special characters with special functions. For example, “\n” represents a new line, and “\s” represents a white space. Here are some others:

|Escaped Character|Description|
|---|---|
|`\.`|Escaped period|
|`\*`|Escaped asterisk|
|`\\`|Escaped backslash|
|`\t`|Tab|
|`\n`|Newline or linefeed|
|`\r`|Carriage return|

For example, to search for the `.` to mark the end of a sentence without regex trying to interpret it as “any character except newline”, we use “\.” in the pattern.

Escaped characters insert reserved, special, and Unicode characters into the regex pattern. All escaped characters begin with the `\` character, which also allows the pattern to search for special characters without enacting their special properties by treating the special character as plaintext.

### Quantifiers
Quantifiers look at preceding tokens and indicate how many matches to look for, defaulting to trying to match as many characters as possible unless otherwise defined. The following are examples of quantifiers (note that “a” is user-defined and can be any character or group of characters. Any numerical digits used are also user-defined):

|Quantifier|Description|
|---|---|
|`a*`|0 or more|
|`a+`|1 or more|
|`a?`|0 or 1|
|`a{5}`|Exactly five|
|`a{3,}`|Three or more|
|`a{1,3}`|Between one and three|
|`a+?`|Match as few as possible|
|`a{2,}?`|Match as few as possible with a lower bound|

Patterns with quantifiers are generally straightforward. All they do is grab and group the quantified amount of characters together when found.

```java
Pattern pattern = Pattern.compile("a*b");
```

This pattern searches for text that includes 0 or more “a”s followed by a “b.” It’ll find any “ab,” “aab,” “aaaaaaab,” but also, because it can match any text that has 0 “a”s followed by a “b,” it will also find “b.”

### Alternation
_Alternation_ is just the [regex](https://www.codecademy.com/resources/docs/general/regular-expressions?page_ref=catalog) way of saying OR. In regex, this is denoted by the following (note the “ab” and “cd” are user-defined):

|Alternation|Description|
|---|---|
|`ab\|cd`|Match `ab` OR `cd`|

The use of alternation works just like the boolean OR. The pattern will search for any text that matches either alternated pattern and only return nothing if neither is found. Otherwise, this pattern will group either match in the search results regardless of which pattern matched.

Alternation is also found implicitly in character [classes](https://www.codecademy.com/resources/docs/java/classes). For instance, a character class like `[A-Z]` grabs a range of characters. This is the equivalent of grabbing `A` OR `B` OR `C` and so on.

This just allows you to get a bit more complicated, especially if you want to look for slight differences between words that share a pattern. For instance, when looking at code, someone might type the following in two possible ways:

```java
i < 10
10 > i
```

Both ways are technically correct and produce the same result. So to make a regex pattern accept both when looking for the same technical thing, you can write a pattern for each and just alternate it with an `|` to ensure you’re finding both feasible ways to write the same code.


# JUnit Testing

## JUnit Testing

### Introduction to JUnit
_JUnit_ testing operates in a Test Driven Development setting, or _TDD_, usually utilized specifically in “test-first” programming. Java programming as a whole is often synonymous with TDD due to the incorporation of JUnit.

As you learn more about what JUnit is and how it works, you’ll pick up a particular mantra along the way:

**“Red — Green — Refactor!”**

JUnit is a [unit testing](https://www.codecademy.com/resources/docs/general/unit-testing?page_ref=catalog) framework for Java that tests the functionality of an application to ensure it runs as expected. The “units” being tested are single entities, like [classes](https://www.codecademy.com/resources/docs/java/classes?page_ref=catalog) and [methods](https://www.codecademy.com/resources/docs/java/methods?page_ref=catalog).

Programmers write JUnit tests for quality reasons, but they also do so to reduce stress and the time spent debugging code. Proper testing practices can not only keep code organized and maintain a solid direction, but it also ensures maintainability in the future and is friendly to a team-based setting.

### JUnit Classes and Methods
JUnit testing takes place in a traditional Java [class](https://www.codecademy.com/resources/docs/java/classes?page_ref=catalog), just like the classes written for the application you want to test. The functionality for those tests comes from JUnit classes, most commonly the `Assert` class and annotation classes.

“Annotating” is a general term that refers to ways of marking [methods](https://www.codecademy.com/resources/docs/java/methods) for testing, changing how these methods are compiled, and establishing when they’ll be run by the [compiler](https://www.codecademy.com/resources/docs/java/compiler). The four most essential annotations are `@Before`, `@Test`, `@After`, and `@Ignore`.

The above annotations can be imported in the following ways:

```java
import org.junit.Before;
import org.junit.Test;
import org.junit.After;
import org.junit.Ignore;
```

Additionally, the following line will grab all functionality from the Assert class library, but note that each assert method can be imported individually:

```java
import static org.junit.Assert.*;
```

### @Test-ing, @Test-ing, 1 2 3
`@Test` will be the bulk of any JUnit testing. Anything that needs to be “checked” and “verified” will likely occur within a method marked with the `@Test` annotation.

A test method looks like this:

```java
@Test
public void test() {
  // Test cases
}
```

The way this method functions is atypical of [methods](https://www.codecademy.com/resources/docs/java/methods) found in traditional Java [classes](https://www.codecademy.com/resources/docs/java/classes). These `@Test` annotated methods will _always_ run unless otherwise annotated as `@Ignore`, which tells the [compiler](https://www.codecademy.com/resources/docs/java/compiler) to skip over that particular method. These test methods also don’t have to be called, as they’re automatically detected and run by the compiler.

Typically, there will be a test method for every class object and class method in the program. For instance, if a method exists called `takeDamage()`, there will often also be a `testTakeDamage()` test method verifying the functionality of that method.

The word **coverage** may arise at some point during a programmer’s testing journey, which in the case of JUnit just means “test coverage.” In other words, it asks the question “how much of the code is actually tested?” Or in other _other_ words, “do the test methods touch all of the code?” A good program will have full coverage.

Most Java IDEs will make it easy to detect coverage, often supporting ways to visibly see all the code touched by testing and all the code missed. Eclipse, an example of a Java IDE, does this by tinting the code green or red depending on whether or not a test case hits that area of the program.

The test cases themselves, regardless of the coverage algorithm, will actually follow a similar color pallet when run. JUnit makes it a standard to use the colors **green** and **red** to indicate whether or not a test method passes or fails. A test will go green if it passes, and red otherwise.

Programmers have created a mantra around this JUnit standard: “Red — Green — Refactor!”

This mantra emphasizes the “test-first” approach to programming. In the simplest sense, this just means that a program’s tests are written before the code is made.

“Red” is the start of the mantra and the first thing a programmer needs to do in test-first development. In other words, a programmer needs to write a test and make it go red as the first step for testing.

The act of doing this establishes a test to exist first, which is good practice for coverage but also lays the requirements for the code. A skeleton of the method they want to be testing is then created, which often will be set to return `0` (or some other arbitrary value) to ensure the test has something to compare against. This arbitrary value will be different from what the test is “expecting” and make the test go red.

“Green” is the second step of the mantra. Now that we have our red test, we can write code into the skeleton method to make it work. We then run the test again and watch the test method go green.

These two steps help ensure the following things: we have good test coverage, our tests are testing what they should be testing, and the code works as expected.

The last step of the mantra is “Refactor,” which is often the last “clean-up” step of any coding. This step cleans up and polishes the code now that its bare minimum processing is tested and functional.

### @Test Methods and Asserts
A typical `@Test` method involves **assertions**.

Assertions are found in the `junit.org.Assert` class library. Each “assert” is a way to perform a specific test in JUnit testing.

Below are a couple of common assert [methods](https://www.codecademy.com/resources/docs/java/methods) (note: they all have a return type of `void`):

|Assert Method|Description|
|---|---|
|`assertEquals(expected, actual)`|Checks if two values are equal|
|`assertNotEquals(expected, actual)`|Checks if two values are not equal|
|`assertTrue(boolean condition)`|Checks if a condition is `true`|
|`assertFalse(boolean condition)`|Checks if a condition is `false`|
|`assertNotNull(Object object)`|Checks if an object isn’t `null`|
|`assertNull(Object object)`|Checks if an object is `null`|
|`assertArrayEquals(expectedArray, actualArray)`|Checks if two [arrays](https://www.codecademy.com/resources/docs/java/arrays) are equal|

When called, each “assert” is considered as a test case by the [compiler](https://www.codecademy.com/resources/docs/java/compiler), and any given assert can either pass or fail. A `@Test` method can only pass if all test cases inside of it pass. If any case fails, the whole test method will be marked red and considered a failed test.

Suppose we have a class object called `Human`. We assign that object a `name`, represented by a string, and an integer value to represent their `hitpoints` upon creation.

```java
Human sam = new Human("Sam", 100);
```

We want to test whether or not Sam gets properly created and also test a `takeDamage()` method within the `Human` class to ensure any damage taken is being recorded. Because this implies two different tests, let’s create two different test methods:

```java
@Test
public void testHuman() {
  Human sam = new Human("Sam", 100);
  assertEquals(100, sam.getHitpoints());
  assertEquals("Sam", sam.getName());
}
 
@Test
public void testHumanTakeDamage() {
  Human sam = new Human("Sam", 100);
  assertEquals(100, sam.getHitpoints());
  sam.takeDamage(10);
  assertEquals(90, sam.getHitpoints());
}
```

Take note that `assertEquals()` is overloaded to account for different variable types.

Each assert method is a tool a programmer can use to uniquely test their code. They typically follow the pattern of “expected value first,” then find the “actual” value in the second parameter to check against the expected.

There are a few exceptions to this rule. When checking a boolean or an object’s existence, one parameter is used. When checking a decimal value, a third parameter (range) can be included to indicate that a value plus or minus this range is considered passable.

```java
assertEquals(25.5, sam.calculateDamage(), 0.9);
```

This will pass if `sam.calculateDamage()` returns a value anywhere within the range of `24.6` and `26.4`.

---

Hamcrest example of an `assertEquals(expected, actual)`:

```java
assertThat(actual, equalTo(expected));
```

The above will always use the following imports:

```java
import static org.junit.Assert.fail;
import static org.hamcrest.MatcherAssert.assertThat;
import static org.hamcrest.CoreMatchers.equalTo;
```

### @Before We Go Further
The `@Before` annotation can be used to accompany the `@Test` [methods](https://www.codecademy.com/resources/docs/java/methods). Methods tagged with `@Before` will run before each test method and look like the following:

```java
@Before
public void beforeEachTest() {
  // Something multiple tests use
}
```

They’re typically used if multiple test methods share a similarly created object or set of [variables](https://www.codecademy.com/resources/docs/java/variables). Placing those inside the `@Before` annotated method ensures those objects are always freshly created and have the same starting attributes upon instantiation. This allows each test to work with those objects and variables without needing to create them inside their test bodies.

If we look at the example we covered in the previous exercise, we created the `Human` named “Sam” twice in the exact same fashion. Now that we know about the `@Before` annotation, we could instead place the creation of `sam` inside of the `@Before` method:

```java
Human sam;
 
@Before
public void createSam() {
  sam = new Human("Sam", 100);
}
 
@Test
public void testHuman() {
  assertEquals(100, sam.getHitpoints());
  assertEquals("Sam", sam.getName());
}
 
@Test
public void testHumanTakeDamage() {
  assertEquals(100, sam.getHitpoints());
  sam.takeDamage(10);
  assertEquals(90, sam.getHitpoints());
}
```

This is different from just making `sam` a class variable, which is also visible by all tests because the `@Before` will be re-run _before_ each test. This means if tests modify the `sam` variable in any way, it ensures `sam` gets reset before the next test runs.

There’s another variant of the `@Before` annotation that will let us create a method that will run one time before _all_ tests instead of multiple times before _each_ test. This is done by using the `@BeforeClass` annotation.

`@Before` and `@BeforeClass` both have their unique uses, making them valuable tools for JUnit testing.

### The @After-math
The `@After` annotation acts just like the `@Before` but will run _after_ each test method. Particularly if this cleanup needs to occur after each test.

```java
@After
public void afterEachTest() {
  // Cleanup
}
```

`@After` is used for cleaning up [variables](https://www.codecademy.com/resources/docs/java/variables) and objects, and freeing memory. If a file needs to be closed, an object needs to be removed, or an environment or array needs to be emptied, this is perfect.

If the cleanup needs to happen only once after all of the tests conclude, much like `@BeforeClass`, an `@AfterClass` annotation exists for this purpose. This will ensure the method runs after all tests within the class have already run.

```java
// Test imports
import org.junit.Test;
import org.junit.Before;
import org.junit.After;
import static org.junit.Assert.fail;
import static org.hamcrest.MatcherAssert.assertThat;
import static org.hamcrest.CoreMatchers.equalTo;
// File imports
import java.io.File;
import java.io.FileWriter;
import java.util.Scanner;
// Possible exceptions to detect
import java.io.IOException;

public class TestExample {
  static File file;
  static FileWriter w;
  static Scanner s;

  @Before
  public void beforeEachTest() throws IOException {
    file = new File("test.txt");
    w = new FileWriter("test.txt");
    s = new Scanner(file);
  }

  @Test
  public void test1() throws IOException {
    w.write("Testing testing 1 2 3!");
    w.close();
   
    assertThat(s.nextLine(), equalTo("Testing testing 1 2 3!"));
  }

  @Test
  public void test2() throws IOException {
    w.write("Poking poking 4 5 6!");
    w.close();
   
    assertThat(s.nextLine(), equalTo("Poking poking 4 5 6!"));
  }

  @After
  public void afterEachTest() throws IOException {
    s.close();
  }
}
```

### Running With the @Suite-s
Getting the `@Before`, `@Test`, and `@After` [methods](https://www.codecademy.com/resources/docs/java/methods) all put together and tied up in a neat test class is the basis for JUnit testing. However, there’s one more step a programmer can take to apply one last layer of organization.

Test suites.

A **test suite** is a way to bundle JUnit test [classes](https://www.codecademy.com/resources/docs/java/classes) and run them together. The `@RunWith` and `@Suite` annotations are used to accomplish this, and they look like the following:

```java
@RunWith(Suite.class)
@Suite.SuiteClasses({
  // List of test classes to bundle together
})
 
public class MyTestSuite {
}
```

The above `MyTestSuite` class doesn’t need anything within the class itself to run. It instead will be called via some sort of “runner” class in the following way:

```java
import org.junit.runner.JUnitCore;
import org.junit.runner.Result;
import org.junit.runner.notification.Failure;
 
public class TestSuiteRunner {
  public static void main(String [] args) {
    Result result = JUnitCore.runClasses(MyTestSuite.class);
 
    for (Failure failure : result.getFailures()) {
      System.out.println(failure.toString());
    }
 
    System.out.println(result.wasSuccessful());
  }
}
```

The runner will typically always look the same and can be used to run multiple different test suites depending on which test classes a programmer wants to bundle together. The `Result` and `Failure` imports are ways to gather and print the results of all the test cases run within the bundled test classes.

However, this feels like an overcomplicated way to run all of your tests, right? Ordinarily, test suites aren’t conducive to JUnit testing and aren’t always used or needed. However, there are valid reasons for a test suite to be used.

Consider the following scenario: A programmer builds an environment and fills it with objects for testing. Tests have to be done to make sure those objects made it into the environment without problems, and then more tests are done to manipulate those objects within the environment to make sure they can interact with each other. A final test empties the environment and makes sure everything gets cleaned up.

Without a test suite, multiple test classes that interact with this environment would need to recreate both the environment and the objects within that environment between test classes. This could get time-consuming with enough test classes and a large enough environment for testing.

With a test suite, one environment can be created and all of the test classes can interact with it accordingly. The last test class bundled into the suite can then handle the cleanup.

In retrospect, a test suite is really just another way to apply the `@Before` and `@After` methodology to testing, but on a larger class-based scale. It’s not always useful, but when it is, it’s _really_ useful.

```java
import org.junit.runner.RunWith;
import org.junit.runners.Suite;
import org.junit.runners.Suite.SuiteClasses;
 
import TestOne;
import TestTwo;

@RunWith(Suite.class)
@Suite.SuiteClasses({
  TestOne.java,
  TestTwo.java
})
 
public class MyTestSuite {
}
```

- JUnit testing makes sure we have good test coverage across a program’s code and verifies everything is working as expected.
- How to write `@Test` [methods](https://www.codecademy.com/resources/docs/java/methods) and their incorporations of the `Assert` class library.
- How to write `@Before` methods and why they’re useful.
- How to write `@After` methods and why they’re useful.
- What test suites are and what they’re used for.
- “Red — Green — Refactor!”


## JUnit 4 vs JUnit 5
JUnit testing opens a lot of doors for scalability and quality control. Well-written tests can often act as documentation in and of themselves, showing a programmer what a line of code or method should be doing at any given time.

Traditionally, JUnit 4 is more commonly used in general programming. While JUnit 4 laid the groundwork for JUnit testing, JUnit 5 adopted new Java 8 coding styles and aimed to be more robust and flexible than its previous iteration.

### Different Annotations
The annotations between the two versions are mostly the same, but with some differences.

|JUnit 4|JUnit 5|Functionality|
|---|---|---|
|`@Test`|`@Test`|Declare a test method|
|`@BeforeClass`|`@BeforeAll`|Execute before all test methods in the current class|
|`@AfterClass`|`@AfterAll`|Execute after all test methods in the current class|
|`@Before`|`@BeforeEach`|Execute before each test method|
|`@After`|`@AfterEach`|Execute after each test method|
|`@Ignore`|`@Disabled`|Disable a test method/class|
|N/A|`@TestFactory`|Test factory for dynamic tests|
|N/A|`@Nested`|Nested tests|
|`@Category`|`@Tag`|Tagging and filtering|
|N/A|`@ExtendWith`|Register custom extensions|

### Other major JUnit 4 vs JUnit 5 differences

#### Architecture
While JUnit 4 bundles everything it has into a single jar file, JUnit 5 breaks itself up into 3 sub-projects: JUnit Platform, JUnit Jupiter, and JUnit Vintage.

- **JUnit Platform**: Defines the TestEngine API for developing new testing frameworks that run on-platform.
- **JUnit Jupiter**: Entirely new JUnit annotations and TestEngine implementation to apply those new annotations.
- **JUnit Vintage**: Supports JUnit 3 and JUnit 4 on the JUnit 5 platform.

#### JDK Version
JUnit 4 requires at minimum Java 5, or any higher version. JUnit 5 requires Java 8 or higher.

#### Asserts
JUnit 4 supports a way to incorporate an error message into all assert methods as the first argument, the message of which would print if a test fails.

```java
public static void assertEquals(long expected, long actual)
public static void assertEquals(String message, long expected, long actual)
```

JUnit 5 changed the class name, now called “Assertions,” and added new `assertThrows()` and `assertAll()` methods. The new version also changed where the error message is inserted into the assert methods and added a third overloaded method with a way to print the supplier of the message.

```java
public static void assertEquals(long expected, long actual)
public static void assertEquals(long expected, long actual, String message)
public static void assertEquals(long expected, long actual, Supplier messageSupplier)
```

#### Assumptions
JUnit 4 supports five `org.junit.Assume` methods, while JUnit 5 supports three.

- **JUnit 4**: `assumeFalse()`, `assumeNoException()`, `assumeNotNull()`, `assumeThat()`, `assumeTrue()`
- **JUnit 5**: `assumeFalse()`, `assumeThat()`, `assumeTrue()`

#### Test Suites
Both JUnit 4 and JUnit 5 have ways to use test suites for testing, but the syntax has been changed for JUnit 5.

JUnit 4 uses `@RunWith` and `@Suite`.

```java
import org.junit.runner.RunWith;
import org.junit.runners.Suite;
 
@RunWith(Suite.class)
@Suite.SuiteClasses({
   // List of classes
})
```

JUnit 5 uses `@SelectPackages` and `@SelectClasses`.

```java
mport org.junit.platform.runner.JUnitPlatform;
import org.junit.platform.suite.api.SelectPackages;
import org.junit.runner.RunWith;
 
@Suite
@SelectPackages("com.package.path")
```

JUnit 5 uses a way to locate the package containing the test classes intended to be run in the test suite, which simplifies the overall process and doesn’t require a hardcoded list like JUnit 4 uses.

#### Non-public vs Public Test Methods
JUnit 4 has always required its test classes and methods all be public. JUnit 5 changed this to now allow them to be package protected and private. It does this by using “reflection,” which allows JUnit 5 to discover non-public classes and methods despite the limited visibility.

This effect also extends to the constructors within the test classes, and allows the constructors to accept arguments now. JUnit 4 required a public no-argument constructor, whereas JUnit 5 does not.

#### 3rd Party Integration
No integration support exists in JUnit 4 for third-party plugins or IDEs. JUnit 5, however, has a dedicated sub-project, JUnitPlatform, for this purpose which uses the TestEngine API defined inside it.


## JUnit Testing in your Environment

### To IDE or not to IDE
Terminal compilation of Java projects is fairly straightforward but requires references to the JUnit directory and careful directory management for where your files are stored. Working entirely in this setting is preferable for some, especially due to the control it provides over the compilation process, but as projects scale larger it can start becoming a bit more tricky to upkeep.

This is where Java IDEs come in.

An **IDE** is an integrated development environment software for building applications that combine common developer tools into a single graphical user interface (GUI).

IDEs typically consist of some combination of three necessary components:

- a source code editor
- local build automation
- a debugger

Eclipse and IntelliJ are two popular Java IDEs.

### Eclipse
The **“Red — Green — Refactor”** mantra is a cemented practice in Test Driven Development, so much so that certain IDEs visually color the outputs of their tests to match this fashion.

Eclipse is one such IDE. It does this by tinting failed tests red and tinting passed tests green. When a test is run, it also graphically creates a “progress bar” that reflects the testing being performed. To this effect, the bar will steadily fill with green until it either hits a red test and turns red or completes and finishes with a solid green bar, thus indicating all tests have passed.

The IDE also provides details on which tests ran and whether or not they each individually passed, allowing you to track down which particular test was the one that failed. Details on the manner of the testing are also provided, for instance, what the “actual” value was that came out of the calculation and what the test was “expecting” it to be based on your assert statements.