# Basics of Asynchronous JavaScript
## General Asynchronous Programming Concepts

### What is Synchronous Code?
*Synchronous code* executes in sequential order — it starts with the code at the top of the file and executes line by line until it gets to the end of the file. This type of behavior is known as *blocking* (or blocking code) since each line of code cannot execute until the previous line finishes.

### What is Asynchronous Code?
*Asynchronous code* can be executed in parallel to other code that is already running. Without the need to wait for other code to finish before executing, our apps can save time and be more efficient. This type of behavior is considered *non-blocking*.

### Asynchronous Code Under the Hood
For most programming languages, the ability to execute asynchronous code depends on the number of *threads* that an app has access to. We can think of a thread as a resource that a computer provides an app to do a task. Typically one thread allows for an app to complete one task.

The more threads we have, the more tasks we can run concurrently. Also, in most modern-day computers, multithreading is achieved by having a CPU that has multiple cores or by some other technology.

### Asynchronous Code in Web Development
If we use synchronous (blocking) code in the browser, we might be stopping a user from being able to interact with a web app until the code is done running.

However, if we opt for an asynchronous approach, we can cut down on the wait time. We’d load only the code that’s necessary for user interactions and then load up other bits of code in the background.


## Introduction to Asynchronous JavaScript

### Asynchronous Code in Web Development
It is our job as developers to think about how much time it takes to complete a task and how to plan around that wait. Tasks like contacting the back-end to retrieve information, querying our database for user information, or making a request to an external server, like a 3rd party API, take varying amounts of time. Since we aren’t sure when we’ll get this information back, we can use asynchronous code to run these tasks in the background.

### JavaScript and Asynchronous Code
JavaScript is a *single-threaded* language. This means it has a single thread that can carry out one task at a time. However, Javascript has what is known as the *event loop*, a specific design that allows it to perform asynchronous tasks even while only using a single thread.

#### Asynchronous Callbacks
One common example of asynchronicity in JavaScript is the use of *asynchronous callbacks*. This is a type of callback function that executes after a specific condition is met and runs concurrently to any other code currently running.

```js
easterEgg.addEventListener('click', () => {
  console.log('Up, Up, Down, Down, Left, Right, Left, Right, B, A');
});
```

In the code above, the function passed as the second argument of `.addEventListener()` is an asynchronous callback — this function doesn’t execute until the `easterEgg` is clicked.

#### setTimeout
In addition to asynchronous callbacks, JavaScript provides a handful of built-in functions that can perform tasks asynchronously. One function that is commonly used is the `setTimeout()` function.

With `setTimeout()` we can write code that tells our JavaScript program to wait a minimum amount of time before executing its callback function.

```js
setTimeout(() => {
  console.log('Delay the printing of this string, please.');
}, 1000);
```

Notice that `setTimeout()` takes 2 arguments, a callback function and a number specifying how long to wait before executing the function. In the example above, the function will print `'Delay the printing of this string, please.'` after 1000 milliseconds (or 1 second) have passed.

Since `setTimeout()` is non-blocking, we can be executing multiple lines of code at the same time! 

```js
setTimeout(() => {
  console.log('Delay the printing of this string, please.');
}, 1000);
console.log('Doing important stuff.');
console.log('Still doing important stuff.'); 
```

In web development, this means we can write code to wait for an event to trigger all while a user goes on interacting with our app.

#### setInterval()
Another common built-in function is `setInterval()` which also takes a callback function and a number specifying how often the callback function should execute. 

```js
setInterval(() => {
  alert('Are you paying attention???')
}, 300000)
```

The `setInterval()` would call the `alert()` function and show a pop-up message of `'Are you paying attention???'` every 300000 milliseconds (or 5 minutes).

While we wait for our alert to chime in every 5 minutes, our users could still use our app!

With `setInterval()`, we can programmatically create an alarm, a countdown timer, set the frequency of an animation, and so much more!


# Concurrency Model and Event Loop in JavaScript

## Why Do We Need an Event Loop?
JavaScript is a *single-threaded language*, which means that two statements can’t be executed simultaneously.

Input/output (I/O) is handled with events and callbacks so code execution can continue.

## Concurrency in JavaScript
Usually when we think about *concurrency* in programming, it means that two or more procedures are executed at the same time on the same shared resources. Since JavaScript is single-threaded, we’ll never have that flavor of “true” concurrency. However, we can emulate concurrency using the event loop.

## What Is the Event Loop?
At a high level, the event loop is a system for managing code execution.

We have data structures that we call the heap and the call stack, which are part of the JavaScript engine. The heap and call stack interact with Node and Web APIs, which pass messages back to the stack via an event queue. The event queue’s interaction with the call stack is managed by an event loop. All together, those parts maintain the order of code execution when we run asynchronous functions.

## Understand the Components of the Event Loop
The *event loop* is made up of these parts:

- Memory Heap
- Call Stack
- Event Queue
- Event Loop
- Node or Web APIs

### The Heap
The *heap* is a block of memory where we store objects in an unordered manner. JavaScript variables and objects that are currently in use are stored in the heap.

### The Call Stack
The *stack*, or *call stack*, tracks what function is currently being run in your code.

When you invoke a function, a *frame* is added to the stack. Frames connect that function’s arguments and local variables from the heap. Frames enter the stack in a *last in, first out* (LIFO) order.

```js
function foo() {
 return function bar() {
   return function baz() {
     return 'I love CodeCademy'
   }
 }
}
console.log(foo()()());
```

The function executing at any given point in time is at the top of the stack. In our example code, since we have nested functions, they will all be added to the stack until the innermost function has been executed. When the function finishes executing e.g. returns, its frame is removed from the stack.

You might have noticed that `global()` is at the bottom of the stack–when you first initiate a program, the *global execution context* is added to the call stack, which contains the global variable and lexical environment. Each subsequent frame for a called function has a function execution context that includes the function’s lexical and variable environment.

So when we say the call stack tracks what function is currently being run in our code, what we are tracking is the current execution context. When a function runs to completion, it is popped off of the call stack. The memory, or the frame, is cleared.

### The Event Queue
The *event queue* is a list of messages corresponding to functions that are waiting to be processed. In the diagram, these messages are entering the event queue from sources such as various web APIs or async functions that were called and are returning additional events to be handled by the stack. Messages enter the queue in a first in, first out (FIFO) order. No code is executed in the event queue; instead, it holds functions that are waiting to be added back into the stack.

### The Event Loop
This event loop is a specific part of our overall event loop concept. Messages that are waiting in the event queue to be added back into the stack are added back via the event loop. When the call stack is empty, if there is anything in the event queue, the event loop can add those one at a time to the stack for execution.

1. First the event loop will poll the stack to see if it is empty.
2. It will add the first waiting message.
3. It will repeat steps 1 and 2 until the stack has cleared.

## Summary
Thanks to the event loop, JavaScript is a single-threaded, event-driven language that can run non-blocking code asynchronously. The Event Loop can be summarized as: when code is executed, it is handled by the heap and call stack, which interact with Node and Web APIs. Those APIs enable concurrency and pass asynchronous messages back to the stack via an event queue. The event queue’s interaction with the call stack is managed by an event loop. All together, those parts maintain the order of code execution when we run asynchronous functions.


# Learn JavaScript Syntax: Promises
## JavaScript Promises

### Introduction
An *asynchronous operation* is one that allows the computer to “move on” to other tasks while waiting for the asynchronous operation to complete. Asynchronous programming means that time-consuming operations don’t have to bring everything else in our programs to a halt.

### What is a Promise?
Promises are objects that represent the eventual outcome of an asynchronous operation. A `Promise` object can be in one of three states:

- **Pending**: The initial state— the operation has not completed yet.
- **Fulfilled**: The operation has completed successfully and the promise now has a *resolved value*. For example, a request’s promise might resolve with a JSON object as its value.
- **Rejected**: The operation has failed and the promise has a reason for the failure. This reason is usually an `Error` of some kind.

We refer to a promise as *settled* if it is no longer pending— it is either fulfilled or rejected.

All promises eventually settle, enabling us to write logic for what to do if the promise fulfills or if it rejects.

### Constructing a Promise Object
To create a new `Promise` object, we use the `new` keyword and the `Promise` constructor method:

```js
const executorFunction = (resolve, reject) => { };
const myFirstPromise = new Promise(executorFunction);
```

The `Promise` constructor method takes a function parameter called the *executor function* which runs automatically when the constructor is called. The executor function generally starts an asynchronous operation and dictates how the promise should be settled.

The executor function has two function parameters, usually referred to as the `resolve()` and `reject()` functions. The `resolve()` and `reject()` functions aren’t defined by the programmer. When the `Promise` constructor runs, JavaScript will pass its own `resolve()` and `reject()` functions into the executor function.

- `resolve` is a function with one argument. Under the hood, if invoked, `resolve()` will change the promise’s status from `pending` to `fulfilled`, and the promise’s resolved value will be set to the argument passed into `resolve()`.
- `reject` is a function that takes a reason or error as an argument. Under the hood, if invoked, `reject()` will change the promise’s status from `pending` to `rejected`, and the promise’s rejection reason will be set to the argument passed into `reject()`.

```js
const executorFunction = (resolve, reject) => {
  if (someCondition) {
      resolve('I resolved!');
  } else {
      reject('I rejected!'); 
  }
}
const myFirstPromise = new Promise(executorFunction);
```

In practice, promises settle based on the results of asynchronous operations. For example, a database request may fulfill with the data from a query or reject with an error thrown.

### The Node setTimeout() Function
`setTimeout()` is a Node API (a comparable API is provided by web browsers) that uses callback functions to schedule tasks to be performed after a delay. `setTimeout()` has two parameters: a callback function and a delay in milliseconds.

```js
const delayedHello = () => {
  console.log('Hi! This is an asynchronous greeting!');
};
 
setTimeout(delayedHello, 2000);
```

In at least two seconds `delayedHello()` will be invoked. This delay is performed asynchronously—the rest of our program won’t stop executing during the delay. Asynchronous JavaScript uses something called the *event-loop*. After two seconds, `delayedHello()` is added to a line of code waiting to be run. Before it can run, any synchronous code from the program will run. Next, any code in front of it in the line will run. This means it might be more than two seconds before `delayedHello()` is actually executed.

```js
const returnPromiseFunction = () => {
  return new Promise((resolve, reject) => {
    setTimeout(( ) => {resolve('I resolved!')}, 1000);
  });
};
 
const prom = returnPromiseFunction();
```

### Consuming Promises
The initial state of an asynchronous promise is `pending`, but we have a guarantee that it will settle.

Promise objects come with an aptly named `.then()` method. It allows us to say, “I have a promise, when it settles, then here’s what I want to happen…”

`.then()` is a higher-order function— it takes two callback functions as arguments. We refer to these callbacks as *handlers*. When the promise settles, the appropriate handler will be invoked with that settled value.

- The first handler, sometimes called `onFulfilled`, is a *success handler*, and it should contain the logic for the promise resolving.
- The second handler, sometimes called `onRejected`, is a *failure handler*, and it should contain the logic for the promise rejecting.

We can invoke `.then()` with one, both, or neither handler! This allows for flexibility, but it can also make for tricky debugging. If the appropriate handler is not provided, instead of throwing an error, `.then()` will just return a promise with the same settled value as the promise it was called on. One important feature of `.then()` is that it always returns a promise.

### Success and Failure Callback Functions
To handle a “successful” promise, or a promise that resolved, we invoke `.then()` on the promise, passing in a success handler callback function:

```js
const prom = new Promise((resolve, reject) => {
  resolve('Yay!');
});
 
const handleSuccess = (resolvedValue) => {
  console.log(resolvedValue);
};
 
prom.then(handleSuccess); // Prints: 'Yay!'
```

Since `prom` resolves, `handleSuccess()` is invoked with prom‘s resolved value, `'Yay'`, so `'Yay'` is logged to the console.

With typical promise consumption, we won’t know whether a promise will resolve or reject, so we’ll need to provide the logic for either case. We can pass both a success callback and a failure callback to `.then()`.

```js
let prom = new Promise((resolve, reject) => {
  let num = Math.random();
  if (num < .5 ){
    resolve('Yay!');
  } else {
    reject('Ohhh noooo!');
  }
});
 
const handleSuccess = (resolvedValue) => {
  console.log(resolvedValue);
};
 
const handleFailure = (rejectionReason) => {
  console.log(rejectionReason);
};
 
prom.then(handleSuccess, handleFailure);
```

### Using catch() with Promises
`.then()` will return a promise with the same settled value as the promise it was called on if no appropriate handler was provided. This implementation allows us to separate our resolved logic from our rejected logic. Instead of passing both handlers into one `.then()`, we can chain a second `.then()` with a failure handler to a first `.then()` with a success handler and both cases will be handled.

```js
prom
  .then((resolvedValue) => {
    console.log(resolvedValue);
  })
  .then(null, (rejectionReason) => {
    console.log(rejectionReason);
  });
  ```

Since JavaScript doesn’t mind whitespace, we follow a common convention of putting each part of this chain on a new line to make it easier to read. To create even more readable code, we can use a different promise function: `.catch()`.

The `.catch()` function takes only one argument, `onRejected`. In the case of a rejected promise, this failure handler will be invoked with the reason for rejection. Using `.catch()` accomplishes the same thing as using a `.then()` with only a failure handler.

```js
prom
  .then((resolvedValue) => {
    console.log(resolvedValue);
  })
  .catch((rejectionReason) => {
    console.log(rejectionReason);
  });
  ```

### Chaining Multiple Promises
One common pattern we’ll see with asynchronous programming is multiple operations which depend on each other to execute or that must be executed in a certain order.

This process of chaining promises together is called *composition*.

```js
firstPromiseFunction()
.then((firstResolveVal) => {
  return secondPromiseFunction(firstResolveVal);
})
.then((secondResolveVal) => {
  console.log(secondResolveVal);
});
```

In order for our chain to work properly, we had to return the promise `secondPromiseFunction(firstResolveVal)`. This ensured that the return value of the first `.then()` was our second promise rather than the default return of a new promise with the same settled value as the initial.

### Avoiding Common Mistakes
**Mistake 1**: Nesting promises instead of chaining them.

```js
returnsFirstPromise()
.then((firstResolveVal) => {
  return returnsSecondValue(firstResolveVal)
    .then((secondResolveVal) => {
      console.log(secondResolveVal);
    })
})
```

We invoke a second `.then()` to handle the logic for the second promise settling all inside the first `then()`!

Instead of having a clean chain of promises, we’ve nested the logic for one inside the logic of the other. Imagine if we were handling five or ten promises!

**Mistake 2**: Forgetting to `return` a promise.

```js
returnsFirstPromise()
.then((firstResolveVal) => {
  returnsSecondValue(firstResolveVal)
})
.then((someVal) => {
  console.log(someVal);
})
```

We invoke a second `.then()`. It’s supposed to handle the logic for the second promise, but since we didn’t return, this `.then()` is invoked on a promise with the same settled value as the original promise!

Since forgetting to return our promise won’t throw an error, this can be a really tricky thing to debug!

### Using Promise.all()
To maximize efficiency we should use *concurrency*, multiple asynchronous operations happening together. With promises, we can do this with the function `Promise.all()`.

`Promise.all()` accepts an array of promises as its argument and returns a single promise. That single promise will settle in one of two ways:

- If every promise in the argument array resolves, the single promise returned from `Promise.all()` will resolve with an array containing the resolve value from each promise in the argument array.
- If any promise from the argument array rejects, the single promise returned from `Promise.all()` will immediately reject with the reason that promise rejected. This behavior is sometimes referred to as *failing fast*.

```js
let myPromises = Promise.all([returnsPromOne(), returnsPromTwo(), returnsPromThree()]);
 
myPromises
  .then((arrayOfValues) => {
    console.log(arrayOfValues);
  })
  .catch((rejectionReason) => {
    console.log(rejectionReason);
  });
  ```

### Review
- Promises are JavaScript objects that represent the eventual result of an asynchronous operation.
- Promises can be in one of three states: pending, resolved, or rejected.
- A promise is settled if it is either resolved or rejected.
- We construct a promise by using the `new` keyword and passing an executor function to the `Promise` constructor method.
- `setTimeout()` is a Node function which delays the execution of a callback function using the event-loop.
- We use `.then()` with a success handler callback containing the logic for what should happen if a promise resolves.
- We use `.catch()` with a failure handler callback containing the logic for what should happen if a promise rejects.
- Promise composition enables us to write complex, asynchronous code that’s still readable. We do this by chaining multiple `.then()`‘s and `.catch()`‘s.
- To use promise composition correctly, we have to remember to return promises constructed within a `.then()`.
- We should chain multiple promises rather than nesting them.
- To take advantage of concurrency, we can use `Promise.all()`.


# Learn JavaScript Syntax: Async-Await
## Async-Await

### Introduction
JavaScript is continually improving, and ES8 provides a new syntax for handling our asynchronous action, `async...await`. The `async...await` syntax allows us to write asynchronous code that reads similarly to traditional synchronous, imperative programs.

The `async...await` syntax is syntactic sugar— it doesn’t introduce new functionality into the language, but rather introduces a new syntax for using promises and generators. Both of these were already built in to the language.

### The async Keyword
The `async` keyword is used to write functions that handle asynchronous actions. We wrap our asynchronous logic inside a function prepended with the `async` keyword. Then, we invoke that function.

```js
async function myFunc() {
  // Function body here
};
 
myFunc();
```

We can also create `async` function expressions:

```js
const myFunc = async () => {
  // Function body here
};
 
myFunc();
```

`async` functions always return a promise. This means we can use traditional promise syntax, like `.then()` and `.catch` with our `async` functions. An `async` function will return in one of three ways:

- If there’s nothing returned from the function, it will return a promise with a resolved value of `undefined`.
- If there’s a non-promise value returned from the function, it will return a promise resolved to that value.
- If a promise is returned from the function, it will simply return that promise.

```js
async function fivePromise() { 
  return 5;
}
 
fivePromise()
.then(resolvedValue => {
    console.log(resolvedValue);
  })  // Prints 5
  ```

In the example above, even though we return `5` inside the function body, what’s actually returned when we invoke `fivePromise()` is a promise with a resolved value of `5`.

### The await Operator
`async` functions are almost always used with the additional keyword `await` inside the function body.

The `await` keyword can only be used inside an `async` function. `await` is an operator: it returns the resolved value of a promise. Since promises resolve in an indeterminate amount of time, `await` halts, or pauses, the execution of our `async` function until a given promise is resolved.

In most situations, we’re dealing with promises that were returned from functions. Generally, these functions are through a library.

In the example below, `myPromise()` is a function that returns a promise which will resolve to the string `"I am resolved now!"`.

```js
async function asyncFuncExample(){
  let resolvedValue = await myPromise();
  console.log(resolvedValue);
}
 
asyncFuncExample(); // Prints: I am resolved now!
```

We’re able to handle the logic for a promise in a way that reads like synchronous code.

### Writing async Functions
We’ve seen that the `await` keyword halts the execution of an `async` function until a promise is no longer pending. Don’t forget the `await` keyword! It may seem obvious, but this can be a tricky mistake to catch because our function will still run— it just won’t have the desired results.

```js
let myPromise = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve('Yay, I resolved!')
    }, 1000);
  });
}

async function noAwait() {
 let value = myPromise();
 console.log(value);
}
 
async function yesAwait() {
 let value = await myPromise();
 console.log(value);
}
 
noAwait(); // Prints: Promise { <pending> }
yesAwait(); // Prints: Yay, I resolved!
```

Without the `await` keyword, the function execution wasn’t paused. The `console.log()` on the following line was executed before the promise had resolved.

Remember that the `await` operator returns the resolved value of a promise. When used properly in `yesAwait()`, the variable `value` was assigned the resolved value of the `myPromise()` promise, whereas in `noAwait()`, `value` was assigned the promise object itself.

### Handling Dependent Promises
The true beauty of `async...await` is when we have a series of asynchronous actions which depend on one another. For example, we may make a network request based on a query to a database. In that case, we would need to wait to make the network request until we had the results from the database. With native promise syntax, we use a chain of `.then()` functions making sure to return correctly each one:

```js
function nativePromiseVersion() {
  returnsFirstPromise()
    .then((firstValue) => {
      console.log(firstValue);
      return returnsSecondPromise(firstValue);
    })
   .then((secondValue) => {
      console.log(secondValue);
    });
}
```

Here’s how we’d write an `async` function to accomplish the same thing:

```js
async function asyncAwaitVersion() {
  let firstValue = await returnsFirstPromise();
  console.log(firstValue);
  let secondValue = await returnsSecondPromise(firstValue);
  console.log(secondValue);
}
```

The `async...await` syntax also makes it easy to store and refer to resolved values from promises further back in our chain which is a much more difficult task with native promise syntax.

### Handling Errors
When `.catch()` is used with a long promise chain, there is no indication of where in the chain the error was thrown. This can make debugging challenging.
 
With `async...await`, we use `try...catch` statements for error handling. By using this syntax, not only are we able to handle errors in the same way we do with synchronous code, but we can also catch both synchronous and asynchronous errors. 

```js
async function usingTryCatch() {
 try {
   let resolveValue = await asyncFunction('thing that will fail');
   let secondValue = await secondAsyncFunction(resolveValue);
 } catch (err) {
   // Catches any errors in the try block
   console.log(err);
 }
}
 
usingTryCatch();
```

Since `async` functions return promises we can still use native promise’s `.catch()` with an `async` function.

```js
async function usingPromiseCatch() {
   let resolveValue = await asyncFunction('thing that will fail');
}
 
let rejectedPromise = usingPromiseCatch();
rejectedPromise.catch((rejectValue) => {
console.log(rejectValue);
})
```

This is sometimes used in the global scope to catch final errors in complex code.

### Handling Independent Promises
Remember that `await` halts the execution of our `async` function. This allows us to conveniently write synchronous-style code to handle dependent promises. But what if our `async` function contains multiple promises which are not dependent on the results of one another to execute?

```js
async function waiting() {
 const firstValue = await firstAsyncThing();
 const secondValue = await secondAsyncThing();
 console.log(firstValue, secondValue);
}
 
async function concurrent() {
 const firstPromise = firstAsyncThing();
 const secondPromise = secondAsyncThing();
console.log(await firstPromise, await secondPromise);
}
```

In the `waiting()` function, we pause our function until the first promise resolves, then we construct the second promise. Once that resolves, we print both resolved values to the console.

In our `concurrent()` function, both promises are constructed without using `await`. We then `await` each of their resolutions to print them to the console.

With our `concurrent()` function both promises’ asynchronous operations can be run simultaneously. If possible, we want to get started on each asynchronous operation as soon as possible! Within our `async` functions we should still take advantage of *concurrency*, the ability to perform asynchronous actions at the same time.

**Note**: if we have multiple truly independent promises that we would like to execute fully in parallel, we must use individual `.then()` functions and avoid halting our execution with `await`.

### Await Promise.all()
Another way to take advantage of concurrency when we have multiple promises which can be executed simultaneously is to `await` a `Promise.all()`.

We can pass an array of promises as the argument to `Promise.all()`, and it will return a single promise. This promise will resolve when all of the promises in the argument array have resolved. This promise’s resolve value will be an array containing the resolved values of each promise from the argument array.

```js
async function asyncPromAll() {
  const resultArray = await Promise.all([asyncTask1(), asyncTask2(), asyncTask3(), asyncTask4()]);
  for (let i = 0; i<resultArray.length; i++){
    console.log(resultArray[i]); 
  }
}
```

`Promise.all()` allows us to take advantage of asynchronicity— each of the four asynchronous tasks can process concurrently. `Promise.all()` also has the benefit of *failing fast*, meaning it won’t wait for the rest of the asynchronous actions to complete once any one has rejected. As soon as the first promise in the array rejects, the promise returned from `Promise.all()` will reject with that reason. As it was when working with native promises, `Promise.all()` is a good choice if multiple asynchronous tasks are all required, but none must wait for any other before executing.

### Review
- `async...await` is syntactic sugar built on native JavaScript promises and generators.
- We declare an `async` function with the keyword `async`.
- Inside an `async` function we use the `await` operator to pause execution of our function until an asynchronous action completes and the awaited promise is no longer pending.
- `await` returns the resolved value of the awaited promise.
- We can write multiple `await` statements to produce code that reads like synchronous code.
- We use `try...catch` statements within our `async` functions for error handling.
- We should still take advantage of concurrency by writing `async` functions that allow asynchronous actions to happen in concurrently whenever possible.


# APIs and HTTP Requests
## HTTP Requests

### Background
The internet is made up of a bunch of resources hosted on different servers. The term “resource” corresponds to any entity on the web, including HTML files, stylesheets, images, videos, and scripts. To access content on the internet, your browser must ask these servers for the resources it wants and then display these resources to you.

### What is HTTP?
HTTP stands for Hypertext Transfer Protocol and is used to structure requests and responses over the internet. HTTP requires data to be transferred from one point to another over the network.

The transfer of resources happens using TCP (Transmission Control Protocol). TCP manages the channels between your browser and the server. TCP is used to manage many types of internet connections in which one computer or device wants to send something to another. HTTP is the command language that the devices on both sides of the connection must follow in order to communicate.

### HTTP & TCP: How it Works
When you type an address such as www.codecademy.com into your browser, you are commanding it to open a TCP channel to the server that responds to that URL (or Uniform Resource Locator). A URL is like your home address or phone number because it describes how to reach you.

In this situation, your computer, which is making the request, is called the client. The URL you are requesting is the address that belongs to the server.

Once the TCP connection is established, the client sends a HTTP GET request to the server to retrieve the webpage it should display. After the server has sent the response, it closes the TCP connection. If you open the website in your browser again, or if your browser automatically requests something from the server, a new connection is opened which follows the same process described above. GET requests are one kind of HTTP method a client can call.

Suppose you want to check out the latest course offerings from http://codecademy.com. After you type the URL into your browser, your browser will extract the http part and recognize that it is the name of the network protocol to use. Then, it takes the domain name from the URL, in this case “codecademy.com”, and asks the internet Domain Name Server to return an Internet Protocol (IP) address.

Now the client knows the destination’s IP address. It then opens a connection to the server at that address, using the http protocol as specified. It will initiate a GET request to the server which contains the IP address of the host and optionally a data payload. The GET request contains the following text:

```
GET / HTTP/1.1
Host: www.codecademy.com
```

This identifies the type of request, the path on www.codecademy.com (in this case, “/“) and the protocol “HTTP/1.1.” HTTP/1.1 is a revision of the first HTTP, which is now called HTTP/1.0. In HTTP/1.0, every resource request requires a separate connection to the server. HTTP/1.1 uses one connection more than once, so that additional content (like images or stylesheets) is retrieved even after the page has been retrieved. As a result, requests using HTTP/1.1 have less delay than those using HTTP/1.0.

The second line of the request contains the address of the server which is "www.codecademy.com". There may be additional lines as well depending on what data your browser chooses to send.

If the server is able to locate the path requested, the server might respond with the header:

```
HTTP/1.1 200 OK
Content-Type: text/html
```

This header is followed by the content requested, which in this case is the information needed to render www.codecademy.com.

The first line of the header, HTTP/1.1 200 OK, is confirmation that the server understands the protocol that the client wants to communicate with (HTTP/1.1), and an HTTP status code signifying that the resource was found on the server. The second line, Content-Type: text/html, shows the type of content that it will be sending to the client.

If the server is not able to locate the path requested by the client, it will respond with the header:

```
HTTP/1.1 404 NOT FOUND
```

In this case, the server identifies that it understands the HTTP protocol, but the 404 NOT FOUND status code signifies that the specific piece of content requested was not found. This might happen if the content was moved or if you typed in the URL path incorrectly or if the page was removed.

### What is HTTPS?
Since your HTTP request can be read by anyone at certain network junctures, it might not be a good idea to deliver information such as your credit card or password using this protocol. Fortunately, many servers support HTTPS, short for HTTP Secure, which allows you to encrypt data that you send and receive.

HTTPS is important to use when passing sensitive or personal information to and from websites. However, it is up to the businesses maintaining the servers to set it up. In order to support HTTPS, the business must apply for a certificate from a Certificate Authority.


## Introduction to Web APIs

### What are APIs?
An *Application Programming Interface (API)* is a software tool that makes it easier for developers to interact with another application to use some of that application’s functionality.

### Types of APIs
There are two main categories of web APIs: browser APIs and 3rd party APIs.

*Browser APIs* are specific to writing code related to browsers and give developers access to information that the browser can also access. One example is the geolocation API which allows the program to know where a user is when accessing our app. This specific API requires that the user grant permissions to the browser to access their geolocation information. There are also browser APIs for audio, cryptography, VR, and much more.

*Third-party APIs* are apps that provide some type of functionality or information from a third-party, usually a company. For example, we could use the OpenWeather API to get in-depth information about the weather in an area, forecasts, historical weather data, and more! On our own, we wouldn’t even have access to this data and we would certainly not want to write up this code ourselves just for one app!

### Requesting Information from a Third-party API
Each API has a specific structure and protocol that we have to follow in order to gain access to its functionality.

#### Rules and Requirements
Organizations that maintain third-party APIs often set rules and requirements for how developers can interact with their APIs. For OpenWeather, we need to sign up for an account and generate a special token called an *API key* that grants our account the ability to make API requests. These API keys are unique to individual accounts and should be kept secret. OpenWeather provides some free functionality and some paid functionality. So before committing to a third-party API, check out their specifications which can often be found in the API documentation.

#### Making Requests
Some of an API’s specifications relate to making a *request* for data. These specifications could include more parameters for specific information or the inclusion of an API key. For example, when using the OpenWeather API, we need to provide more information to search for weather information — such information could include: the name of a city, time of day, the type of forecast, etc. These specifications for making a request can also be found in the API documentation.

#### Response Data
After we make a successful API request, the API sends back data. Many APIs format their data using *JavaScript Object Notation (JSON)* which looks like a JavaScript object.

```json
{ 
  "temperature" : { 
     "celcius" : 25,
  },
  "city": "chicago", 
}
```

It’s then up to us how to determine how to *consume*, or use, this information in our apps. If we got back that sample JSON above, we could parse out the temperature information and display it on our app.

### Review
- With web APIs, we have a tool that we can use to access the functionality and data of another application.
- There are two main types of APIs: browser and third-party.
	- Browser APIs require specific syntax and permissions.
	- Third-party APIs have their own rules and requirements set by the organizations that maintain them.
- When making a request to API, we might have to supply more details about what information we want.
- If we get a successful response, we still have to decide how to consume the response data.


## What is REST?

### REpresentational State Transfer
REST, or REpresentational State Transfer, is an architectural style for providing standards between computer systems on the web, making it easier for systems to communicate with each other. REST-compliant systems, often called RESTful systems, are characterized by how they are stateless and separate the concerns of client and server. 

### Separation of Client and Server
In the REST architectural style, the implementation of the client and the implementation of the server can be done independently without each knowing about the other. This means that the code on the client side can be changed at any time without affecting the operation of the server, and the code on the server side can be changed without affecting the operation of the client.

As long as each side knows what format of messages to send to the other, they can be kept modular and separate. Separating the user interface concerns from the data storage concerns, we improve the flexibility of the interface across platforms and improve scalability by simplifying the server components. Additionally, the separation allows each component the ability to evolve independently.

By using a REST interface, different clients hit the same REST endpoints, perform the same actions, and receive the same responses.

### Statelessness
Systems that follow the REST paradigm are stateless, meaning that the server does not need to know anything about what state the client is in and vice versa. In this way, both the server and the client can understand any message received, even without seeing previous messages. This constraint of statelessness is enforced through the use of *resources*, rather than *commands*. Resources are the nouns of the Web - they describe any object, document, or *thing* that you may need to store or send to other services.

Because REST systems interact through standard operations on resources, they do not rely on the implementation of interfaces.

These constraints help RESTful applications achieve reliability, quick performance, and scalability, as components that can be managed, updated, and reused without affecting the system as a whole, even during operation of the system.

### Communication between Client and Server
In the REST architecture, clients send requests to retrieve or modify resources, and servers send responses to these requests. 

#### Making Requests
REST requires that a client make a request to the server in order to retrieve or modify data on the server. A request generally consists of:

- an HTTP verb, which defines what kind of operation to perform
- a *header*, which allows the client to pass along information about the request
- a path to a resource
- an optional message body containing data

##### HTTP Verbs
There are 4 basic HTTP verbs we use in requests to interact with resources in a REST system:

- GET — retrieve a specific resource (by id) or a collection of resources
- POST — create a new resource
- PUT — update a specific resource (by id)
- DELETE — remove a specific resource by id

##### Headers and Accept parameters
In the header of the request, the client sends the type of content that it is able to receive from the server. This is called the `Accept` field, and it ensures that the server does not send data that cannot be understood or processed by the client. The options for types of content are MIME Types (or Multipurpose Internet Mail Extensions).

MIME Types, used to specify the content types in the `Accept` field, consist of a `type` and a `subtype`. They are separated by a slash (/).

For example, a text file containing HTML would be specified with the type `text/html`. If this text file contained CSS instead, it would be specified as `text/css`. A generic text file would be denoted as `text/plain`. This default value, `text/plain`, is not a catch-all, however. If a client is expecting `text/css` and receives `text/plain`, it will not be able to recognize the content.

Other types and commonly used subtypes:

- `image` — `image/png`, `image/jpeg`, `image/gif`
- `audio` — `audio/wav`, `audio/mpeg`
- `video` — `video/mp4`, `video/ogg`
- `application` — `application/json`, `application/pdf`, `application/xml`, `application/octet-stream`

For example, a client accessing a resource with `id` 23 in an `articles` resource on a server might send a GET request like this:
 
```
GET /articles/23
Accept: text/html, application/xhtml
```

##### Paths
Requests must contain a path to a resource that the operation should be performed on. In RESTful APIs, paths should be designed to help the client know what is going on.

Conventionally, the first part of the path should be the plural form of the resource. This keeps nested paths simple to read and easy to understand.

A path like fashionboutique.com/customers/223/orders/12 is clear in what it points to, even if you’ve never seen this specific path before, because it is hierarchical and descriptive. We can see that we are accessing the order with id 12 for the customer with id 223.

Paths should contain the information necessary to locate a resource with the degree of specificity needed. When referring to a list or collection of resources, it is not always necessary to add an id. For example, a POST request to the fashionboutique.com/customers path would not need an extra identifier, as the server will generate an id for the new object.

If we are trying to access a single resource, we would need to append an id to the path. For example: `GET fashionboutique.com/customers/:id` — retrieves the item in the customers resource with the id specified. `DELETE fashionboutique.com/customers/:id` — deletes the item in the customers resource with the id specified.

#### Sending Responses

##### Content Types
In cases where the server is sending a data payload to the client, the server must include a `content-type` in the header of the response. This `content-type` header field alerts the client to the type of data it is sending in the response body. These content types are MIME Types, just as they are in the `accept` field of the request header. The `content-type` that the server sends back in the response should be one of the options that the client specified in the `accept` field of the request.

For example, when a client is accessing a resource with id 23 in an articles resource with this GET Request:

```
GET /articles/23 HTTP/1.1
Accept: text/html, application/xhtml
```

The server might send back the content with the response header:

```
HTTP/1.1 200 (OK)
Content-Type: text/html
```

##### Response Codes
Responses from the server contain status codes to alert the client to information about the success of the operation. As a developer, you do not need to know every status code (there are many of them), but you should know the most common ones and how they are used:

Status code | Meaning
--- | ---
200 (OK)	| This is the standard response for successful HTTP requests.
201 (CREATED)	| This is the standard response for an HTTP request that resulted in an item being successfully created.
204 (NO CONTENT)	| This is the standard response for successful HTTP requests, where nothing is being returned in the response body.
400 (BAD REQUEST)	| The request cannot be processed because of bad request syntax, excessive size, or another client error.
403 (FORBIDDEN)	| The client does not have permission to access this resource.
404 (NOT FOUND)	| The resource could not be found at this time. It is possible it was deleted, or does not exist yet.
500 (INTERNAL SERVER ERROR)	| The generic answer for an unexpected failure if there is no more specific information available.

For each HTTP verb, there are expected status codes a server should return upon success:

- GET — return 200 (OK)
- POST — return 201 (CREATED)
- PUT — return 200 (OK)
- DELETE — return 204 (NO CONTENT) If the operation fails, return the most specific status code possible corresponding to the problem that was encountered.

#### Examples of Requests and Responses
Let’s say we have an application that allows you to view, create, edit, and delete customers and orders for a small clothing store hosted at fashionboutique.com. We could create an HTTP API that allows a client to perform these functions:

If we wanted to view all customers, the request would look like this:

```
GET http://fashionboutique.com/customers
Accept: application/json
```

A possible response header would look like:

```
Status Code: 200 (OK)
Content-type: application/json
```

followed by the `customers` data requested in `application/json` format.

Create a new customer by posting the data:

```
POST http://fashionboutique.com/customers
Body:
{
  “customer”: {
    “name” = “Scylla Buss”,
    “email” = “scylla.buss@codecademy.org”
  }
}
```

The server then generates an id for that object and returns it back to the client, with a header like:

```
201 (CREATED)
Content-type: application/json
```

To view a single customer we GET it by specifying that customer’s id:

```
GET http://fashionboutique.com/customers/123
Accept: application/json
```

A possible response header would look like:

```
Status Code: 200 (OK)
Content-type: application/json
```

followed by the data for the customer resource with id 23 in application/json format.

We can update that customer by PUT ting the new data:

```
PUT http://fashionboutique.com/customers/123
Body:
{
  “customer”: {
    “name” = “Scylla Buss”,
    “email” = “scyllabuss1@codecademy.com”
  }
}
```

A possible response header would have `Status Code: 200 (OK)`, to notify the client that the item with id 123 has been modified.

We can also DELETE that customer by specifying its id:

```
DELETE http://fashionboutique.com/customers/123
```

The response would have a header containing `Status Code: 204 (NO CONTENT)`, notifying the client that the item with id 123 has been deleted, and nothing in the body.


## What Is JSON?

### What is JSON?
JSON, or JavaScript Object Notation, is a popular, language-independent, standard format for storing and exchanging data. Adopted by ECMA International, an industry association founded in 1961 to standardize information and communication systems, JSON has become the de facto standard that facilitates storing and sending data between all programming languages.

### Common Uses of JSON
JSON is heavily used to facilitate data transfer in web applications between a client, such as a web browser, and a server. A typical example where such data transfer occurs is when you fill out a web form. The form data is converted from HTML to JavaScript objects to JSON objects and sent to a remote web server for processing.

When companies make their data public for other applications, like Spotify sharing its music library or Google sharing its map data, the information is formatted in JSON. This way, any application, regardless of language, can collect and parse the data.

### JSON Syntax
Since JSON is derived from the JavaScript programming language, its appearance is similar to that of JavaScript objects.

```json
{
  "student": {
    "name": "Rumaisa Mahoney",
    "age": 30,
    "fullTime": true,
    "languages": [ "JavaScript", "HTML", "CSS" ],
    "GPA": 3.9,
    "favoriteSubject": null
  }
}
```

Trailing commas are forbidden.

JSON property names must be in double-quoted (`" "`) text even though JavaScript names do not hold by this stringency.

### JSON Data Types
A JSON data type must be one of the following:

- string (double-quoted)
- number (integer or floating point)
- object (name-value pair)
- array (comma-delimited)
- boolean (true or false)
- null

Notably, JSON doesn’t cover every data type. Types that are not represented in JSON such as dates can be stored as a string and converted to a language-specific data structure. Here’s an acceptable internationally-recognized date format in ISO 8601:

```
"2014-01-01T23:28:56.782Z"
```

This above format contains parts which resemble a date and time. However, as a string, it is hard for a programming language to use as is. Conveniently, every programming language has built-in JSON facilities to convert this string into a more readable and usable format, such as:

```
Wed Jan 01 2014 13:28:56 GMT-1000 (Hawaiian Standard Time)
```


## Working with JSON in JavaScript

### JSON Object vs. JavaScript Object
Here is an example JSON object of a person named Kate, who is 30 years old, and whose hobbies include reading, writing, cooking, and playing tennis:

```json
{
  "person": {  
    "name": "Kate",  
    "age": 30,  
    "hobbies": [ "reading", "writing", "cooking", "tennis" ] 
  }
}
```

Represented as a JavaScript object literal, the same information would appear as:

```js
{  
  person: {
    name: 'Kate',  
    age: 30,  
    hobbies: [ 'reading', 'writing', 'cooking', 'tennis' ] 
  }
}
```

The name portion in each JSON name-value pair and all string values must be enclosed in double-quotes while this is optional in JavaScript.

JavaScript accepts string values that are single or double-quoted, however, there exists JavaScript coding guidelines that prefer one style over another.

### Reading a JSON String
In a typical web application, the JSON data that we receive from a web request comes in the form of a string. At other times, JSON data is stored in a file that is used for authentication, configuration, or database storage. These files typically have a .json extension, and they have to be opened in order to retrieve the JSON string in it. In either case, we will need to convert the string to a format that we can use in order to access its parts. Each programming language has its own mechanism to handle this conversion. In JavaScript, for example, we have a built-in JSON class with a method called `.parse()` that takes a JSON string as a parameter and returns a JavaScript object.

```js
const jsonData = '{ "book": { "name": "JSON Primer", "price": 29.99, "inStock": true, "rating": null } }';
 
const jsObject = JSON.parse(jsonData);
 
console.log(jsObject);
```

```
{
  book: { name: 'JSON Primer', price: 29.99, inStock: true, rating: null }
}
```

Once we have converted a JSON object to a JavaScript object, we can access the individual properties inside the JavaScript object. To access a value inside a JavaScript object based on its property name, we can either use dot notation, (`.propertyName`), or bracket notation, (`['propertyName']`).

```js
// Using the dot notation
const book = jsObject.book;    
console.log(book);
console.log(book.name, book.price, book.inStock);
 
// Using the bracket notation
const book2 = jsObject['book'];
console.log(book2);
console.log(book2["name"], book2["price"], book2["inStock"]);
```

As you can see, after parsing jsonData into a JavaScript object that’s stored in the variable, `book`, you can treat `book` like any other object! 

### Writing a JSON String
Before we can send off our data across the web, we need to convert them to a JSON string. In JavaScript, we would use the built-in JSON class method, `.stringify()` to transform our JavaScript object to a JSON string.

```js
const jsObject = { book: 'JSON Primer', price: 29.99, inStock: true, rating: null };
const jsonData = JSON.stringify(jsObject);
console.log(jsonData);
```

```
{ "book": "JSON Primer", "price": 29.99, "inStock": true, "rating": null }
```

 
# Learn JavaScript Syntax: Requests
## Requests with Fetch API

### Introduction to Requests with ES6
There are many types of HTTP requests. The four most commonly used types of HTTP requests are GET, POST, PUT, and DELETE. 

With a GET request, we’re retrieving, or *getting*, information from some source (usually a website). For a POST request, we’re *posting* information to a source that will process the information and send it back.

JavaScript uses an event loop to handle asynchronous function calls. When a program is run, function calls are made and added to a stack. The functions that make requests that need to wait for servers to respond then get sent to a separate queue. Once the stack has cleared, then the functions in the queue are executed.

To make asynchronous event handling easier, *promises* were introduced in ES6 JavaScript.

### Intro to GET Requests using Fetch
The `fetch()` function:

- Creates a request object that contains relevant information that an API needs.
- Sends that request object to the API endpoint provided.
- Returns a promise that ultimately resolves to a response object, which contains the status of the promise with information the API sent back.

```js
fetch('https://api-to-call.com/endpoint').then(response => { // sends request
	if(response.ok) {
		return response.json(); // converts response object to JSON
	}
	throw new Error('Request failed!'); // handles errors
}, networkError => console.log(networkError.message) // handles errors
).then(jsonResponse => { // handles success
	// code to execute with jsonResponse
});
```

First, call the `fetch()` function and pass it a URL as a string for the first argument, determining the endpoint of the request.

The `.then()` method is chained at the end of the `fetch()` function and in its first argument, the response of the GET request is passed to the callback arrow function. The `.then()` method will fire only after the promise status of `fetch()` has been resolved.

Inside the callback function, the `ok` property of the response object returns a Boolean value. If there are no errors, `response.ok` will be `true` and the code will return `response.json()`.

If `response.ok` is a falsy value, our code will `throw` an error.

A second argument passed to `.then()` will be another arrow function that will be triggered when the promise is rejected. It takes a single parameter, `networkError`. This object logs the `networkError` if we could not reach the endpoint at all (e.g., the server is down).

A second `.then()` method will run after the previous `.then()` method has finished running without error. It takes `jsonResponse`, which contains the returned `response.json()` object from the previous `.then()` method, as its parameter and can now be handled, however we may choose.

Note that if there is an error returned in the first `.then()` method, the second `.then()` method will not execute.

### Intro to POST Requests using Fetch

```js
fetch('http://api-to-call.com/endpoint', { // sends request
	method: 'POST',
	body: JSON.stringify({id: '200'})
}).then(response => {
	if(response.ok) {
		return response.json();
	}
	throw new Error('Request failed!');
}, networkError => console.log(networkError.message)
).then(jsonResponse => {
	// Code to execute with jsonResponse
});
```

Notice that the `fetch()` call takes two arguments: an endpoint and an object that contains information needed for the POST request.

The object passed to the `fetch()` function as its second argument contains two properties: `method`, with a value of `'POST'`, and `body`, with a value of `JSON.stringify({id: '200'});`. This second argument determines that this request is a POST request and what information will be sent to the API.

A successful POST request will return a response body, which will vary depending on how the API is set up.

The rest of the request is identical to the GET request. A `.then()` method is chained to the `fetch()` function to check and return the response as well as throw an exception when a network error is encountered. A second `.then()` method is added on so that we can use the response however we may choose.

### Intro to async GET Requests

```js
const getData = async () => {
	try {
		const response = await fetch('https://api-to-call.com/endpoint');
		if(response.ok) { // handles response if successful
			const jsonResponse = await response.json();
			// code to execute with jsonResponse
		}
		throw new Error('Request failed!'); // handles response if unsuccessful
	} catch(error) {
		console.log(error);
	}
}
```

The `async` keyword is used to declare an `async` function that returns a promise.

The `await` keyword can only be used within an `async` function. `await` suspends the program while waiting for a promise to resolve.

In a `try...catch` statement, code in the `try` block will be run and in the event of an exception, the code in the `catch` statement will run.
 
### Intro to async POST Requests
```js
const getData = async () => {
	try {
		const response = await fetch('https://api-to-call.com/endpoint', {
			method: 'POST',
			body: JSON.stringify({id: 200})
		});
		if(response.ok) {
			const jsonResponse = await response.json();
			// Code to execute with jsonResponse
		}
		throw new Error('Request failed!');
	} catch(error) {
		console.log(error);
	}
}
```

The `method` property value is set to `'POST'` to specify the type of request we are making. Then we have to include a `body` property with the value of `JSON.stringify({id: 200})`.

Query strings start out with a question mark, `?`, followed by the key/value pairs. The format looks like this:

```js
const queryString = `?key=value`;
```

### Review
- GET and POST requests can be created in a variety of ways.
- We can use `fetch()` and `async`/`await` to asynchronous request data from APIs.
- Promises are a type of JavaScript object that represents data that will eventually be returned from a request.
- The `fetch()` function can be used to create requests and will return promises.
- We can chain `.then()` methods to handle promises returned by the `fetch()` function.
- The `async` keyword is used to create asynchronous functions that will return promises.
- The `await` keyword can only be used with functions declared with the `async` keyword.
- The `await` keyword suspends the program while waiting for a promise to resolve.


# Cheatsheets

## Basics of Asynchronous JavaScript
![[basics_of_asynchronous_javascript.pdf]]

## Learn JavaScript Syntax: Promises
![[javascript_syntax_promises.pdf]]

## Learn JavaScript Syntax: Async-Await
![[javascript_syntax_async_await.pdf]]

## APIs and HTTP Requests
![[apis_and_http_requests.pdf]]

## Learn JavaScript Syntax: Requests
![[javascript_syntax_requests.pdf]]

