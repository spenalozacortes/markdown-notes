# Hello World
## Hello World

### Introduction to Java
Sun Microsystems released the Java programming language in 1995. Java is known for being simple, portable, secure, and robust. 

One reason people love Java is the Java Virtual Machine, which ensures the same Java code can be run on different operating systems and platforms. Sun Microsystems’ slogan for Java was “write once, run everywhere”.

```java
public class HelloWorld {
  public static void main(String[] args) {
    System.out.println("Hello World!");
  }
}
```

### Hello Java File!
Java files have a **.java** extension. 

Inside **HelloWorld.java**, we had a class:

```java
public class HelloWorld {
 
}
```

We’ll talk about classes more in the future, but for now think of them as a **single** concept.

The `HelloWorld` concept is: Hello World Printer.

We marked the domain of this concept using curly braces: `{}`. Syntax inside the curly braces is part of the class.

Each file has one primary class named after the file. Our class name: `HelloWorld` and our file name: **HelloWorld**. Every word is capitalized.

Inside the class we had a `main()` *method* which lists our program tasks:

```java
public static void main(String[] args) {
 
}
```

Like classes, we used curly braces to mark the beginning and end of a method.

`String[] args` is a placeholder for information we want to pass into our program.

Our program also displayed the text `"Hello World"` on the screen. This was accomplished using a print statement:

```java
System.out.println("Hello World");
```

### Print Statements
Print statements output information to the screen (also referred to as the output terminal).

- `System` is a built-in Java class that contains useful tools for our programs.
- `out` is short for “output”.
- `println` is short for “print line”.

We can use `System.out.println()` whenever we want the program to create a new line on the screen after outputting a value:

```java
System.out.println("Hello World");
System.out.println("Today is a great day to code!");
```

```
Hello World
Today is a great day to code!
```

We also can output information using `System.out.print()`. Notice that we’re using `print()`, not `println()`. Unlike `System.out.println()`, this type of print statement outputs everything on the same line. 

```java
System.out.print("Hello ");
System.out.print("World");
```

```
Hello World
```

In this example, if you were to use `print()` or `println()` again, the new text will print immediately after `World` on the same line. It’s important to remember where you left your program’s “cursor”. If you use `println()` the cursor is moved to the next line. If you use `print()` the cursor stays on the same line.

### Commenting Code
When comments are short we use the single-line syntax: `//`.

```java
// calculate customer satisfaction rating
```

When comments are long we use the multi-line syntax: `/*` and `*/`.

```java
/*
We chose to store information across multiple databases to
minimize the possibility of data loss. We'll need to be careful
to make sure it does not go out of sync!
*/
```

Another type of commenting option is the Javadoc comment which is represented by `/**` and `*/`. Javadoc comments are used to create documentation for APIs (Application Programming Interfaces). When writing Javadoc comments, remember that they will eventually be used in the documentation that your users might read, so make sure to be especially thoughtful when writing these comments.

Javadoc comments are typically written before the declaration of fields, methods, and classes.

```java
/**
* The following class accomplishes the following task...
*/
```

### Semicolons and Whitespace
Java does not interpret *whitespace*, the areas of the code without syntax, but humans use whitespace to read code without difficulty.

Java **does** interpret semicolons. Semicolons are used to mark the end of a *statement*, one line of code that performs a single task.

Curly braces mark the scope of our classes and methods. There are no semicolons at the end of a curly brace.

### Compilation: Catching Errors
Java is a *compiled* programming language, meaning the code we write in a **.java** file is transformed into *byte code* by a compiler before it is executed by the Java Virtual Machine on your computer.

A compiler is a program that translates human-friendly programming languages into other programming languages that computers can execute.

The compiling process catches mistakes **before** the computer runs our code.

The Java compiler runs a series of checks while it transforms the code. Code that does not pass these checks will not be compiled.

For example, with a file called **Plankton.java**, we could compile it with the terminal command:

```bash
javac Plankton.java
```

A successful compilation produces a **.class** file: **Plankton.class**, that we execute with the terminal command:

```bash
java Plankton
```

An unsuccessful compilation produces a list of errors. No **.class** file is made until the errors are corrected and the compile command is run again.

### Review
- Java programs have at least one class and one `main()` method.
	- Each class represents one real-world idea.
	- The `main()` method runs the tasks of the program.
- Java comments add helpful context to human readers.
- Java has whitespace, curly braces, and semicolons.
	- Whitespace is for humans to read code easily.
	- Curly braces mark the scope of a class and method.
	- Semicolons mark the end of a statement.
- Java is a compiled language.
	- Compiling catches mistakes in our code.
	- Compilers transform code into an executable class.


## Java Program Structure
We have the text of a program inside the file called **HelloWorld.java**.

```java
// This program outputs the message "Hello World!" to the monitor
 
public class HelloWorld {
  public static void main(String[] args) {
    System.out.println("Hello World!");
  }
}
```

### Case-Sensitivity
Java is a case-sensitive language. Case sensitivity means that syntax, the words our computer understands, must match the case. 

### Classes

```java
public class HelloWorld { 
  // class code
}
```

This is the class of the file. All Java programs are made of at least one class. The class name must match the file: our file is **HelloWorld.java** and our class is `HelloWorld`. We capitalize every word, a style known as *pascal case*. Java variables and methods are named in a similar style called *camel case* where every word after the first is capitalized.

### Methods

```java
  public static void main(String[] args) {
   // Statements
  }
```

Every Java program must have a method called `main()`. A method is a sequence of tasks for the computer to execute. This `main()` method holds all of the instructions for our program.

### Statements

```java
System.out.println("Hello World!");
```

This code uses the method `println()` to send the text “Hello World!” to the terminal as output. `println()` comes from an *object* called `out`, which is responsible for various types of output. Objects are packages of state and behavior, and they’re often modeled on real-world things.

`out` is located within `System`, which is another object responsible for representing our computer within the program! We can access parts of an object with a `.`, which is known as *dot notation*.

This line of code is a *statement*, because it performs a **single** task. Statements always conclude with a semicolon.

### Whitespace
Java programs allow judicious use of whitespace (tabs, spaces, newlines) to create code that is easier to read. The compiler ignores whitespace, but humans need it! Use whitespace to indent and separate lines of code. Whitespace increases the readability of your code.


# Variables
## Learn Java: Variables

### Introduction
We store information in *variables*, named locations in memory.

Naming a piece of information allows us to use that name later, accessing the information we stored.

In Java, we specify the type of information we’re storing. *Primitive data types* are types of data built-in to the Java system. The three main primitive types we’ll cover are `int`, `double`, and `boolean`.

We must *declare* a variable to reference it within our program. Declaring a variable requires that we specify the type and name:

```java
// datatype variableName
int age;
double salaryRequirement;
boolean isEmployed;
```

These variables don’t have any associated value. To assign a value to a variable, we use the assignment operator `=`:

```java
age = 85;
```

When code is used to represent a fixed value, like `85`, it is referred to as a *literal*.

It’s also common to declare a variable and assign it a value in one line!

```java
int yearCodecademyWasFounded = 2011;
```

### ints
In Java, whole numbers are stored in the *int* primitive data type.

`int`s hold positive numbers, negative numbers, and zero. They do not store fractions or numbers with decimals in them.

The `int` data type allows values between -2,147,483,648 and 2,147,483,647, inclusive.

```java
// int variable declaration
int yearJavaWasCreated;
// assignment
yearJavaWasCreated = 1996;
// declaration and assignment
int numberOfPrimitiveTypes = 8;
```

### doubles
`double` can hold decimals as well as very large and very small numbers. The maximum value is 1.797,693,134,862,315,7 E+308, which is approximately 17 followed by 307 zeros. The minimum value is 4.9 E-324, which is 324 decimal places!

```java
// doubles can have decimal places:
double price = 8.99;
// doubles can have values bigger than what an int could hold:
double gdp = 12237700000;
```

### booleans
Often our programs face questions that can only be answered with yes or no.

These questions are answered with a *boolean*, a type that references one of two values: `true` or `false`.

```java
boolean javaIsACompiledLanguage = true;
boolean javaIsACupOfCoffee = false;
```

### char
The `char` data type can hold any character, like a letter, space, or punctuation mark.

It must be surrounded by single quotes, `'`.

```java
char grade = 'A';
char firstLetter = 'p';
char punctuation = '!';
```

### String
So far, we have learned primitive data types, which are the simplest types of data with no built-in behavior. Our programs will also use `Strings`, which are *objects*, instead of primitives. Objects have built-in behavior.

`String`s hold sequences of characters.

There are two ways to create a `String` object: using a `String` literal or calling the `String` class to create a new `String` object.

A *String literal* is any sequence of characters enclosed in double-quotes (`""`).

```java
String greeting = "Hello World";
```

We could also create a *new String object* by calling the `String` class when declaring a `String` like so:

```java
String salutations = new String("Hello World");
```

There are subtle differences in behavior depending on whether you create a `String` using a `String` literal or a new `String` object. 

Certain symbols, known as escape sequences, have an alternative use in Java print statements. Escape sequences are interpreted differently by the compiler than other characters. Escape characters begin with the character `\`.

The `\"` escape sequence allows us to add quotation marks `"` to a `String` value:

```java
System.out.println("\"Hello World\"");
// Prints: "Hello World"
```

Using the `\\` escape sequence allows us to place backslashes in our `String` text:

```java
System.out.println("This is the backslash symbol: \\");
// Prints: This is the backslash symbol: \
```

If we place a `\n` escape sequence in a `String`, the compiler will output a new line of text:

```java
System.out.println("Hello\nGoodbye");
/*
Prints:
Hello
Goodbye
*/
```

### Static Checking
The Java programming language has *static typing*. Java programs will not compile if a variable is assigned a value of an incorrect type. This is a bug, specifically a type declaration bug.

Static typing helps because bugs are caught during programming rather than during execution of the code.

When bugs are not caught at compilation, they interrupt execution of the code by causing *runtime errors*. The program will crash.

### Naming
In Java, variable names are case-sensitive. `myHeight` is a different variable from `myheight`. The length of a variable name is unlimited, but we should keep it concise while keeping the meaning clear.

A variable starts with a valid letter, or a `$`, or a `_`. No other symbols or numbers can begin a variable name.

Variable names of only one word are spelled in all lowercase letters. Variable names of more than one word have the first letter lowercase while the beginning letter of each subsequent word is capitalized. This style of capitalization is called *camelCase*.

```java
// good style
boolean isHuman;
 
// bad styles
// no capitalization for new word
boolean ishuman;
// first word should be lowercase
boolean IsHuman;
// underscores don't separate words
boolean is_human;
```

### Review
- `int`, which stores whole numbers.
- `double`, which stores bigger whole numbers and decimal numbers.
- `boolean`, which stores true and false.
- `char`, which stores single characters using single quotes.
- `String`, which stores multiple characters using double quotes.
- *Static typing*, which is one of the safety features of Java.


## Learn Java: Manipulating Variables

### Introduction
The data type of a variable plays a large role in the operations we can use to manipulate it. We can think of a data type as a combination of a set of values, and a set of operations on those values.

The data type of an expression is determined by the resulting value. For example, an expression that uses two `int` values will evaluate to an `int` value. If an expression contains a `double` value, then the resulting value will also be type `double`.

### Addition and Subtraction
We use the `+` operator to add the values `balance` and `depositAmount`:

```java
double balance = 20000.99;
double depositAmount = 1000.0;
balance = balance + depositAmount;
// balance now holds 21000.99
```

If we wanted to withdraw from the balance, we would use the `-` operator:

```java
double withdrawAmount = 500;
balance = balance - withdrawAmount;
// balance now holds 19500.99
```

Addition and subtraction work with `int` type values as well! 

```java
int numPicturesOfCats = 60 + 24;
```

When we append `++` to a number-based variable, it increases the value by 1. We also have the decrement operator, `--`, which decreases the value by 1.

```java
// Take a picture
numPicturesOfCats++ // Value is now 85
 
// Delete a picture
numPicturesOfCats-- // Value is now 84
```

### Multiplication and Division
We worked 40 hours last week, at a rate of $15.50 an hour. Java can calculate this with the multiplication operator `*`:

```java
double paycheckAmount = 40 * 15.50;
//paycheckAmount now holds 620.0
```

If we want to see how many hours our total balance represents, we use the division operator `/`:

```java
double balance = 20010.5;
double hourlyRate = 15.5;
double hoursWorked = balance / hourlyRate;
//hoursWorked now holds 1291.0
```

Division has different results with integers. The `/` operator does *integer division*, which means that any remainder is lost.

```java
int evenlyDivided = 10 / 5;
//evenlyDivided holds 2, because 10 divided by 5 is 2
int unevenlyDivided = 10 / 4;
//unevenlyDivided holds 2, because 10 divided by 4 is 2.5
```

It’s important to note that the `int` doesn’t round the decimal, but floors it.

It’s important to note that if we try to divide any number by 0, we will get an `ArithmeticException` error as a result.

### Modulo
The modulo operator `%`, gives us the remainder after two numbers are divided.

```java
int cookiesBaked = 10;
int cookiesLeftover = 10 % 3;
//cookiesLeftover holds 1
```

### Compound Assignment Operators
*Compound assignment operators* perform an arithmetic operation on a variable and then reassigns its value. 

```java
int numCupcakes = 12;

numCupcakes += 8; // Value is now 20
```

- Addition (`+=`)
- Subtraction (`-=`)
- Multiplication (`*=`)
- Division (`/=`)
- Modulo (`%=`)

### Order of Operations
The order of operations dictates the order in which an expression is evaluated. Operators that share the same precedence are evaluated from Left-to-Right within the expression.

The order is as follows:

1. Parentheses
2. Exponents
3. Modulo/Multiplication/Division
4. Addition/Subtraction
 
### Greater Than and Less Than
Java has relational operators for numeric datatypes that make `boolean` comparisons. These include less than (`<`) and greater than (`>`).

```java
double balance = 20000.01;
double amountToWithdraw = 5000.01;
System.out.print(amountToWithdraw < balance);
//this will print true, since amountToWithdraw is less than balance
```

You can save the result of a comparison as a `boolean`.

```java
double myBalance = 200.05;
double costOfBuyingNewLaptop = 1000.05;
boolean canBuyLaptop = myBalance > costOfBuyingNewLaptop;
//canBuyLaptop is false, since 200.05 is not more than 1000.05
```

### Equals and Not Equals
`==` will tell us if two variables are equal:

```java
double paycheckAmount = 620;
double calculatedPaycheck = 15.50 * 40;
 
System.out.print(paycheckAmount == calculatedPaycheck);
// This will print true, since paycheckAmount equals calculatedPaycheck
```

To check if two variables are not equal, we can use `!=`:

```java
double balance = 20000.0;
double amountToDeposit = 620;
double updatedBalance = balance + amountToDeposit;
 
boolean balanceHasChanged = balance != updatedBalance;
// balanceHasChanged holds true, since balance does not equal updatedBalance
```

### Greater/Less Than or Equal To
How could we make sure we got paid at least the amount we expected in our paycheck? We could use greater than or equal to, `>=`, or less than or equal to, `<=`!

```java
double paycheckAmount = 620;
double calculatedPaycheck = 15.50 * 40;
System.out.println(paycheckAmount >= calculatedPaycheck);
//this will print true, since paycheckAmount equals calculatedPaycheck
```

### .equals()
With objects, such as `String`s, we can’t use the primitive equality operator. To test equality with objects, we use a built-in method called `.equals()`. When comparing objects, make sure to always use `.equals()`. `==` will work occasionally, but the reason why it sometimes works has to do with how objects are stored in memory.

To use it, we call it on one `String`, by using `.`, and pass in the `String` to compare against in parentheses:

```java
String person1 = "Paul";
String person2 = "John";
String person3 = "Paul";
 
System.out.println(person1.equals(person2));
// Prints false, since "Paul" is not "John"
 
System.out.println(person1.equals(person3));
// Prints true, since "Paul" is "Paul"
```

### String Concatenation
The `+` operator, which we used for adding numbers together, can be used to *concatenate* `String`s.

```java
String username = "PrinceNelson";
System.out.println("Your username is: " + username); // Your username is: PrinceNelson
```

We can even use a primitive datatype as the second variable to concatenate, and Java will intelligently make it a `String` first:

```java
int balance = 10000;
String message = "Your balance is: " + balance;
System.out.println(message); // Your balance is: 10000
```

### final Keyword
To declare a variable with a value that cannot be manipulated, we need to use the `final` keyword.

```java
final int yearBorn = 1968;
```

When we declare a variable using `final`, the value cannot be changed; any attempts at doing so will cause an error to occur:

```
error: cannot assign a value to final variable yearBorn
```

### Review
- Addition and subtraction, using `+` and `-`
- Multiplication and division, using `*` and `/`
- The modulo operator for finding remainders, `%`
- Compound assignment operators `+=`, `-=`, `*=`, `/=`, and `%=`.
- The order of operations: parentheses -> exponents -> multiplication, division, modulo -> addition, subtraction
- Greater than, `>`, and less than, `<`
- Equal to, `==`, and not equal to, `!=`
- Greater than or equal to, `>=`, and less than or equal to, `<=`
- `equals()` for comparing `String`s and other objects
- Using `+` to concatenate `String`s
- The `final` keyword which makes variables unchangeable


# Object-Oriented Java
## Java: Introduction to Classes

### Introduction to Classes
All programs require one or more classes that act as a model for the world.

This is *object-oriented programming* because programs are built around objects and their interactions. An object contains state and behavior.

Classes are a blueprint for objects. Blueprints detail the general structure.

An instance is the thing itself.

### Classes: Syntax
The fundamental concept of object-oriented programming is the class.

A *class* is the set of instructions that describe how an instance can behave and what information it contains.

Java has pre-defined classes such as `System`.

Here’s a definition of a Java class:

```java
public class Car {
// scope of Car class starts after curly brace
 
  public static void main(String[] args) {
    // scope of main() starts after curly brace
 
    // program tasks
 
  }
  // scope of main() ends after curly brace
 
}
// scope of Car class ends after curly brace
```

`public` is an *access level modifier* that allows other classes to interact with this class. 

This class has a `main()` method, which lists the tasks performed by the program. `main()` runs when we execute the compiled **Car.class** file.

### Classes: Constructors
In order to create an object (an instance of a class), we need a constructor method. The constructor is defined within the class.

The constructor, `Car()`, shares the same name as the class:

```java
public class Car {
  // Constructor method
  public Car() {
    // instructions for creating a Car instance
  }  
 
  public static void main(String[] args) {
    // body of main method
  }
}
```

To create an instance, we need to *call* or *invoke* the constructor within `main()`.

```java
public class Car {
 
  public Car() {
    // instructions for creating a Car instance
  }
 
  public static void main(String[] args) {
    // Invoke the constructor
    Car ferrari = new Car(); 
  }
}
```

In this example, instead of being declared with a primitive data type like `int` or `boolean`, our variable `ferrari` is declared as a *reference data type*. This means that the value of our variable is a reference to an instance’s memory address. During its declaration, the class name is used as the variable’s type. In this case, the type is `Car`.

After the assignment operator, (`=`), we invoke the constructor method: `Car()`, and use the keyword `new` to indicate that we’re creating an instance. Omitting `new` causes an error.

If we were to output the value of `ferrari` we would see its memory address:

```
Car@76ed5528
```

We can initialize a reference-type variable without assigning it a reference if we utilize the special value `null`. Something that is `null` has no value; if we were to assign `null` to an object, it would have a void reference.

```java
Car thunderBird = new Car();
System.out.println(thunderBird); // Prints: Car@76ed5528
 
thunderBird = null; // change value to null
System.out.println(thunderBird); // Prints: null
```

It’s important to note that if we use a null reference to call a method or access an instance variable, we will receive a `NullPointerException` error.

### Classes: Instance Fields
When an object is created, the constructor sets the initial state of the object. The *state* is made up of associated data that represents the characteristics of an object.

We’ll add data to an object by introducing *instance variables*, or *instance fields*.

Often times, instance variables are described as a “has-a” relationship with the object. For example, a `Car` “has-a” color. Another way to think of this is that instance variables are the nouns and adjectives associated with an object.

```java
public class Car {
  /*
  declare fields inside the class
  by specifying the type and name
  */
  String color;
 
  public Car() {
    /* 
    instance fields available in
    scope of constructor method
    */
  }
 
  public static void main(String[] args) {
    // body of main method
  }
}
```

The declaration is within the class and the instance variable will be available for assignment inside the constructor.

Fields are a type of state each instance will possess. One instance may have `"red"` as its color, another `"blue"`, etc. It’s the job of the constructor to give these instance fields initial value.

### Classes: Constructor Parameters
To create objects with dynamic, individual states, we’ll use a combination of the constructor method and instance fields.

In order to assign a value to an instance variable, we need to alter our constructor method to include parameters so that it can access the data we want to assign to an instance.

```java
public class Car {
  String color;
  // constructor method with a parameter
  public Car(String carColor) {
    // parameter value assigned to the field
    color = carColor;
  }
  public static void main(String[] args) {
    // program tasks
  }
}
```

Our method also has a *signature* which defines the name and parameters of the method. In the above example, the signature is `Car(String carColor)`.

There are two types of parameters: formal and actual. A *formal parameter* specifies the type and name of data that can be passed into a method. In our example above, `String carColor` is a formal parameter;  `carColor` will represent whatever `String` value is passed into the constructor. 

In Java, because of *constructor overloading*, a class can have multiple constructors as long as they have different parameter values. The signature is useful in that it helps the compiler differentiate between the different methods.

```java
public class Car {
  String color;
  int mpg;
  boolean isElectric;
 
  // constructor 1
  public Car(String carColor, int milesPerGallon) {
    color = carColor;
    mpg = milesPerGallon;
  }
  // constructor 2
  public Car(boolean electricCar, int milesPerGallon) {
    isElectric = electricCar;
    mpg = milesPerGallon;
  }
}
```

When we initialize an object, the compiler will know which constructor to use because of the values we pass into it. For example, `Car myCar = new Car(true, 40)` will be created by the second constructor because the arguments match the type and order of the second constructor’s signature.

If we do not define a constructor, the Java compiler will generate a default constructor that contains no arguments and assigns the object default values. Default values can be created by assigning values to the instance fields during their declaration:

```java
public class Car {
  String color = "red";
  boolean isElectric = false;
  int cupHolders = 4;
 
  public static void main(String[] args) {
    Car myCar = new Car();
    System.out.println(myCar.color); // Prints: red
  }
}
```

### Classes: Assigning Values to Instance Fields
Now that our constructor has a parameter, we must pass values into the method call. These values are referred to as *arguments*; once they are passed in, they will be used to give the instance fields initial value.

```java
public class Car {
  String color;
 
  public Car(String carColor) {
    // assign parameter value to instance field
    color = carColor;
  }
 
  public static void main(String[] args) {
    // parameter value supplied when calling constructor
    Car ferrari = new Car("red");
  }
}
```

The type of the value given to the invocation **must match** the type declared by the parameter.

We access the value of this field with the *dot operator* (`.`):

```java
/*
accessing a field:
objectName.fieldName
*/
 
ferrari.color;
// "red"
```

An *actual parameter*, or argument, refers to the value being passed during a method call.

*Call by value* is the process of calling a method with an argument value. When an argument is passed, the formal parameter is initialized with a copy of the argument value. For example, when we declared the `ferrari` object, the `String` value `"red"` is passed as an argument; then, the formal parameter `carColor` is assigned a copy of that value.

### Classes: Multiple Fields
Objects are not limited to a single instance field. We can declare as many fields as are necessary for the requirements of our program.

```java
public class Car {
  String color;
  // new fields!
  boolean isRunning;
  int velocity;
 
  // new parameters that correspond to the new fields
  public Car(String carColor, boolean carRunning, int milesPerHour) {
    color = carColor;
    // assign new parameters to the new fields
    isRunning = carRunning;
    velocity = milesPerHour;
  }
 
  public static void main(String[] args) {
    // new values passed into the method call
    Car ferrari = new Car("red", true, 27);
    Car renault = new Car("blue", false, 70);
 
    System.out.println(renault.isRunning);
    // false
    System.out.println(ferrari.velocity);
    // 27
  }
}
```

Ordering matters! We must pass values into the constructor invocation in the same order that they’re listed in the parameters.

### Review
Java is an object-oriented programming language where every program has at least one class. Programs are often built from many classes and objects, which are the instances of a class.

Classes define the state and behavior of their instances. Behavior comes from methods defined in the class. State comes from instance fields declared inside the class.

Classes are modeled on the real-world things we want to represent in our program.

```java
public class Dog {
  // instance field
  String breed;
  // constructor method
  public Dog(String dogBreed) {
    /* 
    value of parameter dogBreed 
    assigned to instance field breed
    */
    breed = dogBreed;
  }
  public static void main(String[] args) {
    /* 
    create instance: 
    use 'new' operator and invoke constructor
    */
    Dog fido = new Dog("poodle");
    /* 
    fields are accessed using: 
    the instance name, `.` operator, and the field name.
    */
    fido.breed;
    // "poodle"
  }
}
```


## Learn Java: Methods

### Introduction
Now, we’re going to learn how to create object *behavior* using methods. 

Methods are repeatable, modular blocks of code used to accomplish specific tasks. We have the ability to define our own methods that will take input, do something with it, and return the kind of output we want.

Through *method decomposition*, we can use methods to break down a large problem into smaller, more manageable problems.

Methods are also reusable.

If we were to share this sandwich-making program with another person, they wouldn’t have to understand *how* `makeSandwich()` worked. If we wrote our program well, all they would need to know is that if they called `makeSandwich()`, they would receive a sandwich. This concept is known as *procedural abstraction*: knowing what a method does, but not how it accomplishes it.

### Defining Methods
If we were to define a `checkBalance()` method for a Savings Account, it would look like the following:

```java
public void checkBalance(){
  System.out.println("Hello!");
  System.out.println("Your balance is " + balance);
}
```

The first line, `public void checkBalance()`, is the method declaration. It gives the program some information about the method:

- `public` means that other classes can access this method. 
- The `void` keyword means that there is no specific output from the method.
- `checkBalance()` is the name of the method.

Every method has its own unique *method signature* which is comprised of the method’s name and its parameter type. In this example, the method signature is `checkBalance()`.

Anything we can do in our `main()` method, we can do in other methods!

`checkBalance()` is considered a non-static method because its signature does not include the keyword `static` like the `main()` method does.

### Calling Methods
When we add a non-static method to a class, it becomes available to use on an object of that class. In order to have our methods get executed, we must *call* the method on the object we created.

```java
class Car {
 
  String color;
 
  public Car(String carColor) {
    color = carColor;
  }
 
  public void startEngine() {
    System.out.println("Starting the car!");
    System.out.println("Vroom!");
  }
 
  public static void main(String[] args){
    Car myFastCar = new Car("red");
    // Call a method on an object 
    myFastCar.startEngine();
    System.out.println("That was one fast car!");
  }
}
```

First, we reference our object `myFastCar`. Then, we use the dot operator (`.`) to call the method `startEngine()`. Note that we must include parentheses `()` after our method name in order to call it.

```
Starting the car!
Vroom!
That was one fast car!
```

Code generally runs in a top-down order where code execution starts at the top of a program and ends at the bottom of a program; however, methods are ignored by the compiler unless they are being called.

When a method is called, the compiler executes every statement contained within the method. Once all method instructions are executed, the top-down order of execution continues.

### Scope
A method is a task that an object of a class performs.

We mark the domain of this task using curly braces: `{`, and `}`. Everything inside the curly braces is part of the task. This domain is called the *scope* of a method.

We can’t access variables that are declared inside a method in code that is outside the scope of that method.

```java
class Car {
  String color;
  int milesDriven;
 
  public Car(String carColor) {
    color = carColor;
    milesDriven = 0;         
  }
 
  public void drive() {
     String message = "Miles driven: " + milesDriven;
     System.out.println(message);
  }
 
  public static void main(String[] args){
     Car myFastCar = new Car("red");
     myFastCar.drive();
  }
}
```

The variable `message`, which is declared and initialized inside of `drive`, cannot be used inside of `main()`! It only exists within the scope of the `drive()` method.

However, `milesDriven`, which is declared at the top of the class, can be used inside all methods in the class, since it is in the scope of the whole class.

### Adding Parameters
Similar to how we added parameters to *constructors*, we can customize all other methods to accept parameters. 

```java
class Car {
 
  String color;
 
  public Car(String carColor) {
    color = carColor;         
  }
 
  public void startRadio(double stationNum, String stationName) {
    System.out.println("Turning on the radio to " + stationNum + ", " + stationName + "!");
    System.out.println("Enjoy!");
  }
 
  public static void main(String[] args){
    Car myCar = new Car("red");
    myCar.startRadio(103.7, "Meditation Station");
  }
}
```

Adding parameter values impacts our method’s signature. Like constructor signatures, the method signature includes the method name as well as the parameter types of the method. 

Note that when we call on a method with multiple parameters, the arguments given in the call must be placed in the same order as the parameters appear in the signature. If the argument types do not match the parameter types, we’ll receive an error.

Through method overloading, our Java programs can contain multiple methods with the same name as long as each method’s parameter list is unique.

```java
// Method 1
public void startRadio(double stationNum, String stationName) {
  System.out.println("Turning on the radio to " + stationNum + ", " + stationName + "!");
  System.out.println("Enjoy!");
}
 
// Method 2
public void startRadio(double stationNum) {
  System.out.println("Turning on the radio to " + stationNum + "!");
}
 
public static void main(String[] args){
  Car myCar = new Car("red");
  // Calls the first startRadio() method
  myCar.startRadio(103.7, "Meditation Station");
 
  // Calls the second startRadio() method
  myCar.startRadio(98.2);
}
```

### Reassigning Instance Fields

```java
public class SavingsAccount{
  double balance;
  public SavingsAccount(double startingBalance){
    balance = startingBalance;
  }
 
  public void deposit(double amountToDeposit){
     //Add amountToDeposit to the balance
  }
 
  public void withdraw(double amountToWithdraw){
     //Subtract amountToWithdraw from the balance
  }
 
  public static void main(String[] args){
 
  }
}
```

These methods would change the value of the variable `balance`. We can *reassign* `balance` to be a new value by using our assignment operator, `=`, again.

```java
public void deposit(double amountToDeposit){
  double updatedBalance = balance + amountToDeposit;
  balance = updatedBalance;
}
```

### Returns
Remember, variables can only exist in the *scope* that they were declared in. We can use a value outside of the method it was created in if we *return* it from the method.

We return a value by using the keyword `return`:

```java
public int numberOfTires() {
   int tires = 4;
   // return statement
   return tires;
}
```

Once the return statement is executed, the compiler exits the function. Any code that exists after the return statement in a function is ignored.

In past exercises, when creating new methods, we used the keyword `void`. Here, we are replacing `void` with `int`, to signify that the return type is an `int`.

The `void` keyword (which means “completely empty”) indicates that no value is returned after calling that method.

A non-void method, like `numberOfTires()` returns a value when it is called. We can use datatype keywords (such as `int`, `char`, etc.) to specify the type of value the method should return. The return value’s type must match the return type of the method. If the return expression is compatible with the return type, a copy of that value gets returned in a process known as *return by value*.

Unlike void methods, non-void methods can be used as either a variable value or as part of an expression like so:

```java
public static void main(String[] args){
    Car myCar = new Car("red");
    int numTires = myCar.numberOfTires();
}
```

Returning an object works a little differently than returning a primitive value. When we return a primitive value, a copy of the value is returned; however, when we return an object, we return a reference to the object instead of a copy of it.

```java
class CarLot {
    Car carInLot;
    public CarLot(Car givenCar) {
        carInLot = givenCar;
    }
 
    public Car returnACar() {
        // return Car object
        return carInLot;
    }
 
    public static void main(String[] args) {
        Car myCar = new Car("red", 70);
        System.out.println(myCar); 
        CarLot myCarLot = new CarLot(myCar);
        System.out.println(myCarLot.returnACar());
    }
}
```

This code outputs the same memory address because `myCar` and `carInLot` have the same reference value:

```
Car@2f333739
Car@2f333739
```

### The toString() Method
When we print out Objects, we often see a String that is not very helpful in determining what the Object represents.

We can add a method to our classes that makes this printout more descriptive.

When we define a `toString()` method for a class, we can return a `String` that will print when we print the object:

```java
class Car {
 
    String color;
 
    public Car(String carColor) {
        color = carColor;
    }
 
    public static void main(String[] args){
        Car myCar = new Car("red");
        System.out.println(myCar);
    }
 
   public String toString(){
       return "This is a " + color + " car!";
   }
}
```

### Review
Methods are a powerful way to abstract tasks away and make them repeatable. They allow us to define behavior for classes, so that the Objects we create can do the things we expect them to.

- Defining a method : Method declarations will declare a method’s return type, name, and parameters
- Calling a method : Methods are invoked with a `.` and `()`
- Parameters : Inputs to the method and their types are declared in parentheses in the method signature
- Changing Instance Fields : Methods can be used to change the value of an instance field
- Scope : Variables only exist within the domain that they are created in
- Return : The type of the variables that will be output are declared in the method declaration


# Conditionals and Control Flow
## Conditionals and Control Flow

### Introduction to Control Flow
Conditional statements check a `boolean` condition and run a *block* of code depending on the condition. Curly braces mark the scope of a conditional block similar to a method or class.

```java
if (true) {
 
  System.out.println("Hello World!");
 
}
```

### If-Then Statement
The *if-then* statement is the most simple control flow we can write. It tests an expression for truth and executes some code based on it.

```java
if (flip == 1) {
 
  System.out.println("Heads!");
 
}
```

For the condition in parentheses we can also use variables that reference a boolean, or comparisons that evaluate to a boolean.

If a conditional is brief we can omit the curly braces entirely:

```java
if (true) System.out.println("Brevity is the soul of wit");
```

Note: Conditional statements do not end in a semicolon.

### If-Then-Else
We create an alternate conditional branch with the `else` keyword:

```java
if (hasPrerequisite) {
 
  // Enroll in course
 
} else {
 
  // Enroll in prerequisite
 
}
```

This conditional statement ensures that exactly one code block will be run.

### If-Then-Else-If
The conditional structure we’ve learned can be chained together to check as many conditions as are required by our program.

```java
String course = "Theatre";
 
if (course.equals("Biology")) {
 
  // Enroll in Biology course
 
} else if (course.equals("Algebra")) {
 
  // Enroll in Algebra course
 
} else if (course.equals("Theatre")) {
 
  // Enroll in Theatre course
 
} else {
 
  System.out.println("Course not found!");
 
}
```

**The first** condition to evaluate to true will have that code block run.

**Note**: Only one of the code blocks will run.

### Nested Conditional Statements
We can create more complex conditional structures by creating *nested conditional statements*, which is created by placing conditional statements inside other conditional statements:

```
if (outer condition) {
  if (nested condition) {
    Instruction to execute if both conditions are true
  }
}
```

When we implement nested conditional statements, the outer statement is evaluated first. If the outer condition is `true`, then the inner, nested statement is evaluated.

```java
int temp = 45;
boolean raining = true;
 
if (temp < 60) {
  System.out.println("Wear a jacket!");
  if (raining == true) {
    System.out.println("Bring your umbrella.");
  } else {
    System.out.println("Leave your umbrella home.");
  }
}
```

Note that, if the first condition was `false`, the nested condition would not be evaluated.

### Switch Statement
An alternative to chaining if-then-else conditions together is to use the `switch` statement. This conditional will check a given value against any number of conditions and run the code block where there is a match.

```java
String course = "History";
 
switch (course) {
  case "Algebra": 
    // Enroll in Algebra
    break; 
  case "Biology": 
    // Enroll in Biology
    break;
  case "History": 
    // Enroll in History
    break;
  case "Theatre":
    // Enroll in Theatre
    break;
  default:
    System.out.println("Course not found");
}
```

When no value matches, the `default` block runs. Think of this as the `else` equivalent.

Switch blocks are different than other code blocks because they are not marked by curly braces and we use the `break` keyword to exit the switch statement.

Without `break`, code below the matching case label is run, including code under other case labels, which is rarely the desired behavior.

```java
String course = "Biology";
 
switch (course) {
  case "Algebra": 
    // Enroll in Algebra
  case "Biology": 
    // Enroll in Biology
  case "History": 
    // Enroll in History
  case "Theatre":
    // Enroll in Theatre
  default:
    System.out.println("Course not found");
}
 
// enrolls student in Biology... AND History and Theatre!
```

### Review
Conditional statements add branching paths to our programs. We use conditionals to make decisions in the program so that different inputs will produce different results.

Conditionals have the general structure:

```java
if (condition) {
    // consequent path
} else {
    // alternative path
}
```

Specific conditional statements have the following behavior:

- `if-then`:
	- code block runs if condition is true
- `if-then-else`:
	- one block runs if conditions is true
	- another block runs if condition is false
- `if-then-else` chained:
	- same as if-then but an arbitrary number of conditions
- `switch`:
	- switch block runs if condition value matches `case` value


## Conditional Operators

### Introduction to Conditional Operators
Java includes operators that only use boolean values. These *conditional operators* help simplify expressions containing complex boolean relationships by reducing multiple boolean values to a single value: `true` or `false`.

### Conditional-And: &&
The AND operator, `&&`, is used between two boolean values and evaluates to a single boolean value. If the values on both sides are `true`, then the resulting value is `true`, otherwise the resulting value is `false`.

```java
if (tuitionPaid) {
  if (hasPrerequisite) {
    // enroll student
  }
}
```

We’ve nested two if-then statements. This does the job but we can be more concise with the AND operator:

```java
if (tuitionPaid && hasPrerequisite) {
  // enroll student
}
```

### Conditional-Or: ||
The OR operator, `||`, is used between two boolean values and evaluates to a single boolean value. If either of the two values is `true`, then the resulting value is `true`, otherwise the resulting value is `false`.

```java
if (hasAlgebraPrerequisite) {
  // Enroll in course
}
 
if (hasGeometryPrerequisite) {
  // Enroll in course
}
```

We’re using two different if-then statements with the same code block. We can be more concise with the OR operator:

```java
if (hasAlgebraPrerequisite || hasGeometryPrerequisite) {
  // Enroll in course
}
```

On some occasions, the compiler can determine the truth value of a logical expression by only evaluating the first boolean operand; this is known as *short-circuited evaluation*. Short-circuited evaluation only works with expressions that use `&&` or `||`.

In an expression that uses `||`, the resulting value will be `true` as long as one of the operands has a `true` value. If the first operand of an expression is `true`, we don’t need to see what the value of the other operand is to know that the final value will also be `true`.

An expression that uses `&&` will only result in `true` if both operands are `true`. If the first operand in the expression is `false`, the entire value will be `false`.

### Logical NOT: !
The *unary* operator NOT, `!`, works on a single value. This operator evaluates to the opposite boolean to which it’s applied.

```java
boolean hasPrerequisite = false;
 
if (!hasPrerequisite) {
  System.out.println("Must complete prerequisite course!");
}
```

### Combining Conditional Operators
The order of evaluation when it comes to conditional operators is as follows:

1. Conditions placed in parentheses - `()`
2. NOT - `!`
3. AND - `&&`
4. OR - `||`

### Review
Conditional operators work on boolean values to simplify our code. They’re often combined with conditional statements to consolidate the branching logic.

Conditional-AND, `&&`, evaluates to `true` if the booleans on both sides are `true`.

```java
if (true && false) {
  System.out.println("You won't see me print!");
} else if (true && true) {
  System.out.println("You will see me print!");
}
```

Conditional-OR, `||`, evaluates to `true` if one or both of the booleans on either side is `true`.

```java
if (false || false) {
  System.out.println("You won't see me print!");
} else if (false || true) {
  System.out.println("You will see me print!");
}
```

Logical-NOT, `!`, evaluates to the opposite boolean value to which it is applied.

```java
if (!false) {
  System.out.println("You will see me print!");
}
```


# Arrays and ArrayLists
## Learn Java: Arrays

### Introduction
An array holds a fixed number of values of one type. Arrays hold `double`s, `int`s, `boolean`s, or any other primitives. Arrays can also contain `String`s as well as object references!

Each index of an array corresponds with a different value.

Notice that the indexes start at 0!

### Creating an Array Explicitly
To create an array, we provide a name and declare the type of data it holds:

```java
double[] prices;
```

Just like with variables, we can declare and initialize in the same line.

```java
double[] prices = {13.15, 15.87, 14.22, 16.66};
```

### Importing Arrays
When we printed out the array we created in the last exercise, we saw a memory address that did not help us understand what was contained in the array.

If we want to have a more descriptive printout of the array itself, we need a `toString()` method that is provided by the `Arrays` *package* in Java.

```java
import java.util.Arrays;
```

We put this at the top of the file, before we even define the class!

When we import a package in Java, we are making all of the methods of that package available in our code.

The Arrays package has many useful methods, including `Arrays.toString()`. When we pass an array into `Arrays.toString()`, we can see the contents of the array printed out:

```java
import java.util.Arrays;
 
public class Lottery(){
 
  public static void main(String[] args){
    int[] lotteryNumbers = {4, 8, 15, 16, 23, 42};
    String betterPrintout = Arrays.toString(lotteryNumbers);
    System.out.println(betterPrintout); // [4, 8, 15, 16, 23, 42]
  } 
}
```

### Get Element By Index
We use square brackets, `[` and `]`, to access data at a certain index:

```java
double[] prices = {13.1, 15.87, 14.22, 16.66};
 
System.out.println(prices[1]); // 15.87
```

If we try to access an element outside of its appropriate index range, we will receive an `ArrayIndexOutOfBoundsException` error.

### Creating an Empty Array
We can also create empty arrays and then fill the items one by one. Empty arrays have to be initialized with a fixed size:

```java
String[] menuItems = new String[5];
```

Once you declare this size, it cannot be changed!

After declaring and initializing, we can set each index of the array to be a different item:

```java
menuItems[0] = "Veggie hot dog";
menuItems[1] = "Potato salad";
menuItems[2] = "Cornbread";
menuItems[3] = "Roasted broccoli";
menuItems[4] = "Coffee ice cream";
```

This group of commands has the same effect as assigning the entire array at once:

```java
String[] menuItems = {"Veggie hot dog", "Potato salad", "Cornbread", "Roasted broccoli", "Coffee ice cream"};
```

We can also change an item after it has been assigned!

```java
menuItems[3] = "Baked cauliflower";
```

When we use `new` to create an empty array, each element of the array is initialized with a specific value depending on what type the element is:

Data Type | Initialized Value
--- | ---
int | 0
double | 0.0
boolean | false
Reference | null

```java
String[] my_names = new String[5];
```

Because a `String` is a reference to an Object, `my_names` will contain five `null`s.

### Length
To get the length of an array, we can access the `length` field of the array object:

```java
String[] menuItems = new String[5];
System.out.println(menuItems.length);
```

### String[] args
When we write `main()` methods for our programs, we use the parameter `String[] args`.

A `String[]` is an array made up of `String`s.

The `arg`s parameter is another example of a `String` array. In this case, the array `args` contains the arguments that we pass in from the terminal when we run the class file. (So far, `args` has been empty.)

```java
public class HelloYou {
  public static void main(String[] args) {
    System.out.println("Hello " + args[0]);  
  }
}
```

When we run the file **HelloYou** in the terminal with an argument of "Laura":

```bash
java HelloYou Laura
```

We get the output:

```
Hello Laura
```

The `String[] args` would be interpreted as an array with one element, `"Laura"`.

### Review
- Creating arrays explicitly, using `{` and `}`.
- Accessing an index of an array using `[` and `]`.
- Creating empty arrays of a certain size, and filling the indices one by one.
- Getting the length of an array using `length`.
- Using the argument array `args` that is passed into the `main()` method of a class.


## Learn Java: ArrayLists

### Introduction
When we work with arrays in Java, we’ve been limited by the fact that once an array is created, it has a fixed size. We can’t add or remove elements.

To create mutable and dynamic lists, we can use Java’s `ArrayList` class. `ArrayList` allows us to:

- Store object references as elements
- Store elements of the same type (just like arrays)
- Access elements by index (just like arrays)
- Add elements
- Remove elements

To use an `ArrayList` at all, we need to import them from Java’s `util` package as well:

```java
import java.util.ArrayList;
```

### Creating ArrayLists
To create an `ArrayList`, we need to declare the type of objects it will hold, just as we do with arrays:

```java
ArrayList<String> babyNames;
```

We use angle brackets `<` and `>` to declare the type of the `ArrayList`. These symbols are used for *generics*. Generics are a Java construct that allows us to define classes and objects as parameters of an `ArrayList`. For this reason, we can’t use primitive types in an `ArrayList`:

```java
// This code won't compile:
ArrayList<int> ages;
 
// This code will compile:
ArrayList<Integer> ages;
```

The `<Integer>` generic has to be used in an `ArrayList` instead. You can also use `<Double>` and `<Character>` for types you would normally declare as `double`s or `char`s.

We can initialize to an empty `ArrayList` using the `new` keyword:

```java
// Declaring:
ArrayList<Integer> ages;
// Initializing:
ages = new ArrayList<Integer>();
 
// Declaring and initializing in one line:
ArrayList<String> babyNames = new ArrayList<String>();
```

### Adding an Item
`ArrayList` comes with an `add()` method which inserts an element into the structure. There are two ways we can use `add()`.

If we want to add an element to the end of the `ArrayList`, we’ll call `add()` using only one argument that represents the value we are inserting.

```java
ArrayList<Car> carShow = new ArrayList<Car>();
 
carShow.add(ferrari);
// carShow now holds [ferrari]
carShow.add(thunderbird);
// carShow now holds [ferrari, thunderbird]
carShow.add(volkswagen);
// carShow now holds [ferrari, thunderbird, volkswagen]
```

If we want to add an element at a specific index of our `ArrayList`, we’ll need two arguments in our method call: the first argument will define the index of the new element while the second argument defines the value of the new element:

```java
// Insert object corvette at index 1
carShow.add(1, corvette);
// carShow now holds [ferrari, corvette, thunderbird, volkswagen]
 
// Insert object porsche at index 2
carShow.add(2, porsche);
// carShow now holds [ferrari, corvette, porsche, thunderbird, volkswagen]
```

By inserting a value at a specified index, any elements that appear after this new element will have their index value shift over by 1.

Also, note that an error will occur if we try to insert a value at an index that does not exist.

When using `ArrayList` methods (like `add()`), the reference parameters and return type of a method must match the declared element type of the `ArrayList`. For example, we cannot add an `Integer` type value to an `ArrayList` of `String` elements.

It is possible to create an `ArrayList` that holds values of different types.

In the following snippet, `assortment` is an `ArrayList` that can store different values because we do not specify its type during initialization.

```java
ArrayList assortment = new ArrayList<>();
assortment.add("Hello"); // String
assortment.add(12); // Integer
assortment.add(ferrari); // reference to Car
// assortment holds ["Hello", 12, ferrari]
```

In this case, the items stored in this `ArrayList` will be considered Objects. As a result, they won’t have access to some of their methods without doing some fancy casting. Although this type of `ArrayList` is allowed, using an `ArrayList` that specifies its type is preferred.

### ArrayList Size
If we wanted to display the number of items in the cart, we could find the size of it using the `size()` method:

```java
ArrayList<String> shoppingCart = new ArrayList<String>();
 
shoppingCart.add("Trench Coat");
System.out.println(shoppingCart.size());
// 1 is printed
shoppingCart.add("Tweed Houndstooth Hat");
System.out.println(shoppingCart.size());
// 2 is printed
shoppingCart.add("Magnifying Glass");
System.out.println(shoppingCart.size());
// 3 is printed
```

### Accessing an Index
For `ArrayList`s, bracket notation won’t work. Instead, we use the method `get()` to access an index:

```java
ArrayList<String> shoppingCart = new ArrayList<String>();
 
shoppingCart.add("Trench Coat");
shoppingCart.add("Tweed Houndstooth Hat");
shoppingCart.add("Magnifying Glass");
 
System.out.println(shoppingCart.get(2));
```

### Changing a Value
`ArrayList` has a slightly different way of doing this, using the `set()` method:

```java
ArrayList<String> shoppingCart = new ArrayList<String>();
 
shoppingCart.add("Trench Coat");
shoppingCart.add("Tweed Houndstooth Hat");
shoppingCart.add("Magnifying Glass");
 
shoppingCart.set(0, "Tweed Cape");
 
// shoppingCart now holds ["Tweed Cape", "Tweed Houndstooth Hat", "Magnifying Glass"]
```

### Removing an Item
For arrays, we would have to make a completely new array without the value.

Luckily, `ArrayList`s allow us to remove an item by specifying the index to remove:

```java
ArrayList<String> shoppingCart = new ArrayList<String>();
 
shoppingCart.add("Trench Coat");
shoppingCart.add("Tweed Houndstooth Hat");
shoppingCart.add("Magnifying Glass");
 
shoppingCart.remove(1);
// shoppingCart now holds ["Trench Coat", "Magnifying Glass"]
```

We can also remove an item by specifying the value to remove:

```java
ArrayList<String> shoppingCart = new ArrayList<String>();
 
shoppingCart.add("Trench Coat");
shoppingCart.add("Tweed Houndstooth Hat");
shoppingCart.add("Magnifying Glass");
 
shoppingCart.remove("Trench Coat");
// shoppingCart now holds ["Tweed Houndstooth Hat", "Magnifying Glass"]
```

**Note**: This command removes the FIRST instance of the value "Trench Coat".
 
### Getting an Item's Index
What if we had a really large list and wanted to know the position of a certain element in it?

```java
// detectives holds ["Holmes", "Poirot", "Marple", "Spade", "Fletcher", "Conan", "Ramotswe"];
System.out.println(detectives.indexOf("Fletcher"));
```

### Review
- Adding a new `ArrayList` item using `add()`.
- Accessing the size of an `ArrayList` using `size()`.
- Finding an item by index using `get()`.
- Changing the value of an `ArrayList` item using `set()`.
- Removing an item with a specific value using `remove()`.
- Retrieving the index of an item with a specific value using `indexOf()`.


# Loops
## Learn Java: Loops

### Introduction to Loops
A *loop* is a programming tool that allows developers to repeat the same block of code until some condition is met.

First, a starting condition is evaluated. If the starting condition is `true`, then the loop body is executed. When the last line of the loop body is executed, the condition is *re-evaluated*. This process continues until the condition is `false` (if the condition never becomes `false`, we can actually end up with an infinite loop!). If the starting condition is `false`, the loop never gets executed.

### While We're Here
A `while` loop looks a bit like an `if` statement:

```java
while (silliness > 10) {
 
  // code to run
 
}
```

A `while` loop will continue running the code over and over until the condition evaluates to `false`. 

*Infinite loops* occur when the condition will never evaluate to `false`. This can cause your entire program to crash.

```java
int hedgehogs = 5;
 
// This will cause an infinite loop:
while (hedgehogs < 6) {
 
  System.out.println("Not enough hedgehogs!");
 
}
```

### Incrementing While Loops
When looping through code, it’s common to use a counter variable. A *counter* (also known as an *iterator*) is a variable used in the conditional logic of the loop and (usually) incremented in value during each iteration through the code.

```java
// counter is initialized
int wishes = 0;
 
// conditional logic uses counter
while (wishes < 3) {
 
  System.out.println("Wish granted.");
  // counter is incremented
  wishes++;
 
}
```

We can also decrement counters like this:

```java
int pushupsToDo = 10;
 
while (pushupsToDo > 0) {
 
  doPushup();
  pushupsToDo--;
 
}
```

### For Loops
A `for` loop header is made up of the following three parts, each separated by a semicolon:

1. The initialization of the loop control variable.
2. A boolean expression.
3. An increment or decrement statement.

```java
for (int i = 0; i < 5; i++) {
 
  // code that will run
 
}
```

In a `for` loop, an initialization statement is run once in order to initialize the loop control variable. This variable is modified in every iteration, can be referenced in the loop body, and used to test the boolean condition.

### Using For Loops
It’s important to be aware that, if we don’t create the correct `for` loop header, we can cause the iteration to loop one too many or one too few times; this occurrence is known as an “off by one” error.

For example, imagine we wanted to find the sum of the first ten numbers and wrote the following code:

```java
int sum = 0;
for (int i = 0; i < 10; i++) {
  sum += i
}
```

This code would produce an incorrect value of 45. We skipped adding 10 to sum because our loop control variable started with a value of 0 and stopped the iteration after it had a value of 9. We were off by one! We could fix this by changing the condition of our loop to be `i <= 10;` or `i < 11;`.

### Iterating Over Arrays and ArrayLists
One common pattern we’ll encounter as a programmer is *traversing*, or looping, through a list of data and doing something with each item.

```java
for (int i = 0; i < secretCode.length; i++) {
  // Increase value of element value by 1
  secretCode[i] += 1;
}
```

Traversing an ArrayList looks very similar:

```java
for (int i = 0; i < secretCode.size(); i++) {
  // Increase value of element value by 1
  int num = secretCode.get(i);
  secretCode.set(i, num + 1);
}
```

Let’s use a `while` loop to traverse through an array:

```java
int i = 0; // initialize counter
 
while (i < secretCode.length) {
  secretCode[i] += 1;
  i++; // increment the while loop
}
```

Traversing through an ArrayList with a `while` loop would look like this:

```java
int i = 0; // initialize counter
 
while (i < secretCode.size()) {
  int num = secretCode.get(i);
  secretCode.set(i, num + 1);
  i++; // increment the while loop
}
```

### break and continue
If we ever want to exit a loop before it finishes all its iterations or want to skip one of the iterations, we can use the `break` and `continue` keywords.

The `break` keyword is used to exit, or break, a loop. Once `break` is executed, the loop will stop iterating.

```java
for (int i = 0; i < 10; i++) {
  System.out.println(i);
  if (i == 4) {
    break;
  }
}
```

The `continue` keyword can be placed inside of a loop if we want to skip an iteration. If `continue` is executed, the current loop iteration will immediately end, and the next iteration will begin.

```java
int[] numbers = {1, 2, 3, 4, 5};
 
for (int i = 0; i < numbers.length; i++) {
  if (numbers[i] % 2 == 0) {
    continue;
  }
  System.out.println(numbers[i]);
}
```

Loops can exist all throughout our code - including inside a method. If the `return` keyword was executed inside a loop contained in a method, then the loop iteration would be stopped and the method/constructor would be exited.

```java
public static boolean checkForJacket(String[] lst) {
  for (int i = 0; i < lst.length; i++) {
    System.out.println(lst[i]);
    if (lst[i] == "jacket") {
      return true;
    }
  }
  return false;
} 
 
public static void main(String[] args) {
  String[] suitcase = {"shirt", "jacket", "pants", "socks"};   
  System.out.println(checkForJacket(suitcase));
}
```

### For-Each Loops
Sometimes we couldn’t care less about the indices; we only care about the element itself.

*For-each loops*, which are also referred to as *enhanced loops*, allow us to directly loop through each item in a list of items (like an array or ArrayList) and perform some action with each item.

```java
for (String inventoryItem : inventoryItems) {
  // Print element value
  System.out.println(inventoryItem);
 
}
```

Our enhanced loop contains two items: an enhanced `for` loop variable (`inventoryItem`) and a list to traverse through (`inventoryItems`).

If we try to assign a new value to the enhanced `for` loop variable, the value stored in the array or `ArrayList` will not change. This is because, for every iteration in the enhanced loop, the loop variable is assigned a copy of the list element.

**Note:** We can name the enhanced `for` loop variable whatever we want; using the singular of a plural is just a convention. We may also encounter conventions like `String word : sentence`.

### Removing Elements During Traversal
When an element is removed from an `ArrayList`, all the items that appear after the removed element will have their index value shift by negative one — it’s like all elements shifted to the left! We’ll have to be very careful with how we use our counter variable to avoid skipping elements.

#### Removing An Element Using `while`
When using a `while` loop and removing elements from an `ArrayList`, we should **not** increment the `while` loop’s counter whenever we remove an element. We don’t need to increase the counter because all of the other elements have now shifted to the left.

```java
int i = 0; // initialize counter
 
while (i < lst.size()) {
  // if value is odd, remove value
  if (lst.get(i) % 2 != 0){
    lst.remove(i);
  } else {
    // if value is even, increment counter
    i++;
  }
}
```

#### Removing An Element Using `for`
When using a `for` loop, we, unfortunately, _must_ increase our loop control variable — the loop control variable will always change when we reach the end of the loop (and it will usually change by `1` because we often use something like `i++`.) Since we can’t avoid increasing our loop control variable, we can take matters into our own hands and decrease the loop control variable whenever we remove an item.

```java
for (int i = 0; i < lst.size(); i++) {
  if (lst.get(i) == "value to remove"){
    // remove value from ArrayList
    lst.remove(lst.get(i));
    // Decrease loop control variable by 1
    i--;    
  }
}
```

**Note:** Avoid manipulating the size of an `ArrayList` when using an enhanced `for` loop. Actions like adding or removing elements from an `ArrayList` when using a `for each` loop can cause a `ConcurrentModificationException` error.

### Review
- `while` loops: These are useful to repeat a code block an unknown number of times until some condition is met.
- `for` loops: These are ideal for when you are incrementing or decrementing with a counter variable.
- For-each loops: These make it simple to do something with each item in a list.
 

# String Methods
## String Methods

### Introduction to String Methods
We don’t have to import anything to use the `String` class because it’s part of the `java.lang` package which is available by default.

### length()
In Java, the `length()` string method returns the length ⁠— total number of characters ⁠— of a `String`.

```java
String str = "Hello World!";  
 
System.out.println(str.length()); // 12
```

In theory, the length of a `String` is the same as the Unicode units of the `String`. For example, escape sequences such as `\n` count as only one character.

### concat()
The `concat()` method concatenates one string to the end of another string. Concatenation is the operation of joining two strings together.

```java
String name = new String("Code");
 
name = name.concat("cademy");
 
System.out.println(name); // Codecademy
```

`String`s are immutable objects which means that `String` methods, like `concat()` do not actually change a `String` object.

Our variable, `name` holds a reference to the `String` object, `"Code"`. When we use `concat()` on `name`, we changed its value so that it references a new object — `"Code"`, combined with the String literal, `"cademy"`.

```java
String name = "Code";
 
name.concat("cademy");
 
System.out.println(name);
```

`Code` would be printed instead. The value of the `String` can’t change! Instead, we create a new object and need to assign that new object to some variable.

When we first discussed Objects we learned that if we tried printing an Object, we’d get an output of the class name and the Object’s memory address. If we wanted to get a more useful printout, we’d have to call the Object’s `toString()` method.

This `toString()` method comes into play with `concat()`. If we concatenate a String with another Object, we’re really adding the result of that Object’s `toString()` method to our original String. We can even see this when we concatenate two Strings together (remember a String is an Object). When we use `concat()` on another String, we don’t concatenate its memory address to the original String. Instead, we combine the result of its `toString()` method to the original String.

### equals()
With objects, such as `String`s, we can’t use the primitive equality operator `==` to check for equality between two strings. To test equality with strings, we use a built-in method called `equals()`.

```java
String flavor1 = "Mango";
String flavor2 = "Peach";
 
System.out.println(flavor1.equals("Mango"));
// prints true
 
System.out.println(flavor2.equals("Mango"));
// prints false
```

Side note, there’s also an `equalsIgnoreCase()` method that compares two strings without considering upper/lower cases.

We can also compare `String` values lexicographically (think dictionary order) using the `.compareTo()` method. When we call the `.compareTo()` method, each character in the `String` is converted to Unicode; then the Unicode character from each `String` is compared.

The method will return an `int` that represents the difference between the two Strings.

```java
String flavor1 = "Mango";
String flavor2 = "Peach";
 
System.out.println(flavor1.compareTo(flavor2)); // -3
```

When we use `.compareTo()`, we must pay attention to the return value:

- If the method returns `0`, the two `String`s are equal.
- If the value is less than `0`, then the `String` object is lexicographically less than the `String` object argument.
- If the value is greater than `0`, then the `String` object is lexicographically greater than the `String` object argument.

In the example above, `"Mango"` comes before `"Peach"`, so we get a negative number (we specifically get `-3` because the Unicode values of `"M"` and `"P"` differ by 3). If we did `flavor2.compareTo(flavor1)`, we would get `3`, signifying that `"Peach"` is greater than `"Mango"`.

**Note:** Make sure to pay attention to capitalization when using `.compareTo()`. Upper case and lower case letters have different Unicode values. For example, when comparing `"Mango"` and `"Peach"`, we got `-3`, meaning that `"Mango"` was smaller. But if we compare `"mango"` and `"Peach"` we get `29`. The Unicode value for lower case `"m"` is actually larger than upper case `"P"`. Using `.compareToIgnoreCase()` will perform the same task, but will not consider upper/lower case.

### indexOf()
If we want to know the index of the first occurence of a character in a string, we can use the `indexOf()` method on a string.

```java
String letters = "ABCDEFGHIJKLMN";
 
System.out.println(letters.indexOf("C")); // 2
```

Suppose we want to know the index of the first occurrence of an entire substring. The `indexOf()` instance method can also return where the substring begins (the index of the first character in the substring):

```java
String letters = "ABCDEFGHIJKLMN";
 
System.out.println(letters.indexOf("EFG")); // 4
```

If the `indexOf()` doesn’t find what it’s looking for, it’ll return a `-1`.

### charAt()
The `charAt()` method returns the character located at a `String`‘s specified index.

```java
String str = "qwer";
 
System.out.println(str.charAt(2)); // e
```

Suppose we try to return the character located at index 4. It would produce an `IndexOutOfBoundsException` error because index 4 is out of `str`‘s range.

### substring()
There may be times when we only want a part of a string. In such cases, we may want to extract a _substring_ from a string.

The `substring()` method does exactly that.

```java
String line = "The Heav'ns and all the Constellations rung";
 
System.out.println(line.substring(24)); // Constellations rung
```

The substring begins with the character at the specified index and extends to the end of the string.

Suppose we want a substring from the middle of the string. We can instead include two arguments in this method.

```java
String line = "The Heav'ns and all the Constellations rung";
 
System.out.println(line.substring(27, 33));
```

When `substring()` is called with two arguments, the first argument is _inclusive_ and the second is _exclusive_. This means the resulting substring will begin at index 27 and extend up to, but _not_ including, index 33. Therefore, the example above would output `stella` because that’s the substring that begins at index 27 and ends at index 32, one index before 33.

We can use this method to return a single-element substring at a specific index. We do this by calling `substring()` with the desired index value as the first argument and then the index value plus one as the second argument.

```java
String line = "The Heav'ns and all the Constellations rung";
 
System.out.println(line.substring(24, 25));
// Prints: C
```

### toUpperCase() / toLowerCase()
There will be times when we have a word in a case other than what we need it in. Luckily, Java has a couple `String` methods to help us out:

-   `toUpperCase()`: returns the string value converted to uppercase
-   `toLowerCase()`: returns the string value converted to lowercase

```java
String input = "Cricket!";
 
String upper = input.toUpperCase();
// stores "CRICKET!"
 
String lower = input.toLowerCase();
// stores "cricket!"
```

A good use of this functionality is to ensure consistency of the data you store in a database. Making sure all of the data you get from a user is lowercase before you store it in your database will make your database easier to search through later.

### Review
We have learned some of the string methods that come with the `String` class:

- `length()`
- `concat()`
- `indexOf()`
- `charAt()`
- `equals()` / `equalsIgnoreCase()`
- `substring()`
- `toUpperCase()` / `toLowerCase()`


# Access, Encapsulation, and Static Methods
## Access, Encapsulation, and Scope

### What are Access and Scope?
To oversimplify things, the concepts of access and scope both center around what parts of your programs can interact with specific variables or methods from other parts of your program.

### The public Keyword
The `public` and `private`  keywords are defining what parts of your code have _access_ to other parts of your code.

We can define the access of many different parts of our code including instance variables, methods, constructors, and even a class itself. If we choose to declare these as `public` this means that any part of our code can interact with them - even if that code is in a different class!

The way we declare something to be `public` is to use the `public` keyword in the declaration statement.

```java
public class Dog{
  public String name;
  public int age;
 
  public Dog(String input_name, int input_age){
    name = input_name;
    age = input_age;
  }
 
  public void speak() {
    System.out.println("Arf Arf! My name is " + name + " and I am a good dog!");
  }
}
```

Since everything about a `Dog` is public, any other class can access anything about a `Dog`. For example, let’s say there was a `DogSchool` class. Any method of the `DogSchool` class could make a new `Dog` using the `public` `Dog` constructor, directly access that `Dog`’s instance variables, and directly use that `Dog`’s methods:

```java
public class DogSchool{
  public void makeADog(){
    Dog cujo = new Dog("Cujo", 7);
    System.out.println(cujo.age);
    cujo.speak();
  }
}
```

### The private Keyword and Encapsulation
When a Class’ instance variable or method is marked as `private`, that means that you can only access those structures from elsewhere inside that same class.

```java
public class DogSchool{
 
  public void makeADog(){
    Dog cujo = new Dog("Cujo", 7);
    System.out.println(cujo.age);
    cujo.speak();
  }
}
```

`makeADog` is trying to directly access `Dog`‘s `.age` variable. It’s also trying to use the `.speak()` method. If those are marked as `private` in the `Dog` class, the `DogSchool` class won’t be able to do that. Other methods within the `Dog` class would be able to use `.age` or `.speak()` (for example, we could use `cujo.age` within the `Dog` class), but other classes won’t have access.

Sometimes restricting our code is actually useful from a design perspective. This is one of the core ideas behind _encapsulation_. By making our instance variables (and some methods) `private`, we encapsulate our code into nice little bundles of logic.

For example, a `Bank` object doesn’t necessarily need to know the inner workings of a `CheckingAccount` object. It doesn’t need to know that the money is stored in a field named `money`, or that interest is added to an account by using a method named `.addInterest()`. In fact, if it had access to those fields or methods, it’s possible that someone using a `Bank` object could change things in a `CheckingAccount` without realizing it. By limiting access by using the `private` keyword, we are able to segment, or encapsulate, our code into individual units.

### Accessor and Mutator Methods
When writing classes, we often make all of our instance variables `private`. However, we still might want some other classes to have access to them, we just don’t want those classes to know the _exact_ variable name. To give other classes access to a private instance variable, we would write an _accessor method_ (sometimes also known as a “getter” method).

```java
public class Dog{
  private String name;
 
  //Other methods and constructors
 
  public String getName() {
    return name;
  }
}
```

Even though the instance variable `name` is `private`, other classes could call the `public` method `getName()` which returns the value of that instance variable. Accessor methods will always be `public`, and will have a return type that matches the type of the instance variable they’re accessing.

Similarly, `private` instance variables often have mutator methods (sometimes known as “setters”). These methods allow other classes to reset the value stored in `private` instance variables.

```java
public class Dog{
  private String name;
 
  //Other methods and constructors
 
  public void setName(String newName) {
    name = newName;
  }
 
  public static void main(String[] args){
    Dog myDog = new Dog("Cujo");
    myDog.setName("Lassie");
  }
}
```

Mutator methods, or “setters”, often are `void` methods — they don’t return anything, they just reset the value of an existing variable. Similarly, they often have one parameter that is the same type as the variable they’re trying to change

### Scope: Local Variables
In addition to access modifiers like `public` and `private`, the _scope_ of the variable also determines what parts of your code can access that variable.

The _scope_ of a variable is determined by where the variable is declared. For example, because instance variables are declared inside a class but outside any methods or constructors, all methods and constructors are within the scope of that variable.

```java
class Dog{
  public String name;
  public int age;
  public int weight;
 
  public Dog(){
    name = "Winston";
    age = 8;
    weight = 30;
  }
 
  public void speak(){
    System.out.println("My name is " + name);
  }
}
```

However, if we have a variable declared inside a method, that variable can only be used inside that method. The same is true for parameters. The scope of those parameters is only the method they’re associated with. If you try to use a parameter outside the function it’s defined in, you’ll get an error. These variables are often called local variables. Note that we don’t use `public` or `private` when declaring local variables.

This idea of scope extends to conditionals and loops as well. If you declare a variable inside the body of a conditional or in a loop, that variable can only be used inside that structure. This also includes the variable you’re using as your looping variable.

```java
for(int i = 0; i < 10; i++){
  // You can use i here
}
// i is out of scope here
```

In general, whenever you see curly braces, be aware of scope. If a variable is defined inside curly braces, and you try to use that variable outside of those curly braces, you will likely see an error!

### Scope: The this Keyword
Often times when creating classes, programmers will create local variables with the same name as instance variables.

```java
public class Dog{
  public String name;
 
  public Dog(String inputName){
    name = inputName;
  }
 
  public void speakNewName(String name){
    System.out.println("Hello, my new name is" + name);
  }
 
  public static void main(String[] args){
    Dog myDog = new Dog("Winston");
    myDog.speakNewName("Darla"); // Prints "Darla" - "Winston" ignored
 
  }
}
```

We have an instance variable named `name`, but the method `speakNewName` has a parameter named `name`. So when the method tries to print `name`, which variable will be printed? By default, Java refers to the local variable name. So in this case, the value passed to the parameter will be printed and not the instance variable.

If we wanted to access the instance variable and not the local variable, we could use the `this` keyword.

```java
public class Dog{
  public String name;
 
  public Dog(String inputName){
    name = inputName;
  }
 
  public void speakNewName(String name){
    System.out.println("Hello, my new name is" + this.name);
  }
 
  public static void main(String[] args){
    Dog a = new Dog("Fido");
    Dog b = new Dog("Odie");
 
    a.speakNewName("Winston");
    // "Fido", the instance variable of Dog a is printed. "Winston" is ignored
 
    b.speakNewName("Darla");
    // "Odie", the instance variable of Dog b is printed. "Darla" is ignored.
  }
}
```

The `this` keyword is a reference to the current object. We used `this.name` in our `speakNewName()` method. This caused the method to print out the value stored in the instance variable `name` of whatever `Dog` Object called `speakNewName()`.

Oftentimes, you’ll see constructors have parameters with the same name as the instance variable.

```java
public Dog(String name){
  this.name = name;
}
```

You can read this as “set `this` `Dog`‘s instance variable `name` equal to the variable passed into the constructor”. While this naming is a common convention, it can also be confusing. There’s nothing wrong with naming your parameters something else to be more clear.

```java
public Dog(String inputName){
  this.name = inputName;
}
```

This is now a little clearer — we’re setting the `Dog`‘s instance variable `name` equal to the name we give the constructor.

Finally, mutator methods also usually follow this pattern:

```java
public void setName(String name){
  this.name = name;
}
```

We reset the instance variable to the value passed into the parameter.

This isn’t always explicitly necessary — if there’s no local variable with the same name, Java will know to use the instance variable with that name. That being said, it is a good habit to use `this.` when working with your instance variables to avoid potential confusion.

### Using this With Methods
We’ve seen how the `this` works with variables, but we can also use the `this` with methods.

When defining methods, we can also use the `this` keyword to call other methods.

```java
public class Computer{
  public int brightness;
  public int volume;
 
  public void setBrightness(int inputBrightness){
    this.brightness = inputBrightness;
  }
 
  public void setVolume(int inputVolume){
    this.volume = inputVolume;
  }
 
  public void resetSettings(){
    this.setBrightness(0);
    this.setVolume(0);
  }
}
```

Take a look at the `resetSettings()` method in particular. This method calls other methods from the class. But it needs an object to call those methods! Rather than create a new object, we use `this` as the object. What this means is that the object that calls `resetSettings()` will be used to call `setBrightness(0)` and `setVolume(0)`.

```java
public static void main(String[] args){
  Computer myComputer = new Computer();
  myComputer.resetSettings();
}
```

In this example, calling `myComputer.resetSettings()` is as if we called `myComputer.setBrightness(0)` and `myComputer.setVolume(0)`. `this` serves as a placeholder for whatever object was used to call the original method.

Finally, `this` can be used as a value for a parameter. Let’s say a method exists that takes a `Computer` as a parameter (that method’s signature might be something like `public void pairWithOtherComputer(Computer other)`. If you’re writing another method of the `Computer`, and want to call the `pairWithOtherComputer()` method, you could use `this` as the parameter. That call might look something like `this.pairWithOtherComputer(this)`. You’re using the current object to call the method _and_ are passing that object as that method’s parameter.

```java
public void pairWithOtherComputer(Computer other){
  // Code for method that uses the parameter other
}
 
public void setUpConnection(){
  // We use "this" to call the method and also pass "this" to the method so it can be used in that method
  this.pairWithOtherComputer(this);
}
```

### Other Private Methods
Oftentimes, `private` methods are helper methods — that is to say that they’re methods that other, bigger methods use.

For example, for our `CheckingAccount` example, we might want a public method like `getAccountInformation()` that prints information like the name of the account owner, the amount of money in the account, and the amount of interest the account will make in a month. That way, another class, like a `Bank`, could call that public method to get all of that information quickly.

Well, in order to get that information, we might want to break that larger method into several helper methods. For example, inside `getAccountInformation()`, we might want to call a function called `calculateNextMonthInterest()`. That helper method should probably be `private`. There’s no need for a `Bank` to call these smaller helper methods — instead, a `Bank` can call the one `public` method, and rely on that method to do all of the complicated work by calling smaller `private` methods.

### Review
- The `public` and `private` keywords are used to define what parts of code have access to other classes, methods, constructors, and instance variables.
- Encapsulation is a technique used to keep implementation details hidden from other classes. Its aim is to create small bundles of logic.
- The `this` keyword can be used to designate the difference between instance variables and local variables.
- Local variables can only be used within the scope that they were defined in.
- The `this` keyword can be used to call methods when writing classes.

```java
public class CheckingAccount{
  private String name;
  private int balance;
  private String id;
  private double interestRate;

  public CheckingAccount(String inputName, int inputBalance, String inputId){
    this.name = inputName;
    this.balance = inputBalance;
    this.id = inputId;
    this.interestRate = 0.02;
  }

  public int getBalance(){
    return this.balance;
  }
  
  public void setBalance(int newBalance){
    this.balance = newBalance;
  }

  public double getMonthlyInterest(){
    return this.interestRate * this.balance;
  }

}
```

```java
public class Bank{
  private CheckingAccount accountOne;
  private CheckingAccount accountTwo;

  public Bank(){
    accountOne = new CheckingAccount("Zeus", 100, "1");
    accountTwo = new CheckingAccount("Hades", 200, "2");
  }

  public static void main(String[] args){
    Bank bankOfGods = new Bank();
    System.out.println(bankOfGods.accountOne.getBalance());
    bankOfGods.accountOne.setBalance(5000);
    System.out.println(bankOfGods.accountOne.getBalance());
    System.out.println(bankOfGods.accountOne.getMonthlyInterest());

  }

}
```


## Static Methods of the Math Class

### The Math Class
The Java `Math` class is part of the `java.lang` package; it contains a variety of methods that can be used to perform numerical calculations in our programs.

### Calling Static Methods
Every method in the `Math` class is static. This means that we can call and use these methods without creating an object of the class. There are two main options for calling a static method.

Our first option is to append the dot operator to the class name followed by the method we want to execute. If we wanted to reference a method of the `Math` class, we would use `Math.NameOfMethodHere`.

```java
class Numbers {
  public static void main(String[] args) {
    // Call method using the Class name, the dot operator, the method name, and arguments
    int smallerNumber = Math.min(3, 10);
    System.out.println(smallerNumber); // Prints: 3
  }
}
```

How is this any different from calling a non-static method? We don’t need to create an object of the class in order to use the methods it contains.

```java
class Numbers {
  int firstNumber;
  int secondNumber;
 
  public Numbers (int num1, int num2) {
    firstNumber = num1;
    secondNumber = num2;
  }
 
  // non-static method
  public int returnSum() {
    return firstNumber + secondNumber;
  }
 
  public static void main(String[] args) {
    // Create an object
    Numbers myNumbers = new Numbers(2, 5);
    // Call a non-static method on object
    int sum = myNumbers.returnSum();
    System.out.println(sum); // Prints: 7
  }
}
```

With non-static methods, if we don’t create an object of this class (or one of its subclasses), we do not have access to its methods. This isn’t the case for static methods.

Our second option for calling a static method from the `Math` class is to import the class by adding `import static java.lang.Math.*;` to the top of our program. If we import the `Math` class, we can reference the method using only the method name like so:

```java
import static java.lang.Math.*; // import Math class
 
class Numbers {
  public static void main(String[] args) {
    // Call method by using method name and arguments
    int smallerNumber = min(3, 10);
    System.out.println(smallerNumber); // Prints: 3
  }
}
```

### Useful Methods

#### int abs(int x)
**Purpose:** Returns the absolute value of an int value.

```java
System.out.println(Math.abs(5)); // Prints: 5
System.out.println(Math.abs(-5)); // Prints: 5
```

#### double abs(double x)
**Purpose:** Returns the absolute value of a double value.

```java
System.out.println(Math.abs(5.0)); // Prints: 5.0
System.out.println(Math.abs(-5.0)); // Prints: 5.0
```

#### double pow(double base, double exponent)
**Purpose:** Returns the value of the first parameter raised to the power of the second parameter.

```java
double x = Math.pow(5, 3);
System.out.println(x); // Prints: 125.0
```

#### double sqrt(double x)
**Purpose:** Returns the positive square root of a double value.

```java
double x = Math.sqrt(49); 
System.out.println(x); // Prints: 7.0
double y = Math.sqrt(52); 
System.out.println(y); // Prints: 7.211102550927978
```

#### double random()
**Purpose:** Returns a double value greater than or equal to `0.0` and less than `1.0`.

```java
System.out.println(Math.random());
```

With some manipulation, we can use `Math.random()` to create a random `int` or `double` value within a predefined range.

```java
// Random double value between 0 and 10, not including 10
double a = Math.random() * 10;
```

If we wanted a random `int` value between `0` and `9`, we would need to implement the `(int)` casting operator in our expression like so:

```java
// Random int value between 0 and 9
int b = (int)(Math.random() * 10);
```

If we wanted our range to start at `1` and end at `10`, we would have to add `1` to the end of our previous expression:

```java
// Random int value between 1 and 10
int c = (int)(Math.random() * 10) + 1;
```

Using addition also gives us the ability to start the range at any number. What if we wanted an `int` value in the range of `10` up to and including `20`? We would have to implement the algorithm `(Math.random() * (maxValue - minValue + 1)) + minValue`.

```java
// Random int value between 10 and 20
int d = (int)(Math.random() * 11 ) + 10;
```

Here’s another way to think about this algorithm — the value that you multiply by defines the number of possible values you can get. The number that you add defines the starting value.

### Review
- The `Math` class is part of the `java.lang` package and provides useful static methods for performing mathematical equations.
- To call these static methods, reference the class name + the dot operator + the method name. To only reference the method name, import the `Math` class into your program.


## Static Variables and Methods

### Static Methods Refresher
Static methods are methods that belong to an entire class, not a specific object of the class. Static methods are called using the class name and the `.` operator.

```java
double randomNumber = Math.random();
// Stores a random decimal between 0.0 and 1.0 in randomNumber
 
double number = Double.valueOf("2.5");
// Transforms the String "2.5" into a double
```

In the first example, `random()` is a static method that belongs to the `Math` class. We didn’t need to create a `Math` object (like `Math myMathObject = new Math()`) in order to use that method. We could just call it using the class name.

Finally, notice that our `main()` methods have been `static` this whole time. When Java runs your program, it calls that the main method of your class — `YourClassName.main()`.

### Static Variables
Much like static methods, you can think of _static variables_ as belonging to the class itself instead of belonging to a particular object of the class.

Just like with static methods, we can access static variables by using the name of the class and the `.` operator. Finally, we declare static variables by using the `static` keyword during declaration. This keyword usually comes after the variable’s access modifier (`public` or `private`).

```java
public class Dog{
 
  // Static variables
  public static String genus = "Canis";
 
  //Instance variables
  public int age;
  public String name;
 
  public Dog(int inputAge, String inputName){
    this.age = inputAge;
    this.name = inputName;
  }
}
```

Since all dogs share the same genus, we could use a static variable to store that information for the entire class. However, we want each dog to have its own unique `name` and `age`, so those aren’t `static`. We could now access this static variable in a `main()` function like so:

```java
public class Dog{
  //Variables, constructors and methods defined here
 
  public static void main(String[] args){
    System.out.println(Dog.genus); // Prints Canis
  }
}
```

Unlike static methods, you can still access static variables from a specific object of the class. However, no matter what object you use to access the variable, the value will always be the same. You can think of it as all objects of the class sharing the same variable.

```java
public static void main(String[] args){
  Dog snoopy = new Dog(3, "Snoopy");
  Dog ringo = new Dog(5, "Ringo");
 
  System.out.println(Dog.genus); // Prints Canis
  System.out.println(snoopy.genus); // Prints Canis
  System.out.println(ringo.genus); // Prints Canis
}
```

Finally, you might have seen a few static variables before. If you want easy access to the largest possible integer, you can get it by using `Integer.MAX_VALUE`. If you look at the [official documentation](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#MAX_VALUE) you’ll see that this variable is `public`, `static`, _and_ `final`. (`final` means that you can’t change the variable’s value after creating it.)

### Modifying Static Variables
Whether you’re writing code in a constructor, a non-static method, or a static method, you have access to static variables.

Often times, you’ll see static variables used to keep track of information about all objects of a class. For example, our variable `numATMs` is keeping track of the total number of `ATM`s in the system. Therefore, every time an `ATM` is created (using the constructor), we should increase that variable by `1`. If we could somehow destroy an `ATM`, the method that destroys it should decrease `numATMs` static variable by `1`.

### Writing Your Own Static Methods
Just like with variables, to create a static method, use the `static` keyword in the method’s definition. Just like with variables, this keyword usually comes after `public` or `private`.

```java
public static void myFirstStaticMethod(){
  // Some code here
}
```

Often times, you’ll see static methods that are accessors or mutators for static variables.

```java
public static int getMyStaticVariable(){
  return myStaticVariable;
}
 
public static void setMyStaticVariable(int newValue){
  myStaticVariable = newValue;
}
```

One important rule to note is that static methods can’t interact with non-static instance variables.

The `this` keyword can’t be used by a static method since static methods are associated with an entire class, not a specific object of that class. If you try to mix `this` with a static method, you’ll see the error message `non-static variable this cannot be referenced from a static context`.

### Review
- Static methods and variables are associated with the class as a whole, not objects of the class.
- Static methods and variables are declared as static by using the `static` keyword upon declaration.
- Static methods cannot interact with non-static instance variables. This is due to static methods not having a `this` reference.
- Both static methods and non-static methods can interact with static variables.

```java
public class ATM{
  // Static variables
  public static int totalMoney = 0;
  public static int numATMs = 0;

  // Instance variables
  public int money;

  public ATM(int inputMoney){
    this.money = inputMoney;
    numATMs += 1;
    totalMoney += inputMoney;
  }

  public void withdrawMoney(int amountToWithdraw){
    if(amountToWithdraw <= this.money){
      this.money -= amountToWithdraw;
      totalMoney -= amountToWithdraw;
    }
  }

  public static void averageMoney(){
    System.out.println(totalMoney / numATMs);
  }

  public static void main(String[] args){

    System.out.println("Total number of ATMs: " + ATM.numATMs); 
    ATM firstATM = new ATM(1000);
    ATM secondATM = new ATM(500);
    System.out.println("Total number of ATMs: " + ATM.numATMs); 

    System.out.println("Total amount of money in all ATMs: " + ATM.totalMoney);  
    firstATM.withdrawMoney(500);
    secondATM.withdrawMoney(200);
    System.out.println("Total amount of money in all ATMs: " + ATM.totalMoney);    

    // Call averageMoney() here
    ATM.averageMoney();
  }

}
```


# Inheritance and Polymorphism
## Inheritance and Polymorphism

### Introducing Inheritance
A Java class can _inherit_ traits from another class. The object-oriented principle of inheritance saves us the headache of redefining the same class members all over again.

Our `Triangle` class will inherit all the traits of `Shape`, but `Triangle` can also contain its own unique methods and variables. For example, we could have an instance variable called `hypotenuse` and a method called `findHypotenuse()` that can only be accessed by `Triangle` class references. Objects of `Triangle` can call any method contained in `Triangle` or `Shape`.

There are several terms you’ll encounter frequently:

- _Parent class_, _superclass_, and _base class_ refer to the class that another class inherits from (like `Shape`).
- _Child class_, _subclass_, and _derived class_ refer to a class that inherits from another class (like `Triangle`).

### Inheritance in Practice
So how do we define a child class so that it inherits from a parent class? We use the keyword `extends` like this:

```java
class Shape {
 
  // Shape class members
 
}
 
class Triangle extends Shape {
 
  // additional Triangle class members
 
}
```

When we use inheritance to extend a subclass from a superclass, we create an “is-a” relationship from the subclass to the superclass. For example, an object of `Triangle` _is a_ member of the `Shape` class; however, an object of `Shape` is not necessarily an object of `Triangle`.

Until now, we’ve only been working with one class and one file. However, most Java programs utilize multiple classes, each of which requires its own file. Only one file needs a `main()` method — this is the file we will run.

Note: the various classes in our Java package — even though they are in different files — will have access to each other, so we can instantiate one class inside of another.

### Inheriting the Constructor
The `super()` method acts like the parent constructor inside the child class constructor:

```java
class Triangle extends Shape {
 
  Triangle() {
    super(3);
  }
 
  // additional Triangle class members
 
}
```

It is also possible to write a constructor without making a call to any `super()` constructor:

```java
class Triangle extends Shape {
 
  Triangle() {
    this.numSides = 3;
  }
 
  // additional Triangle class methods
 
}
```

In this situation, Java secretly calls the parent class’ no-argument constructor (`super()`).

If you’re writing a constructor of a child class, and don’t explicitly make a call to a constructor from a parent class using `super`, it’s important to remember that Java will automatically (and secretly) call `super()` as the first line of your child class constructor.
 
### Parent Class Aspect Modifiers
So does a child class inherit its parent’s `private` members?

Well, no. But there is another access modifier we can use to keep a parent class member accessible to its child classes and to files in the package it’s contained in — and otherwise private: `protected`.

![[Pasted image 20230414124758.png]]

```java
class Shape {
 
  protected double perimeter;
 
}
 
// any child class of Shape can access perimeter
```

In addition to access modifiers, there’s another way to establish how child classes can interact with inherited parent class members: using the `final` keyword. If we add `final` after a parent class method’s access modifier, we disallow any child classes from changing that method. This is helpful in limiting bugs that might occur from modifying a particular method.

Though it is not required, there is an established order when two or more field modifiers are used (eg. `public final`). To learn more about this read the [documentation](https://docs.oracle.com/javase/specs/jls/se11/html/jls-8.html#jls-8.3.1).

### Introducing Polymorphism
In Java, if `Orange` is a `Fruit` through inheritance, you can then use `Orange` in the same contexts as `Fruit` like this:

```java
String makeJuice(Fruit fruit) {
 
  return "Apple juice and " + fruit.squeeze();
 
}
 
// inside main()
Orange orange = new Orange();
System.out.println(juicer.makeJuice(orange));
```

Java incorporates the object-oriented programming principle of _polymorphism_. Polymorphism, which derives from Greek meaning “many forms”, allows a child class to share the information and behavior of its parent class while also incorporating its own functionality.

The main advantages of polymorphic programming:

- Simplifying syntax
- Reducing cognitive overload for developers

Note that the reverse situation is not true; you cannot use a generic parent class instance where a child class instance is required. So an `Orange` can be used as a `Fruit`, but a `Fruit` cannot be used as an `Orange`.

### Method Overriding
One common use of polymorphism with Java classes is something we mentioned earlier — _overriding_ parent class methods in a child class.

We can give a single method slightly different meanings for different classes. This is useful when we want our child class method to have the same name as a parent class method but behave a bit differently in some way.

Let’s say we have a `BankAccount` class that allows us to print the current balance. We want to build a `CheckingAccount` class that inherits the functionality of a `BankAccount` but with a modified `printBalance()` method.

```java
class BankAccount {
  protected double balance;
 
  public BankAccount(double balanceIn){
    balance = balanceIn;
  }
 
  public void printBalance() {
    System.out.println("Your account balance is $" + balance);
  }
}
 
class CheckingAccount extends BankAccount {
 
  public CheckingAccount(double balance) {
    super(balance);
  }
 
  @Override
  public void printBalance() {
    System.out.println("Your checking account balance is $" + balance);
  }
}
```

Notice that in order to properly override `printBalance()`, in `CheckingAccount` the method has the following in common with the corresponding method in `BankAccount`:

- Method name
- Return type
- Number and type of parameters

You may have also noticed the `@Override` keyword above `printBalance()` in `CheckingAccount`. This annotation informs the compiler that we want to override a method in the parent class. If the method doesn’t exist in the parent class, we’ll get a helpful error when we compile the program.

In a previous exercise, we learned that the `super` keyword can be used to call the constructor of a superclass. That’s not the only use of `super`; we can also use this keyword to call the methods of a parent class. While we now have the ability to override methods from a superclass, we may find ourselves in a unique situation where we want to use the superclass method instead of the subclass’ overridden method.

If that’s the case, we can call the parent class method by prepending `super` followed by the dot operator (`.`) to the method call. Note that this only works if we pass in the proper method parameters. Let’s see this in action by adding a `checkBalances()` method to `CheckingAccount` that calls both versions of `printBalance()`:

```java
class CheckingAccount extends BankAccount {
  public CheckingAccount(double balance) {
    super(balance);
  }
 
  @Override
  public void printBalance() {
    System.out.println("Your checking account balance is $" + balance);
  }
 
  public void checkBalances() {
    // calls method from CheckingAccount
    printBalance();
    // calls method from BankAccount
    super.printBalance();
  }
 
  public static void main(String[] args) {
    CheckingAccount myCheckings = new CheckingAccount(5000);
    myCheckings.checkBalances();
  }
}

// Your checking account balance is $5000  
// Your account balance is $5000
```

### Using a Child Class as its Parent Class
An important facet of polymorphism is the ability to use a child class object where an object of its parent class is expected.

One way to do this explicitly is to instantiate a child class object as a member of the parent class. We can instantiate a `CheckingAccount` object as a `BankAccount` like this:

```java
BankAccount kaylasAccount = new CheckingAccount(600.00);
```

We can use `kaylasAccount` as if it were an instance of `BankAccount`, in any situation where a `BankAccount` object would be expected. (This would be true even if `kaylasAccount` were instantiated as a `CheckingAccount`, but using the explicit child as parent syntax is most helpful when we want to declare objects in bulk.)

It is important to note here that the compiler just considers `kaylasAccount` to be any old `BankAccount`. But because method overriding is handled at runtime, if we call `printBalance()`, we’ll see something `CheckingAccount` specific:

```
Your checking account balance is $600.00
```

This is because at runtime, `kaylasAccount` is recognized as the `CheckingAccount` it is. So, what if `CheckingAccount` has a method `transferToSavings()` that `BankAccount` does not have? Can `kaylasAccount` still use that method?

Well, no. The compiler believes that `kaylasAccount` is just a `BankAccount` that doesn’t have some fancy child class `transferToSavings()` method, so it would throw an error.

### Child Classes in Arrays and ArrayLists
Usually, when we create an array or an `ArrayList`, the list items all need to be the same type. But polymorphism puts a new spin on what is considered the same type…

In fact, we can put instances of different classes that share a parent class together in an array or `ArrayList`! For example, let’s say we have a `Monster` parent class with a few child classes: `Vampire`, `Werewolf`, and `Zombie`.

```java
Monster dracula, wolfman, zombie1;
 
dracula = new Vampire();
wolfman = new Werewolf();
zombie1 = new Zombie();
 
Monster[] monsters = {dracula, wolfman, zombie1};
```

We can even iterate through the list of items — regardless of subclass — and perform the same action with each item:

```java
for (Monster monster : monsters) {
 
  monster.attack();
 
}
```

### Child Classes in Method Parameters
When we call a method that contains parameters, the arguments we place in our method call must match the parameter type.

If we use a superclass reference as a method parameter, we can call the method using subclass reference arguments!

For example, imagine the class `ScaryStory`, whose constructor takes in a reference to the `Monster` class:

```java
class ScaryStory {
  Monster monster;
  String setting;
 
  public ScaryStory(Monster antagonist, String place) {
    monster = antagonist;
    setting = place;
  }
 
  public void tellStory(){
    System.out.println("Once upon a time, " + monster.name + " was at " + setting + " looking to scare some mortals.");
  }
 
  public static void main(String[] args) {
    Monster dracula;
    dracula = new Vampire("Dracula");
    ScaryStory countDracula = new ScaryStory(dracula, "Dracula Castle");
    countDracula.tellStory();
  }
}
```

In the `main()` method, we used a reference of the class `Vampire` as our argument even though the constructor requested an object of class `Monster`. This is allowed because `Vampire` is a subclass of the `Monster` class.

### Review
- A Java class can inherit fields and methods from another class.
- Each Java class requires its own file, but only one class in a Java package needs a `main()` method.
- Child classes inherit the parent constructor by default, but it’s possible to modify the constructor using `super()` or override it completely.
- You can use `protected` and `final` to control child class access to parent class members.
- Java’s OOP principle of polymorphism means you can use a child class object like a member of its parent class, but also give it its own traits.
- You can override parent class methods in the child class, ideally using the `@Override` keyword.
- It’s possible to use objects of different classes that share a parent class together in an array or `ArrayList`.


# Debugging
## Debugging

### Introduction to Bugs
In Java, there are many different ways of classifying errors, but they can be boiled down to three categories:

- **Syntax errors:** Errors found by the compiler.
- **Run-time errors:** Errors that occur when the program is running.
- **Logic errors:** Errors found by the programmer looking for the causes of erroneous results.

### Syntax Errors
_Syntax errors_ represent grammar errors in the use of the programming language. They are the easiest to find and correct. The compiler will tell you where it got into trouble, and its best guess as to what you did wrong.

Some common syntax errors are:

- Misspelled variable and method names
- Omitting semicolons `;`
- Omitting closing parenthesis `)`, square bracket `]`, or curly brace `}`

### Run-time Errors
Errors which happen during program execution (run-time) after successful compilation are called run-time errors. _Run-time errors_ occur when a program with no compile-time errors asks the computer to do something that the computer is unable to reliably do.

Some common run-time errors:

- Division by zero also known as division error
- Trying to open a file that doesn’t exist

There is no way for the compiler to know about these kinds of errors when the program is compiled.

### Exceptions
Java uses _exceptions_ to handle errors and other exceptional events. Exceptions are the conditions that occur at runtime and may cause the termination of the program.

When an exception occurs, Java displays a message that includes the name of the exception, the line of the program where the exception occurred, and a _stack trace_. The stack trace includes:

- The method that was running
- The method that invoked it
- The method that invoked that one
- and so on…

Some common exceptions that you will see in the wild:

- `ArithmeticException`: Something went wrong during an arithmetic operation; for example, division by zero.
- `NullPointerException`: You tried to access an instance variable or invoke a method on an object that is currently `null`.
- `ArrayIndexOutOfBoundsException`: The index you are using is either negative or greater than the last index of the array (i.e., `array.length-1`).
- `FileNotFoundException`: Java didn’t find the file it was looking for.

### Exception Handling
Exception handling is an essential feature of Java programming that allows us to use run-time error exceptions to make our debugging process a little easier.

One way to handle exceptions is using the `try`/`catch`:

- The `try` statement allows you to define a block of code to be tested for errors while it is being executed.  
- The `catch` statement allows you to define a block of code to be executed if an error occurs in the try block.

The `try` and `catch` keywords come in pairs, though you can also catch several types of exceptions in a single block:

```java
try {
 
  //  Block of code to try
 
} catch (NullPointerException e) {
 
  // Print the error message like this:
  System.err.println("NullPointerException: " + e.getMessage());
 
  // Or handle the error another way here
 
}
```

`System.err.println()` will print to the standard error and the text will be in red.

You can also chain exceptions together:

```java
try {
 
  //  Block of code to try
 
} catch (NullPointerException e) {
 
  //  Code to handle a NullPointerException
 
} catch (ArithmeticException e) {
 
  //  Code to handle an ArithmeticException
 
}
```

### Logic Errors
These types of errors, which provide incorrect output, but appear to be error-free, are called _logic errors_. Logic errors occur when there is a design flaw in your program.

Because logical errors solely depend on the logical thinking of the programmer, your job now is to figure out why the program didn’t do what you wanted it to do.

Some common logic errors:

- Program logic is flawed
- Some “silly” mistake in an `if` statement or a `for`/`while` loop

**Note:** Logic errors don’t have error messages. Sometimes, programmers use a process called [test-driven development (TDD)](https://en.wikipedia.org/wiki/Test-driven_development), a way to give logic errors error messages and save yourself a lot of headaches!

### Debugging Techniques
**1. Divide and conquer:** Comment out or temporarily delete half the code to isolate an issue.

- If the program compiles now, you know the error is in the code you deleted. Bring back about half of what you removed and repeat.
- If the program still doesn’t compile, the error must be in the code that remains. Delete about half of the remaining code and repeat.

**2. Print statements for the rescue:** Use `System.out.println()` to check variable/return values at various points throughout the program.

### Review
- **Syntax errors:** Errors found by the compiler.
- **Run-time errors:** Errors found by checks in a running program.
- **Logic errors:** Errors found by the programmer looking for the causes of erroneous results.


# Two-Dimensional Arrays
## 2-D Arrays: Java

### Introduction to 2D Arrays
In Java, arrays are considered Objects; therefore, we can also have an array of arrays:

```java
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

These are called 2D arrays since we can logically view them as a two-dimensional matrix of values containing both rows and columns.

Additionally, we can have 2D arrays which are not rectangular in shape. These are called jagged arrays:

```java
[['a', 'b', 'c', 'd'], ['e', 'f'], ['g', 'h', 'i', 'j'], ['k']]
```

The only downside is that once initialized, no new rows or columns can be added or removed without copying the data to a newly initialized 2D array. This is because the length of arrays in Java are immutable (unable to be changed after creation).

### Declaration, Initialization, and Assignment
When declaring 2D arrays, the format is similar to normal, one-dimensional arrays, except that you include an extra set of brackets after the data type.

```java
int[][] intTwoDArray;
```

When initializing arrays, we define their size. Initializing a 2D array is different because, instead of only including the number of elements in the array, you also indicate how many elements are going to be in the sub-arrays. This can also be thought of as the number of rows and columns in the 2D matrix.

```java
int[][] intArray1;
intArray1 = new int[row][column];
```

If you already know what values are going to be in the 2D array, you can initialize it and write all of the values into it at once. We can accomplish this through initializer lists

- In Java, initializer lists are a way of initializing arrays and assigning values to them at the same time
- We can use this for 2D arrays as well by creating an initializer list of initializer lists

Similar to how a regular initializer list defines the size and values of the array, nested initializer lists will define the number of rows, columns, and the values for a 2D array.

There are three situations in which we can use initializer lists for 2D arrays:

1. In the case where the variable has not yet been declared, we can provide an abbreviated form since Java will infer the data type of the values in the initializer lists:

```java
double[][] doubleValues = {{1.5, 2.6, 3.7}, {7.5, 6.4, 5.3}, {9.8,  8.7, 7.6}, {3.6, 5.7, 7.8}};
```

2. If the variable has already been declared, you can initialize it by creating a `new` 2D array object with the initializer list values:

```java
String[][] stringValues;
stringValues = new String[][] {{"working", "with"}, {"2D", "arrays"}, {"is", "fun"}};
```

3. The previous method also applies to assigning a new 2D array to an existing 2D array stored in a variable.
 
### Accessing Elements in a 2D Array
Now for 2D arrays, the syntax is slightly different. This is because instead of only providing a single index, we provide two indices.

```java
// Given a 2D array of integer data
int[][] data = {{2,4,6}, {8,10,12}, {14,16,18}};
 
// Access and store a desired element 
int stored = data[0][2];
```

There are two ways of thinking when accessing a specific element in a 2D array.

- The first way of thinking is that the first value represents a row and the second value represents a column in the matrix
- The second way of thinking is that the first value represents which subarray to access from the main array and the second value represents which element of the subarray is accessed

When accessing these elements, if either the row or column value is out of bounds, then an `ArrayIndexOutOfBoundsException` will be thrown by the application.

### Modifying Elements in a 2D Array
For 2D arrays, the format is similar, but we will provide the outer array index in the first set of brackets and the subarray index in the second set of brackets. We can also think of it as providing the row in the first set of brackets and the column index in the second set of brackets if we were to visualize the 2D array as a rectangular matrix:

```java
twoDArray[1][3] = 150;
```

To assign a new value to a certain element, make sure that the new value you are using is either of the same type or is castable to the type already in the 2D array.

To print a 2D array, use

```java
System.out.println(Arrays.deepToString(intMatrix));
```

### Review of Nested Loops
The way it works is that, for every iteration of the outer loop, the inner loop finishes all of its iterations.

```java
for(int outer = 0; outer < 3; outer++){
    System.out.println("The outer index is: " + outer);
    for(int inner = 0; inner < 4; inner++){
        System.out.println("\tThe inner index is: " + inner);
    }
}
```

Here is an example of nested while loops:

```java
int outerCounter = 0;
int innerCounter = 0; 
while(outerCounter<5){
    outerCounter++;
    innerCounter = 0;
    while(innerCounter<7){
        innerCounter++;
    }
}
```

Here is an enhanced **for** loop inside of a while loop:

```java
int outerCounter = 0;
int[] innerArray = {1,2,3,4,5};
 
while(outerCounter<7){
    System.out.println();
    for(int number : innerArray){
        System.out.print(number * outerCounter + " ");
    }
    outerCounter++;
}
```

### Traversing 2D Arrays: Introduction
You might be wondering how we can figure out the number of iterations needed in order to fully traverse the 2D array.

- In order to find the number of elements in the outer array, we just need to get the length of the 2D array.
    - `int lengthOfOuterArray = letterBlock.length;`
    - When thinking about the 2D array in matrix form, this is the height of the matrix (the number of rows)
- In order to find the number of elements in the subarray, we can get the length of the subarray after it has been retrieved from the outer array.
    - Remember that we retrieved the sub array earlier using this format:
        - `char[] subArray = letterBlock[0];`
    -   Therefore, we can use this to get the length of the first subarray in the 2D array
        - `int lengthOfSubArray = letterBlock[0].length;`
        - When thinking about the 2D array in matrix form, this is the width of the matrix (the number of columns)
    - In most cases, getting the length of the first subarray in the 2D array will apply to the rest of the subarrays (if it is rectangular in shape), but there are rare occasions where the length of the subarrays could be different. This occurs if the 2D array is a jagged array.

```java
for(int a = 0; a < letterBlock.length; a++) {
    for(int b = 0; b < letterBlock[a].length; b++) {
        System.out.print("Accessed: " + letterBlock[a][b] + "\t");
    }
    System.out.println();
}
```

You can think of the variable `a` as being the outer loop index, and the variable `b` as being the inner loop index.

We don’t have to only use regular **for** loops for traversing 2D arrays. We can use enhanced **for** loops if we do not need to keep track of the indices. Since enhanced **for** loops only use the element of the arrays, it is a bit more cumbersome to keep track of which index we are at. This same idea applies to while and do-while loops as well. This is why we usually use regular **for** loops except for when we want to do something simple like printing.

### Traversing 2D Arrays: Practice with Loops
For example, you may want to only retrieve elements without keeping track of the indices using enhanced **for** loops, or you could continuously update the 2D array until a condition is met using **while** loops.

In enhanced **for** loops, each element is iterated through until the end of the array. When we think about the structure of 2D arrays in Java (arrays of array objects) then we know that the outer enhanced **for** loop elements are going to be arrays.

```java
char[][] charData = {{'a', 'b', 'c', 'd', 'e', 'f'},{'g', 'h', 'i', 'j', 'k', 'l'}};

for(char[] charRow : charData) {
    for(char c : charRow) {
        System.out.print(c + " ");
    }
    System.out.println();
}
```

Here is an example which accomplishes the same thing, but using **while** loops:

```java
int i = 0, j=0;
while(i<charData.length) {
    j = 0;
    while(j<charData[i].length) {
        System.out.print(charData[i][j] + " ");
        j++;
    }
    System.out.println();
    i++;
}
```

### Traversing 2D Arrays: Row-Major Order
Row-major order for 2D arrays refers to a traversal path which moves horizontally through each row starting at the first row and ending with the last.

#### Why Use Row-Major Order?
Row-major order is important when we need to process data in our 2D array by row. You can be provided data in a variety of formats and you may need to perform calculations of rows of data at a time instead of individual elements.

```java
double[][] data = {{0.51,0.99,0.12},
                   {0.28,0.99,0.89},
                   {0.05,0.94,0.05},
                   {0.32,0.22,0.61},
                   {1.00,0.95,0.09},
                   {0.67,0.22,0.17}};

double rowSum = 0.0;
for(int o = 0; o < data.length; o++) {
    rowSum = 0.0;
    for(int i = 0; i < data[o].length; i++) {
        rowSum += data[o][i];
    }
    System.out.println("Row: " + o +", Sum: " + rowSum);
}
```

An interesting thing to note is that, due to the way 2D arrays are structured in Java, enhanced **for** loops are always in row-major order. This is because an enhanced **for** loop iterates through the elements of the outer array which causes the terminating condition to be the length of the 2D array which is the number of rows.

### Traversing 2D Arrays: Column-Major Order
Column-major order for 2D arrays refers to a traversal path which moves vertically down each column starting at the first column and ending with the last.

This ordering system also conceptualizes the 2D array into a rectangular matrix and starts the traversal at the top left element and ends at the bottom right element. Column-major order has the same starting and finishing point as row-major order, but it’s traversal is completely different

In order to perform column-major traversal, we need to set up our nested loops in a different way. We need to change the outer loop from depending on the number of rows, to depending on the number of columns. Likewise we need the inner loop to depend on the number of rows in its termination condition.

```java
String[][] matrix = {{"[0][0]", "[0][1]", "[0][2]"}, 
                     {"[1][0]", "[1][1]", "[1][2]"},
                     {"[2][0]", "[2][1]", "[2][2]"},
                     {"[3][0]", "[3][1]", "[3][2]"}};

int stepCount = 0;
 
for(int a = 0; a < matrix[0].length; a++) {
    for(int b = 0; b < matrix.length; b++) {
        System.out.print("Step: " + stepCount);
        System.out.print(", Element: " + matrix[b][a]);
        System.out.println();
        stepCount++;
    }
}    
```

#### Why Use Column-Major Order?
Column major order is important because there are a lot of cases when you need to process data vertically.

```java
double[][] data = {{0.51,0.99,0.12},
                   {0.28,0.99,0.89},
                   {0.05,0.94,0.05},
                   {0.32,0.22,0.61},
                   {1.00,0.95,0.09},
                   {0.67,0.22,0.17}};

double colSum = 0.0;
for(int o = 0; o < data[0].length; o++) {
    colSum = 0.0;
    for(int i = 0; i < data.length; i++) {
        colSum += data[i][o];
    }
    System.out.println("Column: " + o +", Sum: " + colSum);
}
```

### Combining Traversal and Conditional Logic
 Here are a few ways in how conditional logic can affect 2D array traversal:

- Skipping or selecting certain rows and columns
- Modifying elements only if they meet certain conditions
- Complex calculations using the 2D array data
- Formatting the 2D array
- Avoiding exceptions / smart processing

```java
String[][] calendar = {{"volunteer", "delivery", null, null, "doctor", null, "soccer"}, {null, "exam 1", null, "mechanic", null, null, "soccer"}, {"volunteer", "off work", null, "birthday", null, "concert", null}, {null, "exam 2", null, null, "doctor", null, "soccer"}, {"visit family", null, null, null, null, null, null}};

for(int i = 0; i < calendar.length; i++) {
    numberOfEventsPerWeek = 0;
    for(int j = 0; j < calendar[i].length; j++) {
        // We need conditional logic to ensure that we do not count the empty days
        String event = calendar[i][j];
        if(event!=null && !event.equals("")) {
            // If the day does not have a null value and an empty string for an event, then we print it and count it
            System.out.println("Week: " + (i+1) + ", Day: " + (j+1) + ", Event: " + event);
            numberOfEventsPerWeek++;
        }
    }
    System.out.println("Total number of events for week "+ (i+1) +": " + numberOfEventsPerWeek + "\n");
}

int numberOfEventsPerWeekday = 0;  
// We will use this array of day strings for our output later on so we don't have (day: 1)  
String[] days = {"Sundays", "Mondays", "Tuesdays", "Wednesdays", "Thursdays", "Fridays", "Saturdays"};  
for(int i = 0; i < calendar[0].length; i++) {  
    numberOfEventsPerWeekday = 0;  
    for(int j = 0; j < calendar.length; j++) {  
        // Don't forget to flip the iterators in the accessor since we are flipping the direction we are navigating.  
        // Remember, i now controls columns and j now controls rows  
        String event = calendar[j][i];  
        if(event!=null && !event.equals("")) {  
            // Make sure we have an event for the day before counting it  
            numberOfEventsPerWeekday++;  
        }  
    }  
    // Use the days string array from earlier to convert the day index to a real weekday string  
    System.out.println("Number of events on " + days[i] + ": " + numberOfEventsPerWeekday);  
}
```

### Review
Arrays are objects in Java, we can have arrays of objects, therefore we can also have arrays of arrays. This is the way 2D arrays are structured in Java.

We can declare and initialize 2D arrays in a few different ways depending on the situation:

```java
// Declaring without initializing
int[][] intTwoD;
 
// Initializing an empty 2D array which has already been declared
intTwoD = new int[5][5];
 
// Declaring and initializing an empty 2D array at once
String[][] stringData = new String[3][6];
 
// Declaring and initializing a 2D array using initializer lists
double[][] doubleValues = {{1.5, 2.6, 3.7}, {7.5, 6.4, 5.3}, {9.8,  8.7, 7.6}, {3.6, 5.7, 7.8}};
 
// Initializing a 2D array using initializer lists after it has already been declared, or already contains data;
char[][] letters = new char[100][250];
letters = new char[][]{{'a', 'b', 'c'}, {'d', 'e', 'f'}};
```

We retrieve elements in a 2D array by providing a row and column index `char c = letters[0][1];`

- We can also think of them as the index of the outer array and the index of the subarray
- We can modify elements the same way `letters[1][2] = 'z';`

We traverse 2D arrays using nested loops.

- We can use loops of any type, but we typically use nested **for** loops to keep track of the indices
- Row-major order traverses through each row moving horizontally to the right through each row
- Column-major order traverses through each column moving vertically down through each column
- Row-major order and column-major order start and end on the same elements, but the paths are different.
- In order to convert row-major to column-major, we need to make the outer loop terminating condition depend on the number of columns, make the inner loop terminating condition depend on the number of rows, and flip the variables in our accessor within the inner loop to ensure that we don’t try to access outside of the 2D array since we flipped the direction of traversal.

Here are examples of row-major and column-major order:

```java
// Row-major order
for(int o = 0; o < letters.length; o++) {
    for(int i = 0; i < letters[o].length; i++) {
        char c = letters[o][i];
    }
}
 
// Column-major order
for(int o = 0; o < letters[0].length; o++) {
    for(int i = 0; i < letters.length; i++) {
        char c = letters[i][o];
    }
}
```

Conditional logic in our 2D array traversal allows us to use the data in a meaningful way. We can control which rows and columns we look at, ensure that the data we are looking at is what we want, perform calculations on specific elements, avoid throwing exceptions, and more.

```java
String[][] words = {{"championship", "QUANTITY", "month"},{"EMPLOYEE", "queen", "understanding"},{"method", "writer", "MOVIE"}};

System.out.println("Before...");
System.out.println(Arrays.deepToString(words).replace("],", "],\n") + "\n");
 
for(int i=0; i<words.length; i++) {
    for(int j = 0; j<words[i].length; j++) {
        if(words[i][j]!=null) {
 
            // Check the capitalization
            boolean allCaps = true;
            for(char c : words[i][j].toCharArray()) 
                if(!Character.isUpperCase(c)) 
                    allCaps = false;
 
            // Flip the capitalization
            if(allCaps)
                words[i][j] = words[i][j].toLowerCase();
            else
                words[i][j] = words[i][j].toUpperCase();
        }
    }
}
 
System.out.println("After...");
System.out.println(Arrays.deepToString(words).replace("],", "],\n") + "\n");
```

# Cheatsheets

## Hello World
![[java_hello_world.pdf]]

## Variables
![[java_variables.pdf]]

## Object-Oriented Java
![[java_object_oriented_java.pdf]]

## Conditionals and Control Flow
![[java_conditionals_and_control_flow.pdf]]

## Arrays and ArrayLists
![[java_arrays_and_arraylists.pdf]]

## Loops
![[java_loops.pdf]]

## String Methods
![[java_string_methods.pdf]]

## Access, Encapsulation, and Static Methods
![[java_access_encapsulation_and_static_methods.pdf]]

## Inheritance and Polymorphism
![[java_inheritance_and_polymorphism.pdf]]

## Two-Dimensional Arrays
![[java_two_dimensional_arrays.pdf]]
