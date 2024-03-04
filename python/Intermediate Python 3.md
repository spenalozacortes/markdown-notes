#python
# Function Arguments

## Python Gotcha: Mutable Default Arguments

### A Python Gotcha!
When writing a function with default arguments, it can sometimes be tempting to include an empty list as a default argument to that function.

```python
def createStudent(name, age, grades=[]):
    return {
        'name': name,
        'age': age,
        'grades': grades
    }
```

We can create two new students based off this code (assuming they have no grades yet):

```python
chrisley = createStudent('Chrisley', 15)
dallas = createStudent('Dallas', 16)
```

Realistically, as both Chrisley and Dallas progress in school, there should be a way for us to add new grades. Something like this method:

```python
def addGrade(student, grade):
    student['grades'].append(grade)
    # To help visualize the grades we have added a print statement
    print(student['grades'])
```

Let’s give Chrisley and Dallas some grades:

```python
addGrade(chrisley, 90)
addGrade(dallas, 100)
```

Here, we _**expect**_ that the output probably would be :

```
[90]
[100]
```

That would make sense since we want each student to have an individual grades list. Surprisingly (or maybe not so much), the actual output is:

```python
[90]
[90, 100]
```

This is known as a _gotcha_ - a counterintuitive feature of a programming language that often leads to mistakes in programs.

### Mutables and Functions
To understand this gotcha, we must first establish what Python classifies as mutable. A mutable object refers to various containers in Python that are intended to be changed. A list for example has append and remove operations that change the elements of the list. Sets and dictionaries are also two other mutable objects in Python as they can be changed on the fly.

It might be helpful to note some of the objects in Python that are not mutable (and therefore OK to use as default arguments). `int`, `float`, and other numbers can’t be mutated (arithmetic operations will return a new number). Tuples are a kind of immutable list, and strings are also immutable since operations that update a string will all return a completely new string.

When using a mutable in function arguments, it’s important to note the following (from the [official documentation](https://docs.python.org/3/reference/compound_stmts.html#function-definitions)):

> **Default parameter values are evaluated from left to right when the function definition is executed.** This means that the expression is evaluated once, when the function is defined, and that the same “pre-computed” value is used for each call.

This means that when we call a function, the default values we provide for parameters are only created once, and used for each subsequent call of the function. This means our `grades=[]` from our earlier function was only created once and anytime we tried to access it, the same list was being modified. We can even see that the memory id of the grades property for both students is the same (using the built-in `id()` function):

```python
# The ids printed will vary depending on the computer we are using. 
print(id(chrisley['grades']))
print(id(dallas['grades']))
```

Would output:

```
139828567365696
139828567365696
```

### The None Workaround
If we want an empty list as a potential default argument value, we can use `None` as a special value to indicate we did not receive anything. After we check whether an argument was provided, we can instantiate a new list if it wasn’t.

```python
def createStudent(name, age, grades=None):
  if grades is None:
    grades = []
  return {
    'name': name,
    'age': age,
    'grades': grades
  }

def addGrade(student, grade):
    student['grades'].append(grade)
    # To help visualize the grades we have added a print statement
    print(student['grades'])
```

Now if we create our students again and add grades to them:

```python
chrisley = createStudent('Chrisley', 15)
dallas = createStudent('Dallas', 16)

addGrade(chrisley, 90)
addGrade(dallas, 100)
```

We would get our expected result:

```
[90]
[100]
```

While it may seem more cumbersome to write the `if` clause, this is one of the most common (and flexible) ways to avoid running into issues with mutable default arguments.

## Function Arguments

### Function Arguments: A Recap
In Python, there are three common types of function arguments:

- Positional arguments: arguments that are called by their position in the function definition.
- Keyword arguments: arguments that are called by their name.
- Default arguments: arguments that are given default values.

### Variable number of arguments: `*args`
To start exploring variable argument lengths in Python [functions](https://www.codecademy.com/resources/docs/python/functions), let’s take a look at a familiar function we have been using for a long time:

```python
print('This', 'is', 'the', 'print', 'function')
```

Notice how the [`print()`](https://www.codecademy.com/resources/docs/python/built-in-functions/print) function does not care how many arguments we pass to it. It has no expectation that we are going to pass in one argument or even a million!

Well, in Python, there is an additional operator called the _unpacking operator_ (`*`). The unpacking operator allows us to give our functions a variable number of arguments by performing what’s known as _positional argument packing_.

Let’s explore how it works by examining a basic function that utilizes the unpacking operator:

```python
def my_function(*args):
  print(args)
```

If we called this function with random arguments:

```python
my_function('Arg1', 245, False)
```

Our output would show us what is inside of `*args`:

```
('Arg1', 245, False)
```

The name of `args` is completely arbitrary.

Whatever name follows the unpacking operator (`*`) will store the arguments passed into the function in the form of a tuple.

### Working with `*args`
Say we wanted to build a function that works similarly to our trusty [`print()`](https://www.codecademy.com/resources/docs/python/built-in-functions/print) statement but instead prints all of the arguments in uppercase form. Using our knowledge of iteration, combined with the power of the unpacking operator, our solution might look like this:

```python
def shout_strings(*args):
  for argument in args:
    print(argument.upper())

shout_strings('Working on', 'learning', 'argument unpacking!')
```

Would output:

```
WORKING ON
LEARNING
ARGUMENT UNPACKING!
```

The unpacking operator is not limited to being used alone, but rather it can be combined with other positional arguments. Let’s examine a function that truncates (cuts off) sentences based on a provided length:

```python
def truncate_sentences(length, *sentences):
  for sentence in sentences:
    print(sentence[:length])

truncate_sentences(8, "What's going on here", "Looks like we've been cut off")
```

Would output:

```
What's g
Looks li
```

### Variable number of arguments: `**kwargs`
Python doesn’t stop at allowing us to accept unlimited positional arguments; it also gives us the power to define [functions](https://www.codecademy.com/resources/docs/python/functions) with unlimited keyword arguments. The syntax is very similar but uses two asterisks `**` instead of one. We typically call these `kwargs` as a shorthand for keyword arguments.

```python
def arbitrary_keyword_args(**kwargs):
  print(type(kwargs))
  print(kwargs)
  # See if there's an 'anything_goes' keyword arg and print it
  print(kwargs.get('anything_goes'))

arbitrary_keyword_args(this_arg='wowzers', anything_goes=101)
```

Would output:

```
<class 'dict'>
{'this_arg': 'wowzers', 'anything_goes': 101}
101
```

`**kwargs` takes the form of a dictionary with all the keyword argument values passed to `arbitrary_keyword_args`. Since `**kwargs` is a dictionary, we can use standard dictionary functions like `.get()` to retrieve values.

Just as we saw with `*args`, the name of `kwargs` is completely arbitrary.

### Working with `**kwargs`
Since `**` generates a standard dictionary, we can use iteration just like we did earlier by taking advantage of the [`.values()`](https://www.codecademy.com/resources/docs/python/dictionaries/values) method.

```python
def print_data(**data):
  for arg in data.values():
    print(arg)

print_data(a='arg1', b=True, c=100)
```

Would output:

```
arg1
True
100
```

We can also combine our use of `**` with regular positional arguments. However, Python requires that all positional arguments come first in our function definition.

```python
def print_data(positional_arg, **data):
  print(positional_arg)
  for arg in data.values():
    print(arg)

print_data('position 1', a='arg1', b=True, c=100)
```

Would output:

```
position 1
arg1
True
100
```

If we were to switch the position of `positional_arg` to come after `**data`, we would be met with a `SyntaxError`.

### All together now!
So far we have seen how both `*args` and `**kwargs` can be combined with standard arguments. This is useful, but in some cases, we may want to use all three types together! Thankfully Python allows us to do so as long as we follow the correct order in our function definition. The order is as follows:

1. Standard positional arguments
2. `*args`
3. Standard keyword arguments
4. `**kwargs`

```python
def print_animals(animal1, animal2, *args, animal4, **kwargs):
  print(animal1, animal2)
  print(args)
  print(animal4)
  print(kwargs)
```

We could call our function like so:

```python
print_animals('Snake', 'Fish', 'Guinea Pig', 'Owl', animal4='Cat', animal5='Dog')
```

And our result would be:

```
Snake Fish
('Guinea Pig', 'Owl')
Cat
{'animal5': 'Dog'}
```

### Function Call Unpacking & Beyond
Not only can we use the operators when defining parameters, but we can also use them in function calls.

Let’s imagine we want to sum a few numbers together:

```python
def sum(num1, num2, num3):
  print(num1 + num2 + num3)
```

Right now, our function forces us to pass in an individual argument for `num1`, `num2`, and `num3`. This isn’t a big issue if we have separate [variables](https://www.codecademy.com/resources/docs/python/variables) or know our numbers in advance. However, what if we wanted to use a list like `[3, 6, 9]` instead? Well, that is where the unpacking operator comes to the rescue.

```python
my_num_list = [3, 6, 9]

def sum(num1, num2, num3):
  print(num1 + num2 + num3)

sum(*my_num_list)
```

Would output:

```
18
```

by using the unpacking operator (`*`) we are spreading the contents of our list `my_num_list` into the individual arguments in our function definition. We are immediately saved the hassle of writing [loops](https://www.codecademy.com/resources/docs/python/loops) and are given the flexibility to use any iterable with three elements.

This way of using the `*` in a function call also applies to our keyword operator `**`. As long as the [keywords](https://www.codecademy.com/resources/docs/python/keywords) match the function parameter names, we can accomplish the same goal:

```python
numbers  = {'num1': 3, 'num2': 6, 'num3': 9}

def sum(num1, num2, num3):
  print(num1 + num2 + num3)

sum(**numbers)
```

Would output:

```
18
```

We can even use the operators inside of [built-in functions](https://www.codecademy.com/resources/docs/python/built-in-functions). For example, instead of manually providing the [`range()`](https://www.codecademy.com/resources/docs/python/built-in-functions/range) built-in function with a start and stop value, we can unpack a list directly into it.

```python
start_and_stop = [3, 6]

range_values = range(*start_and_stop)
print(list(range_values))
```

Would output:

```
[3, 4, 5]
```

The possibilities of using the `*` and `**` operators are endless.

- Unpacking parts of an iterable

```python
 a, *b, c = [3, 6, 9, 12, 15]
 print(b)
```

Would output:

```
[6, 9, 12]
```

- Merging iterables

```python
my_tuple = (3, 6, 9)
merged_tuple = (0, *my_tuple, 12)
print(merged_tuple)
```

Would output:

```
(0, 3, 6, 9, 12)
```

- Combining unpacking and packing

```python
num_collection = [3, 6, 9]

def power_two(*nums): 
  for num in nums:
    print(num**2)

power_two(*num_collection)
```

Would output:

```
9 
36
81
```
#aqui 




# Namespaces and Scope

## Namespaces

## Scope


# Functions Deep Dive

## Lambda Functions

## Introduction to Higher-Order Functions

## Built-In Higher-Order Functions


# Object-Oriented Programming

## Object-Oriented Programming

## The @property Decorator


# Unit Testing

## Exceptions

## Unit Testing


# Iterators & Generators

## Iterables & Iterators

## Generators


# Specialized Collections

## Sets

## Collections


# Resource Management

## Context Managers
