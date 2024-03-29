20# Function Arguments

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
 
# Namespaces and Scope

## Namespaces

### Introduction to Names and Namespaces
In Python, a _name_ (sometimes also called a _symbolic name_) is an identifier for an object.

```python
color = "cyan"
```

A *namespace* is a collection of names and the objects that they reference. Python will host a dictionary where the keys are the names that have been defined and the mapped values are the objects that they reference.

```
{'color': 'cyan'}
```

The four distinct types of namespaces that Python generates:

1. Built-In
2. Global
3. Local
4. Enclosing

### Built-in Namespace

![[Pasted image 20240317141829.png]]

Ever wonder why [functions](https://www.codecademy.com/resources/docs/python/functions) like [`print()`](https://www.codecademy.com/resources/docs/python/built-in-functions/print) and [`str()`](https://www.codecademy.com/resources/docs/python/built-in-functions/str) are available to us in all our programs? Well, Python knows these function _**names**_ because they exist in the highest level of namespaces and thus can be called in any program we write.

Whenever we run a Python application, we are provided a built-in namespace that is created when the interpreter is started and has a lifetime until the interpreter terminates (usually when our program is finished running). Since Python provides the namespace, these objects are accessible without the need to import a separate module.

Let’s take a look together at the standard built-in namespace! In order to see it, we can use the following statement:

```python
print(dir(__builtins__))
```

This allows us to access the `builtins` module that Python provides for us.

```
['ArithmeticError', 'AssertionError', 'AttributeError', 'BaseException', 'BlockingIOError', 'BrokenPipeError', 'BufferError', 'BytesWarning', 'ChildProcessError', 'ConnectionAbortedError', 'ConnectionError', 'ConnectionRefusedError', 'ConnectionResetError', 'DeprecationWarning', 'EOFError', 'Ellipsis', 'EnvironmentError', 'Exception', 'False', 'FileExistsError', 'FileNotFoundError', 'FloatingPointError', 'FutureWarning', 'GeneratorExit', 'IOError', 'ImportError', 'ImportWarning', 'IndentationError', 'IndexError', 'InterruptedError', 'IsADirectoryError', 'KeyError', 'KeyboardInterrupt', 'LookupError', 'MemoryError', 'ModuleNotFoundError', 'NameError', 'None', 'NotADirectoryError', 'NotImplemented', 'NotImplementedError', 'OSError', 'OverflowError', 'PendingDeprecationWarning', 'PermissionError', 'ProcessLookupError', 'RecursionError', 'ReferenceError', 'ResourceWarning', 'RuntimeError', 'RuntimeWarning', 'StopAsyncIteration', 'StopIteration', 'SyntaxError', 'SyntaxWarning', 'SystemError', 'SystemExit', 'TabError', 'TimeoutError', 'True', 'TypeError', 'UnboundLocalError', 'UnicodeDecodeError', 'UnicodeEncodeError', 'UnicodeError', 'UnicodeTranslateError', 'UnicodeWarning', 'UserWarning', 'ValueError', 'Warning', 'ZeroDivisionError', '__build_class__', '__debug__', '__doc__', '__import__', '__loader__', '__name__', '__package__', '__spec__', 'abs', 'all', 'any', 'ascii', 'bin', 'bool', 'bytearray', 'bytes', 'callable', 'chr', 'classmethod', 'compile', 'complex', 'copyright', 'credits', 'delattr', 'dict', 'dir', 'divmod', 'enumerate', 'eval', 'exec', 'exit', 'filter', 'float', 'format', 'frozenset', 'getattr', 'globals', 'hasattr', 'hash', 'help', 'hex', 'id', 'input', 'int', 'isinstance', 'issubclass', 'iter', 'len', 'license', 'list', 'locals', 'map', 'max', 'memoryview', 'min', 'next', 'object', 'oct', 'open', 'ord', 'pow', 'print', 'property', 'quit', 'range', 'repr', 'reversed', 'round', 'set', 'setattr', 'slice', 'sorted', 'staticmethod', 'str', 'sum', 'super', 'tuple', 'type', 'vars', 'zip']
```

Let’s note a few interesting facts about the objects hosted built-in namespace:

- It contains many of the [built-in functions](https://www.codecademy.com/resources/docs/python/built-in-functions) we are able to use in our Python programs such as `str()`, [`zip()`](https://www.codecademy.com/resources/docs/python/built-in-functions/zip), `slice()`, [`sorted()`](https://www.codecademy.com/resources/docs/python/built-in-functions/sorted), and many more.
- It also hosts many of the exceptions that we may encounter in our programs such as `'ArithmeticError'`, `'IndexError'`, `'KeyError'`, and many more.
- There are even constants like `True` and `False`!

In total there are 152 names that include exceptions, functions, types, special attributes, and other Python built-in objects.

### Global Namespace
The _global namespace_ exists one level below the built-in namespace. Generally, it includes all non-nested names in the module (file) we are choosing to run the Python interpreter on. The [global](https://www.codecademy.com/resources/docs/python/keywords/global) namespace is created when we run our main program and has a lifetime until the interpreter terminates (usually when our program is finished running).

```python
#Imaginary File: main.py
import random

first_name = "Jaya"
last_name = "Bodegard" 

def print_variables():
  random_number = random.randint(0,9)
  print(first_name)
  print(last_name)
  print(random_number)
```

In order to see what objects exist in the global namespace, Python provides the [`globals()`](https://www.codecademy.com/resources/docs/python/built-in-functions/globals) built-in function.

Funnily enough, the `globals()` function actually comes from the built-in namespace (and is thus called a built-in function), and we can access it anywhere in our program (or any program)!

```python
print(globals())
```

```
{'__name__': '__main__', '__doc__': None, '__package__': None, '__loader__': <_frozen_importlib_external.SourceFileLoader object at 0x7f224a7ae4c0>, '__spec__': None, '__annotations__': {}, '__builtins__': <module 'builtins' (built-in)>, '__file__': 'main.py', '__cached__': None, 'random': <module 'random' from '/usr/lib/python3.8/random.py'>, 'first_name': 'Jaya', 'last_name': 'Bodegard', 'print_variables': <function print_variables at 0x7f224a76a1f0>}
```

1. The global namespace contains all of the non-nested objects of our program. This includes the variables `first_name` and `last_name` as well as the function `print_variables`. However, the `random_number` variable is not included in the namespace because it is nested inside of our function.
2. Anytime we use the `import` statement to bring in a new module into our program, instead of adding every name from that module (such as all the names in the `random` module) to our current global namespace, Python will create a new namespace for it. This means there might be potentially multiple global namespaces in a single program.

---

Depending on where we call `globals()` we will have a different namespace generated. This means `globals()` will show the namespace at the time it was executed. Since we called `globals()` a second time after defining a few items (such as variables and functions), those items now show up in the global namespace.

### Local Namespace
In Python, whenever the interpreter executes a function, it will generate a local namespace for that specific function. This namespace only exists inside of the function and remains in existence until the function terminates.

Similar to how we can see the global namespace using a built-in function called [`globals()`](https://www.codecademy.com/resources/docs/python/built-in-functions/globals), Python provides a function called `locals()` to see any generated local namespace.

```python
global_variable = 'global'

def add(num1, num2):
  nested_value = 'Inside Function'   
  print(num1 + num2)
  print(locals())

add(5, 10) 
```

```
15
{'num1': 5, 'num2': 10, 'nested_value': 'Inside Function'}
```

- If we called `locals()` outside of a function in our program, it behaves the same as `globals()`.
- The namespace does not include `global_variable` since it exists outside of the function (in the global namespace).

### Enclosing Namespace
Enclosing namespaces are created specifically when we work with nested [functions](https://www.codecademy.com/resources/docs/python/functions) and just like with the local namespace, will only exist until the function is done executing.

```python
global_variable = 'global'

def outer_function():
  outer_value = "outer"

  def inner_function():
    inner_value = "inner"

 inner_function()

outer_function()
```

The `outer_function()` serves the role of an _enclosing function_ while `inner_function` is an _enclosed function_. By creating this structure, we generate an enclosing namespace - a namespace created by an enclosing function and any number of enclosed functions inside it.

While Python doesn’t give us any particular function like `enclosing()` to visualize the namespace, we can use `locals()` to see when enclosed namespaces are generated.

```python
global_variable = 'global'

def outer_function():
  outer_value = "outer"

  def inner_function():
    inner_value = "inner"
  inner_function()
  # Added locals output
  print(locals())

outer_function()
```

```
{'outer_value': 'outer', 'inner_function': <function outer_function.<locals>.inner_function at 0x7f46b56bc820>}
```

Notice the `'inner_function': <function outer_function.<locals>.inner_function` shows that our local namespace inside of `outer_function()` encloses the local namespace of `inner_function()`.

## Scope

### Introduction to Scope
Scope defines which namespaces our program will look into (to check names) and in what order. While multiple namespaces usually exist at once, this does not mean we can access all of them in different parts of our program!

Similar to namespaces, there are four different levels of scope. These levels are:

1. Built-in Scope 
2. Global Scope
3. Enclosing Scope
4. Local Scope

_**Note:**_ As we explore the ideas around scope, there may be some confusion between what distinguishes the concept of scope and namespaces. While both concepts are interlinked and work together, namespaces are simply the mechanism for storing name-object pairs, while scope will serve as a rule system on where (which point in our code) we can retrieve those names.

### Local Scope
Whenever we decide to call a function, a new _local scope_ will be generated. Each subsequent function call will generate a new local [scope](https://www.codecademy.com/resources/docs/python/scope). Since the local scope is the deepest level of the four scopes, names in a local scope cannot be accessed or modified by any code called in outer scopes. As a rule of thumb, any names created in a local namespace are usually also locally scoped.

```python
def favorite_color(): 
  color = 'Red'

print(color) 
```

In this case, the name of `color` is scoped locally to the function `favorite_color()`. Since the statement `print(color)` is called outside of the function, it has no access to the local scope (and thus the local namespace) inside of `favorite_color()` and returns an error.

However, if we were to refactor our code:

```python
def favorite_color(): 
  color = 'Red'
  print(color) 

favorite_color()
```

Then, we wouldn’t have trouble accessing the name of `color` since now the [`print()`](https://www.codecademy.com/resources/docs/python/built-in-functions/print) function is scoped locally, and our output would return `'Red'`.

### Enclosing/Nonlocal Scope
Similar to how nested [functions](https://www.codecademy.com/resources/docs/python/functions) form a unique namespace within their enclosing functions (the enclosing namespace), there also exist special rules that apply for accessing nested values. These rules make up the _enclosing scope_ (also known as _nonlocal scope_).

```python
def outer_function():
  enclosing_value = 'Enclosing Value'
 
  def nested_function():
    nested_value = 'Nested Value'
    print(enclosing_value)
  
  nested_function()

outer_function()
```

Our output would be:

```
Enclosing Value
```

Enclosing scope allows any value defined in an enclosing function to be accessed in nested functions below it.

There are two caveats to be aware of with enclosing scope:

- The flow of scope access only flows upwards. This means that the deepest level has access to every enclosing namespace above it, but not the other way around. For example, if we tried to access `nested_value` from one level above where it was defined:

```python
def outer_function():
  enclosing_value = 'Enclosing Value'
  print(nested_value)

  def nested_function():
    nested_value = 'Nested Value'

  nested_function()

outer_function()
```

The program would produce an error:

```
NameError: name 'nested_value' is not defined
```

- Immutable objects, such as [strings](https://www.codecademy.com/resources/docs/python/strings) or numbers, can be accessed in nested functions, but cannot be modified. Let’s try to change `enclosing_value` to see this restriction in action:

```python
def outer_function():
  enclosing_value = 'Enclosing Value'
  
  def nested_function():
    enclosing_value += 'changed'
  
  nested_function()
  print(enclosing_value)

outer_function()
```

Would output:

```
UnboundLocalError: local variable 'enclosing_value' referenced before assignment
```

### Modifying Scope Behavior: nonlocal Statement
We just witnessed that we can access names from the enclosing [scope](https://www.codecademy.com/resources/docs/python/scope) with nested [functions](https://www.codecademy.com/resources/docs/python/functions), but we cannot modify them. Python does however provide a way for us to modify names in the enclosing scope, by using the `nonlocal` statement.

```python
def enclosing_function():
  var = "value"

  def nested_function():
    var = "new_value"

  nested_function()

  print(var)

enclosing_function()
```

The output would be:

```
value
```

After using the `nonlocal` statement, the variable is now modifiable from the local scope.

```python
def enclosing_function():
  var = "value"

  def nested_function():
    nonlocal var
    var = "new_value"

  nested_function()
  print(var)

enclosing_function()
```

The output would now be: 

```
new_value
```

### Global Scope
At the highest level of access, we have the _global scope_. Names defined in the [global](https://www.codecademy.com/resources/docs/python/keywords/global) namespace will automatically be globally scoped and can be accessed anywhere in our program.

```python
# global scope variable
gravity = 9.8

def get_force(mass):
  return mass * gravity

print(get_force(60))
```

Would output:

```
588.0
```

However, similar to local [scope](https://www.codecademy.com/resources/docs/python/scope), values can only be accessed but not modified. For example, if we tried to manipulate the value of `gravity`:

```python
# global scope variable
gravity = 9.8

def get_force(mass):
  gravity += 100
  return mass * gravity

print(get_force(60))
```

Would output:

```
UnboundLocalError: local variable 'gravity' referenced before assignment
```

### Modifying Scope Behavior: global Statement
Sometimes, we want to modify a [global](https://www.codecademy.com/resources/docs/python/keywords/global) name from within a local [scope](https://www.codecademy.com/resources/docs/python/scope).

```python
global_var = 10

def some_function():
  global_var = 20

some_function()

print(global_var)
```

The output would be:

```
10
```

Similar to the `nonlocal` statement, Python provides the `global` statement to allow the modification of global names from a local scope.

```python
global_var = 10

def some_function():
  global global_var
  global_var = 20

some_function()

print(global_var)
```

The output would now be:

```
20
```

In addition, the `global` statement can be used even if the name has not been defined in the global namespace. Using the `global` statement would create the new variable in the global namespace.

```python
def some_function():
  global x
  x = 30

some_function()
print(x)
```

This would output:

```
30
```

### Scope Resolution: The LEGB Rule
Scope resolution is a term used to describe a search procedure for a name in the various namespaces. A set of rules dictates the order that the search needs to follow.

In Python, the unofficial rule (often referred to in literature but does not exist in the official documentation) is known as the _LEGB rule_.

LEGB stands for Local, Enclosing, Global, and Built-in. These four letters represent the order of namespaces Python will check to see if a name exists.

```python
age = 27 

def func(): 

  def inner_func():
    print(age)
  inner_func()

func()
```

Would output:

```
27
```

- First, Python looked in the local (The L of LEGB) scope that existed inside of `inner_func()`. This is the lowest level of the LEGB rule and thus where Python starts the search for a name that is trying to be called (in this case via a [`print()`](https://www.codecademy.com/resources/docs/python/built-in-functions/print)). Python then realized the name of `age` isn’t in the local namespace and continues the search to the upper levels of scope.
- The second level Python examined is the enclosing scope (The E of LEGB) of `func()`. Unfortunately, again the name of `age` doesn’t exist in the enclosing namespace, and Python moves upwards to higher scopes.
- Next, Python arrives at the [global](https://www.codecademy.com/resources/docs/python/keywords/global) scope and finds the name of `age` in the global namespace. The search is finished, and the result is returned.

The second scenario to examine is seeing what happens when we have two of the same name in different namespaces.

```python
age = 27 

def func(): 
  age = 42

  def inner_func():
    print(age)
  
  inner_func() 

func()
```

Here the output will be `42` because Python could find a name (`age`) in the enclosing scope and did not continue to search for the value up into the global scope. If Python cannot find a name in any of the four scopes it searches, it will return a `NameError` exception.

# Functions Deep Dive

## Lambda Functions
In Python, a _lambda function_ (also commonly called an _anonymous function_) is a one-line shorthand for function.

Take for example, a function called `add_two()`:

```python
def add_two(my_input):
  return my_input + 2
```

The same function could be written as a lambda function:

```python
add_two = lambda my_input: my_input + 2
```

So this code using the above lambda function:

```python
print(add_two(3))
print(add_two(100))
print(add_two(-2))
```

Would output:

```
5
102
0
```

Let’s break this syntax down:

1. The function is stored in a variable called `add_two`.
2. The `lambda` keyword declares that this is a lambda function (similar to how we use `def` to declare a normal function).
3. `my_input` is a parameter used to hold the value passed to `add_two`.
4. In the lambda function version, we are returning `my_input + 2` without the use of a `return` keyword (the normal Python function explicitly uses the keyword `return`).

Let’s say that we have a function `check_if_A_grade` that outputs `'Got an A!'` if a grade is at least 90, and otherwise says you `'Did not get an A.'`.

```python
print(check_if_A_grade(91))
print(check_if_A_grade(70))
print(check_if_A_grade(20))
```

Would output:

```
'Got an A!'
'Did not get an A.'
'Did not get an A.'
```

We can do this using a conditional _if statement_ in a lambda function, with syntax that looks like this:

```python
check_if_A_grade = lambda grade: 'Got an A!' if grade >= 90 else 'Did not get an A.'
```

If we wanted our function complexity to extend beyond one line, we would opt for a regular function since making our function longer would impair readability.

## Introduction to Higher-Order Functions

### Functions as First-Class Objects
In Python, all functions, including the ones we’ve written, are classified as _first-class objects_ (sometimes also called _first-class citizens_ or _first-class functions_). This means they have four important characteristics:

1. First-class objects can be stored as variables.
2. First-class objects can be passed as arguments to a function.
3. First-class objects can be returned by a function.
4. First-class objects can be stored in data structures (e.g., lists, dictionaries, etc.).

```python
# Here, we assign a function to a variable
uppercase = str.upper 

# And then call it 
big_pie = uppercase("pumpkinpie")

# Here we store two functions in a list  
string_manipulation_functions = [str.upper, str.lower]
```

The fact that functions are first-class objects in Python, and therefore have all the flexibility of objects, enables us to write even more powerful types of functions called _higher-order functions_.

Higher-order functions operate on other functions via arguments or via return values. This means higher-order functions do one or both of the following:

- Accept a function as an argument
- Have a return value that is a function

### Functions as Arguments

```python
def total_bill(func, value):
  total = func(value)
  return total
```

In order to see it in action, let’s define a function called, `add_tax()`, and then pass it to our higher-order `total_bill()` function along with a numeric value:

```python
def add_tax(total):
  tax = total * 0.06
  new_total = total + tax
  return new_total
 
total_bill(add_tax, 100)
```

Would output:

```
106.0
```

Here, `total_bill()` is classified as a higher-order function because it takes in an argument that is a function (`add_tax()` in the above example).

The true power comes when we want to keep a consistent manipulation no matter what function is passed in. We can see this if we modify our `total_bill()` function so it adds formatting to the total amount owed in a consistent and friendly way, regardless of which function is passed in:

```python
def total_bill(func, value):
  total = func(value)
  return ("The total amount owed is $" + "{:.2f}".format(total) + ". Thank you! :)")


print(total_bill(add_tax, 100))
print(total_bill(add_tip, 100))
```

Now, no matter the function we pass as the argument and the behavior we want the function to accomplish, we can always consistently format the total and add a friendly message to the returned result.

### Functions as Arguments - Iteration
Now say we have a list of bills instead of just one, and we want to add tax or tip to each bill, depending on the type of sale it is.

One way to accomplish this could be to write out separate loops: one for sales that need to have tax added and one for sales that should have a tip added. To get a sense of what this would look like, let’s write out the loop for adding tax first:

```python
bills = [115, 120, 42]
 
new_bills = []
 
for i in range(len(bills)):
  total = add_tax(bills[i])
  new_bills.append("Total amount owed is $" + "{:.2f}".format(total) + ". Thank you! :)")

print(new_bills)
```

Would output:

```
['Total amount owed is $121.90. Thank you! :)',
 'Total amount owed is $127.20. Thank you! :)',
 'Total amount owed is $44.52. Thank you! :)']
```

Now, we could write out another loop for when we need to add a tip instead of tax, but we can probably guess how many repetitions would be involved. A much more powerful solution would be to use a higher-order function to apply `add_tax()` or `add_tip()` to each balance in our list.

```python
def total_bills(func, list):
  # This list will store all the new bill values
  new_bills = []

  # This loop will iterate through our bills
  for i in range(len(list)):

    # Here we apply the function to each element of the list!
    total = func(list[i])
    new_bills.append("Total amount owed is $" + "{:.2f}".format(total) + ". Thank you! :)")

  return new_bills
```

Next, let’s use the `add_tax()` function that we wrote before with our new `total_bills()` higher-order function:

```python
bills = [115, 120, 42]
 
bills_w_tax = total_bills(add_tax, bills)
 
print(bills_w_tax)
```

And if we needed to add a tip instead of tax, we could simply swap out the function argument:

```python
bills_w_tip = total_bills(add_tip, bills)
 
print(bills_w_tip)
```

### Functions as Return Values

```python
def make_box_volume_function(height):
    # defines and returns a function that takes two numeric arguments,        
    # length &  width, and returns the volume given the input height
    def volume(length, width):
        return length*width*height

    return volume
 
box_volume_height15 = make_box_volume_function(15)
 
print(box_volume_height15(3,2))
```

Would output:

```
90
```

### Wrap Up

1. Higher-order functions are possible because functions are first-class objects in Python, meaning that a function can be stored as a variable, passed as an argument to a function, returned by a function, and stored in data structures (lists, dictionaries, etc.).
2. Higher-order functions are functions that operate on other functions by taking another function as an argument, returning another function, or both.
3. Higher-order functions can reduce repetition in code, making code easier to read and less prone to mistakes.

## Built-In Higher-Order Functions

### Map
The `map()` higher-order function has the following base structure:

```
returned_map_object = map(function, iterable)
```

When called, `map()` applies the passed function to each and every element in the iterable and returns a `map` object. The returned `map` object holds the results from applying the mapping function to each element in the passed iterable. We will usually convert the `map` into a list to enable viewing and further use.

```python
def double(x):
 return x*2
 
int_list = [3, 6, 9]
 
doubled = map(double, int_list)
 
print(doubled)
```

Would output:

```
<map at 0x7f1ca0f58090>
```

If we want to see the actual results of mapping `double()` to the elements of `int_list`, we need to convert the `map` object to a list using the built-in `list()` function:

```python
print(list(doubled))
```

This would output:

```
[6, 12, 18]
```

Higher-order functions like `map()` work especially well with lambda functions. Because lambda functions are anonymous, we don’t need to define a new named function for `map()` if that function won’t be used again elsewhere. In this case, if we don’t plan on reusing `double()` somewhere else in our program, we can rewrite the `double()` function from the previous example with a lambda function like so:

```python
doubled = map(lambda input: input*2, int_list)
 
print(list(doubled))
```

### Filter
Similar to `map()`, the `filter()` function takes a function and an iterable as arguments. Just as the name suggests, the goal of the `filter()` function is to “filter” values out of an iterable.

The filtering function should be a function that returns a boolean value: `True` or `False`. The returned `filter` object will hold only those elements of the passed iterable for which the filtering function returned `True`.

```python
names = ["margarita", "Linda", "Masako", "Maki", "Angela"]
 
M_names = filter(lambda name: name[0] == "M" or name[0] == "m", names) 
 
print(list(M_names))
```

This would output:

```
['margarita', 'Masako', 'Maki']
```

### Reduce

1. In contrast to the `map()` and `filter()` functions that are always available, the `reduce()` function must be imported from the `functools` module to use it.
2. Rather than returning a `reduce` object as might be expected after learning about `map()` and `filter()`, `reduce()` returns a single value. To get to this single value, `reduce()` cumulatively applies a passed function to each sequential pair of elements in an iterable.

```python
from functools import reduce
 
int_list = [3, 6, 9, 12]
 
reduced_int_list = reduce(lambda x,y: x*y, int_list)
 
print(reduced_int_list)
```

This would output:

```
1944
```

### Wrap Up

1. The `map()` function applies a passed function to each element in an iterable and returns a `map` object.
2. The `filter()` function applies a filtering function (a function that returns a boolean) to each element in an iterable. `filter()` returns a `filter` object with only the elements for which the filtering function returned `True`.
3. `reduce()` must be imported from the `functools` module. It reduces an iterable to a single value by cumulatively applying a passed function to the first pair of elements in the iterable and then each sequential element with the return value.
4. These three functions streamline code on their own, but they are even easier to read when they are used in conjunction with lambda functions.

## Decorators

### Decorating a function

```python
def title_decorator(print_name_function):
	def wrapper():
		print("Professor:")
		print_name_function()
	return wrapper

def print_my_name():
	print("Fanjo")

decorated_function = title_decorator(print_my_name)
decorated_function()
```

### Decorators

```python
def title_decorator(print_name_function):
	def wrapper():
		print("Professor:")
		print_name_function()
	return wrapper

@title_decorator
def print_my_name():
	print("Fanjo")

print_my_name()
```

### Decorators with parameters

```python
def title_decorator(print_name_function):
	def wrapper(*args, **kwargs):
		print("Professor:")
		print_name_function(*args, **kwargs)
	return wrapper

@title_decorator
def print_my_name(name, age):
	print(name + " you are " + str(age))

print_my_name("Shelby", 50)
```

# Object-Oriented Programming

## Object-Oriented Programming

### Introduction to Object-Oriented Programming
In programming, most languages offer various features that give us different ways to tackle technical problems. With so many different languages out there, with their own unique set of features, it became necessary to create a classification system to help distinguish those [sets](https://www.codecademy.com/resources/docs/python/sets) of features. This ultimately led to the creation of the term _programming paradigm_ - a way to classify different programming languages and the unique features that they offered.

As we explore Python deeper, our code might fall into multiple paradigm categories at once. This is because most modern-day languages offer more than one specific paradigm we can program in.

At the forefront of any language classified as an OOP language, there must exist the ability to create programs around [classes](https://www.codecademy.com/resources/docs/python/classes) and objects.

```python
class Dog:
  sound = "Woof"

  def __init__(self, name, age):
    self.name = name
    self.age = age

  def bark(self):
    print(Dog.sound)
```

To explore the paradigm further, we will examine the four core pillars of OOP:

- Inheritance
- Polymorphism
- Abstraction
- Encapsulation

### OOP Pillar: Inheritance

```python
class Dog:

  def bark(self):
    print('Woof!')

class Cat:

  def meow(self):
    print('Meow!')
```

Now, what if we wanted to give both of these classes the ability to eat by calling a method called `eat()`. We could write the method twice in both classes but then we would be repeating code! We also may need to write it inside every specific animal class we ever create. Instead, we can utilize the power of inheritance.

Since both `Cat` and `Dog` fall under the classification of `Animal` we can create a _parent class_ to represent properties and methods they can both share!

```python
class Animal: 
  def eat(self): 
    print("Nom Nom Nom...eating food!")
```

Great, we have an `Animal` class with a `eat()` method, but how do we actually get the `Dog` and `Cat` class to **inherit** this method so it can be shared with both classes? Well here is what the base structure will look like:

```python
class ParentClass:
  #class methods/properties...

class ChildClass(ParentClass):
  #class methods/properties...
```

If we apply this structure to our example, our code looks like this:

```python
class Dog(Animal):
  def bark(self):
    print('Bark!')

class Cat(Animal):
  def meow(self):
    print('Meow!')
```

Now, let’s see inheritance in action:

```python
fluffy = Dog()
zoomie = Cat()

fluffy.eat() # Nom Nom Nom...eating food!
zoomie.eat() # Nom Nom Nom...eating food!
```

### Overriding Methods
When implementing [inheritance](https://www.codecademy.com/resources/docs/python/inheritance), a child class may want to change the behavior of a method from its parent class. In Python, all we have to do is _override_ a method definition. An overriding method in a subclass is one that has the same definition as the parent class but contains different behavior.

```python
class Animal:
  def __init__(self, name):
    self.name = name

  def make_noise(self):
    print("{} says, Grrrr".format(self.name))

pet1 = Animal("Rex")
pet1.make_noise() # Rex says, Grrrr
```

If we define a subclass of `Animal` we may want to make a different sound.

```python
class Cat(Animal):

  def make_noise(self):
    print("{} says, Meow!".format(self.name))

pet2 = Cat("Maisy")
pet2.make_noise() # Maisy says, Meow!
```

### super()
When overriding methods we sometimes want to still access the behavior of the parent method. In order to do that we need a way to call the method of the parent class. Python gives us a way to do that using [`super()`](https://www.codecademy.com/resources/docs/python/built-in-functions/super).

`super()` gives us a _proxy object_. With this proxy object, we can invoke the method of an object’s parent class (also called its superclass). We call the required function as a method on `super()`:

```python
class Animal:
  def __init__(self, name, sound="Grrrr"):
    self.name = name
    self.sound = sound

  def make_noise(self):
    print("{} says, {}".format(self.name, self.sound))

class Cat(Animal):
  def __init__(self, name):
    super().__init__(name, "Meow!") 

pet_cat = Cat("Rachel")
pet_cat.make_noise() # Rachel says, Meow!
```

`super()` is used in subclasses to invoke a needed behavior from the superclass alongside the behavior of a subclass method.

### Multiple Inheritance
One form of multiple [inheritance](https://www.codecademy.com/resources/docs/python/inheritance) is when there are multiple levels of inheritance. This means a class inherits members from its superclass and its super-superclass.

```python
class Animal:
  def __init__(self, name):
    self.name = name
 
  def say_hi(self):
    print("{} says, Hi!".format(self.name))

class Cat(Animal):
  pass

class Angry_Cat(Cat):
  pass

my_pet = Angry_Cat("Mr. Cranky")
my_pet.say_hi() # Mr. Cranky says, Hi!
```

Another form of multiple inhertance involves a subclass that inherits directly from two [classes](https://www.codecademy.com/resources/docs/python/classes) and can use the attributes and methods of both.

```python
class Animal:
  def __init__(self, name):
    self.name = name

class Dog(Animal):
  def action(self):
    print("{} wags tail. Awwww".format(self.name))

class Wolf(Animal):
  def action(self):
    print("{} bites. OUCH!".format(self.name))

class Hybrid(Dog, Wolf):
  def action(self):
    super().action()
    Wolf.action(self)

my_pet = Hybrid("Fluffy")
my_pet.action() # Fluffy wags tail. Awwww
                # Fluffy bites. OUCH!
```

Care must be taken when creating an inheritance structure like this, especially when using the [`super()`](https://www.codecademy.com/resources/docs/python/built-in-functions/super) method. In the above example, calling `super().action()` inside the `Hybrid` class invokes the `.action()` method of the `Dog` class. This is due to it being listed before `Wolf` in the `Hybrid(Dog, Wolf)` definition.

The line `Wolf.action(self)` calls the `Wolf` class `.action()` method. The important thing to note here is that `self` is passed as an argument. This ensures that the `.action()` method in `Wolf` receives the `Hybrid` class instance to output the correct `name`.

### OOP Pillar: Polymorphism
In computer programming, _polymorphism_ is the ability to apply an identical operation onto different types of objects. This can be useful when an object type may not be known at the program runtime.

```python
class Animal:
  def __init__(self, name):
    self.name = name

  def make_noise(self):
    print("{} says, Grrrr".format(self.name))

class Cat(Animal):

  def make_noise(self):
    print("{} says, Meow!".format(self.name))

class Robot:
  
  def make_noise(self):
    print("beep.boop...BEEEEP!!!")
```

The identical method name with different behaviors is a form of polymorphism.

```python
an_animal = Animal("Bear")
my_pet = Cat("Maisy")
my_vacuum = Robot()
objects = [an_animal, my_pet, my_vacuum]
for o in objects:
  o.make_noise()

# OUTPUT
# "Bear says, Grrrr"
# "Maisy says, Meow!"
# "beep.boop...BEEEEP!!!"
```

With the [classes](https://www.codecademy.com/resources/docs/python/classes) instantiated and added to a list, we are able to iterate through the list and call `.make_noise()`. This is done without needing to know what type of class `.make_noise()` belongs to.

### Dunder Methods
The code below shows that when working with different object types like, `int`, `str` or `list`, the `+` operator performs different [functions](https://www.codecademy.com/resources/docs/python/functions). This is known as _operator overloading_ and is another form of polymorphism.

```python
# For an int and an int, + returns an int
2 + 4 == 6

# For a string and a string, + returns a string
"Is this " + "addition?" == "Is this addition?"

# For a list and a list, + returns a list
[1, 2] + [3, 4] == [1, 2, 3, 4]
```

To implement this behavior, we must first discuss _dunder methods_. Every defined class in Python has access to a group of these special methods. We’ve explored a few already, the constructor [`__init__()`](https://www.codecademy.com/resources/docs/python/dunder-methods/init) and the string representation method [`__repr__()`](https://www.codecademy.com/resources/docs/python/dunder-methods/repr). The name dunder method is derived from the **D**ouble **UNDER**scores that surround the name of each method.

Defining a class’s [dunder methods](https://www.codecademy.com/resources/docs/python/dunder-methods) is a way to perform operator overloading.

```python
class Animal:
  def __init__(self, name):
    self.name = name

  def __repr__(self):
    return self.name

  def __add__(self, another_animal):
    return Animal(self.name + another_animal.name)

a1 = Animal("Horse")
a2 = Animal("Penguin")
a3 = a1 + a2
print(a1) # Prints "Horse"
print(a2) # Prints "Penguin"
print(a3) # Prints "HorsePenguin"
```

```python
class Employee():
  new_id = 1
  def __init__(self):
    self.id = Employee.new_id
    Employee.new_id += 1

class Meeting:
  def __init__(self):
    self.attendees = []
  
  def __add__(self, employee):
    print("ID {} added.".format(employee.id))
    self.attendees.append(employee)

  # Write your code
  def __len__(self):
    return len(self.attendees)
    
e1 = Employee()
e2 = Employee()
e3 = Employee()
m1 = Meeting()

m1 + e1
m1 + e2
m1 + e3
print(len(m1))
```

### OOP Pillar: Abstraction
When a program starts to get big, [classes](https://www.codecademy.com/resources/docs/python/classes) might start to share functionality or we may lose sight of the purpose of a class’s [inheritance](https://www.codecademy.com/resources/docs/python/inheritance) structure. In order to alleviate issues like this, we can use the concept of _abstraction_.

Abstraction helps with the design of code by defining necessary behaviors to be implemented within a class structure. By doing so, abstraction also helps avoid leaving out or overlapping class functionality as class hierarchies get larger.

```python
from abc import ABC, abstractmethod

class Animal(ABC):
  def __init__(self, name):
    self.name = name

  @abstractmethod
  def make_noise(self):
    pass

class Cat(Animal):
  def make_noise(self):
    print("{} says, Meow!".format(self.name))

class Dog(Animal):
  def make_noise(self):
    print("{} says, Woof!".format(self.name))

kitty = Cat("Maisy")
doggy = Dog("Amber")
kitty.make_noise() # "Maisy says, Meow!"
doggy.make_noise() # "Amber says, Woof!"
```

The `Animal` class now inherits from an imported class `ABC`, which stands for Abstract Base Class.

This is the first step to making `Animal` an abstract class that cannot be instantiated. The second step is using the imported decorator `@abstractmethod` on the empty method `.make_noise()`.

The below line of code would throw an error.

```python
an_animal = Animal("Scruffy")

# TypeError: Can't instantiate abstract class Animal with abstract method make_noise
```

The abstraction process defines what an `Animal` is but does not allow the creation of one. The `.__init__()` method still requires a name, since we feel all animals deserve a name.

The `.make_noise()` method exists since all animals make some form of noise, but the method is not implemented since each animal makes a different noise. Each subclass of `Animal` is now required to define their own `.make_noise()` method or an error will occur.

### OOP Pillar: Encapsulation
_Encapsulation_ is the process of making methods and data hidden inside the object they relate to. Languages accomplish this with what are called access modifiers like:

- Public
- Protected
- Private

In general, public members can be accessed from anywhere, protected members can only be accessed from code within the same module and private members can only be accessed from code within the class that these members are defined.

Python doesn’t have any inbuilt mechanism to prevent access from any member (i.e. all members are public in Python). However, there is a common convention amongst developers to use a single underscore `self._x` to indicate that a member is protected. Accessing a protected member outside of the module will not cause an error, it is added by developers to inform other developers that they should be careful when accessing this member in such a manner.

Similarly, we can declare a member as private with two leading underscores `self.__x`. This is more than just a convention in Python because of a mechanism called _name mangling_. Members that are preceded with two underscores have their names modified in the background to `obj._Classname__x`. While they can still be publicly accessed, the purpose of this mechanism is to prevent clashing member names of any inheriting [classes](https://www.codecademy.com/resources/docs/python/classes) that might define a member of the same name.

Note that this is different from the [dunder methods](https://www.codecademy.com/resources/docs/python/dunder-methods) we discussed earlier. A dunder method has two leading and two trailing underscores and is treated differently than a private member. One important difference is that dunder method names are not mangled.

---

`dir()` is a built-in Python function that returns a list of all class members, including dunder methods.

### Getters, Setters and Deleters
Using _getter_, _setter_, and _deleter_ [functions](https://www.codecademy.com/resources/docs/python/functions) are one way to implement encapsulation within Python where the state of class attributes can be handled within the class. These functions are useful in making sure that the data being handled is appropriate for the defined class functionality.

```python
class Animal:
  def __init__(self, name):
    self._name = name
    self._age = None

  def get_age(self):
    return self._age

  def set_age(self, new_age):
    if isinstance(new_age, int):
      self._age = new_age
    else:
      raise TypeError

  def delete_age(self):
    print("_age Deleted")
    del self._age

a = Animal("Rufus")
print(a.get_age()) # None

a.set_age(10)
print(a.get_age()) # 10

a.set_age("Ten") # Raises a TypeError

a.delete_age() # "_age Deleted"
print(a.get_age()) # Raises a AttributeError
```

### Review
We discussed the four pillars of object-oriented programming as they apply to the Python programming language.

- [Inheritance](https://www.codecademy.com/resources/docs/python/inheritance)

Python allows [classes](https://www.codecademy.com/resources/docs/python/classes) to inherit on multiple levels. Meaning a class can inherit from a base class as well as a derived class. Python also supports multiple inheritance, where one class can inherit from any number of other classes. This allows us to describe complex relationships between objects with minimal repeated code.

- Polymorphism

Polymorphism is a concept that allows [functions](https://www.codecademy.com/resources/docs/python/functions) and objects to behave in different ways depending on context. There is the polymorphism of functions like [`len()`](https://www.codecademy.com/resources/docs/python/built-in-functions/len) or the addition operator `+`, which can act differently depending on the provided data.

- Abstraction

Python supports the concept of abstraction by allowing objects with methods that have the same name, to be called in a general manner. Further, Python provides the Abstract Base Class (ABC) for us to create a more clearly defined interface.

- Encapsulation

Python’s approach to encapsulation is unique compared to most other object-oriented programming languages. In Python, all members of an object are publicly accessible but there are conventions to indicate to developers that a member is intended to be protected or private.

## The @property Decorator

### Introduction
Let’s start by looking at an example class called `Box` with one attribute called `weight`. In this case, `weight` will be a private attribute with a getter and a setter (`getWeight()` and `setWeight()`).

```python
class Box:
  def __init__(self, weight):
    self.__weight = weight

  def getWeight(self):
    return self.__weight
 
  def setWeight(self, weight):
    if weight >= 0:
      self.__weight = weight
```

### The built-in property() function
The Python built-in `property()` function accepts four optional arguments: `fget`, `fset`, `fdel`, and `doc`. The first three represent getter, setter, and deleter methods, respectively, and the last one is a docstring for the attribute.

```python
class Box:
  def __init__(self, weight):
    self.__weight = weight

  def getWeight(self):
    return self.__weight
 
  def setWeight(self, weight):
    if weight >= 0:
      self.__weight = weight

  def delWeight(self):
    del self.__weight

  weight = property(getWeight, setWeight, delWeight, "Docstring for the 'weight' property")
```

We then call the `property()` function and pass the getter, setter, and deleter in as arguments. This will immediately allow us to use the following syntax for our class:

```python
box = Box(10)

print(box.weight) #this calls .getWeight()

box.weight = 5 #this called .setWeight()

del box.weight #this calls .delWeight()

box.weight = -5 #box.__weight is unchanged 
```

- We can now use the `weight` attribute as if it was public. We no longer have to call the setters, getters, and deleter methods directly and thus giving our program a simpler syntax.
- Even though we no longer call the methods directly, we still can maintain constraints such as the weight limit in `setWeight()`. It’s the best of both worlds!
- If we had a huge codebase that used our methods multiple times in multiple places, a single change to the method name would seriously mess up our program since we would have to change it everywhere! We no longer have this issue using the `property()` method since we never call it directly.

### @property Decorator
The most pythonic way to define getters, setters, and deleters is by using the `@property` decorator. This decorator is syntactic sugar for using the `property()` function and helps our code look much cleaner.

```python
class Box:
 def __init__(self, weight):
   self.__weight = weight

 @property
 def weight(self):
   """Docstring for the 'weight' property"""
   return self.__weight


 @weight.setter
 def weight(self, weight):
   if weight >= 0:
     self.__weight = weight

 @weight.deleter
 def weight(self):
   del self.__weight
```

- First, we have renamed all of our methods to simply be `weight()`.
- Then we denoted our getter with a `@property`. This marks the property to be used as a prefix for decorating the setter and deleter methods.
- Lastly, we use `@weight.setter` and `@weight.deleter` to define our setter and deleter methods, respectively.

### Wrap up
When using the decorator, remember three rules:

- All three methods must use the same member name (ex. `weight`).
- The first method must be the getter and is identified using `@property`.
- The decorators for the setter and deleter are defined by the name of the method `@property` is used with.

# Unit Testing

## Exceptions

### Introduction to Exceptions
At this point, we are probably very familiar with the most common type of error: a _syntax error_. Syntax errors are mistakes in the structure of Python code. They are caught during a special parsing stage before a program is executed. They always prevent the entire program from running.

As opposed to a syntax error, an exception is a different kind of error that can occur with syntactically correct code. Exceptions are _runtime errors_ because they occur during program execution, only when the offending code (the code causing the error) is reached. An example of an exception, and one we have probably seen before, is a `NameError`:

```
Traceback (most recent call last):
  File "script.py", line 1, in <module>
    print(five)
NameError: name 'five' is not defined
```

Although the `NameError` has a similar output to a `SyntaxError` (both end with `Error`), it falls under the category of exceptions. Exceptions and syntax errors make up the two core categories for any error we will run into.

![[Pasted image 20240319113212.png]]

Luckily, as we saw in the example above, Python gives us a tool for gaining insight into exceptions - the _traceback_. A traceback is a summary that includes the exception type, a message, and the series of function calls preceding the exception, along with file names and line numbers.

### Built-in Exceptions
The `NameError` is just one of the many _built-in exceptions_ — exceptions that are built into the Python language. Other built-in exceptions cover fields ranging from mathematical [errors](https://www.codecademy.com/resources/docs/python/errors) all the way to operating system errors.

Exceptions are objects just like anything else. Most exceptions inherit directly from a class called `Exception`; however, they all are derived directly or indirectly from the `BaseException` class. We can examine the base [classes](https://www.codecademy.com/resources/docs/python/classes) by using the `__bases__` attribute on any specific exception:

```python
print(NameError.__bases__)
```

Will output:

```
<class 'Exception'>
```

We can even call `__bases__` on the `Exception` class to see its origins:

```python
print(Exception.__bases__)
```

Will output:

```
<class 'BaseException'>
```

The full hierarchy of built-in exceptions is the following:

```
BaseException
 +-- Exception
      +-- StopIteration
      +-- StopAsyncIteration
      +-- ArithmeticError
      |    +-- FloatingPointError
      |    +-- OverflowError
      |    +-- ZeroDivisionError
      +-- AssertionError
      +-- AttributeError
      +-- BufferError
      +-- EOFError
      +-- ImportError
      |    +-- ModuleNotFoundError
      +-- LookupError
      |    +-- IndexError
      |    +-- KeyError
      +-- MemoryError
      +-- NameError
      |    +-- UnboundLocalError
      +-- OSError
      |    +-- BlockingIOError
      |    +-- ChildProcessError
      |    +-- ConnectionError
      |    |    +-- BrokenPipeError
      |    |    +-- ConnectionAbortedError
      |    |    +-- ConnectionRefusedError
      |    |    +-- ConnectionResetError
      |    +-- FileExistsError
      |    +-- FileNotFoundError
      |    +-- InterruptedError
      |    +-- IsADirectoryError
      |    +-- NotADirectoryError
      |    +-- PermissionError
      |    +-- ProcessLookupError
      |    +-- TimeoutError
      +-- ReferenceError
      +-- RuntimeError
      |    +-- NotImplementedError
      |    +-- RecursionError
      +-- SyntaxError
      |    +-- IndentationError
      |         +-- TabError
      +-- SystemError
      +-- TypeError
      +-- ValueError
      |    +-- UnicodeError
      |         +-- UnicodeDecodeError
      |         +-- UnicodeEncodeError
      |         +-- UnicodeTranslateError
```

We can find details on each of the exceptions listed above in the [Python documentation](https://docs.python.org/3/library/exceptions.html#built-in-exceptions).

### Raising Exceptions
Encountering exceptions isn’t always an accident. We can throw an exception at any time by using the `raise` keyword, even when Python would not normally throw it.

We might want to raise an exception anytime we think a mistake has or will occur in our program. This lets us stop program execution immediately and provide a useful error message instead of allowing mistakes to occur that may be difficult to diagnose at a later point.

One way to use the `raise` keyword is by pairing it with a specific exception class name. We can either call the class by itself or call a constructor and provide a specific error message.

```python
raise NameError
# or 
raise NameError('Custom Message')
```

When only the class name is provided (as in the first example), Python calls the constructor method for us without any arguments (and thus no custom message will come up).

For a more concrete example, let’s examine raising a `TypeError` for a function that checks if an employee tries to open the cash register but does not have the correct access:

```python
def open_register(employee_status):
  if employee_status == 'Authorized':
    print('Successfully opened cash register')
  else:
    # Alternatives: raise TypeError() or TypeError('Message')
    raise TypeError
```

Alternatively, when no built-in exception makes sense for the type of error our program might experience, it might be better to use a generic exception with a specific message. This is where we can use the base `Exception` class and provide a single argument that serves as the error message.

```python
def open_register(employee_status):
  if employee_status == 'Authorized':
    print('Successfully opened cash register')
  else:
    raise Exception('Employee does not have access!')
```

### Try / Except
So far, the exceptions we’ve encountered have caused our programs to stop executing. However, it is possible for programs to continue executing even after encountering an exception. This process is known as _exception handling_ and is accomplished using the Python `try`/`except` clauses.

![[Pasted image 20240319114644.png]]

- Python will first attempt to execute code inside the `try` clause code block.
- If no exception is encountered in the code, the `except` clause is skipped and the program continues normally.
- If an exception does occur inside of the `try` code block, Python will immediately stop executing the code and begin executing the code inside the `except` code block (sometimes called a _handler_).

```python
colors = {
    'red': '#FF0000',
    'blue': '#0000FF',
    'yellow': '#FFFF00',
}

for color in ('red', 'green', 'yellow'):
  try:
    print('The hex value of ' + color + ' is ' + colors[color])
  except:
    print('An exception occurred! Color does not exist.')
  print('Loop continues...')
```

```
The hex value of red is #FF0000
Loop continues...
An exception occurred! Color does not exist.
Loop continues...
The hex value of yellow is #FFFF00
Loop continues...
```

Exception handling is a powerful tool that lets us gain more flexibility in dealing with [errors](https://www.codecademy.com/resources/docs/python/errors) in our applications. We can use it to perform an action multiple times until it succeeds, or perhaps simply print a message when a non-critical part of our program doesn’t work properly.

### Catching Specific Exceptions
The exception handlers from the previous exercise handled any exception hit during the `try` clause. However, in most cases, we will have an idea of the types of exceptions that might occur within our code. It is generally considered best practice to be as specific as possible with the exceptions we want to raise unless there is a specific reason for catching any type of exception.

We can catch a specific exception by listing it after the `except` keyword.

```python
try:
    print(undefined_var)
except NameError:
    print('We hit a NameError')
```

If any other exception occurs, it is unhandled, and the program terminates.

When we specify exception types, Python also allows us to capture the exception object using the `as` keyword. The exception object hosts information about the specific error that occurred.

```python
try:
    print(undefined_var)
except NameError as errorObject:
    print('We hit a NameError')
    print(errorObject)
```

Would output:

```
We hit a NameError
name 'undefined_var' is not defined
```

### Handling Multiple Exceptions
We can list more than one exception type in a tuple with a single `except` clause.

```python
try:
    # Some code to try!
except (NameError, ZeroDivisionError) as e:
    print('We hit an Exception!')
    print(e)
```

In the above example, we expect to encounter either a `NameError` or a `ZeroDivisionError`. We can list any number of exceptions in this tuple format as long as it makes sense for the code in our `try` block. This is where we can see the benefit of capturing our exception object (via the `as` clause) since it enables us to print (or operate on) the specific exception that is caught.

In addition to catching multiple exceptions, we can also pair multiple `except` clauses with a single `try` clause, enabling specific exceptions to be handled differently.

```python
try:
    # Some code to try!
except NameError:
    print('We hit a NameError Exception!')
except KeyError:
    print('We hit a TypeError Exception!')
except Exception:
    print('We hit an exception that is not a NameError or TypeError!')
```

Note that the order of handlers is important here - if an exception is encountered, Python will execute the first one that matches its type. In this case, and a valid strategy for exception handling, we use the last `except` clause as a generic `Exception` as a backup if no other specific exception gets caught.

### The else Clause
We’ve seen how exception handlers get executed when we encounter exceptions during a `try` clause - but what if we want to run some code only if we do not encounter an exception? Python provides us a way to do this as well - the `else` clause.

![[Pasted image 20240319125436.png]]

```python
try:
  check_password()
except ValueError:
  print('Wrong Password! Try again!')
else:
  login_user()
  # 20 other lines of imaginary code
```

Now, one could argue, we could have written our program a different way to achieve a similar outcome:

```python
try:
  check_password()
  login_user()
  # 20 other lines of imaginary code
except ValueError:
  print('Wrong Password! Try again!')
```

Here, if our `check_password()` ever fails, we will be able to catch the exception just like before. Python does offer a bit of insight on this scenario in the official documentation:

> The use of the else clause is better than adding additional code to the try clause because it avoids accidentally catching an exception that wasn’t raised by the code being protected by the try … except statement.

This suggestion is valid in this case since in the alternative style, the `ValueError` could occur in any of the other lines of code other than `check_password()`, and it would be challenging to tell where it came from.

### The finally Clause
With `try`/`except`/`else`, we’ve seen how to run certain code when an exception occurs and other code when it does not. There is also a way to execute code regardless of whether an exception occurs - the `finally` clause.

![[Pasted image 20240319131917.png]]

```python
try:
  check_password()
except ValueError:
  print('Wrong Password! Try again!')
else:
  login_user()
  # 20 other lines of imaginary code
finally:
  load_footer()
```

The one change we made was we added the `finally` clause to execute no matter if the user fails to login or not. In either case, we use an imaginary function called `load_footer()` to load the page’s footer. Since the footer area of our imaginary application stays the same for both states, we always want to load it, and thus call it inside of the `finally` clause.

Note that the `finally` clause can be used independently (without an `except` or `else` clause). This is a convenient way to guarantee that a behavior will occur, regardless of whether an exception occurs:

```python
try:
    check_password()
finally:
    load_footer()
    # Other code we always want to run 
```

### User-defined Exceptions
Python gives us the ability to create _user-defined exceptions_.

User-defined exceptions are exceptions that we create to allow for better readability in our program’s [errors](https://www.codecademy.com/resources/docs/python/errors).

```python
class CustomError(Exception):
    pass
```

All we have to do to create a custom exception is to derive a subclass from the built-in `Exception` class. Although not required, most custom exceptions end in “Error” similar to the naming of the built-in exceptions.

If someone tries to schedule a delivery but their address is too far, we want to raise a custom `LocationTooFarError` exception. This isn’t a type of exception that is built into Python, but rather one that is specific to our program and use case.

```python
class LocationTooFarError(Exception):
   pass

def schedule_delivery(distance_from_store):
    if distance_from_store > 10:
        raise LocationTooFarError
    else:
        print('Scheduling the delivery...')
```

Now, if we call `schedule_delivery(20)`, we get the following output:

```
Traceback (most recent call last):
  File "inventory.py", line 10, in <module>
    schedule_delivery(20)
  File "inventory.py", line 6, in schedule_delivery
    raise LocationTooFarError
__main__.LocationTooFarError
```

Since our class name populates into the traceback, even this simple class proves to be more useful than a generic `Exception` object or any built-in types!

### Customizing User-defined Exceptions
Let’s say we wanted to expand our `LocationTooFarError` exception from earlier to also provide a custom error message.

```python
class LocationTooFarError(Exception):
   def __init__(self, distance):
       self.distance = distance
       
   def __str__(self):
        return 'Location is not within 10 km: ' + str(self.distance)
```

- The reason for taking in a distance is to use it in our `__str__` method that will return a custom error message when the exception is hit!
- The `__str__` method provides our exception a custom message by returning a string with the distance property from the constructor.

```python
def schedule_delivery(distance_from_store):
    if distance_from_store > 10:
        raise LocationTooFarError(distance_from_store)
    else:
        print('Scheduling the delivery...')
```

We would see our expanded custom exception in action:

```
Traceback (most recent call last):
  File "inventory.py", line 14, in <module>
    schedule_delivery(20)
  File "inventory.py", line 11, in schedule_delivery
    raise LocationTooFarError(distance_from_store)
__main__.LocationTooFarError: Location is not within 10 km: 20
```

## Unit Testing

### Introduction to Testing
The world of testing can generally be divided into two categories:

- Manual Testing:
    - With manual testing, a physical person interacts with software much as a user would.
- Automated Testing:
    - With automated testing, tests are performed with code. Generally, automated testing is faster and less prone to human error.

### The assert Statement
Python provides an easy way to perform simple tests in our code - the [`assert`](https://www.codecademy.com/resources/docs/python/keywords/assert) statement. An `assert` statement can be used to test that a condition is met. If the condition evaluates to `False`, an `AssertionError` is raised with an optional error message.

```
assert <condition>, 'Message if condition is not met'
```

Consider the following example that demonstrates the `assert` statement paired with a function called `times_ten`.

```python
def times_ten(number):
    return number * 100

result = times_ten(20)
assert result == 200, 'Expected times_ten(20) to return 200, instead got ' + str(result)
```

```
AssertionError: Expected times_ten(20) to return 200, instead got 2000
```

### Unit Testing
Generally, we can start by testing the smallest unit of a program. 

In programming, these types of individual tests are called _unit tests_. A unit test validates a single behavior and will make sure all of the units of a program are functioning properly.

To test a single function, we might create several _test cases_. A test case validates that a specific set of inputs produces an expected output for the unit we are trying to test.

```python
# The unit we want to test
def times_ten(number):
    return number * 10

# A unit test function with a single test case
def test_multiply_ten_by_zero():
    assert times_ten(0) == 0, 'Expected times_ten(0) to return 0'
```

We can improve our testing coverage of this function by adding some more test cases with different inputs. A common approach is to create test cases for specific edge case inputs as well as reasonable ones.

```python
def test_multiply_ten_by_one_million():
    assert times_ten(1000000) == 10000000, 'Expected times_ten(1000000) to return 10000000'

def test_multiply_ten_by_negative_number():
    assert times_ten(-10) == -100, 'Expected times_ten(-10) to return -100'
```

### Python's unittest Framework
There are some problems with the approach to our previous unit tests that would make them difficult to maintain. First, we had to call each function specifically when a new test was created. We also didn’t have any way of grouping tests, which is necessary when the number of tests increases. Perhaps most importantly, if one test failed, the `AssertionError` would prevent any remaining tests from running!

Luckily, Python provides a framework that solves these problems and provides many other tools for writing unit tests. This framework lives in the `unittest` module which is included in the standard library.

```python
import unittest

#The rest of our program….
```

The `unittest` module provides us with a _test runner_. A test runner is a component that collects and executes tests and then provides results to the user. The framework also provides many other tools for test grouping, setup, teardown, skipping, and other features.

First, we must create a class which inherits from `unittest.TestCase`, as follows:

```python
import unittest 

class TestTimesTen(unittest.TestCase):
    pass
```

This class will serve as the main storage of all our unit testing [functions](https://www.codecademy.com/resources/docs/python/functions). Once we have the class, we need to change our test functions so that they are methods of the class. The `unittest` module requires that test functions begin with the word `'test'`.

```python
import unittest

class TestTimesTen(unittest.TestCase):
    def test_multiply_ten_by_zero(self):
        pass

    def test_multiply_ten_by_one_million(self):
        pass

    def test_multiply_ten_by_negative_number(self):
        pass
```

Lastly, we need to change our [`assert`](https://www.codecademy.com/resources/docs/python/keywords/assert) statements to use the `assertEqual` method of `unittest.TestCase`. The framework requires that we use special methods instead of standard `assert` statements.

```python
import unittest

class TestTimesTen(unittest.TestCase):
    def test_multiply_ten_by_zero(self):
        self.assertEqual(times_ten(0), 0, 'Expected times_ten(0) to return 0')

    def test_multiply_ten_by_one_million(self):
        self.assertEqual(times_ten(1000000), 10000000, 'Expected times_ten(1000000) to return 10000000')

    def test_multiply_ten_by_negative_number(self):
        self.assertEqual(times_ten(-10), -100, 'Expected add_times_ten(-10) to return -100')
```

Now we can run our tests by calling `unittest.main()`. The `unittest` framework will work its magic to detect any tests in the existing module, run them, and provide us results.

```python
# Importing unittest framework
import unittest

# Function that gets tested
def times_ten(number):
    return number * 100

# Test class
class TestTimesTen(unittest.TestCase):
    def test_multiply_ten_by_zero(self):
        self.assertEqual(times_ten(0), 0, 'Expected times_ten(0) to return 0')

    def test_multiply_ten_by_one_million(self):
        self.assertEqual(times_ten(1000000), 10000000, 'Expected times_ten(1000000) to return 10000000')

    def test_multiply_ten_by_negative_number(self):
        self.assertEqual(times_ten(-10), -100, 'Expected add_times_ten(-10) to return -100')

# Run the tests
unittest.main()
```

When we run this code, we would see the following output:

```
FF.
======================================================================
FAIL: test_multiply_ten_by_negative_number (__main__.TestTimesTen)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "scratch.py", line 16, in test_multiply_ten_by_negative_number
    self.assertEqual(times_ten(-10), -100, 'Expected add_times_ten(-10) to return -100')
AssertionError: -1000 != -100 : Expected add_times_ten(-10) to return -100

======================================================================
FAIL: test_multiply_ten_by_one_million (__main__.TestTimesTen)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "scratch.py", line 13, in test_multiply_ten_by_one_million
    self.assertEqual(times_ten(1000000), 10000000, 'Expected times_ten(1000000) to return 10000000')
AssertionError: 100000000 != 10000000 : Expected times_ten(1000000) to return 10000000

----------------------------------------------------------------------
Ran 3 tests in 0.001s

FAILED (failures=2)
```
 
### Assert Methods I: Equality and Membership
The framework relies on built-in assert methods instead of `assert` statements to track results without actually raising any exceptions. Specific assert methods take arguments instead of a condition, and like assert statements, they can take an optional message argument.

- [assertEqual](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertEqual): The `assertEqual()` method takes two values as arguments and checks that they are equal. If they are not, the test fails.

```python
 self.assertEqual(value1, value2)
```

- [assertIn](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertIn): The `assertIn()` method takes two arguments. It checks that the first argument is found in the second argument, which should be a container. If it is not found in the container, the test fails.

```python
 self.assertIn(value, container)
```

- [assertTrue](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertTrue): The `assertTrue()` method takes a single argument and checks that the argument evaluates to `True`. If it does not evaluate to `True`, the test fails.

```python
 self.assertTrue(value)
```

The equivalent `assert` statements would be the following:

| Method                        | Equivalent               |
| ----------------------------- | ------------------------ |
| `self.assertEqual(2, 5)`      | `assert 2 == 5`          |
| `self.assertIn(5, [1, 2, 3])` | `assert 5 in [1, 2, 3]`  |
| `self.assertTrue(0)`          | `assert bool(0) is True` |

The full list for equality and membership can be seen in the [Python documentation](https://docs.python.org/3/library/unittest.html#unittest.TestCase.debug).

### Assert Methods II: Quantitative Methods
Often we need to test conditions related to numbers.

- [assertLess](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertLess): The `assertLess()` method takes two arguments and checks that the first argument is less than the second one. If it is not, the test will fail.

```python
 self.assertLess(value1, value2)
```

- [assertAlmostEqual](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertAlmostEqual): The `assertAlmostEqual()` method takes two arguments and checks that their difference, when rounded to 7 decimal places, is 0. In other words, if they are almost equal. If the values are not close enough to equality, the test will fail.

```python
 self.assertAlmostEqual(value1, value2)
```

The equivalent `assert` statements would be the following:

| Method                              | Equivalent                         |
| ----------------------------------- | ---------------------------------- |
| `self.assertLess(2, 5)`             | `assert 2 < 5`                     |
| `self.assertAlmostEqual(.22, .225)` | `assert round(.22 - .225, 7) == 0` |

### Assert Methods III: Exception and Warning Methods

- [assertRaises](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertRaises): The `assertRaises()` method takes an exception type as its first argument, a function reference as its second, and an arbitrary number of arguments as the rest.

It calls the function and checks if an exception is raised as a result. The test passes if an exception is raised, is an error if another exception is raised, or fails if no exception is raised. This method can be used with custom exceptions as well!

```python
self.assertRaises(specificException, function, functionArguments...)
```

- [assertWarns](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertWarns): The `assertWarns()` method takes a warning type as its first argument, a function reference as its second, and an arbitrary number of arguments for the rest.

It calls the function and checks that the warning occurs. The test passes if a warning is triggered and fails if it isn’t.

```python
 self.assertWarns(specificWarningException, function, functionArguments...)
```

### Parameterizing Tests
To decrease repetition, Python provides us a specific toolset for tests with only minor differences. This is known as _test parameterization_. By parameterizing tests, we can leverage the functionality of a single test to get a large amount of coverage of different inputs.

To accomplish test parameterization, the `unittest` framework provides us with the [`subTest` context manager](https://docs.python.org/3/library/unittest.html#distinguishing-test-iterations-using-subtests).

```python
import unittest

# The function we want to test
def times_ten(number):
    return number * 100

# Our test class
class TestTimesTen(unittest.TestCase):
    
    # A test method
    def test_times_ten(self):
        for num in [0, 1000000, -10]:
            with self.subTest():
                expected_result = num * 10
                message = 'Expected times_ten(' + str(num) + ') to return ' + str(expected_result)
                self.assertEqual(times_ten(num), expected_result, message)
```

By using `subTest`, each iteration of our loop is treated as an individual test. Python will run the code inside of the context manager on each iteration, and if one fails, it will return the failure as a separate test case failure.

Optionally, we can give our subtests better readability by making a small change in our code for the first argument of `self.subTest()`.

```python
# ... more code above..

for num in [0, 1000000, -10]:
  with self.subTest(num):

# ... more code below ....
```

### Test Fixtures
One of the most important principles of testing is that tests need to occur in a known state. If the conditions in which a test runs are not controlled, then our results could contain false negatives (invalid failed results) or false positives (invalid passed results).

This is where _test fixtures_ come in. A test fixture is a mechanism for ensuring proper test setup (putting tests into a known state) and test teardown (restoring the state prior to the test running). Test fixtures guarantee that our tests are running in predictable conditions, and thus the results are reliable.

```python
def power_cycle_device():
  print('Power cycling bluetooth device...')

class BluetoothDeviceTests(unittest.TestCase):
  def setUp(self):
    power_cycle_device()

  def test_feature_a(self):
    print('Testing Feature A')

  def test_feature_b(self):
    print('Testing Feature B')

  def tearDown(self):
    power_cycle_device()
```

The `unittest` framework automatically identifies setup and teardown methods based on their names. A method named `setUp` runs before each test case in the class. Similarly, a method named `tearDown` gets called after each test case.

Let’s refactor the previous example so that setup and teardown only happen once - before and after all tests in the class are run:

```python
def power_cycle_device():
    print('Power cycling bluetooth device...')

class BluetoothDeviceTests(unittest.TestCase):
  @classmethod
  def setUpClass(cls):
    power_cycle_device()

  def test_feature_a(self):
    print('Testing Feature A')

  def test_feature_b(self):
    print('Testing Feature B')

  @classmethod
  def tearDownClass(cls):
    power_cycle_device()
```

We replaced our `setUp` method with the `setUpClass` method and added the [`@classmethod` decorator](https://docs.python.org/3/library/functions.html#classmethod). We changed the argument from `self` to `cls` because this is a class method. Similarly, we replaced the `tearDown` method with the `tearDownClass` class method.

In addition to calling [functions](https://www.codecademy.com/resources/docs/python/functions), we can also use setup methods to instantiate objects and or gather any other data needed. Anything stored in our class will be available throughout our test functions.

It’s generally good practice to create fixtures that run for every test. However, when a fixture has a large cost (i.e. it takes a long time), then it might make more sense to have it run once per test class rather than once per test.

### Skipping tests
Sometimes we have tests that should only run in a particular context. For example, we might have a group of tests that only runs on the Windows operating system but not Linux or macOS. For these situations, it’s helpful to be able to skip tests.

The `unittest` framework provides two different ways to skip tests:

1. The `@unittest` skip decorator
2. The `skipTest()` method

```python
import sys

class LinuxTests(unittest.TestCase):

    @unittest.skipUnless(sys.platform.startswith("linux"), "This test only runs on Linux")
    def test_linux_feature(self):
        print("This test should only run on Linux")

    @unittest.skipIf(not sys.platform.startswith("linux"), "This test only runs on Linux")
    def test_other_linux_feature(self):
        print("This test should only run on Linux")
```

- The `skipUnless` option skips the test if the condition evaluates to `False`.
- The `skipIf` option skips the test if the condition evaluates to `True`.

Both share common requirements. Firstly, both of these skip [decorators](https://www.codecademy.com/resources/docs/python/decorators) are prefaced with `@unittest` to denote the decorator pattern. They both take a condition as a first argument, followed by a string message as the second.

The second way to skip tests is to call the `skipTest` method of the `TestCase` class.

```python
import sys

class LinuxTests(unittest.TestCase):

    def test_linux_feature(self):
        if not sys.platform.startswith("linux"):
            self.skipTest("Test only runs on Linux")
```

Skip decorators are slightly more convenient and make it easy to see under what conditions the test is skipped. When the conditions for skipping a test are too complicated to pass into a skip decorator, the `skipTest` method is the recommended alternative.

### Expected Failures
Sometimes we have a test that we know will fail. This could happen when a feature has a known bug or is designed to fail on purpose. In this case, we wouldn’t want an expected failure to cloud our test results. Rather than simply skipping the test, `unittest` provides a way to mark tests as expected failures. Expected failures are counted as passed in our test results. If the test passes when we expected it to fail, then it is marked as failed in test results.

To setup a test to have an expected failure, we can use the [`expectedFailure` decorator](https://docs.python.org/3/library/unittest.html#unittest.expectedFailure).

```python
class FeatureTests(unittest.TestCase):

    @unittest.expectedFailure
    def test_broken_feature(self):
        raise Exception("This test is going to fail")
```

The `expectedFailure` decorator takes no arguments. The test in the example will always fail because an exception was raised during test execution. When run, we get the following output:

```
x
----------------------------------------------------------------------
Ran 1 test in 0.000s

OK (expected failures=1)
```

# Iterators & Generators

## Iterables & Iterators

### Introduction to Iterables
In Python, an _iterable_ is an object that is capable of being looped through one element at a time.

Dictionaries, lists, tuples, and sets are all classified as iterables!

### Iterator Objects: `__iter__()` and iter()

```python
for food_brand in dog_foods:
    print(food_brand + " has " + str(dog_foods[food_brand]) + " bags")
```

Under the hood, the first step that the `for` loop has to do is to convert our dictionary (the iterable) of `dog_foods` to an _iterator object_. An iterator object is a special object that represents a stream of data that we can operate on. To accomplish this, it uses a built-in function called [`iter()`](https://docs.python.org/3/library/functions.html#iter):

```python
dog_food_iterator = iter(dog_foods)
```

To go behind the scenes even further, `iter(dog_foods)` is actually calling a method defined within the iterable called `__iter__()`. All iterables have this `__iter__()` method defined.

In summary, the `__iter__()` method simply returns the iterator object that allows us to iterate over the iterable. Calling `dog_foods.__iter__()` will retrieve the same iterator object as calling `iter(dog_foods)`.

### Iterator Objects: `__next__()` and next()
The iterator object has a method called `__next__()`, which retrieves the iterator’s next value.

```python
sku_list = [7046538, 8289407, 9056375, 2308597]
sku_iterator = iter(sku_list)
next_sku = sku_iterator.__next__()
print(next_sku)
```

Running this code would produce the following result for `next_sku`:

```
7046538
```

Similarly to `__iter__()` and [`iter()`](https://www.codecademy.com/resources/docs/python/iterators/iter), there is a Python built-in function called [`next()`](https://www.codecademy.com/resources/docs/python/built-in-functions/next) that we can use in place of calling the `__next__()` method. Calling `next()` simply calls the iterator object’s `__next__()` method.

```python
sku_list = [7046538, 8289407, 9056375, 2308597]
sku_iterator = iter(sku_list)
next_sku = next(sku_iterator)
print(next_sku)
```

But how does the iterator object know when to stop retrieving values? Does it keep calling `__next__()` forever? Well, luckily `__next__()` method will raise an exception called `StopIteration` when all items have been iterated through.

If we call `__next__()` a total of 5 times, one more than the total number of SKUs in our list, we will see the `StopIteration` exception raise on the last `__next__()` call:

```python
sku_list = [7046538, 8289407, 9056375, 2308597]
sku_iterator = iter(sku_list)
for i in range(5):
  next_sku = sku_iterator.__next__()
  print(next_sku)
```

Running this code will produce the following output:

```
7046538
8289407
9056375
2308597
```

Followed by:

```
Traceback (most recent call last):
  File "main.py", line 24, in <module>
    next_sku = sku_iterator.__next__()
StopIteration
```

### Iterators and For Loops
Let’s look back at the following `dog_foods` dictionary and the `for` loop that performs the iteration:

```python
dog_foods = {
  "Great Dane Foods": 4,
  "Min Pip Pup Foods": 10,
  "Pawsome Pup Foods": 8
}
for food_brand in dog_foods:
  print (food_brand + " has " + str(dog_foods[food_brand]) + " bags")
```

To summarize, the three main steps are:

1. The `for` loop will first retrieve an iterator object for the `dog_foods` dictionary using [`iter()`](https://www.codecademy.com/resources/docs/python/iterators/iter).
2. Then, [`next()`](https://www.codecademy.com/resources/docs/python/built-in-functions/next) is called on each iteration of the `for` loop to retrieve the next value. This value is set to the `for` loop’s variable, `food_brand`.
3. On each `for` loop iteration, the print statement is executed, until finally, the `for` loop executes a call to `next()` that raises the `StopIteration` exception. The `for` loop then exits and is finished iterating.

### Custom Iterators
We have seen that the methods `__iter__()` and `__next__()` must be implemented for an object to be an iterator object. The implementation of these methods is known as the _iterator protocol_.

If we desire to create our own custom iterator class, we must implement the iterator protocol, meaning we need to have a class that defines at minimum the `__iter__()` and `__next__()` methods.

```python
class FishInventory:
  def __init__(self, fishList):
      self.available_fish = fishList
```

By default, custom classes are not iterable. We can’t just go around plugging our custom classes into `for` [loops](https://www.codecademy.com/resources/docs/python/loops) and expecting any results! This presents a problem if the class we are working with needs the ability to iterate.

When we create a `FishInventory` class object, we want to iterate over all the fish available within `self.available_fish`. If we attempt to directly iterate over our custom `FishInventory` class object, we will receive an error because we have not yet implemented the iterator protocol for this custom class. To make the `FishInventory` class iterable, we can simply define `__iter__()` and `__next__()` methods.

To iterate over a custom class we must implement the iterator protocol by defining the `__iter__()` and `__next__()` methods. In most cases the two methods can do the following:

- The `__iter__()` method must always return the iterator object itself. Typically, this is accomplished by returning `self`. It can also include some class member initializing.
- The `__next__()` method must either return the next value available or raise the `StopIteration` exception. It can also include any number of operations.

We can initialize a class member within the `__iter__()` method called `index` that will help us track the current position we’re in within the `self.available_fish` list.

```python
class FishInventory:
  def __init__(self, fishList):
      self.available_fish = fishList

  def __iter__(self):
    self.index = 0
    return self
```

Notice that the `__iter__()` method returns itself since this class will be an iterator object. The `__iter__()` method can return other iterator objects, but typically the object itself is returned here by using `return self`.

Then, we define the `__next__()` method. Recall that we can perform operations inside this method, like incrementing class members or traversing a `for` loop for instance.

```python
class FishInventory:
  def __init__(self, fishList):
      self.available_fish = fishList

  def __iter__(self):
    self.index = 0
    return self

  def __next__(self):
    fish_status = self.available_fish[self.index] + " is available!"
    self.index += 1
    return fish_status
```

Iterating over this class object will eventually error out since we fail to do any checking of our `index` value against the length of the `self.available_fish` list. We can avoid this and cleanly stop the iterator by raising the `StopIteration` exception in our `__next__()` method. Here, we’ll modify our `__next__()` method to raise `StopIteration` if `index` exceeds the length of `available_fish`.

```python
class FishInventory:
  def __init__(self, fishList):
      self.available_fish = fishList

  def __iter__(self):
    self.index = 0
    return self

  def __next__(self):
    if self.index < len(self.available_fish):
      fish_status = self.available_fish[self.index] + " is available!"
      self.index += 1
      return fish_status
    else:
      raise StopIteration
```

```python
class CustomerCounter:
  def __iter__(self):
    self.count = 0
    return self

  def __next__(self):
    self.count += 1
    if self.count > 100:
      raise StopIteration
    return self.count

customer_counter = CustomerCounter()
for count in customer_counter:
  print(count)
```

### Python’s Itertools: Built-in Iterators
While building our own custom iterator [classes](https://www.codecademy.com/resources/docs/python/classes) can be useful, Python offers a convenient, built-in module named _itertools_ that provides the ability to create complex iterator manipulations. These iterator operations can input either a single iterable or a combination of them.

There are three categories of itertool iterators:

- **Infinite**: Infinite [iterators](https://www.codecademy.com/resources/docs/python/iterators) will repeat an infinite number of times. They will not raise a StopIteration exception and will require some type of stop condition to exit from.
- **Input-Dependent**: Input-dependent iterators are terminated by the input iterable(s) sequence length. This means that the smallest length iterable parameter of an input-dependent iterator will terminate the iterator.
- **Combinatoric**: Combinatoric iterators are iterators that are combinational, where mathematical [functions](https://www.codecademy.com/resources/docs/python/functions) are performed on the input iterable(s).

We can use the itertools module by simply supplying an import statement at the top of the module like this:

```python
import itertools
```

The full list of itertools can be found in the official [Python documentation](https://docs.python.org/3/library/itertools.html).

### Infinite Iterator: Count
An infinite iterator will repeat an infinite number of times with no endpoint and no `StopIteration` exception raised. Infinite [iterators](https://www.codecademy.com/resources/docs/python/iterators) are useful when we have unbounded streams of data to process.

A useful itertool that is an infinite iterator is the `count()` itertool. This infinite iterator will count from a first value until we provide some type of stop condition. The base syntax of the function looks like this:

```python
count(start,[step])
```

The first argument of `count()` is the value where we start counting from. The second argument is an optional step that will return `current value + step`. The step value can be positive, negative, and an integer or float number. It will always default to 1 if not provided.

```python
import itertools

for i in itertools.count(start=0, step=2):
  print(i)
  if i >= 20:
    break
```

And our output becomes:

```
0
2
4
6
8
10
12
14
16
18
20
```

### Input-Dependent Iterator: Chain
An input-dependent iterator will terminate based on the length of one or more input values. They are great for working with and modifying existing [iterators](https://www.codecademy.com/resources/docs/python/iterators).

A useful itertool that is an input-dependent iterator is the `chain()` itertool. `chain()` takes in one or more iterables and combine them into a single iterator.

```python
chain(*iterables)
```

The input value of `chain()` is one or more iterables of the same or varying iterable types. For example, we could use the `chain()` itertool to combine a list and a set into one iterator.

```python
import itertools

odd = [5, 7, 9]
even = {6, 8, 10}

all_numbers = itertools.chain(odd, even)

for number in all_numbers:
  print(number)
```

Note that Python sets are not ordered so the last 3 numbers in this example’s output will not always be in the initialized order.

### Combinatoric Iterator: Combinations
A _combinatoric_ iterator will perform a set of statistical or mathematical operations on an input iterable.

A useful itertool that is a combinatoric iterator is the `combinations()` itertool. This itertool will produce an iterator of [tuples](https://www.codecademy.com/resources/docs/python/tuples) that contain combinations of all elements in the input.

```python
combinations(iterable, r)
```

The `combinations()` itertool takes in two inputs, the first is an iterable, and the second is a value `r` that represents the length of each combination tuple.

The return type of `combinations()` is an iterator that can be used in a `for` loop or can be converted into an iterable type using [`list()`](https://www.codecademy.com/resources/docs/python/built-in-functions/list) or a [`set()`](https://www.codecademy.com/resources/docs/python/built-in-functions/set).

```python
import itertools
even = [2, 4, 6]
even_combinations = list(itertools.combinations(even, 2))
print(even_combinations)
```

The resulting list of `2` member tuples are the combinations of all 3 members of `even`:

```
[(2, 4), (2, 6), (4, 6)]
```

## Generators
#project
### Introduction to Generators
In Python, a _generator_ allows for the creation of [iterators](https://www.codecademy.com/resources/docs/python/iterators) without having to implement `__iter__()` and `__next__()` methods. [Generators](https://www.codecademy.com/resources/docs/python/generators) improve code readability, save memory by allowing for iterative access of elements, and allow for the traversal of infinite streams of data.

There are two types of generators in Python:

1. Generator [functions](https://www.codecademy.com/resources/docs/python/functions)
2. Generator Expressions

Both of these return a generator object that can be looped over similar to a list, but unlike a list, the contents of the generator object are not stored in memory, allowing for complex and even infinite iteration of data.

### yield vs return
Generator [functions](https://www.codecademy.com/resources/docs/python/functions) are similar to regular functions except that they must return an iterator. But instead of using a `return` statement, generator functions use an expression called `yield`.

So how does `yield` differ from a `return` statement? Well, any code that is written after a `yield` expression will execute on the next iteration of the iterator. Code written after a `return` statement will not execute.

```python
def course_generator():
  yield 'Computer Science'
  yield 'Art'
  yield 'Business'
```

This function will return an iterator that contains the string values ‘Computer Science’, ‘Art’, and ‘Business’. On each iteration of the iterator, each yield will return its corresponding course value.

```python
courses = course_generator()
for course in courses:
    print(course)
```

Would print out:

```
Computer Science
Art
Business
```

Another key difference between `yield` and `return` is that the `yield` expression will suspend the execution of the function and preserve any local [variables](https://www.codecademy.com/resources/docs/python/variables) that exist within the function. The `return` statement will terminate the function immediately and return the result(s) to the caller.

Like all objects, the iterator object returned by a generator function can be stored in a variable to be used later. It can then be iterated through as needed.

### next() and StopIteration
Generator [functions](https://www.codecademy.com/resources/docs/python/functions) return an iterator object that contains traversable values. To retrieve the next value from a generator object, we can use the Python built-in function [`next()`](https://www.codecademy.com/resources/docs/python/built-in-functions/next) which will cause the generator function to resume its execution until the next `yield` expression is found. After the next `yield` expression is found, the function will pause execution again.

If no additional `yield` expressions are found in a generator function, that means the code has finished and a StopIteration is raised.

Generator functions are not limited to just single `yield` statements. They can also include [loops](https://www.codecademy.com/resources/docs/python/loops) where the `yield` occurs.

To see this in action, imagine we have a dictionary of students and their student ID numbers. We want to hold a raffle where every student whose student ID is a multiple of 3 wins prize A and every student whose ID is a multiple of 5 wins prize B. Any student whose ID is both a multiple of 3 and 5 wins prize C.

```python
def prize_generator():
  student_info = {
    "Joan Stark": 355,
    "Billy Mars": 45,
    "Tori Rivers": 18,
    "Kyle Newman": 25
  }

  for student in student_info:
    name = student
    id = student_info[name]
    if id % 3 == 0 and id % 5 == 0:
      yield student + " gets prize C"
    elif id % 3 == 0:
      yield student + " gets prize A"
    elif id % 5 == 0:
      yield student + " gets prize B"
```

Since this is a generator function, the local variable dictionary, `student_info` is preserved while the function executes with each `next()` call.

```python
prizes = prize_generator()
print(next(prizes))
print(next(prizes))
print(next(prizes))
print(next(prizes))
```

```
Joan Stark gets prize B
Billy Mars gets prize C
Tori Rivers gets prize A
Kyle Newman gets prize B
```

If we were to call `next()` one additional time, we would see a `StopIteration` exception raised since the `student_info` dictionary will have been exhausted.

### Generator Expressions
Generator expressions allow for a clean, single-line definition and creation of an iterator. By using a generator expression, there is no need to define a full generator function.

Generator expressions resemble the syntax of list comprehensions. However, they do differ in the following ways:

| Generator Expressions            | List Comprehensions |
| -------------------------------- | ------------------- |
| Returns a newly defined iterator | Returns a new list  |
| Uses parentheses                 | Uses brackets       |

```python
# List comprehension
a_list = [i*i for i in range(4)]

# Generator comprehension
a_generator = (i*i for i in range(4))
```

In this code above, `a_list` will be a list object containing the values [0, 1, 4, 9]. The object `a_generator` will be a generator object that cannot be accessed directly like `a_list`. It will need to be traversed to retrieve the values it contains.

```python
print(a_list)
print(a_generator)
```

```
[0, 1, 4, 9]
<generator object <genexpr> at 0x7f82e0e4d4c0>
```

Since our generator expression returns an iterator object, we can loop through to obtain the values within it:

```python
for i in a_generator:
    print(i)
```

```
0
1
4
9
```

### Generator Methods: send()
The `.send()` method allows us to send a value to a generator using the `yield` expression. If you assign `yield` to a variable the argument passed to the `.send()` method will be assigned to that variable. Calling `.send()` will also cause the generator to perform an iteration.

```python
def count_generator():
  while True:
    n = yield
    print(n)

my_generator = count_generator()
next(my_generator) # 1st Iteration Output: 
next(my_generator) # 2nd Iteration Output: None
my_generator.send(3) # 3rd Iteration Output: 3
next(my_generator) # 4th Iteration Output: None
```

In the code example above, the generator definition contains the line `n = yield`. This assigns the value in `yield` to `n` which will be `None` unless a value is passed using `.send()`.

The `.send()` method can control the value of the generator when a second variable is introduced. One variable holds the iteration value and the other holds the value passed through `yield`.

```python
def generator():
  count = 0
  while True:
    n = yield count
    if n is not None:
      count = n
    count += 1

my_generator = generator()
print(next(my_generator)) # Output: 0
print(next(my_generator)) # Output: 1
print(my_generator.send(3)) # Output: 4
print(next(my_generator)) # Output: 5
```

In the above example, the generator function defines `count = 0` as the iteration value. `n` is used to hold the value provided by `yield`. Just like `next()`, the `.send()` method returns the value of the recent iteration.

The updated line, `n = yield count`, has 2 behaviors:

- At the start of each iteration the value provided by `yield` is assigned to `n`. This value will be `None` when `next()` causes an iteration or it will be equal to the value passed using `.send()`
- At the end of each iteration, the value stored in `count` is returned by the generator.

If `n is not None` the value stored in `n` can be assigned to the iterator variable, `count`. This allows the iterator to only change the value of `count` when the `.send()` method is called.

```python
MAX_STUDENTS = 50

def get_student_ids():
  student_id = 1
  while student_id <= MAX_STUDENTS:
    n = yield student_id
    if n is not None:
      student_id = n
      continue
    student_id += 1

student_id_generator = get_student_ids()
for i in student_id_generator:
  if i == 1:
    i = student_id_generator.send(25)
  print(i)
```

### Generator Methods: throw()
The generator method `throw()` provides the ability to throw an exception inside the generator from the caller point. This can be useful if we need to end the generator once it reaches a certain value or meets a particular condition.

```python
def generator():
  i = 0
  while True:
    yield i
    i += 1

my_generator = generator()
for item in my_generator:
    if item == 3:
        my_generator.throw(ValueError, "Bad value given")
```

### Generator Methods: close()
The generator method [`.close()`](https://www.codecademy.com/resources/docs/python/files/close) is used to terminate a generator early. Once the `.close()` method is called the generator is finished just like the end of a `for loop`. Any further iteration attempts will raise a `StopIteration` exception.

```python
def generator():
  i = 0
  while True:
    yield i
    i += 1

my_generator = generator()
next(my_generator)
next(my_generator)
my_generator.close()
next(my_generator) # raises StopGenerator exception
```

In the above example, `my_generator()` holds an an infinite generator object.

The `.close()` method works by raising a `GeneratorExit` exception inside the generator function. The exception is generally ignored but can be handled using `try` and `except`.

```python
def generator():
  i = 0
  while True:
    try:
      yield i
    except GeneratorExit:
      print("Early exit, BYE!")
      break
    i += 1

my_generator = generator()
for item in my_generator:
  print(item)
  if item == 1:
    my_generator.close()
```

```
0
1
Early exit, BYE!
```

Because we interrupted the automatic behavior of the `.close()` method, we must also use a `break` to exit the loop or else a `RuntimeError` will occur.

### Connecting Generators
There are some cases where it is useful to connect multiple [generators](https://www.codecademy.com/resources/docs/python/generators) into one. This allows us to delegate the operations of one generator to another sub-generator. Connecting generators is similar to using the itertools `chain()` function to combine [iterators](https://www.codecademy.com/resources/docs/python/iterators) into a single iterator.

```python
def cs_courses():
    yield 'Computer Science'
    yield 'Artificial Intelligence'

def art_courses():
    yield 'Intro to Art'
    yield 'Selecting Mediums'


def all_courses():
    yield from cs_courses()
    yield from art_courses()

combined_generator = all_courses()
```

If we iterate through each value within `combined_generator` using [`print()`](https://www.codecademy.com/resources/docs/python/built-in-functions/print) and [`next()`](https://www.codecademy.com/resources/docs/python/built-in-functions/next), we can see that `yield from` retrieves each individual yield item at a time in the order that the yields are called within the generator [functions](https://www.codecademy.com/resources/docs/python/functions).

```python
print(next(combined_generator))
print(next(combined_generator))
print(next(combined_generator))
print(next(combined_generator))
```

Our printouts will look like the following:

```
Computer Science
Artificial Intelligence
Intro to Art
Selecting Mediums
```

### Generator Pipelines
_Generator pipelines_ allow us to use multiple [generators](https://www.codecademy.com/resources/docs/python/generators) to perform a series of operations all within one expression. We can break down complex operations into smaller, more manageable parts where they can then be pipelined together to achieve the desired output.

To pipeline generators, the output of one generator function can be the input of another generator function. That resulting generator can then be used as input for another generator function, and so on.

Pipeline generators are also often referred to as _nested generators_.

```python
def number_generator():
  i = 0
  while True:
    yield i
    i += 1
    
def even_number_generator(numbers):
  for n in numbers:
    if n % 2 == 0:
      yield n

even_numbers = even_number_generator(number_generator())

for e in even_numbers:
  print(e)
  if e == 100:
    break
```

### Review

```python 
def summa():
    yield 'Summa Cum Laude'
def magna():
    yield 'Magna Cum Laude' 
def cum_laude():
    yield 'Cum Laude'

def graduation_countdown(days):
  while days >= 0:
    days_left = yield days
    if days_left is not None:
      days = days_left
    else:
      days -= 1

days = 25
countdown_generator = (day for day in range(days, -1, -1))
grad_days = graduation_countdown(days)
for days in grad_days:
  if days == 15:
    grad_days.send(10)
  elif days == 3:
    grad_days.close()
  print("Days Left: {}".format(days))

def honors_generator(gpas):
  for gpa in gpas:
    if gpa > 3.9:
      yield from summa()
    elif gpa > 3.7:
      yield from magna()
    elif gpa > 3.5:
      yield from cum_laude()

gpas = [3.2, 4.0, 3.6, 2.9]
honors = honors_generator(gpas)
for honor in honors:
  print(honor)
```

# Specialized Collections
#project 
## Sets

### Introduction to Python Sets
In Python, a set is a group of elements that are unordered and do not contain duplicates.

We can imagine two different groups of items that have some similarities and differences. Using set mathematics, we can find the matching items, differences, combine the [sets](https://www.codecademy.com/resources/docs/python/sets) based on different parameters, and more!

Alternatively, there is also an immutable version of a set called a frozenset. A frozenset behaves similarly to a normal set, but it does not include methods that modify the frozenset in any way.

### Creating a Set
In Python, there are multiple ways to create a set. A set object can be created by passing an iterable object into its constructor, using curly braces, or using a set comprehension.

```python
# Creating a set with curly braces
music_genres = {'country', 'punk', 'rap', 'techno', 'pop', 'latin'}

# Creating a set from a list using set()
music_genres_2 = set(['country', 'punk', 'rap', 'techno', 'pop', 'latin'])
```

It’s worth noting that creating a set from a list with duplicates produces a set with the duplicates removed.

```python
# Creating a set from a list that contains duplicates
music_genres_3 = set(['country', 'punk', 'rap', 'pop', 'pop', 'pop'])
print(music_genres_3)
```

Will output:

```
{'country', 'punk', 'pop', 'rap'}
```

While we use a similar data type in the [sets](https://www.codecademy.com/resources/docs/python/sets) above, sets can actually contain any combination of [data types](https://www.codecademy.com/resources/docs/python/data-types) as long as they are unique values.

```python
music_different = {70, 'music times', 'categories', True , 'country', 45.7}
```

We can also create an empty set with one specific method:

```python
# Creating an empty set using the set() constructor
# Doing set = {} will define a dictionary rather than a set.  

empty_genres = set()
```

Lastly, similar to list comprehensions, we can create sets using a set comprehension and a data set (such as a list).

```python
items = ['country', 'punk', 'rap', 'techno', 'pop', 'latin']

music_genres = {category for category in items if category[0] == 'p'}
print(music_genres)
```

Would output a set containing all elements from `items` starting with the letter `'p'`:

```
{'punk', 'pop'}
```

### Creating a Frozenset
Unlike a normal `set`, you can only create a `frozenset` using its constructor. Remember that using a `frozenset` means that you cannot modify the elements inside of it.

```python
# Creating a frozenset from a list
frozen_music_genres = frozenset(['country', 'punk', 'rap', 'techno', 'pop', 'latin'])
```

We can also create an empty `frozenset`:

```python
empty_frozen_music_genres = frozenset()
```

### Adding to a Set
There are two different ways to add elements to a set:

1. The `.add()` method can add a single element to the `set`.

```python
# Create a set to hold the song tags
song_tags = {'country', 'folk', 'acoustic'}

# Add a new tag to the set and try to add a duplicate.
song_tags.add('guitar')
song_tags.add('country')

print(song_tags)
```

Would output:

```
{'country', 'acoustic', 'guitar', 'folk'}
```

2. The [`.update()`](https://www.codecademy.com/resources/docs/python/dictionaries/update) method can add multiple elements.

```python
# Create a set to hold the song tags
song_tags = {'country', 'folk', 'acoustic'}

# Add more tags using a hashable object (such as a list of elements)
other_tags = ['live', 'blues', 'acoustic']
song_tags.update(other_tags)

print(song_tags)
```

Would output:

```
{'acoustic', 'folk', 'country', 'live', 'blues'}
```

There are a few things to note about adding to a set:

- Neither of these methods will add a duplicate item to a `set`.
- A `frozenset` can not have any items added to it and so neither of these methods will work.
- Notice that when the elements are printed, they are not printed in the same order in which they entered the `set`. This is because `set` and `frozenset` containers are unordered.

### Removing From a Set
There are two methods for removing specific elements from a `set`:

1. The `.remove()` method searches for an element within the `set` and removes it if it exists, otherwise, a `KeyError` is thrown.

```python
# Given a list of song tags
song_tags = {'guitar', 'acoustic', 'folk', 'country', 'live', 'blues'}

# Remove an existing element
song_tags.remove('folk')
print(song_tags)

# Try removing a non-existent element
song_tags.remove('fiddle')
```

Would output:

```
{'blues', 'acoustic', 'country', 'guitar', 'live'}
```

Followed by:

```
Traceback (most recent call last):
File "some_file_name.py", line 9, in <module>
  song_tags.remove('fiddle')
KeyError: 'fiddle'
```

2. The `.discard()` method works the same way but does not throw an exception if an element is not present.

```python
# Given a list of song tags
song_tags = {'guitar', 'acoustic', 'folk', 'country', 'live', 'blues'}

# Try removing a non-existent element but with the discard method
song_tags.discard('guitar')
print(song_tags)

# Try removing a non-existent element but with the discard method
song_tags.discard('fiddle')
print(song_tags)
```

Would output:

```
{'folk', 'acoustic', 'blues', 'live', 'country'}
{'folk', 'acoustic', 'blues', 'live', 'country'}
```

Note that items cannot be removed from a `frozenset` so neither of these methods would work.

### Finding Elements in a Set
In Python, `set` and `frozenset` items cannot be accessed by a specific index. This is due to the fact that both containers are unordered and have no indices. However, like most other Python containers, we can use the `in` keyword to test if an element is in a `set` or `frozenset`.

```python
# Given a list of song tags
song_tags = {'guitar', 'acoustic', 'folk', 'country', 'live', 'blues'}

# Print the result of testing whether 'country' is in the set of tags or not
print('country' in song_tags)
```

Would output:

```
True
```

This also works for `frozenset`:

```python
song_tags = {'guitar', 'acoustic', 'folk', 'country', 'live', 'blues'}

frozen_tags = frozenset(song_tags)
print('rock' in frozen_tags)
```

Would output:

```
False
```

### Introduction to Set Operations
A lot of the usefulness of a set container comes from the set operations. These allow you to combine [sets](https://www.codecademy.com/resources/docs/python/sets), find the difference and intersections of sets, and more! You can combine these operations to perform complex logic problems on multiple sets. This can be useful for filtering items, categorizing, combining, as well as many other uses.

The operations which we will be looking at are:

- Unions
- Intersections (and Intersection Updates)
- Differences (and Difference Updates)
- Symmetric Differences (and Symmetric Difference Updates)

Additional operations will not be covered in this lesson, such as finding subsets and supersets. Information about these operations can be found in the [Python documentation](https://docs.python.org/3/library/stdtypes.html#set).

### Set Union
When working with `set` or `frozenset` container, one of the most common operations we can perform is a merge. To do this, we can return the union of two sets using the [`.union()`](https://www.codecademy.com/resources/docs/python/sets/union) method or `|` operator. Doing so will return a new `set` or `frozenset` containing all elements from both sets without duplicates.

![[Pasted image 20240321184607.png]]

Notice the resulting set contains all the elements in both set `A` and set `B` as well as elements they have in common (minus the duplicates).

1. Using `union()`:

```python
# Given a set and frozenset of song tags for two python related hits
prepare_to_py = {'rock', 'heavy metal', 'electric guitar', 'synth'}

py_and_dry = frozenset({'classic', 'rock', 'electric guitar', 'rock and roll'})

# Get the union using the .union() method
combined_tags = prepare_to_py.union(py_and_dry)
print(combined_tags)
```

Would output:

```
{'electric guitar', 'classic', 'heavy metal', 'rock and roll', 'rock', 'synth'}
```

2. Using `|`:

```python
# Get the union using the | operator
frozen_combined_tags = py_and_dry | prepare_to_py
print(frozen_combined_tags)
```

Would output:

```
frozenset({'electric guitar', 'rock and roll', 'rock', 'synth', 'heavy metal', 'classic'})
```

Note that the return value in both methods takes the form of the left operand. In the first example since `prepare_to_py()` called the `union()` function, so the result was a regular `set`. In the second example, since `py_and_dry` was the left operand, the end result was a `frozenset`.

### Set Intersection
Let’s say that we have two or more sets, and we want to find which items both sets have in common. The `set` container has a method called [`.intersection()`](https://www.codecademy.com/resources/docs/python/sets/intersection) which returns a new `set` or `frozenset` consisting of those elements. An intersection can also be performed on multiple sets using the `&` operator.

Similar to the other operations, the type of the first operand (a `set` or `frozenset` on the left side of the operator or method) determines if a `set` or `frozenset` is returned when finding the intersection.

![[Pasted image 20240321190206.png]]

```python
# Given a set and frozenset of song tags for two python related hits
prepare_to_py = {'rock', 'heavy metal', 'electric guitar', 'synth'}

py_and_dry = frozenset({'classic', 'rock', 'electric guitar', 'rock and roll'})

# Find the intersection between them while providing the `frozenset` first.
frozen_intersected_tags = py_and_dry.intersection(prepare_to_py)
print(frozen_intersected_tags)
```

Would output:

```
frozenset({'electric guitar', 'rock'})
```

And here it is with the `&` operator:

```python
# Find the intersection using the operator `&` and providing the normal set first
intersected_tags = prepare_to_py & py_and_dry
print(intersected_tags)
```

Would output:

```
{'rock', 'electric guitar'}
```

In addition to a regular intersection, the `set` container can also use a method called `.intersection_update()`. Instead of returning a new `set`, the original `set` is updated to contain the result of the intersection.

### Set Difference
Similar to how we can find elements in common between sets, we can also find unique elements in one set. To do so, the `set` or `frozenset` use the [`.difference()`](https://www.codecademy.com/resources/docs/python/sets/difference) method or the `-` operator. This returns a `set` or `frozenset`, which contains only the elements from the first set which are not found in the second set. Similar to the other operations, the type of the first operand (a `set` or `frozenset` on the left side of the operator or method) determines if a `set` or `frozenset` is returned when finding the difference.

![[Pasted image 20240321191355.png]]

```python
# Given a set and frozenset of song tags for two python related hits
prepare_to_py = {'rock', 'heavy metal', 'electric guitar', 'synth'}

py_and_dry = frozenset({'classic', 'rock', 'electric guitar', 'rock and roll'})

# Find the elements which are only in prepare_to_py
only_in_prepare_to_py = prepare_to_py.difference(py_and_dry)
print(only_in_prepare_to_py)
```

Would Output:

```
{'heavy metal', 'synth'}
```

Alternatively, we can use the `-` operator:

```python
# Find the elements which are only in py_and_dry
only_in_py_and_dry = py_and_dry - prepare_to_py
print(only_in_py_and_dry)
```

Would output:

```
frozenset({'rock and roll', 'classic'})
```

This operation also supports an updating version of the method. You can use `.difference_update()` to update the original `set` with the result instead of returning a new `set` or `frozenset` object.

### Symmetric Difference
We can think of this operation as the opposite of the intersection operation. A resulting set will include all elements from the [sets](https://www.codecademy.com/resources/docs/python/sets) which are in one or the other, but not both. In other words, elements that are unique to each set.

To perform this operation on the `set` or `frozenset` containers, we can use the `.symmetric_difference()` method or the `^` operator. Like the other [operators](https://www.codecademy.com/resources/docs/python/operators), the type of the first operand (a `set` or `frozenset` on the left side of the operator or method) determines if a `set` or `frozenset` is returned when finding the symmetric difference.

![[Pasted image 20240321193104.png]]

```python
# Given a set and frozenset of song tags for two python related hits
prepare_to_py = {'rock', 'heavy metal', 'electric guitar', 'synth'}

py_and_dry = frozenset({'classic', 'rock', 'electric guitar', 'rock and roll'})

# Find the elements which are exclusive to each song and not shared using the method
exclusive_tags = prepare_to_py.symmetric_difference(py_and_dry)
print(exclusive_tags)
```

Would output:

```
{'heavy metal', 'synth', 'rock and roll', 'classic'}
```

Alternatively, we can use the `^` operator:

```python
# Find the elements which are exclusive to each song and not shared using the operator
frozen_exclusive_tags = py_and_dry ^ prepare_to_py
print(frozen_exclusive_tags)
```

Would output:

```
frozenset({'synth', 'rock and roll', 'heavy metal', 'classic'})
```

We can also update the original `set` using this operation by using the `.symmetric_difference_update()` method to update the original `set` with the result instead of returning a new `set` or `frozenset` object.

### Review
Creating a `set` or `frozenset`:

- For `set` containers, we can use curly braces `{}`, the [`set()`](https://www.codecademy.com/resources/docs/python/built-in-functions/set) constructor, or set comprehension.
- For `frozenset` containers, we can only use the [`frozenset()`](https://www.codecademy.com/resources/docs/python/built-in-functions/frozenset) constructor.

Adding items to a `set`:

- We can add items to a `set` individually using the `.add()` method.
- We can add multiple items at once using the [`.update()`](https://www.codecademy.com/resources/docs/python/dictionaries/update) method.

Removing items from a `set`:

- The `.remove()` method is used to remove elements from a `set`.
- The `.discard()` method can also be used to remove elements from a `set`. It does not throw a `KeyError` if the element is not found.

Finding Elements:

- The `in` keyword can be used with `set` and `frozenset` containers to test if an element exists inside of them.

Union:

- A union can be found using `set` or `frozenset` containers with the [`.union()`](https://www.codecademy.com/resources/docs/python/sets/union) method or `|` operator.

Intersection:

- An intersection can be found using `set` or `frozenset` containers with the [`.intersection()`](https://www.codecademy.com/resources/docs/python/sets/intersection) method or `&` operator.

Difference:

- The difference can be found using `set` or `frozenset` containers with the [`.difference()`](https://www.codecademy.com/resources/docs/python/sets/difference) method or `-` operator.

Symmetric Difference:

- The symmetric difference can be found using `set` or `frozenset` containers with the `.symmetric_difference()` method or `^` operator.

## Collections

### Recap: Python Containers
Any object which stores data is called a _container_.

We are familiar with Python’s built-in containers (such as [lists](https://www.codecademy.com/resources/docs/python/lists) or dictionaries), but there are many other containers that exist in Python. These containers each specialize in a specific job and can be imported into your code from other [modules](https://www.codecademy.com/resources/docs/python/modules) or even be custom-made!

Let’s take some time to review some of the common built-in containers we are most familiar with:

#### Lists
Lists are an ordered group of elements. Elements can be added, removed, accessed, and modified.

```python
products = ['t-shirt', 'pants', 'shoes', 'dress', 'blouse']

products.append('jacket')
products.sort()
products.remove('shoes')
```

#### Tuples
Tuples are immutable objects which group multiple elements together. They are similar to lists, except that they cannot be modified once created.

```python
searched_terms = ('clothes', 'phone', 'app', 'purchase', 'clothes', 'store', 'app', 'clothes')

term = searched_terms[2]
num_of_occurrences = searched_terms.count('clothes')
```

#### Dictionaries
Dictionaries are unordered groups of key-value pairs.

```python
orders = {'order_4829': {'type': 't-shirt', 'size': 'large', 'price': 9.99}, 
          'order_6184': {'type': 'pants', 'size': 'medium', 'price': 14.99}
         }

order_4829_price = orders['order_4829']['price']
order_6184_size = orders['order_6184']['size']
orders['order_4829']['size'] = 'x-large'
num_of_orders = len(orders)
```

#### Sets
Sets are unordered groups of elements that cannot contain duplicates, elements cannot be modified.

```python
old_products_set = {'t-shirt', 'pants', 'shoes'}
new_products_set = {'t-shirt', 'pants', 'blouse', 'dress'}
updated_products = new_products_set | old_products_set
removed_products = old_products_set - new_products_set
```
 
### Introduction to Specialized Containers
The [classes](https://www.codecademy.com/resources/docs/python/classes) from the `collections` module are very similar to the built-in containers we’ve been already using, but they contain new methods and utilities. Each of these specialized containers focuses on a certain improvement to its built-in counterpart such as optimizing performance, better organization, fewer steps for performing tasks, and more!

In order to use classes from the `collections` module, we will first need to import the module into our code. This is different than the previous containers we’ve seen because they were built-in and did not require an import.

```python
# To import a single class or multiple classes
from collections import name_of_class, name_of_another_class

# To import all classes in the collections module
from collections import *

# Another way to import all classes in a module
import collections
```

For a more specific example, here is what importing the `OrderedDict` (one of the specialized containers) would look like.

```python
from collections import OrderedDict

orders = OrderedDict({'order_4829': {'type': 't-shirt', 'size': 'large', 'price': 9.99},
          'order_6184': {'type': 'pants', 'size': 'medium', 'price': 14.99},
          'order_2905': {'type': 'shoes', 'size': 12, 'price': 22.50}})

orders.move_to_end('order_4829')
orders.popitem()
```

#### Advanced Containers

- `deque`
- [`namedtuple`](https://www.codecademy.com/resources/docs/python/collections-module/namedtuple)
- `Counter`
- [`defaultdict`](https://www.codecademy.com/resources/docs/python/collections-module/defaultdict)
- `OrderedDict`
- `ChainMap`

#### Container Wrappers

- `UserDict`
- `UserList`
- `UserString`

### Deque
Let’s imagine a situation where we are processing a large document containing bug reports for an application. In order to prioritize the most important bugs, we want any normal bug reports to be appended to the end of the list and higher priority bugs to be at the front of the list (kind of like a priority list). As we fix the bugs, they can be removed from the front of the list.

The program below is an example of what our implementation might look like using lists.

```python
bug_data = []

loaded_bug_reports = get_all_bug_reports()

for bug in loaded_bug_reports:
    if bug['priority'] == 'high':
        # A list uses the insert method to append to the front
        bug_data.insert(0, bug)
    else:
        bug_data.append(bug)

# A list must provide an index to pop
next_bug_to_fix = bug_data.pop(0)
```

The problem with this implementation is that lists are not optimized for appending and popping large amounts of data, although they are great at accessing data at any index which you provide.

To solve this problem, we can use `deque` containers. These are similar to lists, but they are optimized for appending and popping to the front and back, rather than having optimized accessing. Because of this, they are great for working with data where you don’t need to access elements in the middle very often or at all.

```python
from collections import deque

bug_data = deque()

loaded_bug_reports = get_all_bug_reports()

for bug in loaded_bug_reports:
    if bug['priority'] == 'high':
        # With a deque, we can append to the front directly
        bug_data.appendleft(bug)
    else:
        bug_data.append(bug)

# With a deque, we can pop from the front directly
next_bug_to_fix = bug_data.popleft()
```

More information about the `deque` container can be found in the [Python Documentation](https://docs.python.org/3/library/collections.html#collections.deque)

### Named Tuple
[Tuples](https://www.codecademy.com/resources/docs/python/tuples), another common built-in container, are very useful for grouping together data that does not need to be modified in the future. Tuples do however run into an issue when they host various data and even nested data.

```python
actor_data_tuple = ('Leonardo DiCaprio', 1974, 'Titanic', 1997)
```

While the tuple does a great job of creating a container that can keep ordered immutable data, it can become quite confusing to represent properties using numerical indices.

```python
actor_data_tuple[3]
```

Unless we explicitly define a variable name that describes what the third index represents, it’s very hard to tell what data we are talking about. We would also need to make separate [variables](https://www.codecademy.com/resources/docs/python/variables) for each property! Thanks to the `collections` module, we have a solution to this problem.

The [`namedtuple`](https://www.codecademy.com/resources/docs/python/collections-module/namedtuple) collection allows us to have an immutable tuple object, but every element becomes self-documented.

```python
from collections import namedtuple

# General Structure: namedtuple(typename, field_names, *, rename=False, defaults=None, module=None)

ActorData = namedtuple('ActorData', ['name', 'birth_year', 'movie', 'movie_release_date'])
```

In this example, we are defining an instance of the `namedtuple` collection with a _typename_ called `'ActorData'` and a sequence of [strings](https://www.codecademy.com/resources/docs/python/strings) called _field_names_ that represent the labels for the data we want to store.

We can then define an instance of our `ActorData`:

```python
actor_data = ActorData('Leonardo DiCaprio', 1974, 'Titanic', 1997)
```

This then allows us to access the mapped property value to its associated name from before using the `.` notation:

```python
print(actor_data.name)
```

Would return:

```
Leonardo DiCaprio
```

Some things to note about `namedtuples`:

- You may have noticed we use a CapWords convention when defining our `namedtuple`. This is because `namedtuple` actually returns a _subclass_ and thus falls under the conventions we use for [classes](https://www.codecademy.com/resources/docs/python/classes).
- The `field_names` argument can alternatively be a single string with each fieldname separated by whitespace and/or commas, for example, `'x y'` or `'x, y'`.
- At first glance, `namedtuples` might seem like it is trying to replicate a dictionary. While the key idea of labeling properties is the same in both structures, `namedtuples` have some key advantages over a regular dictionary:
    - They are immutable and maintain their order, while a dictionary does not.
    - They are more lightweight than [dictionaries](https://www.codecademy.com/resources/docs/python/dictionaries) and take no more memory than a regular tuple.

There are other useful methods that a `namedtuple` uses such as converting from a `namedtuple` to a `dict`, replacing elements and field names, and even setting default values for attributes. More information about `namedtuple` containers can be found in the [Python Documentation](https://docs.python.org/3/library/collections.html#collections.namedtuple).

### DefaultDict
[Dictionaries](https://www.codecademy.com/resources/docs/python/dictionaries) are another popular type of collection we use in our programs. Although they are great for a lot of situations, applications that rely heavily on them always run into a common issue. This issue deals with how to handle missing keys!

When we try to access a key-value pair in a dictionary, but the key does not exist, a dictionary will normally throw a `KeyError`.

```python
prices = {'jeans': 19.99, 'shoes': 24.99, 't-shirt': 9.99, 'blouse': 19.99}

print(prices['jacket'])
```

Would output:

```
KeyError: 'jacket'
```

One of the ways Python offers to deal with this issue is by having a default missing value in the dictionary, and this is exactly what the [`defaultdict`](https://www.codecademy.com/resources/docs/python/collections-module/defaultdict) collection does.

First, we import the class and set the default value:

```python
from collections import defaultdict

validate_prices = defaultdict(lambda: 'No Price Assigned')
```

Next, we can set the keys and values like a regular `dict`:

```python
validate_prices['jeans'] = 19.99
validate_prices['shoes'] = 24.99
validate_prices['t-shirt'] = 9.99
validate_prices['blouse'] = 19.99
```

Finally, we access an invalid key to observe the result:

```python
print(validate_prices['jacket'])
```

Would output:

```
No Price Assigned
```

Notice the following:

- We set the default value using a [lambda](https://www.codecademy.com/resources/docs/python/keywords/lambda) expression.
- Any time we try to access a key that does not exist, it automatically updates our `defaultdict` object by creating the new key-value pair using the missing key and the default value.

To read more about the `defaultdict` container, take a look at the [Python Documentation](https://docs.python.org/3/library/collections.html#collections.defaultdics)

---

Not only can we create a `defaultdict` from scratch, but we can also create one from an existing dictionary. To do this, we can use the `.update()` method from the `defaultdict` class. This behaves the same way as the `.update()` method from the `dict` class.

### OrderedDict
When keeping track of many different [dictionaries](https://www.codecademy.com/resources/docs/python/dictionaries) with the built-in Python containers, we could try storing dictionaries in a list, or even a dictionary of dictionaries. This may work in some cases, but there are a few problems which might come up.

When storing dictionaries in a list, the order is preserved, but we have to access the elements by their index before we can access the dictionary:

```python
first_order = {'order_2905': {'type': 'shoes', 'size': 12, 'price': 22.50}}
second_order = {'order_6184': {'type': 'pants', 'size': 'medium', 'price': 14.99}}
third_order = {'order_4829': {'type': 't-shirt', 'size': 'large', 'price': 9.99}}

list_of_dicts = [first_order, second_order, third_order]
```

In order to get the price of a specific order, we must know the index of it already before we can access the dictionary data stored inside:

```python
print(list_of_dicts[1]['order_6184']['price'])

# Output
# 14.99
```

On the other hand, depending on the Python version, the `dict` container can preserve the order, but it is difficult to move elements around:

```python
dict_of_dicts = {}
dict_of_dicts.update(first_order)
dict_of_dicts.update(second_order)
dict_of_dicts.update(third_order)

print(dict_of_dicts['order_6184']['price'])

# Output
# 14.99
```

Note: The `dict` class is unordered in earlier versions of python, so implementing it this way must have version 3.6 or greater.

To solve these issues, we can use an `OrderedDict`!

The `OrderedDict` container allows us to access values using keys, but it also preserves the order of the elements inside of it.

Import and create an `OrderedDict`.

```python
from collections import OrderedDict

orders = OrderedDict()
```

The order of the data is preserved when adding it to the `OrderedDict`:

```python
orders.update({'order_2905': {'type': 'shoes', 'size': 12, 'price': 22.50}})
orders.update({'order_6184': {'type': 'pants', 'size': 'medium', 'price': 14.99}})
orders.update({'order_4829': {'type': 't-shirt', 'size': 'large', 'price': 9.99}})
```

Data can be accessed using keys like a normal dictionary:

```python
# Get a specific order
find_order = orders['order_2905']
```

The order can be retrieved by converting it to a list then accessing by index:

```python
# Get the data in a list format
orders_list = list(orders.items())
third_order = orders_list[2]
```

When using an `OrderedDict`, we are able to use its methods for moving the data around. We can move an element to the back or front and pop the data from the back or front of the `OrderedDict`:

```python
# Move an item to the end of the OrderedDict
orders.move_to_end('order_4829')

# Pop the last item in the dictionary
last_order = orders.popitem()
```

Note: These two methods also accept boolean arguments which determine if the element is moved / popped from the front or back of the `OrderedDict`.

For more information about the `OrderedDict` container, take a look at the [Python Documentation](https://docs.python.org/3/library/collections.html#collections.OrderedDict).

### ChainMap
The `ChainMap` container allows us to store many mappings in an ordered group, but lookups (accessing the value using a key) are repeated for every mapping inside of the `ChainMap` until something is found or the end is reached. If we try to modify the data in any way, then only the first mapping in the `ChainMap` will receive the changes. When accessing data, one way to think of the `ChainMap` is that it treats all of the stored dictionaries as one large dictionary, where if there are repeated keys, then the first found result is returned.

```python
from collections import ChainMap

customer_info = {'name': 'Dmitri Buyer', 'age': '31', 'address': '123 Python Lane', 'phone_number': '5552930183'}

shirt_dimensions = {'shoulder': 20, 'chest': 42, 'torso_length': 29}

pants_dimensions = {'waist': 36, 'leg_length': 42.5, 'hip': 21.5, 'thigh': 25, 'bottom': 18}
```

Next, we initialize a `ChainMap` with the mappings which we want to use. In this case, the mappings are the dimensions dictionaries.

```python
customer_data = ChainMap(customer_info, shirt_dimensions, pants_dimensions)
```

Now we can access values from any of the stored mappings.

```python
customer_leg_length = customer_data['leg_length']
```

The parents property skips the first mapping and returns everything else (all of the parents of the first mapping).

```python
customer_size_data = customer_data.parents
```

We can directly modify the data only in the first dictionary.

```python
customer_data['address'] = '456 ChainMap Drive'
```

Note: In order to modify data from dictionaries which are deeper in the `ChainMap`, we will need to iterate through the dictionaries which are stored inside of it.

Another interesting concept that the `ChainMap` uses is the concept of a parent mappings. If we use the `.parents` property, all mappings except the first one will be returned. This is because those mappings are considered to be the parent mappings to the first one. You can add a new “child” mapping to the front of the list of mappings using the `.new_child()` method.

To find out more about this container, check out the [Python Documentation](https://docs.python.org/3/library/collections.html#collections.ChainMap).

---

Remember that a `ChainMap` accepts a variable number of arguments so we need to expand the list (`*`) so the constructor will read them as individual arguments instead of one single argument.

### Counter
One of the most common tasks we might have to do in a program is to count instances of an element in a collection.

First, let’s define a list of items.

```python
clothes_list = ['skirt', 'hoodie', 'dress', 'blouse', 'jeans', 'shoes', 'skirt', 'skirt', 'jeans', 'hoodie', 'boots', 'jeans', 'jacket', 't-shirt', 'skirt', 'skirt', 'dress', 'shoes', 'blouse', 'hoodie', 'skirt', 'boots', 'shoes', 'boots', 'jeans', 'hoodie', 'blouse', 'hoodie', 'shoes', 'shoes', 'blouse', 'boots', 'blouse', 'hoodie', 't-shirt', 'jeans', 'dress', 'skirt', 'jacket', 'boots', 'skirt', 'dress', 'jeans', 'jeans', 'jacket', 'jeans', 'shoes', 'dress', 'hoodie', 'blouse']
```

If we wanted to create a representation of how many of each item exist in our collection, we could use a loop and a dictionary.

```python
counted_items = {}
for item in clothes_list:
   if item not in counted_items:
       counted_items[item] = 1
   else:
       counted_items[item] += 1

print(counted_items)
```

This would output (in no particular order):

```
{'skirt': 8, 'hoodie': 7, 'dress': 5, 'blouse': 6, 'jeans': 8, 'shoes': 6, 'boots': 5, 'jacket': 3, 't-shirt': 2}
```

The `Counter` container instantly counts elements for any hashable object. It stores the data as a dictionary where the keys are the elements and the values are the number of occurrences.

```python
from collections import Counter

counted_items = Counter(clothes_list)
print(counted_items)
```

Would Output:

```
Counter({'skirt': 8, 'jeans': 8, 'hoodie': 7, 'blouse': 6, 'shoes': 6, 'dress': 5, 'boots': 5, 'jacket': 3, 't-shirt': 2})
```

This allows us to create a much more elegant solution without many lines of code. Additionally, the `Counter` class has methods that provide further utility when working with our data. These methods include mathematical operations for subtracting one count dictionary from another, finding the most common elements, and even generating a new list of elements based on the number of occurrences.

For more information about the `Counter` class, take a look at the [Python documentation](https://docs.python.org/3/library/collections.html#collections.Counter).

---

Luckily, the `Counter` container has a method that allows us to accomplish this really easily.

Take a look at the Python documentation for the [.subtract()](https://docs.python.org/3/library/collections.html#collections.Counter.subtract) method.

### Container Wrappers
In Python, wrappers are modifications to [functions](https://www.codecademy.com/resources/docs/python/functions) or [classes](https://www.codecademy.com/resources/docs/python/classes) which change the behavior in some way. They are called wrappers because they “wrap” around the existing code to modify it. This is most commonly used with function wrapping, but we can also wrap classes.

First, we need a class to wrap around.

```python
class Customer:

  def __init__(self, name, age, address, phone_number):
    self.name = name
    self.age = age
    self.address = address
    self.phone_number = phone_number
```

Next, we create a wrapper class which stores an object of the class we are wrapping around. It also includes some additional functionality.

```python
class CustomerWrap(Customer):

  def __init__(self, name, age, address, phone_number):
    self.customer = Customer(name, age, address, phone_number)

  def display_customer_info(self):
    print('Name: ' + self.customer.name)
    print('Age: ' + str(self.customer.age))
    print('Address: ' + self.customer.address)
    print('Phone Number: ' + self.customer.phone_number)
```

Finally, we can create an object from the wrapper class to access the new functionality and the wrapped class contained inside.

```python
customer = CustomerWrap('Dmitri Buyer', 38, '123 Python Avenue', '5557098603')
customer.display_customer_info()

# Output
# Name: Dmitri Buyer
# Age: 38
# Address: 123 Python Avenue
# Phone Number: 5557098603
```

Wrapper classes allow us to create different variations of classes with different purposes while avoiding duplicate code. Since we use an instance of the wrapped class inside of it, it preserves all of the attributes and methods from the wrapped class and keeps us from having to re-type all of the code.

In the case of containers, the `collections` class has three different wrapper classes set up for us to modify! Because of this, we can refer to them as wrapper containers. The advanced containers which we have already been looking at are variations of the standard built-in containers, so using wrapper containers allows us to create our own versions as well.

The three wrapper containers we will be looking at are:

- `UserDict`
- `UserList`
- `UserString`

### UserDict
The `UserDict` container wrapper lets us create our own version of a dictionary. This class contains all of the functionality of a normal `dict`, except that we can access the dictionary data through the `data` property.

```python
from collections import UserDict

# Create a class which inherits from the UserDict class
class DisplayDict(UserDict):
    # A new method to increase the dictionary's functionality
    def display_info(self):
        print("Number of Keys: " + str(len(self.keys())))
        print("Keys: " + str(list(self.keys())))
        print("Number of Values: " + str(len(self.values())))
        print("Values: " + str(list(self.values())))

    # We can also overwrite a method from the dictionary class
    def clear(self):
        print("Deleting all items from the dictionary!")
        super().clear()

disp_dict = DisplayDict({'user': 'Mark', 'device': 'desktop', 'num_visits': 37})

disp_dict.display_info()

disp_dict.clear()

```

As shown in this code example, we can add additional methods and overwrite methods from the `UserDict` class. This is the same as inheriting from regular [classes](https://www.codecademy.com/resources/docs/python/classes) in Python.

```python
class OrderProcessingDict(UserDict):
  def clean_orders(self):
    to_delete = []
    for key, val in self.data.items():
      if val['order_status'] == 'complete':
        to_delete.append(key)

    for key in to_delete:
      del self.data[key]
```

### UserList
Not only can we create our own version of a dictionary, the `UserList` wrapper container lets us create our own `list` as well! This class contains all of the functionality of a regular `list`, but it also has a property called `data` which allows us to access the list contents directly.

```python
from collections import UserList

# Create a class which inherits from the UserList class
class CondenseList(UserList):

    # A new method to remove duplicate items from the list
    def condense(self):
        self.data = list(set(self.data))
        print(self.data)


    # We can also overwrite a method from the list class
    def clear(self):
        print("Deleting all items from the list!")
        super().clear()

condense_list = CondenseList(['t-shirt', 'jeans', 'jeans', 't-shirt', 'shoes'])

condense_list.condense()

condense_list.clear()
```

As shown in this code example, we can add additional methods and overwrite methods from the `UserList` class. This is the same as inheriting from regular [classes](https://www.codecademy.com/resources/docs/python/classes) in Python.

```python
class ListSorter(UserList):
  def append(self, item):
    self.data.append(item)
    self.data.sort()
```

### UserString
Since [strings](https://www.codecademy.com/resources/docs/python/strings) are also considered containers, the `collections` module also provides a container wrapper for the string class. This contains all of the functionality of a regular string, but it includes the string’s data inside of a property called `data`.

```python
from collections import UserString

# Create a class which inherits from the UserString class
class IntenseString(UserString):

    # A new method to capitalize and add exclamation points to our string
    def exclaim(self):
        self.data = self.data.upper() + '!!!'
        return self.data


    # Overwrite the count method to only count a certain letter
    def count(self, sub=None, start=0, end=0):
        num = 0
        for let in self.data:
            if let == 'P':
                num+=1
        return num


intense_string = IntenseString("python rules")

print(intense_string.exclaim())
print(intense_string.count())
```

This shows how we can add additional methods to the original container’s class or even overwrite existing methods. This is the same as inheriting from regular [classes](https://www.codecademy.com/resources/docs/python/classes) in Python.

```python
class SubtractString(UserString):
  def __sub__(self, str):
    if str in self.data:
      self.data = self.data.replace(str, '')

subtract_string = SubtractString(str_name)
subtract_string - str_word
print(subtract_string)
```

### Review

- `deque`
    - An advanced container which is optimized for appending and popping items from the front and back. For accessing many elements positioned elsewhere, it is better to use a `list`.
- [`namedtuple`](https://www.codecademy.com/resources/docs/python/collections-module/namedtuple)
    - The `namedtuple` lets us create an immutable data structure similar to a `tuple`, but we don’t have to access the stored data using indices. Instead, we can create instances of our `namedtuple` with named attributes. We can then use the `.` operator to retrieve data by the attribute names.
- `Counter`
    - This advanced container automatically counts the data within a hashable object which we pass into it’s constructor. It stores it as a dictionary where the keys are the elements and the values are the number of occurrences.
- [`defaultdict`](https://www.codecademy.com/resources/docs/python/collections-module/defaultdict)
    - An advanced container which behaves like a regular dictionary, except that it does not throw an error when trying to access a key which does not exist. Instead, it creates a new `key:value` pair where the value defaults to what we provide in the constructor for the `defaultdict`.
- `OrderedDict`
    - The `OrderedDict` combines the functionality of a `list` and a `dict` by preserving the order of elements, but also allowing us to access values using keys without having to provide an index for the position of stored [dictionaries](https://www.codecademy.com/resources/docs/python/dictionaries).
- `ChainMap`
    - This interesting container combines multiple mappings into a single container. When accessing a value using a key, it will search through every mapping contained within until a match is found or the end is reached. It also provides some useful methods for grouping parent and child mappings.
- `UserDict`
    - This is a container wrapper which lets us create our own version of a dictionary
- `UserList`
    - This is a container wrapper which lets us create our own version of a list
- `UserString`
    - This is a container wrapper which lets us create our own version of a string

```python
from collections import *

overstock_items = [['shirt_103985', 15.99],
                    ['pants_906841', 19.99],
                    ['pants_765321', 15.99],
                    ['shoes_948059', 29.99],
                    ['shoes_356864', 9.99],
                    ['shirt_865327', 10.99],
                    ['shorts_086853', 9.99],
                    ['pants_267953', 21.99],
                    ['dress_976264', 32.99],
                    ['shoes_135786', 17.99],
                    ['skirt_196543', 12.99],
                    ['jacket_976535', 26.99],
                    ['pants_086367', 30.99],
                    ['dress_357896', 29.99],
                    ['shoes_157895', 14.99]]

split_prices = deque()

for item in overstock_items:
  if item[1] > 20.0:
    split_prices.appendleft(item)
  else:
    split_prices.append(item)
print(split_prices)

ClothesBundle = namedtuple('ClothesBundle', ['bundle_items', 'bundle_price'])

bundles = []
while len(split_prices) >= 5:
  bundle_list = [split_prices.pop(), split_prices.pop(), split_prices.pop(), split_prices.popleft(),split_prices.popleft()]

  calc_price = sum(b[1] for b in bundle_list)
  bundles.append(ClothesBundle(bundle_list, calc_price))

promoted_bundles = []
for bundle in bundles:
  if bundle.bundle_price > 100:
    promoted_bundles.append(bundle)

print(promoted_bundles)
print(bundle)    
```

# Resource Management

## Context Managers

### Introduction to Resource Management
For computers, the resources we manage usually come in the form of memory, storage, or power. Since all resources are limited, if they are not managed well, it can lead to the computer running out of memory, space, and even cause crashes. So how do we manage these resources? Well, one of the easiest ways (and one we already started to explore) is through the use of _context managers_.

A context manager is an object that takes care of the assigning and releasing of resources (files, database connections, etc). Learning to properly use context managers will give our software benefits such as:

- Preventing resource leaks
- Preventing crashes
- Decreasing the vulnerability of our data
- Preventing program slow-down.

### A Familiar Face: The with Statement
One of the most common ways to manage resources in Python is to make sure the [files](https://www.codecademy.com/resources/docs/python/files) we use in our scripts are properly closed after use.

We already explored this concept when we used the `with` statement when operating on files. The `with` statement is the most common and pythonic way of invoking context managers in python.

```python
with open("file_name.txt", "w") as file:
   file.write("How you gonna win when you ain't right within?")
```

1. The `with` statement calls the built-in [`open()`](https://www.codecademy.com/resources/docs/python/built-in-functions/open) function on `"file_name.txt"` with a mode of `"w"` which represents write mode.
2. The `as` clause assigns the object opened (the file) to a target variable called `file`, which can be accessed inside of the context manager.
3. `file.write()` writes a sentence to `"file_name.txt"`

Here is what the same code would look like without the use of a context manager like `with`:

```python
file = open("file_name.txt", "w")
try:
   file.write("How you gonna win when you ain't right within?")
finally:
   file.close()
```

By using the `with` statement in the first example, it serves as a context manager where files are automatically closed after script completion and we don’t ever have to worry about the possibility of forgetting to close a resource. Remember, leaving our resources open will hog up our finite computer resources. We are never guaranteed that Python will close the file for us if we happen to forget to do it!

### Class Based Context Managers
One of the two approaches of creating context managers is referred to as the _class-based approach_. The class-based approach of writing context managers requires explicitly defining and implementing the following two methods inside of a class:

- An `__enter__` method
    
    - The `__enter__` method allows for the setup of context managers. This method commonly takes care of opening resources (like files). This method also begins what is known as the _runtime context_ - the period of time in which a script runs. In our previous examples, it was the time in which the code passed into the `with` statement code block was executed (basically everything under the `with` statement).
- An `__exit__` method
    
    - The `__exit__` ensures the breakdown of the context manager. This method commonly takes care of closing open resources that are no longer in use.

```python
class ContextManager:
  def __init__(self):
    print('Initializing class...')
 
  def __enter__(self):
    print('Entering context...')
 
  def __exit__(self, *exc):
    print('Exiting context...')
```

By defining these two methods, we are implementing the _context management protocol_ - a guideline for the required methods for a context manager.

Implementing the context management protocol allows us to immediately invoke the class using the `with` statement as shown below:

```python
with ContextManager() as cm:
  print('Code inside with statement')
```

After running the code, our output of this context manager would be:

```
Initializing class...
Entering context...
Code inside with statement
Exiting context...
```

The above shows that our context manager class is executed in the following sequence:

1. `__init__` method
2. `__enter__` method
3. The code in the `with` statement block
4. `__exit__` method

```python
class WorkWithFile:
  def __init__(self, file, mode):
    self.file = file
    self.mode = mode
 
  def __enter__(self):
    self.opened_file = open(self.file, self.mode)
    return self.opened_file
 
  def __exit__(self, *exc):
    self.opened_file.close()
```

The `__init__` method:

This method is standard across most classes, even ones that are not context managers themselves. In this case, we have three parameters:

- `self`: This is standard for any class we work with and allows us to work with methods and properties we assign to an instance of a class.
- `file`: Since we are working with files, we need to be able to take in a file argument when we call the class with a `with` statement.
- `mode`: Lastly, we need to provide the file a mode. This allows us to manage what our context manager will actually be doing, such as reading, writing, or both!

Both `file` and `mode` arguments allow us to accomplish the following syntax:

```python
with WorkWithFile('file.txt', 'r')
```

The `__enter__` method:

This is where we deal with opening the file we want to work on. Since any new instance of our context manager will have a `file` and `mode` property, we can pass them into the `open()` function to open a specific file with a specific mode. Then, we save it as a variable called `self.opened_file,` and return it.

By returning `self.opened_file`, the file will be passed into the variable we define when we call it with the `with` statement. So for example:

```python
with WorkWithFile('file.txt', 'r') as file
```

Will assign the open file `'file.txt'` to the variable called `file` that follows the `as` clause and thus allowing us to use it in the `with` statement code block.

- The `__exit__` method:
    
    Lastly, but one of the most important steps, we have to close the file we work on. Here we are still taking in a `*exc` argument, but we won’t touch on that until the next exercise. For now, this method is solely responsible for closing the resource we opened in `__enter__`.

Now that we created our context manager, we can now use it in a `with` statement like so:

```python
with WorkWithFile("file.txt", "r") as file:
  print(file.read())
```

### Handling Exceptions
Context managers play an important role in handling exceptions. Recall exceptions are [errors](https://www.codecademy.com/resources/docs/python/errors) that happen within the runtime of a code, terminating it before its completion. Within a context manager, the `__exit__` method is responsible for dealing with any exceptions. It can implement how to close the file and any other operations we want to perform if an exception occurs.

The `__exit__` method needs four total arguments! In the past exercises, we ignored this requirement by using the `*` operator to tell the method we will pass a variable number of arguments even though we never did.

The `__exit__` method has three required arguments (in addition to `self`):

1. An exception type: which indicates the class of exception (i.e. `AttributeError` class, or `NameError` class)
2. An exception value: the actual value of the error
3. A traceback: a report detailing the sequence of steps that caused the error and all the details needed to fix the error.

```python
class OpenFile:
 
 def __init__(self, file, mode):
   self.file = file
   self.mode = mode

 def __enter__(self):
   self.opened_file = open(self.file, self.mode)
   return self.opened_file
 
 def __exit__(self, exc_type, exc_val, traceback):
   print(exc_type)
   print(exc_val)
   print(traceback)
   self.opened_file.close()
```

We can see the outcome of our simple exception handling when we run our `with` statement with an intentional failure:

```python
with OpenFile("file.txt", "r") as file:
  # .see() is not a real method
  print(file.see())
```

Would output:

```
<class 'AttributeError'>
'_io.TextIOWrapper' object has no attribute 'see'
<traceback object at 0x7f08dcfb5040>

Traceback (most recent call last): File "script.py", line 14, in <module> print(file.see()) AttributeError: '_io.TextIOWrapper' object has no attribute 'see'
```

When an error occurs, the code stops, and resources (i.e., file in our earlier example) are still closed. The values of these three arguments are then thrown or suppressed.

In contrast, if no error occurs in the `with` statement above, the `__exit__` method would have printed:

```
None
None
None
```

Note that `exc_type`, `exc_value`, and `traceback` are completely arbitrary names. We can use any name we want for these parameters as long as it does not hinder the readability of our code.

Printing exceptions isn’t the only way we can handle them in the `__exit__` method. An exception that occurs in a context manager can be handled in two ways:

- If we want to throw an error when an error occurs, we can either:
    - Return `False` after the [`.close()`](https://www.codecademy.com/resources/docs/python/files/close) method
    - Do nothing
- If we want to suppress the error, we can:
    - Return `True` after the `.close()` method

```python
class OpenFile:
 
  def __init__(self, file, mode):
    self.file = file
    self.mode = mode
 
  def __enter__(self):
    self.opened_file = open(self.file, self.mode)
    return self.opened_file
 
  def __exit__(self, exc_type, exc_val, traceback):
    print(exc_type, exc_val, traceback)
    print("The exception has been handled")
    self.opened_file.close()
    return True

with OpenFile("file.txt", "r") as file:
  # .see() is not a real method
  print(file.see())

with OpenFile("file.txt", "r") as file:
  print(file.read())
```

When we run this code, our output is as follows:

```
<class 'AttributeError'> '_io.TextIOWrapper' object has no attribute 'see' <traceback object at 0x7fedf822d180>

The exception has been handled

None None None
```

- The error message we manually coded is printed but there is no automatic error message thrown by the program.
- Both `with` statements ran.

If we did not return `True`, the second (and all proceeding) `with` statements would not have run since an exception would be hit.

Additionally, we can choose to handle a specific exception, while also suppressing it! This is useful if we want our context manager to not block the execution of other code, but also customize the output if a certain exception occurs. Here is an example of working with a `TypeError`:

```python
class OpenFile:
 
  def __init__(self, file, mode):
    self.file = file
    self.mode = mode
 
  def __enter__(self):
    self.opened_file = open(self.file, self.mode)
    return self.opened_file
 
  def __exit__(self, exc_type, exc_val, traceback):
    self.file.close()
    if isinstance(exc_val, TypeError):
      # Handle TypeError here...
      print("The exception has been handled")
      return True
```

Notice the `if` statement that compares `exc_val` to a specific exception we are trying to catch. Anything we want to happen for this specific exception can occur in the conditional code block. Lastly, we return `True` to make sure we suppress the exception from arising and stopping the rest of our code from running.

**NOTE**: Remember that the `__exit__()` method’s primary responsibility is to close the resource the context manager is working with. In this example, we close the file first, before handling the error, so that it will always execute.

### Introduction to Contextlib
We’ve learned that we can create our own context managers using the class-based method, but there’s an even simpler way of creating context managers. We can use a built-in Python module called `contextlib`!

The `contextlib` module allows for the creation of a context manager with the use of a generator function (a function that uses `yield` instead of `return`) and the contextlib decorator - `@contextmanager`. Instead of creating a class and definining `__enter__` and `__exit__` methods, we can use a simple function!

First, we will need to import the built-in module into our script and grab the `@contextmanager` decorator:

```python
from contextlib import contextmanager
```

Once we have successfully imported the module, we can automatically use the `@contextmanager` decorator to wrap a simple generator function:

```python
from contextlib import contextmanager

@contextmanager
def open_file_contextlib(file, mode):
  opened_file = open(file, mode)
 try:
   yield opened_file
 finally:
   opened_file.close()
```

1. We have written a generator function called `open_file_contextlib` with the expectation that it will take in two arguments, a file and a mode.
2. We then use the built-in [`open()`](https://www.codecademy.com/resources/docs/python/built-in-functions/open) function to open the file (that we received as an argument) and save it to a variable called `opened_file`.
3. The function then will attempt (via a `try` statement) to `yield` the opened file and complete whatever code we pass when we use it in conjunction with the `with` statement.
4. Lastly the resource (file) will be closed once all the code is done being executed.

If we think about this structure in sections relative to the class-based approach, it essentially breaks down into this:

```
@contextmanager
def generator_function(<parameters>):
    <setup section - equivalent to __enter__ >
    try:
        yield <value>
    finally:
        <cleanup section - equivalent to __exit__ >
```

Once we have created this function and denoted it as a context manager using the `@contextmanager` decorator, we can immediately use it like before in a `with` statement:

```python
with open_file_contextlib('file.txt', 'w') as opened_file:
 opened_file.write('We just made a context manager using contexlib')
```

Following this pattern of creating context managers allows us to quickly convert generator [functions](https://www.codecademy.com/resources/docs/python/functions) to become context managers without the need to create any extra [classes](https://www.codecademy.com/resources/docs/python/classes).

### Contextlib Error Handling
Like any other pattern, you may run into errors when invoking your context manager using the `@contextmanager` decorator.

For the class-based context manager, the `__exit__` method dealt with exceptions. For the decorator method, errors are most commonly dealt with within an `except` block. There are two main ways to deal with errors:

- To throw an error and stop the execution of our entire program, we can:
    - Simply do nothing by excluding an `except` block
- To catch errors and continue the execution of our program, we can:
    - Handle the exception via an `except` block.

```python
from contextlib import contextmanager

@contextmanager
def open_file_contextlib(file, mode):
  open_file = open(file, mode)
 
try:
   yield open_file
 
 # Exception Handling
 except Exception as exception:
   print('We hit an error: ' + str(exception))
 
 finally:
   open_file.close()
 
with open_file_contextlib('file.txt', 'w') as opened_file:
 opened_file.sign('We just made a context manager using contexlib')
```

### Nested Context Managers
In most programs, there might be a need to use context managers for a couple of different scenarios that include working with multiple files! For example, we might want to:

- Work with information from multiple [files](https://www.codecademy.com/resources/docs/python/files).
- Copy the same information to multiple files.
- Copy information from one file to another.

To accomplish this goal of working with multiple resources at once, context managers can be nested together in a `with` statement to manage multiple resources simultaneously.

Let’s imagine we have two files: a `teacher.txt` file and a `student.txt`. We want to copy all the information on the student file to the teachers.

```python
with open('teacher.txt', 'w') as teacher, open('student.txt', 'r') as student:
 teacher.write(student.read())
```

- The `with` statement is being called once but invoking two context managers. This is a single-line nested `with` statement.
- Each context manager is separated by a comma and has its own target variable.
- Here we have chosen to use the [`open()`](https://www.codecademy.com/resources/docs/python/built-in-functions/open) built-in function rather than a custom context manager. It is entirely possible to use our own in place of the `open()` function.

We can also write the above `nested` context managers in a slightly different way:

```python
with open("teacher.txt", "w") as teacher:
   with open("student.txt", "r") as student:
     teacher.write(student.read())
```

- The `with` statement is being called twice
- This method, though slightly longer gives a clearer visual of `nesting` and is preferable when working with more than two context managers.

### Review

**Context Managers:**

- Context managers are a form of resource management in python invoked by the `with` statement.
- They ensure that resources are closed/released after usage regardless of whether or not an error occurs.
- They can be created from scratch using either the class-based method or the `contextlib` decorator-based method.
- Behind every context manager, there’s an `__enter__` and `__exit__` method taking place.
- Context managers can be nested together to work with resources simultaneously.

**Class-Based Context Managers**

- They can be created from scratch with the manual implementation of the `__enter__` and `__exit__` method.
- The `__exit__` method takes three arguments: An exception type, exception value, and a traceback. The method can then handle exceptions.

**Decorator Based Context Managers**

- They can be created from scratch using the `contextlib` contextmanager decorator on a generator function
- In the `contextlib` method, the `except` block handles exception’s code block

To explore context managers further check out the [Python Documentation](https://docs.python.org/3/library/contextlib.html#module-contextlib).