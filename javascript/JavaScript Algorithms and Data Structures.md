# Basic JavaScript

**JavaScript is a scripting language you can use to make web pages interactive. It is one of the core technologies of the web, along with HTML and CSS, and is supported by all modern browsers.**

## Comment your JavaScript code
Comments are lines of code that JavaScript will intentionally ignore. Comments are a great way to leave notes to yourself and to other people who will later need to figure out what that code does.

There are two ways to write comments in JavaScript:

Using `//` will tell JavaScript to ignore the remainder of the text on the current line. This is an in-line comment:

```js
// This is an in-line comment.
```

You can make a multi-line comment beginning with `/*` and ending with `*/`. This is a multi-line comment:

```js
/* This is a
multi-line comment */
```

## Declare JavaScript variables
In computer science, data is anything that is meaningful to the computer. JavaScript provides eight different data types which are undefined, null, boolean, string, symbol, bigint, number, and object.

Variables allow computers to store and manipulate data in a dynamic fashion. They do this by using a "label" to point to the data rather than using the data itself. Any of the eight data types may be stored in a variable.

We tell JavaScript to create or declare a variable by putting the keyword `var` in front of it.

```js
var ourName;
```

In JavaScript we end statements with semicolons. Variable names can be made up of numbers, letters, and $ or `_`, but may not contain spaces or start with a number.

## Storing Values with the Assignment Operator
In JavaScript, you can store a value in a variable with the assignment operator (`=`).

```js
myVariable = 5;
```

If there are any calculations to the right of the `=` operator, those are performed before the value is assigned to the variable on the left of the operator.

## Assigning the Value of One Variable to Another
After a value is assigned to a variable using the assignment operator, you can assign the value of that variable to another variable using the assignment operator.

```js
var myVar;
myVar = 5;
var myNum;
myNum = myVar;
```

## Initializing Variables with the Assignment Operator
It is common to initialize a variable to an initial value in the same line as it is declared.

```js
var myVar = 0;
```

## Declare String Variables
You can also declare a string variable like this:

```js
var myName = "your name";
```

`"your name"` is called a string literal. A string literal, or string, is a series of zero or more characters enclosed in single or double quotes.

## Understanding Uninitialized Variables
When JavaScript variables are declared, they have an initial value of `undefined`. If you do a mathematical operation on an undefined variable your result will be `NaN` which means "Not a Number". If you concatenate a string with an `undefined` variable, you will get a string of `undefined`.

## Understanding Case Sensitivity in Variables
In JavaScript all variables and function names are case sensitive. This means that capitalization matters.

MYVAR is not the same as MyVar nor myvar. It is possible to have multiple distinct variables with the same name but different casing. It is strongly recommended that for the sake of clarity, you do not use this language feature.

**Best practice**: Write variable names in JavaScript in camelCase. In camelCase, multi-word variable names have the first word in lowercase and the first letter of each subsequent word is capitalized.

## Explore Differences Between the var and let Keywords
One of the biggest problems with declaring variables with the var keyword is that you can easily overwrite variable declarations.

```js
var camper = "James";
var camper = "David";
console.log(camper);
```

In the code above, the camper variable is originally declared as James, and is then overridden to be David. The console then displays the string David.

A keyword called let was introduced in ES6, a major update to JavaScript, to solve this potential issue with the var keyword. 

If you replace var with let in the code above, it results in an error:

```js
let camper = "James";
let camper = "David";
```

So unlike var, when you use let, a variable with the same name can only be declared once.

## Declare a Read-Only Variable with the const Keyword
The keyword `let` is not the only new way to declare variables. In ES6, you can also declare variables using the `const` keyword.

`const` has all the awesome features that `let` has, with the added bonus that variables declared using `const` are read-only. They are a constant value, which means that once a variable is assigned with `const`, it cannot be reassigned.

```js
const FAV_PET = "Cats";
FAV_PET = "Dogs";
```

The console will display an error due to reassigning the value of FAV_PET.

You should always name variables you don't want to reassign using the `const` keyword. This helps when you accidentally attempt to reassign a variable that is meant to stay constant.

**Note**: It is common for developers to use uppercase variable identifiers for immutable values and lowercase or camelCase for mutable values (objects and arrays). 

## Add Two Numbers with JavaScript
Number is a data type in JavaScript which represents numeric data.

JavaScript uses the + symbol as an addition operator when placed between two numbers.

```js
const myVar = 5 + 10;
```

## Subtract One Number from Another with JavaScript
We can also subtract one number from another.

JavaScript uses the - symbol for subtraction.

```js
const myVar = 12 - 6;
```

## Multiply Two Numbers with JavaScript
We can also multiply one number by another.

JavaScript uses the * symbol for multiplication of two numbers.

```js
const myVar = 13 * 13;
```

## Divide One Number by Another with JavaScript
We can also divide one number by another.

JavaScript uses the / symbol for division.

```js
const myVar = 16 / 2;
```

## Increment a Number with JavaScript
You can easily increment or add one to a variable with the ++ operator.

```js
i++;
```

is the equivalent of

```js
i = i + 1;
```

## Decrement a Number with JavaScript
You can easily decrement or decrease a variable by one with the -- operator.

```js
i--;
```

is the equivalent of

```js
i = i - 1;
```

## Create Decimal Numbers with JavaScript
Decimal numbers are sometimes referred to as floating point numbers or floats.

```js
let myDecimal = 5.7;
```

## Finding a Remainder in JavaScript
The remainder operator % gives the remainder of the division of two numbers.

In mathematics, a number can be checked to be even or odd by checking the remainder of the division of the number by 2.

**Note**: The remainder operator is sometimes incorrectly referred to as the modulus operator. It is very similar to modulus, but does not work properly with negative numbers.

```js
remainder = 11 % 3;
```

## Compound Assignment With Augmented Addition
Since this is such a common pattern, there are operators which do both a mathematical operation and assignment in one step.

One such operator is the += operator.

```js
let myVar = 1;
myVar += 5;
```

6 would be displayed in the console.

## Compound Assignment With Augmented Subtraction
Like the += operator, -= subtracts a number from a variable.

```js
myVar = myVar - 5;
```

will subtract 5 from myVar. This can be rewritten as:

```js
myVar -= 5;
```

## Compound Assignment With Augmented Multiplication
The `*=` operator multiplies a variable by a number.

```js
myVar = myVar * 5;
```

will multiply myVar by 5. This can be rewritten as:

```js
myVar *= 5;
```

## Compound Assignment With Augmented Division
The /= operator divides a variable by another number.

```js
myVar = myVar / 5;
```

Will divide myVar by 5. This can be rewritten as:

```js
myVar /= 5;
```

## Escaping Literal Quotes in Strings
When you are defining a string you must start and end with a single or double quote. What happens when you need a literal quote: " or ' inside of your string?

In JavaScript, you can escape a quote from considering it as an end of string quote by placing a backslash (`\`) in front of the quote.

```js
const sampleStr = "Alan said, \"Peter is learning JavaScript\".";
```

This signals to JavaScript that the following quote is not the end of the string, but should instead appear inside the string. 

## Quoting Strings with Single Quotes
String values in JavaScript may be written with single or double quotes, as long as you start and end with the same type of quote. Unlike some other programming languages, single and double quotes work the same in JavaScript.

```js
const doubleQuoteStr = "This is a string"; 
const singleQuoteStr = 'This is also a string';
```

The reason why you might want to use one type of quote over the other is if you want to use both in a string. This might happen if you want to save a conversation in a string and have the conversation in quotes. Another use for it would be saving an `<a>` tag with various attributes in quotes, all within a string.

```js
const conversation = 'Finn exclaims to Jake, "Algebraic!"';
```

However, this becomes a problem if you need to use the outermost quotes within it. Remember, a string has the same kind of quote at the beginning and end. But if you have that same quote somewhere in the middle, the string will stop early and throw an error.

```js
const goodStr = 'Jake asks Finn, "Hey, let\'s go on an adventure?"'; 
const badStr = 'Finn responds, "Let's go!"';
```

Here badStr will throw an error.

In the goodStr above, you can use both quotes safely by using the backslash `\` as an escape character.

## Escape Sequences in Strings
Quotes are not the only characters that can be escaped inside a string. There are two reasons to use escaping characters:

1. To allow you to use characters you may not otherwise be able to type out, such as a newline.
2. To allow you to represent multiple quotes in a string without JavaScript misinterpreting what you mean.

Code | Output
--- | ---
`\'`	| single quote
`\"` | double quote
`\\` | backslash
`\n`	| newline
`\t` | tab
`\r` | carriage return
`\b` | word boundary
`\f` | form feed

Note that the backslash itself must be escaped in order to display as a backslash.

```js
const myStr = "FirstLine\n\t\\SecondLine\nThirdLine";
```

## Concatenating Strings with Plus Operator
In JavaScript, when the + operator is used with a String value, it is called the concatenation operator. You can build a new string out of other strings by concatenating them together.

**Note**: Watch out for spaces. Concatenation does not add spaces between concatenated strings, so you'll need to add them yourself.
```js
const ourStr = "I come first. " + "I come second.";
```

## Concatenating Strings with the Plus Equals Operator
We can also use the += operator to concatenate a string onto the end of an existing string variable. This can be very helpful to break a long string over several lines.
```js
let ourStr = "I come first. ";
ourStr += "I come second.";
```

## Constructing Strings with Variables
Sometimes you will need to build a string. By using the concatenation operator (+), you can insert one or more variables into a string you're building.

```js
const ourName = "freeCodeCamp";
const ourStr = "Hello, our name is " + ourName + ", how are you?";
```

## Appending Variables to Strings
Just as we can build a string over multiple lines out of string literals, we can also append variables to a string using the plus equals (+=) operator.
```js
const anAdjective = "awesome!";
let ourStr = "freeCodeCamp is ";
ourStr += anAdjective;
```

## Find the Length of a String
You can find the length of a String value by writing `.length` after the string variable or string literal.

```js
console.log("Alan Peter".length);
```

The value 10 would be displayed in the console. Note that the space character between "Alan" and "Peter" is also counted.

## Use Bracket Notation to Find the First Character in a String
Bracket notation is a way to get a character at a specific index within a string.

Most modern programming languages, like JavaScript, don't start counting at 1 like humans do. They start at 0. This is referred to as Zero-based indexing.

```js
const firstName = "Charles";
const firstLetter = firstName[0];
```

firstLetter would have a value of the string C.

## Understand String Immutability
In JavaScript, String values are immutable, which means that they cannot be altered once created.

For example, the following code will produce an error because the letter B in the string Bob cannot be changed to the letter J.

```js
let myStr = "Bob";
myStr[0] = "J";
```

Note that this does not mean that myStr could not be re-assigned. The only way to change myStr would be to assign it with a new value.

```js
let myStr = "Bob";
myStr = "Job";
```

## Use Bracket Notation to Find the Nth Character in a String
You can also use bracket notation to get the character at other positions within a string.

```js
const firstName = "Ada";
const secondLetterOfFirstName = firstName[1];
```

secondLetterOfFirstName would have a value of the string d.

## Use Bracket Notation to Find the Last Character in a String
In order to get the last letter of a string, you can subtract one from the string's length.

```js
const firstName = "Ada";
const lastLetter = firstName[firstName.length - 1];
```

lastLetter would have a value of the string a.

## Use Bracket Notation to Find the Nth-to-Last Character in a String
You can use the same principle we just used to retrieve the last character in a string to retrieve the Nth-to-last character.

```js
const firstName = "Augusta";
const thirdToLastLetter = firstName[firstName.length - 3];
```

thirdToLastLetter would have a value of the string s.

## Store Multiple Values in one Variable using JavaScript Arrays
With JavaScript array variables, we can store several pieces of data in one place.

You start an array declaration with an opening square bracket, end it with a closing square bracket, and put a comma between each entry.

```js
const sandwich = ["peanut butter", "jelly", "bread"];
```

## Nest one Array within Another Array
You can also nest arrays within other arrays.

```js
const teams = [["Bulls", 23], ["White Sox", 45]];
```

This is also called a *multi-dimensional array*.

## Access Array Data with Indexes
We can access the data inside arrays using indexes.

Array indexes are written in the same bracket notation that strings use, except that instead of specifying a character, they are specifying an entry in the array. Like strings, arrays use zero-based indexing, so the first element in an array has an index of 0.

```js
const array = [50, 60, 70];
console.log(array[0]);
const data = array[1];
```

The `console.log(array[0])` prints 50, and data has the value 60.

## Modify Array Data With Indexes
Unlike strings, the entries of arrays are mutable and can be changed freely, even if the array was declared with const.

```js
const ourArray = [50, 40, 30];
ourArray[0] = 15;
```

ourArray now has the value `[15, 40, 30]`.

***Note***: There shouldn't be any spaces between the array name and the square brackets, like array `[0]`. Although JavaScript is able to process this correctly, this may confuse other programmers reading your code.

## Access Multi-Dimensional Arrays With Indexes
One way to think of a multi-dimensional array, is as an array of arrays. When you use brackets to access your array, the first set of brackets refers to the entries in the outermost (the first level) array, and each additional pair of brackets refers to the next level of entries inside.

```js
const arr = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
  [[10, 11, 12], 13, 14]
];

const subarray = arr[3];
const nestedSubarray = arr[3][0];
const element = arr[3][0][1];
```

In this example, subarray has the value `[[10, 11, 12], 13, 14]`, nestedSubarray has the value `[10, 11, 12]`, and element has the value 11 .

## Manipulate Arrays With push()
An easy way to append data to the end of an array is via the push() function.

.push() takes one or more parameters and "pushes" them onto the end of the array.

```js
const arr1 = [1, 2, 3];
arr1.push(4);

const arr2 = ["Stimpson", "J", "cat"];
arr2.push(["happy", "joy"]);
```

arr1 now has the value `[1, 2, 3, 4]` and arr2 has the value `["Stimpson", "J", "cat", ["happy", "joy"]]`.

## Manipulate Arrays With pop()
.pop() is used to pop a value off of the end of an array. We can store this popped off value by assigning it to a variable. In other words, .pop() removes the last element from an array and returns that element.

Any type of entry can be popped off of an array - numbers, strings, even nested arrays.

```js
const threeArr = [1, 4, 6];
const oneDown = threeArr.pop();
console.log(oneDown);
console.log(threeArr);
```

The first console.log will display the value 6, and the second will display the value `[1, 4]`.

## Manipulate Arrays With shift()
pop() always removes the last element of an array. What if you want to remove the first?

That's where .shift() comes in. It works just like .pop(), except it removes the first element instead of the last.

```js
const ourArray = ["Stimpson", "J", ["cat"]];
const removedFromOurArray = ourArray.shift();
```

removedFromOurArray would have a value of the string Stimpson, and ourArray would have `["J", ["cat"]]`.

## Manipulate Arrays With unshift()
Not only can you shift elements off of the beginning of an array, you can also unshift elements to the beginning of an array i.e. add elements in front of the array.

.unshift() works exactly like .push(), but instead of adding the element at the end of the array, unshift() adds the element at the beginning of the array.

```js
const ourArray = ["Stimpson", "J", "cat"];
ourArray.shift();
ourArray.unshift("Happy");
```

After the shift, ourArray would have the value `["J", "cat"]`. After the unshift, ourArray would have the value `["Happy", "J", "cat"]`.

## Write Reusable JavaScript with Functions
In JavaScript, we can divide up our code into reusable parts called functions.

```js
function functionName() {
  console.log("Hello World");
}
```

You can call or invoke this function by using its name followed by parentheses, like this: functionName(); Each time the function is called it will print out the message Hello World on the dev console. All of the code between the curly braces will be executed every time the function is called.

## Passing Values to Functions with Arguments
Parameters are variables that act as placeholders for the values that are to be input to a function when it is called. When a function is defined, it is typically defined along with one or more parameters. The actual values that are input (or "passed") into a function when it is called are known as arguments.

Here is a function with two parameters, param1 and param2:

```js
function testFun(param1, param2) {
  console.log(param1, param2);
}
```

Then we can call testFun like this: testFun("Hello", "World");. We have passed two string arguments, Hello and World. Inside the function, param1 will equal the string Hello and param2 will equal the string World. Note that you could call testFun again with different arguments and the parameters would take on the value of the new arguments.

## Return a Value from a Function with Return
We can pass values into a function with arguments. You can use a return statement to send a value back out of a function.

```js
function plusThree(num) {
  return num + 3;
}

const answer = plusThree(5);
```

answer has the value 8.

plusThree takes an argument for num and returns a value equal to num + 3.

## Global Scope and Functions
In JavaScript, *scope* refers to the visibility of variables. Variables which are defined outside of a function block have *Global* scope. This means, they can be seen everywhere in your JavaScript code.

Variables which are declared without the let or const keywords are automatically created in the global scope. This can create unintended consequences elsewhere in your code or when running a function again. You should always declare your variables with let or const.

## Local Scope and Functions
Variables which are declared within a function, as well as the function parameters, have local scope. That means they are only visible within that function.

Here is a function myTest with a local variable called loc.

```js
function myTest() {
  const loc = "foo";
  console.log(loc);
}

myTest();
console.log(loc);
```

The myTest() function call will display the string foo in the console. The console.log(loc) line (outside of the myTest function) will throw an error, as loc is not defined outside of the function.

## Global vs. Local Scope in Functions
It is possible to have both local and global variables with the same name. When you do this, the local variable takes precedence over the global variable.

In this example:

```js
const someVar = "Hat";

function myFun() {
  const someVar = "Head";
  return someVar;
}
```

The function myFun will return the string Head because the local version of the variable is present.

## Understanding Undefined Value returned from a Function
A function can include the return statement but it does not have to. In the case that the function doesn't have a return statement, when you call it, the function processes the inner code but the returned value is undefined.
```js
let sum = 0;

function addSum(num) {
  sum = sum + num;
}

addSum(3);
```

addSum is a function without a return statement. The function will change the global sum variable but the returned value of the function is undefined.

## Assignment with a Returned Value
Everything to the right of the equal sign is resolved before the value is assigned. This means we can take the return value of a function and assign it to a variable.

Assume we have pre-defined a function sum which adds two numbers together, then:

```js
ourSum = sum(5, 12);
```

will call the sum function, which returns a value of 17 and assigns it to the ourSum variable.

## Stand in Line
In Computer Science a queue is an abstract Data Structure where items are kept in order. New items can be added at the back of the queue and old items are taken off from the front of the queue.

```js
function nextInLine(arr, item) {
  // Only change code below this line
  arr.push(item);
  item = arr.shift();
  return item;
  // Only change code above this line
}

// Setup
let testArr = [1, 2, 3, 4, 5];

// Display code
console.log("Before: " + JSON.stringify(testArr));
console.log(nextInLine(testArr, 6));
console.log("After: " + JSON.stringify(testArr));
```

## Understanding Boolean Values
Another data type is the Boolean. Booleans may only be one of two values: true or false. They are basically little on-off switches, where true is on and false is off. These two states are mutually exclusive.

**Note**: Boolean values are never written with quotes. The strings "true" and "false" are not Boolean and have no special meaning in JavaScript.

## Use Conditional Logic with If Statements
if statements are used to make decisions in code. The keyword if tells JavaScript to execute the code in the curly braces under certain conditions, defined in the parentheses. These conditions are known as Boolean conditions and they may only be true or false.

When the condition evaluates to true, the program executes the statement inside the curly braces. When the Boolean condition evaluates to false, the statement inside the curly braces will not execute.

```js
function test (myCondition) {
  if (myCondition) {
    return "It was true";
  }
  return "It was false";
}

test(true);
test(false);
```

test(true) returns the string It was true, and test(false) returns the string It was false.

## Comparison with the Equality Operator
There are many comparison operators in JavaScript. All of these operators return a boolean true or false value.

The most basic operator is the equality operator `==`. The equality operator compares two values and returns true if they're equivalent or false if they are not. Note that equality is different from assignment (`=`), which assigns the value on the right of the operator to a variable on the left.

```js
function equalityTest(myVal) {
  if (myVal == 10) {
    return "Equal";
  }
  return "Not Equal";
}
```

If myVal is equal to 10, the equality operator returns true, so the code in the curly braces will execute, and the function will return Equal. Otherwise, the function will return Not Equal. In order for JavaScript to compare two different data types (for example, numbers and strings), it must convert one type to another. This is known as Type Coercion. Once it does, however, it can compare terms as follows:

```js
1   ==  1  // true
1   ==  2  // false
1   == '1' // true
"3" ==  3  // true
```

## Comparison with the Strict Equality Operator
Strict equality (`===`) is the counterpart to the equality operator (`==`). However, unlike the equality operator, which attempts to convert both values being compared to a common type, the strict equality operator does not perform a type conversion.

If the values being compared have different types, they are considered unequal, and the strict equality operator will return false.

```js
3 ===  3  // true
3 === '3' // false
```

In the second example, 3 is a Number type and '3' is a String type.

## Practice comparing different values
In JavaScript, you can determine the type of a variable or a value with the typeof operator, as follows:

```js
typeof 3
typeof '3'
```

typeof 3 returns the string number, and typeof '3' returns the string string.

## Comparison with the Inequality Operator
The inequality operator (!=) is the opposite of the equality operator. It means not equal and returns false where equality would return true and vice versa. Like the equality operator, the inequality operator will convert data types of values while comparing.

```js
1 !=  2    // true
1 != "1"   // false
1 != '1'   // false
1 != true  // false
0 != false // false
```

## Comparison with the Strict Inequality Operator
The strict inequality operator (`!==`) is the logical opposite of the strict equality operator. It means "Strictly Not Equal" and returns false where strict equality would return true and vice versa. The strict inequality operator will not convert data types.

```js
3 !==  3  // false
3 !== '3' // true
4 !==  3  // true
```

## Comparison with the Greater Than Operator
The greater than operator (>) compares the values of two numbers. If the number to the left is greater than the number to the right, it returns true. Otherwise, it returns false.

Like the equality operator, the greater than operator will convert data types of values while comparing.

```js
5   >  3  // true
7   > '3' // true
2   >  3  // false
'1' >  9  // false
```

## Comparison with the Greater Than Or Equal To Operator
The greater than or equal to operator (>=) compares the values of two numbers. If the number to the left is greater than or equal to the number to the right, it returns true. Otherwise, it returns false.

```js
6   >=  6  // true
7   >= '3' // true
2   >=  3  // false
'7' >=  9  // false
```

## Comparison with the Less Than Operator
The less than operator (<) compares the values of two numbers. If the number to the left is less than the number to the right, it returns true. Otherwise, it returns false.

```js
2   < 5 // true
'3' < 7 // true
5   < 5 // false
3   < 2 // false
'8' < 4 // false
```

## Comparison with the Less Than Or Equal To Operator
The less than or equal to operator (<=) compares the values of two numbers. If the number to the left is less than or equal to the number to the right, it returns true. If the number on the left is greater than the number on the right, it returns false.

```js
4   <= 5 // true
'7' <= 7 // true
5   <= 5 // true
3   <= 2 // false
'8' <= 4 // false
```

## Comparisons with the Logical And Operator
Sometimes you will need to test more than one thing at a time. The logical and operator (&&) returns true if and only if the operands to the left and right of it are true.

The same effect could be achieved by nesting an if statement inside another if:

```js
if (num > 5) {
  if (num < 10) {
    return "Yes";
  }
}
return "No";
```

will only return Yes if num is greater than 5 and less than 10. The same logic can be written as:

```js
if (num > 5 && num < 10) {
  return "Yes";
}
return "No";
```

## Comparisons with the Logical Or Operator
The logical or operator (||) returns true if either of the operands is true. Otherwise, it returns false.

The logical or operator is composed of two pipe symbols: (||). 

The pattern below should look familiar from prior waypoints:

```js
if (num > 10) {
  return "No";
}
if (num < 5) {
  return "No";
}
return "Yes";
```

will return Yes only if num is between 5 and 10 (5 and 10 included). The same logic can be written as:

```js
if (num > 10 || num < 5) {
  return "No";
}
return "Yes";
```

## Introducing Else Statements
When a condition for an if statement is true, the block of code following it is executed. What about when that condition is false? Normally nothing would happen. With an else statement, an alternate block of code can be executed.

```js
if (num > 10) {
  return "Bigger than 10";
} else {
  return "10 or Less";
}
```

## Introducing Else If Statements
If you have multiple conditions that need to be addressed, you can chain if statements together with else if statements.

```js
if (num > 15) {
  return "Bigger than 15";
} else if (num < 5) {
  return "Smaller than 5";
} else {
  return "Between 5 and 15";
}
```

## Logical Order in If Else Statements
Order is important in if, else if statements.

The function is executed from top to bottom so you will want to be careful of what statement comes first.

Take these two functions as an example.

Here's the first:

```js
function foo(x) {
  if (x < 1) {
    return "Less than one";
  } else if (x < 2) {
    return "Less than two";
  } else {
    return "Greater than or equal to two";
  }
}
```

And the second just switches the order of the statements:

```js
function bar(x) {
  if (x < 2) {
    return "Less than two";
  } else if (x < 1) {
    return "Less than one";
  } else {
    return "Greater than or equal to two";
  }
}
```

While these two functions look nearly identical if we pass a number to both we get different outputs.

```js
foo(0)
bar(0)
```

foo(0) will return the string Less than one, and bar(0) will return the string Less than two.

## Selecting from Many Options with Switch Statements
If you have many options to choose from, use a switch statement. A switch statement tests a value and can have many case statements which define various possible values. Statements are executed from the first matched case value until a break is encountered.

```js
switch (lowercaseLetter) {
  case "a":
    console.log("A");
    break;
  case "b":
    console.log("B");
    break;
}
```

case values are tested with strict equality (`===`). The break tells JavaScript to stop executing statements. If the break is omitted, the next statement will be executed.

## Adding a Default Option in Switch Statements
In a switch statement you may not be able to specify all possible values as case statements. Instead, you can add the default statement which will be executed if no matching case statements are found. Think of it like the final else statement in an if/else chain.

A default statement should be the last case.

```js
  switch(val) {
    case 'a':
      answer = "apple";
      break;
    case 'b':
      answer = "bird";
      break;
    case 'c':
      answer = "cat";
      break;
    default:
      answer = "stuff";
      break;
  }
```

## Multiple Identical Options in Switch Statements
If the break statement is omitted from a switch statement's case, the following case statement(s) are executed until a break is encountered. If you have multiple inputs with the same output, you can represent them in a switch statement like this:

```js
let result = "";
switch (val) {
  case 1:
  case 2:
  case 3:
    result = "1, 2, or 3";
    break;
  case 4:
    result = "4 alone";
}
```

Cases for 1, 2, and 3 will all produce the same result.

## Replacing If Else Chains with Switch
If you have many options to choose from, a switch statement can be easier to write than many chained if/else if statements. The following:

```js
if (val === 1) {
  answer = "a";
} else if (val === 2) {
  answer = "b";
} else {
  answer = "c";
}
```

can be replaced with:
```js
switch (val) {
  case 1:
    answer = "a";
    break;
  case 2:
    answer = "b";
    break;
  default:
    answer = "c";
}
```

## Return Early Pattern for Functions
When a return statement is reached, the execution of the current function stops and control returns to the calling location.
```js
function myFun() {
  console.log("Hello");
  return "World";
  console.log("byebye")
}
myFun();
```

The above will display the string Hello in the console, and return the string World. The string byebye will never display in the console, because the function exits at the return statement.

## Build JavaScript Objects
Objects are similar to arrays, except that instead of using indexes to access and modify their data, you access the data in objects through what are called properties.

Objects are useful for storing data in a structured way, and can represent real world objects, like a cat.

```js
const cat = {
  "name": "Whiskers",
  "legs": 4,
  "tails": 1,
  "enemies": ["Water", "Dogs"]
};
```

You can also use numbers as properties. You can even omit the quotes for single-word string properties, as follows:

```js
const anotherObject = {
  make: "Ford",
  5: "five",
  "model": "focus"
};
```

However, if your object has any non-string properties, JavaScript will automatically typecast them as strings.

## Accessing Object Properties with Dot Notation
There are two ways to access the properties of an object: dot notation (.) and bracket notation (`[]`), similar to an array.

Dot notation is what you use when you know the name of the property you're trying to access ahead of time.

```js
const myObj = {
  prop1: "val1",
  prop2: "val2"
};

const prop1val = myObj.prop1;
const prop2val = myObj.prop2;
```

prop1val would have a value of the string val1, and prop2val would have a value of the string val2.

## Accessing Object Properties with Bracket Notation
The second way to access the properties of an object is bracket notation (`[]`). If the property of the object you are trying to access has a space in its name, you will need to use bracket notation.

However, you can still use bracket notation on object properties without spaces.

```js
const myObj = {
  "Space Name": "Kirk",
  "More Space": "Spock",
  "NoSpace": "USS Enterprise"
};

myObj["Space Name"];
myObj['More Space'];
myObj["NoSpace"];
```

`myObj["Space Name"]` would be the string Kirk, `myObj['More Space']` would be the string Spock, and `myObj["NoSpace"]` would be the string USS Enterprise.

Note that property names with spaces in them must be in quotes (single or double).

## Accessing Object Properties with Variables
Another use of bracket notation on objects is to access a property which is stored as the value of a variable. This can be very useful for iterating through an object's properties or when accessing a lookup table.

```js
const dogs = {
  Fido: "Mutt",
  Hunter: "Doberman",
  Snoopie: "Beagle"
};

const myDog = "Hunter";
const myBreed = dogs[myDog];
console.log(myBreed);
```

The string Doberman would be displayed in the console.

Note that we do not use quotes around the variable name when using it to access the property because we are using the *value* of the variable, not the *name*.

## Updating Object Properties
After you've created a JavaScript object, you can update its properties at any time just like you would update any other variable. You can use either dot or bracket notation to update.

```js
const ourDog = {
  "name": "Camper",
  "legs": 4,
  "tails": 1,
  "friends": ["everything!"]
};
```

Since he's a particularly happy dog, let's change his name to the string Happy Camper. Here's how we update his object's name property: `ourDog.name = "Happy Camper";` or `ourDog["name"] = "Happy Camper";` Now when we evaluate ourDog.name, instead of getting Camper, we'll get his new name, Happy Camper.

## Add New Properties to a JavaScript Object
You can add new properties to existing JavaScript objects the same way you would modify them.

```js
const ourDog = {
  "name": "Camper",
  "legs": 4,
  "tails": 1,
  "friends": ["everything!"]
};

ourDog.bark = "bow-wow";
```

## Delete Properties from a JavaScript Object
We can also delete properties from objects like this:

```js
const ourDog = {
  "name": "Camper",
  "legs": 4,
  "tails": 1,
  "friends": ["everything!"],
  "bark": "bow-wow"
};

delete ourDog.bark;
```

## Using Objects for Lookups
Objects can be thought of as a key/value storage, like a dictionary. If you have tabular data, you can use an object to lookup values rather than a switch statement or an if/else chain. This is most useful when you know that your input data is limited to a certain range.

## Testing Objects for Properties
Sometimes it is useful to check if the property of a given object exists or not. We can use the .hasOwnProperty(propname) method of objects to determine if that object has the given property name. .hasOwnProperty() returns true or false if the property is found or not.

```js
const myObj = {
  top: "hat",
  bottom: "pants"
};

myObj.hasOwnProperty("top");
myObj.hasOwnProperty("middle");
```

The first hasOwnProperty returns true, while the second returns false.

## Manipulating Complex Objects
Sometimes you may want to store data in a flexible Data Structure. A JavaScript object is one way to handle flexible data. They allow for arbitrary combinations of strings, numbers, booleans, arrays, functions, and objects.

```js
const ourMusic = [
  {
    "artist": "Daft Punk",
    "title": "Homework",
    "release_year": 1997,
    "formats": [ 
      "CD", 
      "Cassette", 
      "LP"
    ],
    "gold": true
  }
];
```

This is an array which contains one object inside. The object has various pieces of metadata about an album. It also has a nested formats array. If you want to add more album records, you can do this by adding records to the top level array.

**Note**: You will need to place a comma after every object in the array, unless it is the last object in the array.

## Accessing Nested Objects
The sub-properties of objects can be accessed by chaining together the dot or bracket notation.

```js
const ourStorage = {
  "desk": {
    "drawer": "stapler"
  },
  "cabinet": {
    "top drawer": { 
      "folder1": "a file",
      "folder2": "secrets"
    },
    "bottom drawer": "soda"
  }
};

ourStorage.cabinet["top drawer"].folder2;
ourStorage.desk.drawer;
```

`ourStorage.cabinet["top drawer"].folder2` would be the string secrets, and ourStorage.desk.drawer would be the string stapler.

## Accessing Nested Arrays
As we have seen in earlier examples, objects can contain both nested objects and nested arrays. Similar to accessing nested objects, array bracket notation can be chained to access nested arrays.

```js
const ourPets = [
  {
    animalType: "cat",
    names: [
      "Meowzer",
      "Fluffy",
      "Kit-Cat"
    ]
  },
  {
    animalType: "dog",
    names: [
      "Spot",
      "Bowser",
      "Frankie"
    ]
  }
];

ourPets[0].names[1];
ourPets[1].names[0];
```

`ourPets[0].names[1]` would be the string Fluffy, and `ourPets[1].names[0]` would be the string Spot.

## Record Collection

```js
// Setup
const recordCollection = {
  2548: {
    albumTitle: 'Slippery When Wet',
    artist: 'Bon Jovi',
    tracks: ['Let It Rock', 'You Give Love a Bad Name']
  },
  2468: {
    albumTitle: '1999',
    artist: 'Prince',
    tracks: ['1999', 'Little Red Corvette']
  },
  1245: {
    artist: 'Robert Palmer',
    tracks: []
  },
  5439: {
    albumTitle: 'ABBA Gold'
  }
};

// Only change code below this line
function updateRecords(records, id, prop, value) {
  if(prop != "tracks" && value != "") {
    records[id][prop] = value;
  } else if(prop == "tracks" && !records[id].hasOwnProperty("tracks")) {
    records[id][prop] = [value];
  } else if(prop == "tracks" && value != "") {
    records[id][prop].push(value);
  } else if(value == "") {
    delete records[id][prop];
  }
  
  return records;
}

updateRecords(recordCollection, 5439, 'artist', 'ABBA');
```

## Iterate with JavaScript While Loops
You can run the same code multiple times by using a loop.

The first type of loop we will learn is called a while loop because it runs while a specified condition is true and stops once that condition is no longer true.

```js
const ourArray = [];
let i = 0;

while (i < 5) {
  ourArray.push(i);
  i++;
}
```

In the code example above, the while loop will execute 5 times and append the numbers 0 through 4 to ourArray.

## Iterate with JavaScript For Loops
The most common type of JavaScript loop is called a for loop because it runs for a specific number of times.

For loops are declared with three optional expressions separated by semicolons:

for (a; b; c), where a is the initialization statement, b is the condition statement, and c is the final expression.

The initialization statement is executed one time only before the loop starts. It is typically used to define and setup your loop variable.

The condition statement is evaluated at the beginning of every loop iteration and will continue as long as it evaluates to true. When the condition is false at the start of the iteration, the loop will stop executing. This means if the condition starts as false, your loop will never execute.

The final expression is executed at the end of each loop iteration, prior to the next condition check and is usually used to increment or decrement your loop counter.

In the following example we initialize with i = 0 and iterate while our condition i < 5 is true. We'll increment i by 1 in each loop iteration with i++ as our final expression.

```js
const ourArray = [];

for (let i = 0; i < 5; i++) {
  ourArray.push(i);
}
```

ourArray will now have the value `[0, 1, 2, 3, 4]`.

## Iterate Odd Numbers With a For Loop
For loops don't have to iterate one at a time. By changing our final-expression, we can count by even numbers.

```js
const ourArray = [];

for (let i = 0; i < 10; i += 2) {
  ourArray.push(i);
}
```

ourArray will now contain `[0, 2, 4, 6, 8]`. 

## Count Backwards With a For Loop
A for loop can also count backwards, so long as we can define the right conditions.

In order to decrement by two each iteration, we'll need to change our initialization, condition, and final expression.

```js
const ourArray = [];

for (let i = 10; i > 0; i -= 2) {
  ourArray.push(i);
}
```

ourArray will now contain `[10, 8, 6, 4, 2]`.

## Iterate Through an Array with a For Loop
A common task in JavaScript is to iterate through the contents of an array. One way to do that is with a for loop. This code will output each element of the array arr to the console:

```js
const arr = [10, 9, 8, 7, 6];

for (let i = 0; i < arr.length; i++) {
   console.log(arr[i]);
}
```

## Nesting For Loops
If you have a multi-dimensional array, you can use the same logic as the prior waypoint to loop through both the array and any sub-arrays. Here is an example:

```js
const arr = [
  [1, 2], [3, 4], [5, 6]
];

for (let i = 0; i < arr.length; i++) {
  for (let j = 0; j < arr[i].length; j++) {
    console.log(arr[i][j]);
  }
}
```

This outputs each sub-element in arr one at a time.

## Iterate with JavaScript Do...While Loops
It is called a do...while loop because it will first do one pass of the code inside the loop no matter what, and then continue to run the loop while the specified condition evaluates to true.

```js
const ourArray = [];
let i = 0;

do {
  ourArray.push(i);
  i++;
} while (i < 5);
```

The example above behaves similar to other types of loops, and the resulting array will look like `[0, 1, 2, 3, 4]`. However, what makes the do...while different from other loops is how it behaves when the condition fails on the first check. 

Essentially, a do...while loop ensures that the code inside the loop will run at least once. 

## Replace Loops using Recursion
Recursion is the concept that a function can be expressed in terms of itself. To help understand this, start by thinking about the following task: multiply the first n elements of an array to create the product of those elements. Using a for loop, you could do this:

```js
  function multiply(arr, n) {
    let product = 1;
    for (let i = 0; i < n; i++) {
      product *= arr[i];
    }
    return product;
  }
  ```

However, notice that `multiply(arr, n) == multiply(arr, n - 1) * arr[n - 1]`. That means you can rewrite multiply in terms of itself and never need to use a loop.

```js
  function multiply(arr, n) {
    if (n <= 0) {
      return 1;
    } else {
      return multiply(arr, n - 1) * arr[n - 1];
    }
  }
```

The recursive version of multiply breaks down like this. In the base case, where n <= 0, it returns 1. For larger values of n, it calls itself, but with n - 1. That function call is evaluated in the same way, calling multiply again until n <= 0. At this point, all the functions can return and the original multiply returns the answer.

**Note**: Recursive functions must have a base case when they return without calling the function again (in this example, when n <= 0), otherwise they can never finish executing.

## Profile Lookup

```js
// Setup
const contacts = [
  {
    firstName: "Akira",
    lastName: "Laine",
    number: "0543236543",
    likes: ["Pizza", "Coding", "Brownie Points"],
  },
  {
    firstName: "Harry",
    lastName: "Potter",
    number: "0994372684",
    likes: ["Hogwarts", "Magic", "Hagrid"],
  },
  {
    firstName: "Sherlock",
    lastName: "Holmes",
    number: "0487345643",
    likes: ["Intriguing Cases", "Violin"],
  },
  {
    firstName: "Kristian",
    lastName: "Vos",
    number: "unknown",
    likes: ["JavaScript", "Gaming", "Foxes"],
  },
];

function lookUpProfile(name, prop) {
  // Only change code below this line
  for (let i = 0; i < contacts.length; i++) {
    if (contacts[i].firstName == name) { // Primero encuentra el nombre y luego busca la propiedad
      if (contacts[i].hasOwnProperty(prop)) {
        return contacts[i][prop];
      } else {
        return "No such property";
      }
    } 
  }
  return "No such contact";

  // Only change code above this line
}

lookUpProfile("Akira", "likes");
```

## Generate Random Fractions with JavaScript
JavaScript has a Math.random() function that generates a random decimal number between 0 (inclusive) and 1 (exclusive). Thus Math.random() can return a 0 but never return a 1.

## Generate Random Whole Numbers with JavaScript
It's great that we can generate random decimal numbers, but it's even more useful if we use it to generate random whole numbers.

1. Use Math.random() to generate a random decimal.
2. Multiply that random decimal by 20.
3. Use another function, Math.floor() to round the number down to its nearest whole number.

Remember that Math.random() can never quite return a 1 and, because we're rounding down, it's impossible to actually get 20. This technique will give us a whole number between 0 and 19.

```js
Math.floor(Math.random() * 20);
```

## Generate Random Whole Numbers within a Range
Instead of generating a random whole number between zero and a given number like we did before, we can generate a random whole number that falls within a range of two specific numbers.

To do this, we'll define a minimum number min and a maximum number max.

```js
Math.floor(Math.random() * (max - min + 1)) + min
```

## Use the parseInt Function
The parseInt() function parses a string and returns an integer. 

```js
const a = parseInt("007");
```

The above function converts the string 007 to the integer 7. If the first character in the string can't be converted into a number, then it returns NaN.

## Use the parseInt Function with a Radix
The parseInt() function parses a string and returns an integer. It takes a second argument for the radix, which specifies the base of the number in the string. The radix can be an integer between 2 and 36.

```js
const a = parseInt("11", 2);
```

The radix variable says that 11 is in the binary system, or base 2. This example converts the string 11 to an integer 3.

## Use the Conditional (Ternary) Operator
The conditional operator, also called the ternary operator, can be used as a one line if-else expression.

The syntax is a ? b : c, where a is the condition, b is the code to run when the condition returns true, and c is the code to run when the condition returns false.

The following function uses an if/else statement to check a condition:

```js
function findGreater(a, b) {
  if(a > b) {
    return "a is greater";
  }
  else {
    return "b is greater or equal";
  }
}
```

This can be re-written using the conditional operator:

```js
function findGreater(a, b) {
  return a > b ? "a is greater" : "b is greater or equal";
}
```

## Use Multiple Conditional (Ternary) Operators
In the previous challenge, you used a single conditional operator. You can also chain them together to check for multiple conditions.

The following function uses if, else if, and else statements to check multiple conditions:

```js
function findGreaterOrEqual(a, b) {
  if (a === b) {
    return "a and b are equal";
  }
  else if (a > b) {
    return "a is greater";
  }
  else {
    return "b is greater";
  }
}
```

The above function can be re-written using multiple conditional operators:

```js
function findGreaterOrEqual(a, b) {
  return (a === b) ? "a and b are equal" 
    : (a > b) ? "a is greater" 
    : "b is greater";
}
```

It is considered best practice to format multiple conditional operators such that each condition is on a separate line, as shown above. Using multiple conditional operators without proper indentation may make your code hard to read.

## Use Recursion to Create a Countdown
There will be a base case. The base case tells the recursive function when it no longer needs to call itself. It is a simple case where the return value is already known. There will also be a recursive call which executes the original function with different arguments. If the function is written correctly, eventually the base case will be reached.

For example, say you want to write a recursive function that returns an array containing the numbers 1 through n. This function will need to accept an argument, n, representing the final number. Then it will need to call itself with progressively smaller values of n until it reaches 1. You could write the function as follows:

```js
function countup(n) {
  if (n < 1) {
    return [];
  } else {
    const countArray = countup(n - 1);
    countArray.push(n);
    return countArray;
  }
}
console.log(countup(5));
```

The value `[1, 2, 3, 4, 5]` will be displayed in the console.


# ES6
**ECMAScript, or ES, is a standardized version of JavaScript. Because all major browsers follow this specification, the terms ECMAScript and JavaScript are interchangeable.**

**Most of the JavaScript you've learned up to this point was in ES5 (ECMAScript 5), which was finalized in 2009. While you can still write programs in ES5, JavaScript is constantly evolving, and new features are released every year.**

**ES6, released in 2015, added many powerful new features to the language.**

## Compare Scopes of the var and let Keywords
When you declare a variable with the var keyword, it is declared globally, or locally if declared inside a function.

The let keyword behaves similarly, but with some extra features. When you declare a variable with the let keyword inside a block, statement, or expression, its scope is limited to that block, statement, or expression.

```js
var numArray = [];
for (var i = 0; i < 3; i++) {
  numArray.push(i);
}
console.log(numArray);
console.log(i);
```

Here the console will display the values `[0, 1, 2]` and 3.

With the var keyword, i is declared globally. So when i++ is executed, it updates the global variable. This code is similar to the following:

```js
var numArray = [];
var i;
for (i = 0; i < 3; i++) {
  numArray.push(i);
}
console.log(numArray);
console.log(i);
```

Here the console will display the values `[0, 1, 2]` and 3.

This behavior will cause problems if you were to create a function and store it for later use inside a for loop that uses the i variable. This is because the stored function will always refer to the value of the updated global i variable.

```js
var printNumTwo;
for (var i = 0; i < 3; i++) {
  if (i === 2) {
    printNumTwo = function() {
      return i;
    };
  }
}
console.log(printNumTwo());
```

Here the console will display the value 3.

As you can see, printNumTwo() prints 3 and not 2. This is because the value assigned to i was updated and the printNumTwo() returns the global i and not the value i had when the function was created in the for loop. The let keyword does not follow this behavior:

```js
let printNumTwo;
for (let i = 0; i < 3; i++) {
  if (i === 2) {
    printNumTwo = function() {
      return i;
    };
  }
}
console.log(printNumTwo());
console.log(i);
```

Here the console will display the value 2, and an error that i is not defined.

i is not defined because it was not declared in the global scope. It is only declared within the for loop statement. printNumTwo() returned the correct value because three different i variables with unique values (0, 1, and 2) were created by the let keyword within the loop statement.

## Mutate an Array Declared with const
The const declaration has many use cases in modern JavaScript.

Some developers prefer to assign all their variables using const by default, unless they know they will need to reassign the value. Only in that case, they use let.

However, it is important to understand that objects (including arrays and functions) assigned to a variable using const are still mutable. Using the const declaration only prevents reassignment of the variable identifier.

```js
const s = [5, 6, 7];
s = [1, 2, 3];
s[2] = 45;
console.log(s);
```

s = `[1, 2, 3]` will result in an error. After commenting out that line, the console.log will display the value `[5, 6, 45]`.

As you can see, you can mutate the object `[5, 6, 7]` itself and the variable s will still point to the altered array `[5, 6, 45]`. Like all arrays, the array elements in s are mutable, but because const was used, you cannot use the variable identifier s to point to a different array using the assignment operator.

## Prevent Object Mutation
As seen in the previous challenge, const declaration alone doesn't really protect your data from mutation. To ensure your data doesn't change, JavaScript provides a function Object.freeze to prevent data mutation.

Any attempt at changing the object will be rejected, with an error thrown if the script is running in strict mode.

```js
let obj = {
  name:"FreeCodeCamp",
  review:"Awesome"
};
Object.freeze(obj);
obj.review = "bad";
obj.newProp = "Test";
console.log(obj); 
```

The obj.review and obj.newProp assignments will result in errors, because our editor runs in strict mode by default, and the console will display the value { name: "FreeCodeCamp", review: "Awesome" }.

## Use Arrow Functions to Write Concise Anonymous Functions
In JavaScript, we often don't need to name our functions, especially when passing a function as an argument to another function. Instead, we create inline functions. We don't need to name these functions because we do not reuse them anywhere else.

To achieve this, we often use the following syntax:

```js
const myFunc = function() {
  const myVar = "value";
  return myVar;
}
```

ES6 provides us with the syntactic sugar to not have to write anonymous functions this way. Instead, you can use arrow function syntax:

```js
const myFunc = () => {
  const myVar = "value";
  return myVar;
}
```

When there is no function body, and only a return value, arrow function syntax allows you to omit the keyword return as well as the brackets surrounding the code. This helps simplify smaller functions into one-line statements:

```js
const myFunc = () => "value";
```

This code will still return the string value by default.

## Write Arrow Functions with Parameters
Just like a regular function, you can pass arguments into an arrow function.

```js
const doubler = (item) => item * 2;
doubler(4);
```

doubler(4) would return the value 8.

If an arrow function has a single parameter, the parentheses enclosing the parameter may be omitted.

```js
const doubler = item => item * 2;
```

It is possible to pass more than one argument into an arrow function.

```js
const multiplier = (item, multi) => item * multi;
multiplier(4, 2);
```

multiplier(4, 2) would return the value 8.

## Set Default Parameters for Your Functions
In order to help us create more flexible functions, ES6 introduces default parameters for functions.

```js
const greeting = (name = "Anonymous") => "Hello " + name;

console.log(greeting("John"));
console.log(greeting());
```

The console will display the strings Hello John and Hello Anonymous.

The default parameter kicks in when the argument is not specified (it is undefined). As you can see in the example above, the parameter name will receive its default value Anonymous when you do not provide a value for the parameter. You can add default values for as many parameters as you want.

## Use the Rest Parameter with Function Parameters
In order to help us create more flexible functions, ES6 introduces the rest parameter for function parameters. With the rest parameter, you can create functions that take a variable number of arguments. These arguments are stored in an array that can be accessed later from inside the function.

```js
function howMany(...args) {
  return "You have passed " + args.length + " arguments.";
}
console.log(howMany(0, 1, 2));
console.log(howMany("string", null, [1, 2, 3], { }));
```

The console would display the strings You have passed 3 arguments. and You have passed 4 arguments..

The rest parameter eliminates the need to check the args array and allows us to apply map(), filter() and reduce() on the parameters array.

## Use the Spread Operator to Evaluate Arrays In-Place
ES6 introduces the spread operator, which allows us to expand arrays and other expressions in places where multiple parameters or elements are expected.

The ES5 code below uses apply() to compute the maximum value in an array:

```js
var arr = [6, 89, 3, 45];
var maximus = Math.max.apply(null, arr);
```

maximus would have a value of 89.

We had to use Math.max.apply(null, arr) because Math.max(arr) returns NaN. Math.max() expects comma-separated arguments, but not an array. The spread operator makes this syntax much better to read and maintain.

```js
const arr = [6, 89, 3, 45];
const maximus = Math.max(...arr);
```

maximus would have a value of 89.

...arr returns an unpacked array. In other words, it spreads the array. However, the spread operator only works in-place, like in an argument to a function or in an array literal. The following code will not work:

```js
const spreaded = ...arr;
```

## Use Destructuring Assignment to Extract Values from Objects
Destructuring assignment is special syntax introduced in ES6, for neatly assigning values taken directly from an object.

Consider the following ES5 code:

```js
const user = { name: 'John Doe', age: 34 };

const name = user.name;
const age = user.age;
```

name would have a value of the string John Doe, and age would have the number 34.

Here's an equivalent assignment statement using the ES6 destructuring syntax:

```js
const { name, age } = user;
```

Again, name would have a value of the string John Doe, and age would have the number 34.

Here, the name and age variables will be created and assigned the values of their respective values from the user object. You can see how much cleaner this is.

You can extract as many or few values from the object as you want.

## Use Destructuring Assignment to Assign Variables from Objects
Destructuring allows you to assign a new variable name when extracting values. You can do this by putting the new name after a colon when assigning the value.

Using the same object from the last example:

```js
const user = { name: 'John Doe', age: 34 };
```

Here's how you can give new variable names in the assignment:

```js
const { name: userName, age: userAge } = user;
```

You may read it as "get the value of user.name and assign it to a new variable named userName" and so on. The value of userName would be the string John Doe, and the value of userAge would be the number 34.

## Use Destructuring Assignment to Assign Variables from Nested Objects
You can use the same principles from the previous two lessons to destructure values from nested objects.

Using an object similar to previous examples:

```js
const user = {
  johnDoe: { 
    age: 34,
    email: 'johnDoe@freeCodeCamp.com'
  }
};
```

Here's how to extract the values of object properties and assign them to variables with the same name:
```js
const { johnDoe: { age, email }} = user;
```

And here's how you can assign an object properties' values to variables with different names:

```js
const { johnDoe: { age: userAge, email: userEmail }} = user;
```

## Use Destructuring Assignment to Assign Variables from Arrays
ES6 makes destructuring arrays as easy as destructuring objects.

One key difference between the spread operator and array destructuring is that the spread operator unpacks all contents of an array into a comma-separated list. Consequently, you cannot pick or choose which elements you want to assign to variables.

Destructuring an array lets us do exactly that:

```js
const [a, b] = [1, 2, 3, 4, 5, 6];
console.log(a, b);
```

The console will display the values of a and b as 1, 2.

The variable a is assigned the first value of the array, and b is assigned the second value of the array. We can also access the value at any index in an array with destructuring by using commas to reach the desired index:

```js
const [a, b,,, c] = [1, 2, 3, 4, 5, 6];
console.log(a, b, c);
```

The console will display the values of a, b, and c as 1, 2, 5.

## Destructuring via rest elements
In some situations involving array destructuring, we might want to collect the rest of the elements into a separate array.

The result is similar to Array.prototype.slice(), as shown below:

```js
const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];
console.log(a, b);
console.log(arr);
```

The console would display the values 1, 2 and `[3, 4, 5, 7]`.

Variables a and b take the first and second values from the array. After that, because of the rest syntax presence, arr gets the rest of the values in the form of an array. The rest element only works correctly as the last variable in the list. As in, you cannot use the rest syntax to catch a subarray that leaves out the last element of the original array.

## Use Destructuring Assignment to Pass an Object as a Function's Parameters
In some cases, you can destructure the object in a function argument itself.

Consider the code below:

```js
const profileUpdate = (profileData) => {
  const { name, age, nationality, location } = profileData;

}
```

This effectively destructures the object sent into the function. This can also be done in-place:

```js
const profileUpdate = ({ name, age, nationality, location }) => {

}
```

When profileData is passed to the above function, the values are destructured from the function parameter for use within the function.

## Create Strings using Template Literals
A new feature of ES6 is the template literal. This is a special type of string that makes creating complex strings easier.

Template literals allow you to create multi-line strings and to use string interpolation features to create strings.

Consider the code below:

```js
const person = {
  name: "Zodiac Hasbro",
  age: 56
};

const greeting = `Hello, my name is ${person.name}!
I am ${person.age} years old.`;

console.log(greeting);
```

The console will display the strings Hello, my name is Zodiac Hasbro! and I am 56 years old..

A lot of things happened there. Firstly, the example uses backticks (\`), not quotes (' or "), to wrap the string. Secondly, notice that the string is multi-line, both in the code and the output. This saves inserting \\n within strings. The ${variable} syntax used above is a placeholder. Basically, you won't have to use concatenation with the + operator anymore. To add variables to strings, you just drop the variable in a template string and wrap it with ${ and }. Similarly, you can include other expressions in your string literal, for example ${a + b}. This new way of creating strings gives you more flexibility to create robust strings.

### Challenge
```js
const result = {
  success: ["max-length", "no-amd", "prefer-arrow-functions"],
  failure: ["no-var", "var-on-top", "linebreak"],
  skipped: ["no-extra-semi", "no-dup-keys"]
};
function makeList(arr) {
  // Only change code below this line
  const failureItems = [];
  for (let i = 0; i < arr.length; i++) {
    failureItems.push(`<li class="text-warning">${arr[i]}</li>`);
  }
  // Only change code above this line

  return failureItems;
}

const failuresList = makeList(result.failure);
```

## Write Concise Object Literal Declarations Using Object Property Shorthand
ES6 adds some nice support for easily defining object literals.

Consider the following code:

```js
const getMousePosition = (x, y) => ({
  x: x,
  y: y
});
```

getMousePosition is a simple function that returns an object containing two properties. ES6 provides the syntactic sugar to eliminate the redundancy of having to write x: x. You can simply write x once, and it will be converted to x: x (or something equivalent) under the hood. Here is the same function from above rewritten to use this new syntax:

```js
const getMousePosition = (x, y) => ({ x, y });
```

### Challenge

```js
const createPerson = (name, age, gender) => {
  return {
    name, age, gender
  };
};
```

## Write Concise Declarative Functions with ES6
When defining functions within objects in ES5, we have to use the keyword function as follows:

```js
const person = {
  name: "Taylor",
  sayHello: function() {
    return `Hello! My name is ${this.name}.`;
  }
};
```

With ES6, you can remove the function keyword and colon altogether when defining functions in objects. Here's an example of this syntax:

```js
const person = {
  name: "Taylor",
  sayHello() {
    return `Hello! My name is ${this.name}.`;
  }
};
```

### Challenge

```js
const bicycle = {
  gear: 2,
  setGear(newGear) {
    this.gear = newGear;
  }
};

bicycle.setGear(3);
console.log(bicycle.gear);
```

## Use class Syntax to Define a Constructor Function
ES6 provides a new syntax to create objects, using the class keyword.

It should be noted that the class syntax is just syntax, and not a full-fledged class-based implementation of an object-oriented paradigm, unlike in languages such as Java, Python, Ruby, etc.

In ES5, an object can be created by defining a constructor function and using the new keyword to instantiate the object.

In ES6, a class declaration has a constructor method that is invoked with the new keyword. If the constructor method is not explicitly defined, then it is implicitly defined with no arguments.

```js
// Explicit constructor
class SpaceShuttle {
  constructor(targetPlanet) {
    this.targetPlanet = targetPlanet;
  }
  takeOff() {
    console.log("To " + this.targetPlanet + "!");
  }
}

// Implicit constructor 
class Rocket {
  launch() {
    console.log("To the moon!");
  }
}

const zeus = new SpaceShuttle('Jupiter');
// prints To Jupiter! in console
zeus.takeOff();

const atlas = new Rocket();
// prints To the moon! in console
atlas.launch();
```

It should be noted that the class keyword declares a new function, to which a constructor is added. This constructor is invoked when new is called to create a new object.

**Note**: UpperCamelCase should be used by convention for ES6 class names, as in SpaceShuttle used above.

The constructor method is a special method for creating and initializing an object created with a class. 

### Challenge

```js
class Vegetable {
  constructor(name) {
    this.name = name;
  }
}

const carrot = new Vegetable('carrot');
console.log(carrot.name); // Should display 'carrot'
```

## Use getters and setters to Control Access to an Object
You can obtain values from an object and set the value of a property within an object.

These are classically called getters and setters.

Getter functions are meant to simply return (get) the value of an object's private variable to the user without the user directly accessing the private variable.

Setter functions are meant to modify (set) the value of an object's private variable based on the value passed into the setter function. This change could involve calculations, or even overwriting the previous value completely.

```js
class Book {
  constructor(author) {
    this._author = author;
  }
  // getter
  get writer() {
    return this._author;
  }
  // setter
  set writer(updatedAuthor) {
    this._author = updatedAuthor;
  }
}
const novel = new Book('anonymous');
console.log(novel.writer);
novel.writer = 'newAuthor';
console.log(novel.writer);
```

The console would display the strings anonymous and newAuthor.

Notice the syntax used to invoke the getter and setter. They do not even look like functions. Getters and setters are important because they hide internal implementation details.

**Note**: It is convention to precede the name of a private variable with an underscore (`_`). However, the practice itself does not make a variable private.

### Challenge

```js
class Thermostat {
  constructor(fahrenheit) {
    this.fahrenheit = fahrenheit;
  }
  get temperature() {
    return 5/9 * (this.fahrenheit - 32);  
  }
  set temperature(celsius) {
    this.fahrenheit = celsius * 9.0 / 5 + 32;
  }
}

const thermos = new Thermostat(76); // Setting in Fahrenheit scale
let temp = thermos.temperature; // 24.44 in Celsius
thermos.temperature = 26;
temp = thermos.temperature; // 26 in Celsius
```

## Create a Module Script
In order to make JavaScript more modular, clean, and maintainable; ES6 introduced a way to easily share code among JavaScript files. This involves exporting parts of a file for use in one or more other files, and importing the parts you need, where you need them. In order to take advantage of this functionality, you need to create a script in your HTML document with a type of module. 

```html
<script type="module" src="filename.js"></script>
```

A script that uses this module type can now use the import and export features.

## Use export to Share a Code Block
Imagine a file called math_functions.js that contains several functions related to mathematical operations. One of them is stored in a variable, add, that takes in two numbers and returns their sum. You want to use this function in several different JavaScript files. In order to share it with these other files, you first need to export it.

```js
export const add = (x, y) => {
  return x + y;
}
```

The above is a common way to export a single function, but you can achieve the same thing like this:

```js
const add = (x, y) => {
  return x + y;
}

export { add };
```

When you export a variable or function, you can import it in another file and use it without having to rewrite the code. You can export multiple things by repeating the first example for each thing you want to export, or by placing them all in the export statement of the second example, like this:

```js
export { add, subtract };
```

## Reuse JavaScript Code Using import
import allows you to choose which parts of a file or module to load. In the previous lesson, the examples exported add from the math_functions.js file. Here's how you can import it to use in another file:

```js
import { add } from './math_functions.js';
```

Here, import will find add in math_functions.js, import just that function for you to use, and ignore the rest. The ./ tells the import to look for the math_functions.js file in the same folder as the current file. The relative file path (./) and file extension (.js) are required when using import in this way.

You can import more than one item from the file by adding them in the import statement like this:

```js
import { add, subtract } from './math_functions.js';
```

## Use * to Import Everything from a File
Suppose you have a file and you wish to import all of its contents into the current file. This can be done with the import * as syntax. Here's an example where the contents of a file named math_functions.js are imported into a file in the same directory:

```js
import * as myMathModule from "./math_functions.js";
```

The above import statement will create an object called myMathModule. This is just a variable name, you can name it anything. The object will contain all of the exports from math_functions.js in it, so you can access the functions like you would any other object property. Here's how you can use the add and subtract functions that were imported:

```js
myMathModule.add(2,3);
myMathModule.subtract(5,3);
```

## Create an Export Fallback with export default
In the export lesson, you learned about the syntax referred to as a *named export*. This allowed you to make multiple functions and variables available for use in other files.

There is another export syntax you need to know, known as *export default*. Usually you will use this syntax if only one value is being exported from a file. It is also used to create a fallback value for a file or module.

Below are examples using export default:

```js
export default function add(x, y) {
  return x + y;
}

export default function(x, y) {
  return x + y;
}
```

The first is a named function, and the second is an anonymous function.

Since export default is used to declare a fallback value for a module or file, you can only have one value be a default export in each module or file. Additionally, you cannot use export default with var, let, or const.

## Import a Default Export
In the last challenge, you learned about export default and its uses. To import a default export, you need to use a different import syntax. In the following example, add is the default export of the math_functions.js file. Here is how to import it:

```js
import add from "./math_functions.js";
```

The syntax differs in one key place. The imported value, add, is not surrounded by curly braces ({}). add here is simply a variable name for whatever the default export of the math_functions.js file is. You can use any name here when importing a default.

## Create a JavaScript Promise
A promise in JavaScript is exactly what it sounds like - you use it to make a promise to do something, usually asynchronously. When the task completes, you either fulfill your promise or fail to do so. Promise is a constructor function, so you need to use the new keyword to create one. It takes a function, as its argument, with two parameters - resolve and reject. These are methods used to determine the outcome of the promise. 

```js
const myPromise = new Promise((resolve, reject) => {

});
```

## Complete a Promise with resolve and reject
A promise has three states: pending, fulfilled, and rejected. The promise you created in the last challenge is forever stuck in the pending state because you did not add a way to complete the promise. The resolve and reject parameters given to the promise argument are used to do this. resolve is used when you want your promise to succeed, and reject is used when you want it to fail. These are methods that take an argument, as seen below.

```js
const myPromise = new Promise((resolve, reject) => {
  if(condition here) {
    resolve("Promise was fulfilled");
  } else {
    reject("Promise was rejected");
  }
});
```

The example above uses strings for the argument of these functions, but it can really be anything. Often, it might be an object, that you would use data from, to put on your website or elsewhere.

## Handle a Fulfilled Promise with then
Promises are most useful when you have a process that takes an unknown amount of time in your code (i.e. something asynchronous), often a server request. When you make a server request it takes some amount of time, and after it completes you usually want to do something with the response from the server. This can be achieved by using the then method. The then method is executed immediately after your promise is fulfilled with resolve. 

```js
myPromise.then(result => {
  
});
```

result comes from the argument given to the resolve method.

## Handle a Rejected Promise with catch
catch is the method used when your promise has been rejected. It is executed immediately after a promise's reject method is called. Here’s the syntax:

```js
myPromise.catch(error => {
  
});
```

error is the argument passed in to the reject method.

### Challenge
```js
const makeServerRequest = new Promise((resolve, reject) => {
  // responseFromServer is set to false to represent an unsuccessful response from a server
  let responseFromServer = false;
    
  if(responseFromServer) {
    resolve("We got the data");
  } else {  
    reject("Data not received");
  }
});

makeServerRequest.then(result => {
  console.log(result);
});

makeServerRequest.catch(error => {
  console.log(error);
});
```


# Regular Expressions

**Regular expressions, often shortened to "regex" or "regexp", are patterns that help programmers match, search, and replace text. Regular expressions are very powerful, but can be hard to read because they use special characters to make more complex, flexible matches.**

## Using the Test Method
Regular expressions are used in programming languages to match parts of strings. You create patterns to help you do that matching.

If you want to find the word *the* in the string *The dog chased the cat*, you could use the following regular expression: /the/. Notice that quote marks are not required within the regular expression.

JavaScript has multiple ways to use regexes. One way to test a regex is using the .test() method. The .test() method takes the regex, applies it to a string (which is placed inside the parentheses), and returns true or false if your pattern finds something or not.

```js
let testStr = "freeCodeCamp";
let testRegex = /Code/;
testRegex.test(testStr);
```

The test method here returns true.

## Match Literal Strings
In the last challenge, you searched for the word *Hello* using the regular expression /Hello/. That regex searched for a literal match of the string *Hello*. Here's another example searching for a literal match of the string *Kevin*:

```js
let testStr = "Hello, my name is Kevin.";
let testRegex = /Kevin/;
testRegex.test(testStr);
```

This test call will return true.

Any other forms of *Kevin* will not match. For example, the regex /Kevin/ will not match *kevin* or *KEVIN*.

```js
let wrongRegex = /kevin/;
wrongRegex.test(testStr);
```

This test call will return false.

## Match a Literal String with Different Possibilities
Using regexes like /coding/, you can look for the pattern *coding* in another string.

This is powerful to search single strings, but it's limited to only one pattern. You can search for multiple patterns using the alternation or OR operator: |.

This operator matches patterns either before or after it. For example, if you wanted to match the strings yes or no, the regex you want is /yes|no/.

You can also search for more than just two patterns. You can do this by adding more patterns with more OR operators separating them, like /yes|no|maybe/.

```js
let petString = "James has a pet cat.";
let petRegex = /dog|cat|bird|fish/; 
let result = petRegex.test(petString);
```

## Ignore Case While Matching
Up until now, you've looked at regexes to do literal matches of strings. But sometimes, you might want to also match case differences.

Case (or sometimes letter case) is the difference between uppercase letters and lowercase letters. Examples of uppercase are A, B, and C. Examples of lowercase are a, b, and c.

You can match both cases using what is called a flag. There are other flags but here you'll focus on the flag that ignores case - the i flag. You can use it by appending it to the regex. An example of using this flag is /ignorecase/i. This regex can match the strings ignorecase, igNoreCase, and IgnoreCase.

```js
let myString = "freeCodeCamp";
let fccRegex = /freecodecamp/i; 
let result = fccRegex.test(myString);
```

## Extract Matches
So far, you have only been checking if a pattern exists or not within a string. You can also extract the actual matches you found with the .match() method.

To use the .match() method, apply the method on a string and pass in the regex inside the parentheses.

```js
"Hello, World!".match(/Hello/);
let ourStr = "Regular expressions";
let ourRegex = /expressions/;
ourStr.match(ourRegex);
```

Here the first match would return `["Hello"]` and the second would return `["expressions"]`.

Note that the .match syntax is the "opposite" of the .test method you have been using thus far:

```js
'string'.match(/regex/);
/regex/.test('string');
```

## Find More Than the First Match
So far, you have only been able to extract or search a pattern once.

```js
let testStr = "Repeat, Repeat, Repeat";
let ourRegex = /Repeat/;
testStr.match(ourRegex);
```

Here match would return `["Repeat"]`.

To search or extract a pattern more than once, you can use the global search flag: g.

```js
let repeatRegex = /Repeat/g;
testStr.match(repeatRegex);
```

And here match returns the value `["Repeat", "Repeat", "Repeat"]`.

**Note**: You can have multiple flags on your regex like /search/gi

## Match Anything with Wildcard Period
Sometimes you won't (or don't need to) know the exact characters in your patterns. Thinking of all words that match, say, a misspelling would take a long time. Luckily, you can save time using the wildcard character: .

The wildcard character . will match any one character. The wildcard is also called *dot* and *period*. You can use the wildcard character just like any other character in the regex. For example, if you wanted to match *hug*, *huh*, *hut*, and *hum*, you can use the regex /hu./ to match all four words.

```js
let humStr = "I'll hum a song";
let hugStr = "Bear hug";
let huRegex = /hu./;
huRegex.test(humStr);
huRegex.test(hugStr);
```

Both of these test calls would return true.

## Match Single Character with Multiple Possibilities
You learned how to match literal patterns (/literal/) and wildcard character (/./). Those are the extremes of regular expressions, where one finds exact matches and the other matches everything. There are options that are a balance between the two extremes.

You can search for a literal pattern with some flexibility with character classes. Character classes allow you to define a group of characters you wish to match by placing them inside square (`[` and `]`) brackets.

For example, you want to match *bag*, *big*, and *bug* but not *bog*. You can create the regex `/b[aiu]g/` to do this. The `[aiu] is the character class that will only match the characters a, i, or u.
```js
let bigStr = "big";
let bagStr = "bag";
let bugStr = "bug";
let bogStr = "bog";
let bgRegex = /b[aiu]g/;
bigStr.match(bgRegex);
bagStr.match(bgRegex);
bugStr.match(bgRegex);
bogStr.match(bgRegex);
```
In order, the four match calls would return the values `["big"]`, `["bag"]`, `["bug"]`, and null.

### Challenge
```js
let quoteSample = "Beware of bugs in the above code; I have only proved it correct, not tried it.";
let vowelRegex = /[aeiou]/gi;
let result = quoteSample.match(vowelRegex); 
```

## Match Letters of the Alphabet
You saw how you can use character sets to specify a group of characters to match, but that's a lot of typing when you need to match a large range of characters (for example, every letter in the alphabet). Fortunately, there is a built-in feature that makes this short and simple.

Inside a character set, you can define a range of characters to match using a hyphen character: -.

For example, to match lowercase letters a through e you would use `[a-e]`.

```js
let catStr = "cat";
let batStr = "bat";
let matStr = "mat";
let bgRegex = /[a-e]at/;
catStr.match(bgRegex);
batStr.match(bgRegex);
matStr.match(bgRegex);
```

In order, the three match calls would return the values `["cat"]`, `["bat"]`, and null.

## Match Numbers and Letters of the Alphabet
Using the hyphen (-) to match a range of characters is not limited to letters. It also works to match a range of numbers.

For example, `/[0-5]/` matches any number between 0 and 5, including the 0 and 5.

Also, it is possible to combine a range of letters and numbers in a single character set.

```js
let jennyStr = "Jenny8675309";
let myRegex = /[a-z0-9]/ig;
jennyStr.match(myRegex);
```

## Match Single Characters Not Specified
So far, you have created a set of characters that you want to match, but you could also create a set of characters that you do not want to match. These types of character sets are called negated character sets.

To create a negated character set, you place a caret character (^) after the opening bracket and before the characters you do not want to match.

For example, `/[^aeiou]/gi` matches all characters that are not a vowel. Note that characters like ., !, `[`, @, / and white space are matched - the negated vowel character set only excludes the vowel characters.

### Challenge
```js
let quoteSample = "3 blind mice.";
let myRegex = /[^aeiou0-9]/gi; 
let result = quoteSample.match(myRegex); 
```

### Match Characters that Occur One or More Times
Sometimes, you need to match a character (or group of characters) that appears one or more times in a row. This means it occurs at least once, and may be repeated.

You can use the + character to check if that is the case. Remember, the character or pattern has to be present consecutively. That is, the character has to repeat one after the other.

For example, /a+/g would find one match in abc and return ```["a"]```. Because of the +, it would also find a single match in aabc and return ```["aa"]```.

If it were instead checking the string abab, it would find two matches and return ```["a", "a"]``` because the a characters are not in a row - there is a b between them. Finally, since there is no a in the string bcd, it wouldn't find a match.

### Match Characters that Occur Zero or More Times
The last challenge used the plus + sign to look for characters that occur one or more times. There's also an option that matches characters that occur zero or more times.

The character to do this is the asterisk or star: \*.
```js
let soccerWord = "gooooooooal!";
let gPhrase = "gut feeling";
let oPhrase = "over the moon";
let goRegex = /go*/;
soccerWord.match(goRegex);
gPhrase.match(goRegex);
oPhrase.match(goRegex);
```
In order, the three match calls would return the values ```["goooooooo"]```, ```["g"]```, and null.

### Find Characters with Lazy Matching
In regular expressions, a greedy match finds the longest possible part of a string that fits the regex pattern and returns it as a match. The alternative is called a lazy match, which finds the smallest possible part of the string that satisfies the regex pattern.

You can apply the regex ```/t[a-z]*i/``` to the string "titanic". This regex is basically a pattern that starts with t, ends with i, and has some letters in between.

Regular expressions are by default greedy, so the match would return ```["titani"]```. It finds the largest sub-string possible to fit the pattern.

However, you can use the ? character to change it to lazy matching. "titanic" matched against the adjusted regex of ```/t[a-z]*?i/``` returns ```["ti"]```.

**Note**: Parsing HTML with regular expressions should be avoided, but pattern matching an HTML string with regular expressions is completely fine.
```js
let text = "<h1>Winter is coming</h1>";
let myRegex = /<.*?>/; 
let result = text.match(myRegex);
```
### Match Beginning String Patterns
Prior challenges showed that regular expressions can be used to look for a number of matches. They are also used to search for patterns in specific positions in strings.

In an earlier challenge, you used the caret character (^) inside a character set to create a negated character set in the form ```[^thingsThatWillNotBeMatched]```. Outside of a character set, the caret is used to search for patterns at the beginning of strings.
```js
let firstString = "Ricky is first and can be found.";
let firstRegex = /^Ricky/;
firstRegex.test(firstString);
let notFirst = "You can't find Ricky now.";
firstRegex.test(notFirst);
```
The first test call would return true, while the second would return false.

### Match Ending String Patterns
In the last challenge, you learned to use the caret character to search for patterns at the beginning of strings. There is also a way to search for patterns at the end of strings.

You can search the end of strings using the dollar sign character $ at the end of the regex.
```js
let theEnding = "This is a never ending story";
let storyRegex = /story$/;
storyRegex.test(theEnding);
let noEnding = "Sometimes a story will have to end";
storyRegex.test(noEnding);
```
The first test call would return true, while the second would return false.

### Match All Letters and Numbers
Using character classes, you were able to search for all letters of the alphabet with ```[a-z]```. This kind of character class is common enough that there is a shortcut for it, although it includes a few extra characters as well.

The closest character class in JavaScript to match the alphabet is \\w. This shortcut is equal to ```[A-Za-z0-9_]```. This character class matches upper and lowercase letters plus numbers. Note, this character class also includes the underscore character (\_).
```js
let longHand = /[A-Za-z0-9_]+/;
let shortHand = /\w+/;
let numbers = "42";
let varNames = "important_var";
longHand.test(numbers);
shortHand.test(numbers);
longHand.test(varNames);
shortHand.test(varNames);
```
All four of these test calls would return true.

These shortcut character classes are also known as *shorthand character classes*.

#### Challenge
```js
let quoteSample = "The five boxing wizards jump quickly.";
let alphabetRegexV2 = /\w/gi; 
let result = quoteSample.match(alphabetRegexV2).lenght;
```
### Match Everything But Letters and Numbers
You've learned that you can use a shortcut to match alphanumerics ```[A-Za-z0-9_]``` using ```\w```. A natural pattern you might want to search for is the opposite of alphanumerics.

You can search for the opposite of the ```\w``` with ```\W```. Note, the opposite pattern uses a capital letter. This shortcut is the same as ```[^A-Za-z0-9_]```.
```js
let shortHand = /\W/;
let numbers = "42%";
let sentence = "Coding!";
numbers.match(shortHand);
sentence.match(shortHand);
```
The first match call would return the value ```["%"]``` and the second would return ```["!"]```.

### Match All Numbers
You've learned shortcuts for common string patterns like alphanumerics. Another common pattern is looking for just digits or numbers.

The shortcut to look for digit characters is ```\d```, with a lowercase d. This is equal to the character class ```[0-9]```, which looks for a single character of any number between zero and nine.
```js
let movieName = "2001: A Space Odyssey";
let numRegex = /\d/g; 
let result = movieName.match(numRegex).length;
```
### Match All Non-Numbers
The last challenge showed how to search for digits using the shortcut ```\d``` with a lowercase d. You can also search for non-digits using a similar shortcut that uses an uppercase D instead.

The shortcut to look for non-digit characters is ```\D```. This is equal to the character class ```[^0-9]```, which looks for a single character that is not a number between zero and nine.
```js
let movieName = "2001: A Space Odyssey";
let noNumRegex = /\D/g; 
let result = movieName.match(noNumRegex).length;
```
### Restrict Possible Usernames
Usernames are used everywhere on the internet. They are what give users a unique identity on their favorite sites.

You need to check all the usernames in a database. Here are some simple rules that users have to follow when creating their username.

1. Usernames can only use alpha-numeric characters.
2. The only numbers in the username have to be at the end. There can be zero or more of them at the end. Username cannot start with the number.
3. Username letters can be lowercase and uppercase.
4. Usernames have to be at least two characters long. A two-character username can only use alphabet letters as characters.
```js
let username = "JackOfAllTrades";
let userCheck = /^[a-z][a-z]+\d*$|^[a-z]\d\d+$/i;
let result = userCheck.test(username);
```
### Match Whitespace
The challenges so far have covered matching letters of the alphabet and numbers. You can also match the whitespace or spaces between letters.

You can search for whitespace using ```\s```, which is a lowercase s. This pattern not only matches whitespace, but also carriage return, tab, form feed, and new line characters. You can think of it as similar to the character class ```[ \r\t\f\n\v]```.
```js
let whiteSpace = "Whitespace. Whitespace everywhere!"
let spaceRegex = /\s/g;
whiteSpace.match(spaceRegex);
```
This match call would return ```[" ", " "]```.

### Match Non-Whitespace Characters
You learned about searching for whitespace using ```\s```, with a lowercase s. You can also search for everything except whitespace.

Search for non-whitespace using ```\S```, which is an uppercase s. This pattern will not match whitespace, carriage return, tab, form feed, and new line characters. You can think of it being similar to the character class ```[^ \r\t\f\n\v]```.
```js
let whiteSpace = "Whitespace. Whitespace everywhere!"
let nonSpaceRegex = /\S/g;
whiteSpace.match(nonSpaceRegex).length;
```
The value returned by the .length method would be 32.

### Specify Upper and Lower Number of Matches
Recall that you use the plus sign + to look for one or more characters and the asterisk * to look for zero or more characters. These are convenient but sometimes you want to match a certain range of patterns.

You can specify the lower and upper number of patterns with quantity specifiers. Quantity specifiers are used with curly brackets ({ and }). You put two numbers between the curly brackets - for the lower and upper number of patterns.

For example, to match only the letter a appearing between 3 and 5 times in the string ah, your regex would be /a{3,5}h/.
```js
let A4 = "aaaah";
let A2 = "aah";
let multipleA = /a{3,5}h/;
multipleA.test(A4);
multipleA.test(A2);
```
The first test call would return true, while the second would return false.

#### Challenge
Change the regex ohRegex to match the entire phrase Oh no only when it has 3 to 6 letter h's.
```js
let ohStr = "Ohhh no";
let ohRegex = /Oh{3,6} no/; // Change this line
let result = ohRegex.test(ohStr);
```
### Specify Only the Lower Number of Matches
You can specify the lower and upper number of patterns with quantity specifiers using curly brackets. Sometimes you only want to specify the lower number of patterns with no upper limit.

To only specify the lower number of patterns, keep the first number followed by a comma.

For example, to match only the string hah with the letter a appearing at least 3 times, your regex would be /ha{3,}h/.
```js
let A4 = "haaaah";
let A2 = "haah";
let A100 = "h" + "a".repeat(100) + "h";
let multipleA = /ha{3,}h/;
multipleA.test(A4);
multipleA.test(A2);
multipleA.test(A100);
```
In order, the three test calls would return true, false, and true.

### Specify Exact Number of Matches
You can specify the lower and upper number of patterns with quantity specifiers using curly brackets. Sometimes you only want a specific number of matches.

To specify a certain number of patterns, just have that one number between the curly brackets.

For example, to match only the word hah with the letter a 3 times, your regex would be /ha{3}h/.
```js
let A4 = "haaaah";
let A3 = "haaah";
let A100 = "h" + "a".repeat(100) + "h";
let multipleHA = /ha{3}h/;
multipleHA.test(A4);
multipleHA.test(A3);
multipleHA.test(A100);
```
In order, the three test calls would return false, true, and false.

### Check for All or None
Sometimes the patterns you want to search for may have parts of it that may or may not exist. However, it may be important to check for them nonetheless.

You can specify the possible existence of an element with a question mark, ?. This checks for zero or one of the preceding element. You can think of this symbol as saying the previous element is optional.

For example, there are slight differences in American and British English and you can use the question mark to match both spellings.
```js
let american = "color";
let british = "colour";
let rainbowRegex= /colou?r/;
rainbowRegex.test(american);
rainbowRegex.test(british);
```
Both uses of the test method would return true.

### Positive and Negative Lookahead
Lookaheads are patterns that tell JavaScript to look-ahead in your string to check for patterns further along. This can be useful when you want to search for multiple patterns over the same string.

There are two kinds of lookaheads: positive lookahead and negative lookahead.

A positive lookahead will look to make sure the element in the search pattern is there, but won't actually match it. A positive lookahead is used as (?=...) where the ... is the required part that is not matched.

On the other hand, a negative lookahead will look to make sure the element in the search pattern is not there. A negative lookahead is used as (?!...) where the ... is the pattern that you do not want to be there. The rest of the pattern is returned if the negative lookahead part is not present.

Lookaheads are a bit confusing but some examples will help.
```js
let quit = "qu";
let noquit = "qt";
let quRegex= /q(?=u)/;
let qRegex = /q(?!u)/;
quit.match(quRegex);
noquit.match(qRegex);
```
Both of these match calls would return ```["q"]```.

A more practical use of lookaheads is to check two or more patterns in one string. Here is a (naively) simple password checker that looks for between 3 and 6 characters and at least one number:
```js
let password = "abc123";
let checkPass = /(?=\w{3,6})(?=\D*\d)/;
checkPass.test(password);
```
#### Challenge
Use lookaheads in the pwRegex to match passwords that are greater than 5 characters long, and have two consecutive digits.
```js
let sampleWord = "astronaut";
let pwRegex = /(?=\w{6,})(?=\D*\d\d)/; // Change this line
let result = pwRegex.test(sampleWord);
```
### Check For Mixed Grouping of Characters
Sometimes we want to check for groups of characters using a Regular Expression and to achieve that we use parentheses ().

If you want to find either Penguin or Pumpkin in a string, you can use the following Regular Expression: /P(engu|umpk)in/g

Then check whether the desired string groups are in the test string by using the test() method.
```js
let testStr = "Pumpkin";
let testRegex = /P(engu|umpk)in/;
testRegex.test(testStr);
```
The test method here would return true.

#### Challenge
Fix the regex so that it checks for the names of Franklin Roosevelt or Eleanor Roosevelt in a case sensitive manner and it should make concessions for middle names.
```js
let myString = "Eleanor Roosevelt";
let myRegex = /(Eleanor|Franklin) .*Roosevelt/; // Change this line
let result = myRegex.test(myString); // Change this line
```
### Reuse Patterns Using Capture Groups
Say you want to match a word that occurs multiple times like below.
```js
let repeatStr = "row row row your boat";
```
You could use /row row row/, but what if you don't know the specific word repeated? Capture groups can be used to find repeated substrings.

Capture groups are constructed by enclosing the regex pattern to be captured in parentheses. In this case, the goal is to capture a word consisting of alphanumeric characters so the capture group will be ```\w+``` enclosed by parentheses: ```/(\w+)/```.

The substring matched by the group is saved to a temporary "variable", which can be accessed within the same regex using a backslash and the number of the capture group (e.g. ```\1```). Capture groups are automatically numbered by the position of their opening parentheses (left to right), starting at 1.

The example below matches a word that occurs thrice separated by spaces:
```js
let repeatRegex = /(\w+) \1 \1/;
repeatRegex.test(repeatStr); // Returns true
repeatStr.match(repeatRegex); // Returns ["row row row", "row"]
```
Using the .match() method on a string will return an array with the matched substring, along with its captured groups.

#### Challenge
Use capture groups in reRegex to match a string that consists of only the same number repeated exactly three times separated by single spaces.
```js
let repeatNum = "42 42 42";
let reRegex = /^(\d+) \1 \1$/; // Change this line
let result = reRegex.test(repeatNum);
```
### Use Capture Groups to Search and Replace
Searching is useful. However, you can make searching even more powerful when it also changes (or replaces) the text you match.

You can search and replace text in a string using .replace() on a string. The inputs for .replace() is first the regex pattern you want to search for. The second parameter is the string to replace the match or a function to do something.
```js
let wrongText = "The sky is silver.";
let silverRegex = /silver/;
wrongText.replace(silverRegex, "blue");
```
The replace call would return the string The sky is blue..

You can also access capture groups in the replacement string with dollar signs ($).
```js
"Code Camp".replace(/(\w+)\s(\w+)/, '$2 $1');
```
The replace call would return the string Camp Code.

#### Challenge
Write a regex fixRegex using three capture groups that will search for each word in the string one two three. Then update the replaceText variable to replace one two three with the string three two one and assign the result to the result variable. 
```js
let str = "one two three";
let fixRegex = /(\w+) (\w+) (\w+)/; // Change this line
let replaceText = "$3 $2 $1"; // Change this line
let result = str.replace(fixRegex, replaceText);
```
### Remove Whitespace from Start and End
Write a regex and use the appropriate string methods to remove whitespace at the beginning and end of strings.
```js
let hello = "   Hello, World!  ";
let wsRegex = /^\s+|\s+$/g; // Change this line
let result = hello.replace(wsRegex, ""); // Change this line
```




















