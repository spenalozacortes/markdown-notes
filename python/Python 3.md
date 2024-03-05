# Hello World
## Hello World

### Comments
Text written in a program but not run by the computer is called a comment. Python interprets anything after a `#` as a comment.

Comments can:

- Provide context for why something is written the way it is:

```python
# This variable will be used to count the number of times anyone tweets the word persnickety
persnickety_count = 0
```

- Help other people reading the code understand it faster:

```python
# This code will calculate the likelihood that it will rain tomorrow
complicated_rain_calculation_for_tomorrow()
```

- Ignore a line of code and see how a program will run without it:

```python
# useful_value = old_sloppy_code()
useful_value = new_clean_code()
```

### Print
In Python, the `print()` function is used to tell a computer to talk. The message to be printed should be surrounded by quotes:

```python
# from Mary Shelley's Frankenstein
print("There is something at work in my soul, which I do not understand.")
```

### Strings
Computer programmers refer to blocks of text as strings. In Python a string is either surrounded by double quotes (`"Hello world"`) or single quotes (`'Hello world'`). It doesn’t matter which kind you use, just be consistent.

### Variables
Programming languages offer a method of storing data for reuse. In Python, we assign variables by using the equals sign (`=`).

```python
message_string = "Hello there"
# Prints "Hello there"
print(message_string)
```

Variables can’t have spaces or symbols in their names other than an underscore (`_`). They can’t begin with numbers but they can have numbers after the first letter (e.g., `cool_variable_5` is OK).

```python
# Greeting
message_string = "Hello there"
print(message_string)
 
# Farewell
message_string = "Hasta la vista"
print(message_string)
```

### Errors
Two common errors that we encounter while writing Python are `SyntaxError` and `NameError`.

- `SyntaxError` means there is something wrong with the way your program is written — punctuation that does not belong, a command where it is not expected, or a missing parenthesis can all trigger a `SyntaxError`.
- A `NameError` occurs when the Python interpreter sees a word it does not recognize. Code that contains something that looks like a variable but was never defined will throw a `NameError`.

### Numbers
Python has a few numeric data types. 

An *integer*, or `int`, is a whole number. It has no decimal point and contains all counting numbers (1, 2, 3, …) as well as their negative counterparts and the number 0. 

A *floating-point number*, or a `float`, is a decimal number. It can be used to represent fractional quantities as well as precise measurements.

```python
an_int = 2
a_float = 2.1
 
print(an_int + 3)
# Output: 5
```

We call the number 3 here a *literal*, meaning it’s actually the number 3 and not a variable with the number 3 assigned to it.

### Calculations
Python performs the arithmetic operations of addition, subtraction, multiplication, and division with `+`, `-`, `*`, and `/`.

```python
# Prints "500"
print(573 - 74 + 1)
 
# Prints "50"
print(25 * 2)
 
# Prints "2.0"
print(10 / 5)
```

Notice that when we perform division, the result has a decimal place. This is because Python converts all `int`s to `float`s before performing division. In older versions of Python (2.7 and earlier) this conversion did not happen, and integer division would always round down to the nearest integer.

Division can throw its own special error: `ZeroDivisionError`. Python will raise this error when attempting to divide by 0.

Mathematical operations in Python follow the standard mathematical order of operations.

### Changing Numbers
Performing arithmetic on variables does not change the variable — you can only update a variable using the `=` sign.

```python
coffee_price = 1.50
number_of_coffees = 4
 
# Prints "6.0"
print(coffee_price * number_of_coffees)
# Prints "1.5"
print(coffee_price)
# Prints "4"
print(number_of_coffees)
 
# Updating the price 
coffee_price = 2.00
 
# Prints "8.0"
print(coffee_price * number_of_coffees)
# Prints "2.0"
print(coffee_price)
# Prints "4"
print(number_of_coffees)
```

### Exponents
Python can also perform exponentiation. Since this operation is so related to multiplication, we use the notation `**`.

```python
# 2 to the 10th power, or 1024
print(2 ** 10)
 
# 8 squared, or 64
print(8 ** 2)
 
# 9 * 9 * 9, 9 cubed, or 729
print(9 ** 3)
 
# We can even perform fractional exponents
# 4 to the half power, or 2
print(4 ** 0.5)
```

### Modulo
The modulo operator is indicated by `%` and gives the remainder of a division calculation. If the number is divisible, then the result of the modulo operator will be 0.

```python
# Prints 4 because 29 / 5 is 5 with a remainder of 4
print(29 % 5)
 
# Prints 2 because 32 / 3 is 10 with a remainder of 2
print(32 % 3)
 
# Modulo by 2 returns 0 for even numbers and 1 for odd numbers
# Prints 0
print(44 % 2)
```

The modulo operator is useful in programming when we want to perform an action every nth-time the code is run.

### Concatenation
The `+` operator doesn’t just add two numbers, it can also “add” two strings! The process of combining two strings is called string concatenation. Performing string concatenation creates a brand new string comprised of the first string’s contents followed by the second string’s contents (without any added space in-between).

```python
greeting_text = "Hey there!"
question_text = "How are you doing?"
full_text = greeting_text + question_text
 
# Prints "Hey there!How are you doing?"
print(full_text)
```

Let’s add the space in-between using the same concatenation operator!

```python
full_text = greeting_text + " " + question_text
 
# Prints "Hey there! How are you doing?"
print(full_text)
```

If you want to concatenate a string with a number you will need to make the number a string first, using the `str()` function. If you’re trying to `print()` a numeric variable you can use commas to pass it as a different argument rather than converting it to a string.

```python
birthday_string = "I am "
age = 10
birthday_string_2 = " years old today!"
 
# Concatenating an integer with strings is possible if we turn the integer into a string first
full_birthday_string = birthday_string + str(age) + birthday_string_2
 
# Prints "I am 10 years old today!"
print(full_birthday_string)
 
# If we just want to print an integer 
# we can pass a variable as an argument to 
# print() regardless of whether 
# it is a string.
 
# This also prints "I am 10 years old today!"
print(birthday_string, age, birthday_string_2)
```

### Plus Equals
Python offers a shorthand for updating variables. When you have a number saved in a variable and want to add to the current value of the variable, you can use the `+=` (plus-equals) operator.

```python
# First we have a variable with a number saved
number_of_miles_hiked = 12
 
# Then we need to update that variable
# Let's say we hike another two miles today
number_of_miles_hiked += 2
 
# The new value is the old value
# Plus the number after the plus-equals
print(number_of_miles_hiked)
# Prints 14
```

The plus-equals operator also can be used for string concatenation.

```python
hike_caption = "What an amazing time to walk through nature!"
 
# Almost forgot the hashtags!
hike_caption += " #nofilter"
hike_caption += " #blessed"
```

### Multi-line Strings
Python strings are very flexible, but if we try to create a string that occupies multiple lines we find ourselves face-to-face with a `SyntaxError`. Python offers a solution: multi-line strings. By using three quote-marks (`"""` or `'''`) instead of one, we tell the program that the string doesn’t end until the next triple-quote. This method is useful if the string being defined contains a lot of quotation marks and we want to be sure we don’t close it prematurely.

```python
leaves_of_grass = """
Poets to come! orators, singers, musicians to come!
Not to-day is to justify me and answer what I am for,
But you, a new brood, native, athletic, continental, greater than
  before known,
Arouse! for you must justify me.
"""
```

If a multi-line string isn’t assigned a variable or used in an expression it is treated as a comment.

## User Input
While we output a variable’s value using `print()`, we assign information to a variable using `input()`. The `input()` function requires a prompt message, which it will print out for the user before they enter the new information.

```python
likes_snakes = input("Do you like snakes? ")
```


# Control Flow
## Control Flow

### Boolean Expressions
A boolean expression is a statement that can either be `True` or `False`.

### Relational Operators: Equals and Not Equals
We can create a boolean expression by using *relational operators*.

Relational operators compare two items and return either `True` or `False`. For this reason, you will sometimes hear them called *comparators*.

- Equals: `==`
- Not equals: `!=`

These operators compare two items and return `True` or `False` if they are equal or not.

```python
1 == 1     # True
 
2 != 4     # True
 
3 == 5     # False
 
'7' == 7   # False
```

When using relational operators it is important to always be mindful of type.

### Boolean Variables
`True` and `False` are the only `bool` types, and any variable that is assigned one of these values is called a *boolean variable*.

### If Statement
Understanding boolean variables and expressions is essential because they are the building blocks of *conditional statements*.

```python
if is_raining:
  print("bring an umbrella")
  ```

### Relational Operators II
- `>` greater than
- `>=` greater than or equal to
- `<` less than
- `<=` less than or equal to

### Boolean Operators: and
Often, the conditions you want to check in your conditional statement will require more than one boolean expression to cover. In these cases, you can build larger boolean expressions using *boolean operators*. These operators (also known as *logical operators*) combine smaller boolean expressions into larger boolean expressions.

- `and`
- `or`
- `not`

`and` combines two boolean expressions and evaluates as `True` if both its components are `True`, but `False` otherwise.

```python
(1 + 1 == 2) and (2 + 2 == 4)   # True
 
(1 > 9) and (5 != 6)            # False
 
(1 + 1 == 2) and (2 < 1)        # False
 
(0 == 10) and (1 + 1 == 1)      # False
```

### Boolean Operators: or
The boolean operator `or` combines two expressions into a larger expression that is `True` if either component is `True`.

```python
True or (3 + 4 == 7)    # True
(1 - 1 == 0) or False   # True
(2 < 0) or True         # True
(3 == 8) or (3 > 4)     # False
```

### Boolean Operators: not
This operator is straightforward: when applied to any boolean expression it reverses the boolean value. So if we have a `True` statement and apply a `not` operator we get a `False` statement.

```python
not True == False
not False == True
not 1 + 1 == 2  # False
not 7 < 0       # True
```

### Else Statements
`else` statements allow us to elegantly describe what we want our code to do when certain conditions are **not** met.

`else` statements always appear in conjunction with `if` statements. 

```python
if weekday:
  print("wake up at 6:30")
else:
  print("sleep in")
  ```

### Else If Statements
An `elif` statement checks another condition after the previous `if` statements conditions aren’t met.

We can use `elif` statements to control the order we want our program to check each of our conditional statements. First, the `if` statement is checked, then each `elif` statement is checked from top to bottom, then finally the `else` code is executed if none of the previous conditions have been met.

```python
print("Thank you for the donation!")
 
if donation >= 1000:
  print("You've achieved platinum status")
elif donation >= 500:
  print("You've achieved gold donor status")
elif donation >= 100:
  print("You've achieved silver donor status")
else:
  print("You've achieved bronze donor status")
```

### Review
- Boolean expressions are statements that can be either `True` or `False`
- A boolean variable is a variable that is set to either `True` or `False`
- We can create boolean expressions using relational operators:
	- `==`: Equals
	- `!=`: Not equals
	- `>`: Greater than
	- `>=`: Greater than or equal to
	- `<`: Less than
	- `<=`: Less than or equal to
- `if` statements can be used to create control flow in your code.
- `else` statements can be used to execute code when the conditions of an `if` statement are not met.
- `elif` statements can be used to build additional checks into your `if` statements

## Errors in Python

### Introduction to bugs
Python refers to the mistakes within the program as *errors* and will point to the location where an error occurred with a `^` character. When programs throw errors that we didn’t expect to encounter, we call those errors *bugs*. Programmers call the process of updating the program so that it no longer produces bugs *debugging*.

In Python, there are many different ways of classifying errors, but here are some common ones:

- `SyntaxError`: Error caused by not following the proper structure (syntax) of the language.
- `NameError`: Errors reported when the interpreter detects a variable that is unknown.
- `TypeError`: Errors thrown when an operation is applied to an object of an inappropriate type.

### Syntax Errors
`SyntaxError` means there is something wrong with the way your program is written — punctuation that does not belong, a command where it is not expected, or a missing parenthesis can all trigger a `SyntaxError`.

```
File "script.py", line 1
  print(Hello world!)
                  ^
SyntaxError: invalid syntax
```

The interpreter will tell us where (the file name and line number) it got into trouble and its best guess as to what is wrong.

Some common syntax errors are:

- Misspelling a Python keyword.
- Missing colon `:`.
- Missing closing parenthesis `)`, square bracket `]`, or curly brace `}`.

### Name Errors
A `NameError` is reported by the Python interpreter when it detects a variable that is unknown.

This can occur if a variable is used before it has been assigned a value or if a variable name is spelled differently than the point at which it was defined.

```
File "script.py", line 1, in <module>
    print(score)
NameError: name 'score' is not defined
```

Some common name errors are:

- Misspelling a variable name.
- Forgetting to define a variable.

### Type Errors
A `TypeError` is reported by the Python interpreter when an operation is applied to a variable of an inappropriate type.

This can occur in Python when one attempts to use an operator on something of the incorrect type.

```
Traceback (most recent call last):
  File "script.py", line 1, in <module>
    piggy_bank = '2' + 0.25
TypeError: must be str, not float
```

Some common type errors are:

- Accidentally adding or subtracting a string value.
- Call a function on something of the incorrect type.

### Review
- `SyntaxError`: Error caused by not following the proper structure (syntax) of the language.
- `NameError`: Errors reported when the interpreter detects an object that is unknown.
- `TypeError`: Errors thrown when an operation is applied to an object of an inappropriate type.


# Lists
## Introduction to Lists

### What is a List?
In Python, a *list* is one of the many built-in data structures that allows us to work with a collection of data in sequential order.

```python
heights = [61, 70, 67, 64]
```

### What can a List contain?
Lists can contain more than just numbers.

```python
names = ["Noelle", "Ava", "Sam", "Mia"]
```

We can even combine multiple data types in one list. 

```python
mixed_list_string_number = ["Noelle", 61]
```

### Empty Lists
A list doesn’t have to contain anything.

```python
empty_list = []
```

### List Methods
In Python, for any specific data-type ( strings, booleans, lists, etc. ) there is built-in functionality that we can use to create, manipulate, and even delete our data. We call this built-in functionality a *method*.

For lists, methods will follow the form of `list_name.method()`. Some methods will require an input value that will go between the parenthesis of the method `( )`.

An example of a popular list method is `.append()`, which allows us to add an element to the end of a list.

```python
append_example = [ 'This', 'is', 'an', 'example']
append_example.append('list')
```

### Growing a List: Plus (+)
When we want to add multiple items to a list, we can use `+` to combine two lists (this is also known as concatenation).

```python
items_sold = ["cake", "cookie", "bread"]
items_sold_new = items_sold + ["biscuit", "tart"]
print(items_sold_new)
```

We can only use `+` with other lists. If we want to add a single element using `+`, we have to put it into a list with brackets `([])`:

```python
my_list + [4]
```

### Accessing List Elements
In Python, we call the location of an element in a list its *index*.

Python lists are *zero-indexed*. This means that the first element in a list has index `0`, rather than `1`.

We can select a single element from a list by using square brackets (`[]`) and the index of the list item. 

```python
print(calls[2])
```

Note: When accessing elements of a list, you *must* use an `int` as the index. If you use a `float`, you will get an error. This can be especially tricky when using division.

To solve this problem, you can force the result of your division to be an `int` by using the `int()` function. `int()` takes a number and cuts off the decimal point. 

Selecting an element that does not exist produces an `IndexError`.

### Accessing List Elements: Negative Index
We can use the index `-1` to select the last item of a list, even when we don’t know how many elements are in a list.

```python
print(pancake_recipe[-1])
```

### Modifying List Elements
To change a value in a list, reassign the value using the specific index.

```python
garden[2] = "Strawberries"
```

### Shrinking a List: Remove
We can remove elements in a list using the `.remove()` Python method.

```python
shopping_line.remove("Chris")
```

We can also use `.remove()` on a list that has duplicate elements.

Only the first instance of the matching element is removed:

```python
# Create a list
shopping_line = ["Cole", "Kip", "Chris", "Sylvana", "Chris"]
 
# Remove a element
shopping_line.remove("Chris")
print(shopping_line) # ["Cole", "Kip", "Sylvana", "Chris"]
```

When we call `.remove()` on a list with a value that does not exist, we will receive a `ValueError`.

### Two-Dimensional (2D) Lists
Lists can contain other lists! We will commonly refer to these as *two-dimensional (2D)* lists.

```python
heights = [["Noelle", 61], ["Ava", 70], ["Sam", 67], ["Mia", 64]]
```

### Accessing 2D Lists
Two-dimensional lists can be accessed similar to their one-dimensional counterpart. Instead of providing a single pair of brackets `[ ]` we will use an additional set for each dimension past the first.

```python
#Access the sublist at index 0, and then access the 1st index of that sublist. 
noelles_height = heights[0][1] 
```

### Modifying 2D Lists
To change a value in a two-dimensional list, reassign the value using the specific index.

```python
# The list of Jenny is at index 0. The hobby is at index 1. 
class_name_hobbies[0][1] = "Meditation"
```

Negative indices will work as well.

```python
# The list of Grace is the last entry. The hobby is the last element. 
class_name_hobbies[-1][-1] = "Football"
```

### Project: Gradebook
You are a student and you are trying to organize your subjects and grades using Python. Let’s explore what we’ve learned about lists to organize your subjects and scores.

```python
last_semester_gradebook = [["politics", 80], ["latin", 96], ["dance", 97], ["architecture", 65]]

# Your code below: 
subjects = ["physics", "calculus", "poetry", "history"]
grades = [98, 97, 85, 88]
gradebook = [["physics", 98], ["calculus", 97], ["poetry", 85], ["history", 88]]

gradebook.append(["computer science", 100])
gradebook.append(["visual arts", 93])

gradebook[-1][-1] = 98

gradebook[-1].remove(98)
gradebook[-1].append("Pass")

full_gradebook = last_semester_gradebook + gradebook

print(full_gradebook)
```


## Working with Lists in Python

### Adding by Index: Insert
The Python list method `.insert()` allows us to add an element to a specific index in a list.

The `.insert()` method takes in two inputs:

1. The index you want to insert into.
2. The element you want to insert at the specified index.

The `.insert()` method will handle shifting over elements and can be used with negative indices.

```python
store_line = ["Karla", "Maxium", "Martim", "Isabella"]
store_line.insert(2, "Vikor")
print(store_line) #  ['Karla', 'Maxium', 'Vikor', 'Martim', 'Isabella']
```

### Removing by Index: Pop
Python gives us a method to remove elements at a specific index using a method called `.pop()`.

The `.pop()` method takes an optional single input:

1. The index for the element you want to remove.

```python
cs_topics = ["Python", "Data Structures", "Balloon Making", "Algorithms", "Clowns 101"]
removed_element = cs_topics.pop()
print(cs_topics) # ['Python', 'Data Structures', 'Balloon Making', 'Algorithms']
print(removed_element) # 'Clowns 101'
cs_topics.pop(2)
print(cs_topics) # ['Python', 'Data Structures', 'Algorithms']
```

Using `.pop()` without an index will remove whatever the last element of the list is. 

`.pop()` is unique in that it will return the value that was removed. If we wanted to know what element was deleted, simply assign a variable to the call of the `.pop()` method.

We don’t have to save the removed value to any variable if we don’t care to use it later.

Note: Passing in an index that does not exist or calling `.pop()` on an empty list will both result in an `IndexError`.

### Consecutive Lists: Range
Often, we want to create a list of consecutive numbers in our programs. Python gives us an easy way of creating these types of lists using a built-in function called `range()`.

The function `range()` takes a single input, and generates numbers starting at `0` and ending at the number **before** the input.

So, if we want the numbers from 0 through 9, we use `range(10)` because 10 is 1 greater than 9:

```python
my_range = range(10)
print(my_range) # range(0, 10)
```

The `range()` function is unique in that it creates a *range object*.

In order to use this object as a list, we have to first convert it using another built-in function called `list()`.

The `list()` function takes in a single input for the object you want to convert.

```python
print(list(my_range)) # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### The Power of Range!
By default, `range()` creates a list starting at `0`. However, if we call `range()` with two inputs, we can create a list that starts at a different number.

```python
my_list = range(2, 9)
print(list(my_list)) # [2, 3, 4, 5, 6, 7, 8]
```

If we use a third input, we can create a list that “skips” numbers.

```python
my_range2 = range(2, 9, 2)
print(list(my_range2)) # [2, 4, 6, 8]
```

### Length
Often, we’ll need to find the number of items in a list, usually called its *length*. 

We can do this using a built-in function called `len()`.

When we apply `len()` to a list, we get the number of elements in that list:

```python
my_list = [1, 2, 3, 4, 5]
 
print(len(my_list)) # 5
```

Note: Range objects do not need to be converted to lists in order to determine their length.

### Slicing Lists I
In Python, often we want to extract only a portion of a list. Dividing a list in such a manner is referred to as *slicing*.

```python
letters = ["a", "b", "c", "d", "e", "f", "g"]
```

Suppose we want to select from `"b"` through `"f"`.

We can do this using the following syntax: `letters[start:end]`, where:

- `start` is the index of the first element that we want to include in our selection.
- `end` is the index of *one more than* the last index that we want to include.

```python
sliced_list = letters[1:6]
print(sliced_list) # ["b", "c", "d", "e", "f"]
```

### Slicing Lists II
If we want to select the *first n elements* of a list, we could use the following code: `fruits[:n]`

The following code would start slicing from index 0 and up to index 3. Note that the fruit at index 3 (`orange`) is not included in the results.

```python
fruits = ["apple", "cherry", "pineapple", "orange", "mango"]
print(fruits[:3]) # ['apple', 'cherry', 'pineapple']
```

We can do something similar when we want to slice the *last n elements* in a list: `fruits[-n:]`

```python
print(fruits[-2:]) # ['orange', 'mango']
```

Negative indices can also accomplish taking *all but n last elements* of a list: `fruits[:-n]`

```python
print(fruits[:-1]) # ['apple', 'cherry', 'pineapple', 'orange']
```

### Counting in a List
In Python, it is common to want to count occurrences of an item in a list.

```python
letters = ["m", "i", "s", "s", "i", "s", "s", "i", "p", "p", "i"]
```

If we want to know how many times i appears in this word, we can use the list method called `.count()`:

```python
num_i = letters.count("i")
print(num_i) # 4
```

Notice that since `.count()` *returns* a value, we can assign it to a variable to use it.

We can even use `.count()` to count element appearances in a two-dimensional list.

```python
number_collection = [[100, 200], [100, 200], [475, 29], [34, 34]]
num_pairs = number_collection.count([100, 200])
print(num_pairs) # 2
```

### Sorting Lists I
Often, we will want to sort a list in either numerical (1, 2, 3, …) or alphabetical (a, b, c, …) order.

We can sort a list using the method `.sort()`.

```python
names = ["Xander", "Buffy", "Angel", "Willow", "Giles"]
names.sort()
print(names) # ['Angel', 'Buffy', 'Giles', 'Willow', 'Xander']
```

`.sort()` also provides us the option to go in reverse.

```python
names.sort(reverse=True)
print(names) # ['Xander', 'Willow', 'Giles', 'Buffy', 'Angel']
```

**Note**: The `.sort()` method does not return any value and thus does not need to be assigned to a variable since it modifies the list directly. If we do assign the result of the method, it would assign the value of `None` to the variable.

When sorting a two-dimensional list using `.sort()`, the list by default will be sorted by the first element in each sublist.

### Sorting Lists II
A second way of sorting a list in Python is to use the built-in function `sorted()`.

The `sorted()` function is different from the `.sort()` method in two ways:

1. It comes *before* a list, instead of after as all built-in functions do.
2. It generates a new list rather than modifying the one that already exists.

```python
names = ["Xander", "Buffy", "Angel", "Willow", "Giles"]
sorted_names = sorted(names)
print(sorted_names) # ['Angel', 'Buffy', 'Giles', 'Willow', 'Xander']
```

Note that using `sorted` did not change `names`.

### Review
- Add elements to a list by index using the `.insert()` method.
- Remove elements from a list by index using the `.pop()` method.
- Generate a list using the `range()` function.
- Get the length of a list using the `len()` function.
- Select portions of a list using slicing syntax.
- Count the number of times that an element appears in a list using the `.count()` method.
- Sort a list of items using either the `.sort()` method or `sorted()` function.

### Project: Len's Slice
You work at Len’s Slice, a new pizza joint in the neighborhood. You are going to use your knowledge of Python lists to organize some of your sales data.

```python
# Your code below:
toppings = ["pepperoni", "pineapple", "cheese", "sausage", "olives", "anchovies", "mushrooms"]
prices = [2, 6, 1, 3, 2, 7, 2]

num_two_dollar_slices = prices.count(2)

num_pizzas = len(toppings)
print("We sell " + str(num_pizzas) + " different kinds of pizza!")

pizza_and_prices = [[2, "pepperoni"], [6, "pineapple"], [1, "cheese"], [3, "sausage"], [2, "olives"], [7, "anchovies"], [2, "mushrooms"]]

pizza_and_prices.sort()

cheapest_pizza = pizza_and_prices[0]
priciest_pizza = pizza_and_prices[-1]

pizza_and_prices.pop()

pizza_and_prices.insert(4, [2.5, "peppers"])
print(pizza_and_prices)

three_cheapest = pizza_and_prices[:3]
print(three_cheapest)
```

## Combining Lists: The Zip Function
The `zip()` function allows us to quickly combine associated data-sets without needing to rely on multi-dimensional lists. 

Suppose that we already had a list of names and a list of heights:

```python
names = ["Jenny", "Alexus", "Sam", "Grace"]
heights = [61, 70, 67, 64]
```

The `zip()` function takes two (or more) lists as inputs and returns an object that contains a list of pairs. Each pair contains one element from each of the inputs.

```python
names_and_heights = zip(names, heights)
print(names_and_heights) # <zip object at 0x7f1631e86b48>
```

This *zip object* contains the location of this variable in our computer’s memory.

It is fairly simple to convert this object into a usable list by using the built-in function `list()`:

```python
converted_list = list(names_and_heights)
print(converted_list) # [('Jenny', 61), ('Alexus', 70), ('Sam', 67), ('Grace', 64)]
```

Our inner lists don’t use square brackets `[ ]` around the values. This is because they have been converted into *tuples* (an immutable type of list).


# Loops
## Loops

### What are Loops?
In programming, this process of using an initialization, repetitions, and an ending condition is called a *loop*. In a loop, we perform a process of *iteration* (repeating tasks).

Programming languages like Python implement two types of iteration:

1. *Indefinite iteration*, where the number of times the loop is executed depends on how many times a condition is met.
2. *Definite iteration*, where the number of times the loop will be executed is defined in advance (usually based on the collection size).

### For Loops: Introduction
In a `for` loop, we will know in advance how many times the loop will need to iterate because we will be working on a collection with a predefined length. 

With `for` loops, on each iteration, we will be able to perform an action on each element of the collection.

```
for <temporary variable> in <collection>:
  <action>
```

```python
ingredients = ["milk", "sugar", "vanilla extract", "dough", "chocolate"]
 
for ingredient in ingredients:
  print(ingredient)
```

A temporary variable’s name is arbitrary and does not need to be defined beforehand.

Everything at the same level of indentation after the `for` loop declaration is included in the loop body and is run on every iteration of the loop.

If we ever forget to indent, we’ll get an `IndentationError` or unexpected behavior.

Python loves to help us write elegant code so it allows us to write simple `for` loops in one-line.

```python
for ingredient in ingredients: print(ingredient)
```

Note: One-line `for` loops are useful for simple programs. It is not recommended you write one-line loops for any loop that has to perform multiple complex actions on each iteration. Doing so will hurt the readability of your code and may ultimately lead to buggier code.

### For Loops: Using Range
Often we won’t be iterating through a specific list (or any collection), but rather only want to perform a certain action multiple times.

To create arbitrary collections of any length, we can pair our for loops with the trusty Python built-in function `range()`.

```python
for temp in range(6):
  print("Learning Loops!")
```

Something to note is we are not using `temp` anywhere inside of the loop body. If we are curious about which loop iteration (step) we are on, we can use `temp` to track it. Since our range starts at `0`, we will add `+ 1` to our `temp` to represent how many iterations (steps) our loop takes more accurately.

```python
for temp in range(6):
  print("Loop is on iteration number " + str(temp + 1))
```

### While Loops: Introduction
Another type of loop is called a `while` loop and is a form of indefinite iteration.

A `while` loop performs a set of instructions as long as a given condition is true.

```
while <conditional statement>:
  <action>
```

```python
count = 0
while count <= 3:
  # Loop Body
  print(count)
  count += 1
```

Similar to a `for` loop, everything at the same level of indentation after the `while` loop declaration is run on every iteration of the loop while the condition is true.

If we ever forget to indent, we’ll get an `IndentationError` or unexpected behavior.

Similar to `for` loops, Python allows us to write elegant one-line while loops. 

```python
count = 0
while count <= 3: print(count); count += 1
```

Note: Here we separate each statement with a `;` to denote a separate line of code.

If the stop condition for our loop is never met, we will create an infinite loop which stops our program from running anything else.

### While Loops: Lists
Similar to how we saw `for` loops working with lists, we can use `while` loops to iterate through a list as well.

```python
ingredients = ["milk", "sugar", "vanilla extract", "dough", "chocolate"]

length = len(ingredients)
index = 0
 
while index < length:
  print(ingredients[index])
  index += 1
```

### Infinite Loops
A loop that never terminates is called an *infinite loop*. These are very dangerous for our code because they will make our program run forever and thus consume all of your computer’s resources.

### Loop Control: Break
It’s often the case that we want to search a list to check if a specific value exists. What does our loop look like if we want to search for the value of "knit dress" and print out "Found it" if it did exist?

```python
items_on_sale = ["blue shirt", "striped socks", "knit dress", "red headband", "dinosaur onesie"]

for item in items_on_sale:
  if item == "knit dress":
    print("Found it")
```

Once "knit_dress" is found in the list `items_on_sale`, we don’t need to go through the rest of the `items_on_sale` list. Unfortunately, our loop will keep running until we reach the end of the list.

Thankfully you can stop iteration from inside the loop by using `break` loop control statement.

When the program hits a `break` statement it immediately terminates a loop.

```python
items_on_sale = ["blue shirt", "striped socks", "knit dress", "red headband", "dinosaur onesie"]
 
print("Checking the sale list!")
 
for item in items_on_sale:
  print(item)
  if item == "knit dress":
    break
 
print("End of search!")
```

### Loop Control: Continue
While the `break` control statement will come in handy, there are other situations where we don’t want to end the loop entirely. What if we only want to skip the current iteration of the loop?

What if we want to print out all of the numbers in a list, but only if they are positive integers. We can use another common loop control statement called `continue`.

```python
big_number_list = [1, 2, -1, 4, -5, 5, 2, -9]

for i in big_number_list:
  if i <= 0:
    continue
  print(i)
```

Similar to when we were using the `break` control statement, our `continue` control statement is usually paired with some form of a conditional (`if`/`elif`/`else`).

When the loop then encounters a `continue` statement it immediately skips the current iteration and moves onto the next element in the list.

### Nested Loops
Loops can be nested in Python, as they can with other programming languages.

```python
project_teams = [["Ava", "Samantha", "James"], ["Lucille", "Zed"], ["Edgar", "Gabriel"]]

# Loop through each sublist
for team in project_teams:
  # Loop elements in each sublist
  for student in team:
    print(student)
```

### List Comprehensions: Introduction
To start, let’s say we had a list of integers and wanted to create a list where each element is doubled. We could accomplish this using a `for` loop and a new list called `doubled`:

```python
numbers = [2, -1, 79, 33, -45]
doubled = []
 
for number in numbers:
  doubled.append(number * 2)
 
print(doubled) # [4, -2, 158, 66, -90]
```

Here is our same problem but now written as a list comprehension:

```python
numbers = [2, -1, 79, 33, -45]
doubled = [num * 2 for num in numbers]
print(doubled)
```

```
new_list = [<expression> for <element> in <collection>]
```

### List Comprehensions: Conditionals
Suppose we wanted to double only our negative numbers from our previous `numbers` list.

We will start by using a for loop and a list `only_negative_doubled`:

```python
numbers = [2, -1, 79, 33, -45]
only_negative_doubled = []
 
for num in numbers:
  if num < 0: 
    only_negative_doubled.append(num * 2)
 
print(only_negative_doubled) # [-2, -90]
```

Now, here is what our code would look like using a list comprehension:

```python
numbers = [2, -1, 79, 33, -45]
negative_doubled = [num * 2 for num in numbers if num < 0]
print(negative_doubled)
```

We can also use If-Else conditions directly in our comprehensions. For example, let’s say we wanted to double every negative number but triple all positive numbers.

```python
numbers = [2, -1, 79, 33, -45]
doubled = [num * 2 if num < 0 else num * 3 for num in numbers ]
print(doubled) # [6, -2, 237, 99, -90]
```

The placement of the conditional expression within the comprehension is dependent on whether or not an `else` clause is used. When an `if` statement is used without `else`, the conditional must go after `for <element> in <collection>`. If the conditional expression includes an `else` clause, the conditional must go before `for`. Attempting to write the expressions in any other order will result in a `SyntaxError`.

### Project: Carly's Clippers
You are the Data Analyst at Carly’s Clippers, the newest hair salon on the block. Your job is to go through the lists of data that have been collected in the past couple of weeks. You will be calculating some important metrics that Carly can use to plan out the operation of the business for the rest of the month.

You have been provided with three lists:

- `hairstyles`: the names of the cuts offered at Carly’s Clippers.
- `prices`: the price of each hairstyle in the `hairstyles` list.
- `last_week`: the number of purchases for each hairstyle type in the last week.

Each index in `hairstyles` corresponds to an associated index in `prices` and `last_week`.

For example, The hairstyle "bouffant" has an associated price of 30 from the prices list, and was purchased 2 times in the last week as shown in the `last_week` list. Each of these elements are in the first index of their respective lists.

```python
hairstyles = ["bouffant", "pixie", "dreadlocks", "crew", "bowl", "bob", "mohawk", "flattop"]

prices = [30, 25, 40, 20, 20, 35, 50, 35]

last_week = [2, 3, 5, 8, 4, 4, 6, 2]

total_price = 0
for price in prices:
  total_price += price

average_price = total_price / len(prices)
print("Average Haircut Price:", average_price)

new_prices = [price - 5 for price in prices]
print(new_prices)

total_revenue = 0
for i in range(len(hairstyles)):
  total_revenue += prices[i] * last_week[i]
print("Total Revenue:", total_revenue)

average_daily_revenue = total_revenue / 7
print(average_daily_revenue)

cuts_under_30 = [hairstyles[i] for i in range(len(new_prices)) if new_prices[i] < 30]
print(cuts_under_30)
```


# Functions
## Introduction to Functions

### Introduction to Functions
*Functions* are a convenient way to group our code into reusable blocks. A function contains a sequence of steps that can be performed repeatedly throughout a program without having to repeat the process of writing the same code again.

### Defining a Function
Here’s an example of a function definition:

```python
def function_name():
  # functions tasks go here
```

The `def` keyword indicates the beginning of a function (also known as a function header). The function header is followed by a name in snake_case format that describes the task the function performs.

Following the function name is a pair of parenthesis `( )` that can hold input values known as parameters.

Like loops and conditionals, code inside a function must be indented to show that they are part of the function.

```python
def trip_welcome():
  print("Welcome to Tripcademy!") 
  print("Let's get you to your destination.")
```

The `print()` statements within the function will not execute since our function hasn’t been used.

### Calling a Function
The process of executing the code inside the body of a function is known as calling it (This is also known as “executing a function”). To call a function in Python, type out its name followed by parentheses `( )`.

```python
def directions_to_timesSq():
  print("Walk 4 mins to 34th St Herald Square train station.")
  print("Take the Northbound N, Q, R, or W train 1 stop.")
  print("Get off the Times Square 42nd Street stop.")

directions_to_timesSq()
```

Note that you can only call a function *after* it has been defined in your code.

### Whitespace & Execution Flow
In Python, the amount of whitespace tells the computer what is part of a function and what is not part of that function.

Note that the execution of a program always begins on the first line. The code is then executed one line at a time from top to bottom. This is known as *execution flow* and is the order a program in python executes code.

### Parameters & Arguments
Function *parameters* allow our function to accept data as an input value. We list the parameters a function takes as input between the parentheses of a function `( )`.

```python
def trip_welcome(destination):
  print("Welcome to Tripcademy!") 
  print("Looks like you're going to " + destination + " today.")
```

Our parameter of `destination` is used by passing in an *argument* to the function when we call it.

```python
trip_welcome("Times Square")
```

The parameter is the name defined in the parenthesis of the function and can be used in the function body.

The argument is the data that is passed in when we call the function, which is then assigned to the parameter name.

### Multiple Parameters
We can write a function that takes in more than one parameter by using commas:

```python
def trip_welcome(origin, destination):
  print("Welcome to Tripcademy")
  print("Looks like you are traveling from " + origin)
  print("And you are heading to " + destination)
```

When we call our function, we will need to provide arguments for each of the parameters we assigned in our function definition.

The ordering of your parameters is important as their position will map to the position of the arguments and will determine their assigned value in the function body.

```python
trip_welcome("Prospect Park", "Atlantic Terminal")
```

You can also add a `pass` statement inside your empty function and it will prevent the `SyntaxError: unexpected EOF while parsing` error.

### Types of Arguments
In Python, there are 3 different types of arguments we can give a function.

- Positional arguments: arguments that can be called by their position in the function definition.
- Keyword arguments: arguments that can be called by their name.
- Default arguments: arguments that are given default values.

We can use *Keyword Arguments* where we explicitly refer to what each argument is assigned to in the function call. Notice in the code example that the arguments do not follow the same order as defined in the function declaration.

```python
def calculate_taxi_price(miles_to_travel, rate, discount):
  print(miles_to_travel * rate - discount )

calculate_taxi_price(rate=0.5, discount=10, miles_to_travel=100)
```

We can provide a default value to an argument by using the assignment operator (`=`). This will happen in the function declaration rather than the function call.

```python
def calculate_taxi_price(miles_to_travel, rate, discount = 10):
  print(miles_to_travel * rate - discount )
```

When using a default argument, we can either choose to call the function without providing a value for a discount (and thus our function will use the default value assigned) or overwrite the default argument by providing our own:

```python
# Using the default value of 10 for discount.
calculate_taxi_price(10, 0.5)
 
# Overwriting the default value of 10 with 20
calculate_taxi_price(10, 0.5, 20)
```

### Built-in Functions vs User Defined Functions
There are two distinct categories for functions in the world of Python. What we have been writing so far in our exercises are called *User Defined Functions* - functions that are written by users.

There is another category called *Built-in functions* - functions that come built into Python for us to use.

#### max()
Return the largest item in an iterable or the largest of two or more arguments. 

If one positional argument is provided, it should be an iterable.

If multiple items are maximal, the function returns the first one encountered. 

```python
tshirt_price = 9.75
shorts_price = 15.50
mug_price = 5.99
poster_price = 2.00

max_price = max(tshirt_price, shorts_price, mug_price, poster_price)
print(max_price) # 15.5
```

#### min()
Return the smallest item in an iterable or the smallest of two or more arguments.

If one positional argument is provided, it should be an iterable.

If multiple items are minimal, the function returns the first one encountered. 

```python
min_price = min(tshirt_price, shorts_price, mug_price, poster_price)
print(min_price) # 2.0
```

#### round(number, ndigits=None)
Return number rounded to ndigits precision after the decimal point. If ndigits is omitted or is None, it returns the nearest integer to its input.

```python
rounded_price = round(tshirt_price, 1)
print(rounded_price) # 9.8
```

### Variable Access
As we expand our programs with more functions, we might start to ponder, where exactly do we have access to our variables? 

```python
def trip_welcome(destination):
  print(" Looks like you're going to the " + destination + " today. ")
```

What if we wanted to access the variable `destination` outside of the function? Could we use it?

```python
def trip_welcome(destination):
  print(" Looks like you're going to the " + destination + " today. ")
 
print(destination)
```

If we try to run this code, we will get a `NameError`, telling us that `destination` is not defined. The variable `destination` has only been defined inside the space of a function, so it does not exist outside the function.

We call the part of a program where `destination` can be accessed its *scope*. The scope of destination is only inside the `trip_welcome()`.

```python
budget = 1000
 
# Here we are using a default value for our parameter of `destination` 
def trip_welcome(destination="California"):
    print(" Looks like you're going to " + destination)
    print(" Your budget for this trip is " + str(budget))
 
print(budget) # 1000
trip_welcome()
```

Here we are able to access the `budget` both inside the `trip_welcome` function as well as our `print()` statement. If a variable lives outside of any function it can be accessed anywhere in the file.

### Returns
At this point, our functions have been using `print()` to help us visualize the output in our interpreter. Functions can also *return* a value to the program so that this value can be modified or used later. We use the Python keyword `return` to do this.

```python
def calculate_exchange_usd(us_dollars, exchange_rate):
  return us_dollars * exchange_rate
 
new_zealand_exchange = calculate_exchange_usd(100, 1.4)
 
print("100 dollars in US currency would give you " + str(new_zealand_exchange) + " New Zealand dollars")
```

Saving our values returned from a function like we did with `new_zealand_exchange` allows us to reuse the value (in the form of a variable) throughout the rest of the program.

When there is a result from a function that is stored in a variable, it is called a *returned function value*.

### Multiple Returns
Sometimes we may want to return more than one value from a function. We can return several values by separating them with a comma.

```python
weather_data = ['Sunny', 'Sunny', 'Cloudy', 'Raining', 'Snowing']
 
def threeday_weather_report(weather):
  first_day = " Tomorrow the weather will be " + weather[0]
  second_day = " The following day it will be " + weather[1]
  third_day = " Two days from now it will be " + weather[2]
  return first_day, second_day, third_day
```

We can get our returned function values by assigning them to variables when we call the function:

```python
monday, tuesday, wednesday = threeday_weather_report(weather_data)
 
print(monday) # Tomorrow the weather will be Sunny
print(tuesday) # The following day it will be Sunny
print(wednesday) # Two days from now it will be Cloudy
```

### Project: Getting Ready for Physics Class
You are a physics teacher preparing for the upcoming semester. You want to provide your students with some functions that will help them calculate some fundamental physical properties.

```python
# Uncomment this when you reach the "Use the Force" section
train_mass = 22680
train_acceleration = 10
train_distance = 100
bomb_mass = 1

# Write your code below: 
def f_to_c(f_temp):
  c_temp = (f_temp - 32) * 5/9
  return c_temp

def c_to_f(c_temp):
  f_temp = c_temp * 9/5 + 32
  return f_temp

def get_force(mass, acceleration):
  return mass * acceleration

def get_energy(mass, c=3*10**8):
  return mass * c ** 2

def get_work(mass, acceleration, distance):
  return get_force(mass, acceleration) * distance

f100_in_celsius = f_to_c(100)
c0_in_fahrenheit = c_to_f(0)
print(f100_in_celsius)
print(c0_in_fahrenheit)

train_force = get_force(train_mass, train_acceleration)
print("The GE train supplies " + str(train_force) + " Newtons of force.")

bomb_energy = get_energy(bomb_mass)
print("A 1kg bomb supplies " + str(bomb_energy) + " Joules.")

train_work = get_work(train_mass, train_acceleration, train_distance)
print("The GE train does " + str(train_work) + " Joules of work over " + str(train_distance) + " meters.")
```

 
# Strings
## Introduction to Strings

### Introduction to Strings
In Python, the way we store something like a word, a sentence, or even a whole paragraph is as a *string*. A string is a sequence of characters contained within a pair of `'single quotes'` or `"double quotes"`. A string can be any length and can contain any letters, numbers, symbols, and spaces.

### They're all Lists!
A string can be thought of as a list of characters.

Like any other list, each character in a string has an index. 

```python
favorite_fruit = "blueberry"
print(favorite_fruit[1])
# Output: l
```

The indices of a string start at 0.

It’s important to note that indices of strings must be integers. If we were to try to select a non-integer index we would get a `TypeError`.

### Cut Me a Slice of String
Not only can we select a single character from a string, but we can also select entire chunks of characters from a string. 

```
string[first_index:last_index]
```

This is called *slicing* a string. When we slice a string we are creating a substring - a brand new string that starts at (and includes) the `first_index` and ends at (but excludes) the `last_index`.

```python
favorite_fruit = "blueberry"
print(favorite_fruit[4:6])
# Output: be
```

We can also have open-ended selections. If we remove the first index, the slice starts at the beginning of the string and if we remove the second index the slice continues to the end of the string.

```python
print(favorite_fruit[:4])
# Output: blue
 
print (favorite_fruit[4:])
# Output: berry
```

### Concatenating Strings
We can also *concatenate*, or combine, two existing strings together into a new string.

```python
fruit_prefix = "blue"
fruit_suffix = "berries"

favorite_fruit = fruit_prefix + fruit_suffix
 
print(favorite_fruit)
# Output: blueberries
```

Notice that there are no spaces added here. We have to manually add in the spaces when concatenating strings if we want to include them.

```python
fruit_sentence = "My favorite fruit is" + favorite_fruit
 
print(fruit_sentence)
# Output: My favorite fruit isblueberries
 
fruit_sentence = "My favorite fruit is " + favorite_fruit
 
print(fruit_sentence)
# Output: My favorite fruit is blueberries
```

### More and More String Slicing (How Long is that String?)
Python comes with some built-in functions for working with strings. One of the most commonly used of these functions is `len()`. `len()` returns the number of characters in a string:

```python
favorite_fruit = "blueberry"
 
length = len(favorite_fruit)
 
print(length)
# Output: 9
```

If you are taking the length of a sentence the spaces are counted as well.

### Negative Indices
Negative indices count backward from the end of the string, so `string_name[-1]` is the last character of the string, `string_name[-2]` is the second last character of the string, etc.

```python
favorite_fruit = 'blueberry'
print(favorite_fruit[-1])
# => 'y'
 
print(favorite_fruit[-2])
# => 'r'
 
print(favorite_fruit[-3:])
# => 'rry'
```

### Strings are Immutable
So far in this lesson, we’ve been selecting characters from strings, slicing strings, and concatenating strings. Each time we perform one of these operations we are creating an entirely new string.

This is because strings are *immutable*. This means that we cannot change a string once it is created. We can use it to create other strings, but we cannot change the string itself.

This property, generally, is known as *mutability*. Data types that are *mutable* can be changed, and data types, like strings, that are *immutable* cannot be changed.

### Escape Characters
Occasionally when working with strings, you’ll find that you want to include characters that already have a special meaning in Python.

By adding a backslash in front of the special character we want to escape, `\"`, we can include it in a string.

```python
favorite_fruit_conversation = "He said, \"blueberries are my favorite!\""
```

### Iterating through Strings
Because strings are lists, that means we can iterate through a string using `for` or `while` loops.

```python
def print_each_letter(word):
  for letter in word:
    print(letter)

favorite_color = "blue"
print_each_letter(favorite_color)
# => 'b'
# => 'l'
# => 'u'
# => 'e'
```

### Strings and Conditionals (Part One)
When we iterate through a string we do *something* with each character. By including conditional statements inside of these iterations, we can start to do some really cool stuff.

```python
favorite_fruit = "blueberry"
counter = 0
for character in favorite_fruit:
  if character == "b":
    counter = counter + 1
print(counter)
```

### Strings and Conditionals (Part Two)
There’s an even easier way than iterating through the entire string to determine if a character is in a string. We can do this type of check more efficiently using `in`. `in` checks if one string is part of another string.

```python
letter in word
```

Here, `letter in word` is a boolean expression that is `True` if the string letter is in the string `word`.

### Review
- A string is a list of characters.
- A character can be selected from a string using its index `string_name[index]`. These indices start at 0.
- A ‘slice’ can be selected from a string. These can be between two indices or can be open-ended, selecting all of the string from a point.
- Strings can be concatenated to make larger strings.
- `len()` can be used to determine the number of characters in a string.
- Strings can be iterated through using `for` loops.
- Iterating through strings opens up a huge potential for applications, especially when combined with conditional statements.

## String Methods

### Formatting Methods
There are three string methods that can change the casing of a string.

- `.lower()` returns the string with all lowercase characters.
- `.upper()` returns the string with all uppercase characters.
- `.title()` returns the string in title case, which means the first letter of each word is capitalized.

```python
favorite_song = 'SmOoTH'
favorite_song_lowercase = favorite_song.lower()
print(favorite_song_lowercase)
# => 'smooth'
```

It’s important to remember that string methods can only create new strings, they do not change the original string.

```python
print(favorite_song)
# => 'SmOoTH'
```

### Splitting Strings
`.split()` is performed on a string, takes one argument, and returns a list of substrings found between the given argument (which in the case of `.split()` is known as the delimiter). The following syntax should be used:

```python
string_name.split(delimiter)
```

If you do not provide an argument for `.split()` it will default to splitting at spaces.

```python
man_its_a_hot_one = "Like seven inches from the midday sun"
print(man_its_a_hot_one.split())
# => ['Like', 'seven', 'inches', 'from', 'the', 'midday', 'sun']
```

Note: if we run `.split()` on a string with no spaces, we will get the same string in return.

### Splitting Strings II
If we provide an argument for `.split()` we can dictate the character we want our string to be split on. This argument should be provided as a string itself.

```python
greatest_guitarist = "santana"
print(greatest_guitarist.split('n'))
# => ['sa', 'ta', 'a']

print(greatest_guitarist.split('a'))
# => ['s', 'nt', 'n', '']
```

When you split a string on a character that it also ends with, you’ll end up with an empty string at the end of the list.
 
### Splitting Strings III
We can also split strings using *escape sequences*. Escape sequences are used to indicate that we want to split by something in a string that is not necessarily a character. The two escape sequences we will cover here are

- `\n` Newline
- `\t` Horizontal Tab

Newline or `\n` will allow us to split a multi-line string by line breaks and `\t` will allow us to split a string by tabs. 

```python
smooth_chorus = \
"""And if you said, "This life ain't good enough."
I would give my world to lift you up
I could change my life to better suit your mood
Because you're so smooth"""
 
chorus_lines = smooth_chorus.split('\n')
 
print(chorus_lines)
```

```
['And if you said, "This life ain\'t good enough."', 'I would give my world to lift you up', 'I could change my life to better suit your mood', "Because you're so smooth"]
```

Notice that Python automatically escaped the `'` character in the first line and adjusted to double quotation marks to allow the apostrophe on last line when it created the new list.

### Joining Strings
`.join()` is essentially the opposite of `.split()`, it joins a list of strings together with a given delimiter. The syntax of `.join()` is:

```python
'delimiter'.join(list_you_want_to_join)
```

Now this may seem a little weird, because with `.split()` the argument was the delimiter, but now the argument is the list. This is because *join* is still a string method, which means it has to act on a string. The string `.join()` acts on is the delimiter you want to join with, therefore the list you want to join has to be the argument.

```python
my_munequita = ['My', 'Spanish', 'Harlem', 'Mona', 'Lisa']
print(' '.join(my_munequita))
# => 'My Spanish Harlem Mona Lisa'
```

### Joining Strings II
You can use any string as a delimiter to join together a list of strings.

```python
santana_songs = ['Oye Como Va', 'Smooth', 'Black Magic Woman', 'Samba Pa Ti', 'Maria Maria']
```

We could join this list together with ANY string. One often used string is a comma `,` because then we can create a string of *comma separated variables*, or CSV.

```python
santana_songs_csv = ','.join(santana_songs)
print(santana_songs_csv)
# => 'Oye Como Va,Smooth,Black Magic Woman,Samba Pa Ti,Maria Maria'
```

You can also join using *escape sequences* as the delimiter. 

```python
smooth_fifth_verse_lines = ['Well I\'m from the barrio', 'You hear my rhythm on your radio', 'You feel the turning of the world so soft and slow', 'Turning you \'round and \'round']
 
smooth_fifth_verse = '\n'.join(smooth_fifth_verse_lines)
 
print(smooth_fifth_verse)
```

```
Well I'm from the barrio
You hear my rhythm on your radio
You feel the turning of the world so soft and slow
Turning you 'round and 'round
```

### .strip()
When working with strings that come from real data, you will often find that the strings aren’t super clean. You’ll find lots of extra whitespace, unnecessary linebreaks, and rogue tabs.

Python provides a great method for cleaning strings: `.strip()`. Stripping a string removes all whitespace characters from the beginning and end. 

```python
featuring = "           rob thomas                 "
print(featuring.strip())
# => 'rob thomas'
```

You can also use `.strip()` with a character argument, which will strip that character from either end of the string.

```python
featuring = "!!!rob thomas       !!!!!"
print(featuring.strip('!'))
# => 'rob thomas       '
```

Notice that now that we’ve included an argument we are no longer stripping whitespace, we are ONLY stripping the argument.

### Replace
`replace()` takes two arguments and replaces all instances of the first argument in a string with the second argument.

```python
string_name.replace(substring_being_replaced, new_substring)
```

```python
with_spaces = "You got the kind of loving that can be so smooth"
with_underscores = with_spaces.replace(' ', '_')
print(with_underscores)
# 'You_got_the_kind_of_loving_that_can_be_so_smooth'
```

Note that in this example, we used a single character, but these substrings can be multiple characters long!

### .find()
`.find()` takes a string as an argument and searching the string it was run on for that string. It then returns the first *index value* where that string is located.

```python
print('smooth'.find('t'))
# => '4'
```

You can also search for larger strings, and `.find()` will return the index value of the first character of that string.

```python
print("smooth".find('oo'))
# => '2'
```

### .format()
`.format()` takes variables as an argument and includes them in the string that it is run on. You include `{}` marks as placeholders for where those variables will be imported.

```python
def favorite_song_statement(song, artist):
  return "My favorite song is {} by {}.".format(song, artist)
```

Note: `.format()` can take as many arguments as there are `{}` in the string it is run on.

```python
print(favorite_song_statement("Smooth", "Santana"))
# => "My favorite song is Smooth by Santana."
```

### .format() II
`.format()` can be made even more legible for other people reading your code by including *keywords*.

```python
def favorite_song_statement(song, artist):
  return "My favorite song is {song} by {artist}.".format(song=song, artist=artist)
```

You can even reverse the order of `artist` and `song` in the code above and it will work the same way.

### Review
- `.upper()`, `.title()`, and `.lower()` adjust the casing of your string.
- `.split()` takes a string and creates a list of substrings.
- `.join()` takes a list of strings and creates a string.
- `.strip()` cleans off whitespace, or other noise from the beginning and end of a string.
- `.replace()` replaces all instances of a character/string in a string with another character/string.
- `.find()` searches a string for a character/string and returns the index value that character/string is found at.
- `.format()` allows you to interpolate a string with variables.


# Modules
## Modules in Python

### Modules Python Introduction
Python allows us to package code into files or sets of files called *modules*.

A module is a collection of Python declarations intended broadly to be used as a tool. Modules are also often referred to as “libraries” or “packages” — a package is really a directory that holds a collection of modules.

Usually, to use a module in a file, the basic syntax you need at the top of that file is:

```python
from module_name import object_name
```

Often, a library will include a lot of code that you don’t need that may slow down your program or conflict with existing code. Because of this, it makes sense to only import what you need.

One common library that comes as part of the Python Standard Library is `datetime`. `datetime` helps you work with dates and times in Python.

In this case, you’ll notice that `datetime` is both the name of the library *and* the name of the object that you are importing.

```python
from datetime import datetime
```

### Modules Python Random
There are hundreds of Python modules that you can use. Another one of the most commonly used is `random` which allows you to generate numbers or select items at random.

With `random`, we’ll be using more than one piece of the module’s functionality, so the import syntax will look like:

```python
import random
```

We’ll work with two common `random` functions:

- `random.choice()` which takes a list as an argument and returns a number from the list
- `random.randint()` which takes two numbers as arguments and generates a random number between the two numbers you passed in

`random.randint` is inclusive.

```python
random_list = [random.randint(1, 100) for i in range(101)]
randomer_number = random.choice(random_list)
```

### Modules Python Namespaces
Notice that when we want to invoke the `randint()` function we call `random.randint()`. This is default behavior where Python offers a *namespace* for the module. A namespace isolates the functions, classes, and variables defined in the module from the code in the file doing the importing. Your *local namespace*, meanwhile, is where your code is run.

Python defaults to naming the namespace after the module being imported, but sometimes this name could be ambiguous or lengthy. Sometimes, the module’s name could also conflict with an object you have defined within your local namespace.

Fortunately, this name can be altered by *aliasing* using the `as` keyword:

```python
import module_name as name_you_pick_for_the_module
```

You might also occasionally encounter `import *`. The `*` is known as a “wildcard” and matches anything and everything. This syntax is considered dangerous because it could *pollute* our local namespace. Pollution occurs when the same name could apply to two possible things. For example, if you happen to have a function `floor()` focused on floor tiles, using `from math import *` would also import a function `floor()` that rounds down floats.

`matplotlib` allows you to plot your Python code in 2D.

`random.sample()` takes a range and a number as its arguments. It will return the specified number of random numbers from that range.

```python
#random.sample takes a list and randomly selects k items from it
new_list = random.sample(list, k)
#for example:
nums = [1, 2, 3, 4, 5]
sample_nums = random.sample(nums, 3)
print(sample_nums) # 2, 5, 1
```

It’s best to keep all imports at the top of your file.

### Modules Python Decimals
Let’s say you are writing software that handles monetary transactions. If you used Python’s built-in floating-point arithmetic to calculate a sum, it would result in a weirdly formatted number.

```python
cost_of_gum = 0.10
cost_of_gumdrop = 0.35
 
cost_of_transaction = cost_of_gum + cost_of_gumdrop
# Returns 0.44999999999999996
```

Being familiar with rounding errors in floating-point arithmetic you want to use a data type that performs decimal arithmetic more accurately. You could do the following:

```python
from decimal import Decimal
 
cost_of_gum = Decimal('0.10')
cost_of_gumdrop = Decimal('0.35')
 
cost_of_transaction = cost_of_gum + cost_of_gumdrop
# Returns 0.45 instead of 0.44999999999999996
```

### Modules Python Files and Scope
Scope also applies to *classes* and to the *files* you are working within.

Even files inside the *same directory* do not have access to each other’s variables, functions, classes, or any other code.

*Files are actually modules*, so you can give a file access to another file’s content using that glorious `import` statement.

### Review
This is just the beginning. Using a package manager (like conda or pip3), you can install any modules available on the Python Package Index.


# Dictionaries
## Creating Dictionaries

### Introduction to Python Dictionaries
A *dictionary* is an unordered set of `key: value` pairs.

In Python, we can create a dictionary called `menu` to store this data:

```python
menu = {"avocado toast": 6, "carrot juice": 5, "blueberry muffin": 2}
```

It’s considered good practice to insert a space (` `) after each comma, but our code will still run without the space.

### Make a Dictionary
Values can be of any type. We can use a string, a number, a list, or even another dictionary as the value associated with a key!

```python
students_in_classes = {"software design": ["Aaron", "Delila", "Samson"], "cartography": ["Christopher", "Juan", "Marco"], "philosophy": ["Frederica", "Manuel"]}
```

### Invalid Keys
We can have a list or a dictionary as a value of an item in a dictionary, but we cannot use these data types as keys of the dictionary. If we try to, we will get a `TypeError`.

```python
powers = {[1, 2, 4, 8, 16]: 2, [1, 3, 9, 27, 81]: 3}
```

```
TypeError: unhashable type: 'list'
```

The word “unhashable” in this context means that this ‘list’ is an object that can be changed.

Dictionaries in Python rely on each key having a *hash value*, a specific identifier for the key. If the key can change, that hash value would not be reliable. So the keys must always be unchangeable, hashable data types, like numbers or strings.

### Empty Dictionary
A dictionary doesn’t have to contain anything. Sometimes we need to create an empty dictionary when we plan to fill it later based on some other input.

```python
empty_dict = {}
```

### Add A Key
To add a single `key: value` pair to a dictionary, we can use the syntax:

```python
dictionary[key] = value
```

```python
menu = {"oatmeal": 3, "avocado toast": 6, "carrot juice": 5, "blueberry muffin": 2}

menu["cheesecake"] = 8
```

### Add Multiple Keys
If we wanted to add multiple key : value pairs to a dictionary at once, we can use the `.update()` method.

```python
sensors = {"living room": 21, "kitchen": 23, "bedroom": 20}

sensors.update({"pantry": 22, "guest room": 25, "patio": 34})
```

### Overwrite Values
What if we used a key that already has an entry in the `menu` dictionary? In that case, our value assignment would overwrite the existing value attached to that key.

```python
menu = {"oatmeal": 3, "avocado toast": 6, "carrot juice": 5, "blueberry muffin": 2}
menu["oatmeal"] = 5
print(menu)
```

```
{"oatmeal": 5, "avocado toast": 6, "carrot juice": 5, "blueberry muffin": 2}
```

### Dict Comprehensions
Let’s say we have two lists that we want to combine into a dictionary, like a list of students and a list of their heights, in inches:

```python
names = ['Jenny', 'Alexus', 'Sam', 'Grace']
heights = [61, 70, 67, 64]
```

Python allows you to create a dictionary using a dict comprehension, with this syntax:

```python
students = {key:value for key, value in zip(names, heights)}
#students is now {'Jenny': 61, 'Alexus': 70, 'Sam': 67, 'Grace': 64}
```

Remember that `zip()` combines two lists into an iterator of tuples with the list elements paired together. 

## Using Dictionaries

### Get A Key
Once you have a dictionary, you can access the values in it by providing the key.

```python
building_heights = {"Burj Khalifa": 828, "Shanghai Tower": 632, "Abraj Al Bait": 601, "Ping An": 599, "Lotte World Tower": 554.5, "One World Trade": 541.3}

building_heights["Burj Khalifa"] # 828
```

### Get an Invalid Key

```python
building_heights = {"Burj Khalifa": 828, "Shanghai Tower": 632, "Abraj Al Bait": 601, "Ping An": 599, "Lotte World Tower": 554.5, "One World Trade": 541.3}

print(building_heights["Landmark 81"])
```

But `"Landmark 81"` does not exist as a key in the `building_heights` dictionary! So this will throw a `KeyError`:

```
KeyError: 'Landmark 81'
```

One way to avoid this error is to first check if the key exists in the dictionary:

```python
key_to_check = "Landmark 81"
 
if key_to_check in building_heights:
  print(building_heights["Landmark 81"])
```

### Safely Get a Key
We saw in the last exercise that we had to add a key:value pair to a dictionary in order to avoid a `KeyError`. This solution is not sustainable. We can’t predict every key a user may call and add all of those placeholder values to our dictionary!

Dictionaries have a `.get()` method to search for a value instead of the `my_dict[key]` notation we have been using. If the key you are trying to `.get()` does not exist, it will return `None` by default:

```python
building_heights = {"Burj Khalifa": 828, "Shanghai Tower": 632, "Abraj Al Bait": 601, "Ping An": 599, "Lotte World Tower": 554.5, "One World Trade": 541.3}
 
#this line will return 632:
building_heights.get("Shanghai Tower")
 
#this line will return None:
building_heights.get("My House")
```

You can also specify a value to return if the key doesn’t exist. For example, we might want to return a building height of `0` if our desired building is not in the dictionary:

```python
building_heights.get('Mt Olympus', 0) # 0
building_heights.get('Kilimanjaro', 'No Value') # 'No Value'
```

### Delete a Key
Sometimes we want to get a key and remove it from the dictionary. 

```python
raffle = {223842: "Teddy Bear", 872921: "Concert Tickets", 320291: "Gift Basket", 412123: "Necklace", 298787: "Pasta Maker"}
```

We can use `.pop()` to do this. Just like with `.get()`, we can provide a default value to return if the key does not exist in the dictionary:

```python
raffle.pop(320291, "No Prize") # "Gift Basket"
```

`.pop()` works to delete items from a dictionary, when you know the key value.

### Get All Keys
Sometimes we want to operate on all of the keys in a dictionary.

```python
test_scores = {"Grace":[80, 72, 90], "Jeffrey":[88, 68, 81], "Sylvia":[80, 82, 84], "Pedro":[98, 96, 95], "Martin":[78, 80, 78], "Dina":[64, 60, 75]}
```

We want to get a roster of the students in the class, without including their grades. We can do this with the built-in `list()` function:

```python
list(test_scores)
# ["Grace", "Jeffrey", "Sylvia", "Pedro", "Martin", "Dina"]
```

Dictionaries also have a `.keys()` method that returns a `dict_keys` object. A `dict_keys` object is a *view* object, which provides a look at the current state of the dictionary, without the user being able to modify anything. The `dict_keys` object returned by `.keys()` is a set of the keys in the dictionary. You cannot add or remove elements from a `dict_keys` object, but it can be used in the place of a list for iteration:

```python
for student in test_scores.keys():
  print(student)
```

### Get All Values
Dictionaries have a `.values()` method that returns a `dict_values` object (just like a `dict_keys` object but for values!) with all of the values in the dictionary. It can be used in the place of a list for iteration:

```python
test_scores = {"Grace":[80, 72, 90], "Jeffrey":[88, 68, 81], "Sylvia":[80, 82, 84], "Pedro":[98, 96, 95], "Martin":[78, 80, 78], "Dina":[64, 60, 75]}
 
for score_list in test_scores.values():
  print(score_list)
```

```
[80, 72, 90]
[88, 68, 81]
[80, 82, 84]
[98, 96, 95]
[78, 80, 78]
[64, 60, 75]
```

There is no built-in function to get all of the values as a list, but if you *really* want to, you can use:

```python
list(test_scores.values())
```

However, for most purposes, the `dict_values` object will act the way you want a list to act.

### Get All Items
You can get both the keys and the values with the `.items()` method. Like `.keys()` and `.values()`, it returns a `dict_list` object. Each element of the `dict_list` returned by `.items()` is a tuple consisting of `(key, value)`.

```python
biggest_brands = {"Apple": 184, "Google": 141.7, "Microsoft": 80, "Coca-Cola": 69.7, "Amazon": 64.8}
 
for company, value in biggest_brands.items():
  print(company + " has a value of " + str(value) + " billion dollars. ")
```

 
# Files
## Learn Python: Files

### Reading a File
Computers use file systems to store and retrieve data. Each file is an individual container of related information. 

```python
with open('real_cool_document.txt') as cool_doc:
  cool_contents = cool_doc.read()
print(cool_contents)
```

This opens a file object called `cool_doc` and creates a new indented block where you can read the contents of the opened file. We then read the contents of the file `cool_doc` using `cool_doc.read()` and save the resulting string into the variable `cool_contents`. Then we print `cool_contents`.

### Iterating Through Lines
When we read a file, we might want to grab the whole document in a single string, like `.read()` would return. But what if we wanted to store each line in a variable? We can use the `.readlines()` function to read a text file line by line instead of having the whole thing.

```python
with open('keats_sonnet.txt') as keats_sonnet:
  for line in keats_sonnet.readlines():
    print(line)
```

### Reading a Line
Sometimes you don’t want to iterate through a whole file. For that, there’s a different file method, `.readline()`, which will only read a single line at a time. If the entire document is read line by line in this way subsequent calls to `.readline()` will not throw an error but will start returning an empty string (`""`).

```python
with open('millay_sonnet.txt') as sonnet_doc:
  first_line = sonnet_doc.readline()
  second_line = sonnet_doc.readline()
  print(second_line)
```

### Writing a File
It turns out that our `open()` function that we’re using to open a file to read needs another argument to open a file to write to.

```python
with open('generated_file.txt', 'w') as gen_file:
  gen_file.write("What an incredible file!")
```

Here we pass the argument `'w'` to `open()` in order to indicate to open the file in write-mode. The default argument is `'r'` and passing `'r'` to `open()` opens the file in read-mode as we’ve been doing.

It’s important to note that if there is already a file called **generated_file.txt** it will completely overwrite that file, erasing whatever its contents were before.

### Appending to a File
Instead of opening the file using the argument `'w'` for write-mode, we open it with `'a'` for append-mode.

```python
with open('generated_file.txt', 'a') as gen_file:
  gen_file.write("\n... and it still is")
```

The newline character `\n` moves to the next line before adding the rest of the string.

### What's With "with"?
The `with` keyword invokes something called a *context manager* for the file that we’re calling `open()` on. This context manager takes care of opening the file when we call `open()` and then closing the file after we leave the indented block.

Leaving a file connection open unnecessarily can affect performance or impact other programs on your computer that might be trying to access that file.

The `with` syntax replaces older ways to access files where you need to call `.close()` on the file object manually. We can still open up a file and append to it with the old syntax, as long as we remember to close the file connection afterwards.

```python
fun_cities_file = open('fun_cities.txt', 'a')
 
# We can now append a line to "fun_cities".
fun_cities_file.write("Montréal")
 
# But we need to remember to close the file
fun_cities_file.close()
```

### What Is a CSV File?
Text files aren’t the only thing that Python can read, but they’re the only thing that we don’t need any additional parsing library to understand. CSV files are an example of a text file that impose a structure to their data. CSV stands for *Comma-Separated Values* and CSV files are usually the way that data from spreadsheet software (like Microsoft Excel or Google Sheets) is exported into a portable format.

```
Name,Username,Email
Roger Smith,rsmith,wigginsryan@yahoo.com
Michelle Beck,mlbeck,hcosta@hotmail.com
Ashley Barker,a_bark_x,a_bark_x@turner.com
Lynn Gonzales,goodmanjames,lynniegonz@hotmail.com
Jennifer Chase,chasej,jchase@ramirez.com
Charles Hoover,choover,choover89@yahoo.com
Adrian Evans,adevans,adevans98@yahoo.com
Susan Walter,susan82,swilliams@yahoo.com
Stephanie King,stephanieking,sking@morris-tyler.com
Erika Miller,jessica32,ejmiller79@yahoo.com
```

Notice that the first row of the CSV file doesn’t actually represent any data, just the labels of the data that’s present in the rest of the file. The rest of the rows of the file are the same as the rows in the spreadsheet software, just instead of being separated into different cells they’re separated by… well I suppose it’s fair to say they’re separated by commas.

### Reading a CSV File
Even though we can read these lines as text without a problem, there are ways to access the data in a format better suited for programming purposes. In Python we can convert that data into a dictionary using the `csv` library’s `DictReader` object.

```python
import csv
 
list_of_email_addresses = []
with open('users.csv', newline='') as users_csv:
  user_reader = csv.DictReader(users_csv)
  for row in user_reader:
    list_of_email_addresses.append(row['Email'])
```

We pass the additional keyword argument `newline=''` to the file opening `open()` function so that we don’t accidentally mistake a line break in one of our data fields as a new row in our CSV.

After opening our new CSV file we use `csv.DictReader(users_csv)` which converts the lines of our CSV file to Python dictionaries which we can use access methods for. The keys of the dictionary are, by default, the entries in the first line of our CSV file.

When we iterate through the rows of our `user_reader` object, we access all of the rows in our CSV as dictionaries (except for the first row, which we used to label the keys of our dictionary).

### Reading Different Types of CSV Files
We’ve been acting like CSV files are Comma-Separated Values files. It’s true that CSV stands for that, but it’s also true that other ways of separating values are valid CSV files these days.

People used to call Tab-Separated Values files TSV files, but as other separators grew in popularity everyone realized that creating a new `.[a-z]sv` file format for every value-separating character used is not sustainable.

So we call all files with a list of different values a CSV file and then use different *delimiters* (like a comma or tab) to indicate where the different values start and stop.

```
Name;Address;Telephone
Donna Smith;126 Orr Corner Suite 857\nEast Michael, LA 54411;906-918-6560
Aaron Osborn;6965 Miller Station Suite 485\nNorth Michelle, KS 64364;815.039.3661x42816
Jennifer Barnett;8749 Alicia Vista Apt. 288\nLake Victoriaberg, TN 51094;397-796-4842x451
Joshua Bryan;20116 Stephanie Stravenue\nWhitneytown, IA 87358;(380)074-6173
Andrea Jones;558 Melissa Keys Apt. 588\nNorth Teresahaven, WA 63411;+57(8)7795396386
Victor Williams;725 Gloria Views Suite 628\nEast Scott, IN 38095;768.708.3411x954
```

Notice the `\n` character, this is the escape sequence for a new line. The possibility of a new line escaped by a `\n` character in our data is why we pass the `newline=''` keyword argument to the `open()` function.

```python
import csv
 
with open('addresses.csv', newline='') as addresses_csv:
  address_reader = csv.DictReader(addresses_csv, delimiter=';')
  for row in address_reader:
    print(row['Address'])
```

Notice that when we call `csv.DictReader` we pass in the `delimiter` parameter, which is the string that’s used to delineate separate fields in the CSV.

### Writing a CSV File
Naturally if we have the ability to read different CSV files we might want to be able to programmatically create CSV files that save output and data that someone could load into their spreadsheet software.

```python
big_list = [{'name': 'Fredrick Stein', 'userid': 6712359021, 'is_admin': False}, {'name': 'Wiltmore Denis', 'userid': 2525942, 'is_admin': False}, {'name': 'Greely Plonk', 'userid': 15890235, 'is_admin': False}, {'name': 'Dendris Stulo', 'userid': 572189563, 'is_admin': True}] 
 
import csv
 
with open('output.csv', 'w') as output_csv:
  fields = ['name', 'userid', 'is_admin']
  output_writer = csv.DictWriter(output_csv, fieldnames=fields)
 
  output_writer.writeheader()
  for item in big_list:
    output_writer.writerow(item)
```

We define the fields we’re going to be using into a variable called `fields`. We then instantiate our CSV writer object and pass two arguments. The first is `output_csv`, the file handler object. The second is our list of fields `fields` which we pass to the keyword parameter `fieldnames`.

First we want the headers, so we call `.writeheader()` on the writer object. This writes all the fields passed to `fieldnames` as the first row in our file. Then we iterate through our `big_list` of data. Each `item` in `big_list` is a dictionary with each field in `fields` as the keys. We call `output_writer.writerow()` with the `item` dictionaries which writes each line to the CSV file.

### Reading a JSON File
We can also use Python’s file tools to read and write JSON. JSON, an abbreviation of JavaScript Object Notation, is a file format inspired by the programming language JavaScript. The name, like CSV is a bit of a misnomer — some JSON is not valid JavaScript (and plenty of JavaScript is not valid JSON).

Python comes with a `json` package that will help us parse JSON files into actual Python dictionaries.

```json
{
  'user': 'ellen_greg',
  'action': 'purchase',
  'item_id': '14781239',
}
```

```python
import json
 
with open('purchase_14781239.json') as purchase_json:
  purchase_data = json.load(purchase_json)
 
print(purchase_data['user'])
# Prints 'ellen_greg'
```

We continue by parsing `purchase_json` using `json.load()`, creating a Python dictionary out of the file.

### Writing a JSON File
Naturally we can use the `json` library to translate Python objects to JSON as well. 

```python
turn_to_json = {
  'eventId': 674189,
  'dateTime': '2015-02-12T09:23:17.511Z',
  'chocolate': 'Semi-sweet Dark',
  'isTomatoAFruit': True
}

import json
 
with open('output.json', 'w') as json_file:
  json.dump(turn_to_json, json_file)
```

`json.dump()` takes two arguments: first the data object, then the file object you want to save.


# Classes
## Introduction to Classes

### Types
Python equips us with many different ways to store data. A `float` is a different kind of number from an `int`, and we store different data in a `list` than we do in a `dict`. These are known as different *types*. We can check the type of a Python variable using the `type()` function.

```python
a_string = "Cool String"
an_int = 12
 
print(type(a_string))
# prints "<class 'str'>"
 
print(type(an_int))
# prints "<class 'int'>"
```

A variable’s type determines what you can do with it and how you can use it. You can’t `.get()` something from an integer, just as you can’t add two dictionaries together using `+`. This is because those operations are defined at the type level.

### Class
A *class* is a template for a data type. It describes the kinds of information that class will hold and how a programmer will interact with that data. Define a class using the `class` keyword. PEP 8 Style Guide for Python Code recommends capitalizing the names of classes to make them easier to identify.

```python
class CoolClass:
  pass
```

### Instantiation
A class doesn’t accomplish anything simply by being defined. A class must be *instantiated*. In other words, we must create an *instance* of the class, in order to breathe life into the schematic.

Instantiating a class looks a lot like calling a function. We would be able to create an instance of our defined `CoolClass` as follows:

```python
cool_instance = CoolClass()
```

Above, we created an object by adding parentheses to the name of the class.

### Object-Oriented Programming
A class instance is also called an *object*. The pattern of defining classes and creating objects to represent the responsibilities of a program is known as *Object Oriented Programming* or OOP.

Instantiation takes a class and turns it into an object, the `type()` function does the opposite of that. When called with an object, it returns the class that the object is an instance of.

```python
print(type(cool_instance))
# prints "<class '__main__.CoolClass'>"
```

In Python `__main__` means “this current file that we’re running” and so one could read the output from `type()` to mean “the class `CoolClass` that was defined here, in the script you’re currently running.”

### Class Variables
When we want the same data to be available to every instance of a class we use a *class variable*. A class variable is a variable that’s the same for every instance of the class.

You can define a class variable by including it in the indented part of your class definition, and you can access all of an object’s class variables with `object.variable` syntax.

```python
class Musician:
  title = "Rockstar"
 
drummer = Musician()
print(drummer.title)
# prints "Rockstar"
```

### Methods
*Methods* are functions that are defined as part of a class. The first argument in a method is always the object that is calling the method. Convention recommends that we name this first argument `self`. Methods always have at least this one argument.

We define methods similarly to functions, except that they are indented to be part of the class.

```python
class Dog:
  dog_time_dilation = 7
 
  def time_explanation(self):
    print("Dogs experience {} years for every 1 human year.".format(self.dog_time_dilation))
 
pipi_pitbull = Dog()
pipi_pitbull.time_explanation()
# Prints "Dogs experience 7 years for every 1 human year."
```

Notice we didn’t pass any arguments when we called `.time_explanation()`, but were able to refer to self in the function body. When you call a method it automatically passes the object calling the method as the first argument.

### Methods with Arguments
Methods can also take more arguments than just `self`:

```python
class DistanceConverter:
  kms_in_a_mile = 1.609
  def how_many_kms(self, miles):
    return miles * self.kms_in_a_mile
 
converter = DistanceConverter()
kms_in_5_miles = converter.how_many_kms(5)
print(kms_in_5_miles)
# prints "8.045"
```

### Constructors
There are several methods that we can define in a Python class that have special behavior. These methods are sometimes called “magic,” because they behave differently from regular methods. Another popular term is *dunder methods*, so-named because they have two underscores (double-underscore abbreviated to “dunder”) on either side of them.

The first dunder method we’re going to use is the `__init__()` method (note the two underscores before and after the word “init”). This method is used to initialize a newly created object. It is called every time the class is instantiated.

Methods that are used to prepare an object being instantiated are called *constructors*. The word “constructor” is used to describe similar features in other object-oriented programming languages but programmers who refer to a constructor in Python are usually talking about the `__init__()` method.

```python
class Shouter:
  def __init__(self):
    print("HELLO?!")
 
shout1 = Shouter()
# prints "HELLO?!"
 
shout2 = Shouter()
# prints "HELLO?!"
```

`Shouter()` looks a lot like a function call, doesn’t it? If it’s a function, can we pass parameters to it? We absolutely can, and those parameters will be received by the `__init__()` method.

```python
class Shouter:
  def __init__(self, phrase):
    # make sure phrase is a string
    if type(phrase) == str:
 
      # then shout it out
      print(phrase.upper())
 
shout1 = Shouter("shout")
# prints "SHOUT"
 
shout2 = Shouter("shout")
# prints "SHOUT"
 
shout3 = Shouter("let it all out")
# prints "LET IT ALL OUT"
```

### Instance Variables
The data held by an object is referred to as an *instance variable*. Instance variables aren’t shared by all instances of a class — they are variables that are specific to the object they are attached to.

```python
class FakeDict:
  pass

fake_dict1 = FakeDict()
fake_dict2 = FakeDict()
 
fake_dict1.fake_key = "This works!"
fake_dict2.fake_key = "This too!"
 
# Let's join the two strings together!
working_string = "{} {}".format(fake_dict1.fake_key, fake_dict2.fake_key)
print(working_string)
# prints "This works! This too!"
```

### Attribute Functions
Instance variables and class variables are both accessed similarly in Python. This is no mistake, they are both considered *attributes* of an object. If we attempt to access an attribute that is neither a class variable nor an instance variable of the object Python will throw an `AttributeError`.

```python
class NoCustomAttributes:
  pass
 
attributeless = NoCustomAttributes()
 
try:
  attributeless.fake_attribute
except AttributeError:
  print("This text gets printed!")
 
# prints "This text gets printed!"
```

What if we aren’t sure if an object has an attribute or not? `hasattr()` will return `True` if an object has a given attribute and `False` otherwise. If we want to get the actual value of the attribute, `getattr()` is a Python function that will return the value of a given object and attribute. In this function, we can also supply a third argument that will be the default if the object does not have the given attribute.

`hasattr(object, “attribute”)` has two parameters:

- *object* : the object we are testing to see if it has a certain attribute
- *attribute* : name of attribute we want to see if it exists

`getattr(object, “attribute”, default)` has three parameters (one of which is optional):

- *object* : the object whose attribute we want to evaluate
- *attribute* : name of attribute we want to evaluate
- *default* : the value that is returned if the attribute does not exist (note: this parameter is optional)

```python
hasattr(attributeless, "fake_attribute")
# returns False
 
getattr(attributeless, "other_fake_attribute", 800)
# returns 800, the default value
```

### Self
Since we can already use dictionaries to store key-value pairs, using objects for that purpose is not really useful. Instance variables are more powerful when you can guarantee a rigidity to the data the object is holding.

This convenience is most apparent when the constructor creates the instance variables, using the arguments passed in to it. If we were creating a search engine, and we wanted to create classes for each separate entry we could return. We’d do that like this:

```python
class SearchEngineEntry:
  def __init__(self, url):
    self.url = url
 
codecademy = SearchEngineEntry("www.codecademy.com")
wikipedia = SearchEngineEntry("www.wikipedia.org")
 
print(codecademy.url)
# prints "www.codecademy.com"
 
print(wikipedia.url)
# prints "www.wikipedia.org"
```

Since the `self` keyword refers to the object and not the class being called, we can define a `secure` method on the `SearchEngineEntry` class that returns the secure link to an entry.

```python
class SearchEngineEntry:
  secure_prefix = "https://"
  def __init__(self, url):
    self.url = url
 
  def secure(self):
    return "{prefix}{site}".format(prefix=self.secure_prefix, site=self.url)
 
codecademy = SearchEngineEntry("www.codecademy.com")
wikipedia = SearchEngineEntry("www.wikipedia.org")
 
print(codecademy.secure())
# prints "https://www.codecademy.com"
 
print(wikipedia.secure())
# prints "https://www.wikipedia.org"
```

This is the strength of writing object-oriented programs. We can write our classes to structure the data that we need and write methods that will interact with that data in a meaningful way.

### Everything is an Object
Attributes can be added to user-defined objects after instantiation, so it’s possible for an object to have some attributes that are not explicitly defined in an object’s constructor. We can use the `dir()` function to investigate an object’s attributes at runtime. `dir()` is short for *directory* and offers an organized presentation of object attributes.

```python
class FakeDict:
  pass
 
fake_dict = FakeDict()
fake_dict.attribute = "Cool"
 
dir(fake_dict)
# Prints ['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__()', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'attribute']
```

Python automatically adds a number of attributes to all objects that get created. These internal attributes are usually indicated by double-underscores.

Do you remember being able to use `type()` on Python’s native data types? This is because they are also objects in Python. Their classes are `int`, `float`, `str`, `list`, and `dict`. These Python classes have special syntax for their instantiation, `1`, `1.0`, `"hello"`, `[]`, and `{}` specifically. But these instances are still full-blown objects to Python.

```python
fun_list = [10, "string", {'abc': True}]
 
type(fun_list)
# Prints <class 'list'>
 
dir(fun_list)
# Prints ['__add__', '__class__', [...], 'append', 'clear', 'copy', 'count', 'extend', 'index', 'insert', 'pop', 'remove', 'reverse', 'sort']
```

### String Representation
`__repr__()`is a method we can use to tell Python what we want the *string representation* of the class to be. `__repr__()` can only have one parameter, `self`, and must return a string.

```python
class Employee():
  def __init__(self, name):
    self.name = name
 
  def __repr__(self):
    return self.name
 
argus = Employee("Argus Filch")
print(argus)
# prints "Argus Filch"
```
 