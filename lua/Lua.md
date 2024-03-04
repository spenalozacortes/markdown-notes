#lua
# Introduction to Lua

## Introduction to Lua

### Hello World
When learning a new language, tradition suggests that our first program prints to the screen: `Hello, world!`.

In Lua, this can be done in a single line:

```lua
print("Hello, world!")
```

### Comments
A **single line comment** will comment out a single line and is denoted by two dashes `--` preceding it:

```lua
-- Start the program by greeting the world! Prints "hi"
print("hi")
```

You can also use a single line comment after a line of code:

```lua
print("hi")  -- Prints "hi"
```

### Multi-line Comments
Sometimes, we will have a section of our code that we want to temporarily disable. We can do this by using [comments](https://www.codecademy.com/resources/docs/lua/comments) to “comment out” those lines.

A **multi-line comment** will comment out multiple lines and is denoted by `--[[` to begin the comment, and `]]` to end the comment:

```lua
--[[ 
print("Disable me!")
print("This shouldn't happen")
print("Let the hacking begin...")
]]
```

### Review
- Lua is a general-purpose coding language.
- The code is read from top to bottom.
- `print()` is used to output to the terminal:

```lua
print("This... is... fun.")
```

- Single line [comments](https://www.codecademy.com/resources/docs/lua/comments) are created using `--`.

```lua
--This will not run
```

- Multiline comments are created using `--[[` `]]--`.

```lua
--[[ 
print("Disable me!")
print("This shouldn't happen")
print("Let the hacking begin...")
]]--
```

# Variables and Data

## Data Types and Operators

### Introduction
All programs consist of **data** and **operations** we perform on that data.

In programming, this differentiation of **data types** is essential.

### Categorizing Data With Types
**Data** is information stored by a computer.

To stop the data from becoming a jumbled mess inside our computers, we must have a system to _organize_ and _differentiate_ the data.

This organization is crucial because we can do different things with different data.

In Lua, data can be organized into four basic **data types**, each with distinct behavior and purposes.

|Data Types|Definition|Syntax|Example of Use|
|---|---|---|---|
|Number|A numeric value including positive values, negative values, and decimal values.|`10`, `3.5`, `-4`|To store how many followers you have on Instagram.|
|String|A sequence of individual characters inside quotations. It can be letters, spaces, numbers, or symbols.|`"This is a string"`  <br>`'I have 5 cats!'`|To store your username on a website.|
|Boolean  <br>(boo·lee·uhn)|A value that only has two possible values: true or false.|`true`  <br>`false`|To indicate whether you have dark mode on or not.|
|Nil|A representation for the absence of a value. If there is no value, it is nil.|`nil`|To indicate an empty box on a fillable form.|

Note: There are also an additional four complex data types that we won’t go into now. They are: Tables, Functions, Userdata, and Threads.

### String and Number Syntax
Strings can be created using double quotes (`"`) or single quotes (`'`), it’s up to you (as long as they match). Both of these are valid strings:

```lua
print("Hello, World!")
-- output: Hello, World!

print('Hello, World!')
-- output: Hello, World!
```

To include single and double quote characters in your string, use `\` in front of the character you want to include:

```lua
print("\"What? Like it's hard?\" -Legally Blonde (2001)")
-- output: "What? Like it's hard?" - Legally Blonde (2001)
```

Whenever you’re not sure what type your value is, use the [`type()`](https://www.codecademy.com/resources/docs/lua/mathematical-library/type) function to help you figure it out!

```lua
print(type("What am I?"))
-- output: string
```

### Calculating With Arithmetic Operators
An operator is a special character that transforms data. Arithmetic operators are characters that help us perform calculations such as addition, subtraction, multiplication, and more.

|Operator Name|Description|Syntax|Example|Result|
|---|---|---|---|---|
|Addition|Adds two numbers|x + y|5 + 2|7|
|Subtraction|Subtracts two numbers|x - y|5 - 2|3|
|Multiplication|Multiplies two numbers|x * y|5 * 2|10|
|Division|Divides two numbers|x / y|5 / 2|2.5|
|Exponential|Takes the exponent of two numbers|x ^ y|5 ^ 2|25|
|Remainder  <br>(also known as modulo or modulus)|Gives us the remaining leftover number after we’ve divided two numbers.|x % y|5 % 2|1|
|Negation|Reverses the sign value of the number.|-x|-(3+2)|-5|
When we use an operator to transform data, we call it an **expression** that **evaluates** to a new value.

### Review
- Programs use **data**. *Data has an associated **data type**. *Data types determine what we can do with the data.
- The four basic [data types](https://www.codecademy.com/resources/docs/lua/data-types) are:
    - **Number**: A numeric value.
    - **String**: A sequence of characters, often used for text.
    - **Nil**: A value that represents the absence of value.
    - **Boolean**: A value that can be either true or false only.
- A **string** can look like many other data types, but data is a string only if the value is surrounded by matching single or double quotation marks.
- We can use **arithmetic operations** on number data.
- The arithmetic [operators](https://www.codecademy.com/resources/docs/lua/operators) are `+`, `-`, `*`, `/`, `^`, `%`, `-`.
- Transformations by arithmetic operators result in an **expression**. Expressions are code that can be **evaluated** to a resulting value.
- Whenever we’re unsure what data type a value has, we can use the [`type()`](https://www.codecademy.com/resources/docs/lua/mathematical-library/type) function to help us figure that out.

## Variables
#aqui
### Introduction to Variables
[Variables](https://www.codecademy.com/resources/docs/lua/variables) are named containers in the computer’s memory that can help us store, retrieve, and manipulate data.

### Defining Variables
Suppose we have two players, we’ll need to create two variables:

```lua
player1Score = 0
player2Score = 0
```

The basic syntax for declaring a variable is: `name = value`. 

We can directly reference the variable with

```lua
print(player1Score)
--output: 0
```

### Using type() With Variables
Previously, we were able to use `type()` to find the data type of our data values. We can also use `type()` on variables to find the data type of its value.

```lua
catchphrase = "Avengers Assemble!"
print(type(catchphrase))
--output: string
```

### Variable Reassignment
After we’ve declared a variable and assigned it a value, we can change that value if we need to. The variable name will continue to represent that piece of data, even after the data value has been changed.

```lua
highestScore = nil
print(highestScore)
--output: nil
highestScore = 25
print(highestScore)
--output: 25
```

Reassignment looks identical to creating a new variable.

We can also assign variables to the value of another variable like this:

```lua
legendaryPlayerScore = 616
highestScore = legendaryPlayerScore
print(highestScore)
--output: 616
```

Since variables in Lua do not have a type — it is just a container for data — you can reassign a value of any data type to a variable. Be careful with this feature of Lua. Accidentally changing the type of a variable is easy and can lead to trouble down the road!

```lua
highestScore = 24
print(highestScore + 1) --output: 25
highestScore = "Kamala"
print(highestScore + 1) --error: attempt to add a 'string' with a 'number'
```

### Using Arithmetic Operators With Variables
We can compute new values for our [variables](https://www.codecademy.com/resources/docs/lua/variables) with arithmetic [operators](https://www.codecademy.com/resources/docs/lua/operators).

```lua
player1Score = 0
player1Score = player1Score + 1
print(player1Score)
--output: 1
```

|Operator|Example|
|---|---|
|Addition|myVariable = myVariable + 1|
|Subtraction|myVariable = myVariable - 1|
|Multiplication|myVariable = myVariable * 1|
|Division|myVariable = myVariable / 1|
|Exponentiation|myVariable = myVariable ^ 1|
|Remainder|myVariable = myVariable % 1|
|Negation|myVariable = -myVariable|
### Concatenation
**Concatenation** is the act of joining values (often [strings](https://www.codecademy.com/resources/docs/lua/strings) or numbers) together. To do this, we use the concatenation operator (`..`).

```lua
print("The current player with the highest score is " .. "Bruno")
--output: The current player with the highest score is Bruno
```

Concatenation becomes useful when we need changeable or reusable output with different values.

```lua
highestScorerName = "Bruno"
print("The current player with the highest score is " .. highestScorerName)
--output: The current player with the highest score is Bruno
```

Note: Concatenation produces a whole new string to the output and does not modify the values used to create it.

### Type Coercion in Concatenation and Arithmetic Operations
Suppose we need to use concatenation to make a result that mixes different data types such as a number and a string like this:

```lua
highestScore = 25
print("The highest score is: " .. highestScore)
```

In Lua, these situations are handled with automatic **type coercion**. Type coercion is the conversion of a value from one data type to another. Lua does this automatically and converts a string to a number or a number to a string depending on what is needed.

With type coercion, the _number_ value `25` will be coerced into a _string_ data type. Thus, it will work with the concatenation operator and string to produce `"The highest score is: 25"`.

Type coercion extends to arithmetic operators too.

```lua
print("100" + 5)
```

`105`. `"100"` is a string data type coerced into a number data type. Thus, the expression becomes `100 + 5` thanks to the presence of the addition operator.

```lua
print("100" + 5 .. 6)
```

`1056`. The expression is evaluated from left to right. From the last example, we know `"100" + 5` evaluates to the number `105`. But, the concatenation operator (`..`) coerces both `105` and `6` into string data types and produces `1056`.

If we want to be clear with our expressions, we can convert with functions `tonumber()` and `tostring()` when we are mixing data types.

```lua
highestScore = 25
print("The highest score is: " .. tostring(highestScore))
-- output: The highest score is: 25
```

### Review
- A **variable** is a container in the computer’s memory that helps us store, retrieve, and manipulate data.
- A variable can store data values of different **data types**. To find the data type of the data inside a variable, we can use [`type()`](https://www.codecademy.com/resources/docs/lua/mathematical-library/type) with the name of the variable.
- To define a variable, we give the variable a name, followed by the equal sign (`=`), and the value the variable should store.
- We can change the value in a variable by **reassigning** it to a new value.
- The **concatenation** operator (`..`) allows us to join values together and results in a string.
- When different [data types](https://www.codecademy.com/resources/docs/lua/data-types) are combined with concatenation or arithmetic [operators](https://www.codecademy.com/resources/docs/lua/operators), values are **coerced** into the appropriate data type.
#aqui 




# Conditionals & Logic

## Conditionals & Logic



# Functions

## Functions

