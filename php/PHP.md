# PHP Variables, Strings, and Numbers
## Getting Started with PHP
### Introduction to PHP

#### History of PHP
PHP was created in 1994 and is one of the foundational technologies of modern web development.

PHP remains one of the widest used server-side technologies on the internet. It provides the underlying code for many popular content management systems (CMS) including [WordPress](https://wordpress.com/), [Drupal](https://www.drupal.org/), and [Joomla](https://www.joomla.org/). A _CMS_ allows users to create and update their own websites without having to write a lot of complex code themselves.

PHP also provides the underlying code for many e-commerce sites including [WooCommerce](https://woocommerce.com/) and [Magento](https://magento.com/). These e-commerce platforms offer a number of tools for selling products online. This way companies can focus on other aspects of their business without having to implement complex programming logic from scratch.

PHP contains built-in functionality for interacting with web data, _Vanilla PHP_, or PHP without any other tools, can be used on its own to create web application back-ends. But we don’t have to reinvent the wheel every time! Once we’re comfortable with the basics of the PHP language, we have our pick of powerful PHP frameworks to choose from! These frameworks provide scaffolding and solutions to common problems in back-end web development. Some popular PHP frameworks are [Laravel](https://laravel.com/), [CakePHP](https://cakephp.org/), and [Symfony](https://symfony.com/).

#### How is PHP used in HTML?
PHP is often used to build _dynamic web pages_. A _dynamic web page_ is one where each visitor to the website gets a customized page that can look different than how the site looks to another visitor. This is in contrast to _static web pages_ which provide the same content to each visitor.

In order to create this dynamic behavior, PHP was designed to work closely with HTML. PHP can be used directly in-line with an HTML document. When the web site is delivered from the back-end to the front-end, the PHP content is executed and added to the HTML to form one HTML document. The start of in-line PHP is denoted with `<?php` and the end is denoted with `?>`.

```php
<p>This HTML will get delivered as is</p>
<?php echo "<p>But this code is interpreted by PHP and turned into HTML</p>";?>
```

In PHP, the `echo` keyword is used to output text. The text in this case is everything between the double quotes (`"`). An instruction written in PHP is called a _statement_. A semicolon (`;`) is required at the end of each statement in PHP.

So when the code above is executed, it outputs the text into the HTML file and the front-end will receive the following HTML document:

```html
<p>This HTML will get delivered as is</p>
<p>But this code is interpreted by PHP and turned into HTML</p>
```

#### How is PHP Executed?
PHP is flexible and can also be executed from the terminal. We can use PHP as a general purpose programming language to write programs that give simple instructions to the computer without involving HTML or the web. When this is done, the output of the program is logged to the terminal. This is useful when testing functionality or for writing simple local programs.

When writing a PHP script file, we still need to denote that we are beginning our PHP code using `<?php`, but the closing tag is no longer required. It is typically left out by convention.

```php
<?php
echo "Hello, World!";
```

When the code above is run, `"Hello, World!"` will be output to the terminal.

Generally, PHP ignores whitespace (tabs, spaces, new lines), so this code yields the same result as the previous example:

```php
<?php
echo     "Hello, World!";
```

You may be surprised that this code also works:

```php
<?php
Echo "Hello, World!";
```

Unlike many other languages, PHP is not always case-sensitive, so `Echo` is a valid statement in PHP. However, it’s best practice to use standard casing – in this case, `echo`.

#### PHP Comments
Sometimes, we want to include text in our files that we don’t want the computer to execute or display to the end user. We can do this with _comments_. Comments can be used to annotate our code to make it clearer to ourselves or others. They are also useful to prevent lines of code from being executed without deleting them.

In PHP, there are two main ways to add comments to our code. The first is single line comments. These are typically used for short explanations or points of clarification. Either `#` or `//` can be used to create a single line comment. Anything on the same line after these symbols is not executed by PHP.

```php
// I will always remember this
echo "Hello world"; // My first PHP statement
```

or

```php
# I will always remember this
echo "Hello, World!"; # My first PHP statement
```

The second type of comment is a multi-line comment. This is used for longer descriptions, a more detailed guide on how to properly use the section of code, or to prevent several lines of code from being executed. These comments are started with `/*` and ended with `*/`.

```php
/* "I've never thought of PHP as more 
than a simple tool to solve problems."
- Rasmus Lerdorf */
echo "Hello, World!";
```
 
#### Todo: Learn PHP
The todo list example is frequently used when demonstrating a web framework or technology. It provides a way to exhibit how the CRUD (Create, Read, Update, Delete) behaviors are implemented using a specific technology.

Within a todo app, the functionality is typically:

- Add new items to the list (Create)
- View the existing list (Read)
- Change the completion status of each item (Update)
- Remove items from the list (Delete)

#### Review
- Despite its age, PHP is still a commonly used technology in web development.
- PHP is designed to interact with HTML to generate dynamic websites.
- Embedding PHP in HTML is done by placing PHP code between `<?php` and `?>` tags.
- Every statement in PHP must be terminated with a semicolon `;`.
- PHP files have a **.php** extension and the file always starts with the opening PHP tag `<?php`. The closing tag is implied and left out by convention.
- Whitespace is generally ignored when executing PHP code.
- Keywords are not case sensitive in PHP. As a convention, use the standard casing.
- Single line comments are made in PHP using `#` or `//`. Multi-line comments are placed between `/*` and `*/`.


## Learn PHP Variables, Strings, and Numbers
### PHP Strings and Variables

#### Strings
The PHP language has different ways of handling different types of data. Which actions the computer can perform and how the computer stores the data in memory will vary based on the type.

Strings are words or pieces of text that the computer treats as a single item. A string is a sequence of characters. It can be any length and contain any letters, numbers, symbols, or spaces surrounded by quotation marks.

```php
echo "My first string"; // Prints: My first string
```

#### Escape Sequences
In order to indicate which quotation marks the computer should view as instructions vs which it should view as simply characters, PHP allows for _escape sequences_. An escape sequence usually consists of a backslash (`\`) immediately followed by another character.

```php
echo "She said \"hi\" to the dog."; // Prints: She said "hi" to the dog.
```

Quotation marks aren’t the only symbol requiring an escape sequence. When we print multiple strings, PHP will print them to the same line by default:

```php
echo "1. Go to gym";
echo "2. Cook dinner"; 
```

The code above will output `1. Go to gym2. Cook dinner`. To print the second string on a new line, we can use the newline escape sequence (`\n`):

```php
echo "1. Go to gym";
echo "\n2. Cook dinner"; 
/* Prints
1. Go to gym
2. Cook dinner
*/
```

#### String Concatenation
It can be useful to combine two strings together. This process is called _string concatenation_, and we can use the concatenation operator (`.`) to do this.

An _operator_ is a character that performs a task in our code. The computer will take the string to the left of the concatenation operator, combine it with the string to the right, and return the resulting single string.

```php
echo "one" . "two"; // Prints: onetwo
```

#### Variables
With variables, we store values so that we can easily reuse them throughout a program.

Before we can use variables in our code, we need to declare and assign them.

_Declaring_ a variable is the process of reserving a word, the _variable name_, which we’ll be able to refer to in our code. It’s good practice to name the variable in a way that describes the data it holds.

_Assignment_ is the process of associating that variable name with a specific value so that everytime we use the variable’s name the computer will grab that value.

#### Creating Variables

```php
$my_name = "Aisle Nevertell";
```

In the code above, we’re actually doing two things with a single statement: we’re _declaring_ a new variable by giving it the name `my_name`. We’re also _assigning_ it the value `"Aisle Nevertell"`.

To declare a variable we use the dollar sign character (`$`) followed by our chosen variable name. The dollar sign is known as a _sigil_; it’s a character that allows the computer to see quickly that something is a variable.

To assign it a value we use another operator: the assignment operator (`=`) followed by the value we’re assigning to the variable.

In PHP, variables names can contain numbers, letters, and underscores (`_`), but they have to start with either a letter or an underscore. Variable names are case sensitive.

One common convention when naming PHP variables is to use an underscore between words on variable names with more than one word in their name. This is known as _snake case_:

```php
$mood = ":)";
$favorite_food = "Red curry with eggplant";
```

#### Using Variables
We refer to a variable by using the dollar sign followed by the variable’s name.

```php
$favorite_food = "Red curry with eggplant, green beans, and peanuts";
echo $favorite_food; 
// Prints: Red curry with eggplant, green beans, and peanuts
```

Since the computer treats a variable just as if it were the value it holds, this means we can do operations on variables just as we would with any value of that type.

```php
$dog_name = "Tadpole";
echo "My dog is named " . $dog_name; 
// Prints: My dog is named Tadpole
```

#### Variable Parsing
PHP strings allow us to place variables directly into double quoted strings. These variables will be _parsed_ which means the computer will read the variables as the value they hold rather than see them as just a sequence of characters.

```php
$dog_name = "Tadpole";
$favorite_food = "salmon";
$color = "brown";
 
echo "I have a $color dog named $dog_name and her favorite food is $favorite_food.";
// Prints: I have a brown dog named Tadpole and her favorite food is salmon.
```

Sometimes this can get complicated. Consider the following example:

```php
$toy = "frisbee";
echo "Alex likes playing with $toys";
```

The code above will cause an error. Why? The computer was looking for a variable `$toys` and couldn’t find one.

PHP allows us to specifically indicate the variable name by wrapping it in curly braces to avoid any confusion.

```php
$dog_name = "Tadpole";
$favorite_food = "treat";
$color = "brown";
 
echo "I have a ${color}ish dog named $dog_name and her favorite food is ${favorite_food}s.";
// Prints: I have a brownish dog named Tadpole and her favorite food is treats.
```

#### Variable Reassignment
The word variable comes from the latin variāre which means “to make changeable.” This is an apt name because the value assigned to a variable can change.

The process of assigning a new value to a variable is called _reassignment_. We reassign a variable using the assignment operator on a variable that’s already been declared:

```php
$favorite_food = "Red curry with eggplant";
echo $favorite_food; // Prints: Red curry with eggplant
 
// Reassign the value of $favorite_food to a new string
$favorite_food = "Pizza"; 
echo $favorite_food; // Prints: Pizza
```

It’s often useful to create new variables assigned to the same value as an existing variable:

```php
$first_player_rank = "Beginner";
$second_player_rank = $first_player_rank; 
```

During variable assignment or reassignment, the variable on the left of the assignment operator is treated as a variable (named storage for holding a value) while a variable on the right of the operator is treated as the value it stores.

#### Concatenating Assignment Operator
We can assign and reassign variables to the values that result from operations:

```php
$full_name = "Aisle" . " Nevertell";
echo $full_name; // Prints: Aisle Nevertell
```

During assignment, the computer will first evaluate everything to the right of the assignment operator and return a single value.

One theme you may notice as you learn a programming language’s syntax is that common actions that programmers need to do a lot often have a shortcut. Consider the following:

```php
$full_name = "Aisle";
$full_name = $full_name . " Nevertell";
echo $full_name; // Prints: Aisle Nevertell
```

Believe it or not, this is such a common task that PHP offers a shorthand notation, the concatenating assignment operator (`.=`). Let’s compare the same action but using this alternate operator:

```php
$full_name = "Aisle";
$full_name .= " Nevertell";
echo $full_name; // Prints: Aisle Nevertell
```

#### Assign by Reference
When we create a variable assigned to another variable, the computer finds a new space in memory which it associates with the left operand, and it stores a copy of the right operand’s value there.

This new variable holds a _copy_ of the value held by the original variable, but it’s an independent entity; changes made to either variable won’t affect the other:

```php
$first_player_rank = "Beginner"; 
$second_player_rank = $first_player_rank; 
echo $second_player_rank; // Prints: Beginner
 
$first_player_rank = "Intermediate"; // Reassign the value of $first_player_rank
echo $second_player_rank; // Still Prints: Beginner
```

We can also create an alias, or nickname, for a variable. Instead of a copy of the original variable’s value, we create a new name which points to the same spot in memory.

We use a different operator for this—the reference assignment operator (`=&`).

When we _assign by reference_ we’re saying that the variable on the left of the operator should point, or _refer_, to the exact same data as the variable on the right. With assignment by reference, changes made to one variable will affect the other:

```php
$first_player_rank = "Beginner";
$second_player_rank =& $first_player_rank; 
echo $second_player_rank; // Prints: Beginner
 
$first_player_rank = "Intermediate"; // Reassign the value of $first_player_rank
echo $second_player_rank; // Prints: Intermediate
```

#### Review
- Strings are collections of text that the computer treats as a single piece of data.
- A string can be any length and contain any letters, numbers, symbols, or spaces surrounded by quotation marks.
- In order to include certain characters inside strings we have to use escape sequences.
- An _operator_ is a character that performs a task in our code.
- We can use the concatenation operator (`.`) to combine two strings into one.
- Variables are a fundamental programming concept which allow us to easily reuse data in our code.
- We declare a variable using the dollar sign (`$`) followed by the variable name and then use the assignment operator (`=`) to give it a value.
- PHP has variable parsing which allows us to include variables directly in our strings.
- Once a variable has been assigned, we can change its value. This is called reassignment.
- We can create an alias for a variable, instead of just a copy, using the reference assignment operator (`=&`).
- Operations to the right of the assignment operator will be evaluated before assignment takes place.
- The concatenating assignment operator (`.=`) is a shorthand notation for reassigning a string variable to its current value appended with another string value.


### PHP Numbers

#### Numbers
PHP has two number data types. The _integer_ data type includes positive and negative whole numbers (such as 3, 4599, -98, and 0). The _floating point_ data type is used to represent decimal numbers (such as 4.98273, 2.1, -9.7, -182736.8).

```php
echo 5; // Prints: 5
echo -22.8; // Prints: -22.8
```

We can also declare variables and assign numbers as their values:

```php
$my_int = 78;
$my_float = -897.21;
 
echo $my_int; // Prints: 78
echo $my_float; // Prints: -897.21
```

#### Addition and Subtraction
PHP provides several operators we can use on numbers. Let’s start with two that are likely familiar: the addition (`+`) and subtraction (`-`) operators:

```php
echo 5 + 1; // Prints: 6
echo 6.6 + 1.2; // Prints: 7.8
echo 198263 - 263;  // Prints: 198000
echo -22.8 - 19.1; // Prints: -41.9
```

Most of the time, we don’t have to worry about which type of number we’re using. We can add a float to an integer, subtract an integer from a float, and so on.

One quirk is that operators will return integers whenever the result of the operation evaluates to a whole number. So `8.9 + 1.1` will return `10`, an integer, and not `10.0` even though both of the operands in the calculation were floating point numbers.

#### Using Number Variables
We can use number operators on variables that hold number values:

```php
$tadpole_age = 7;
$lily_age = 6; 
$age_difference = $tadpole_age - $lily_age;
echo $age_difference; // Prints 1
```

We reassign number variables using the assignment operator:

```php
$age = 82;
echo $age; // Prints: 82
 
$age = $age + 2;
echo $age; // Prints: 84
```

#### Multiplication and Division
PHP also gives us operators for performing multiplication (`*`) and division (`/`).

```php
echo 2 * 3; // Prints: 6
echo -21 / 7; // Prints: -3
```

Like with addition and subtraction, when we perform multiplication or division, the computer will return an integer whenever the operation evaluates to a whole number.

#### Exponentiation
PHP give us an operator for raising a number to the power of another number: the exponentiation operator (`**`).

```php
echo 4 ** 2; // Prints: 16
```

We can also use this operator on floats and negative numbers:

```php
echo 2.89 ** 3.2;  // Prints: 29.845104015297
echo 10 ** -1; // Prints: 0.1
```

#### Modulo
PHP also provides an operator that might be less familiar: modulo (`%`). The _modulo_ operator returns the remainder after the left operand is divided by the right operand.

```php
echo 7 % 3; // Prints: 1
```

The modulo operator will convert its operands to integers before performing the operation. This means `7.9 % 3.8` will perform the same calculation as `7 % 3`—both operations will return `1`.

#### Order of Operations
Operations will be evaluated in the following order:

1. Any operation wrapped in parentheses (`()`)
2. Exponents (`**`)
3. Multiplication (`*`) and division (`/`)
4. Addition (`+`) and subtraction (`-`).

The acronym PEMDAS can be helpful for remembering the order of precedence for these arithmetic operations.

```php
echo 1 + 3 * 9; // Prints: 28
```

#### Mathematical Assignment Operators
One common task when manipulating number variables is to reassign them to their old value with some operation performed on it.

```php
$savings = 800;
$bike_cost = 75;
$savings = $savings - $bike_cost;
echo $savings; // Prints: 725
```

This is such a common task that PHP provides a shorter syntax using arithmetic assignment operators:

**Operation:** | **Long Syntax:** | **Short Syntax:**
--- | --- | ---
Add | `$x = $x + $y` | `$x += $y`
Subtract | `$x = $x - $y` | `$x -= $y`
Multiply | `$x = $x * $y` | `$x *= $y`
Divide | `$x = $x / $y` | `$x /= $y`
Mod | `$x = $x % $y` | `$x %= $y`

We could use this shorter syntax to rewrite the above code:

```php
$savings = 800;
$bike_cost = 75;
$savings -= $bike_cost;
echo $savings; // Prints: 725
```

[Increment operators](https://www.php.net/manual/en/language.operators.increment.php) allow us to subtract or add one to a number with just two characters.

```php
$age = 89; 
$age++;
echo $age; // Prints: 90
 
$days_til_vacation = 7; 
$days_til_vacation--;
echo $days_til_vacation; // Prints: 6
```

In the code above, we used the post-increment (`++`) operator to add one to `$age` and we used the post-decrement operator (`--`) to subtract one from `$days_til_vacation`.

#### Review
- PHP has two number data types: integers and floating point numbers
- We can use arithmetic operators for performing math operations
- Operations have an order of precedence meaning that certain types of operations in a chain will be evaluated before others: first evaluated will be any operation wrapped in **p**arenthesis (`()`), next **e**xponents (`**`), then **m**ultiplication (`*`) and **d**ivision (`/`), and finally **a**ddition (`+`) and **s**ubtraction (`-`). The acronym PEMDAS can be a helpful way of remembering the order.
- We can assign number values to variables and then perform numerical operations with them.
- We can use mathematical assignment operators as a shorthand when reassigning number variables.


# PHP Functions
## Introduction to Functions in PHP
### Introduction to PHP Functions

#### Introduction
A _function_ is a set of instructions we package as a unit, often with a name, so that we can reuse it. We _define_ a function by writing out the series of steps that should happen whenever we use the function. To use the function we _call_ or _invoke_ it.

#### Defining Functions

```php
function greetLearner()
{
  echo "Hello, Learner!\n";
  echo "I hope you're enjoying PHP!\n";
  echo "Love, Codecademy";
}
```

- We used the `function` keyword to start our function definition.
- Function names must start with a letter or underscore, followed by any number of letters, numbers, or underscores.
- We created a _code block_ with curly brackets (`{ }`).

With our `greetLearner()` function defined, we’ll be able to invoke the function multiple times and print those strings without having to copy or retype the three `echo` statements again and again.

A few notes on naming conventions: we typically snake case (separate words with underscores) our variable names, but, in order to easily tell the difference between variables and functions in our code, we’ll do something different when naming functions. We’re going to use _camel case_ for our function names—we’ll start with a lowercase letter and then capitalize the first letter of every new word: `camelCase` vs. `snake_case`. Another good practice is to name functions in a way that describes what they do—typically we’ll start function names with a verb.

#### Invoking Functions
Defining a function only tells the computer to associate a name with a set of instructions. To actually execute this code we’ll need in _invoke_, or _call_, the function. Invoking a function is the process of using a function that’s been defined.

```php
function greetLearner()
{
  echo "Hello, Learner!\n";
  echo "I hope you're enjoying PHP!\n";
  echo "Love, Codecademy";
}
 
greetLearner(); 
/*
Prints:
Hello, Learner!
I hope you're enjoying PHP!
Love, Codecademy
*/
```

Below the definition of our `greetLearner` function, we invoked the function by writing its name followed by an opening and closing parenthesis (`( )`). This tells the computer to grab the instructions specified in the function definition and execute them.

#### Return Statements
In order for the data to be useful, functions have the ability to _return_ a value in addition to performing instructions.

```php
function countdown() 
{
  echo "4, 3, 2, 1, ";
  return "blastoff!";
}
```

We have a lot of options for what to do with a returned value. For example, we could capture it in a variable:

```php
$return_value = countdown(); // Prints: 4, 3, 2, 1, 
echo $return_value; // Prints: blastoff!
```

#### More on Return Statements
The `return` keyword immediately stops a function. This means that any code after a `return` won’t run.

```php
function announceRunning2()
{
  return "This is the return value of the second function.";
  echo "P.S., I love you";
}
 
$second_result = announceRunning2();
echo $second_result;
```

In this example, the string `"P.S., I love you"` will never be printed! As soon as the `return` statement is reached, the function will end.

#### Return Values
The value returned from a function is just that—a value. This means it can be used in any manner we would normally use a value of that type.

```php
function returnFive() 
{
  return 5;
}
 
echo returnFive(); // Prints: 5
```

We need to think of functions as both what they _do_ (the instructions in their code block) and what they _return_.
 
#### Returning NULL
Any function without a `return` returns a special value `NULL`. `NULL` is a special data type that stands for the absence of a value.

```php
function returnNothing() 
{
  echo "I'm running! I'm running!\n";
}
 
$result = returnNothing(); // Prints: I'm running! I'm running!
 
echo $result; // Nothing is printed
```

`NULL` can sometimes act like `0` … other times it won’t.

#### Parameters
When we define a function, we can also define parameters. A _parameter_ is a variable which serves as a placeholder throughout the function’s code block. When the function is invoked, it’s invoked with a specific value. As the computer executes the function, it replaces each occurrence of the parameter with the value that was passed in. The actual value passed in is known as an _argument_.

```php
function sayCustomHello($name)
{
echo "Hello, $name!";
};
 
sayCustomHello("Aisle Nevertell"); // Prints: Hello, Aisle Nevertell!
 
sayCustomHello("Codecademy learner"); // Prints: Hello, Codecademy Learner!
```

#### Multiple Parameters
We can also define functions with multiple parameters.

```php
function divide($num_one, $num_two)
{
  return $num_one / $num_two;
};
```

Notice that the order we pass in the arguments decides which parameters they correspond to—the first argument we pass into `divide()` will be assigned to `$num_one` and the second argument to `$num_two`.

Invoking a function with fewer arguments than expected will result in an error:

```php
function expectTwo($first, $second)
{
  return "whatever";
}
 
echo expectTwo("test"); // Will result in an error
```

#### Default Parameters
We can be more flexible about parameters when defining our functions. We want to print `"Hello, [name passed in]!"` if an argument is provided, and `"Hello, old chum!"` _only_ if no argument is passed in.

We can accomplish this by providing a default value for the `$name` parameter:

```php
function greetFriend($name = "old chum")
{
  echo "Hello, $name!";
};
 
greetFriend("Marvin"); // Prints: Hello, Marvin!
 
greetFriend(); // Prints: Hello, old chum!
```

#### Pass By Reference
When we invoke a function with a variable as its argument, it’s as if we’re assigning the value held by that variable to the function’s parameter. We assign a _copy_ of the value held by the argument variable. The variable argument and the parameter are distinct entities; changes made inside the function to the parameter will not affect the variable that was passed in:

```php
function addX ($param)
{
  $param = $param . "X";
  echo $param;
};
$word = "Hello";
addX($word); // Prints: HelloX
echo $word; // Prints: Hello
```

If we do want to make permanent changes to a variable within a function, we can prepend the parameter name with the reference sign (`&`). In this way, we assign the parameter to be an alias for the argument variable. Both will refer to the same spot in memory, and changes to the parameter within the function will permanently affect the argument variable.

```php
function addXPermanently (&$param)
{
  $param = $param . "X";
  echo $param;
};
$word = "Hello";
addXPermanently($word); // Prints: HelloX
echo $word; // Prints: HelloX
```

#### Variable Scope
Consider the following function.

```php
function calculateDaysLeft($feed_quantity, $number, $rate)
{
  $result = $feed_quantity / ($number * $rate);
  return $result;
}
echo calculateDaysLeft(300, 2, 30);
```

You can immediately see that this function depends on three pieces of information to provide an answer:

- `$feed_quantity`
- `$number`
- `$rate`

We also `echo` what is returned by the function, instead of a variable from inside the function. If we attempted to:

```php
echo $result;
```

outside of the function, it would throw an error (`Undefined variable`). This is due to variable _scope_. Each function has its own _local scope_. This means that any variables defined within the function’s code block can only be accessed within the code block itself.

However, if many functions depend on the same piece of information, it can be beneficial to have a variable that can be accessed anywhere without being passed in. To do this, we have to use the `global` keyword to tell PHP to look in the _global scope_ for the variable, instead of the local scope of the function.

```php
$feed_quantity = 300;
function calculateDaysLeft($number, $rate)
{
  global $feed_quantity;
  $result = $feed_quantity / ($number * $rate);
  return $result;
}
echo calculateDaysLeft(2, 120);
```

When using this pattern, it becomes slightly more difficult to determine what information this function depends on. Make sure to consider this trade-off when implementing your own functions.

Note that the `global` keyword is not used when invoking functions. Once a function has been defined, it can be used within the same code block or even within other function code blocks. This code will print “This works!” to the console.

```php
function first()
{
  echo "This works!\n";
}
function second()
{
  first();
}
second();
```

#### Review
- We can package a set of instructions within a named _function_ to reuse whenever we’d like.
- When we _invoke_ a function, the computer will execute the function body, specified by the code block following the parameters list.
- Functions can return a value by using the `return` keyword otherwise they return `NULL` which means no value.
- We can store the return value of a function in a variable or use it any other way we’d use a value.
- We can define functions with _parameters_ which are variables we can refer to throughout our function’s body.
- When invoking functions, the values that we give them are called _arguments_.
- Functions can have multiple parameters.
- The order in which the arguments are passed in decides which parameters they correspond to.
- You can make an argument optional by providing its corresponding parameter with a default value.
- If you prepend a parameter with the reference sign (`&`) that argument will be passed by reference.
- Variables within functions have local scope and can not be accessed from outside the function.
- Use the `global` keyword to use variables from the global scope within a function.


## PHP Built-in Functions
### Intro to Built-in PHP Functions

#### Introduction
PHP comes with a number of _built-in functions_. These functions—also known as internal functions— can be invoked without writing them ourselves.

We’ve been using `echo` to print information to the console. [`echo` is NOT a function](https://www.php.net/manual/en/function.echo.php) (it’s a “language construct”). But, one little PHP quirk is that we can use it in a way that looks a lot like invoking a function—we can wrap an argument for `echo` in parentheses.

`echo` can also be used to print multiple string arguments, but unlike a function, for this feature to work we must NOT wrap them in parentheses.

```php
echo("This works!\n");

echo "This also works!\n";

//echo("This would NOT work", "\n");

echo "Buuuut!", " ", "This", " ", "does!", "\n";
```

#### Working with Variables
PHP includes useful built-in functions for getting information about variables. [The `gettype()` function](https://www.php.net/manual/en/function.gettype.php) takes a variable as its argument and returns a string value representing the data type of the argument.

```php
$name = "Aisle Nevertell";
$age = 1000000;
 
echo gettype($name); // Prints: string
 
echo gettype($age); // Prints: integer
```

Since the function is included within the language itself, we can just call it anywhere within our PHP code.

 [The `var_dump()` function](https://www.php.net/manual/en/function.var-dump.php) also takes a variable argument. It prints details about the argument it receives.

```php
var_dump($name); // Prints: string(15) "Aisle Nevertell"
 
var_dump($age); // Prints: int(1000000)
```

#### String Functions
The [`strrev()` function](https://www.php.net/manual/en/function.strrev.php) takes in a string as its argument and returns a string with all of the characters of the original string in reverse order.

```php
echo strrev("Hello, World!"); // Prints: !dlroW ,olleH
```

PHP also comes with built-in functions to change the capitalization of a string. We can use the [`strtolower()` function](https://www.php.net/manual/en/function.strtolower.php) to transform an argument string into all lowercase letters:

```php
echo strtolower("HeLLo"); // Prints: hello
```

Built-in functions often have multiple parameters. The [`str_repeat()` function](https://www.php.net/manual/en/function.str-repeat.php) takes a string as its first argument and a number as its second. It returns a string containing the argument string repeated the argument number of times.

```php
echo str_repeat("hi", 10); // Prints: hihihihihihihihihihi 
```

#### Working with Substrings
A _substring_ is a portion of a string. For example, `"hello"` is a substring of the string `"Oh hello, how are you?"` and `"el"` is a substring of the string `"hello"`.

The [`substr_count()` function](https://www.php.net/manual/en/function.substr-count.php) returns the number of instances of a substring within a string. It takes two arguments, the string to search _through_—[sometimes called the _haystack_](https://en.wikipedia.org/wiki/Needle_in_a_haystack)— and the string to search _for_—sometimes called the _needle_.

```php
$story = "I was like, \"Dude, like just tell me what you like think because like everyone else is like being totally honest, and like I just want to know what you like think.\" So like I don't know...";
 
echo substr_count($story, "like"); // Prints: 8
```

#### Number Functions
The [`abs()` function](https://www.php.net/manual/en/function.abs.php) returns the absolute value of its number argument:

```php
echo abs(-10.99); // Prints: 10.99
 
echo abs(127); // Prints: 127
```

Another useful function is the [`round()` function](https://www.php.net/manual/en/function.round.php) which returns the nearest integer to its number argument:

```php
echo round(1.2); // Prints: 1
 
echo round(1.5); // Prints: 2
 
echo round(1298736.821763876); // Prints: 1298737
```

#### Generating Random Numbers
The `rand()` function returns a random integer. We have some flexibility with how we invoke it. Invoking `rand()` with no arguments will return a number between 0 and the largest number our current environment will allow; this is a quirk of PHP. We can find out what this number is by invoking a different built-in function, `getrandmax()`:

```php
$max = getrandmax(); 
 
echo $max;
 
echo rand(); // Prints a number between 0 and $max
```

If we’d like more control over the random number we generate, we can invoke the `rand()` function with two integer arguments representing the smallest allowable random number and the largest allowable random number. Fun fact: the second argument provided can be larger than `getrandmax()`. These numbers are _inclusive_ meaning the arguments we pass in could be generated by the function.

```php
echo rand(1, 2); // Prints either 1 or 2
 
echo rand(5, 10); // Prints a number between 5 and 10 (inclusive!)
 
echo rand(1, 100); // Prints a number between 1 and 100 (inclusive!)
```

#### Documentation
Documentation typically includes:

- The name of the function.
- The versions of the PHP language the function is available in.
- An overview of how the function works.
- Additional details on the parameters and return value.
- Examples of the function in use.
- User comments further explaining features of the function.

Here’s the description for the `abs()` function:

**`abs ( mixed $number ) : number`**

Here we see the function name followed by parentheses. The parentheses contain information about the function’s parameter(s)—first the parameter’s type followed by its name. The parameter for `abs()` has the type `mixed` because there are multiple data types the function will accept (an integer or a float). The parameter for `abs()` is named `$number`. After the parentheses is a colon (`:`) followed by `number`; this is the data type the function will return.

A function that prints something but doesn’t return a value will have `:void` instead of a return type. Similarly, a function that doesn’t accept parameters will have `void` within its parentheses.

Here’s the description for the `substr_count()` function:

**`substr_count ( string $haystack , string $needle [, int $offset = 0 [, int $length ]] ) : int`**

Earlier in this lesson, we invoked `substr_count()` with only the two string parameters (`$haystack` and `$needle`). But functions can have optional parameters. This means they’ll work with or without them. These parameters are wrapped in square brackets (`[ ]`) in the function’s description. An optional parameter may have a _default value_, this is the value that will be used if no argument is passed into the function. The default value is indicated with an equal sign (`=`).

The `substr_count()` function accepts two additional integer arguments—`$offset` and `$length`. `$offset` has a default value of `0`.

Let’s look at this description in more detail:

**`str_pad ( string $input , int $pad_length [, string $pad_string = " " [, int $pad_type = STR_PAD_RIGHT ]] ) : string`**

The `: string` tells us that the `str_pad()` returns a string.

`str_pad()` has four paramteters: two required and two optional. The first is a string they call `$input`. This is our original string. The function will add “padding” to this string. 

The second parameter is an integer they call `$pad_length`. This is the length we’d like the final string to be once it has been padded.

The third parameter is a string they call `$pad_string`. This parameter has a default value of `" "`. The `str_pad()` function will add the `$pad_string` to the `$input` string until it’s the correct length (`$pad_length`). If no argument is passed in, the function will pad with space characters.

The final parameter is an integer they call `$pad_type`. This parameter dictates the way the string is padded: only on the left, only on the right, or on both sides. This is a bit of a strange one. The parameter’s type is an integer, but the default value for `$pad_type` is a [predefined constant](https://www.php.net/manual/en/string.constants.php)—`STR_PAD_RIGHT`. The parameter must be the values `0`, `1`, or `2`. `0` means only pad to the left, `1` means only pad to the right, and `2` means pad on both sides. To save us from having to remember which was which and prevent people from using invalid numbers, PHP comes with predefined constants `STR_PAD_LEFT`, `STR_PAD_RIGHT`, and `STR_PAD_BOTH` equal to 0, 1, and 2, respectively. These constants are available from anywhere.

```php
$a = 29;
$b = "You did it!";
$c = STR_PAD_BOTH;
$d = "*~*";

// Write your code below:
echo str_pad($b, $a, $d, $c); // *~**~**~*You did it!*~**~**~*
```

#### Finding Functions
In order to find out about built-in functions (and other language features), you’ll want to get comfortable exploring the [PHP documentation](https://www.php.net/manual/en/langref.php). The docs can get a little overwhelming—for example, [this seemingly infinite index of PHP functions](https://www.php.net/manual/en/indexes.functions.php) is pretty unwieldy.

The documentation contains some lists organized by topic: this is a list of [PHP string functions](https://www.php.net/manual/en/ref.strings.php) and this is a [list of math functions](https://www.php.net/manual/en/ref.math.php).

##### strtoupper()
In PHP, you can convert a string to all capital letters using the `strtoupper()` function. This function returns a string with all alphabetic characters converted to uppercase.

```php
$myString = "hello world";
$uppercaseString = strtoupper($myString);
echo $uppercaseString; // outputs "HELLO WORLD"
```

##### ceil()
In PHP, you can round up a number using the `ceil()` function. This function returns the smallest integer greater than or equal to a given number.

```php
$myNumber = 3.14159;
$roundedNumber = ceil($myNumber);
echo $roundedNumber; // outputs 4
```

##### pi()
In PHP, you can get the value of pi (π) using the `pi()` function. This function returns the mathematical constant pi with a precision of 14 decimal places.

```php
$pi = pi();
echo $pi; // outputs 3.1415926535898
```

##### octdec()
In PHP, you can convert an octal string to a decimal number using the `octdec()` function. This function takes an octal string as its argument and returns the equivalent decimal number.

```php
$octalString = "42";
$decimalNumber = octdec($octalString);
echo $decimalNumber; // outputs 34
```

##### deg2rad()
In PHP, you can convert from degrees to radians using the `deg2rad()` function. This function takes a value in degrees as its argument and returns the equivalent value in radians.

```php
$degrees = 45;
$radians = deg2rad($degrees);
echo $radians; // outputs 0.78539816339745
```

##### cos()
In PHP, you can get the cosine of an angle using the `cos()` function. This function takes a value in radians as its argument and returns the cosine of that angle.

```php
$angle = pi() / 4; // angle of 45 degrees in radians
$cosine = cos($angle);
echo $cosine; // outputs approximately 0.70710678118655
```

It's important to note that the `cos()` function expects its argument to be in radians, not degrees. If you need to calculate the cosine of an angle in degrees, you should first convert the angle to radians using the `deg2rad()` function.

##### round()
In PHP, you can round a number using the `round()` function. This function takes a number as its first argument and an optional precision as its second argument, and returns the rounded value.

```php
$num = 3.14159;
$rounded = round($num, 2); // round to 2 decimal places
echo $rounded; // outputs 3.14
```

##### log()
In PHP, you can get the natural logarithm (base e) of a number using the `log()` function without specifying a base or using the `log()` function specifying a base of `M_E`.

```php
$num = 2.71828;
$ln = log($num);
echo $ln; // outputs 1
```

Alternatively, you can use the `log()` function specifying a base of `M_E`, which is equivalent to the natural logarithm:

```php
$num = 2.71828;
$ln = log($num, M_E);
echo $ln; // outputs 1
```

##### acos()
In PHP, you can get the arc cosine (inverse cosine) of a number using the `acos()` function. This function takes a number as its argument and returns the arc cosine of that number in radians.

```php
$num = 0.5;
$arc_cosine = acos($num);
echo $arc_cosine; // outputs approximately 1.0471975511966
```

It's important to note that the `acos()` function returns the result in radians. If you need the result in degrees, you should first convert the radians to degrees using the `rad2deg()` function.

##### rad2deg()
In PHP, you can convert from radians to degrees using the `rad2deg()` function. This function takes a number in radians as its argument and returns the equivalent value in degrees.

```php
$angle_in_radians = 1.5708;
$angle_in_degrees = rad2deg($angle_in_radians);
echo $angle_in_degrees; // outputs 90
```

##### floor()
In PHP, you can round down (floor) a number to the nearest integer using the `floor()` function. This function takes a number as its argument and returns the largest integer that is less than or equal to the number. 

```php
$num = 3.14;
$floored_num = floor($num);
echo $floored_num; // outputs 3
```


# PHP Conditionals and Logic
## Booleans and Comparison Operators in PHP
### Booleans and Comparison Operators

#### If Statements
An if statement follows this basic structure:

```php
if (/*some condition*/) { 
// Do something...
}
```

The parentheses hold the condition we want the computer to check. **If** the condition is true, the code inside the code block (`{ }`) will run; if it’s not true, the code will not run.

The foundation of any conditional is the _boolean_ data type. A boolean can have one of two values: `TRUE` or `FALSE`. Note that these are the words without quotation marks—the string `"TRUE"` is not the same as the boolean value `TRUE`. These values are not case sensitive, but we follow the convention of making them uppercase.

```php
$is_clicked = TRUE;
if ($is_clicked) {
  $link_color = "purple";
  echo $link_color;
}
```

We can include a block of code to run when the condition is not met with the keyword `else`:

```php
$is_clicked = FALSE;
if ($is_clicked) {
  $link_color = "purple";
  echo $link_color;
} else {
  $link_color = "blue";
  echo $link_color;
}
```

#### Comparison Operators
The condition, or _expression_, in an `if` statement can hold a boolean value—like `TRUE` or `FALSE`, a variable assigned to one of those values, or an expression that evaluates to `TRUE` or `FALSE`.

_Comparison operators_ evaluate a relationship between two operands and return a boolean value.

The less than operator (`<`) will return `TRUE` if the left operand is less than the right operand and `FALSE` if it’s not:

```php
1 < 10; // Evaluates to: TRUE
11 < 3; // Evaluates to: FALSE
```

The less than or equal to operator (`<=`) will return `TRUE` if the left operand is less than **or** equal to the right operand and `FALSE` if it’s not:

```php
1 <= 10; // Evaluates to: TRUE
4 <= 4; // Evaluates to: TRUE
18 <= 2; // Evaluates to: FALSE
```

The greater than operator (`>`) will return `TRUE` if the left operand is greater than the right operand and `FALSE` if it’s not. And the greater than or equal to operator (`>=`) will return `TRUE` if the left operand is greater than **or** equal to the right operand and `FALSE` if it’s not:

```php
1 > 10; // Evaluates to: FALSE
11 > 3; // Evaluates to: TRUE
1 >= 10; // Evaluates to: FALSE
11 >= 11; // Evaluates to: TRUE
54 >= 10; // Evaluates to: TRUE
```

#### Identical and Not Identical Operators
The identical operator (`===`) will return `TRUE` if the left operand is the same as the right operand and `FALSE` if it’s not:

```php
$num = 5;
$num === 5; // Evaluates to: TRUE
10 === 10; // Evaluates to: TRUE
$num === 20; // Evaluates to: FALSE
```

When we think about comparing two values, we’ll need to think like a computer. Are `"hello"` and `"Hello"` the same?

```php
$greeting = "hello";
$greeting === "hello"; // Evaluates to: TRUE
"hello" === "hel" . "lo";   // Evaluates to: TRUE
$greeting === "HELLO"; // Evaluates to: FALSE
```

The not identical operator (`!==`) will return `TRUE` if the two operators are different and `FALSE` if they’re the same:

```php
$num = 5;
$num !== 5; // Evaluates to: FALSE
10 !== 10; // Evaluates to: FALSE
$num !== 20; // Evaluates to: TRUE
 
$greeting = "hello";
"hello" !== "hello"; // Evaluates to: FALSE
$greeting !== "HELLO"; // Evaluates to: TRUE
```

When looking through PHP code, you may encounter another operator—the equal operator (`==`). Like the identical operator, the equal operator will return `TRUE` if the left operand is the same as the right operand and `FALSE` if it’s not. But the equal operator is less strict than the identical operator and can have some hard to predict results, so we prefer to only use the identical operator.

#### Elseif Statements
We can write conditionals with multiple `if` statements using the `elseif` construction. The computer will continue through each condition until it finds a condition which is met or gets to the end—whichever comes first.

```php
$grade = 88;
if ($grade < 60) {
  echo "You got an F";
} elseif ($grade < 70) {
  echo "You got a D";
} elseif ($grade < 80) {
  echo "You got a C";
} elseif ($grade < 90) {
  echo "You got a B";
} else {
  echo "You got an A";
}
```

Notice that the order of our conditionals is important. The grade `55` would satisfy the condition `$grade < 90`, but it meets the condition intended for it, `$grade < 60` first.

Note: you may encounter [the keywords `else if`](https://www.php.net/manual/en/control-structures.elseif.php) with a space separating the two words. In many situations, `else if` will work the same way as `elseif`. Since `elseif` works more universally, that’s what we choose to use.

#### Switch Statement
We often want to compare a value, expression, or variable against many different possible values and run different code depending on which it matches. We can use a series of `if`/`elseif` statements which use the identical operator (`===`) or we can use a `switch` statement—an alternate syntax.

```php
switch ($letter_grade){
  case "A":
    echo "Terrific";
    break;
  case "B":
    echo "Good";
    break;
  case "C":
    echo "Fair";
    break;
  case "D":
    echo "Needs Improvement";
    break;
  case "F":
    echo "See me!";
    break;
  default:
    echo "Invalid grade"; 
}
```

After each `case`, we include the keyword `break` to _break_ out of the `switch` statement. We can provide a `default` that should run if none of the provided cases match.

A `switch` statement is a good example of code that might be preferable _not_ because it’s shorter, but rather because it clearly indicates the purpose of the code.

#### Switch Statements: Fall through
Without the keyword `break`, not only will the first matching case’s block run, but so will all the code in the subsequent cases! This is known as _fall through_. The keyword `break` tells the computer to **break** out of the switch statement, without it, it will **fall through** the rest of the `switch` executing all the code until it reaches a `break`, a `return`, or the end of the statement:

```php
$letter = "a";
switch ($letter) {
  case "a":
    echo "a";
  case "b":
    echo "b";
  case "c":
    echo "c";
  case "d":
    echo "d";
}
```

The code above will output `abcd`.

Fall through may seem like a drag, but it can be useful when we want multiple cases to execute the same code:

```php
switch ($day_of_week) {
  case "Monday":
  case "Tuesday":
    echo "Just getting started!";
    break;
  case "Wednesday":
    echo "Humpday!";
    break;
  case "Thursday":
  case "Friday":
    echo "Almost the weekend!";
    break;
  case "Saturday":
  case "Sunday":
    echo "Enjoy!";
    break;
}
```

#### Ternary Operator
PHP offers a short-hand syntax to conditionally `return` a value.

A ternary operator (`?:`) is another conditional operator. It takes three operands and returns a value:

- The first operand is a condition to check. This is followed by a question mark `?`.
- The second operand is an expression to `return` if the condition is `TRUE`. This is followed by a colon (`:`).
- The third operand is an expression to `return` if the condition is `FALSE`.

```php
$isClicked = FALSE;
$link_color = $isClicked ? "purple" : "blue";
```

Note that code in the expression will be executed, but the intended use of the ternary is to conditionally return a value _not_ to execute code.

#### Truthy and Falsy
In practice, **any** value or expression in the condition will be **converted** to `TRUE` or `FALSE`.

```php
if ("What's going on?"){
  echo "Let us explain…";
} 
// Prints: Let us explain…
```

In the above code, the condition checks the _truthiness_ of the string `"What's going on?"`. The computer converts this value to `TRUE` and therefore executes the code in the block. We sometimes refer to code that will be converted to `TRUE` as _truthy_ and code that will be converted to `FALSE` as _falsy_ since they aren’t actually equivalent to those boolean values, but they will be treated as such in certain contexts. Most values and expressions are treated as truthy, so we’ll focus on those that are falsy:

- Empty strings
- `null`
- an undefined or undeclared variable
- an empty array
- the number `0`
- the string `"0"`

#### User Input: readline()
The [built-in `readline()` function](https://www.php.net/manual/en/function.readline.php) takes a string with which to prompt the user. It waits for the user to enter text into the terminal and returns that value as a string.

```php
echo "Hi, I'm Aisle Nevertell. What's your name?\n";
$name = readline(">> ");
echo "\nNice to meet you, $name";
```

By incorporating in conditionals, we can take different actions depending on the user input:

```php
echo "\nWhat's your favorite color?\n";
$color = readline(">> ");
if ($color === "green"){
  echo "\nCool, that's my favorite too!";
} else {
  echo "\nOh, $color is nice, I guess…";
}
```

To run your program you’ll need to enter `php src/index.php` in the terminal.

#### Review
- Conditionals make it possible for programs to decide how to react to a wide variety of situations.
- `if` statements allow us to run a block of code **if** a condition is met.
- The boolean data type is either the value `TRUE` or `FALSE` and is the foundation of programmatic decision making.
- We use `else` to include a block of code to run when the condition is not met.
- Comparison operators evaluate a relationship between two operands and return a boolean value.
    - The less than operator (`<`)
    - The less than or equal to operator (`<=`)
    - The greater than operator (`>`)
    - The greater than or equal to operator (`>=`)
    - The Identical operator (`===`)
    - The not identical operator `(!==)`
- We can write conditionals with multiple `if` statements using the `elseif` construction.
- Instead of using a series of `if` statements when we want to compare a value, expression, or variable against many different possible values and run different code depending on which it matches, we can use a `switch` statement.
- The keyword `break` tells the computer to break out of the switch statement, without it, it will _fall through_ the rest of the switch executing all the code until it reaches a `break` or the end of the statement.
- A ternary operator (`?:`) is shorthand conditional operator. It takes three operands (a condition to check, an expression to return if the condition is `TRUE`, and an expression to return if the condition is `FALSE`).
- Any value or expression inside a condition will be converted to `TRUE` or `FALSE`. We consider values that will convert to `TRUE` to be _truthy_ and values that will convert to `FALSE` to be _falsy_.
- We can get user input from the terminal with the `readline()` function.


## Logical Operators and Compound Conditions in PHP
### Logical Operators and Compound Conditions

#### Nested Conditional Statements

```php
  $is_elevator_here = true;
  $elevator_direction = "down";
  $my_direction = "up";
  $is_button_pushed = false;
 
  if ($is_elevator_here){
      if ($elevator_direction === $my_direction){
        echo "I'm in the elevator.";
      } else {
          if ($is_button_pushed){
            echo "I'm waiting...!";
          } else {
              echo "I'm pushing the button.";
          }
     }
  } else {
      if ($is_button_pushed){
          echo "I'm waiting...";
      } else {
          echo "I'm pushing the button.";
      }
   }
```

Notice that in order to implement this decision-making process with code, we _nested_ conditionals inside each other.

#### The || Operator
Expressions that use _logical operators_ evaluate to boolean values.

The logical operator `||` takes two different boolean values or expressions as its operands and returns a single boolean value. It returns `TRUE` if **either** its left operand **or** its right operand evaluate to `TRUE`. We can use `||` in situations where more than one condition should lead to the same outcome.
 
```php
TRUE || TRUE;   // Evaluates to: TRUE
 
FALSE || TRUE;  // Evaluates to: TRUE
 
TRUE || FALSE;  // Evaluates to: TRUE
 
FALSE || FALSE; // Evaluates to: FALSE
```

Let’s think about an example we might encounter in web development: when requesting a password change for a web application, the password can only be changed by either the user themselves or an administrator.

```php
$is_admin = FALSE;
$is_user = TRUE;
if ($is_admin || $is_user){
  echo "You can change the password";
}
```

The `||` operator is inclusive—it evaluates to `TRUE` if **either** or **both** of the operands are `TRUE`.

#### The && Operator
Often, we’ll encounter situations where we have more than one condition we need satisfied in order to take an action.

The logical `&&` operator returns `TRUE` only if **both** of its operands evaluate to `TRUE`. It returns `FALSE` if either or both of its operands evaluate to false.

```php
TRUE && TRUE;    // Evaluates to: TRUE
FALSE && TRUE;   // Evaluates to: FALSE
TRUE && FALSE;   // Evaluates to: FALSE
FALSE && FALSE;  // Evaluates to: FALSE
```

Let’s think about a real-world example: when attempting to withdraw money from an ATM, the account holder must **both** provide the correct PIN **and** have enough money in their account.

```php
$correct_pin = TRUE;
$sufficient_funds = TRUE;
if ($correct_pin && $sufficient_funds){
  echo "You can make the withdrawal.";
}
```

The `&&` operator has a higher [operator precedence](https://www.php.net/manual/en/language.operators.precedence.php) than the `||` operator. This means that in a complex statement that includes both operators, the computer will evaluate the part of the expression with `&&` first:

```php
TRUE || TRUE && FALSE // Evaluates to: TRUE
```

If we want to control the order in which the expression is evaluated, we can use parentheses for force the order:

```php
(TRUE || TRUE) && FALSE // Evaluates to: FALSE
```

#### The Not Operator
The logical not operator (`!`) takes only a right operand. It reverses the boolean value of its operand.

```php
!TRUE;    // Evaluates to: FALSE
!FALSE;   // Evaluates to: TRUE
```

The not operator has very high operator precedence; be sure to use parentheses so that code evaluation happens as intended:

```php
!10 < 11; // Evaluates to: TRUE
!(10 < 11);  // Evaluates to: FALSE
!TRUE || TRUE; // Evaluates to: TRUE
!(TRUE || TRUE); // Evaluates to: FALSE
```

The not operator is useful when we only want to take a course of action if a condition is not true. For example, if a user is **not** logged in, a web application may show a pop-up telling them they must do so to continue.

```php
$is_logged_in = FALSE; 
if (!$is_logged_in){
  echo "You must log in to continue.";
}
```

#### The Xor Operator
The logical operator `xor` stands for _exclusive or_. It takes two different boolean values or expressions as its operands and returns a single boolean value. Unlike regular `or` which evaluates to `TRUE` if **either** its left operand **or** its right operand evaluates to `TRUE`, `xor` evaluates to `TRUE` only if either its left operand **or** its right operand evaluates to `TRUE`, but **not both**.

```php
TRUE xor TRUE;   // Evaluates to: FALSE
 
FALSE xor TRUE;  // Evaluates to: TRUE
 
TRUE xor FALSE;  // Evaluates to: TRUE
 
FALSE xor FALSE; // Evaluates to: FALSE
```

We can use `xor` to answer either/or questions.

```php
$is_wearing_glasses = TRUE;
$is_wearing_contacts = TRUE;
 
if ($is_wearing_glasses xor $is_wearing_contacts){
  echo "Your vision is corrected!";
} else {
  echo "Your vision is impaired.";
}
```

#### Alternate Syntax
An alternate syntax for logical `||` operator is the `or` operator, and an alternate syntax for logical `&&` operator is the `and` operator. These operators have the advantage of making our code more human readable.

```php
// The or Operator:
TRUE or TRUE;   // Evaluates to: TRUE
FALSE or TRUE;  // Evaluates to: TRUE
TRUE or FALSE;  // Evaluates to: TRUE
FALSE or FALSE; // Evaluates to: FALSE
 
// The and Operator:
TRUE and TRUE;   // Evaluates to: TRUE
FALSE and TRUE;  // Evaluates to: FALSE
TRUE and FALSE;  // Evaluates to: FALSE
FALSE and FALSE; // Evaluates to: FALSE
```

The computer treats these operators slightly differently from the symbol operators due to [operator precedence](https://www.php.net/manual/en/language.operators.precedence.php). The `or` and `and` logical operators have a lower precedence than `||` and `&&`.

```php
TRUE || TRUE && FALSE // Evaluates to: TRUE
TRUE || TRUE and FALSE // Evaluates to: FALSE
```

#### Multi-File Programs: include
Another way to improve our code and separate concerns is with _modularity_, separating a program into distinct, manageable chunks where each provides a piece of the overall functionality. Instead of having an entire program located in a single file, code is organized into separate files. Each file is then **included** in our main program with the keyword `include`. An `include` statement will bring the code from a file into the current file and also run the code. It’s as if all the code from that file was written right there. We provide the path to the file to be included as a string.

For example, let’s say we had three files **one.php**, **two.php**, and **index.php**, and we want to include the code from files **one.php** and **two.php** inside **index.php**:

```php
// one.php  
echo "How are";
```

```php
// two.php
echo " you?";
```

```php
// index.php
echo "Hello! ";
include "one.php";
include "two.php";
// Prints: Hello! How are you?
```

#### Review
- By nesting conditionals within one another, we can create branching decisions.
- The logical operator `||` takes two different boolean values or expressions as its operands and returns a single boolean value. It returns `TRUE` if either its left operand or its right operand evaluate to `TRUE`.
- The logical `&&` operator returns `TRUE` only if both of its operands evaluate to `TRUE`. It returns `FALSE` if either or both of its operands evaluate to `FALSE`.
- The logical not operator (`!`) takes only a right operand. It reverses the boolean value of its operand.
- The logical exclusive or operator (`xor`) returns `TRUE` only if either its left operand or its right operand evaluate to `TRUE`, but **not both** or **neither**.
- PHP includes alternate syntax for the `||` and `&&` operators: we can use `or` in place of `||`, and we can use `and` in place of `&&`. These operators work much the same way but have different [operator precedence](https://www.php.net/manual/en/language.operators.precedence.php).
- We can **include** code from one file inside another with `include` which allows us to write mode _modular_ programs.


### Common Mistakes with Conditionals

#### Mistake 1: Not treating expressions as distinct
Let’s say we want to print something if our variable `$num` is equal to `1` or `2` or `3`. Why doesn’t the following code work?

```php
$number = 5;
if ($number === 1 || 2 || 3)
{
  echo "Your number is 1, 2, or 3";
} else {
  echo "Your number is NOT 1, 2, or 3";
}
```

The code above prints `"Your number is 1, 2, or 3"` even though our number is `5`… In a compound condition, each expression is treated separately. Since `2` and `3` are _truthy_ values, the condition above is the equivalent of `FALSE || TRUE || TRUE` which evaluates to `TRUE`. Here’s one way we could rewrite the broken code:

```php
$number = 5;
if ($number === 1 || $number === 2 || $number === 3)
{
  echo "Your number is 1, 2, or 3";
} else {
  echo "Your number is NOT 1, 2, or 3";
}
```

#### Mistake 2: Omitting Parentheses
Recall that we can avoid any risk by using parentheses to force expressions to evaluate in the order we intend:

```php
(TRUE || FALSE) && FALSE; // Evaluates to: FALSE
(TRUE || FALSE) and FALSE; // Evaluates to: FALSE
 
$my_bool = (TRUE and FALSE); // $my_bool is FALSE
```

#### Mistake 3: Not thinking like a computer
One of the most difficult things about learning to code, is learning to think the way a computer “thinks”. It’s important to look at expressions like a computer would. Consider the following code to prompt a user if they enter an invalid response:

```php
if ($response !== "yes" || $response !== "no"){
  echo "You must type either yes or no";
}
```

In the code above, we intended to catch situations where the user either didn’t enter `"yes"` or `"no"`. We wrote the code the way we might say it, “If the response isn’t yes or no…” But the expression `$response !== "yes" || $response !== "no"` will always evaluate to `TRUE` even when the `$response` was actually `"yes"` or `"no"`! If the `$response` was `"no"`, for example, the expression will evaluate as `TRUE || FALSE` which evaluates to `TRUE`.

We can fix this broken code by replacing the `||` operator with the `&&` operator:

```php
if ($response !== "yes" && $response !== "no"){
  echo "You must type either yes or no";
}
```

When our code isn’t working the way we expect, we should walk through it like a computer—we should “be” the computer and try to read each line without our natural human bias.
 

# PHP Arrays and Loops
## PHP Arrays
### Ordered Arrays

#### Introduction
To help us store and manipulate related elements of data together, programming languages employ _data structures_.

One type of data structure fundamental to computer science is an _array_, a list of ordered, stored data. In PHP, we refer to this data structure as an _ordered array_.

The location of an element in an array is known as its _index_. The elements in an ordered array are arranged in ascending numerical order starting with zero—the index of the first array element is 0, the index of the second is 1, and so on.

Fun fact: Outside of programming, it’s somewhat unusual to see a count that starts at 0 instead of 1, but there’s a reason you’ll see this in many programming languages. In the original implementation of the array data structure, the computer reserved side-by-side spots in memory for each element in an array, but it was too inefficient to keep track of all these memory locations. Therefore, the computer only stored the memory address of the very first element. The index was used to indicate how far away from the start of the array a given element was located. The first element of an array was zero spaces away from that stored address, hence it was at the 0th index.

#### Creating Arrays with array()
We can construct ordered arrays with a [built-in PHP function: `array()`](https://www.php.net/manual/en/function.array.php).

The `array()` function returns an array. Each of the arguments with which the function was invoked becomes an element in the array (in the order they were passed in).

Arrays are most useful when we store them in variables. We create an array variable the same way we create variables of other data types—with the assignment operator.

```php
$my_array = array(0, 1, 2);
```

PHP arrays can store elements of any data type:

```php
$string_array = array("first element", "second element");
```

PHP arrays can also store elements of multiple data types:

```php
$mixed_array = array(1, "chicken", 78.2, "bubbles are crazy!");
```

We can use the [built-in PHP `count()` function](https://www.php.net/manual/en/function.count.php) to get the number of elements in an array.

```php
echo count($my_array); // Prints: 3
echo count($string_array); // Prints: 2
echo count($mixed_array); // Prints: 4
```

#### Creating Arrays with Short Syntax
In addition to using `array()`, we can also create an array by wrapping comma-separated elements in square brackets (`[ ]`). This feature is sometimes referred to as _short array syntax_, and more closely resembles what you might see in other programming languages.

```php
$number_array = [0, 1, 2];
```

When constructing arrays, we can also place each element on its own line to make it easier to read:

```php
$long_array = [
  1,
  2,
  3,
  4,
  5,
  6
];
```

#### Printing Arrays
Since arrays are a more complicated data type than strings or integers, printing them is slightly more challenging. Using `echo` won’t have the desired result:

```php
$number_array = [0, 1, 2];
echo $number_array; // Prints: Array
```

To print the contents of the array, we can use PHP built-in functions. The [built-in `print_r()` function](https://php.net/manual/en/function.print-r.php) outputs arrays in a human **r**eadable format:

```php
print_r($number_array);
```

This will output the array in the following format:

```
Array
(
    [0] => 0
    [1] => 1
    [2] => 2
)
```

If we merely want to print the elements in the array listed, we can convert the array into a string using the [built-in `implode()` function](https://www.php.net/manual/en/function.implode.php). The `implode()` function takes two arguments: a string to use between each element (the `$glue`), and the array to be joined together (the `$pieces`):

```php
echo implode(", ", $number_array);
```

This will output in the following format:

```
0, 1, 2 
```

#### Accessing an Element
The individual elements in an array can be accessed using the array variable’s name, and the location index surrounded by square brackets (`[]`).

```php
$my_array = ["tic", "tac", "toe"];
 
echo $my_array[1]; // Prints: tac
```

This process is sometimes referred to as _indexing_ an array.

Remember the computer _evaluates_ variables it encounters (outside of assignment): it replaces them with the values they hold.

```php
$num_var = 2;
 
$important_info = ["talking chicken", 181, "magnets?!", 99];
 
echo $important_info[$num_var]; // Prints: magnets?!
```

#### Adding and Changing Elements
We can make adjustments to existing arrays—we don’t have to create a new array when we want our array to change.

We add elements to the end of an array by taking the variable name and appending square brackets (`[]`), the assignment operator (`=`), and the element we want to add:

```php
$string_array = ["first element", "second element"];
 
$string_array[] = "third element";
 
echo implode(", ", $string_array); 
// Prints: first element, second element, third element 
```

We can also reassign the individual elements in an array:

```php
$string_array = ["first element", "second element", "third element"];
 
$string_array[0] = "NEW! different first element";
 
echo $string_array[0]; // Prints: NEW! different first element"
```

#### More Array Methods: Pushing and Popping
PHP also provides us with built-in methods for removing array elements, and for adding many elements at once.

The [`array_pop()` function](https://www.php.net/manual/en/function.array-pop.php) takes an array as its argument. It removes the last element of an array and returns the removed element.

```php
$my_array = ["tic", "tac", "toe"];
array_pop($my_array); 
// $my_array is now ["tic", "tac"]
$popped = array_pop($my_array); 
// $popped is "tac"
// $my_array is now ["tic"]
```

Note that `array_pop()` doesn’t just set the last element to `NULL`. It actually removes it from the array, meaning that array’s length will decrease by one (which we can verify using `count()`).

The [`array_push()` function](https://www.php.net/manual/en/function.array-push.php) takes an array as its first argument. The arguments that follow are elements to be added to the end of the array. `array_push()` adds each of the elements to the array and returns the new number of elements in the array.

```php
$new_array = ["eeny"];
$num_added = array_push($new_array, "meeny", "miny", "moe"); 
echo $num_added; // Prints: 4
echo implode(", ", $new_array); // Prints: eeny, meeny, miny, moe 
```

#### Shifting and Unshifting
PHP also provides functions for adding and removing elements from the beginning of an array (index `0`).

The [`array_shift()` function](https://www.php.net/manual/en/function.array-shift.php) removes the first element of an array and returns that value. Each of the elements in the array will be _shifted_ down an index. For example, the element that was previously at the 3rd index will now be located at the 2nd.

```php
$adjectives = ["bad", "good", "great", "fantastic"];
$removed = array_shift($adjectives); 
echo $removed; //Prints: bad
echo implode(", ", $adjectives); // Prints: good, great, fantastic 
```

Just like `array_pop()`, `array_shift()` reduces the length of the array, and the deleted element is gone for good.

The [`array_unshift()` function](https://www.php.net/manual/en/function.array-unshift.php) takes an array as its first argument. The arguments that follow are elements to be added to the beginning of the array. It returns the new number of elements in the array.

```php
$foods = ["pizza", "crackers", "apples", "carrots"];
$arr_len = array_unshift($foods, "pasta", "meatballs", "lettuce"); 
echo $arr_len; //Prints: 7
echo implode(", ", $foods); 
// Prints: pasta, meatballs, lettuce, pizza, crackers, apples, carrots
```

#### Nested Arrays
We mentioned that arrays can hold elements of any type—this even includes other arrays! We can use chained operations to access and change elements within a nested array:

```php
$nested_arr = [[2, 4], [3, 9], [4, 16]];
$first_el = $nested_arr[0][0];
echo $first_el; // Prints: 2
```

#### Review
- _Arrays_ are ordered collections of data that are a type of data structure fundamental to computer science.
- In PHP, we refer to this data structure as _ordered arrays_.
- The location of an element in an array is known as its _index_.
- The elements in an ordered array are arranged in ascending numerical order starting with index zero.
- We can construct ordered arrays with a built-in PHP function: `array()`.
- We can construct ordered arrays with short array syntax, e.g. `[1,2,3]`.
- We can print arrays using the built-in `print_r()` function or by converting them into strings using the `implode()` function.
- We use square brackets (`[]`) to access elements in an array by their index.
- We can add elements to the end of an array by appending square brackets (`[]`) to an array variable name and assigning the value with the assignment operator (`=`).
- We can change elements in an array using array indexing and the assignment operator.
- The `array_pop()` function removes the last element of an array.
- The `array_push()` function adds elements to the end of an array.
- The `array_shift()` function removes the first element of an array.
- The `array_unshift()` function adds elements to the beginning of the array.
- We can use chained square brackets (`[]`) to access and change elements within a nested array.


### Associative Arrays

#### Introduction
Time to meet another fundamental concept in computer science—the map. A _map_ associates keys with values. A key is a string or integer that we use to access a value (of any type). Whenever we need to access a value, we’ll be able to use the _associated_ key to find it.

The PHP array type that we’ve been working with is actually implemented as a map! In a PHP ordered array, the index locations are the keys. But the PHP array type also enables us to build more traditional map-like structures where we assign meaningful keys to values (as opposed to indices). We call data structures like this _associative arrays_.

#### Associative Arrays
_Associative arrays_ are collections of _key=>value_ pairs. The key in an associative array must be either a string or an integer. The values held can be any type. We use the `=>` operator to associate a key with its value.

We can think of keys as _pointing_ to their values since the key points the computer to the space in memory where the value is stored.

```php
$my_array = ["panda" => "very cute", "lizard" => "cute", "cockroach" => "not very cute"];
```

We can also build associative arrays using the PHP `array()` function.

```php
$about_me = array(
    "fullname" => "Aisle Nevertell",
    "social" => 123456789
);
```

#### Printing Associative Arrays
As with ordered arrays, using `echo` to print an entire associative array is not very useful:

```php
$grades = [
    "Jane" => 98,
    "Lily" => 74,
    "Dan" => 88,
];
 
echo $grades; // Prints: Array
```

We can combine each of the values contained by the array into a single string and use `echo` to print that:

```php
echo implode(", ", $grades); // Prints: 98, 74, 88 
```

A problem with this technique is that it only displays the values. We don’t see the keys in the array or the relationships between the keys and values. To display this information, we can use the built-in `print_r()` function:

```php
print_r($grades);
```

The above code will produce the following output:

```
Array
(
    [Jane] => 98
    [Lily] => 74
    [Dan] => 88
)
```

#### Accessing and Adding Elements
We can access the value that a given key points to by using square brackets (`[]`):

```php
$my_array = ["panda"=>"very cute", "lizard"=>"cute", "cockroach"=>"not very cute"];
echo $my_array["panda"]; // Prints: very cute
```

To add new elements to an associative array, we use the assignment operator (`=`):

```php
$my_array["capybara"] = "cutest";
echo $my_array["capybara"]; // Prints: cutest
```

The computer treats code between the square brackets as an expression, so that code will be evaluated before the array is accessed. This enables us to use variables, functions, and operators within the square brackets:

```php
$favorites = ["favorite_food"=>"pizza", "favorite_place"=>"my dreams", "FAVORITE_CASE"=>"CAPS", "favorite_person"=>"myself"];
 
echo  $favorites["favorite" . "_" . "food"]; 
// Prints: pizza
 
$key =  "favorite_place";
echo  $favorites[$key];  
// Prints: my dreams
 
echo $favorites[strtoupper("favorite_case")];
// Prints: CAPS
```

#### Changing and Removing Elements
The same syntax that adds new array elements can be used to change existing elements:

```php
$new_arr = ["first" => "I am first!", "second" => "I am second!"]; 
 
$new_arr["third"] = "I am third!";
 
echo $new_arr["third"]; // Prints: I am third!
 
$new_arr["third"] = "I am the *NEW* third!";
 
echo $new_arr["third"]; // Prints: I am the *NEW* third!
```

We can remove a _key=>value_ pair entirely using [the PHP `unset()` function](https://www.php.net/manual/en/function.unset.php). Note: if the key used doesn’t exist in the array, then nothing happens.

```php
$nums = ["one" => 1,"two"=> 2];
 
echo implode(", ", $nums); // Prints: 1, 2
 
unset($nums["one"]);
 
echo implode(", ", $nums); // Prints: 2
```

#### Numerical Keys
Associative arrays can use integers as keys, in addition to strings.

```php
$num_array = [1000 => "one thousand", 100 => "one hundred", 600 => "six hundred"];
echo $num_array[1000]; // Prints: one thousand
```

When we build ordered arrays in PHP, the association with numerical keys to values is done for us automatically. The first element is associated with the key `0`, the second with `1`, and so on. But ordered arrays are still the same structure as associative arrays. We can mix and match:

```php
$ordered = [99, 1, 7, 8];
$ordered["special"] = "Cool!";
echo $ordered[3]; // Prints: 8
echo $ordered["special"]; // Prints: Cool!
```

When we add an element to an array without specifying a key (e.g. using `array_push()`), PHP will associate it with the “next” integer key. If no integer keys have been used, it will associate it with the key `0`, otherwise it will associate it one more than the largest integer used thus far. This behavior is the same whether the array is being used as an ordered array or an associative array.

```php
$num_array = [1000 => "one thousand", 100 => "one hundred", 600 => "six hundred"];
$num_array[] = "New Element in \$num_array";
echo $num_array[1001]; // Prints: New Element in $num_array
 
$animals_array = ["panda"=>"very cute", "lizard"=>"cute", "cockroach"=>"not very cute"];
array_push($animals_array, "New Element in \$animals_array");
echo $animals_array[0]; // Prints: New Element in $animals_array
```

Even though associative arrays and ordered arrays are technically the same, we recommend treating them as separate data types. Only use the empty square brackets syntax (or functions like `array_push()`) with ordered arrays.

#### Joining Arrays
PHP also lets us combine arrays. The union (`+`) operator takes two array operands and returns a new array with any unique keys from the second array appended to the first array.

```php
$my_array = ["panda" => "very cute", "lizard" => "cute", "cockroach" => "not very cute"];
$more_rankings = ["capybara" => "cutest", "lizard" => "not cute", "dog" => "max cuteness"];
$animal_rankings = $my_array + $more_rankings;
```

The `$animal_rankings` we created above will have each of the _key=>value_ pairs from `$my_array`. In addition, it will contain the _key=>value_ pairs from `$more_rankings`: `"capybara"`=>`"cutest"` and `"dog"`=>`"max cuteness"`. However, since `"lizard"` is not a unique key, `$animal_rankings["lizard"]` will retain the value of `$my_array["lizard"]` (which is `"cute"`).

The union operator can be a little tricky… consider the following union:

```php
$number_array = [8, 3, 7];
 
$string_array = ["first element", "second element", "third element"];
 
$union_array = $number_array + $string_array;
```

What values does `$union_array` hold? It has the elements `8`, `3`, and `7`. Since the two arrays being joined have identical keys (`0`, `1`, and `2`), no values from the second array, `$string_array`, are included in `$union_array`.

#### Assign by Value or by Reference
There are two ways to assign one variable to another:

- By value—this creates two variables that hold copies of the same value but remain independent entities.
- By reference—this creates two variable names (aliases) which point to the same space in memory. They cannot be modified separately!

This remains true when dealing with array variables:

```php
$favorites = ["food"=>"pizza", "person"=>"myself", "dog"=>"Tadpole"];
$copy = $favorites;
$alias =& $favorites;
$favorites["food"] = "NEW!";
 
echo $favorites["food"]; // Prints: NEW!
echo $copy["food"]; // Prints: pizza
echo $alias["food"]; // Prints: NEW!
```

When passing arrays into functions, both built-in functions and those we write ourselves, we’ll want to be conscious of whether the arrays are being passed by value or by reference.

```php
function changeColor ($arr) 
{
  $arr["color"] = "red";    
}
$object = ["shape"=>"square", "size"=>"small", "color"=>"green"];
changeColor ($object);
echo $object["color"]; // Prints: green
```

Our function above doesn’t accept its array argument by reference. Therefore, `$arr` is merely assigned a copy of the argument’s value. This copy array is changed when the function is invoked, but that doesn’t affect the original argument array (`$object`). To do that, we’d need to pass it by reference:

```php
function reallyChangeColor (&$arr) 
{
  $arr["color"] = "red";    
}
$object = ["shape"=>"square", "size"=>"small", "color"=>"green"];
reallyChangeColor ($object);
echo $object["color"]; // Prints: red
```

#### Review
- _Associative arrays_ are data structures in which string or integer _keys_ are associated with _values_.
- We use the `=>` operator to associate a key with its value. `$my_array = ["panda"=>"very cute"]`
- To print an array’s keys and their values, we can use the `print_r()` function.
- We access the value associated with a given key by using square brackets (`[ ]`). For example: `$my_array["panda"]` will return `"very cute"`.
- We can assign values to keys using this same indexing syntax and the assignment operator (`=`): `$my_array["dog"] = "good cuteness";`
- This same syntax can be used to change existing elements. `$my_array["dog"] = "max cuteness";`
- We can remove a _key=>value_ pair entirely using the PHP `unset()` function.
- Keys can be integers. In fact, ordered arrays are just arrays in which integer keys have been assigned to the values automatically.
- In PHP, associative arrays and ordered arrays are different uses of the same data type.
- The union (`+`) operator takes two array operands and returns a new array with any unique keys from the second array appended to the first array.
- When writing function with array parameters, we can pass the array by value or by reference depending on our intent.
 

## PHP Loops
### Loops

#### Why Use Loops?
When attempting to repeat code over and over again, it can be monotonous to retype or copy and paste the same code. Worse, inadvertent typos can cause errors in your program.

Luckily, most programming languages contain a feature, called _loops_, for repeating code automatically until certain conditions are met. Sometimes the repetition is referred to as _iterating_ and each time the code is executed is considered an _iteration_. Loops can be used to reduce the number of lines of code while also making it much easier to modify later on.

Each of these loops contain conditions for stopping execution of the loop. Improper implementation of these conditions can cause an _infinite loop_ and the computer will never stop executing your code block.

#### while
This type of loop continues to iterate as long as its conditional is true.

```php
$count = 1;
while ($count < 11)
{
  echo "The count is: " . $count . "\n";
  $count += 1;
}
```

#### do while
A `do`…`while` loop is very similar to a `while` loop. The main difference is that the code block will execute once without the conditional being checked. After the first iteration, it behaves the same as a `while` loop.

```php
$count = 1;
do {
  echo "The count is: " . $count . "\n";
  $count += 1;
} while ($count < 11);
```

Unlike the other loop types, the `do`…`while` loop requires a semicolon at the end.

In practice, only use this type of loop when you always need the code block to execute at least one time.

```php
<?php
do {
  $guess = readline("\nGuess the number\n");
} while ($guess != "42");
echo "\nYou correctly guessed 42!";
```

#### for
A `for` loop is commonly used to execute a code block a specific number of times.

```php
for (#expression 1; #expression 2; #expression 3)
{
  # code block
}
```

The `for` loop syntax includes 3 expressions:

- The first is evaluated only one time before the first iteration.
- The second is evaluated before each iteration. If it is `TRUE`, the code block is executed. Otherwise, the loop terminates.
- The third is evaluated after each iteration. Note that expressions 1 and 2 have semicolons after them.

```php
for ($count = 1; $count < 11; $count++)
{
  echo "The count is: " . $count . "\n";
}
```

#### foreach
The `foreach` loop is used for iterating over an array. The code block is executed for every element in the array and the value of that element is available for use in the code block.

```php
$counting_array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
foreach ($counting_array as $count) {
  echo "The count is: " . $count . "\n";
}
```

We can also iterate over dictionary type arrays with keys and values:

```php
$details_array = ["color" => "blue", "shape" => "square"];
foreach ($details_array as $detail) {
  echo "The detail is: " . $detail . "\n";
}
```

This will print:

```
The detail is: blue
The detail is: square
```

But we can change the syntax slightly to get access to the keys as well as the values:

```php
$details_array = ["color" => "blue", "shape" => "square"];
foreach ($details_array as $attribute => $detail) {
  echo "The " . $attribute . " is: " . $detail . "\n";
}
```

This will print:

```
The color is: blue
The shape is: square
```

Since the loop is controlled by the structure of the array, you can encounter some unexpected behavior if you begin modifying the array during the execution of the `foreach` loop. If you are going to do this, make sure you have addressed the notes on this in the [PHP documentation](https://www.php.net/manual/en/control-structures.foreach.php).

#### break and continue
Similar to `switch` statements, the `break` keyword can be used to terminate any of the loop types early.

```php
$count = 1;
while ($count < 11)
{
  echo "The count is: " . $count . "\n";
  if ($count === 5) {
    break;
  }
  $count += 1;
}
```

The code will now count from 1 to 5 and then stop.

One downside of heavy usage of `break` statements is that code can become less readable. In this example, a quick glance might give someone the impression that the loop will iterate until `$count` is `10`. In reality, the buried `break` statement is controlling the final iteration of the loop.

The `continue` keyword is similar to `break` except it only ends the current iteration early, not the entire loop. We could use this in our example to skip counting the number 5:

```php
$count = 1;
while ($count < 11)
{
  if ($count === 5) {
    $count += 1;
    continue;
  }
  echo "The count is: " . $count . "\n";
  $count += 1;
}
```

Note that we needed to add an extra increment before the `continue` (`$count += 1;`) to avoid being caught in an infinite loop.

#### Review
- `while` loops execute only as long as their conditional evaluates to `TRUE`.
- `do`…`while` loops always execute at least once and then continue executing while their conditional is `TRUE`.
- `for` loops contain 3 expressions and are frequently used to execute a code block a specific number of times.
    - The first expression is executed prior to the first iteration.
    - The second expression is evaluated prior to each iteration. If `TRUE`, the code block executes. Otherwise, the loop terminates.
    - The third expression is evaluated after each iteration.
- `foreach` loops are used for iterating over the elements of an array. The key and value of each element is available in the code block.
- `break` is used to end execution of a loop early.
- `continue` is used to end execution of a loop iteration early and continues to the next iteration.


# PHP and HTML
## PHP and HTML
### PHP and HTML

#### Introduction
PHP was designed as a back-end web development language—specifically it was designed to work well with HTML. PHP allowed a convenient way for developers to create HTML templates and programatically fill them out in order to send customized HTML to visitors of their sites.

PHP has evolved into a powerful programming language being used for more than templating HTML, but using PHP combined with HTML remains an important part of many web developers’ skill sets.

#### What is the Front-End?
When navigating to a website from our web browser, the browser makes a request for content on our behalf. What we see and experience as a single website is actually composed of a number of files which come together to form a cohesive experience.

The files we receive consist of JavaScript, CSS, HTML, images, and other _static assets_. A static asset is a file that doesn’t change. When we navigate to a webpage, these assets are sent to a browser.

You may have heard front-end development referred to as _client-side_ development. In web development, we are typically referring to the browser as the client. A human may be experiencing the website, but it’s the browser that makes requests for information and receives the responses.

The front-end of a website or web application consists of all the elements of the website that are sent to the client upon request. But something has to be listening for those requests and deciding what to send — it’s the back-end of the website that does all that and more.

#### What is the Back-End?
The back-ends of websites will differ depending on the needs of the site. Typically, they’ll have at least the following components:

1. A _web server_: a web server is a computer or program which listens for requests from clients and sends back responses. This component is well suited to handling delivery of static content.
2. An _application server_: this is actually often a collection of programming logic which is needed to deliver dynamic content to a client. The application server will often handle other tasks such as site security and interacting with data.
3. A _data base_: important information like usernames and passwords has to be stored and accessed somewhere. A large web application will often have multiple databases to store all different types of data needed to run the site smoothly.

#### PHP in HTML
We can embed PHP scripts within HTML documents with the opening tag `<?php` and the closing tag `?>`. The PHP processor will read the entire file, evaluate any PHP, translate it into HTML, and pass it off to the web server so it can be sent to the client.

```php
<html>
 <head>
  <title>My First PHP Site</title>
 </head>
 <body>
 <?php 
    echo "<h1>Oh hi!</h1>"; 
  ?> 
 </body>
</html>
```

When we use `echo` within HTML we’re no longer printing to the terminal, rather we’re outputting to the HTML document.

Wouldn’t it have been simpler to just add `<h1>Oh hi!</h1>` directly? Yep. This example certainly doesn’t show us **why** we’d want to use PHP within our HTML. As we learn to develop more robust PHP scripts and harness some of the language’s more complex features, we’ll grow to understand how powerful it can be.

---
You’ll notice that the workspace now has a file titled **index.php** instead of **index.html**. We’re using the `php` extension because we want to add some PHP code to it.

#### Beyond Strings
We can also incorporate more complex PHP within our scripts.

```php
<?php
$lucky_number = 5 * 2 - 1;
 
echo "<h1>Your lucky number is ${lucky_number}</h1>";
?>
```

We can incorporate all the language features we know about PHP, including functions:

```php
<?php
function makeHeaderGreeting ($name){
  return "<h1>Hello, ${name}!</h1>";
}
 
echo makeHeaderGreeting("World");
?>
```

The code above will be translated into HTML with a header that reads: `Hello, World!`.

#### Review
- The front-end of a website consists of JavaScript, CSS, HTML, images, and other _static assets_ sent to the _client_.
- When we navigate to a website the browser is the _client_, and it sends a request to the back-end for all the assets needed to view and interact with the website.
- The back-end consists of a _web server_ and all the logic and data needed to create and maintain a website or web application.
- PHP is a back-end language.
- PHP can be used to generate HTML files.
- We embed PHP scripts within HTML by inserting PHP code between the opening (`<?php`) and closing (`?>`) tags.


### Loops in HTML

#### Why Use Shorthand?
Using the traditional loop syntax in PHP with brackets (`{}`) to open and close code blocks can be used when embedding PHP code in HTML:

```php
<ul>
<?php
for ($i = 0; $i < 2; $i++) {
?>
<li>Duck</li>
<?php
}
?>
<li>Goose</li>
</ul>
```

However, when adding nested loops, the readability of the code can suffer. To determine where loops end, we have to count and match brackets.

Luckily, PHP offers an alternate syntax which is especially useful when working with HTML. Instead of using an opening bracket (`{`), we use a colon (`:`) and instead of using a closing bracket (`}`), we use a closing keyword and semicolon (`;`). For the `for` loop, the closing keyword is `endfor`. Our duck, duck, goose example becomes:

```php
<ul>
<?php
for ($i = 0; $i < 2; $i++):
?>
<li>Duck</li>
<?php
endfor;
?>
<li>Goose</li>
</ul>
```

#### Loop Shorthand
For a `while` loop, the closing keyword is `endwhile`, and for the `foreach` loop, the closing keyword is `endforeach`.

```php
<ul>
<?php
$i = 0;
while ($i < 2):
?>
<li>Duck</li>
<?php
$i++;
endwhile;
?>
<li>Goose</li>
</ul>
```

And the same example using `foreach` becomes:

```php
<ul>
<?php
$array = [0, 1];
foreach ($array as $i):
?>
<li>Duck</li>
<?php
endforeach;
?>
<li>Goose</li>
</ul>
```

#### Code Block Considerations
One frequent pattern that we encounter is iterating over an array using a `foreach` loop and creating HTML elements using the items from the array. The following approach does not work as one might hope:

```php
<?php
$array = ["Alice", "Bob", "Charlie"];
foreach($array as $name): ?>
<p>$name</p>
<?php endforeach; ?>
```

Since we are in HTML mode and not PHP mode when using `$name` here, it will simply print `$name`, instead of the corresponding item from the array.

Because of this behavior, it’s important to remember to re-enter PHP mode before using PHP variables. This can be done using the `<?php` opening and `?>` closing tags. If you are going to simply be printing the variable using `echo`, you can also use the `echo` shorthand opening tag (`<?=`).

```php
<?php
$array = ["Alice", "Bob", "Charlie"];
foreach($array as $name): ?>
<p><?=$name?></p>
<?php endforeach; ?>
```

#### Review
- The PHP shorthand for loops uses a colon (`:`) instead of a bracket (`{`) to open the code block.
- The shorthand uses keywords to close the code block instead of a bracket (`}`):
    - Use `endfor` to close a `for` loop
    - Use `endforeach` to close a `foreach` loop
    - Use `endwhile` to close a `while` loop
- The closing keyword needs to be followed by a semicolon (`;`).
- Make sure to re-enter PHP mode using `<?php` or the `echo` shorthand `<?=` before using PHP variables in the loop


## PHP Form Handling
### HTML Form Handling in PHP

#### Request Superglobals
Since PHP was built with web development as a primary use case, it has functionality to ease processing of HTML requests. When the front end client makes a request to a backend PHP server, several _superglobals_ related to the request are available to the PHP script. Superglobals are automatic global variables which are available in all scopes throughout a script.

The list of superglobals in PHP includes the following:

- `$GLOBALS`
- `$_SERVER`
- `$_GET`
- `$_POST`
- `$_FILES`
- `$_COOKIE`
- `$_SESSION`
- `$_REQUEST`
- `$_ENV`

For this lesson, we are focusing on three of these:

- `$_GET` - this contains an associative array of variables passed to the current script using query parameters in the URL
- `$_POST` - this contains an associative array of variables passed to the current script using a form submitted using the “POST” method
- `$_REQUEST` - this contains the contents of `$_GET`, `$_POST`, and `$_COOKIE`

#### GET Form Handling
In HTML, setting a form’s `method` attribute to `"get"` specifies that you would like the form to be submitted using the GET method. When using this method, the form entries are passed as parameters in a URL query string.

For example, this is a request to `www.codecademy.com` with the URL parameters `first` (set to the value `"ellen"`) and `last` (set to the value `"richards"`):

```
www.codecademy.com/?first=ellen&last=richards
```

The parameter names (`first` and `last`) come from the `name` attribute of each form input.

For example, the following form could be used to collect an individual’s name using the GET method:

```php
<form method="get">
First name: <input type="text" name="first">
<br>
Last name: <input type="text" name="last">
<br>
<input type="submit" value="Submit Name">
</form>
```

When the form is submitted, the form data is available in the `$_GET` superglobal array. The data is also accessible using `$_REQUEST` if you do not care about which method was used by the client.

In our example, if a user typed “ellen” into the `first` input and “richards” into the `last` input, then `print_r($_GET)` would look like this:

```
Array ( [first] => ellen [last] => richards )
```

To echo the value of the `first` input, we pass the parameter name to the `$_GET` array like below:

```php
<?=$_GET['first'];?>
```

---

If you try submitting the form, you may notice that the URL is not changing to include URL parameters as you might expect. This is because neither input has a `name` attribute yet.

#### POST Form Handling
In HTML, setting a form’s `method` attribute to `"post"` specifies that you would like the form to be submitted using the POST method. When using POST to submit forms, you will not see the URL change. The form data is sent using the headers of the HTTP request instead of URL parameters.

To use the data from the form in PHP, each input needs to have a unique `name` attribute.

When the form is submitted, the input data is available in the `$_POST` superglobal. Similar to GET, it is also available in `$_REQUEST`.

For example, if a user typed “Katharine” into the `first` input and “McCormick” into the `last` input of this form:

```php
<form method="post">
First name: <input type="text" name="first">
<br>
Last name: <input type="text" name="last">
<br>
<input type="submit" value="Submit Name">
</form>
```

The URL would not change and `print_r($_POST)` would look like this:

```
Array ( [first] => Katharine [last] => McCormick )
```

#### Using the "action" Attribute
Until now, we’ve been handling the response to the form submission on the same page as the form itself. Often times there is no need to present a user with the same form over and over again. It might make sense to move them to a new page or thank them for their submission.

This is where the `action` form attribute comes into play. Since we have not specified an `action` yet, HTML defaults to submitting the form data back to the same script that defined the form.

If you would like to have the user navigate to a new URL and handle the form input there, you can specify the URL in the form’s `action` attribute. Since the `action` attribute specifies a relative URL, you can also enter the name of a PHP file in the same directory as the current one.

For example, given this directory:

```
index.php
receive_form.php
```

To handle a form using **receive_form.php** from **index.php**, you would use the following:

```php
<form method="get" action="receive_form.php">
```

This works for both GET and POST methods.

#### Review
- `<?=` is shorthand for `<?php echo`.
- PHP provides superglobals which can be accessed anywhere in the script.
    - `$_GET` is an associative array containing data from a GET request.
    - `$_POST` is an associative array containing data from a POST request.
    - `$_REQUEST` is an associative array containing data from both GET and POST requests. It should only be used if you don’t care which method was used.
- The array keys in the PHP request superglobals are set by the `name` attributes in the HTML form, which need to be unique.
- The `action` attribute is used to specify which file should handle data from the form request.
 

## PHP Form Validation
### Introduction to PHP Form Validation

#### Introduction
The back-end should **never** trust the data it receives from the client. Either intentionally or not, bad data from the client has the potential to expose sensitive information, corrupt our data, or significantly slow down our server.

#### Form Handling

```php
<form method="post" action="">
Your Favorite Programming Language: <input type="text" name="language">
<input type="submit" value="Submit Language">
</form>
```

Since we want users to have the opportunity to submit the form again if they have errors, we’ll leave the action as an empty string—this means that once it’s submitted, users will be served the same PHP file that originally served them the form.

#### Simple Validation
We’ll _validate_ (confirm the correctness of) the data we receive. If the input is deemed invalid, we’ll want to give the user meaningful feedback so that they can correct their mistake and attempt to submit the form again.

We’ll need to make several modifications to the PHP file that we use to serve our form to users:

1. Add PHP code to check the validity of a user’s input if the form has been submitted.
2. Add an HTML element to display an error message to the user if their submission is not valid.
3. Fill each field in the form with the user’s previously submitted input.

Our third task has to do with creating an improved user experience. Have you ever had to refill every field in a form after submitting it incorrectly? It’s so frustrating! By filling in the user’s submitted values, they’ll be able to quickly correct any fields with errors without having to start over from scratch. To accomplish this, we’ll assign each of the HTML form element’s `value` attribute—aside from the `"submit"` input itself—to the data submitted by the user for each field.

For the purposes of this exercise, let’s assume that “PHP” is the only valid submission for the user’s favorite language.

```php
<?php
$validation_error = "";
$user_language = "";
 
if ($_SERVER["REQUEST_METHOD"] === "POST") {
$user_language = $_POST["language"];
  if ($user_language != "PHP") {
    $validation_error = "* Your favorite language must be PHP!";
  } 
}
?>
 
<form method="post" action="">
Your Favorite Programming Language: <input type="text" name="language" value="<?php echo $user_language;?>">
<p class="error"><?= $validation_error;?></p>
<input type="submit" value="Submit Language">
</form>
```

- We first assign `$validation_error` and `$user_language` to empty strings. We use these PHP values in our HTML, but, if a user has NOT yet submitted their form, we don’t want these elements to have filled in values.
- Remember that we’re validating the form data only AFTER it’s been submitted by the user at least once. To ensure that, we only run our validation code `if ($_SERVER["REQUEST_METHOD"] === "POST")`, which indicates that the current form has been submitted.
- Within our `if` block, we grab the relevant value from the `$_POST` array: `$_POST["language"]`. We assign this value to our `$user_language` variable. This one step actually accomplishes two things! It gives us an easy way to talk about the value the user submitted to this field, and it also means the `value` of the HTML element will now be the user’s submission rather than an empty string.

#### Basic Data Sanitizing
In the previous exercise, we performed a simple validation to check the user’s input, but we made a mistake by directly displaying the data we received from them. Remember that we must never simply trust the data we receive from the client. In order to protect against innocent but dangerous user mistakes, malicious users, or man-in-the-middle attacks, we need to _sanitize_ the data—transform it into a safe and standardized format.

PHP provides several built-in functions to help with sanitization:

We can use [the built-in PHP `trim()` function](https://www.php.net/manual/en/function.trim.php) to remove any whitespace characters from the beginning or end of a string we receive as form input. Though not a security concern, this can help standardize the data prior to validation.

```php
$email = "     aisle.nevertell@yahoo.com   ";
echo trim($email); // Prints: aisle.nevertell@yahoo.com
```

When we want to display the user’s input within our own HTML, we should first run it through `htmlspecialchars()`. [This built-in function](https://www.php.net/manual/en/function.htmlspecialchars.php) transforms HTML elements into [HTML entities](https://developer.mozilla.org/en-US/docs/Glossary/Entity) (characters that represent HTML elements but won’t display as HTML), so that the PHP interpreter doesn’t recognize them as HTML. This prevents, for example, a man-in-the-middle attack in which malicious HTML is injected into a user’s view of our site.

```php
$data = "<a href=\"https://www.evil-spam.biz/html/\">Your account has been compromised! Click here to get technical support!!</a>";
 
echo htmlspecialchars($data);
 
// Prints: &lt;a href=&quot;https://www.evil-spam.biz/html/&quot;&gt;Your account has been compromised! Click here to get technical support!&lt;/a&gt;
```

#### Basic Sanitization with filter_var()
We haven’t yet introduced the most powerful PHP function for sanitizing data: `filter_var()`. [This function](https://www.php.net/manual/en/function.filter-var.php) operates on a variable and passes it through a “filter” that produces the desired outcome.

As its first argument, `filter_var()` takes a variable. As its second, it takes an ID representing the type of filtering that should be performed. There are [several filters for sanitizing common input types](https://www.php.net/manual/en/filter.filters.sanitize), including `FILTER_SANITIZE_EMAIL`. The function will return either the sanitized version of the input or `FALSE` if it was unable to perform the sanitization.

```php
$bad_email = '<a href="www.evil-spam.biz">@gmail.com';
echo filter_var($bad_email, FILTER_SANITIZE_EMAIL);
// Prints: ahref=www.evil-spam.biz@gmail.com 
```

The `FILTER_SANITIZE_EMAIL` filter trimmed whitespace throughout our input and removed dangerous characters thus preventing any HTML injection. Essentially, it **filtered** out any characters not allowed in emails. Once sanitized, we can safely display user inputs.

Of course, `$bad_email` did not store a valid email in the first place. But since we often want to display invalid form data as a hint for the user, this sanitization would be useful to prevent a man-in-the middle attack. We could also have used `htmlspecialchars($bad_email)`, but that would have produced `&lt;a href=&quot;www.evil-spam.biz&quot;&gt;@gmail.com` instead. Choose the sanitization method based on the output you want to show to the users.

```php
<?php
$validation_error = "";
$user_answer = "";
$submission_response = "";

// Write your code here:
if ($_SERVER["REQUEST_METHOD"] === "POST") {
  $user_answer = filter_var($_POST["answer"], FILTER_SANITIZE_NUMBER_INT);

  if ($user_answer === "-5") {
    $submission_response = "Correct!";
  } else {
  $validation_error = "* Wrong answer. Try again.";
  }
}

?>
<h2>Time for a math quiz!</h2>
<form method="post" action="">
<h4>Question 1:</h4>  
<p>What is 6 - 11?</p> 
<input type="text" name="answer" id="answer" value="<?= $user_answer;?>">
<br>
<span class="error" id="error"><?= $validation_error;?></span> 
<br> 
<input type="submit" value="Submit Your Answer">
</form>
<div>
  <p id="answer-display">Your answer was: <?= $user_answer;?></p>
  <p id="submission-response"><?= $submission_response;?></p>
</div>
```

#### Basic Validation with filter_var()
We can use the same `filter_var()` function to **validate** as well as sanitize! There are a number of [provided validation filters](https://www.php.net/manual/en/filter.filters.validate.php), but they work a bit differently from the sanitization filters. If the variable is deemed valid, `filter_var()` will return it; otherwise, it will return `FALSE`:

```php
$bad_email = 'fake - at - prank dot com';
if (filter_var($bad_email, FILTER_VALIDATE_EMAIL)){
  echo "Valid email!";
} else {
  echo "Invalid email!";
} 
// Prints: Invalid email!
```

It’s worth noting that the provided `FILTER_VALIDATE_EMAIL` filter is stricter than the guidelines regulating acceptable email addresses. If a site needed to accept non-latin characters, for example, the built-in `FILTER_VALIDATE_EMAIL` filter wouldn’t be sufficient.

Using the provided validation filters is really convenient. You can check out the list of [available validation filters in the PHP manual](https://www.php.net/manual/en/filter.filters.validate.php). For example, `FILTER_VALIDATE_URL` is useful for checking if a string corresponds to a possible URL.

#### Using Options with filter_var()
The `filter_var()` function accepts an optional third argument that allows us to fine-tune the operation of a given filter. This argument, often called `$options`, takes the form of a nested associative array.

For example, the `$options` argument can help us validate that an integer is within a specified range when using the integer validation filter `FILTER_VALIDATE_INT`. To do this, we set `$options` to a nested array containing the`"min_range"` and `"max_range"` keys in a specific format.

```php
function validateAdult ($age){
  $options = ["options" => ["min_range" => 18, "max_range" => 124]];  
  if (filter_var($age, FILTER_VALIDATE_INT, $options)) {
    echo("You are ${age} years old.");
  } else {
    echo("That is not a valid age.");
  }
}
 
validateAdult(18); // Prints: You are 18 years old.
validateAdult(124); // Prints: You are 124 years old.
validateAdult(8); // Prints: That is not a valid age.
validateAdult(200); // Prints: That is not a valid age. 
```

You can see [which filters accept options in the PHP manual](https://www.php.net/manual/en/filter.filters.php).

```php
<?php
$message = "";
$month_error = "";
$day_error = "";
$year_error = "";
  
// Create your variables here:
$month_options = ["options" => ["min_range" => 1, "max_range" => 12]];
$day_options = ["options" => ["min_range" => 1, "max_range" => 31]];
$year_options = ["options" => ["min_range" => 1903, "max_range" => 2023]];

// Define your function here:
function validateInput($type, &$error, $options_arr)
{
  $filter = filter_var($_POST[$type], FILTER_VALIDATE_INT, $options_arr);

  if ($filter) {
    return TRUE;
  } else {
    $error = "* Invalid ${type}";
    return FALSE;
  }
}

  if ($_SERVER["REQUEST_METHOD"] == "POST") {
    // Uncomment the code below:
    $test_month = validateInput("month", $month_error, $month_options);
    $test_day = validateInput("day", $day_error, $day_options);
    $test_year = validateInput("year", $year_error, $year_options);    
    if ($test_month && $test_day && $test_year){
      $message = "Your birthday is: {$_POST["month"]}/{$_POST["day"]}/{$_POST["year"]}";
    }  
  }

?>

<form method="post" action="">
	Enter your birthday:
	<br>
	Month: <input type="number" name="month" value="<?= $_POST["month"];?>">
	<span class="error"><?= $month_error;?>		</span>
  <br>
	Day: <input type="number" name="day" value="<?= $_POST["day"];?>">
  <span class="error"><?= $day_error;?>		</span>
	<br>  
	Year: <input type="number" name="year" value="<?= $_POST["year"];?>">  
	<span class="error"><?= $year_error;?>		</span>
	<br>
	<input type="submit" value="Submit">
</form>
    <p><?= $message;?></p>
```

#### Custom Validations
We’ll often find the validations offered by built-in functions like `filter_var()` to be insufficient. When validating all but the simplest data, we’ll likely need to write our own, custom input validations.

A very common method for validating data is to compare the input to a pattern we define with a regular expression. The [PHP preg_match() function](https://www.php.net/manual/en/function.preg-match.php) takes two string arguments: a _pattern_ string with a regular expression and a _subject_ string to check. It returns `1` if it matches, `0` if it doesn’t, and `FALSE` if there was an error.

For example, we can use the regular expression `/^[(]*([0-9]{3})[- .)]*[0-9]{3}[- .]*[0-9]{4}$/` to test for 10-digit North American telephone numbers. It will allow spaces, hyphens, or periods as optional separators as well as optional parentheses around the first three numbers:

```php
$pattern = '/^[(]*([0-9]{3})[- .)]*[0-9]{3}[- .]*[0-9]{4}$/';
 
preg_match($pattern, "(999)-555-2222"); // Returns: 1
 
preg_match($pattern, "555-2222"); // Returns: 0
```

Before we test for regular expression matches, we’ll want to make sure the input isn’t too long. Regular expressions checks can take a lot of computing power—one way a bad actor can damage our website is by submitting extremely long inputs, putting strain on our servers. This can slow down or even crash our site!

We can use the [built-in PHP `strlen()` function](https://www.php.net/manual/en/function.strlen.php) to check the length of a given input. Ultimately, the acceptable input length is a judgement call for the web engineer. In this example, we chose 100 characters, but [some names can be much longer](https://en.wikipedia.org/wiki/Hubert_Blaine_Wolfeschlegelsteinhausenbergerdorff_Sr).

```php
$name = "Aisle Nevertell";
$length = strlen($name);
if ($length > 2 && $length < 100){
  echo "That seems like a reasonable name to me...";
} 
```

#### Validating Against Back-end Data
Because modern websites and web applications need to store a lot of data, they usually interact with databases on the back-end. A common type of custom validation involves comparing user input against information in the database.

An important application of this kind of validation is handling the creation of a user’s account. Before creating the account, it is very important to check that a submitted username isn’t already being used by someone else! In order to do this, we’ll need to check the database for that username.

```php
$users = ["coolBro123" => "password123!", "coderKid" => "pa55w0rd*", "dogWalker" => "ais1eofdog$"];
 
function isUsernameAvailable ($username){
  global $users;
  if (isset($users[$username])){
    echo "That username is already taken.";
  } else {
    echo "${username} is available.";
  }
}
 
isUsernameAvailable("coolBro123");
// Prints: That username is already taken. 
 
isUsernameAvailable("aisleOfPHP");
// Prints: aisleOfPHP is available.
```

The above function `isUsernameAvailable` uses the built-in function `isset()` to check if a given `$username` exists in the `$users` array. In production, this check would be done by querying the database.

#### Sanitizing for Back-end Storage
In addition to sanitizing data that is displayed to the user, we always need to sanitize all data before storing it in our own databases. There are serious security concerns with storing data in a database—attempting to store unsanitized inputs into a database can allow a bad actor to corrupt or gain access to sensitive information.

We’ll also want to sanitize the formatting: make sure the data stored in our database follows consistent formatting. If we’re going to be displaying or using the data, we’ll want to make sure it always looks the same. So even though we may want to let users input their phone numbers with or without parentheses or dashes, when we store it in the database, we’ll want to change all phone numbers to the same format.

To sanitize data formatting, we can use the built-in `preg_replace()` function. The `preg_replace()` takes a regular expression, some replacement text, and a subject string; First, It searches through the subject string for instances that match the regular expression. Then, it outputs a copy of the subject string that has the matched instances replaced by the replacement string:

```php
$one = "codeacademy";
$two = "CodeAcademy";
$three = "code academy";
$four = "Code Academy";
 
$pattern = "/[cC]ode\s*[aA]cademy/";
$codecademy = "Codecademy";
 
echo preg_replace($pattern, $codecademy, $one);
// Prints: Codecademy
 
echo preg_replace($pattern, $codecademy, $two);
// Prints: Codecademy
 
echo preg_replace($pattern, $codecademy, $three);
// Prints: Codecademy
 
echo preg_replace($pattern, $codecademy, $four);
// Prints: Codecademy
```

#### Rerouting
So far, we’ve been sending the users back to the same form whether there were errors in their submission or not. We’ve indicated the form was successfully submitted by conditionally displaying a message, but this isn’t always a great user experience. Think of what happens when you log in to your email. Usually, once a form has been submitted successfully, the user is rerouted to an entirely different page.

We can use the [PHP `header()` function](https://www.php.net/manual/en/function.header.php) to perform redirects. We call the `header()` function on a string that begins with `"Location: "`, followed by the URL we want to redirect the user to. For example: `"Location: https://www.best-puppy-pix.com/"`. After invoking the `header()` function we’ll want to use the language construct `exit` to terminate the current script.

To work properly, the `header()` function needs to be run before anything is output by the script—this includes HTML. So we’ll include it in our PHP script before our file outputs any HTML:

```php
if (/* Is the submission data validated? */) {
  header("Location: https://www.best-puppy-pix.com/");
  exit;
}
```

#### Review
- Performing back-end _form validations_ on the data submitted is an essential step to protect our website and its users.
- Using the POST `method` attribute in an HTML form gives our PHP script access to data submitted within the superglobal associative array: `$_POST`.
- We modify our HTML and PHP so that when input is deemed invalid, meaningful feedback is shown to the user.
- If we plan on displaying user input, we need to first _sanitize_ it. We can use methods like `trim()` and `htmlspecialchars()` for basic sanitization.
- We can use `filter_var()` with a filter to sanitize common input types.
- We can also use `filter_var()` with a filter to perform validations on common input types.
- We’ll often want to perform custom validations.
- The `preg_match()` function compares checks if a given string matches a regular expression.
- Since regular expression comparisons can consume a lot of computing power, we’ll want to check the length of inputs before performing regular expression checks.
- It’s common to perform validations by comparing user input to back-end data
- Before storing user input in our back-end, we’ll sanitize it for both safety and consistent formatting
- If a user’s form submission has been accepted, we can reroute them to a different page.


# PHP Classes and Objects
## PHP Classes and Objects
### Classes and Objects

#### What are Classes?
To define a `Pet` class, we use the `class` keyword followed by the class name (typically title cased in PHP) and curly brackets:

```php
class Pet {
 
}
```

Within the curly brackets, we can add _properties_, which define the data each object of the class will contain.

```php
class Pet {
  public $name, $color;
}
```

Note: The `public` keyword has to do with something called visibility.

#### Instantiating
Since objects are specific instances of a class, the process of creating them is called _instantiation_.

In PHP, objects are instantiated using the `new` keyword followed by the class name and parentheses.

```php
$very_good_dog = new Pet();
```

We interact with an object’s properties using the _object operator_ (`->`) followed by the name of the property (without the dollar sign, `$`).

We can use this syntax to assign values to object properties:

```php
$very_good_dog->name = "Lassie";
```

We can also use it to access the existing value of object properties:

```php
echo $very_good_dog->name; # Prints "Lassie"
```

#### Methods
In addition to properties, we can define class methods – essentially functions each object will contain. Methods are frequently used to interact with an object’s properties in a defined manner.

Methods are defined with the same syntax we use when declaring functions (except they are defined within the curly brackets of a class).

Given a `Pet` class with `first` and `last` name properties, we could provide a method which returns the two properties combined into a full name:

```php
class Pet {
  public $first, $last;
  function getFullName() {
    return $this->first . " " . $this->last;
  }
}
```

The `$this` variable refers to the current object; when we invoke this method, `$this` refers to the specific object that called the method.

Methods are accessed in a similar fashion to properties, using the object operator (`->`), but in order to invoke them, use parentheses at the end:

```php
$my_object->classMethod();
```

So, to access the full name of our `Pet`, we can use the following:

```php
$very_good_groundhog = new Pet();
$very_good_groundhog->first = "Punxsutawney";
$very_good_groundhog->last = "Phil";
echo $very_good_groundhog->getFullName(); # Prints "Punxsutawney Phil"
```

#### Constructor Method
A constructor method is one of several [magic methods](https://www.php.net/manual/en/language.oop5.magic.php) provided by PHP. This method is automatically called when an object is instantiated. A constructor method is defined with the special method name `__construct`.

As an example, if we wanted to initialize the `deserves_love` property assigned to `TRUE` for every instance of the `Pet` class, we could use the following constructor:

```php
class Pet {
  public $deserves_love;
  function __construct() {
    $this->deserves_love = TRUE;
  }
}
$my_dog = new Pet();
if ($my_dog->deserves_love){
  echo "I love you!";
}
// Prints: I love you!
```

Constructors can also have parameters. These correspond to arguments passed in when using the `new` keyword. For example, maybe we want to allow for setting the `name` of the `Pet` on instantiation:

```php
class Pet {
  public $name;
  function __construct($name) {
    $this->name = $name;
  }
} 
$dog = new Pet("Lassie");
echo $dog->name; // Prints: Lassie
```

Keep in mind that the number of arguments used when instantiating the object must match the number of parameters in the constructor definition otherwise PHP will throw an error.
 
#### Inheritance
Imagine we wanted a `Dog` class in our program. This class would have all the properties of the more general `Pet` class, but it would have a few more properties and methods specific to only dogs. Rather than having to manually duplicate the things the two classes have in common, we can create a new class which **extends** the other. The original class can be thought of as the _parent_ and the new class can be thought of as the _child_ class. In object oriented programming, we call this process _inheritance_ since the child class _inherits_ properties and methods from its parent class. A child class is also referred to as a _subclass_ in PHP.

To define a class that inherits from another, we use the keyword `extends`:

```php
class ChildClass extends ParentClass {
 
}
```

Let’s define a `Dog` class that extends our `Pet` class. Each `Dog` instance will have an additional method called `bark()`:

```php
class Dog extends Pet {
  function bark() {
    return "woof";
  }
}
```

Now, objects of class `Dog` can `bark`, but objects of `Pet` cannot. This makes sense here, because most dogs can bark, but not all pets can.

#### Overriding Methods
Sometimes, we want to change how methods behave for subclasses from the original parent definition. This is called _overriding_ a method. To do this, define a new method within the subclass with the same name as the parent method.

For example, our `Pet` class might have a `type()` method:

```php
class Pet {
  function type() {
    return "pet";
  }
}
```

But in our `Dog` class, we want to update this message:

```php
class Dog extends Pet{
  function whatIsThis() {
    return "dog";
  }
}
```

We can call the parent’s definition of the method within the subclass using `parent::` followed by the method name:

```php
class Dog extends Pet{
  function type() {
    return "dog";
  }
  function classify(){
    echo "This " . parent::type() . " is of type " . $this->type();
    // Prints: This pet is of type dog 
  }
}
```

#### Visibility - Private Members
To understand visibility we need to think about how classes will be used in complex programs—in large applications, a class might be used in diverse situations (passed around inside functions and used in code written by numerous developers). When we think about our classes being used in many situations, we’ll want to consider restricting access to certain member data.

Up to this point, we’ve been using `public` visibility for properties. This is also the default visibility for methods. A `public` visibility means members can be accessed from within the object **or** from outside it. But sometimes we’ll want a member to only be accessible from within the object. To do this, we can declare this member `private`.

```php
class Pet {
  private $healthScore = 0; 
  function exercise(){
    $this->healthScore++;
  }
  function feed(){
    $this->healthScore++;
  }
  function healthCheck(){
    if ($this->healthScore >= 2){
      echo "This is a healthy pet!";
    } else {
      echo "This is an unhealthy pet";
    }
  }
}
```

The `healthScore` property can be manipulated and accessed by member methods, but since we never want the property to be accessed directly outside of the class, we set the property as `private`. If an attempt is made to access the property directly, our code will raise a `Fatal Error`.

#### Visibility - Protected Members
A class’s `private` members can **only** be accessed using methods within that class itself. This isn’t usually the desired effect when we have subclasses. For example, the following code will throw a `Fatal Error`, since `healthScore` is private to the `Pet` class and can’t be accessed from the `Horse` class:

```php
class Pet {
  private $healthScore = 0; 
}
 
class Horse extends Pet {
  function brushTeeth() {
    $this->healthScore++; 
  }
}
 
$my_pet = new Horse();
$my_pet->brushTeeth(); // Error
```

To allow members to be accessed from within child classes, we can set the visibility within the parent class to `protected` rather than `private`. This enables child classes to access these properties and methods internally while still preventing them from being accessed externally:

```php
class Pet {
  protected $healthScore = 0; 
}
 
class Horse extends Pet {
  function brushTeeth() {
    $this->healthScore++; 
  }
}
 
$my_pet = new Horse();
$my_pet->brushTeeth(); // Successfully increments healthScore
$my_pet->healthScore; // Error
```

#### Getters and Setters
The concept of only accessing properties through methods is commonly referred to as using _getters_ and _setters_.

```php
class Pet {
  private $name;
  function setName($name) {
    $this->name = $name;
  }
  function getName() {
    return $this->name;
  }
}
```

This is the most basic way of using getters and setters in PHP. Initially, it may look like it adds little value over making properties `public` and accessing them directly. But what if we only want to accept a string when setting the name of a `Pet`?

We can add logic to the setter to ensure that the value being passed in is formatted properly:

```php
function setName($name) {
  if (gettype($name) === "string") {
    $this->name = $name;
    return true;
  } else {
    return false;
  }
}
```

We added return values to the setter to provide some feedback as to whether the call to `setName` was successful.

We can also use the getter to format values as they are passed out of the object. In this example, we are capitalizing the first letter of the `Pet` name:

```php
function getName() {
  return ucfirst($this->name);
}
```

#### Static Members
Instantiating objects is the most common way to use classes and is also the most in-line with OOP principles. Sometimes though, it can be useful to group a set of utility functions and variables together into a single class. Since these don’t change for every instance, we don’t need to instantiate them. We can use them _statically_.

When a member is intended to be used statically, we add the keyword `static` to its definition.

```php
class StringUtils {
  public static $max_number_of_characters = 80;
  public static function uclast($string) {
    $string[strlen($string)-1] = strtoupper($string[strlen($string)-1]);
    return $string;
  }
}
```

Accessing these `static` members is done a little differently than with objects. We need to use the [Scope Resolution Operator](https://www.php.net/manual/en/language.oop5.paamayim-nekudotayim.php) (`::`). This can be thought of as switching briefly into the scope of the class itself. Since we are inside the scope, we access properties with the dollar sign.

```php
echo StringUtils::$max_number_of_characters; # Prints "80"
```

Methods are accessed by using the method name:

```php
echo StringUtils::uclast("hello world"); # Prints "hello worlD"
```

#### Review
- Classes are defined using the `class` keyword.
- Functions defined within a class become methods and variables within the class are considered properties.
- There are three levels of visibility for class members:
    - `public` (default) - accessible from outside of the class
    - `protected` - only accessible within the class or its descendants
    - `private` - only accessible within the defining class
- Members can be defined to be `static`.
    - Static members are accessed using the Scope Resolution Operator (`::`).
- Classes are instantiated into objects using the `new` keyword.
    - Members of an object are accessed using the Object Operator (`->`).


# Cheatsheets
## PHP Variables, Strings, and Numbers

### Getting Started with PHP
![[php_getting_started_with_php.pdf]]

### Learn PHP Variables, Strings, and Numbers
![[php_variables_strings_and_numbers.pdf]]

## PHP Functions
### Introduction to Functions in PHP
![[php_introduction_to_functions_in_php.pdf]]

### PHP Built-in Functions
![[php_builtin_functions.pdf]]

## PHP Conditionals and Logic
### Booleans and Comparison Operators in PHP
![[php_booleans_and_comparison_operators_in_php.pdf]]

### Logical Operators and Compound Conditions in PHP
![[php_logical_operators_and_compound_conditions_in_php.pdf]]

## PHP Arrays and Loops
### PHP Arrays
![[php_arrays.pdf]]

### PHP Loops
![[php_loops.pdf]]

## PHP and HTML
### PHP and HTML
![[php_php_and_html.pdf]]

### PHP Form Handling
![[php_php_form_handling.pdf]]

### PHP Form Validation
![[php_php_form_validation.pdf]]