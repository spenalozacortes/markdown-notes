# JavaScript Under the Hood
## Currying in JavaScript

### Currying is a functional programming technique
Functional programming is a declarative paradigm that emphasizes immutability and _pure functions_ — meaning the function is side-effect free and for any given input it will always return the same output.

### How currying works
Below, we’ve created a non-curried function `add()`. `add()` will still execute if called with a missing argument, which would result in the missing variable being evaluated as `undefined`. For the `add()` function below, if `add()` was called with an argument for `a` but not for `b`, the function call would evaluate as `1 + undefined` and return `NaN`.

```js
function add(a,b) {
    return a + b;
}
```

Let’s curry the `add()` function to see how we can handle the function call better if only one argument is available. What we can do is transform the `add()` function, which normally expects multiple arguments, into a series of nested functions that will each take a single argument.

This makes the function calls more modular. With curried functions, calling the outer function returns the next function in the chain and so on until the innermost function is called, which then returns a value.

```js
// traditional function
function add(a,b) {
    return a + b;
}
 
// curried function
function curried_add(a) {
    // The outer function returns a nested single-argument function
    return function nested_func(b) {
        return a + b;
   }
}
```

(The returned function can also be anonymous, but has a name in this example for clarity.)

- Calling the outer function `curried_add()` returns `nested_func()`.
- Calling `nested_func` uses the arguments supplied from calling `curried_add` and `nested_func` to return the evaluated result of `a + b`.

You can call that in your code as `curried_add(a)(b)`, which invokes `curried_add()`, then invokes `nested_func()` immediately following the first function call.

Let’s break that down further. In the code block below, we are assigning the result of calling `curried_add()` to a variable named `add_one`.

```js
let add_one = curried_add(1); 
// returns nested_func()
```

Now, when we call `add_one()`, it will return the value of `a + b`, because it is the function `nested_func()`.

```js
add_one(10); 
// returns 11
```

The argument from calling `curried_add()` is available to the nested functions due to _closure_. A closure means that the nested function retains the scope of parent functions based on where the function is defined, even if the nested function is executed outside of that lexical scope.

You may recall that a function can access variables both in its inner and outer scope. That behavior is an example of _lexical_ scoping rules, which means the scoping is based on the structure of the code.

Taking that one step further, when a function is invoked, lexical scoping is retained. So nested functions will continue to have access to any variables that are declared in the outer scope of parent functions. This is true even if that parent function is done executing.

Overall, that means that when you run the line `let add_one = curried_add(1);` , `add_one()` will retain the scope from `curried_add()` and therefore have access to the variable created for the argument `a` as 1.

### Currying with Arrow Functions
The same `curried_add()` function from earlier can be rewritten much more concisely using ES6 arrow function syntax:

```js
let curried_add = a => b => a + b;
```


## Hoisting in JavaScript

### Behind the Scenes
During the compilation phase of code execution, the JavaScript engine allocates memory to save the names of declared variables and functions by _hoisting_ variable and function declarations to the top of their current scope.

Hoisting does not actually move your code around; instead, it:

- Finds all of the variable and function declarations in the code
- ‘Raises’ the variable names and function declarations to the top of their scope before code execution
- Immediately initializes function declarations
- Postpones handling _initialization_, or assignment of values, until the code is executed

One of the advantages to this is the fact that you can call a function on a line of code that is before the line of code where you actually declare the function.

There are subtle hoisting differences between function declarations, function expressions, and variable declarations, which are important to understand to avoid errors in your code.

JavaScript hoists function declarations, including the function body, to the top of its scope. If a function is declared at the global level, then it is raised to the top of the global scope. Hoisting also occurs within nested functions, so nested functions are raised to the top of the enclosing function scope.

Overall, a function declaration can be called from anywhere within the scope as long as it is in fact declared in the code. In the code below, the `add()` function is called before it is declared, and runs as expected since the declaration of `add()` is hoisted during the compilation phase.

```js
console.log(add(1,2)); 
// prints 3
 
function add(a,b) {
    return a + b
}
```

On the other hand, function expressions obey the hoisting rules for variable declarations, which have two sets of behavior–one set of rules for `var` and a shared set of rules for `let` and `const`.

### var hoisting
`var` has its own playbook when it comes to hoisting. `var` variables are hoisted to the top of function blocks, but not other types of blocks, so you have to be careful when using `var` to declare variables to ensure you have the intended value when the variable is used. `var` variables are initialized as `undefined` when they are hoisted, which can lead to unexpected results in code if a variable is evaluated as undefined instead of an intended value.

### let and const hoisting
Fortunately, variables defined with `let` and `const` are more predictable than `var` variables. Since the release of ES6, there are really no situations where it is preferable to use `var` variables. `let` and `const` variables are hoisted to the top of their parent block for scope, so any type of block or function can be the parent scope for those variables.

`let` and `const` differ from `var` in how they initialize as well; while the names are hoisted, they are not initialized. So calling a variable in your code before it is initialized results in a `ReferenceError`. This is one of the reasons `let` and `const` are preferable, as a `ReferenceError` will immediately alert you to the problem in your code. With `var` variables, you would need to implement unit tests to handle `undefined` values.

When you use `let` or `const`, be sure to initialize the value before referencing the variables.

As mentioned, function expressions will follow the rules of variable hoisting. That said, if you are using ES6 arrow function syntax, it is vital to remember to assign the function to a variable before calling it.


## Introduction to Memory Management in JavaScript

### Why learn about memory
When you execute a program, variables and all of your objects need to be stored and accessed in memory. We call the process of allocating, using, and releasing memory _the memory life cycle_ — and JavaScript handles all of it.

In other programming languages, like C and C++, you use `new`/`delete` to manually allocate and release memory for objects. That kind of responsibility can be a frequent source of bugs. With JavaScript, the primary memory issues that come up relate to _memory leaks_, which is when memory that should be released is still in action.

### Memory in JavaScript
JavaScript has two data structures for memory:

- The heap
- The stack

When you assign values to variables, the JavaScript engine is tasked with figuring out if the value is a primitive or a reference value. The outcome determines if the value is stored in the heap or the stack.

#### The Stack
The stack is used for static storage, where the size of an object is known when the code is compiled. Since the size is known, a fixed amount of data is reserved for the object, and the stack remains ordered. The stack has a finite amount of space provided by the operating system, which you typically only exceed when you have problems in your code, like infinite recursion or memory leaks.

Primitive values, _references_ to non-primitive values, and function call frames are stored in the stack. You can think of references as a parking space number in a massive (but disordered) parking garage telling JavaScript where to find objects and functions.

#### The Heap
The heap provides dynamic memory allocation at runtime for data types that don’t have a fixed size, like objects and functions. These are _reference values_ and we keep track of where to find them in the unstructured heap using a fixed-size _reference_ in the stack. If you modify an object, you are modifying a reference to the object and not the object itself.

```js
const cat = {
    name: "Jupiter"
}
 
const pets = ["Jupiter", "Moshi", "Hercules"]
```

In the example, `cat` is stored in the heap, a reference to `cat` is stored in the stack, and the property `name` is stored in the stack. The `pets` array is stored in the heap, while a reference to it is stored in the stack.

```js
let object = new Object();
let object2 = object;
object.greeting = "Hello, world";
 
console.log(object2); // { greeting: 'Hello, world' }
```

In the example, `object` and `object2` are pointing to the same object in memory in the heap, but with different variables that are saved in the stack.

### Memory Life Cycle
There are three parts to consider:

- Memory allocation (Values are declared and stored in memory)
- Memory in use (Values are read or rewritten)
- Releasing memory (Values are no longer in use and get removed from memory)

#### Memory Allocation
When we create a variable or declare values, memory is allocated. This can be initiated in many ways:

- Regular variable assignment
- Assigning properties to an object
- Declaring callable functions
- Calling functions

Memory allocation takes up bits and bytes in the machine’s RAM.

##### Calling Functions
JavaScript allocates memory during function execution. When a function is called, a function frame is added to the stack and some memory is allocated. Then, as more local variables are declared as the function executes, more stack memory gets allocated on the function frame. Any new objects get stored in the heap with references in the function frame in the stack. If another function is called from within the function, another function frame is added to the stack.

When a function is done executing, its function frame is removed from the stack, and the memory it used is deallocated and becomes available again to the rest of your code. After function execution is done, any objects that were stored in the heap will no longer have references from the stack, so they can be garbage collected.

During execution, the arguments are passed by value or reference. When you pass primitive values, the value is assigned to the argument within the function the same as it would be if you assigned a string to another variable, which means a new version of the string is created.

```js
let str = "Hi";
let str2 = str;
```

In the snippet, `str` and `str2` are two separate primitives, and both are saved in the stack with a fixed amount of memory allocation to store the string “Hi”. There are two separate versions of the string “Hi”.

Objects, on the other hand, are passed via a reference variable copy. This can be a source of bugs in your code, so it is important to be aware of how this works. If you pass an object and modify the object within the function, the original object will be modified, since both the original variable and the function’s internal variable are referencing the same object in memory.

```js
let aaliyah = {
    name: "Aaliyah"
}
 
function nameObjectModification(obj, name) {
    obj.name = name;
    return obj;
}
 
let sarah = nameObjectModification(aaliyah, "Sarah");
 
console.log(aaliyah); // { name: 'Sarah' }
console.log(sarah); // { name: 'Sarah' }
```

#### Memory in Use
Memory is in use when you are reading and writing allocated memory and includes the following tasks:

- Variable reassignment
- Using variables
- Passing arguments to functions

#### Releasing Memory: Garbage Collection
_Garbage collection_ refers to the process of clearing memory. The JavaScript engine manages garbage collection using two key algorithms:

- Reference-counting
- Mark-and-sweep

Garbage collection algorithms use different approaches to detect if some piece of memory is no longer needed by the program. Once memory is no longer needed, it is released and can be reused.

##### Reference-Counting
_Reference-counting_ makes use of the references to variables that live on the stack. When an object is created, it’s reference count is one. If you make a second variable point to that object, the reference count is two. If a function makes use of an object, the reference count is increased by one. Usually, inner elements from function calls are garbage collected when a function is done executing, unless the inner elements are still referenced.

```js
let obj = new Object(); // reference count of one
let obj2 = obj; // reference count of two
obj2 = "string"; // obj has a reference count of one again
```

With the reference-counting algorithm, if the reference count drops down to zero, there are no more references to the object in your program, so the JavaScript engine can mark that memory block as free to use so future allocations can utilize and overwrite the block.

```js
let monument = {
   name: "Eiffel Tower"
};
monument = "Golden Gate Bridge";
```

In the example, the `monument` variable is reassigned to the string value “Golden Gate Bridge,” so the `name` property can be garbage collected as it has a reference count of zero.

This type of algorithm does have some shortcomings.

##### Mark-and-Sweep
The _Mark-and-Sweep_ algorithm runs periodically and starts at the root of your code, the global object. From the root, it’ll “sweep” across your code to find and mark anything that is “reachable” by traversing across all of the variables. The mark is generally something like a boolean. After that process, any of the variables that are unmarked (i.e. they were not marked in the first step and therefore were not reachable) will be garbage collected during the sweep phase. That process is repeated over and over again during code execution.

### What happens when your process runs out of memory
When your code uses more and more memory, it can impact performance and cause Node applications or browser tabs to crash or experience latency. One way that happens is through _memory leaks_. If you have a memory leak, the program might try to allocate more memory than is actually available, and you can encounter memory errors. In the browser, that will just be the tab crashing.

When you don’t have enough memory allowed for Node, you might see a fatal error message:

```
==== JS stack trace =========================================
FATAL ERROR: CALL_AND_RETRY_LAST Allocation failed - JavaScript heap out of memory
```

While that error can be resolved by allocating more memory to your application in Node, that’s not really possible for frontend apps because that would equate to requiring end users to download more RAM. Even though memory leaks can be hidden by adding more hardware, finding and fixing the root cause of a memory leak is generally a better fix than throwing more hardware at a problem.

### Memory Leaks
When memory that’s no longer needed by a program persists, it is called a _memory leak_. The memory should be returned to the pool of free memory for future objects. A memory leak can happen when garbage collection fails to find an object that lost its connection to the root object, or when objects grow in size and are referenced by other objects. When this happens, it can be the source of slowdowns, crashes, and high latency in your code.

You can mostly avoid memory issues in your program if you have awareness of what causes memory problems in the first place. There are a few common scenarios that cause memory leaks in code.

#### Messy Closures

```js
function bigObjMaker() {
    const bigObj = {};
    return (key, val) => {
        bigObj[key] = val;
        console.log(bigObj);
    }
}
let bigMemoryUser = bigObjMaker();
 
Array(1000).fill(1).map((x,i) => {
    bigMemoryUser(i, i);
});
```

#### Dangling Timers and Event Listeners
You might be used to using `setInterval()` or other browser APIs in your code. Sometimes, you can wind up with a dangling timer or callback that references nodes or memory that your program doesn’t need anymore. If the handler is still active, anything it is referencing can’t be garbage collected.

```js
function cb() {
    let count = 0;
 
    return function() {
         count++;
         console.log(count);
    }
}
 
setInterval(cb(), 1000);
```

In the example, the `counter` variable is in the closure when you call `cb()`. When we use the `setInterval()` callback, it repeatedly calls that function `cb()` every 1000ms (set by the second argument). If you don’t assign the `setInterval()` call to a variable, you’ll get a memory leak if you can’t clear the interval later.

```js
let intervalID = setInterval(cb(), 100);
clearInterval(intervalID); // You can use a DOM element to call `clearInterval()`
```

The second snippet shows how you can assign a variable the value of calling `setInterval()` so that you can clear it when the time comes.

Another scenario to watch out for is the existence of anonymous functions when you use event listeners:

```js
const lotsOfMemory = "Imagine this is a value that uses a lot of memory"
 
document.addEventListener('scroll', function() {
 cb(lotsOfMemory);
});
```

In the example, the `lotsOfMemory` string will be stored in the closure of the anonymous function that is called on scroll events.

#### Circular References
If two objects have pointers that reference each other, a _circular reference_ is formed.

```js
let first = new Object();
let second = new Object();
 
first.aProperty = second;
second.anotherProperty = first;
```

As you can see in the example, the `first` object has a property `aProperty` that references the `second` object and the `second` object has a property `anotherProperty` that references the `first` object. Since these two objects reference each other through their properties, they’ll each wind up having a reference count of two. Circular references can cause memory leaks due to the reference-counting algorithm. Luckily, the mark-and-sweep algorithm — used by most browsers — handles that shortcoming.

### Declaring Variables on the Global Object

```js
function helloWorld() {
  // below greeting does not use a `let`, `const` or `var` statement to
  // declare the variable, so it's added to the global object after we
  // call `helloWorld()`
   greeting = "Hello world"; 
 
// This also leaks into the global `this`
  this.greeting2 = "Goodbye!"; 
}
 
helloWorld();
```

This type of issue is easy to avoid as long as you remember scoping rules and always use an appropriate `let` or`const` statement to assign your variables with the correct block scoping. You can also use strict-mode to help keep your global scope clean. Since global variables are available from the root, they never get garbage collected.

### Memory Behavior Can Cause Unexpected Outcomes in Code
Since JavaScript handles garbage collection, it also determines how often it performs garbage collection. The frequency of garbage collection can cause performance issues for your application. Some aspects of your code, like high object churn, can cause more frequent garbage collection, which in turn can slow down your program. One solution to this is to use an object pool, which retains some memory as an unused object that you can recycle instead of allocating and garbage collecting memory.


## Debugging Memory Issues in JavaScript

### How memory issues can impact performance and end-user experience
When your code has memory leaks or you try to use more memory than is available for your program, it can cause websites to slow down and crash. Accidentally introducing memory leaks into your application can be as easy as either of these scenarios:

- Adding an event listener but never removing it
- Adding variables to the global object

When you set objects as data on a DOM element, it can lead you to use more memory than is available, or can even lead to a memory leak if you never remove the DOM object. (For example, you might render a modal box off-screen and keep it there.) When that happens in production, your end users experience the impact.

To find the source of memory issues, we have to consider questions like:

- From where was memory allocated?
- Why wasn’t some piece of memory garbage collected?
- How is memory usage growing over time?

### Developer Tools that can help you debug memory issues
Most browsers, including Google Chrome, Firefox, and Safari, have built-in tools you can use to debug and test your code.

There are a few different tools available in the Memory Inspector:

- **Heap Snapshot**: This tool shows you how memory is distributed among a page’s JavaScript objects and related DOM nodes.
- **Allocation instrumentation on timeline**: This tool shows JavaScript memory allocations over time, and can be used to isolate memory leaks.
- **Allocation sampling**: We can use this to record memory allocations using a sampling method. This tool is best for long-running operations.

#### Heap Snapshot
Heap snapshots are great to use when debugging memory issues, because you can see what is taking up memory at a given time and compare between times. This view shows:

- What objects are in memory
- Details about the objects that are in memory, like the constructor function that was used to make the object
- How objects reference each other
- The size of memory objects are using
- What’s been added or failed to be garbage collected between snapshots

The Heap Snapshot tab has 4 different views:

- **Summary view**: This view groups objects by constructor and can be used to track down DOM leaks.
- **Comparison view**: This displays the difference between Heap snapshots. So if you use more memory or have memory garbage collected between snapshots, you can identify if you have a memory leak based on reference counts and change in freed memory. Note that this view will only be available if you have 2 or more heap snapshots saved in the DevTools Memory Panel.
- **Containment view**: This view is helpful for analyzing objects referenced in the global namespace (Window) to track down why they are not being garbage collected.
- **Statistics view**: This shows a breakdown of how memory is being used based on various categories, like Code, Strings, and JS arrays.

#### Allocation Instrumentation on Timeline
You can use the allocation timeline to identify objects that aren’t being garbage collected when they should be and therefore remain in memory. It is a combination of details you’d find in the heap snapshot, but with the addition of timeline tracking that takes updated snapshots as frequently as every 50 ms. You can use the allocation timeline by making a recording and performing page actions while the recording is underway.

This view shows:

- Where objects were allocated during code execution
- How often garbage is being collected

#### Allocation Sampling
Allocation sampling is similar to the allocation timeline, but has lower performance overhead. Snapshots are taken as a sample of the stack trace rather than with a regular cadence as they are when using the allocation timeline. You can use allocation sampling when you need to record snapshots for long-running operations and use the stack trace to identify where allocations are originating.

This view shows:

- What lines of code are creating garbage for the garbage collector
- What lines of code are allocating new heap memory

### Chrome Dev Tools Lab: How to use the Memory Inspector

- **Distance**: Using the shortest path of nodes from the Window/root, this is the count of nodes on that path.
- **Shallow Size**: Shallow size is the size in bytes of the object’s internal memory. Often, strings and external arrays are in memory in _renderer memory_. Renderer memory is a combination of the native memory, JavaScript heap memory of the page, and JavaScript heap memory of all of the workers that were started by the page.
- **Retained Size**: Retained size is the maximum retained size in bytes of a single object from objects of the same class. Once an object’s memory can be freed, this is the memory that is freed.

While there’s no magic memory number, for a frame of reference — if you’re building a Todo List application and it takes up 1 GB of memory, that is extremely high and there’s likely room for optimizations, whereas if you’re building a video game and it takes up 1 GB of memory, that would be really great and likely wouldn’t need optimizations.


# Design Patterns in JavaScript

## Watch Out for Anti-Patterns

In contrast to design patterns being best practices, anti-patterns describe ineffective solutions to problems that result in bad things happening, such as:

- Namespace pollution — unexpected behavior from interactions from different clients
- Increased code complexity
- Code being difficult to understand and update
- Difficulty with testing and debugging code

You’ll notice some “approved” design patterns also make the list as anti-patterns. In those cases, if the end result winds up being a good or bad choice depends on the implementation context.

Some common anti-patterns include:

- _God Object_: This name is given to an object that does or knows too much. It is an all-knowing and all-encompassing object. While it might seem easier at first to have all of your properties and methods in one place, doing so can cause issues down the line when you go to update and maintain the code base or collaborate with other developers.
- _Big Ball of Mud_/ _Spaghetti Code_: This is when your code lacks any perceivable architecture. It is hard to figure out where code for a specific functionality is located and what other code depends on it.
- _Yo-Yo Problem_: If you find yourself moving from class definition to class definition to understand inheritance and what is happening among classes, you are experiencing the yo-yo problem, which is named due to your head yo-yoing across the screen.
- _Singleton_: We’ll explore this below as a classic design pattern, but it’s worth noting that if used improperly, the Singleton pattern can take you into anti-pattern territory because of the restrictions it imposes.
- Polluting the global namespace (i.e. defining too many variables at the global scope level).
- Modifying or extending the `Object` class prototype. All objects in JavaScripts have a `Prototype` property that can be altered with methods and properties and all new objects inherit from this root `Object` by default. However, altering it is a huge no-no.

## What an Anti-Pattern Looks Like
In the example below of what not to do, `Customer` objects are all-knowing and have too much responsibility–this code follows the “God Object” anti-pattern.

```js
class Customer {
    constructor(userId, first, last) {
        this.userId = userId;
        this.first = first;
        this.last = last;
        this.itemsPurchased = [];
        this.transactions = [
             { transactionId: 1, transactionTotal: 433 },
             { transactionId: 2, transactionTotal: 289 },
             { transactionId: 3, transactionTotal: 99 },
             { transactionId: 4, transactionTotal: 600 }
        ];
 }
    getTotal() {
        return this.transactions.reduce((a,b) => ({transactionTotal: a.transactionTotal + b.transactionTotal}, 0)).transactionTotal;
 }
}
 
let bilbo = new Customer(1, "Bilbo", "Baggins");
bilbo.getTotal(); // 1421
```

We’d want to refactor the above code so the `Customer` objects are only responsible for information directly about the customer, like the customer id, and first and last names. New types of classes — like Transactions, Transaction, and Products — can handle additional information and methods.

Design patterns are commonly grouped into a classification scheme that has three purpose-based categories:

- Creational
- Structural
- Behavioral

## The Creational Category
When you need to control how your objects are created or instantiated, _Creational_ patterns are the right fit.

Creational patterns include:

- Factory
- Singleton
- Abstract Factory
- Constructor
- Prototype

### Factory Pattern
Functions that use the Factory Pattern use a predefined template to return an object with properties and methods. The arguments are used to construct the object, while the methods are usually part of the template.

#### Implementation of the Factory Pattern
In the code example below, the function `createBook()` takes 3 arguments: `title`, `author`, and `read`. (The third argument is optional.) The function returns an object literal with 3 properties (`title`, `author`, and `read`) and 2 methods (`.getDescription()` and `.readBook()`).

```js
function createBook(title, author, read = false) {
    return {
        title: title,
        author: author,
        read: read,
        getDescription() {
            console.log(`${this.title} was written by ${this.author}. I ${this.read ? "have" : "have not"} read it.`);
        },
        readBook() {
            this.read = true;
        },
    }
}
```

We can then instantiate objects and call the methods that become part of the object’s properties, or modify the properties directly.

```js
const beloved = createBook("Beloved", "Toni Morrison");
console.log(beloved);
/*
{
    title: 'Beloved',
    author: 'Toni Morrison',
    read: false,
    getDescription: [Function: getDescription],
    readBook: [Function: readBook]
}
*/
 
// call the `.readBook()` method
beloved.readBook(); // read is updated to true
 
// modifies the property directly
beloved.title = "I can change the property." 
```

### Singleton Pattern
As the name implies, we use the Singleton design pattern when we need exactly one instance of a class. Often, it’s used with the goal of managing global application state, but without using actual global scope. Singletons act as a shared resource namespace with a single point of access for functions. You might be wondering when you’d only want a single instance of an object. Here are a few real-world use cases:

- Thread pools
- Caches
- Logging options
- Configuration settings
- Browser load time impact of Singleton globally accessible variables vs real global variables (that was a mouth full)
- Database connections: reuse existing connections instead of creating new ones, which would increase application and database load

Note: Many of those options can also be handled with modules.

The single instance restriction is established through the way the class is implemented. A method can be written to check if an instance already exists, and only return a new object if it doesn’t already exist.

#### Implementation of the Singleton Pattern
In the code snippet, we implement a Singleton class called `Singleton`. The `constructor()` is critical to the implementation. In the code, we check if an `instance` property already exists. If not, we set that property. If it does, we return the `instance` property. There is a method named `.getInstance()` defined as well — this is not necessary but makes your code easier to reason with.

When you instantiate your instance of `Singleton`, you use the `new` operator when calling `Singleton()`. Given the code in the `constructor()` method, you could theoretically always call your single instance as `new Singleton()` because it will always return your original instance. However, by providing a `.getInstance()` method, you can instead call it as `Singleton.getInstance()`, which is easier to understand and clearer in intent.

```js
class Singleton {
    constructor() {
        if (!Singleton.instance) {
            Singleton.instance = this;
        }
        return Singleton.instance;
     }
     static getInstance() {
         return this.instance;
     }
}
 
const instance = new Singleton();
console.log(Singleton.getInstance()); // logs "Singleton {}"
```

## The Structural Category
_Structural_ design patterns handle relationships between objects. They define how objects and classes can be composed to provide new functionality to objects or create larger structures. For example, an object can be used in the definition of another object to make new functions available, or classes can inherit from super classes.

Structural patterns include:

- Facade
- Proxy
- Flyweight
- Adapter
- Decorator
- Composite
- Bridge

### Proxy Pattern
The _Proxy Pattern_ protects access to an object by acting as a placeholder that intercepts and redefines the operations of the target object. This pattern is particularly useful for things like network requests, as it can help avoid redundant requests.

There is a `Proxy` object built into ES6 that can be used to implement the proxy pattern. This object has two parameters:

- `target`: the object that is being proxied
- `handler`: a definition of any custom behavior handled by the proxy object

If you use the `Proxy()` constructor with an empty handler, it would just behave like the target object. `Proxy` objects have built-in handler function objects, which are called _traps_. Traps are used to call the target object.

`Proxy` objects are used alongside the `Reflect` object, which has methods with the exact same name as the `Proxy` object’s traps. The difference is the `Reflect` methods forward default operations to the target object.

In the code example below, the `get()` trap is used to modify property access of the target object. On the other hand, `Reflect.get()` is a static method that retrieves properties from the target object.

When you run the code below, the proxy will intercept the `city1` property and return `Montreal, Canada`. However, when the key is not `city1`, it will use `Reflect.get()` and return the original value, so `proxy.city2` returns `Mombasa, Kenya`.

```js
const target = {
    city1: "Marseille, France",
    city2: "Mombasa, Kenya"
};
 
const handler = {
    get: function (target, prop, receiver) {
        if (prop === "city1") {
            return "Montreal, Canada";
        }
        return Reflect.get(...arguments);
    },
};
 
const proxy = new Proxy(target, handler);
 
console.log(proxy.city1); // Montreal, Canada
console.log(proxy.city2); // Mombasa, Kenya
```

### Facade Pattern
The _Facade Pattern_ is a single class that takes all of the complexity of a subsystem, and hides it. It is commonly used in JavaScript libraries and to simplify interactions with APIs. Use this pattern to create an easier interface for end users.

In the pseudo-code example below, the `VideoConverter` class provides access to the subsystem classes and is meant to direct client requests across the moving parts. The client would only interface with the `VideoConverter` class.

```js
class VideoConverter {
    constructor() {}
        convertNewVideo(...args) {
        // This method can interact with `Audio`, `Video`, `Codec`, and `Compression`
    }
}
 
class Audio {
    constructor() {}
    // complex subsystem code
}
 
class Video {
    constructor() {}
    // complex subsystem code
}
 
class Codec {
    constructor() {}
    // complex subsystem code
}
 
class Compression {
    constructor() {}
    // complex subsystem code
}
```

## The Behavioral Category
Behavioral patterns streamline messages between unrelated objects in your code by delegating how objects can communicate. They encapsulate the communication behavior to decouple messages between senders and receivers.

Behavioral Patterns include:

- Iterator
- Mediator
- Observer
- Visitor

### Observer Pattern
With the Observer Pattern, objects can have dependencies that “subscribe” to view changes to another object. The notifications can flow in a one-to-many relationship, i.e. one changing object can notify many other objects.

#### Implementation of the Observer Pattern
In the example, a basic model of the notification flow occurs between `Account` objects, which use the `.addToFollowers()` and `.removeFromFollowers()` methods to subscribe other `Account` objects to its feed activity. In the real-world, you’re more likely to use the Observer pattern across different types of objects to track changes of state, but the example shows how updates can be pushed to other objects.

Here we create 3 account objects, `a`, `b`, and `c`. The `a` object uses its `.addToFollowers()` method to be ‘followed’ by the `b` and `c` objects. Then, the `a` object publishes a new post, “Hello, world”. We can log the `b` or `c` object to see the post was added to their `feed` property.

```js
class Account {
    constructor() {
        this.followers = [];
        this.feed = [];
    }
    addToFollowers(follower) {
        this.followers.push(follower);
    }
    removeFromFollowers(follower) {
        this.followers.splice(this.followers.indexOf(follower), 1);
    }
    publish(post) {
        this.followers.forEach(follower => follower.update(post));
    }
    update(post) {
      this.feed.push(post);
    }
}
 
let a = new Account();
let b = new Account();
let c = new Account();
 
a.addToFollowers(b);
a.addToFollowers(c);
 
a.publish("Hello, world");
 
console.log(a);   
/* Output shows b and c objects listed in a's followers array:
[
  Account { followers: [], feed: [ 'Hello, world' ] },
  Account { followers: [], feed: [ 'Hello, world' ] }
] 
*/
 
console.log(b); 
// Account { followers: [], feed: [ 'Hello, world' ] }
```

### Mediator Pattern
The Mediator Pattern in code acts as a central interface to encapsulate how different parts of your codebase can communicate with each other.

This pattern helps prevent having too many direct relationships between different classes or components and helps disparate components know about changes in application state. As a benefit, it also makes your code more reusable and easier to modify down the line since classes are not tightly coupled.

#### Implementation of the Mediator Pattern
In the example below, a `Passenger` object can send a request through a `RideshareApp` object, which acts as a mediator between `Driver` objects and `Passenger` objects. The interface for the `Passenger` and `Driver` objects are simpler than what you’d see in a real-world scenario and do not deal with the complexity of communicating between these two types of objects. In fact, in our example, these two types of objects don’t need to know what instances exist.

```js
class Passenger {
    constructor(name) {
      this.name = name;
    }
    sendRequest(rideshareapp) {
      rideshareapp.receiveRequest(this.name);
    }
}
 
class Driver {
    constructor(name) {
        this.name = name;
    }
    goOnline(rideshareapp) {
        rideshareapp.addDriver(this.name);
    }
}
 
class RideshareApp {
    constructor() {
      this.drivers = [];
      this.riders = [];
    }
    addDriver(name) {
        this.drivers.push(name);
    }
    updateDriverArray(name) {
        this.drivers.splice(this.drivers.indexOf(name), 1);
    }
    assignDriver() {
        // We will assume there are always more drivers than riders
        return this.drivers[Math.floor(Math.random(this.drivers.length))].name;
    }
    receiveRequest(passenger) {
        const driver = this.assignDriver();
        console.log(driver);
        this.sendNotification(passenger, driver);
        this.updateDriverArray(driver);
    }
    sendNotification(passenger, driver) {
        console.log(`${driver} is assigned to ${passenger}.`)
    }
}
 
const rideshareapp = new RideshareApp();
 
const james = new Passenger("James");
const sarah = new Driver("Sarah");
 
rideshareapp.addDriver(sarah);
james.sendRequest(rideshareapp);
```

## Putting It All Together: How to Select the Right Design Pattern
There are a few steps you can take to choose an appropriate design pattern.

- Think about the interface of each object and how it will interact with other objects. Are you encapsulating the right information in each object, or should you create a new type of object?
- Consider the specifications for each object and how you will handle each property. What other objects need awareness of this object’s properties? How will you handle updates?
- Remember the high-level intent of each group of design patterns. If you are designing for object behavior versus how the object is created, review design pattern options in the Behavioral category.
- After you pick a design, review the design to see if there’s any reason you should pick a different design. Is there something you need to refactor, or a problem that seems messy to handle?
- Is there anything you want to change without redesigning your code? Can you do that with your current design pattern selection? Or do you need to introduce another pattern? Remember that you can use multiple different design patterns in the same code base.

## Design Patterns in Architecture
Design patterns can also be applied to system architectures. We can move “up the stack” from code units to processes and systems.

### Using the Proxy Pattern to Implement a Proxy Server
It’s common to use [proxy servers](https://www.codecademy.com/resources/blog/what-is-a-proxy-server/) to streamline web traffic and protect sensitive data. As it happens, the Proxy pattern is a great fit for implementing a proxy server.

You may recall that the Proxy pattern protects access to objects by intercepting and redefining operations on the target object. That is exactly what you need for implementing a proxy server, which can be used to hide your identity from remote servers or modify requests and responses.

The pattern can increase the efficiency of requests; one of the advantages is that we can use the proxy to cache results and handle requests from multiple users.

### Using the Facade Pattern to Implement Microservices
Microservices are an architectural style that structures an application as a collection of services. In theory, microservices make it easier for business units to write their own APIs that can interact with other parts of the code base.

You can use the facade pattern to implement interoperability between these isolated services. The facade is used as an interface so that the individual pieces do not become dependent or tightly coupled and the clients do not need to know about the underlying code implementation of other services.

