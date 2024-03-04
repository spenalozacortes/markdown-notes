#java
# Java Basics

## Welcome to Java

### What Is Java, and Why Is It So Great?
Java is a programming language in the tradition of C and C++.

#### Platform independence
One of the main reasons Java is so popular is its *platform independence*, which simply means that Java programs can be run on many types of computers.

Java’s platform independence isn’t based on providing compatible compilers for different platforms. Instead, Java is based on the concept of a *virtual machine* called the Java Virtual Machine (JVM). Think of the JVM as a hypothetical computer platform — a design for a computer that doesn’t exist as actual hardware. Instead, the JVM simulates the operation of a hypothetical computer that is designed to run Java programs.

The Java compiler doesn’t translate Java into the machine language of the computer that the program is running on. Instead, the compiler translates Java into the machine language of the JVM, which is called *bytecode*. Then the JVM runs the bytecode in the JVM.

#### Object orientation
Java is inherently *object-oriented*, which means that Java programs are made up from programming elements called objects. Simply put, an *object* is a programming entity that represents either some real-world object or an abstract concept.

All objects have two basic characteristics:

- Objects have data, also known as *state*.
- Objects also have *behavior*, which means that they can perform certain tasks. In Java, these tasks are called *methods*.

Classes are closely related to objects. A *class* is the program code you write to create objects. The class describes the data and methods that define the object’s state and behavior. When the program executes, classes are used to create objects.

#### The Java API
The Java language itself is very simple, but Java comes with a library of classes that provide commonly used utility functions that most Java programs can’t do without. This class library, called the *Java API* (short for *application programming interface*), is as much a part of Java as the language itself. The Java language has only about 50 keywords, but the Java API has several thousand classes, with tens of thousands of methods that you can use in your programs.

### Important Features of the Java Language

#### Type checking
All programming languages must deal in one way or the other with *type checking* — the way that a language handles variables that store different types of data. Numbers, strings, and dates, for example, are commonly used *data types* available in most programming languages. Most programming languages also have several types of numbers, such as integers and real numbers.

Java does complete type checking when the program is compiled. As a result, you must declare all variables as a particular type so that the compiler can make sure you use the variables correctly. The following bit of Java code, for example, won’t compile:

```java
int a = 5;
String b = "Strategery";
String c = a * b;
```

In Java, every class you define creates a new type of data for the language to work with. Thus, the data types you have available to you in Java aren’t just simple predefined types, such as numbers and strings. You can create your own types.

#### Exception handling
In Java, the Java Runtime Environment (JRE) intercepts and folds errors of all types into a special type of object called an *exception object*.

# Programming Basics

## Java Programming Basics

### Looking at the Venerable Hello, World! Program

```java
public class HelloApp
{		
	public static void main(String[] args)
	{
		System.out.println("Hello, World!");
	}
}	
```

public: A *keyword* of the Java language that indicates that the element that follows should be made available to other Java elements. In this case, what follows is a class named HelloApp. As a result, this keyword indicates that the HelloApp class is a *public class*, which means other classes can use it.

class: Another Java keyword that indicates that the element being defined here is a class. All Java programs are made up of one or more *classes*. A class definition contains code that defines the behavior of the objects created and used by the program.

The public keyword is used again, this time to indicate that a method being declared here should have public access. That means classes other than the HelloApp class can use it. All Java programs must have a class that declares a public method named main. The main method contains the statements that are executed when you run the program.

void: In Java, a *method* is a unit of code that can calculate and return a value. If a method doesn’t need to return a value, you must use the void keyword to indicate that no value is returned. Because Java requires that the main method not return a value, you must specify void when you declare the main method.

`(String[] args)`: Java requires that the main method must receive a single parameter
that’s an array of String objects. By convention, this parameter is named `args`.

The println method displays a line of text on the console. The text to be displayed is passed to the println method as a parameter in parentheses following the word println.

Note that in Java, most (but not all) statements must end with a semicolon.

### Dealing with Keywords
A *keyword* is a word that has a special meaning defined by the Java programming
language. In all, Java has 53 keywords.

### Working with Statements
Like most programming languages, Java uses statements to build programs. Unlike most programming languages, Java doesn’t use statements as its fundamental unit of code. Instead, it gives that honor to the class. However, every class must have a body, and the body of a class is made up of one or more statements. In other words, you can’t have a meaningful Java program without at least one statement.

#### Types of statements
Java has many types of statements. Some statements simply create variables that
you can use to store data. These types of statements are often called *declaration*
*statements *and tend to look like this:

```java
int i;
String name;
```

Another common type of statement is an *assignment statement*, which assigns a
value to a variable:

```java
i = 42;
name = "Jackie Robinson";
```

Declaration and assignment statements can be combined into a single statement,
like this:

```java
int i = 42;
String name = "Jackie Robinson";
```

Another common type of statement is an *expression statement*, which performs
calculations or other operations.

```java
System.out.println("Hello, World!");
```

The basic rule is that declaration and expression statements must end with a semicolon, but most other statement types do not.

#### White space
In Java, the term *white space* refers to one or more consecutive space characters,
tab characters, or line breaks. All white space is considered the same.

In Java, you don’t have to do anything special to continue a statement onto a second line. Thus the statement

```java
x = (y + 5) / z;
```

is identical to this statement:

```java
x =
(y + 5) / z;
```

Be advised, however, that you can’t put white space in the middle of a keyword or
identifier.

### Working with Blocks
A *block* is a group of one or more statements that’s enclosed in braces. A block
begins with an opening brace ({) and ends with a closing brace (}). Between the
opening and closing braces, you can code one or more statements.

```java
{
	int i, j;
	i = 100;
	j = 200;
}
```

A block is itself a type of statement. As a result, any time the Java language requires
a statement, you can substitute a block to execute more than one statement.

Note that even though a block can be treated as a single statement, you should
not end a block with a semicolon. The statements within the block may require
semicolons, but the block itself does not.

### Creating Identifiers
An *identifier* is a word that you make up to refer to a Java programming element by name. Although you can assign identifiers to many types of Java elements, they’re most commonly used for the following elements:

- Classes
- Methods
- Variables and fields
- Parameters

Identifiers are also sometimes called *names*. Strictly speaking, a name isn’t quite the same thing as an identifier — all names are identifiers, but not all identifiers are names. But in practice, the terms *name* and *identifier* are used interchangeably.

You must follow a few simple rules when you create identifiers:

- Identifiers are case-sensitive
- Identifiers can be made up of upper- or lowercase letters, numerals, underscore characters (`_`), and dollar signs (`$`).
- All identifiers must begin with a letter.
- An identifier can’t be the same as any of the Java keywords
- The Java language specification recommends that you avoid using dollar signs in names you create, because code generators use dollar signs to create identifiers.

### Crafting Comments
A *comment* is a bit of text that provides explanations of your code. The compiler ignores comments, so you can place any text you want in a comment.

Java has three basic types of comments: *end-of-line comments, traditional*
*comments*, and *JavaDoc comments*.

#### End-of-line comments
An end-of-line comment begins with the sequence // (a pair of consecutive slashes)
and ends at the end of the line. You can place an end-of-line comment at the end of any line.

```java
total = total * discountPercent; // calculate the discounted total
```

If you want, you can also place end-of-line comments on separate lines, like this:

```java
// calculate the discounted total
total = total * discountPercent;
```

You can place end-of-line comments in the middle of statements that span two
or more lines.

```java
total = (total * discountPercent) // apply the discount first
+ salesTax; // then add the sales tax
```

#### Traditional comments
A *traditional comment* begins with the sequence `/*`, ends with the sequence `*/`, and can span multiple lines.

```java
/* HelloApp sample program.
This program demonstrates the basic structure
that all Java programs must follow. */
```

### Introducing Object-Oriented Programming

#### Understanding classes and objects
A *class* is code that defines the behavior of a Java programming element called an object. An *object* is an entity that has both state and behavior. The *state* of an object consists of any data that the object might be keeping track of, and the *behavior* consists of actions that the object can perform. The behaviors are represented in the class by one or more methods that can be called on to perform actions.

When an object is created, Java sets aside an area of computer memory that’s sufficient to hold all the data that’s stored by the object. As a result, each instance of a class has its own data, independent of the data used by other instances of the same class.

#### Understanding static methods
You don’t necessarily have to create an instance of a class to use the methods of the class. If you declare a method with the `static` keyword, you can call the method without first creating an instance of the class, because static methods are called from classes, not from objects.

The main method of a Java application must be declared with the static keyword because when you start a Java program by using the java command from a command prompt, Java doesn’t create an instance of the application class. Instead, it simply calls the program’s static main method.

#### Creating an object from a class
In Java, you can create an object from a class in several ways. The most straightforward way is to create a variable that provides a name you can use to refer to the object, use the `new` keyword to create an instance of the class, and then assign the resulting object to the variable.

```java
Class1 myClass1Object = new Class1();
```

Why do you have to list the class name twice? The first time, you’re providing a *type* for the variable. In other words, you’re saying that the variable you’re creating here can be used to hold objects created from the Class1 class. The second time you list the class name, you’re creating an object from the class. The `new` keyword tells Java to create an object, and the class name provides the name of the class to use to create the object.

The equal sign (=) is an assignment operator. It simply says to take the object created by the new keyword and assign it to the variable.

#### Viewing a program that uses an object
Java requires that each public class be stored in a separate file with the same name as the class; the filename ends with the extension .java.

```java
// This application displays a hello message on
// the console by creating an instance of the
// Greeter class and then calling the Greeter
// object's sayHello method.
public class HelloApp2
{
	public static void main(String[] args)
	{
		Greeter myGreeterObject = new Greeter();
		myGreeterObject.sayHello();
	}
}
```

```java
// This class represents a Greeter object that displays
// a hello message on the console.
public class Greeter
{
	public void sayHello()
	{
		System.out.println("Hello, World!");
	}
}
```

#### So what’s the difference?
Simply put, the first version is procedural, and the second is object-oriented. In the first version of the program, the main method of the application class does all the work of the application by itself: It just says hello. The second version defines a class that knows how to say hello to the world and then creates an object from that class and asks that object to say hello. The application itself doesn’t know (or even care) exactly how the Greeter object says hello. It doesn’t know exactly what the greeting will be, what language the greeting will be in, or even how the greeting will be displayed.

To illustrate this point, consider what would happen if you used the Greeter class shown in Listing 1-4 rather than the one shown in Listing 1-3. This version of the Greeter class uses a Java library class called JOptionPane to display a message in a dialog box rather than in a console window.

```java
// This class creates a Greeter object that displays
// a hello message in a dialog box.
import javax.swing.JOptionPane;

public class Greeter
{
	public void sayHello()
	{
		JOptionPane.showMessageDialog(null,
			"Hello, World!", "Greeter",
			JOptionPane.INFORMATION_MESSAGE);
	}
}
```

![[Pasted image 20240219085147.png]]

The important point to realize here is that the HelloApp2 class doesn’t have to be changed to use this new version of the Greeter class. Instead, all you have to do is replace the old Greeter class with the new one, recompile the Greeter class, and the HelloApp2 class won’t know the difference. That’s one of the main benefits of object-oriented programming.

### Importing Java API Classes
You may have noticed that the Greeter class in Listing 1-4 includes this statement:

```java
import javax.swing.JOptionPane;
```

The purpose of the import statement is to let the compiler know that the program is using a class that’s defined by the Java API called JOptionPane.

Because the Java API contains literally thousands of classes, some form of organization is needed to make the classes easier to access. Java does this by grouping classes into manageable groups called *packages*. In the previous example, the package that contains the JOptionPane class is named javax.swing.

Strictly speaking, import statements are never required. But if you don’t use import statements to import the API classes your program uses, you must *fully qualify* the names of the classes when you use them by listing the package name in front of the class name.

```java
javax.swing.JOptionPane.showMessageDialog(null,
"Hello, World!", "Greeter",
javax.swing.JOptionPane.INFORMATION_MESSAGE);
```

- import statements must appear at the beginning of the class file, before any class declarations.
- You can include as many import statements as are necessary to import all the classes used by your program.
- You can import all the classes in a particular package by listing the package name followed by an asterisk wildcard, like this:

```java
import javax.swing.*;
```

- Because many programs use the classes that are contained in the java.lang package, you don’t have to import that package. Instead, those classes are automatically available to all programs. The System class is defined in the java.lang package.
- JDK 9 introduced a new feature for managing packages called the *Java Platform Module System.*

## Working with Variables and Data Types

### Declaring Variables
In Java, you must explicitly declare all variables before using them. This rule is in contrast to some languages — most notably Python, which lets you use variables that haven’t been explicitly declared.

The basic form of a variable declaration is this:

```
type name;
```

```java
int x;
String lastName;
double radius;
```

Notice that variable declarations end with semicolons. That’s because a variable declaration is itself a type of statement.

#### Declaring two or more variables in one statement 


## Working with Numbers and Expressions

## Making Choices

## Going Around in Circles (or, Using Loops)

## Pulling a Switcheroo

## Adding Some Methods to Your Madness

## Handling Exceptions



# Object-Oriented Programming

## Understanding Object-Oriented Programming

## Making Your Own Classes

## Working with Statics

## Using Subclasses and Inheritance

## Using Abstract Classes and Interfaces

## Using the Object and Class Classes

## Using Inner Classes and Anonymous Classes

## Working with Packages and the Java Module System



# Strings and Other Data Types

## Working with Strings

## Using Regular Expressions

## Working with Dates and Times

## Using the BigDecimal Class



# Data Structures

## Introducing Data Structures

## Using Arrays

## Using the ArrayList Class

## using the LinkedList Class

## Creating Generic Collection Classes

## Using Maps and Trees



# Algorithms

## Introducing Algorithms

## Using Recursion

## Sorting 

## Searching



# Programming Techniques

## Programming Threads

## Using Functional Programming and Lambda Expressions

## Consuming Web Services with HttpClient



# JavaFX

## Hello, JavaFX!

## Handling Events

## Setting the Stage and Scene Layout

## Using Layout Panes to Arrange Your Scenes

## Getting Input from the User

## Choosing from a List





