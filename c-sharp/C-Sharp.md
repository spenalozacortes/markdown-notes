#c-sharp
# Hello World

## Hello World

### What is C#?
This programming language can be used to make interactive websites, mobile apps, video games, augmented reality (AR), virtual reality (VR), desktop applications, and back-end services – just to name a few.

Unlike languages like Ruby and JavaScript, C# has you define the _type_ of each data in a program. Assigning a type essentially tells a computer what operations can and cannot be performed on a piece of data. This style of coding helps programmers avoid a large class of errors that are common to Ruby and JavaScript .

### Run Some C-Sharp
`Console.WriteLine()` is a command that prints text to a console. Whatever is in between the parentheses will be printed to the console!

```c#
Console.WriteLine("Hello World!");
```

### Getting Input
We can also read input from a user. The command `Console.ReadLine()` captures text that a user types into the console.

```c#
Console.WriteLine("How old are you?");
string input = Console.ReadLine();
Console.WriteLine($"You are {input} years old!");
```

---

For interactive code like this, run it by typing the command

```shell
dotnet run
```

### Comments
Text written in a program but not run by the computer is called a _comment_. In C#, anything after a `//` or between `/*` and `*/` is a comment. In spoken word we call these symbols “forward slashes” and “asterisks”.

Comments can:

- Provide context for why something is written the way it is:

```c#
/* This variable will be used to count the number of times anyone tweets the word persnickety */
int persnicketyCount = 0;
```

- Help other people reading the code understand it faster:

```c#
/* Calculates tomorrow's rain likelihood as a number between 0 and 100 */
ComplicatedRainCalculationForTomorrow();
```

- Ignore a line of code and see how a program will run without it:

```c#
// string usefulValue = OldSloppyCode();
string usefulValue = NewCleanCode();
```

Developers tend to use `//` for short, one-line comments and `/* */` for anything longer, but the choice is up to you!

### C# in the Wild
Here’s what you need to know:

1. C# technologies are fast: A software company called [Raygun](https://raygun.com/blog/dotnet-vs-nodejs/) built their application using Node.js, a framework for JavaScript. When their app started to slow down, they switched to .NET, a framework for C#. Their performance skyrocketed.
2. The C# community is big: In 2019, [Github ranked C# as the fifth most popular programming language](https://octoverse.github.com/#top-languages) and [StackOverflow ranked it seventh](https://insights.stackoverflow.com/survey/2019#most-popular-technologies).
3. C# is employable: Thanks to good design and the popularity of frameworks supporting the language, C# can get you access to a lot of great jobs.


# Data Types and Variables

## Data Types and Variables

### Introduction to Data Types and Variables in C\#
Languages like C# tell a computer about the type of data in its program using _data types_. Data types represent the different types of information that we can use in our programs and how they should be used.

Without [data types](https://www.codecademy.com/resources/docs/c-sharp/data-types), computers would try and perform processes that are impossible, like squaring a piece of text or capitalizing a number. That’s how we get bugs!

C# is _strongly-typed_, so it requires us to specify the data types that we’re using. It is also _statically-typed_, which means it will check that we used the correct types before the program even runs. Both language features are important because they help write scalable code with fewer bugs.

### C# Data Types
_Data types_ tell us a few things about a piece of data, like:

- How it can be stored
- What operations we can perform with it
- Different [methods](https://www.codecademy.com/resources/docs/c-sharp/methods) it can be used with

C# has several built-in [data types](https://www.codecademy.com/resources/docs/c-sharp/data-types).

- `int` - whole numbers, like: 1, -56, 948
- `double` - decimal numbers, like: 239.43909, -660.01
- `char` - single characters, like: “a”, “&”, “£”
- `string` - string of characters, like: “dog”, “hello world”
- `bool` - boolean values, like: true or false

### Creating Variables with Types
In C#, [data types](https://www.codecademy.com/resources/docs/c-sharp/data-types) and [variables](https://www.codecademy.com/resources/docs/c-sharp/variables) are closely intertwined. Remember how C# is strongly-typed? Every time we declare a variable, we have to specify what kind of data type that variable is going to hold.

There are two ways we can assign variables. We can do it on two lines:

```c#
// Declare an integer
int myAge;
myAge = 32;
```

Or, we can be more concise and just do it on one:

```c#
// Declare a string
string countryName = "Netherlands";
```

### Converting Data Types
Because [variables](https://www.codecademy.com/resources/docs/c-sharp/variables) have to be strictly typed, there may be some circumstances where we want to change the type of data a variable is storing. This strategy is known as _data type conversion_.

C# checks to make sure that when we convert [data types](https://www.codecademy.com/resources/docs/c-sharp/data-types) from one to another that we’re not losing any data, because that could cause problems in our code.

Because of that, there are a couple different ways to do data type conversion:

- _implicit_ conversion: happens automatically if no data will be lost in the conversion. That’s why it’s possible to convert an int (which can hold less data) to a double (which can hold more), but not the other way around.
- _explicit_ conversion: requires a cast operator to convert a data type into another one. So if we do want to convert a double to an int, we could use the operator `(int)`.

```c#
double myDouble = 3.2;

// Round myDouble to the nearest whole number
int myInt = (int)myDouble;
```

It’s also possible to convert data types using built-in [methods](https://www.codecademy.com/resources/docs/c-sharp/methods). For most data types, there is a `Convert.ToX()` method, like `Convert.ToString()` and `Convert.ToDouble()`. For a full list of `Convert` class built-in methods, check out the [Microsoft Documentation](https://docs.microsoft.com/en-us/dotnet/api/system.convert?view=netframework-4.7.2).

---

One example of when we have to use conversions is when we ask a user to input a numerical value. Even if that value is an integer or a decimal, `Console.ReadLine()` will always return a string.

If you tried `dotnet run` again, you’ll see that `(int)` didn’t work either. That’s because it is not possible to explicitly convert a string into an int (or vice versa) in C#. This time, let’s try using a built-in method to do the conversion.

Look at [this article on converting strings to int](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/types/how-to-convert-a-string-to-a-number). It lists a few of the methods in the Convert class, including: `Convert.ToInt32()`. This method takes a string and outputs an integer.

```c#
int faveNumber = Convert.ToInt32(Console.ReadLine());
```

## Working with Numbers

### Numerical Data Types

#### Int
An _int_ is a whole integer value, like 4, 100, or 2349. They’re a good way to count units of things.

```c#
int variableName = 7;
```

#### Double and Decimal
If we need to use a decimal value, we have a few options: float, double, and decimal.

A _double_ is usually the best choice of the three because it is more precise than a `float`, but faster to process than a _decimal_. However, make sure to use a decimal for financial applications, since it is the most precise.

```c#
double variableName = 39.76876;
decimal variableName = 489872.76m;
```

### Arithmetic Operators
Arithmetic [operators](https://www.codecademy.com/resources/docs/c-sharp/operators) include:

- addition `+`
- subtraction `-`
- multiplication `*`
- division `/`

```c#
int answer = 4 + 19;
Console.Write(answer);

// prints 23
```

When using operators, it’s important to pay attention to [data types](https://www.codecademy.com/resources/docs/c-sharp/data-types). If we use two integers, it will return an integer _every time_. However, if we combine an integer with a double, the answer will be a double.

```c#
Console.WriteLine(5 / 3);
Console.WriteLine(5 / 3.0);

// prints 1
// prints 1.66667
```

C# follows [the order of operations](https://en.wikipedia.org/wiki/Order_of_operations).

```c#
int answer = 8 + (9 * 3);
Console.Write(answer);

// prints 35
```

### Operator Shortcuts
Often we need to update a variable in our program. We can do so by modifying that variable using an arithmetic expression, then re-saving it to the same variable name:

```c#
int apple = 0;
apple = apple + 1;
Console.Write(apple); // prints 1
```

We can condense the same program above using the shorthand `++`. The combined addition signs represent the idea of _incrementing by one_. We can do the same with the subtraction symbol `--`.

```c#
// a shorter way to do the same thing 
int apple = 0;
apple++;
Console.Write(apple); // prints 1
```

If we want the amount to increment by another value, say 3, we would do the following:

```c#
int apple = 0;
apple += 3; // is the same as apple = apple + 3
Console.Write(apple); // prints 3
```

Again, if we want to decrement, you would do `-=3`.

### Modulo
A modulo returns a _remainder_, what is left over when we divide a number by another number.

```
4 % 3 = 1
4 % 2 = 0
```

Modulos are useful because they let us know if a number “fits” into a larger number, or if there will be a remainder.

```c#
int eggs = 56;
int crateAmount = 12;

int eggsLeftOver = eggs % crateAmount; 
Console.Write(eggsLeftOver); // prints 8
```

It can also be used to check if a number is odd or even. If a number is even, taking its modulo with 2 it will return a 0 and if it is odd it will return a 1:

```c#
int myNum = 85939824;
Console.Write(myNum % 2); // prints 0, so number is even
```

### Built-In Methods
There are several built-in [methods](https://www.codecademy.com/resources/docs/c-sharp/methods) that we can use to manipulate numerical data and perform more complex mathematical calculations. Here are a few:

- `Math.Abs()`—will find the absolute value of a number. Example: `Math.Abs(-5)` returns 5.
- `Math.Sqrt()`—will find the square root of a number. Example: `Math.Sqrt(16)` returns 4.
- `Math.Floor()`—will round the given double or decimal down to the nearest whole number. Example: `Math.Floor(8.65)` returns 8.
- `Math.Min()`—returns the smaller of two numbers. Example: `Math.Min(39, 12)` returns 12.

---

The built-in method `Math.Sqrt()` can only take a positive number as a value.

- `Math.Pow()`
- `Math.Max()`
- `Math.Ceiling()`

## Working with Text

### Building Strings
A _string_ is a group of characters surrounded by quotation marks, like `"https://codecademy.com"` or `"To be or not to be."` A string is just a collection of a smaller data type, _char_, which is a single character like “a” or “?”.

To define a variable as a string, you write the data type, then the variable name. Then set it equal to the value, which is inside of quotation marks :

```c#
string variableName = "puppy";
```

#### Escape Character Sequences
What happens when you need to include quotes in a string? You can use an escape sequence. An escape sequence places a backslash (`\`) before the inner quotation marks, so the program doesn’t read them accidentally as the end of sequence.

```c#
string withSlash = "Ifemelu said, \"Hello!\"";
```

We can use escape character sequences to create a newline. That means that when we print the string to the console, it will print that line below the rest. If printed on its own, it will create an empty line. To create a newline, use the character combination `\n`.

```c#
string newLine = "Ifemelu walked \n to the park.";
```

### String Concatenation
Often, we want to combine [strings](https://www.codecademy.com/resources/docs/c-sharp/strings) together, or combine strings with a value that we’ve saved to a variable.

A common way to do is by using _string concatenation_. String concatenation is when we combine strings using the addition symbol (`+`), literally adding one string to another.

```c#
string yourFaveMusician = "David Bowie";
string myFaveMusician = "Solange";

Console.WriteLine("Your favorite musician is " + yourFaveMusician + " and mine is " + myFaveMusician + ".");
```

- If we want to concatenate a string with something that is another data type, C# will implicitly convert that value to a string.
- Make sure that you include spaces and proper punctuation so that when it prints out, your variable strings aren’t squished between the rest of the statement.

### String Interpolation
String interpolation was introduced in C# 6 and it enables us to insert our variable values and expressions in the middle of a string, without having to worry about spaces and punctuation.

```c#
string yourFaveMusician = "David Bowie";
string myFaveMusician = "Solange";

Console.WriteLine($"Your favorite musician is {yourFaveMusician} and mine is {myFaveMusician}.");
```

### Get Info About Strings
In addition to containing the value of a piece of text, strings also contain information about themselves. It can be useful to know these properties when working with strings. There are several built-in .NET [methods](https://www.codecademy.com/resources/docs/c-sharp/methods) that we can use to get more information about strings.

#### Length
Since strings are composed of a set of characters, we can find out how many characters exist in a string with the [`.Length`](https://www.codecademy.com/resources/docs/c-sharp/arrays/length) method.

```c#
string userTweet = Console.ReadLine();

userTweet.Length; // returns the length of the tweet
```

#### IndexOf
We can also find the position of a specific character or substring using [`.IndexOf()`](https://www.codecademy.com/resources/docs/c-sharp/strings/indexof). This method is useful for searching to see if something exists in a string.

If it does exist within a string, the method will return the _position_ of the search term in the larger string. Each character in a string has a unique position, like an address. Positions starts at 0 and increment by 1.

```c#
string word = "radio";

word.IndexOf("a"); // returns 1
```

If it doesn’t exist in the string the method will return a -1. If we pass it an empty string, it will return 0. If it occurs more than once, it will return the first instance.

### Get Parts of Strings
We can also use built-in .NET [methods](https://www.codecademy.com/resources/docs/c-sharp/methods) to grab parts of strings or specific characters in a string.

#### Substring
`.Substring()` grabs part of a string using the specified character position, continues until the end of the string, and returns a new string.

```c#
string plantName = "Cactaceae, Cactus"; 
int charPosition = plantName.IndexOf("Cactus"); // returns 11
string commonName = plantName.Substring(charPosition); // returns Cactus
```

`.Substring()` is useful if we only want to use part of a string but keep the original data intact.

We can also pass `.Substring()` a second argument, which will determine the number of characters in the resulting substring.

```c#
string name = "Codecademy"; 
int start = 2;
int length = 6;
string substringName = name.Substring(start, length); // returns 'decade'
```

#### Bracket Notation
Bracket notation is a style of syntax that uses brackets `[]` and an integer value to identify a particular value in a collection. In this case, we can use it to find a specific character in a string.

```c#
string plantName = "Cactaceae, Cactus";
int charPosition = plantName.IndexOf("u"); // returns 15
char u = plantName[charPosition]; // returns u
```

### Manipulate Strings
There are also built-in .NET [methods](https://www.codecademy.com/resources/docs/c-sharp/methods) that we can use to manipulate text data. Using these methods on a string doesn’t change the string itself, but creates an entirely new one.

#### ToUpper, ToLower
We can quickly change the case of our strings using the methods [`.ToUpper()`](https://www.codecademy.com/resources/docs/c-sharp/strings/toupper) and [`.ToLower()`](https://www.codecademy.com/resources/docs/c-sharp/strings/tolower).

```c#
string shouting = "I'm not shouting, you're shouting".ToUpper();
Console.WriteLine(shouting);
// prints I'M NOT SHOUTING, YOU'RE SHOUTING.
```

### Review
You just learned about how to work with textual data in a few different ways:

- How to save char and string values to a variable.
- Use the addition symbol (`+`) to concatenate strings.
- Interpolate strings for easier string construction.
- Find information about a string using [`.Length`](https://www.codecademy.com/resources/docs/c-sharp/arrays/length) and [`.IndexOf()`](https://www.codecademy.com/resources/docs/c-sharp/strings/indexof).
- Grab characters and parts of strings using bracket notation and `.Substring()`.
- Use built-in [methods](https://www.codecademy.com/resources/docs/c-sharp/methods) such as [`.ToUpper()`](https://www.codecademy.com/resources/docs/c-sharp/strings/toupper) and [`.ToLower()`](https://www.codecademy.com/resources/docs/c-sharp/strings/tolower) to manipulate strings.

# Logic and Conditionals

## Understanding Logic in C sharp

### Introduction to Logic in C#
Distinguishing between binaries is the foundation of _Boolean logic_. Boolean logic is based on the idea that all values are either _true_ or _false_.

### Boolean Data Types
In C#, we can represent Boolean values using the `bool` data type. Booleans, unlike numbers or [strings](https://www.codecademy.com/resources/docs/c-sharp/strings), only have two values: true and false.

```c#
bool variableName = true;
```

### Comparison Operators
When writing a program, we often need to check if a value is correct or compare two values. Comparison operators allow us to compare values and evaluate their relationship. Rather than evaluating to an integer, they evaluate to boolean values. Expressions that evaluate to boolean values are known as boolean expressions.

Comparison operators include:

- _Equals_ `==`: returns true if the value to the left is equal to the value to the right.
- _Inequality operator_ `!=`: returns true if the two values are not equal.
- _Less than_ `<`: returns true if the value to the left is less than the value to the right.
- _Greater than_ `>`: returns true if the value to the left is more than the value to the right.
- _Less than or equal to_ `<=`: returns true if the value to the left is less than or equal to the value on the right.
- _Greater than or equal to_ `>=`: returns true if the value to the left is more than or equal to the value to the right.

```c#
bool answer = 3 < 75; 
Console.WriteLine(answer); // prints True
```

In addition to comparing integers, we can also compare variables, strings, and even boolean values:

```c#
bool answer = (true == false);
Console.WriteLine(answer); //prints False
```

### Truth Table
We can also use [operators](https://www.codecademy.com/resources/docs/c-sharp/operators) that use Boolean values as inputs and output. Logical operators, also known as Boolean operators, can be used to create Boolean expressions.

Logical operators include:

- AND `&&`: Both expressions are evaluated and will return True _only_ if both expressions evaluate to True. Otherwise, it will return False.
- OR `||`: Both expressions are evaluated and will return True if _at least one_ of the expressions evaluates to True. Otherwise, it will return False.
- NOT `!`: An expression, no matter its logical value, evaluates to its opposite. What is True becomes False and what is False becomes True.

```c#
bool andExample = ((4 > 1) && (2 < 7)); 
// (True AND True) evaluates to True

bool orExample = ((8 > 6) || (3 > 6));
// (True OR False) evaluates to True

bool notExample = !(1 < 3);
// NOT (True) evaluates to False
```

A common way to visualize these relationships is using a diagram known as a _truth table_. Truth tables allow us to quickly see what the outcome is for different relationships between Boolean values.

## Conditional Statements

### Introduction to Conditional Statements
The order that computer programs execute a set of instructions is known as _control flow_. We can use different _control structures_ to alter the flow of our program.

Boolean logic and conditional statements go hand in hand. A computer will determine if a condition is true or false and execute a set of instructions accordingly.

### If Statements
The most basic conditional statement is an _if statement_. An _if statement_ executes a block of code if specified condition is true.

```c#
string color = "blue";

if (color == "blue")
{
  // this code block will execute only if the value of color is 
  // equivalent to "blue"
  Console.WriteLine("color is blue");
}
```

- Indentation: while whitespace won’t impact our program, it is convention to indent the code inside the braces by two spaces.

### If...Else... Statements
What if we want another set of instructions to execute if the condition is false? An `else` clause can be added to an `if` statement to provide code that will only be executed if the `if` condition is false.

```c#
string color = "red";

if (color == "blue")
{
  // this code block will execute only if the value of color is 
  // equivalent to "blue"
  Console.WriteLine("color is blue");
} 
else 
{
  // this code block will execute if the value of color is 
  // NOT equivalent to "blue"
  Console.WriteLine("color is NOT blue");
}
```

### Else If Statements
What if we want to handle multiple conditions and have a different thing happen each time? Conditional statements can be chained by combining `if` and `else` statements into `else if`. After an initial if statement, one or more `else if` blocks can check additional conditions. An optional `else` block can be added at the end to catch cases that do not match any of the conditions.

```c#
string color = "red";

if (color == "blue")
{
  // this code block will execute only if the value of color is 
  // equivalent to "blue"
  Console.WriteLine("color is blue");
} 
else if (color == "red")
{
  // this code block will execute if the value of color is 
  // equivalent to "red"
  Console.WriteLine("color is NOT blue");
} 
else // this is optional
{
  // this code block will execute if the value of color is 
  // NOT equivalent to "blue" OR "red"
  Console.WriteLine("color is NOT blue OR red");
}
```

### Switch Statements
If it’s necessary to evaluate several conditions with their own unique output, a _switch statement_ is the way to go. [Switch](https://www.codecademy.com/resources/docs/c-sharp/switch) statements allow for compact control flow structures by evaluating a single expression and executing code blocks based on a matched case.

```c#
string color;

switch (color)
{
   case "blue":
      // execute if the value of color is "blue"
      Console.WriteLine("color is blue");
      break;
   case "red":
      // execute if the value of color is "red"
      Console.WriteLine("color is red");
      break;
   case "green":
      // execute if the value of color is "green"
      Console.WriteLine("color is green");
      break;
   default:
      // execute if none of the above conditions are met
      break;
}
```

### Ternary Operators
The _ternary operator_ allows for a compact syntax in the case of binary decisions. Like an `if...else` statement, it evaluates a single condition and executes one expression if the condition is true and the second expression otherwise.

```c#
string color = "blue";
string result = (color == "blue") ? "blue" : "NOT blue";

Console.WriteLine(result);
```

Ternary [operators](https://www.codecademy.com/resources/docs/c-sharp/operators) can also be chained, like else if statements.

# Methods

## Method Calls and Input

### Call a Method
We activate a method’s behavior by _calling_ it. In C# we do this by adding parentheses to the end of a method name.

```c#
Console.WriteLine();
```

Some methods accept inputs called _arguments_. `Console.WriteLine()` accepts one string argument. That argument will be printed to the console.

```c#
// This prints "I'm hungry!"
Console.WriteLine("I'm hungry!"); 
```

Other methods accept multiple arguments, like `Math.Min()`. It expects two number inputs.

```c#
Math.Min(3, 5);
```

You’ve probably seen built-in methods for each data type too. Every string has access to methods like `IndexOf()` and `Substring()`.

```c#
string name = "beatrice";
name.Substring(0, 3); // returns "bea"
```

### Capture Output
Like a math function or a factory machine, a method takes input and _returns_ output.

When a method _returns_ a value, it essentially passes a piece of data to wherever it was called. One way to capture the returned value of a method is with a variable:

```c#
int smallerNumber = Math.Min(3, 4);
```

Not every method returns a value. `Console.WriteLine()`, for example, prints `3` to the console but it doesn’t pass the value `3` to its caller.

### Define a Method
The basic structure of a method definition looks like this:

```c#
static void YourMethodName()
{
}
```

In C#, it’s convention to use PascalCase to name your method. The name starts with an uppercase letter and each word following begins with an uppercase as well. It’s not required in C#, but it makes your code easier to read for other developers.

Just like any other method, we call it with parentheses:

```c#
YourMethodName();
```

Since `Main()` is already a method, we’ll define our own methods outside of `Main()`.

### Define Parameters
While we are defining our method, we don’t know the actual argument values that will be used when calling the method. But we do know the expected data type and how it will be used. We can use this information to define a _parameter_, which sort of works like a variable within a method. Imagine it as a placeholder for the actual argument value.

```c#
static void YourMethodName(string identity)
{
  Console.WriteLine(identity);
}
```

Separate multiple parameters with commas:

```c#
static void YourMethodName(string identity, int age)
{
  Console.WriteLine($"{identity} is {age} years old.");
}
```

When you call your method, the values to be used for each parameter are called _arguments_.

```c#
YourMethodName("Yoda", 900);
```

### A Note on Parameters
One thing to watch for with parameters: they can only be used inside their method!

```c#
static void YourMethodName(string message)
{
  Console.WriteLine(message);
}
Console.WriteLine(message); // causes an error!
```

### Optional Parameters
To make our functions even more flexible, we can make certain parameters _optional_. If someone calls your method without all the parameters, the method will assign a default value to those missing parameters.

All you have to do is use the equals sign (`=`) when defining the method.

```c#
static void Main(string[] args)
{
  YourMethodName("I'm hungry", "!"); // prints "I'm hungry!"
  YourMethodName("I'm hungry");  // prints "I'm hungry."
}

static void YourMethodName(string message, string punctuation = ".")
{
  Console.WriteLine(message + punctuation);
}
```

### Named Arguments
Say your method has lots of optional parameters, but you only want to specify one when you call it.

```c#
static void YourMethodName(int a = 0, int b = 0, int c = 0, int d = 0, int e = 0) {...}
```

When you call the method, you only want to specify `d`. But calling the method this way would set `a` to `4`, not `d`!

```c#
YourMethodName(4);
```

Refer to the parameter by its name instead:

```c#
YourMethodName(d: 4);
```

With named arguments, you can list them in any order:

```c#
YourMethodName(d: 4, b: 1, a: 2);
```

You can also mix named arguments with positional arguments, but positional arguments MUST come before named arguments:

```c#
YourMethodName(2, 1, d: 4) // a is 2, b is 1, d is 4
YourMethodName(d: 4, 2, 1) // Error!
```

### Method Overloading
Say you want to use `Math.Round()`, a built-in method. You go to the [Microsoft documentation](https://docs.microsoft.com/en-us/dotnet/api/system.math.round) to learn how to use it, and find at least 8 different versions! They all have the same name: `Math.Round()`.

What’s happening here is called _method overloading_, and each “version” is called an _overload_. Though they have the same name, the _overloads_ are different because they have either (i) different parameter types or (ii) different number of parameters. This is useful if you want the same method to have different behavior based on its inputs.

Let’s examine this concept with these two overloads: `Math.Round(Double, Int32)` and `Math.Round(Double)`.

The first overload, `Math.Round(Double, Int32)`, rounds the `double` to the `int`‘s number of decimal points.

```c#
Math.Round(3.14159, 2); // returns 3.14
```

The second, `Math.Round(Double)`, rounds the `double` to the nearest integer.

```c#
Math.Round(3.14159); // returns 3
```

In C#, when we say that the [methods](https://www.codecademy.com/resources/docs/c-sharp/methods) are “different”, we are really talking about their method _signatures_, which is the method’s name and parameter types in order.

### Review

- Call a method with its name and parentheses:

```c#
VisitPlanets();
```

- Store a method’s returned value in a variable:

```c#
double result = Math.Round(3.14159, 2);
```

- Define a basic method with the following syntax:

```c#
static void VisitPlanets()
{
}
```

- Every time an application is started, the `Main()` method is called.
- Values passed to a method are called _arguments_. When defined in the method, they are _parameters_.
- Method parameters can only be used within the method body.
- Method parameters can be _optional_ if given a default value using equals `=` syntax:

```c#
static void VisitPlanets(int numberOfPlanets = 0)
```

- When calling a method, pass arguments by position or by name. If using names, use the colon (`:`) syntax:

```c#
VisitPlanets(numberOfPlanets: 9);
```

- In _method overloading_, multiple [methods](https://www.codecademy.com/resources/docs/c-sharp/methods) can have the same name, as long as they have different method _signatures_.
- A method _signature_ is a method’s name and parameter types in order.

## Method Output

### Return
The basic way to _return_ values from a method is to use a `return` statement!

```c#
static string Yell(string phrase) 
{
  return phrase.ToUpper();
}

public static void Main()
{
  string output = Yell("who's there?");
  Console.WriteLine(output); // Prints WHO'S THERE?
}
```

Here’s a more generic definition: the keyword `return` tells the computer to exit the method and return a value to wherever the method was called.

When a method is declared, it must announce the type of value it will return. In this case, `Yell()` returns a string, so it has the `string` modifier (right before the name `Yell`).

That first line of the method is called a _method declaration_, so we can say that the method declaration must contain the type of the return value.

Generally, the method declaration is a combination of details including: the access modifiers, return type, method name, and parameter types.

### Return Errors
The method definition must contain the type of the return value: if a method returns an integer, its return type must be `int`; if it returns text, it must be `string`, and so on. If the method returns nothing, use `void`.

If a method returns a type different from its stated return type, it will throw an error.

This error means you must state a return type before the method name:

```
error CS1520: Method must have a return type
```

This error means that your method doesn’t return a value, when it should:

```
error CS0161: [MethodName]: not all code paths return a value
```

In some cases, this error means that your method returns a `string` when it should be an `int`.

```
error CS0029: Cannot implicitly convert type 'string' to 'int'
```

### Out
A method can only _return_ one value, but sometimes you need to output two pieces of information. Calling a method that uses an `out` parameter is one way to return multiple values.

For example, the `Int32.TryParse()` method tries to parse its input as an integer. If it can properly parse the input, the method returns `true` and sets its `out` variable to the new value. If it cannot properly parse the input, the method returns `false` and sets the `out` variable to 0.

```c#
public static bool TryParse (string s, out int result);
```

The method returns a `boolean` and accepts a `string` and a variable that has been declared of type `int` as input.

```c#
int number;
bool success = Int32.TryParse("10602", out number); 
// number is 10602 and success is true
int number2;
bool success2 = Int32.TryParse(" !!! ", out number2);
// number2 is 0 and success2 is false
```

For a shortcut, you can declare the `int` variable within the method call:

```c#
bool success = Int32.TryParse("10602", out int number);
```

### Using Out
We can use `out` parameters in our own [methods](https://www.codecademy.com/resources/docs/c-sharp/methods) as well.

```c#
static string Yell(string phrase, out bool wasYellCalled)
{
  wasYellCalled = true;
  return phrase.ToUpper();
}
```

- The `out` parameter must be set to a value before the method ends

When calling the method, don’t forget to use the `out` keyword as well:

```c#
string message = "garrrr";
Yell(message, out bool flag);
// returns "GARRRR" and flag is true
```

### Out Errors
As with `return`, `out` is a very useful keyword, but it can lead to errors if used incorrectly. Here are two common ones:

This error means that the `out` parameter needs to be assigned a value within the method:

```
error CS0177: The out parameter 'success' must be assigned to before control leaves the current method
```

This error means you called a method that expects an ‘out’ parameter but you didn’t use the `out` keyword when calling it:

```
error CS1620: Argument 2 must be passed with the 'out' keyword
```

### Review

- Methods return values with the `return` keyword.
- Every method has a return type, designated in its method signature. That type must match the type of the value actually returned.
- If a method returns no type, its return type is `void`.
- `out` parameters can be used to return multiple values from a method.

## Alternate Expressions

### Introduction to Alternate Expressions
In C# there are other ways to define a method, which can save us effort in typing and make our code easier to read. They’re called _expression-bodied definitions_ and _lambda expressions_.

### Expression-bodied Definitions
_Expression-bodied definitions_ are the first “shortcut” for writing [methods](https://www.codecademy.com/resources/docs/c-sharp/methods). They’re great for writing one-line methods, like this one:

```c#
bool IsEven(int num)
{
  return num % 2 == 0;
}
```

We can rewrite this definition as an expression-bodied definition by:

- removing the curly braces and `return` keyword, and
- adding the “fat arrow”, or `=>`, which is composed of the equal sign, `=`, and greater than, `>`, symbols

```c#
bool isEven(int num) => num % 2 == 0;
```

This also works for methods that return nothing, aka `void`:

```c#
void Shout(string x) => Console.WriteLine(x.ToUpper());
```

This type of definition can only be used when a method contains one expression. This helps us remember the name: _expression_-bodied definitions are method definitions with one _expression_.

Fun fact: some developers also call the fat arrow notation, `=>`, a squid! 🦑

### Methods as Arguments
Before we get into the next shortcut, we need to understand how [methods](https://www.codecademy.com/resources/docs/c-sharp/methods) are passed to other methods as arguments. This is possible and sometimes necessary in C#.

For example, say we need to check if there are even values in an array (you don’t need to know much about [arrays](https://www.codecademy.com/resources/docs/c-sharp/arrays) here, except that they are lists of values).

First you need an array of values and the `IsEven()` method that returns `true` if its argument is even:

```c#
int[] numbers = {1, 3, 5, 6, 7, 8};

public static bool IsEven(int num)
{
  return num % 2 == 0;
}
```

Pass both of these as arguments to the method `Array.Exists()`, which returns a boolean value:

```c#
bool hasEvenNumber = Array.Exists(numbers, IsEven);
```

In the background, this is what `Array.Exists()` does:

- The `IsEven()` method is called with each value in the array. We can imagine each of these being called:

```c#
IsEven(1);
IsEven(3);
IsEven(5);
IsEven(6);
```

- If any of these return `true`, `Array.Exists()` returns `true`.

By the end, `Array.Exists()` returns `true` because `isEven(6)` returns `true`.
#aqui 

---

[`Array.Find()` is another method](https://docs.microsoft.com/en-us/dotnet/api/system.array.find) that takes an array and a method as arguments. `Array.Find()` calls the method on each element of the array and returns the first element for which the method returns `true`.

```c#
namespace AlternateExpressions
{
  class Program
  {
  	// Method to be used as second argument
   	public static bool IsLong(string word)
    {
      return word.Length > 8;
    }
      
    static void Main(string[] args)
    {
      // Array to be used as first argument
      string[] adjectives = {"rocky", "mountainous", "cosmic", "extraterrestrial"};
     
      // Call Array.Find() and 
      // Pass in the array and method as arguments
      string firstLongAdjective = Array.Find(adjectives, IsLong);
      
      Console.WriteLine($"The first long word is: {firstLongAdjective}.");
    }
  }
}
```

### Lambda Expressions
The next shortcut, _lambda expressions_, are great for situations when you need to pass a method as an argument.

In the past exercise, we used `IsEven()` to check that an even value exists in the array `numbers`:

```c#
int[] numbers = {1, 3, 5, 6, 7, 8};

public static bool IsEven(int num)
{
  return num % 2 == 0;
}

bool hasEvenNumber = Array.Exists(numbers, IsEven);
```

With a lambda expression, we can define `IsEven()` directly in the method call. We don’t even need to give it a name:

```c#
bool hasEvenNumber = Array.Exists(numbers, (int num) => num % 2 == 0 );
```

This might look similar to an expression-bodied definition. It sort of is! What makes a lambda expression unique is that it is an _anonymous method:_ it has no name.

Generally lambda expressions with one expression (like the above example) take this form. They use the fat arrow, no curly braces, and no semicolon (`;`):

```
(input-parameters) => expression
```

Lambda expressions with more than one expression use curly braces and semicolon:

```
(input-parameters) => { statement; }
```

Here’s an example of the second structure, which checks if any element in `numbers` is a multiple of 12 and greater than 20:

```c#
bool hasBigDozen = Array.Exists(numbers, (int num) => {
  bool isDozenMultiple = num % 12 == 0;
  bool greaterThan20 = num > 20;
  return isDozenMultiple && greaterThan20;
});
```



# Arrays and Loops

## Arrays

## Loops



# Classes and Objects

## Basic Classes and Objects

## Static Members



# Interfaces and Inheritance

## Interfaces

## Inheritance



# References

## Reference Fundamentals

## The Object Class

## String, The Exception



# Lists and LINQ

## Lists

## LINQ

