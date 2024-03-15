# Java Basics

## Understanding Java Syntax

### Objects and Classes in Java
In Java, a class like `Cat` serves as a blueprint for creating objects —a template that defines the state and behavior bound to specific data.

For example, when we instantiate a new Cat object using `Cat tabby = new Cat();`, we bring an instance of the `Cat` class into memory, complete with attributes such as `color` and `mood`, which describe the state of the cat, and methods like `purr()`, which is an action the cat can perform.

```java
class Cat {
    String color;
    String mood;

    void purr() {
        System.out.println("Cat purrs");
    }
}
```

Constructors are specialized methods invoked at the time of object creation to initialize new objects. Java also utilizes access modifiers like `public`, `private`, and others to define the accessibility of class members, which play a crucial role in object interaction and encapsulation.

The `new` keyword is vital as it allocates memory for new `Cat` instances. Through methods, these objects can interact, influence one another, and collaborate to form complex systems.

```java
public class Cat {
    // Using 'private' to restrict access to the properties from outside this class
    private String color;
    private String mood;

    // Public constructor for Cat class
    public Cat(String color, String mood) {
        // The 'this' keyword refers to the current instance of the class
        this.color = color;
        this.mood = mood;
    }

    // Public method to access the private color field
    public String getColor() {
        return color;
    }

    // Public method to access the private mood field
    public String getMood() {
        return mood;
    }

    // Private method, only accessible within this class
    private void changeMood(String newMood) {
        mood = newMood;
    }

    // Public method to expose the behavior of the Cat object
    public void purr() {
        System.out.println("Cat purrs");
    }

    // Public method to interact with the private changeMood method
    public void makeHappy() {
        changeMood("happy");
        purr(); // The cat purrs when made happy
    }
}

// To use the class, you would create an instance of Cat using the new keyword
public class Main {
    public static void main(String[] args) {
        // Creating a new Cat object with the 'new' keyword and the constructor
        Cat myCat = new Cat("black", "sleepy");

        // Accessing the public methods of the Cat class
        System.out.println("The cat is " + myCat.getColor() + " and feels " + myCat.getMood());
        myCat.makeHappy(); // Makes the cat happy which internally changes its mood and makes it purr
    }
}
```

In Java, constructors are crucial for initializing new objects, as demonstrated by the `Cat` class's public constructor `Cat(String color, String mood)`. It's used to set the private fields `color` and `mood`.

These private fields encapsulate the state of a `Cat` object, ensuring controlled access through public methods like `getColor()` and `getMood()`. The `new` keyword is instrumental in this process, allocating memory for new instances. While the `changeMood()` method remains private for internal class use, the `purr()` method is public, allowing interaction with the cat's behavior.

### Methods in Java
Methods in Java are the actionable souls of objects. They define specific tasks that objects can perform.

In the `Cat` class shown, `void meow()` and `void scratch()` are method signatures, where `void` indicates they don't return any value, and the names `meow` and `scratch` are the actions they perform. Parentheses following the method names indicate the potential to accept inputs, which these particular methods do not require.

To activate a method, we call it on an object, like `tabby.meow();`, where `tabby` is the instance of the `Cat` class and `meow()` is the method being invoked.

Methods can encapsulate behaviors, allowing an object like `tabby` to exhibit actions such as meowing or scratching, and they can be reused to perform these actions multiple times.

This modularity not only promotes reusability but also helps maintain the integrity of an object's internal state, a cornerstone of encapsulation in object-oriented programming.

```java
public class Cat {

    // A method with no return value (void) that represents the cat's action of meowing
    public void meow() {
        // Prints "Meow!" to the console when the method is called
        System.out.println("Meow!");
    }

    // A method with no return value (void) that represents the cat's action of scratching
    public void scratch() {
        // Prints "Scratch!" to the console when the method is called
        System.out.println("Scratch!");
    }

    // Example of a method that changes the internal state of the object
    // Here, we assume a mood property is part of the Cat class
    private void changeMood(String mood) {
        // This method is private and cannot be called from outside the Cat class
    }
    
    // Additional method to demonstrate calling other methods and reusability
    public void displayBehavior() {
        meow();  // The cat meows
        scratch(); // The cat scratches
        changeMood("curious"); // The cat's mood is changed internally
    }
}

// Class containing the main method to run the program
public class Main {
    public static void main(String[] args) {
        // Creating a new Cat object using the 'new' keyword
        Cat tabby = new Cat();
        
        // Calling the public methods of the Cat class
        tabby.meow(); // Output: Meow!
        tabby.scratch(); // Output: Scratch!

        // Demonstrating the reusability of methods
        tabby.displayBehavior(); // Calls multiple methods to display behaviors
    }
}
```

### Instance Variables in Java
Instance variables capture the essence of an object's state within a Java class. In the example of a `Cat` class, the properties `name` and `age` are specific to each `Cat` object, giving each a unique identity.

```java
public class Cat {
    // Private instance variables, encapsulating the state of the Cat object
    private String name;
    private int age;

    // Constructor that initializes a Cat object with a given name and age
    public Cat(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Public getter for the name, allowing read access to the private variable
    public String getName() {
        return this.name;
    }

    // Public setter for the name, allowing write access to the private variable
    public void setName(String name) {
        this.name = name;
    }

    // Public getter for the age, allowing read access to the private variable
    public int getAge() {
        return this.age;
    }

    // Public setter for the age, allowing write access to the private variable
    public void setAge(int age) {
        this.age = age;
    }

    // Public method to display the Cat's attributes
    public void displayInfo() {
        System.out.println(this.name + " is " + this.age + " year(s) old.");
    }
}
```

Here, encapsulation is employed by making the `name` and `age` variables private, which means they cannot be accessed directly from outside the class. Instead, public getters and setters (`getName()`, `setName(String name)`, `getAge()`, and `setAge(int age)`) are provided to interact with these properties safely.

This approach not only protects the data from being changed in unintended ways but also enables a controlled interface for other classes to interact with the `Cat` objects.

### Java Basic Syntax Rules

```java
// The 'public' modifier allows this class to be accessed from other classes.
public class MyClass {
    // 'main' method: Java starts executing the program from this method.
    public static void main(String[] args) {
        // ... your code goes here
    }
}
```

When crafting a Java class:

1. **Class Declaration**: The `public` keyword specifies that the class is accessible from anywhere in the program, promoting a modular and interactive coding environment.
2. **The `main` Method**: This is where the program's execution commences. It must be `public` to be universally invokable, `static` to be callable without instantiating the class, and `void` to indicate it doesn't return any value. The `String[] args` parameter serves as a container for any command-line arguments that may be passed to the program.
3. **File Name**: The name of the source file should precisely match the class name (`MyClass` in this case) and should have the `.java` extension (hence `MyClass.java`), which is essential for the Java compiler to recognize and compile the class correctly.

# Java Data Types and Variables

## Primitive Data Types in Java

### Overview of the Eight Primitive Data Types

`int` – a commonly used type for whole numbers:

```java
int score = 100;
```

`byte` – a compact data type, great for conserving memory:

```java
byte age = 27;
```

`short`  – a tad larger than `byte` but smaller than `int`:

```java
short year = 2023;
```

`long` – for representing vast numbers:

```java
long population = 7816253000L;
```

`float` – floating-point numbers with single precision:

```java
float price = 10.99F;
```

`double` – floating-point numbers with double precision:

```java
double distance = 384.4;
```

`boolean` – the epitome of simplicity, true or false:

```java
boolean isJavaFun = true;
```

`char` – encapsulates single characters:

```java
char initial = 'J';
```

### Storage Size, Minimum and Maximum Values, and Examples
Each primitive type occupies a certain space in memory, ranging from `byte`'s modest 8 bits to `long` and `double`'s chunky 64 bits.

Likewise, they each have their own range of representable values. For instance, an `int` can stretch from `-2^31` to `2^31-1`, and a `char`, in its 16-bit purity, can represent Unicode characters.

### Overflow and Underflow

```java
int maxValue = Integer.MAX_VALUE;
int overflow = maxValue + 1;
```

## Non-primitive Data Types
Java's non-primitive data types serve as essential tools, granting programmers the flexibility to define their own data types, store multiple data items, and harness the power of method invocations.

### Types of Non-Primitive Data Types

**Class:** Think of a class as the blueprint of a building. Just as a building comprises various sections like rooms, corridors, and lobbies, a class consists of properties and methods. It's identifiable by its name and can inherit attributes and behaviors from another class, termed as a superclass.

```java
class Demo {
    int a, b;

    // Constructor
    Demo(int a, int b) {
        this.a = a;
        this.b = b;
    }

    // Method to add two numbers
    int addition() {
        return a + b;
    }

    // Method to subtract two numbers
    int subtraction() {
        return a - b;
    }
}
```

**String:** A fundamental component in Java, the String class facilitates the creation and manipulation of a sequence of characters. It's distinct from some other languages in that you don't need to use a terminating null character.

```java
String s1 = "Scaler";
String s2 = new String("Academy");
```

**Array:** If we analogize an array to a bookshelf, each slot (or index) in an array holds a specific element (or value). Crucially, every element on that particular shelf (or array) is of the same data type.

```java
int[] arr1 = {1, 2, 3};
double[] arr2 = {1.1, 2.2, 3.3};
```

**Interface:** Interfaces in Java act as a contract. They outline a set of methods without specifying their implementations. Classes that decide to "sign" this contract (that is implement the interface) are bound to provide implementations for all its methods.

```java
interface Operations {
    int addition(int a, int b);
    int subtraction(int a, int b);
}

class Solve implements Operations {
    public int addition(int a, int b) {
        return a + b;
    }

    public int subtraction(int a, int b) {
        return a - b;
    }
}
```

### Difference between Primitive and Non-Primitive Data Types

- **Origin:** Primitive types are innately defined in Java. On the contrary, non-primitive types are predominantly user-defined, with notable exceptions such as the String.
- **Value Storage:** Primitive data types are designed to hold a single value. In contrast, non-primitive types can encompass multiple values or even complex behaviors.
- **Memory Allocation:** Primitive types are allocated memory on the stack. However, for non-primitive types, the stack merely contains a reference, while the actual object resides in the heap memory.

## Type Casting in Java
Typcasting (translating one data type to another) is an integral concept in software development. You can use it to convert one type of information to another type, either explicitly (something you do yourself) or implicitly (via compiler compilation).

### What is Type Casting?
Type casting refers to the practice of changing one data type entity to another.

Also, as various sections interact within programs and compatibility issues become an issue between these components of code, type casting becomes necessary for compatibility purposes.

### Implicit Casting (Automatic)
When the conversion is risk-free and the destination type can hold the original data without loss, the compiler steps in, handling it automatically.

```java
int myInt = 9;
double myDouble = myInt;  // Implicit casting from int to double
```

### Explicit Casting (Manual)
At times, the conversion might be risky, potentially leading to data loss. Here, developers must step in, indicating the casting manually.

```java
double myDouble = 9.78;
int myInt = (int) myDouble;  // Explicit casting from double to int
```

Note that 9.78 becomes 9, and the decimal portion (.78) is discarded.

### Type Casting in Object-Oriented Programming
In OOP, casting isn't just a data play – it extends to objects and their types.

**Upcasting**: It's like looking at an object through a broader lens. A specific object (like a **`Dog`**) is viewed as a more general object (like an **`Animal`**). It's always safe.

```java
class Animal {}
class Dog extends Animal {
    void bark() {}
}

Animal myDog = new Dog();  // Upcasting the Dog object to Animal type
```

**Downcasting**: This is a tad riskier. It's about viewing a general object through a specific lens. Explicit casting is needed since there's an inherent risk.

```java
Dog myNewDog = (Dog) myDog;  // Downcasting the Animal object to Dog type
```

**Checking Object Type**: Before embarking on downcasting, it's wise to check the type to avoid runtime errors.

```java
if(myDog instanceof Dog) {
    Dog anotherDog = (Dog) myDog;
}
```

### Best Practices in Type Casting
**Caution Over Casting**: Not every situation requires casting. Only use it when necessary. Indiscriminate casting can make your code harder to read and maintain.

**Stay Vigilant**: Always be on the lookout for potential data loss. For instance, when casting float to int, remember the decimal truncation.

**Exception Handling**: Anticipate exceptions that might arise, like **`ClassCastException`**. When they do, handle them gracefully to ensure your program doesn't crash unexpectedly.

```java
try {
    Dog retrievedDog = (Dog) someAnimal;
} catch (ClassCastException e) {
    System.out.println("Failed to cast the object.");
}
```

### Common Pitfalls and How to Avoid Them
**Loss of Precision**: Remember, casting a float or double to an int truncates the decimal. Always ensure that's the desired behavior.

```java
float value = 3.14f;
int intValue = (int) value;  // intValue will be 3
```

**Overflows & Underflows**: Casting might lead to unexpected results if the value doesn't fit into the destination type.

```java
long bigNumber = 5000000000L;
int smallerNumber = (int) bigNumber;  // Potential for unexpected values
```

**ClassCastException**: Particularly in OOP languages, always check object types before attempting to downcast.

```java
if (someAnimal instanceof Dog) {
    Dog d = (Dog) someAnimal;
} else {
    System.out.println("Can't cast this animal to a Dog.");
}
```

# Java Operators and Control Statements
Operators are vital, engaged in over 70% of code logic decisions, while control statements dictate the flow, essential in around 85% of Java applications.

## Arithmetic Operators

### Basic Arithmetic Operators
**Addition (+)**: More than a mere counting mechanism, the addition operator is indispensable in aggregation tasks.

```java
int sum = 3 + 4;  // sum holds value 7
```

**Subtraction (-)**: An unsung hero when it comes to pinpointing differences or making alterations.

```java
int diff = 10 - 3;  // diff holds value 7
```

**Multiplication (`*`)**: While it can represent repeated addition, its true prowess lies in scaling and proportionate increase.

```java
int product = 7 * 3;  // product is 21
```

**Division (/)**: A tool often used to partition values.

```java
double quotient = 20.0 / 3;  // quotient is approximately 6.67
```

**Modulus (%)**: Moving past just division, modulus allows for the understanding of remainders.

```java
int remainder = 7 % 3;  // remainder is 1
```

### Unary Operators

- **Increment (++)**: A succinct way to enhance a value. It's particularly beneficial in loop counters and iterative processes.
- **Prefix**: By using **`++a`**, the value of 'a' is increased before the current operation gets executed.
- **Postfix**: With **`a++`**, the current operation utilizes 'a' before increasing its value.
- **Decrement (--)**: Serving as the inverse of increment, it methodically diminishes a value, commonly used in reverse iterations and counters.
- As with increment, prefix and postfix nuances apply to the decrement operator as well.

### Compound Assignment Operators
These operators infuse arithmetic operations with assignment.

```java
int x = 10;
x += 5;  // An elegant way of saying x = x + 5; x now holds 15
```

### The Importance of Data Types
The behavior of arithmetic operations can vary depending on the data types employed.

**Floating-point arithmetic**: While it affords precision, you need to remain vigilant about rounding errors or floating-point anomalies.

```java
double result = 10.0 / 3;  // result holds 3.3333...
```

**Integer arithmetic**: It delivers whole numbers, eschewing any decimal fractions. Ideal for countable entities but can lead to unintended truncations.

```java
int resultInt = 10 / 3;  // resultInt holds 3, the fraction is discarded
```

### Type Promotion in Expressions
Java strives to avoid accidental data loss by promoting data types in mixed-type operations. For example, an operation involving an `int` and a `double` will convert the `int` to a `double` to ensure a uniform type for accurate computation.

### Mathematical Methods & Classes
Java’s `Math` class is a reservoir of handy mathematical utilities.

`Math.pow(a, b)` efficiently computes 'a' raised to the power of 'b'.

```java
double eight = Math.pow(2, 3);  // eight holds 8.0
```

`Math.sqrt(x)` returns the square root of 'x', a common function in distance calculations and quadratic algorithms.

```java
double squareRoot = Math.sqrt(64);  // squareRoot holds 8.0
```

## Relational Operators
Relational operators, also known as comparison operators, serve as the cornerstone in the world of decision-making for developers.

Java boasts a collection of relational operators that serve the purpose of comparing two values. At their core, these operators yield a boolean outcome – either `true` or `false`:

**Equality (`==`)**: This operator states whether two values share parity.

```java
int a = 5;
boolean result = (a == 5);  // The outcome stored in 'result' is true
```

**Inequality (!=)**: As the counter to equality, it checks if two values aren't the same.

```java
int b = 7;
boolean result = (b != 5);  // Here, 'result' is true since 7 isn't 5
```

**Greater Than (>)**: It evaluates if the value on the left is greater than the one on the right.

```java
boolean check = (10 > 3);  // 'check' is true, 10 does surpass 3
```

**Less Than (<)**: This operator checks if the value on the left is smaller than the one on the right.

```java
boolean check = (2 < 8);  // As expected, 'check' is true here
```

**Greater Than or Equal to (>=)**: A dual-purpose operator, it confirms if the left value either is greater than or equal to the right.

```java
boolean equalityOrGreater = (7 >= 7);  // This yields true since 7 equals 7
```

**Less Than or Equal to (<=)**: Similarly dual-purposed, it verifies if the left value is less than or equal to the right.

```java
boolean equalityOrLess = (4 <= 5);  // 'equalityOrLess' will store true
```

### Relational Operators and Object References
Distinguishing between primitive data types and objects is vital in Java, especially when employing the `==` operator.

With primitive data types, `==` straightforwardly checks whether values are equal.

For objects, the `==` operator delves deeper, determining if both references point to an identical memory location. It doesn't evaluate content equality. Instead, you'll use the `equals()` method for that purpose.

```java
String str1 = new String("Hello");
String str2 = new String("Hello");
boolean refCheck = (str1 == str2);       // This returns false; distinct memory locations
boolean contentCheck = str1.equals(str2);  // True here since the content is identical
```

### Chaining Relational Operators
Using various relational and logical operators together can produce intricate conditions:

```java
int age = 25;
boolean isAdult = (age >= 18 && age <= 65);  // 'isAdult' stands true for ages 18 through 65
```

But there are some potential pitfalls you should be aware of:

**Floating-point Comparisons**: Precision errors can distort direct floating-point comparisons using relational operators. To sidestep this, consider comparing the absolute difference against a minuscule threshold.

```java
double result = 0.1 + 0.2;
boolean isEqual = (result == 0.3);  // False here due to precision glitches
boolean isNearlyEqual = Math.abs(result - 0.3) < 0.000001;  // True since the difference is minuscule
```

**Auto-boxing Hazards**: The quirk of auto-boxing in Java can spawn unexpected results when comparing wrapper objects:

```java
Integer num1 = 127;
Integer num2 = 127;
boolean check1 = (num1 == num2);  // True here due to integer caching within the range of -128 to 127
Integer num3 = 200;
Integer num4 = 200;
boolean check2 = (num3 == num4);  // This turns out false; they're different references
```

Practical scenarios and applications:

- **Sorting Algorithms**: Algorithms like Bubble Sort or Quick Sort lean on relational operators to determine the sequential order of elements.
- **Decision-making in Applications**: If an application is evaluating loan eligibility predicated on age and income, or sifting data in accordance with user specifications, you'll find relational operators at work.
- **Gaming**: Be it adjudging victors based on score metrics or launching events post certain milestones, relational operators sculpt the gaming narrative.

```java
public class FilterSystem {

    // Mock database entries
    private static final String[] DATABASE = {
        "Product A: Price $100, Category Electronics",
        "Product B: Price $50, Category Books",
        "Product C: Price $150, Category Electronics",
        "Product D: Price $30, Category Apparel",
        // ... more entries
    };

    public static void filterByPriceRange(int min, int max) {
        for (String entry : DATABASE) {
            String[] splitEntry = entry.split(" ");
            int price = Integer.parseInt(splitEntry[3].substring(1));  // Extract price
            if (price >= min && price <= max) {
                System.out.println(entry);
            }
        }
    }

    public static void main(String[] args) {
        filterByPriceRange(50, 150);  // Filters entries with prices between $50 and $150
    }
}
```

## Logical Operators

### Fundamental Logical Operators

- **Logical AND (&&)**: Returns true if both operands are true.

```java
boolean result = (5 > 3) && (7 < 10);  // result is true
```

- **Logical OR (||)**: Returns true if at least one of the operands is true.

```java
boolean result = (5 < 3) || (7 < 10);  // result is true
```

- **Logical NOT (!)**: Inverts the truth value of the operand.

```java
boolean result = !(5 > 3);  // result is false
```

### Short-Circuit Behavior in Java
Java supports **short-circuit evaluation** for its logical operators. This means:

- For `&&`, if the left operand is `false`, the right operand is not evaluated.
- For `||`, if the left operand is `true`, the right operand is not evaluated.

This behavior is not only efficient but can also be useful in avoiding potential runtime errors:

```java
String str = null;
if (str != null && !str.isEmpty()) {
    System.out.println("String is not empty");
} else {
    System.out.println("String is empty or null");
}
```

In the above example, using the `&&` operator ensures that `str.isEmpty()` is only called if `str` is not `null`, avoiding a potential `NullPointerException`.

### Logical Operators with Non-Boolean Values

- **Bitwise AND (&)**

```java
int result = 5 & 3;  // result is 1
```

- **Bitwise OR (|)**

```java
int result = 5 | 3;  // result is 7
```

- **Bitwise XOR (^)**: Returns 1 for differing bits and 0 for matching bits.

```java
int result = 5 ^ 3;  // result is 6
```

### Truth Tables: Deciphering Logical Operations
Understanding logical operations becomes more intuitive with **truth tables**. They map all possible truth values of inputs to their resulting outputs.

**AND (&&)**

|A|B|A && B|
|---|---|---|
|T|T|T|
|T|F|F|
|F|T|F|
|F|F|F|

**OR (||)**

|A|B|A \| B|
|---|---|---|
|T|T|T|
|T|F|T|
|F|T|T|
|F|F|F|

**NOT (!)**

|A|!A|
|---|---|
|T|F|
|F|T|

## Control Statements in Java - if, else, switch

### The `if` Statement
Every decision-making process starts with a question. The `if` statement in Java serves as this question. It evaluates a given condition: if the condition holds true, it proceeds to execute a specified block of code.

```
if (condition) {
    // Block of code to be executed if the condition is true
}
```

```java
int age = 20;
if (age >= 18) {
    System.out.println("You are eligible to vote.");
}
```

### The `if-else` Statement
Life is full of choices. Similarly, in programming, there are often two paths to take: one if a condition is met and another if it isn't. The `if-else` statement in Java caters to this type of situation.

```
if (condition) {
    // Block of code executed if condition is true
} else {
    // Block of code executed if condition is false
}
```

```java
int age = 15;
if (age >= 18) {
    System.out.println("You are eligible to vote.");
} else {
    System.out.println("You are not eligible to vote.");
}
```

### The `if-else-if` Ladder
What if there are multiple conditions to check? That's where the `if-else-if` ladder comes in handy. It allows the program to evaluate a series of conditions in sequence.

```
if (condition1) {
    // Executed if condition1 is true
} else if (condition2) {
    // Executed if condition2 is true
} else {
    // Executed if none of the above conditions hold true
}
```

```java
int marks = 75;
if (marks >= 85) {
    System.out.println("Grade A");
} else if (marks >= 70) {
    System.out.println("Grade B");
} else {
    System.out.println("Grade C");
}
```

### The `switch` Statement
When dealing with scenarios where a variable could equate to multiple known values, and each value requires different processing, the `switch` statement is your tool of choice.

```
switch (expression) {
    case value1:
        // Code executed for value1
        break;
    case value2:
        // Code executed for value2
        break;
    // You can have any number of case statements
    default:
        // Code executed if none of the cases are met
}
```

```java
int day = 2;
switch (day) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    default:
        System.out.println("Another day");
}
```

**Cautionary Note**: The `break` keyword ensures that once a match is found and its corresponding block of code is executed, the program exits the `switch` block. Omitting it could lead to unintended results as the program "falls through" to subsequent `case` blocks.

### Nested Control Statements
Just like inception, control statements can exist within other control statements.

```java
int age = 20;
boolean hasDrivingLicense = true;

if (age >= 18) {
    if (hasDrivingLicense) {
        System.out.println("You can drive a car.");
    } else {
        System.out.println("You are eligible, but you need a driving license.");
    }
} else {
    System.out.println("You are not eligible to drive.");
}
```

```java
public class BasicCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Prompt user for input
        System.out.println("Enter first number:");
        double num1 = scanner.nextDouble();

        System.out.println("Enter second number:");
        double num2 = scanner.nextDouble();

        System.out.println("Choose operation (+, -, *, /):");
        char operation = scanner.next().charAt(0);

        // Switch case for calculator operations
        switch (operation) {
            case '+':
                System.out.println("Result: " + (num1 + num2));
                break;
            case '-':
                System.out.println("Result: " + (num1 - num2));
                break;
            case '*':
                System.out.println("Result: " + (num1 * num2));
                break;
            case '/':
                if (num2 != 0) { // Avoid division by zero
                    System.out.println("Result: " + (num1 / num2));
                } else {
                    System.out.println("Cannot divide by zero!");
                }
                break;
            default:
                System.out.println("Invalid operation chosen.");
        }

        scanner.close();
    }
}
```

```java
public class TrafficLightSystem {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Prompt user for traffic light color
        System.out.println("Enter traffic light color (Red, Yellow, Green):");
        String color = scanner.nextLine().trim().toLowerCase();

        // Switch case for traffic light messages
        switch (color) {
            case "red":
                System.out.println("Stop");
                break;
            case "yellow":
                System.out.println("Prepare to stop");
                break;
            case "green":
                System.out.println("Go");
                break;
            default:
                System.out.println("Invalid color entered.");
        }

        scanner.close();
    }
}
```

```java
public class GradeClassification {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Prompt user for student score
        System.out.println("Enter student score (0-100):");
        int score = scanner.nextInt();

        // Grade classification using if-else-if ladder
        if (score >= 90 && score <= 100) {
            System.out.println("Grade A");
        } else if (score >= 80 && score < 90) {
            System.out.println("Grade B");
        } else if (score >= 70 && score < 80) {
            System.out.println("Grade C");
        } else if (score >= 60 && score < 70) {
            System.out.println("Grade D");
        } else if (score >= 0 && score < 60) {
            System.out.println("Grade F");
        } else {
            System.out.println("Invalid score entered.");
        }

        scanner.close();
    }
}
```

## Loops: for, while, do-while
Loops form the cornerstone of many algorithms and routine tasks in Java. Their primary function is to repeat a block of code multiple times, driven by specific conditions.

### The for Loop
The `for` loop provides a concise way to iterate over a range of values or elements in a collection. It's typically used when the number of iterations is known beforehand.

```
for (initialization; condition; increment/decrement) {
    // Block of code to be repeated
}
```

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

**Points to Remember:**

- Initialization: Sets a starting point for the loop.
- Condition: If this evaluates to `true`, the loop continues – otherwise, it stops.
- Increment/Decrement: Modifies the loop variable after each iteration.

### The while Loop
The **`while`** loop repeatedly executes a block of code as long as a specified condition evaluates to **`true`**.

```
while (condition) {
    // Block of code to be repeated
}
```

```java
int i = 1;
while (i <= 5) {
    System.out.println(i);
    i++;
}
```

**Points to Remember:**

Ensure the condition in a while loop eventually becomes false. Otherwise, you'll have an infinite loop.

### The do-while Loop
Similar to the `while` loop, but with a critical difference: the `do-while` loop checks its condition **after** the loop has executed, guaranteeing the loop's body will run at least once.

```
do {
    // Block of code to be repeated
} while (condition);
```

```java
int number;
do {
    System.out.println("Enter a number between 1 and 10:");
    number = scanner.nextInt();
} while (number < 1 || number > 10);
```

**Points to Remember:**

Use the `do-while` loop when the loop's body must execute at least once, regardless of the condition's initial state.

### Enhanced for-loop (for-each)
Introduced in Java 5, the enhanced for loop simplifies iterating over collections and arrays.

```
for (Type variable : collection/array) {
    // Block of code
}
```

```java
int[] numbers = {1, 2, 3, 4, 5};
for (int num : numbers) {
    System.out.println(num);
}
```

**Points to Remember:**

The enhanced for loop is read-only. This means that you cannot modify the current element during iteration.

### Loop Control Statements

- `break`: Exits the current loop immediately.
- `continue`: Skips the rest of the current iteration and proceeds to the next iteration.

```java
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        continue;
    }
    System.out.println(i);
}
```

```java
double totalSalary = 0;
int numberOfEmployees = employeesList.size();

for (Employee emp : employeesList) {
    totalSalary += emp.getSalary();
}

double averageSalary = totalSalary / numberOfEmployees;
System.out.println("Average Salary: " + averageSalary);
```

```java
while (gameIsRunning) {
    processUserInputs();  // e.g., move character, jump, etc.
    updateGameState();    // e.g., move non-player characters, update scores, etc.
    renderGraphics();     // draw the current state of the game on the screen
    delay(16);            // a simple way to aim for ~60 frames per second
}
```

```java
// Linear Search
int[] numbers = {10, 20, 30, 40, 50};
int valueToFind = 30;
boolean found = false;

for (int num : numbers) {
    if (num == valueToFind) {
        found = true;
        break;
    }
}

if (found) {
    System.out.println(valueToFind + " was found in the array.");
} else {
    System.out.println(valueToFind + " was not found in the array.");
}
```

```java
// Bubble Sort
int[] numbers = {64, 34, 25, 12, 22, 11, 90};
int n = numbers.length;

for (int i = 0; i < n-1; i++) {
    for (int j = 0; j < n-i-1; j++) {
        if (numbers[j] > numbers[j+1]) {
            // swap numbers[j] and numbers[j+1]
            int temp = numbers[j];
            numbers[j] = numbers[j+1];
            numbers[j+1] = temp;
        }
    }
}
```

```java
public class FibonacciWhileLoop {
    public static void main(String[] args) {
        int n = 10;  // Number of Fibonacci numbers to print
        int t1 = 0, t2 = 1;

        int count = 1;  // To keep track of how many numbers have been printed

        // Print the first two Fibonacci numbers
        System.out.print("First " + n + " Fibonacci numbers: " + t1 + ", " + t2);

        // Use a while loop to calculate the rest of the numbers
        while (count <= n - 2) {
            int sum = t1 + t2;
            System.out.print(", " + sum);
            t1 = t2;
            t2 = sum;
            count++;
        }
    }
}
```

```java
public class MenuDrivenProgram {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Start with a do-while loop to keep showing the menu until the user chooses to exit
        int choice;
        do {
            // Print out the menu
            System.out.println("\\nMenu:");
            System.out.println("1. Calculator");
            System.out.println("2. Conversion Tools");
            System.out.println("3. Exit");
            System.out.print("Enter your choice: ");

            choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.println("Calculator chosen!");
                    // Implement the calculator here...
                    break;
                case 2:
                    System.out.println("Conversion tools chosen!");
                    // Implement conversion tools here...
                    break;
                case 3:
                    System.out.println("Exiting the program. Goodbye!");
                    break;
                default:
                    System.out.println("Invalid choice! Please select from the menu.");
                    break;
            }
        } while (choice != 3);  // Exit when user chooses 3

        scanner.close();
    }
}
```

```java
public class FizzBuzz {
    public static void main(String[] args) {
        for (int i = 1; i <= 100; i++) { // Looping through numbers 1 to 100
            // If number is divisible by 3 and 5, print "FizzBuzz"
            if (i % 3 == 0 && i % 5 == 0) {
                System.out.println("FizzBuzz");
            }
            // If number is divisible by 3, print "Fizz"
            else if (i % 3 == 0) {
                System.out.println("Fizz");
            }
            // If number is divisible by 5, print "Buzz"
            else if (i % 5 == 0) {
                System.out.println("Buzz");
            }
            // If number is not divisible by either 3 or 5, print the number
            else {
                System.out.println(i);
            }
        }
    }
}
```

# Object-Oriented Programming (OOP)

## What is Object-Oriented Programming?
OOP (Object Oriented Programming) centers around classes and objects as the cornerstones. A class serves as the blueprint, much like architectural plans are used when constructing multiple buildings. Similarly multiple objects may be instantiated from one class.

## Classes and Objects
At its essence, a class encapsulates data for the object and methods to manipulate that data. The data, or attributes, represents the state, and the methods define behavior.

### How to Declare and Define a Class in Java
A class in Java is introduced using the `class` keyword, followed by its name.

```java
class Car {
    String color;  // attribute
    void drive() {  // method
        System.out.println("Car is driving");
    }
}
```

### Objects in Java: Instances of Classes
An object is a specific instance of a class. Each object has a unique identity but shares the structure provided by its class.

Objects are instantiated using the `new` keyword.

```java
Car myCar = new Car();
```

Post-instantiation, the object's attributes and methods can be accessed using the dot operator.

```java
myCar.color = "Red";
myCar.drive();
```

### Constructors: The Object Initializers
Constructors play a pivotal role in object instantiation, allowing for immediate attribute setting.

- **Default Constructor**: Provided by Java if no constructor is defined.
- **Parameterized Constructor**: Accepts parameters to initialize attributes.
- **Constructor Overloading**: Multiple constructors with different parameters.

```java
class Car {
    String color;
    Car() {
        this.color = "Unknown";
    }
    Car(String c) {
        this.color = c;
    }
}
```

### The this Keyword in Java
The `this` keyword refers to the current instance of an object. It's particularly useful when differentiating instance variables from method parameters.

```java
void setColor(String color) {
    this.color = color;
}
```

### Garbage Collection and Destructors
Java inherently handles memory management. Objects no longer in use are automatically cleared by the garbage collector. The `finalize()` method allows an object to clean up resources before it's removed.

### Static vs. Non-static
A **`static`** member belongs to the class itself, rather than any specific instance. For instance, a static variable will share its value across all instances of the class. Non-static members, conversely, are unique to each instance.

```java
class Car {
    static int carCount;  // static variable
    Car() {
        carCount++;
    }
```

### The Final Keyword with Classes and Objects
The `final` keyword, when applied, ensures immutability. A final variable can't be modified, a final method can't be overridden, and a final class can't be subclassed.

```java
final class ImmutableCar {}
```

```java
// The CookieCutter class represents the analogy's cookie cutter.
class CookieCutter {

    // Common shape for all cookies made using this cutter.
    String shape;

    // Constructor to initialize the shape of the cookie cutter.
    public CookieCutter(String shape) {
        this.shape = shape;
    }

    // Method to create a new cookie with the specified flavor using this cutter's shape.
    public Cookie makeCookie(String flavor) {
        return new Cookie(this.shape, flavor);
    }
}

// The Cookie class represents the cookies made using the cookie cutter.
class Cookie {

    // Every cookie will have a shape and a flavor.
    String shape;
    String flavor;

    // Constructor to initialize the shape and flavor of the cookie.
    public Cookie(String shape, String flavor) {
        this.shape = shape;
        this.flavor = flavor;
    }

    // Method to describe the cookie.
    public void describe() {
        System.out.println("This is a " + flavor + " flavored " + shape + " cookie.");
    }
}

public class CookieFactory {

    public static void main(String[] args) {

        // Creating a heart-shaped cookie cutter.
        CookieCutter heartShapedCutter = new CookieCutter("heart");

        // Using the heart-shaped cutter to create cookies with different flavors.
        Cookie chocoHeartCookie = heartShapedCutter.makeCookie("chocolate");
        Cookie vanillaHeartCookie = heartShapedCutter.makeCookie("vanilla");

        // Describing the cookies.
        chocoHeartCookie.describe();
        vanillaHeartCookie.describe();
    }
}
```

```java
// Definition of the Person class.
class Person {

    // Attributes of the Person class.
    String name;
    int age;

    // Static variable to keep count of the number of Person objects created.
    static int personCount = 0;

    // Default constructor.
    public Person() {
        personCount++; // Increment the count whenever a new Person object is created.
    }

    // Parameterized constructor using the 'this' keyword to initialize the attributes.
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
        personCount++; // Increment the count whenever a new Person object is created.
    }

    // speak() method to let the person introduce themselves.
    public void speak() {
        System.out.println("Hello! My name is " + name + " and I am " + age + " years old.");
    }

    // Static method to display the number of Person objects created.
    public static void displayCount() {
        System.out.println("Total number of persons: " + personCount);
    }
}

public class PersonTest {

    public static void main(String[] args) {

        // Instantiating three different Person objects.
        Person person1 = new Person("Alice", 25);
        Person person2 = new Person("Bob", 30);
        Person person3 = new Person("Charlie", 35);

        // Calling the speak() method for each Person object.
        person1.speak();
        person2.speak();
        person3.speak();

        // Displaying the number of Person objects created using the static method.
        Person.displayCount();
    }
}
```

## Constructors
A constructor in Java is a special block of code that initializes the newly created object. It holds the same name as its class and behaves like a method, though it doesn’t have any return type. Constructors breathe life into an object, setting initial values and ensuring that the object is in a valid state upon creation.

### Types of Constructors
**Default Constructor:** A default constructor is one without parameters. If not explicitly defined, Java provides one implicitly to ensure every class has a constructor.

```java
public class MyClass {
    // Default constructor
    public MyClass() {
        // Initialization process
    }
}
```

**Parameterized Constructor:** At times, it's beneficial to initialize an object with specific values. This is where parameterized constructors come into play.

Unlike the default constructor, parameterized constructors accept arguments to initialize the attributes of the object.

```java
public class MyClass {
    int a;
    // Parameterized constructor
    public MyClass(int x) {
        a = x;
    }
}
```

**Constructor Overloading:** Constructors can be overloaded, much like methods. This means a class can have multiple constructors, differentiated by their parameter list.

```java
public class MyClass {
    int a, b;
    // Constructor with one parameter
    public MyClass(int x) {
        a = x;
    }
    // Constructor with two parameters
    public MyClass(int x, int y) {
        a = x;
        b = y;
    }
}
```

This flexibility ensures objects can be initialized in multiple ways as per the requirement.

**`this` Keyword in Constructors:** Often, parameter names in a constructor might conflict with instance variable names. The `this` keyword helps differentiate.

```java
public class MyClass {
    int a;
    public MyClass(int a) {
        this.a = a; // Differentiating using 'this'
    }
}
```

**The `super()` Call:** The **`super()`** call proves invaluable. It invokes the parent class constructor, ensuring a structured initialization.

```java
class Parent {
    // Parent class constructor
}

class Child extends Parent {
    public Child() {
        super(); // Calling parent constructor
    }
}
```

**Copy Constructor:** A copy constructor, as the name suggests, copies the values of one object into another.

```java
public class MyClass {
    int a;
    public MyClass(MyClass obj) {
        a = obj.a; // Copying value
    }
}
```

**Chaining Constructors:** A constructor can call another constructor in the same class using this.

```java
public class MyClass {
    int a, b;
    // Default constructor
    public MyClass() {
        this(0); // Calling parameterized constructor
    }
    public MyClass(int x) {
        a = x;
    }
}
```

Constructors should remain clutter-free, focusing solely on initialization. Avoid heavy computations and, importantly, be cautious of calling overridable methods in constructors.

```java
class Base {
    // Overridable method
    void setup() {
        System.out.println("Base setup");
    }

    // Base constructor
    Base() {
        System.out.println("Base constructor");
        // Calling overridable method inside constructor
        setup();
    }
}

class Derived extends Base {
    private int value;

    // Overriding the setup method
    @Override
    void setup() {
        value = 42;
        System.out.println("Derived setup with value: " + value);
    }

    // Derived class constructor
    Derived() {
        System.out.println("Derived constructor");
    }

    public static void main(String[] args) {
        Derived d = new Derived();
        System.out.println("Derived object value: " + d.value);
    }
}
```

When you run the above code, the output will be:

```
Base constructor
Derived setup with value: 42
Derived constructor
Derived object value: 0
```

However, after everything, the value of `value` in the derived object remains 0 because instance variable initializations occur after the superclass constructor has completed but before the derived class constructor body is executed. This causes a misleading situation.

The call to the overridable method (`setup`) within the base class constructor leads to unpredictable behavior. Avoid calling overridable methods inside constructors. Always aim for constructors to be simple, straightforward, and focused solely on initialization.

```java
class Book {
    // Attributes for the Book class
    String title;
    String author;

    // Method to display book information
    void showBookInfo() {
        System.out.println("Title: " + title + ", Author: " + author);
    }

    public static void main(String[] args) {
        // Creating an object of the Book class
        Book myBook = new Book();
        myBook.title = "The Great Gatsby";
        myBook.author = "F. Scott Fitzgerald";

        // Displaying the book's details
        myBook.showBookInfo();
    }
}
```

```java
lass Book {
    String title;
    String author;

    // Default constructor initializing the attributes to "Unknown"
    Book() {
        title = "Unknown";
        author = "Unknown";
    }

    void showBookInfo() {
        System.out.println("Title: " + title + ", Author: " + author);
    }

    public static void main(String[] args) {
        // Instantiating the class without passing any arguments
        Book unknownBook = new Book();
        unknownBook.showBookInfo();  // This will print: Title: Unknown, Author: Unknown
    }
}
```

```java
class Book {
    String title;
    String author;

    // Parameterized constructor accepting title and author
    Book(String t, String a) {
        title = t;
        author = a;
    }

    void showBookInfo() {
        System.out.println("Title: " + title + ", Author: " + author);
    }

    public static void main(String[] args) {
        // Instantiating the class with specific details
        Book specificBook = new Book("1984", "George Orwell");
        specificBook.showBookInfo();  // This will print: Title: 1984, Author: George Orwell
    }
}
```

```java
class Book {
    String title;
    String author;

    Book() {
        title = "Unknown";
        author = "Unknown";
    }

    Book(String t) {
        title = t;
        author = "Unknown";
    }

    Book(String t, String a) {
        title = t;
        author = a;
    }

    void showBookInfo() {
        System.out.println("Title: " + title + ", Author: " + author);
    }

    public static void main(String[] args) {
        Book onlyTitle = new Book("Brave New World");
        onlyTitle.showBookInfo();  // This will print: Title: Brave New World, Author: Unknown

        Book fullDetails = new Book("The Hobbit", "J.R.R. Tolkien");
        fullDetails.showBookInfo();  // This will print: Title: The Hobbit, Author: J.R.R. Tolkien
    }
}
```

```java
javaCopy code
class Book {
    String title;
    String author;

    Book(String title, String author) {
        this.title = title;  // 'this' keyword differentiates instance variable from parameter
        this.author = author;
    }

    void showBookInfo() {
        System.out.println("Title: " + title + ", Author: " + author);
    }

    public static void main(String[] args) {
        Book exampleBook = new Book("Moby Dick", "Herman Melville");
        exampleBook.showBookInfo();  // This will print: Title: Moby Dick, Author: Herman Melville
    }
}
```

```java
class Parent {
    Parent(int a) {
        System.out.println("Parent Constructor with parameter: " + a);
    }
}

class Child extends Parent {
    Child(int b) {
        super(b);  // Calling the parent's parameterized constructor
        System.out.println("Child Constructor with parameter: " + b);
    }
}

public class ConstructorFlow {
    public static void main(String[] args) {
        Child obj = new Child(5);
    }
}
```

This will print:

```
Parent Constructor with parameter: 5
Child Constructor with parameter: 5
```

## Inheritance
Inheritance allows a class to acquire properties and methods belonging to another class through inheritance, creating code reusability as well as hierarchical relationships among classes.

### Advantages of using Inheritance

1. Code Reusability: Avoid redundant code by inheriting functionalities from the parent class.
2. Enhanced Readability: Hierarchical structures give a clearer, more intuitive view of related classes.
3. Improved Maintainability: Change the parent class, and the child classes get updated accordingly.

### The extends keyword
In Java, inheritance refers to a process by which one class inherits properties (attributes and methods) from another. A key feature of inheritance in this context is the `extends` keyword. It marks out hierarchical relationships between classes in an effort to streamline code, enhance reusability and establish clear lineage among related classes.

When a class inherits from another, two main roles are defined:

1. **Superclass (or Parent Class):** This class acts as the source for inheritance. Its blueprint forms the basis from which subsequent classes inherit attributes or methods from.
2. **Subclass (or Child class):** This is the class that does the inheriting. It will naturally incorporate all non-private properties and methods from its superclass and can also have additional properties and methods of its own.

As an example, consider the Vehicle class with attributes and methods like color and start().

If we wanted to create more specific classes such as Car instead of recreating everything from scratch, instead we can have Car extend Vehicle. It would then automatically include its color attribute, start() method as well as possible specific attributes like numberOfDoors for this example Car class.

### Basic Inheritance

- **Parent and Subclass Relations:** Central to inheritance is the relationship between parent and child classes. For instance, inheritor subclass inherits all accessible attributes and methods from its superclass. This creates a clear lineage from one class to the other – for instance all physicians fall under Human's subclass but not all humans fall within Doctor.
- **Utilizing Attributes and Methods from the Parent Class:** When inheriting from a parent class, its attributes and methods become accessible (with some access-level restrictions). This means that when used directly without having to redefine them first. Also, inheritant classes can extend or override these properties for their unique requirements.

Real-world example to illustrate this idea: Consider an experienced artist. Their apprentice doesn't begin their learning from scratch – rather, leveraging foundational skills taught by their artist (superclass), they then add their unique flair, creating their masterpiece (subclass).

```java
class Animal {
    String name;
    String species;

    // Constructor
    public Animal(String name, String species) {
        this.name = name;
        this.species = species;
    }
}

class Dog extends Animal {
    // Constructor
    public Dog(String name, String species) {
        super(name, species);
    }

    void bark() {
        System.out.println(name + " is barking!");
    }
}

    public static void main(String[] args) {
        Dog myDog = new Dog("Buddy", "Golden Retriever");
        System.out.println(myDog.name);  // Outputs: Buddy
        System.out.println(myDog.species);  // Outputs: Golden Retriever
        myDog.bark();  // Outputs: Buddy is barking!
    }
}
```

**Method Overriding:** Method overriding allows a subclass to provide its unique version of a method already defined in its superclass. For instance, a `Bird` superclass might have a method `sound()`, which returns "Bird makes a sound". A `Sparrow` subclass can override this to return "Sparrow chirps", reflecting its specific behavior.

```java
class Bird {
    // Method in the superclass
    String sound() {
        return "Bird makes a sound";
    }
}

class Sparrow extends Bird {
    // Overriding the method from superclass
    @Override
    String sound() {
        return "Sparrow chirps";
    }
}

public class OverrideExample {
    public static void main(String[] args) {
        Sparrow mySparrow = new Sparrow();
        System.out.println(mySparrow.sound());  // This will print "Sparrow chirps"
    }
}
```

**Method Overloading vs. Method Overriding:** Method overloading lets a class have several methods with the same name but different parameters, allowing varied actions based on parameters.

In contrast, method overriding enables a subclass to offer a distinct behavior for an inherited method.

For instance, a `Calculator` might have overloaded `add()` methods for two or three integers, whereas a subclass `ScientificCalculator` could override the `sqrt()` method to modify its behavior.

```java
class Calculator {
    // Method overloading - same method name with different parameters
    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}

class ScientificCalculator extends Calculator {
    // Overriding the method to modify its behavior in the subclass
    @Override
    int add(int a, int b) {
        return a + b + 10;  // Just for illustration: adding 10 to the result
    }
}

public class OverloadOverrideExample {
    public static void main(String[] args) {
        ScientificCalculator myCalc = new ScientificCalculator();
        System.out.println(myCalc.add(5, 3));       // This will print 18 because of the overridden method
        System.out.println(myCalc.add(5, 3, 2));   // This will print 10 because of method overloading
```

**The `@Override` Annotation:** The `@Override` annotation in Java indicates that a method is meant to override one in its superclass. It's a safeguard, ensuring that the overriding is intentional and correctly done, helping catch errors during compile time.

```java
class Printer {
    void print() {
        System.out.println("Printing from base class");
    }
}

class LaserPrinter extends Printer {
    // Using the @Override annotation to signify intention to override
    @Override
    void print() {
        System.out.println("Laser printing in progress");
    }
}

public class OverrideAnnotationExample {
    public static void main(String[] args) {
        LaserPrinter lp = new LaserPrinter();
        lp.print();  // This will print "Laser printing in progress"
    }
}
```

### Constructors in Inheritance
**Chain of Constructor Calls:** Whenever an object of a subclass is instantiated, its constructor does not just run in isolation. Instead, a series of constructor calls are initiated that traverse from topmost superclass down to actual subclass being instantiated.

Imagine having a hierarchy composed of Grandparent, Parent (that extends Grandparent), and Child classes. When creating objects from this class (Child), its constructor will first call Grandparent's constructor before proceeding onward to Parent and then finally Child. This ensures the inheritance chain starts off correctly.

```java
class Grandparent {
    Grandparent() {
        System.out.println("Grandparent's constructor called.");
    }
}

class Parent extends Grandparent {
    Parent() {
        System.out.println("Parent's constructor called.");
    }
}

class Child extends Parent {
    Child() {
        System.out.println("Child's constructor called.");
    }
}

public class ConstructorChainExample {
    public static void main(String[] args) {
        new Child();  // This will print messages from all three constructors in the order: Grandparent, Parent, Child
    }
}
```

**Use of `super()` to Call Parent Class Constructor:** In Java, `super()` can be used within subclass constructors to call their parent class's constructor. By default, Java will insert an indirect call for you via no-argument `super`. When there's an optional parameterized constructor it's essential that `super` be called with its exact arguments to invoke its constructor correctly.

```java
class Parent {
    Parent(String message) {
        System.out.println(message);
    }
}

class Child extends Parent {
    Child() {
        super("Parent's constructor called with a message.");  // Explicitly calling parent's constructor with a message
        System.out.println("Child's constructor called.");
    }
}

public class SuperExample {
    public static void main(String[] args) {
        new Child();  // This will print both messages: one from the Parent's constructor and one from the Child's constructor
    }
}
```

As shown above, the Child class's constructor explicitly calls its parent class's constructor using `super()` with all required arguments passed as parameters.

### How to Access Superclass Methods
Consider a scenario where we have a `Vehicle` class with a method `description()`, and a `Car` class that extends `Vehicle`. The `Car` class wants to provide additional details in the description but also wants to keep the basic details provided by the `Vehicle` class. This is where `super` comes into play.

```java
class Vehicle {
    void description() {
        System.out.println("This is a generic vehicle.");
    }
}

class Car extends Vehicle {
    @Override
    void description() {
        super.description();  // Calling the parent class's description method
        System.out.println("More specifically, this is a car.");
    }
}

public class SuperUsageExample {
    public static void main(String[] args) {
        Car car = new Car();
        car.description();
        // Output:
        // This is a generic vehicle.
        // More specifically, this is a car.
    }
}
```

### Multiple Inheritance

```java
interface Person {
    void displayPersonDetails();
}

interface Address {
    void displayAddressDetails();
}

class Contact implements Person, Address {
    // Define attributes for both interfaces and provide implementation for both methods
    // This exercise illustrates how one class can inherit from multiple interfaces.
}
```

## Polymorphism
Polymorphism – from Greek words meaning many forms – is an indispensable concept in Object-Oriented Programming (OOP). It serves to ensure that all entities of different types behave similarly when interacting together, adding depth to OOP concepts like class hierarchy.

At its core, polymorphism enables us to view objects of diverse classes as instances of one superclass, creating adaptability within code. This flexibility helps facilitate better reusability. Common behavior can be easily inherited while deviations managed seamlessly. It also improves the readability of code while opening doors for scalable software solutions.

### Types of Polymorphism

- **Compile-time Polymorphism (Static Polymorphism)**: This type of polymorphism is achieved when we overload a method.

```java
void print(int a) { ... }
void print(double b) { ... }
```

Here, the method's name remains the same, but the parameter lists vary – this distinction in parameters is known as method signatures.

- **Run-time Polymorphism (Dynamic Polymorphism)**: This involves overriding methods from a superclass in its subclass.

```java
class Animal {
   void sound() { ... }
}

class Dog extends Animal {
   void sound() { ... }
}
```

At runtime, Java uses the object's actual class (like Dog) to determine which version of an overridden method should execute.

### Casting in Polymorphism

- **Upcasting**: This involves casting an object to one of its superclass types. Being an implicit conversion, it's safe.

```java
Dog myDog = new Dog();
Animal myAnimal = myDog;  // Upcasting
```

- **Downcasting**: Here, we cast an object to one of its subclass types. It must be done explicitly due to potential risks.

```java
Animal myAnimal = new Dog();
Dog myDog = (Dog) myAnimal;  // Downcasting
```

### The Utility of the instanceof Operator
The `instanceof` operator is integral for type verification, often used before downcasting to prevent unwarranted `ClassCastException`.

```java
if (myAnimal instanceof Dog) {
   Dog myDog = (Dog) myAnimal;
}
```

### Benefits of Polymorphism

- **Reusability**: With Polymorphism, code components can be leveraged across multiple classes, curtailing redundancy.
- **Extensibility**: As business needs evolve, Polymorphism ensures minimal disruptions when expanding functionalities.
- **Flexibility**: Modules remain distinct, making systems more manageable.
- **Simplified Design**: Systems designed with Polymorphism are inherently organized and intuitive.
- **Interchangeability**: With Polymorphism, varying implementations can be switched seamlessly.
- **Enhanced Maintainability**: With standardized structures, tasks like debugging and updates become less cumbersome.

```java
// The superclass Animal has a method sound(), which provides a generic implementation.
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

// Dog is a subclass of Animal and overrides the sound() method.
class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

// Cat is another subclass of Animal and also overrides the sound() method.
class Cat extends Animal {
    @Override
    void sound() {
        System.out.println("Cat meows");
    }
}

// This class demonstrates polymorphism.
// We're able to treat both Dog and Cat as Animal and call the sound() method.
public class TestPolymorphism {
    public static void main(String[] args) {
        Animal a;  // Reference variable of type Animal

        a = new Dog();  // a now refers to a Dog object
        a.sound();  // Calls the Dog's overridden sound() method

        a = new Cat();  // a now refers to a Cat object
        a.sound();  // Calls the Cat's overridden sound() method
    }
}
```

```java
// Abstract class defining the contract for payment methods.
abstract class PaymentMethod {
    abstract void pay(double amount);
}

// CreditCard is a concrete subclass that provides an implementation of the pay() method.
class CreditCard extends PaymentMethod {
    @Override
    void pay(double amount) {
        System.out.println("Paid $" + amount + " using Credit Card.");
    }
}

// PayPal is another concrete subclass with its own implementation of pay().
class PayPal extends PaymentMethod {
    @Override
    void pay(double amount) {
        System.out.println("Paid $" + amount + " using PayPal.");
    }
}

// Demonstrates polymorphism by treating both CreditCard and PayPal as PaymentMethod.
public class PaymentTest {
    public static void main(String[] args) {
        PaymentMethod p;  // Reference of type PaymentMethod

        p = new CreditCard();  // p now refers to a CreditCard object
        p.pay(100.50);  // Calls CreditCard's implementation of pay()

        p = new PayPal();  // p now refers to a PayPal object
        p.pay(200.75);  // Calls PayPal's implementation of pay()
    }
}
```

```java
// Interface for elements that respond to click events.
interface OnClickListener {
    void onClick();
}

// Abstract superclass defining a contract for all UI elements.
abstract class UIElement {
    abstract void draw();
    abstract void setOnClickListener(OnClickListener listener);
}

// Button is a subclass of UIElement and also implements OnClickListener.
// Demonstrates multiple polymorphism (with both superclass and interface).
class Button extends UIElement implements OnClickListener {
    private OnClickListener listener;

    @Override
    void draw() {
        System.out.println("Drawing a button...");
    }

    @Override
    public void setOnClickListener(OnClickListener listener) {
        this.listener = listener;
    }

    // Simulates a click event.
    void click() {
        if(listener != null) {
            listener.onClick();
        }
    }

    @Override
    public void onClick() {
        System.out.println("Button was clicked!");
    }
}

// Dropdown is another subclass of UIElement.
// It can potentially implement OnClickListener but for brevity, it's omitted here.
class Dropdown extends UIElement {
    @Override
    void draw() {
        System.out.println("Drawing a dropdown...");
    }

    @Override
    public void setOnClickListener(OnClickListener listener) {
        // Potential implementation for dropdown click.
    }
}

// Test class to demonstrate polymorphism in action, especially with interfaces.
public class UIElementTest {
    public static void main(String[] args) {
        Button btn = new Button();
        btn.draw();
        btn.setOnClickListener(btn);  // Setting the button itself as the click listener
        btn.click();
    }
}

```

In these examples, polymorphism allows us to write code that treats objects of different classes as objects of a common superclass or interface.

## Encapsulation
Among the foundational quartet of OOP principles, encapsulation primarily focuses on bundling the data and operations on that data into a single unit. This ensures that objects maintain their integrity by preventing unauthorized access and modifications.

Beyond just a programming technique, encapsulation is indispensable in fostering secure coding practices and achieving a modular software design.

### How Encapsulation Works
At its core, encapsulation is about data protection and controlled access.

### How to Implement Encapsulation
Java provides us with access modifiers to enforce encapsulation. The most restrictive of these is `private`, ensuring that class members are only accessible within that class. By declaring variables as private, we can shield them from unintended external interference.

```java
private int age;

public int getAge() {
    return age;
}

public void setAge(int age) {
    if (age > 0) {
        this.age = age;
    }
}
```

### Benefits of Encapsulation
**Control**: Using encapsulation, we can add conditions to control how data is accessed or modified.

```java
public class Account {
    private double balance;

    // Getter method for balance
    public double getBalance() {
        return balance;
    }

    // Setter method to control the deposit operation
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        } else {
            System.out.println("Invalid deposit amount!");
        }
    }

    // Setter method to control the withdraw operation
    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
        } else {
            System.out.println("Invalid withdrawal amount!");
        }
    }
}
```

**Flexibility and Maintenance**: By encapsulating data, any internal changes to a class won't directly affect its interactions with other classes.

```java
public class Vehicle {
    private int speed;

    // Now, if we decide to measure speed in terms of mph instead of kph in the future,
    // we just have to change this class without affecting classes that use `Vehicle`.
    public int getSpeedInMph() {
        return speed * 5/8; // converting kph to mph
    }

    public void setSpeed(int speed) {
        this.speed = speed;
    }
}

public class Race {
    public void startRace(Vehicle v1, Vehicle v2) {
        // Uses Vehicle class but is not dependent on how Vehicle internally represents speed.
        int diff = v1.getSpeedInMph() - v2.getSpeedInMph();
        System.out.println("Speed difference is: " + diff + " mph");
    }
}
```

**Increased Security**: Shielding class members and only allowing them to be changed through controlled methods ensures security.

```java
public class PasswordManager {
    private String encryptedPassword;

    public void setPassword(String password) {
        // Assuming encrypt() is a method that encrypts the password.
        this.encryptedPassword = encrypt(password);
    }

    public boolean validatePassword(String password) {
        return encrypt(password).equals(encryptedPassword);
    }

    private String encrypt(String data) {
        // Encryption logic here
        return /* encrypted data */;
    }
}
```

**Modular Approach**: Encapsulation allows a system to be split into clear, well-defined modules, which can then be developed and maintained separately.

```java
// User module
public class User {
    private String name;
    private String email;

    // getters and setters
}

// Product module
public class Product {
    private String productId;
    private String description;

    // getters and setters
}

// Billing module
public class Invoice {
    private User user;
    private Product product;
    private double amount;

    // getters and setters
}
```

Each of these modules (User, Product, Invoice) can be developed, expanded, or maintained independently of the others.

### Advanced Encapsulation Concepts
Creating immutable classes ensures that once an object is created, it cannot be altered. This is achieved by making all members final and providing no setters.

The `final` keyword can also restrict inheritance and prevent method overriding, adding another layer of encapsulation.

While encapsulation focuses on bundling data and its operations, abstraction, another OOP principle, emphasizes hiding complex implementations and exposing only relevant features. Although intertwined, they serve distinct roles.

```java
// Creating immutable class in Java using final keyword
public final class ImmutableClass {
    private final String name;

    public ImmutableClass(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    // No setter methods – this makes the class immutable
}

// Using final keyword to prevent method overriding
class ParentClass {
    public final void showFinalMethod() {
        System.out.println("This is a final method from ParentClass");
    }
}

class ChildClass extends ParentClass {
    // Attempting to override the final method from parent class would result in a compile-time error
    // public void showFinalMethod() {
    //     System.out.println("Trying to override final method");
    // }
}
```

### Common Mistakes and Pitfalls
**Failing to validate data in setter methods can lead to inconsistencies**. Consider a `Person` class with an `age` field. We should validate data in the setter method to ensure the `age` can't be set to a negative value.

```java
public class Person {
    private int age;

    public void setAge(int age) {
        if(age < 0) {
            System.out.println("Age can't be negative.");
        } else {
            this.age = age;
        }
    }
}
```

**Overexposing class details dilutes the essence of encapsulation.** If we have a `BankAccount` class with a `balance` field, we shouldn't expose this detail directly. Instead, we can provide public methods to deposit, withdraw and check the balance.

```java
public class BankAccount {
    private double balance;

    public void deposit(double amount) {
        if(amount > 0) {
            balance += amount;
        }
    }

    public void withdraw(double amount) {
        if(amount > 0 && amount <= balance) {
            balance -= amount;
        }
    }

    public double checkBalance() {
        return balance;
    }
}
```

**Underutilizing or misusing access modifiers can compromise data integrity.** If we have a `Car` class with `speed` field, we should declare it as `private` to prevent uncontrolled access. We can then provide public getter and setter methods to control how `speed` is accessed and modified.

```java
public class Car {
    private int speed;

    public int getSpeed() {
        return speed;
    }

    public void setSpeed(int speed) {
        if(speed >= 0) {
            this.speed = speed;
        }
    }
}
```

## Abstraction
Abstraction in object-oriented programming (OOP) is an integral component that allows developers to streamline complex systems while keeping focus on essential details. Abstraction involves extracting relevant data while hiding irrelevant implementation details.

Abstraction can help with designing modular and maintainable software by providing a clear separation between internal implementation and outside world.

Developers can then define abstract classes and interfaces which serve as blueprints to create objects properly while assuring smooth implementation of objects created through abstraction.

### Creating Modular Code
Abstracting allows developers to break complex systems down into manageable modules for easier understanding and updating of codebases.

```java
// Abstract Module class
abstract class Module {
    // Abstract method to perform module-specific functionality
    public abstract void performAction();
}

// Concrete LoginModule
class LoginModule extends Module {
    @Override
    public void performAction() {
        System.out.println("LoginModule: User logged in successfully.");
        // Add login logic here
    }
}

// Concrete PaymentModule
class PaymentModule extends Module {
    @Override
    public void performAction() {
        System.out.println("PaymentModule: Payment processed.");
        // Add payment processing logic here
    }
}

public class ModularCodeExample {
    public static void main(String[] args) {
        // Create instances of modules
        Module loginModule = new LoginModule();
        Module paymentModule = new PaymentModule();

        // Perform actions using the modules
        loginModule.performAction(); // Perform login
        paymentModule.performAction(); // Process payment
    }
}
```

This example demonstrates how abstraction allows us to write modular code by defining a clear interface (`Module`), then implementing specific functionalities as separate modules (`LoginModule` and `PaymentModule`).

### Encapsulating Complexity
Abstraction helps in encapsulating complexity by separating the high-level behavior from the intricate implementation details. By defining abstract classes and methods, developers can specify common behavior and provide a clear interface for interacting with the underlying system.

```java
// Abstract Shape class defining common behavior
abstract class Shape {
    // Abstract method to calculate the area of the shape
    public abstract double calculateArea();
}

// Concrete Circle class
class Circle extends Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

// Concrete Rectangle class
class Rectangle extends Shape {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public double calculateArea() {
        return width * height;
    }
}

public class AbstractionExample {
    public static void main(String[] args) {
        // Create instances of shapes
        Shape circle = new Circle(5.0);
        Shape rectangle = new Rectangle(4.0, 6.0);

        // Calculate and display the areas
        System.out.println("Area of Circle: " + circle.calculateArea());
        System.out.println("Area of Rectangle: " + rectangle.calculateArea());
    }
}
```

### Promoting Code Reusability
One of the major advantages of abstraction is code reuse. By creating abstract classes with common behaviors and inheriting them into subclasses, developers can build a basis that can be reused across several subclasses quickly. This saves both time and effort during development processes while creating consistency in software applications by standardizing common practices.

```java
// Abstract Vehicle class defining common behavior
abstract class Vehicle {
    private String make;
    private String model;

    public Vehicle(String make, String model) {
        this.make = make;
        this.model = model;
    }

    // Abstract method for starting the vehicle
    public abstract void start();

    // Abstract method for stopping the vehicle
    public abstract void stop();

    public String getMake() {
        return make;
    }

    public String getModel() {
        return model;
    }
}

// Concrete Car class
class Car extends Vehicle {
    public Car(String make, String model) {
        super(make, model);
    }

    @Override
    public void start() {
        System.out.println("Car started.");
    }

    @Override
    public void stop() {
        System.out.println("Car stopped.");
    }
}

// Concrete Motorcycle class
class Motorcycle extends Vehicle {
    public Motorcycle(String make, String model) {
        super(make, model);
    }

    @Override
    public void start() {
        System.out.println("Motorcycle started.");
    }

    @Override
    public void stop() {
        System.out.println("Motorcycle stopped.");
    }
}

public class CodeReuseExample {
    public static void main(String[] args) {
        // Create instances of vehicles
        Vehicle car = new Car("Toyota", "Camry");
        Vehicle motorcycle = new Motorcycle("Honda", "CBR 1000RR");

        // Start and stop the vehicles
        car.start();
        car.stop();

        motorcycle.start();
        motorcycle.stop();
    }
}
```

### Enabling Future Extensibility
Abstraction allows developers to construct software systems that are easily extensible. Utilizing abstract classes and interfaces, developers can design code to be open to future modifications and additions without disrupting existing codebases or disrupting future requirements.

**Version 1 (Before Extension):**

```java
// Abstract Shape class representing a basic shape
abstract class Shape {
    public abstract double calculateArea();
}

// Concrete Circle class
class Circle extends Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

// Concrete Rectangle class
class Rectangle extends Shape {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public double calculateArea() {
        return width * height;
    }
}

public class AbstractionExampleBeforeExtension {
    public static void main(String[] args) {
        Circle circle = new Circle(5.0);
        Rectangle rectangle = new Rectangle(4.0, 6.0);

        System.out.println("Area of Circle: " + circle.calculateArea());
        System.out.println("Area of Rectangle: " + rectangle.calculateArea());
    }
}
```

**Version 2 (After Extension):**

```java
// Abstract Shape class representing a basic shape
abstract class Shape {
    public abstract double calculateArea();
}

// Concrete Circle class
class Circle extends Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

// Concrete Rectangle class
class Rectangle extends Shape {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public double calculateArea() {
        return width * height;
    }
}

// Concrete Triangle class (new shape added)
class Triangle extends Shape {
    private double base;
    private double height;

    public Triangle(double base, double height) {
        this.base = base;
        this.height = height;
    }

    @Override
    public double calculateArea() {
        return 0.5 * base * height;
    }
}

public class AbstractionExampleAfterExtension {
    public static void main(String[] args) {
        Circle circle = new Circle(5.0);
        Rectangle rectangle = new Rectangle(4.0, 6.0);
        Triangle triangle = new Triangle(3.0, 4.0);

        System.out.println("Area of Circle: " + circle.calculateArea());
        System.out.println("Area of Rectangle: " + rectangle.calculateArea());
        System.out.println("Area of Triangle: " + triangle.calculateArea());
    }
}
```

# Advanced Java Concepts

## Interfaces
An interface acts as a contract that specifies which methods a class must implement. It serves as an authoritative blueprint that ensures classes adhere to specific behaviors or functionalities.

Interfaces serve to establish loosely coupled relationships between classes.

One key concept associated with interfaces is their IS-A relationship. A class that implements an interface in Java is considered an implementation of that interface type. This means it inherits all its methods and must provide concrete implementations for them all.

So for instance, say we have an interface called `Shape`, with an implementation for its method called `calculateArea`. All classes implementing the `Shape` interface must provide their own implementation of `calculateArea`, so different shapes, such as circles or rectangles, have their own area calculation logic.

Interfaces only declare methods – they don't provide implementation details. Instead, they serve as contracts that classes must abide by in order to conform to a standardized behavior or functionality.

### Syntax for Java Interfaces
To declare an interface in Java, you use the interface keyword followed by its name – for instance "foo".

**Example 1: Basic Interface Declaration**

```java
// Declare an interface named Printable
interface Printable {
    void print(); // An abstract method with no implementation
}
```

**Example 2: Interface with Constants**

```java
// Declare an interface named Constants
interface Constants {
    // Declare constant variables (implicitly public, static, and final)
    int MAX_VALUE = 100;
    String APP_NAME = "MyApp";
}
```

**Example 3: Interface Inheritance**

```java
// Declare an interface named Drawable
interface Drawable {
    void draw();
}

// Another interface that extends Drawable
interface Resizable extends Drawable {
    void resize();
}
```

**Example 4: Implementing an Interface in a Class**

```java
// Define an interface named Shape
interface Shape {
    void draw(); // Abstract method
}

// Create a class Circle that implements the Shape interface
class Circle implements Shape {
    @Override
    public void draw() {
        System.out.println("Drawing a Circle");
    }
}
```

**Example 5: Multiple Interface Implementation**

```java
// Declare two interfaces
interface Printable {
    void print();
}

interface Displayable {
    void display();
}

// A class that implements both Printable and Displayable interfaces
class Document implements Printable, Displayable {
    @Override
    public void print() {
        System.out.println("Printing document...");
    }

    @Override
    public void display() {
        System.out.println("Displaying document...");
    }
}
```

**Example 6: Interface with Default Method**

```java
// Declare an interface with a default method
interface Logger {
    void log(String message);

    // Default method with an implementation
    default void logError(String error) {
        System.err.println("Error: " + error);
    }
}

// A class that implements the Logger interface
class FileLogger implements Logger {
    @Override
    public void log(String message) {
        System.out.println("Logging: " + message);
    }
}
```

**Example 7: Interface with Static Method**

```java
// Declare an interface with a static method
interface MathOperations {
    int add(int a, int b);

    // Static method
    static int multiply(int a, int b) {
        return a * b;
    }
}

// A class that implements the MathOperations interface
class Calculator implements MathOperations {
    @Override
    public int add(int a, int b) {
        return a + b;
    }
}
```

**Example 8: Functional Interface (Single Abstract Method)**

```java
// Declare a functional interface with a single abstract method
@FunctionalInterface
interface Calculator {
    int calculate(int a, int b);
}

// Using a lambda expression to implement the functional interface
public class Main {
    public static void main(String[] args) {
        Calculator addition = (a, b) -> a + b;
        System.out.println("Addition: " + addition.calculate(5, 3));
    }
}
```

### Uses of Interfaces in Java

#### Code Modularity
Interfaces provide many benefits to code modularity. By creating an interface contract between classes and methods implementation, ensuring consistent behavior and implementations that ease maintenance efforts as classes can be updated independently without disrupting overall program functionality.

```java
// Define an interface for Drawable objects
interface Drawable {
    void draw();
}

// Class representing a Circle that implements the Drawable interface
class Circle implements Drawable {
    @Override
    public void draw() {
        System.out.println("Drawing a Circle");
    }
}

// Class representing a Rectangle that implements the Drawable interface
class Rectangle implements Drawable {
    @Override
    public void draw() {
        System.out.println("Drawing a Rectangle");
    }
}

public class Main {
    public static void main(String[] args) {
        // Create instances of Circle and Rectangle
        Drawable circle = new Circle();
        Drawable rectangle = new Rectangle();

        // Draw shapes without knowing their specific implementations
        circle.draw();
        rectangle.draw();
    }
}
```

```java
// Define a basic interface for Drawable objects
interface Drawable {
    void draw();
}

// Define an interface for Modifiable shapes with additional methods
interface ModifiableShape extends Drawable {
    void setSize(double width, double height);
    void setColor(String color);
}

// Class representing a Circle that implements ModifiableShape
class Circle implements ModifiableShape {
    private double radius;
    private String color;

    public Circle(double radius, String color) {
        this.radius = radius;
        this.color = color;
    }

    @Override
    public void setSize(double width, double height) {
        this.radius = Math.max(width, height) / 2;
    }

    @Override
    public void setColor(String color) {
        this.color = color;
    }

    @Override
    public void draw() {
        System.out.println("Drawing a Circle with radius " + radius + " and color " + color);
    }
}

// Class representing a Rectangle that implements ModifiableShape
class Rectangle implements ModifiableShape {
    private double width;
    private double height;
    private String color;

    public Rectangle(double width, double height, String color) {
        this.width = width;
        this.height = height;
        this.color = color;
    }

    @Override
    public void setSize(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public void setColor(String color) {
        this.color = color;
    }

    @Override
    public void draw() {
        System.out.println("Drawing a Rectangle with dimensions " + width + "x" + height + " and color " + color);
    }
}

public class Main {
    public static void main(String[] args) {
        // Create instances of Circle and Rectangle
        ModifiableShape circle = new Circle(5.0, "Red");
        ModifiableShape rectangle = new Rectangle(4.0, 6.0, "Blue");

        // Modify and draw shapes without knowing their specific implementations
        circle.setSize(8.0, 8.0);
        circle.setColor("Green");
        circle.draw();

        rectangle.setSize(5.0, 7.0);
        rectangle.setColor("Yellow");
        rectangle.draw();
    }
}
```

#### Enabling Multiple Inheritance
While Java classes support only single inheritance, interfaces allow multiple inheritance.

```java
// Define an interface for swimmable objects
interface Swimmable {
    void swim();
}

// Define an interface for flyable objects
interface Flyable {
    void fly();
}

// Class representing a Bird that implements both Swimmable and Flyable interfaces
class Bird implements Swimmable, Flyable {
    @Override
    public void swim() {
        System.out.println("Bird is swimming.");
    }

    @Override
    public void fly() {
        System.out.println("Bird is flying.");
    }
}

public class Main {
    public static void main(String[] args) {
        Bird bird = new Bird();

        // Demonstrate multiple inheritance
        bird.swim();
        bird.fly();
    }
}
```

```java
// Define interfaces for different robot capabilities
interface Walkable {
    void walk();
}

interface Flyable {
    void fly();
}

interface Swimmable {
    void swim();
}

// Class representing a Robot that can combine multiple capabilities through interfaces
class Robot implements Walkable, Flyable, Swimmable {
    @Override
    public void walk() {
        System.out.println("Robot is walking.");
    }

    @Override
    public void fly() {
        System.out.println("Robot is flying.");
    }

    @Override
    public void swim() {
        System.out.println("Robot is swimming.");
    }
}

public class Main {
    public static void main(String[] args) {
        Robot robot = new Robot();

        // Demonstrate the robot's capabilities
        robot.walk();
        robot.fly();
        robot.swim();
    }
}
```

#### Polymorphism and Interface Implementation
Interfaces enable polymorphism in Java by permitting objects to be treated as instances of their implementing interfaces.

Interfaces provide the opportunity to define common functionality that multiple classes can implement to improve overall code structure.

```java
// Define an interface for shapes
interface Shape {
    double calculateArea();
}

// Class representing a Circle that implements the Shape interface
class Circle implements Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

// Class representing a Rectangle that implements the Shape interface
class Rectangle implements Shape {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public double calculateArea() {
        return width * height;
    }
}

public class Main {
    public static void main(String[] args) {
        // Create instances of Circle and Rectangle
        Shape circle = new Circle(5.0);
        Shape rectangle = new Rectangle(4.0, 6.0);

        // Calculate and print the areas without knowing the specific implementations
        System.out.println("Area of Circle: " + circle.calculateArea());
        System.out.println("Area of Rectangle: " + rectangle.calculateArea());
    }
}
```

**Advanced Example: Dynamic Polymorphism with Interfaces**

```java
// Define an interface for shapes
interface Shape {
    double calculateArea();
}

// Class representing a Circle that implements the Shape interface
class Circle implements Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

// Class representing a Rectangle that implements the Shape interface
class Rectangle implements Shape {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public double calculateArea() {
        return width * height;
    }
}

// Class to calculate the total area of a list of shapes
class ShapeCalculator {
    public static double calculateTotalArea(List<Shape> shapes) {
        double totalArea = 0.0;
        for (Shape shape : shapes) {
            totalArea += shape.calculateArea();
        }
        return totalArea;
    }
}

public class Main {
    public static void main(String[] args) {
        // Create a list of shapes
        List<Shape> shapes = new ArrayList<>();
        shapes.add(new Circle(5.0));
        shapes.add(new Rectangle(4.0, 6.0));

        // Calculate and print the total area using dynamic polymorphism
        double totalArea = ShapeCalculator.calculateTotalArea(shapes);
        System.out.println("Total Area of Shapes: " + totalArea);
    }
}
```

#### API Design and Abstraction
Interfaces are frequently employed in API design to specify contracts for other developers to abide by when implementing an interface. This creates abstraction and provides a separation between contract fulfillment and its implementation. This also helps developers to focus on class behavior rather than specific implementation details.

**Basic Example: API Design with Interfaces**

```java
// Define an interface for establishing a database connection
interface DatabaseConnection {
    void connect();
    void disconnect();
}

// A class that implements the DatabaseConnection interface for MySQL
class MySQLConnection implements DatabaseConnection {
    @Override
    public void connect() {
        System.out.println("Connected to MySQL database");
    }

    @Override
    public void disconnect() {
        System.out.println("Disconnected from MySQL database");
    }
}

// A class that implements the DatabaseConnection interface for PostgreSQL
class PostgreSQLConnection implements DatabaseConnection {
    @Override
    public void connect() {
        System.out.println("Connected to PostgreSQL database");
    }

    @Override
    public void disconnect() {
        System.out.println("Disconnected from PostgreSQL database");
    }
}

public class Main {
    public static void main(String[] args) {
        // Create instances of database connections
        DatabaseConnection mysqlConnection = new MySQLConnection();
        DatabaseConnection postgresqlConnection = new PostgreSQLConnection();

        // Connect and disconnect from databases using the interface
        mysqlConnection.connect();
        mysqlConnection.disconnect();

        postgresqlConnection.connect();
        postgresqlConnection.disconnect();
    }
}
```

**Advanced Example: Abstraction in API Design**

```java
// Define an interface for shapes with methods for area and perimeter
interface Shape {
    double calculateArea();
    double calculatePerimeter();
}

// Class representing a Circle that implements the Shape interface
class Circle implements Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }

    @Override
    public double calculatePerimeter() {
        return 2 * Math.PI * radius;
    }
}

// Class representing a Rectangle that implements the Shape interface
class Rectangle implements Shape {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public double calculateArea() {
        return width * height;
    }

    @Override
    public double calculatePerimeter() {
        return 2 * (width + height);
    }
}

public class Main {
    public static void main(String[] args) {
        // Create instances of shapes
        Shape circle = new Circle(5.0);
        Shape rectangle = new Rectangle(4.0, 6.0);

        // Calculate and display area and perimeter using the interface
        System.out.println("Circle Area: " + circle.calculateArea());
        System.out.println("Circle Perimeter: " + circle.calculatePerimeter());

        System.out.println("Rectangle Area: " + rectangle.calculateArea());
        System.out.println("Rectangle Perimeter: " + rectangle.calculatePerimeter());
    }
}
```

### Differences between Classes and Interfaces

**Inheritance**: While classes may only extend one superclass, interfaces support multiple inheritance through the `extends` keyword. This enables interfaces to facilitate multiple inheritance in Java.

**Implementation**: Classes can implement multiple interfaces by using the `implements` keyword. But only one superclass may extend a class.

**Instantiation:** Objects may be instantiated directly from classes using the `new` keyword while interfaces cannot directly instantiated.

**Functionality:** Classes may include both concrete methods with predefined implementations and abstract ones that require subclass implementation, while interfaces only declare methods without providing their implementations.

**Keyword:** When it comes to class definition, we use the `class` keyword. When it comes to interface definition, however, `interface` should be used instead.

**Access Modifiers:** Classes can have various access modifiers like public, protected, private and default while interfaces must always remain public with no further access modifiers available.

**Abstract Classes:** Classes may be declared abstract, meaning they cannot be directly instantiated. Interfaces by definition are implicitly abstract.

Classes provide implementation details and serve as building blocks of objects. Interfaces establish contracts for classes that implement them.

### Multiple Inheritance in Java Using Interface
Java does not directly support multiple inheritance, where a class can inherit from multiple classes. But interfaces offer a way of accomplishing similar functionality through "interface inheritance."

Interface inheritance allows classes to implement multiple interfaces at the same time, inheriting all their methods and constants defined within those interfaces. By adopting multiple interfaces at once, a class may exhibit behaviors or characteristics from each of its inherited interfaces.

```java
interface Drawable {

    void draw();

}

interface Movable {

    void move();

}

class Circle implements Drawable, Movable {

    // Implementing methods declared in the interfaces

    public void draw() {

        // Code to draw a circle

    }

    public void move() {

        // Code to move the circle

    }

}
```

Interface inheritance differs from multiple inheritance in that it does not involve inheriting state or concrete implementation. Rather, its focus lies on inheriting method signatures and constants, providing benefits without some of the associated complexity.

## Abstract Classes and Methods

### Abstract Classes
An abstract class serves as a blueprint for other classes and cannot be instantiated itself. It acts as a partial implementation, providing a common interface and defining certain methods that derived classes must implement.

By marking a class as abstract, you can create a clear separation between the implementation details and the higher-level functionality.

**Example 1: Initializing an Abstract Class (Error)**
Abstract classes cannot be instantiated directly, which means you cannot create an object of an abstract class using the `new` keyword. Attempting to do so will result in a compilation error because abstract classes are meant to be extended by concrete (non-abstract) subclasses that provide implementations for their abstract methods.

```java
// Abstract class representing a Person
abstract class Person {
    private String name;

    public Person(String name) {
        this.name = name;
    }

    public abstract void introduceYourself();
}

public class InitializationErrorExample {
    public static void main(String[] args) {
        // Attempt to initialize an abstract class (Person)
        Person person = new Person("John"); // Error: Cannot instantiate the abstract class Person
    }
}
```

**Example 2: Simple Abstract Class and Regular Class**

```java
// Abstract class representing a Shape
abstract class Shape {
    public abstract double calculateArea();
}

// Concrete class Circle extending Shape
class Circle extends Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

public class SimpleAbstractClassExample {
    public static void main(String[] args) {
        // Create an instance of Circle
        Circle circle = new Circle(5.0);
        
        // Calculate and print the area of the circle
        System.out.println("Area of Circle: " + circle.calculateArea());
    }
}
```

**Example 4: Overriding a Regular Method of an Abstract Class**

```java
// Abstract class representing a Shape
abstract class Shape {
    public void printDescription() {
        System.out.println("This is a shape.");
    }

    public abstract double calculateArea();
}

// Concrete class Circle extending Shape
class Circle extends Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
    
    @Override
    public void printDescription() {
        System.out.println("This is a circle.");
    }
}

public class OverrideRegularMethodExample {
    public static void main(String[] args) {
        // Create an instance of Circle
        Circle circle = new Circle(5.0);
        
        // Print the description and calculate the area of the circle
        circle.printDescription();
        System.out.println("Area of Circle: " + circle.calculateArea());
    }
}
```

**Example 5: Implementing Drawable Interface with Shape Abstract Class in Java**

```java
// Interface for Drawable objects
interface Drawable {
    void draw();
}

// Abstract class representing a Shape
abstract class Shape implements Drawable {
    private String color;

    public Shape(String color) {
        this.color = color;
    }

    // Abstract method to calculate area
    public abstract double calculateArea();

    // Concrete method to print the color
    public void printColor() {
        System.out.println("Color: " + color);
    }

    // Implementing the draw method from the Drawable interface
    @Override
    public void draw() {
        System.out.println("Drawing a shape with color " + color);
    }
}

// Concrete class Circle extending Shape
class Circle extends Shape {
    private double radius;

    public Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }

    // Override to provide the area calculation for a circle
    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

// Concrete class Rectangle extending Shape
class Rectangle extends Shape {
    private double width;
    private double height;

    public Rectangle(String color, double width, double height) {
        super(color);
        this.width = width;
        this.height = height;
    }

    // Override to provide the area calculation for a rectangle
    @Override
    public double calculateArea() {
        return width * height;
    }
}

public class AdvancedAbstractClassExample {
    public static void main(String[] args) {
        // Create instances of Circle and Rectangle
        Circle circle = new Circle("Red", 5.0);
        Rectangle rectangle = new Rectangle("Blue", 4.0, 6.0);

        // Call methods and demonstrate the use of interfaces
        circle.printColor();
        System.out.println("Area of Circle: " + circle.calculateArea());
        circle.draw();

        System.out.println();

        rectangle.printColor();
        System.out.println("Area of Rectangle: " + rectangle.calculateArea());
        rectangle.draw();
    }
}
```

### Abstract Methods
Abstract methods, unlike regular methods, do not have an implementation. They are declared using the `abstract` keyword and must be overridden by any concrete class that extends the abstract class. These methods provide a way for developers to enforce specific behavior in derived classes.

```java
// Abstract class with an abstract method
abstract class Shape {
    // Abstract method declaration
    public abstract double calculateArea();
}

// Concrete subclass Circle extending Shape
class Circle extends Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    // Implementing the abstract method
    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

// Concrete subclass Rectangle extending Shape
class Rectangle extends Shape {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    // Implementing the abstract method
    @Override
    public double calculateArea() {
        return width * height;
    }
}

public class AbstractMethodExample {
    public static void main(String[] args) {
        // Create instances of Circle and Rectangle
        Circle circle = new Circle(5.0);
        Rectangle rectangle = new Rectangle(4.0, 6.0);

        // Calculate and print the areas
        System.out.println("Area of Circle: " + circle.calculateArea());
        System.out.println("Area of Rectangle: " + rectangle.calculateArea());
    }
}
```

Abstract classes and methods in Java offer a powerful mechanism for defining common behavior and ensuring proper implementation in object-oriented programming. They promote code reusability, maintainability, and provide clear separation between higher-level functionality and implementation details.

## Exception Handling

### Fundamentals of Exceptions
In Java, exceptions are unexpected conditions during program execution, arising from issues like invalid input or unavailable resources. Errors are more severe, systemic issues.

Exceptions, manageable and often anticipated, are classified into Checked Exceptions, which must be caught by the compiler, and Unchecked Exceptions, usually due to logical flaws and runtime scenarios.

```java
public class ExceptionExample {

    public static void main(String[] args) {

        // Demonstrating Checked Exception
        // Checked Exceptions are anticipated by the compiler and we are required to handle them
        try {
            // Attempting to read a file that may not exist
            Scanner fileScanner = new Scanner(new File("somefile.txt"));
        } catch (FileNotFoundException e) {
            // FileNotFoundException is a checked exception
            System.out.println("Checked Exception: File not found.");
        }

        // Demonstrating Unchecked Exception
        // Unchecked Exceptions usually result from logical flaws and manifest during runtime
        try {
            // Dividing by zero - a logical flaw
            int result = 10 / 0;
        } catch (ArithmeticException e) {
            // ArithmeticException is an unchecked exception
            System.out.println("Unchecked Exception: Cannot divide by zero.");
        }

        // Note: Errors are different from Exceptions and usually indicate severe problems
        // that a reasonable application should not try to catch.
        // For instance, OutOfMemoryError, StackOverflowError, etc.
    }
}
```

### Basic Exception Handling: try-catch
Java's `try-catch` is used to handle potential exceptions, ensuring the program runs continuously. Multiple `catch` blocks can manage various exceptions. The `finally` block performs cleanup, executing regardless of whether an exception occurs, to properly release or close resources.

```java
public class TryCatchExample {

    public static void main(String[] args) {

        // Resource we want to manage, for the sake of this example let's use a String
        String resource = "exampleResource";

        try {
            // Code that might throw exceptions
            System.out.println("Resource in use: " + resource);

            // This will trigger an ArithmeticException
            int result = 10 / 0;

            // This line will not be executed due to the exception above
            System.out.println(result);

        } catch (ArithmeticException e) {
            // Handle arithmetic exception
            System.out.println("Caught ArithmeticException: " + e.getMessage());

        } catch (Exception e) {
            // General exception handler
            System.out.println("Caught General Exception: " + e.getMessage());

        } finally {
            // Clean-up operations
            resource = null;
            System.out.println("Resource has been released.");
        }
    }
}
```

### Advanced Exception Handling Mechanisms
The `try-with-resources` automatically handles resource closure. Exception chaining allows tracing back to the root cause. It also supports refined exception control through rethrowing and enhanced type-checking.

**Try-with-resources**: Java introduced the `try-with-resources` statement in Java 7 as part of the `java.lang.AutoCloseable` interface. Resources that implement this interface (like streams) can be auto-closed once they're no longer in use.

**Exception Chaining**: This allows exceptions to be linked. When a new exception is thrown because another exception occurs, it's helpful to maintain the original exception as the cause.

```java
public class ExceptionChainingExample {

    public static void main(String[] args) {
        try {
            someMethod();
        } catch (Exception e) {
            System.out.println(e.getMessage());
            System.out.println("Caused by: " + e.getCause().getMessage());
        }
    }

    static void someMethod() throws Exception {
        try {
            // Some code that throws an exception
            throw new RuntimeException("Initial exception");
        } catch (RuntimeException e) {
            throw new Exception("New exception", e);  // Chain the caught exception
        }
    }
}
```

**Rethrowing with Enhanced Type-Checking**: Java 7 introduced the ability to rethrow exceptions with improved type checking, ensuring safer exception handling.

```java
public class RethrowingExample {

    public static void main(String[] args) {
        try {
            testRethrow();
        } catch (IOException | RuntimeException e) {
            System.out.println(e.getMessage());
        }
    }

    static void testRethrow() throws IOException, RuntimeException {
        try {
            // Some code that throws an exception
            throw new IOException("IO exception");
        } catch (Exception e) {
            // Re-throwing the exception with enhanced type-checking
            throw e;
        }
    }
}
```

**Note**: In the last example, even though the catch block captures a general `Exception`, the `testRethrow` method's signature indicates that it can only throw `IOException` and `RuntimeException`. Java's enhanced type-checking ensures that this is the case, and the code will not compile if `throw e` could result in an exception type other than those two.

**Using `throw` and `throws`**: While Java provides an extensive range of exceptions, there will be instances demanding custom exceptions to better represent specific error conditions.

The `throw` keyword facilitates this, letting you craft and launch a custom exception. Conversely, `throws` operates at the method signature level, indicating that a particular method may cause specific exceptions, compelling callers to address them.

### Creating Custom Exceptions
Custom exceptions, though conceptually similar to Java's built-in ones, offer a more detailed portrayal of issues. By simply extending the `Exception` class, you can create bespoke exceptions tailored to your application's needs. Such specificity not only enhances error representation but also aids in more informed error handling and resolution.

```java
// Custom exception class
class InvalidWithdrawalAmountException extends Exception {
    public InvalidWithdrawalAmountException(String message) {
        super(message);  // Passing the error message to the base Exception class
    }
}

public class BankAccount {

    private double balance;

    public BankAccount(double balance) {
        this.balance = balance;
    }

    // Method to withdraw money from the account
    public void withdraw(double amount) throws InvalidWithdrawalAmountException {
        if (amount < 0) {
            throw new InvalidWithdrawalAmountException("Withdrawal amount cannot be negative.");
        } else if (amount > balance) {
            throw new InvalidWithdrawalAmountException("Withdrawal amount exceeds account balance.");
        } else {
            balance -= amount;
            System.out.println("Withdrawal successful. New balance: " + balance);
        }
    }

    public static void main(String[] args) {
        BankAccount account = new BankAccount(500);

        try {
            account.withdraw(600);  // This should trigger our custom exception
        } catch (InvalidWithdrawalAmountException e) {
            System.out.println("Error: " + e.getMessage());  // Handle the custom exception by printing out the error message
        } catch (Exception e) {  // This catch block will handle general exceptions
            System.out.println("A general error occurred: " + e.getMessage());
        }
    }
}
```

### Best Practices in Exception Handling
Don't use empty `catch` blocks, which merely swallow exceptions, leaving them unaddressed. Instead, focus on catching the most specific exceptions before any generic ones. Steer clear of deploying exceptions as regular control flow tools. And remember, always document exceptions using JavaDoc, guiding other developers in anticipating and managing potential pitfalls.

```java
/**
 * Custom exception for insufficient funds.
 */
class InsufficientFundsException extends Exception {
    public InsufficientFundsException(String message) {
        super(message);
    }
}

/**
 * Custom exception for invalid deposit amounts.
 */
class InvalidDepositAmountException extends Exception {
    public InvalidDepositAmountException(String message) {
        super(message);
    }
}

/**
 * Custom exception for invalid withdrawal amounts.
 */
class InvalidWithdrawalAmountException extends Exception {
    public InvalidWithdrawalAmountException(String message) {
        super(message);
    }
}

/**
 * Custom exception for a frozen account.
 */
class AccountFrozenException extends Exception {
    public AccountFrozenException(String message) {
        super(message);
    }
}

public class BankAccount {

    private double balance;
    private boolean isFrozen;

    public BankAccount(double initialBalance) {
        this.balance = initialBalance;
        this.isFrozen = false;
    }

    public void freezeAccount() {
        this.isFrozen = true;
    }

    /**
     * Deposit money into the bank account.
     *
     * @param amount Amount to deposit.
     * @throws InvalidDepositAmountException if the deposit amount is non-positive.
     * @throws AccountFrozenException if the account is frozen.
     */
    public void deposit(double amount) throws InvalidDepositAmountException, AccountFrozenException {
        if (isFrozen) {
            throw new AccountFrozenException("Account is frozen, cannot perform operations.");
        }
        if (amount <= 0) {
            throw new InvalidDepositAmountException("Deposit amount must be positive.");
        }
        balance += amount;
    }

    /**
     * Withdraw money from the bank account.
     *
     * @param amount Amount to withdraw.
     * @throws InsufficientFundsException if there isn't enough balance.
     * @throws InvalidWithdrawalAmountException if the withdrawal amount is non-positive.
     * @throws AccountFrozenException if the account is frozen.
     */
    public void withdraw(double amount) throws InsufficientFundsException, InvalidWithdrawalAmountException, AccountFrozenException {
        if (isFrozen) {
            throw new AccountFrozenException("Account is frozen, cannot perform operations.");
        }
        if (amount <= 0) {
            throw new InvalidWithdrawalAmountException("Withdrawal amount must be positive.");
        }
        if (balance < amount) {
            throw new InsufficientFundsException("Insufficient funds in the account.");
        }
        balance -= amount;
    }

    public double getBalance() {
        return balance;
    }

    public static void main(String[] args) {
        BankAccount account = new BankAccount(500.0);

        try {
            account.deposit(-50);
        } catch (Exception e) {
            System.out.println("Error: " + e.getMessage());
        }

        try {
            account.withdraw(600);
        } catch (Exception e) {
            System.out.println("Error: " + e.getMessage());
        }

        try {
            account.freezeAccount();
            account.deposit(50);
        } catch (Exception e) {
            System.out.println("Error: " + e.getMessage());
        }

        System.out.println("Current balance: " + account.getBalance());
    }
}
```

### Common Mistakes and How to Avoid Them
Catching the generic `Exception` or `Throwable` without justification can mask issues. Letting exceptions go unheeded or ‘swallowing’ them can leave underlying problems unresolved.

Moreover, introducing exceptions within `finally` blocks can overshadow primary exceptions, leading to obscured debugging.

**Catching the generic Exception or Throwable without justification:**

```java
try {
    // some code that might throw exceptions
} catch (Exception e) {
    // This catch block is too generic, and can mask specific issues
    e.printStackTrace();
}
```

**Letting exceptions go unheeded or ‘swallowing’ them:**

```java
try {
    // some code that might throw exceptions
} catch (SpecificException e) {
    // This catch block is empty, 'swallowing' the exception
    // No action is taken to address the underlying problem
}
```

**Introducing exceptions within finally blocks:**

```java
try {
    // some code that might throw exceptions
} catch (SpecificException e) {
    // Handle specific exception
    e.printStackTrace();
} finally {
    try {
        // some cleanup code that might throw exceptions
    } catch (AnotherException e) {
        // Introducing exceptions in the finally block
        // This can overshadow primary exceptions, making debugging difficult
        e.printStackTrace();
    }
}
```

### Practical Scenarios and Use-cases

- Validating input in user-centric forms, ensuring data integrity.
- Engaging in file operations, be it reading or writing, guaranteeing data security and accuracy.
- Managing database connections, especially when handling SQL exceptions, preserving database integrity.

