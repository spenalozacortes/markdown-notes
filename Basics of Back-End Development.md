# What is a Back-End?
## What is a Server?

### What are servers?
A *server* is a computer or program that provides services to other computers and programs, called clients, over a network. Servers are part of client-server architecture in which a client requests something and the server responds to the request. A well-known example of a server is a web server, where the client (web browser) requests a page and the server provides the page to the browser.

### What is a client?
A client is a machine or program that depends on a server for some resource or service. The client will send a request to the server for the resource or service. Different physical locations make no difference to the client and server since they are connected through a mutual network such as the Internet.

### How do servers work?
The roles of a server include:

- Sharing data between one or more client machines.
- Share resources, such as services or programs, between client machines.
- Distribute work to several connected machines.

Servers work in a request-response manner. In a web server, for example, users on the Web request a specific web page by entering a URL in the web browser. If the URL is valid, the server will, in turn, give a response to the user by sending the requested page. Thus, the browser forms a connection to a server, requests a page, and receives it.

### How servers connect to the Internet
Clients use a URL to connect to a server across the Internet. The URL has four main components:

- A connection scheme, usually HTTPS (“Hypertext Transfer Protocol Secure”), browsers and web servers use to talk with one another.
- A subdomain that specifies the particular server (usually organized by resource type) to be delivered to the client.
- A domain name that specifies the name of the organization(s) associated with the URL.
- A top-level domain that specifies the type of organization associated with the URL.

For the URL https://www.codecademy.com, “https” is the scheme, “www” is the subdomain, “codecademy” is the domain name, and “com” is the top-level domain.

1. The browser first communicates with the internet service provider (ISP).
2. This further communicates with the domain name server to get the IP address of the server.
3. The domain name server converts a domain name to an IP address.
4. Using this IP address, the browser connects to the server.
5. Once connected to the web server, our browser sends the request to the server and asks for particular files.
6. When the browser has connected to the server at the correct IP address, the servers send all the requested HTML text for the web page to our browser.

### Examples of server operating systems
The operating system (OS) used in a given server is completely dependent on the server’s requirements. The commonly used server operating systems are:

- Windows: This server operating system is provided by the Microsoft Corporation. It allows users to store files and play videos and music. It also supports multitasking, graphical user interface, and virtual memory management.
- UNIX: It is one of the most popular operating systems for client-server environments. It is a multi-user operating system. This operating system is widely used by websites to provide services on the internet.
- Linux: This operating system is open-source, multi-user, multi-process, and gives a good real-time performance. It offers low cost for delivering services to the clients. This operating system is often chosen over others for servers because of its security services.

### Types of servers
There are different types of servers based on their uses. Some of the most common types of servers are as follows:

- A file server is used to store data files for multiple users. They provide users access to stored files and data and can allow faster retrieval and saving of data. These are used on private networks and provide a location for storage of computer files. It provides a central location to store files where multiple users can work with the same documents.
- A database server allows another computer to access the database and retrieve or upload data. This type of server typically has a large storage capacity.
- A web server delivers web pages requested by multiple client web browsers.
- Mail servers store and deliver email for clients through an email service platform. They are a form of digital ‘post office’ that sorts and stores emails.
- An application server provides a software environment with all the needed requirements. This server allows users to access the application without needing to download additional software.
- The proxy server communicates with the websites you are visiting on your behalf. It links the user with the rest of the internet. The browser connects to the proxy server, and the proxy server sends your request to the website and sends the website’s response back to you.


# Back-End JavaScript with Node.js
## Introduction to Node.js

### Introduction
For a long time, the browser was the only place JavaScript code could be executed. Web developers had to use a different programming language on the front-end than the back-end. It also meant that, even as JavaScript evolved into a more robust and powerful language, it remained a front-end only language.

Though multiple attempts to create off-browser JavaScript environments have been attempted, Node.js, invented by Ryan Dahl in 2009, found unprecedented popularity and is currently being used by numerous top-tier companies. Node.js is a JavaScript *runtime*, or an environment that allows us to execute JavaScript code outside of the browser. A “runtime” converts code written in a *high-level*, human-readable, programming language and compiles it down to code the computer can execute.

Though Node was created with the goal of building web servers and web applications in JavaScript, it can also be used for creating command-line applications or desktop applications.

For more advanced development, Node can be combined with any number of robust frameworks like the Express.js framework for creating effective web application back-ends.

Let’s see what version of Node we have installed.

```shell
node -v
```

### The Node REPL
REPL is an abbreviation for read–eval–print loop. It’s a program that loops, or repeatedly cycles, through three different states: a read state where the program reads input from a user, the eval state where the program evaluates the user’s input, and the print state where the program prints out its evaluation to a console. Then it loops through these states again.

When you install Node, it comes with a built-in JavaScript REPL. You can access the REPL by typing the command `node` (with nothing after it) into the terminal and hitting enter. A `>` character will show up in the terminal, indicating the REPL is running and prompting your input. The Node REPL will evaluate your input line by line.

By default, you indicate the input is ready for eval when you hit enter. If you’d like to type multiple lines and then have them evaluated at once, you can type `.editor` while in the REPL. Once in “editor” mode, you can type control + d when you’re ready for the input to be evaluated. Each session of the REPL has a single shared memory; you can access any variables or functions you define until you exit the REPL.

The Node environment contains a number of Node-specific global elements in addition to those built into the JavaScript language. Every Node-specific global property sits inside the Node `global` object. This object contains a number of useful properties and methods that are available anywhere in the Node environment.

The `Window` object is the JavaScript object in the browser that holds the DOM, since we don’t have a DOM here, there’s no `Window` object.

### Running a Program with Node
We’ll need to create a file with a `.js` extension.

```js
// Inside myProgram.js
console.log('Hello World');
```

We’ll open our terminal and navigate to the directory that contains **myProgram.js**. 

```shell
node myProgram.js
```

The results of our program will print to the terminal.

### Core Modules
*Modularity* is a software design technique where one program has distinct parts, each providing a single piece of the overall functionality. These separate modules come together to build a cohesive whole. Modularity is essential for creating scalable programs which incorporate libraries and frameworks and separate the program’s concerns into manageable chunks. Essentially, a module is a collection of code located in a file. Instead of having an entire program located in a single file, code is organized into separate files based on the concerns they address. These files can then be included in other files by using the `require()` function.

To save developers from reinventing the wheel each time, Node.js has several built-in modules to perform common tasks efficiently. These are known as the *core modules*. The core modules are defined within Node.js’s source code and are located in the **lib/** folder. Core modules can be required by passing a string with the name of the module into the `require()` function:

```js
// Require in the 'events' core module:
const events = require('events');
```

Some core modules are actually used inside other core modules. For instance, the `util` module can be used in the `console` module to format messages.

Once in the REPL, a complete list of core modules can be accessed by typing the command:

```shell
require('module').builtinModules
```

### The Console Module
The `console` object provides many of the same familiar methods such as:

- `.log()` — to print messages to the terminal.
- `.assert()` — to print a message to the terminal if the value is falsy.
- `.table()` — to print out a table in the terminal from an object or array.

Since `console` is a global module, its methods can be accessed from anywhere, and the `require()` function is not necessary.

### The Process Module
In computer science, a *process* is the instance of a computer program that is being executed. Node has a global `process` object with useful methods and information about the current process.

The `process.env` property is an object which stores and controls information about the environment in which the process is currently running. For example, the `process.env` object contains a `PWD` property which holds a string with the directory in which the current process is located. It can be useful to have some `if/else` logic in a program depending on the current environment— a web application in a development phase might perform different tasks than when it’s live to users. We could store this information on the `process.env`. One convention is to add a property to `process.env` with the key `NODE_ENV` and a value of either `production` or `development`.

```js
if (process.env.NODE_ENV === 'development'){
  console.log('Testing! Testing! Does everything work?');
}
```

The `process.memoryUsage()` returns information on the CPU demands of the current process. It returns a property that looks similar to this:

```js
{ rss: 26247168,
  heapTotal: 5767168,
  heapUsed: 3573032,
  external: 8772 }
  ```

*Heap* can mean different things in different contexts: a heap can refer to a specific data structure, but it can also refer to a block of computer memory. The `process.memoryUsage().heapUsed` method will return a number representing how many bytes of memory the current process is using.

The `process.argv` property holds an array of command line values provided when the current process was initiated. The first element in the array is the absolute path to Node, which ran the process. The second element in the array is the path to the file that’s running. The following elements will be any command line arguments provided when the process was initiated. Command line arguments are separated from one another with spaces.

```shell
node myProgram.js testing several features
```

```js
console.log(process.argv[3]); // Prints 'several'
```

### The OS Module
When developing or debugging an app, it can be helpful to have information about the computer, operating system, and network on which the program is running. Before Node, this information could not be retrieved using JavaScript due to the language being confined to the browser. However, Node.js is a JavaScript runtime, which means it can execute code outside of the browser, and we’re able to get access to much of this information through the `os` core module.

Unlike `process` and `console`, the `os` module is not global and needs to be included into the file in order to gain access to its methods.

```js
const os = require('os');
```

With the `os` module saved to the `os` variable, you can call methods like:

- `os.type()` — to return the computer’s operating system.
- `os.arch()` — to return the operating system CPU architecture.
- `os.networkInterfaces()` — to return information about the network interfaces of the computer, such as IP and MAC address.
- `os.homedir()` — to return the current user’s home directory.
- `os.hostname()` — to return the hostname of the operating system.
- `os.uptime()` — to return the system uptime, in seconds.

```js
const os = require('os');
 
const local = {  
  'Home Directory': os.homedir(),    
  'Operating System': os.type(),
  'Last Reboot': os.uptime()
}
```

### The Util Module
Developers sometimes classify outlier functions used to maintain code and debug certain aspects of a program’s functionality as *utility functions*. Utility functions don’t necessarily create new functionality in a program, but you can think of them as internal tools used to maintain and debug your code. The Node.js `util` core module contains methods specifically designed for these purposes. The `util` module can be required into the file using:

```js
const util = require('util');
```

One important object is `types`, which provides methods for runtime type checking in Node.

```js
const util = require('util');
 
const today = new Date();
const earthDay = 'April 22, 2022';
 
console.log(util.types.isDate(today));
console.log(util.types.isDate(earthDay));
```

The `types.isDate()` method checks for `Date` objects and returns a boolean value.

Another important util method is `.promisify()`, which turns callback functions into promises. As you know, asynchronous programming is essential to Node.js. In the beginning, this asynchrony was achieved using error-first callback functions, which are still very prevalent in the Node ecosystem today. But since promises are often preferred over callbacks and especially nested callbacks, Node offers a way to turn these into promises. 

```js
function getUser (id, callback) {
  return setTimeout(() => {
    if (id === 5) {
      callback(null, { nickname: 'Teddy' })
    } else {
      callback(new Error('User not found'))
    }
  }, 1000)
}
 
function callback (error, user) {
  if (error) {
    console.error(error.message)
    process.exit(1)
  }
 
  console.log(`User found! Their nickname is: ${user.nickname}`)
}
 
getUser(1, callback) // -> `User not found`
getUser(5, callback) // -> `User found! Their nickname is: Teddy`
```

Here we have a function that queries a database for a specified user ID. `getUser` methods are very common in back-end applications, and most will also support error-first callbacks. Since a database query typically takes longer to run than other operations, we simulate the query with a `setTimeout()` method that executes a callback function after 1000 milliseconds (or 1 second). If the user with the specified ID is found, the callback function is executed with `null` passed in as the argument for the `error` parameter, and an object containing the returned user information is passed in as an argument for the `user` parameter. If the user is not found, the callback function is executed, passing in a new `Error` as the argument for the `error` parameter. A second argument for `user` is not necessary since the function will end in the case of an error.

With `.promisify()`, we can easily change it into a modern, cleaner, and more maintainable version of itself:

```js
const getUserPromise = util.promisify(getUser);
 
getUserPromise(id)
  .then((user) => {
      console.log(`User found! Their nickname is: ${user.nickname}`);
  })
  .catch((error) => {
      console.log('User not found', error);
  });
 
getUser(1) // -> `User not found`
getUser(5) // -> `User found! Their nickname is: Teddy`
```

We declare a `getUserPromise` variable that stores the `getUser` method turned into a promise using the `.promisify()` method. With that in place, we’re able to use `getUserPromise` with `.then()` and `.catch()` methods (or we could also use the `async...await` syntax here) to resolve the promise returned or catch any errors.

### Review
- Node.js is a JavaScript *runtime*, an environment that allows us to execute our JavaScript code by converting it into something a computer can understand.
- REPLs are processes that read, evaluate, print, and repeat (loop), and Node.js comes with its own REPL we can access in our terminal with the `node` command.
- We run JavaScript programs with Node in the terminal by typing `node` followed by the file name (if we’re in the same directory) or the absolute path of the file.
- Code can be organized into separate files, modules, and combined through *requiring* them where needed using the `require()` function.
- Core modules are built into the Node.js environment to efficiently perform common tasks.
- The `console` module exports a global `console` object allowing the terminal to act as a debugging console, similar to the JavaScript `console` object provided by web browsers.
- The `process` module is a global module that gives access to information about the Node.js runtime environment.
- The `os` module provides methods to retrieve information about the computer, operating system, and network interfaces.
- The `util` module contains methods used to maintain and debug your code.


## Node.js Essentials

### The Events Module
Node is often described as having event-driven architecture. 

In traditional imperative programming, we give the computer a series of instructions to execute in a pre-defined order. In contrast, when we write web applications, we often need to write logic to handle situations without knowing exactly when they’ll occur. For example, when programming a website, we might provide functionality for a click event without knowing when a user will trigger it. When Node was created, it applied this same concept of event-driven principles to the back-end environment.

Node provides an `EventEmitter` class which we can access by requiring in the `events` core module:

```js
// Require in the 'events' core module
let events = require('events');
 
// Create an instance of the EventEmitter class
let myEmitter = new events.EventEmitter();
```

Each event emitter instance has an `.on()` method which assigns a *listener* callback function to a named event. The `.on()` method takes as its first argument the name of the event as a string and, as its second argument, the listener callback function.

Each event emitter instance also has an `.emit()` method which announces a named event has occurred. The `.emit()` method takes as its first argument the name of the event as a string and, as its second argument, the data that should be passed into the listener callback function.

```js
let newUserListener = (data) => {
  console.log(`We have a new user: ${data}.`);
};
 
// Assign the newUserListener function as the listener callback for 'new user' events
myEmitter.on('new user', newUserListener)
 
// Emit a 'new user' event
myEmitter.emit('new user', 'Lily Pad') //newUserListener will be invoked with 'Lily Pad'
```

### User Input/Output
At its most abstract, output is any data or feedback that a computer provides (like to a human user), while input is data provided to the computer.

In Node, we can also receive input from a user through the terminal using the `stdin.on()` method on the process object:

```js
process.stdin.on('data', (userInput) => {
  let input = userInput.toString()
  console.log(input)
});
```

Here, we were able to use `.on()` because under the hood `process.stdin` is an instance of `EventEmitter`. When a user enters text into the terminal and hits enter, a `'data'` event will be fired and our anonymous listener callback will be invoked. The `userInput` we receive is an instance of the Node `Buffer` class, so we convert it to a string before printing.

Input read through the terminal is received as a `Buffer` object with a new line character at the end.

### The Error Module
The Node environment’s error module has all the standard JavaScript errors such as `EvalError`, `SyntaxError`, `RangeError`, `ReferenceError`, `TypeError`, and `URIError` as well as the JavaScript `Error` class for creating new error instances. Within our own code, we can generate errors and `throw` them, and, with synchronous code in Node, we can use error handling techniques such as `try...catch` statements. Note that the `error` module is within the global scope—there is no need to import the module with the `require()` statement.

Many asynchronous Node APIs use *error-first callback functions*—callback functions which have an error as the first expected argument and the data as the second argument. If the asynchronous task results in an error, it will be passed in as the first argument to the callback function. If no error was thrown, the first argument will be `undefined`.

```js
const errorFirstCallback = (err, data)  => {
  if (err) {
    console.log(`There WAS an error: ${err}`);
  } else {
    // err was falsy
    console.log(`There was NO error. Event data: ${data}`);
  }
}
```

Traditional `try...catch` statements won’t work for errors thrown during asynchronous operations.

### The Buffer Module
In Node.js, the `Buffer` module is used to handle binary data. The `Buffer` module is within the global scope, which means that `Buffer` objects can be accessed anywhere in the environment without importing the module with `require()`.

A `Buffer` object represents a fixed amount of memory that can’t be resized. `Buffer` objects are similar to an array of integers where each element in the array represents a byte of data. The buffer object will have a range of integers from 0 to 255 inclusive.

The `Buffer` module provides a variety of methods to handle the binary data such as `.alloc()`, `.toString()`, `.from()`, and `.concat()`.

The `.alloc()` method creates a new `Buffer` object with the size specified as the first parameter. `.alloc()` accepts three arguments:

- Size: Required. The size of the buffer
- Fill: Optional. A value to fill the buffer with. Default is 0.
- Encoding: Optional. Default is UTF-8.

```js
const buffer = Buffer.alloc(5);
console.log(buffer); // Ouput: [0, 0, 0, 0, 0]
```

The `.toString()` method translates the `Buffer` object into a human-readable string. It accepts three optional arguments:

- Encoding: Default is UTF-8.
- Start: The byte offset to begin translating in the `Buffer` object. Default is 0.
- End: The byte offset to end translating in the `Buffer` object. Default is the length of the buffer. The start and end of the buffer are similar to the start and end of an array, where the first element is 0 and increments upwards.

```js
const buffer = Buffer.alloc(5, 'a');
console.log(buffer.toString()); // Output: aaaaa
```

The `.from()` method is provided to create a new `Buffer` object from the specified string, array, or buffer. The method accepts two arguments:

- Object: Required. An object to fill the buffer with.
- Encoding: Optional. Default is UTF-8.

```js
const buffer = Buffer.from('hello');
console.log(buffer); // Output: [104, 101, 108, 108, 111]
```

The `.concat()` method joins all buffer objects passed in an array into one `Buffer` object. `.concat()` comes in handy because a `Buffer` object can’t be resized. This method accepts two arguments:

- Array: Required. An array containing `Buffer` objects.
- Length: Optional. Specifies the length of the concatenated buffer.

```js
const buffer1 = Buffer.from('hello'); // Output: [104, 101, 108, 108, 111]
const buffer2 = Buffer.from('world'); // Output:[119, 111, 114, 108, 100]
const array = [buffer1, buffer2];
const bufferConcat = Buffer.concat(array);
 
console.log(bufferConcat); // Output: [104, 101, 108, 108, 111, 119, 111, 114, 108, 100]
```

### The FS Module
All of the data on a computer is organized and accessed through a *filesystem*. When running JavaScript code on a browser, it’s important for a script to have only limited access to a user’s filesystem. This technique of isolating some applications from others is known as *sandboxing*. Sandboxing protects users from malicious programs and invasions of privacy.

In the back-end, however, less restricted interaction with the filesystem is essential. The Node `fs` core module is an API for interacting with the file system. It was modeled after the POSIX standard for interacting with the filesystem.

Each method available through the `fs` module has a synchronous version and an asynchronous version. One method available on the `fs` core module is the `.readFile()` method which reads data from a provided file:

```js
const fs = require('fs');
 
let readDataCallback = (err, data) => {
  if (err) {
    console.log(`Something went wrong: ${err}`);
  } else {
    console.log(`Provided file contained: ${data}`);
  }
};
 
fs.readFile('./file.txt', 'utf-8', readDataCallback);
```

We invoked the `.readFile()` method with three arguments:

- The first argument is a string that contains a path to the file **file.txt**.
- The second argument is a string specifying the file’s character encoding (usually ‘utf-8’ for text files).
- The third argument is the callback function to be invoked when the asynchronous task of reading from the file system is complete. Node will pass the contents of **file.txt** into the provided callback as its second argument.

### Readable Streams
In more realistic scenarios, data isn’t processed all at once but rather sequentially, piece by piece, in what is known as a *stream*. Streaming data is often preferable since you don’t need enough RAM to process all the data at once nor do you need to have all the data on hand to begin processing it.

One of the simplest uses of streams is reading and writing to files line-by-line. To read files line-by-line, we can use the `.createInterface()` method from the `readline` core module. `.createInterface()` returns an `EventEmitter` set up to emit 'line' events:

```js
const readline = require('readline');
const fs = require('fs');
 
const myInterface = readline.createInterface({
  input: fs.createReadStream('text.txt')
});
 
myInterface.on('line', (fileLine) => {
  console.log(`The line read: ${fileLine}`);
});
```

`fs.createReadStream()` expects the file (as a string) from which it should read.

A 'line' event will be emitted after each line from the file is read.

### Writeable Streams
We can create a writeable stream to a file using the `fs.createWriteStream()` method:

```js
const fs = require('fs')
 
const fileStream = fs.createWriteStream('output.txt');
 
fileStream.write('This is the first line!'); 
fileStream.write('This is the second line!');
fileStream.end();
```

Unlike a readable stream, which ends when it has no more data to read, a writable stream could remain open indefinitely. We can indicate the end of a writable stream with the `.end()` method.

### The Timers Module
There are times when we want some of our code to be executed at a specified point in time. This is what the `timers` module is used for. Like the `Buffer` module, it is not necessary to use the `require()` import statement as the methods of the timer module are global.

Timer functions in Node.js behave similarly to how they work in front-end JavaScript programs, but the difference is that they are added to the Node.js event loop. This means that the timer functions are scheduled and put into a queue. This queue is processed at every iteration of the event loop. If a timer function is executed outside of a module, the behavior will be random (non-deterministic).

The `setImmediate()` function is often compared with the `setTimeout()` function. When `setImmediate()` is called, it executes the specified callback function after the current (poll phase) is completed. The method accepts two parameters: the callback function (required) and arguments for the callback function (optional). If you instantiate multiple `setImmediate()` functions, they will be queued for execution in the order that they were created.

```js
setImmediate(() => {
    console.log('Hello! My name is Codey.')
});
```

### Review
- Blocking code runs synchronously and non-blocking code, such as timer functions, runs asynchronously.
- Core modules are provided to developers to perform common tasks efficiently. Core modules are used by passing a string with the module’s name into the `require()` statement.
- We can make our own instances of the `EventEmitter` class, and we can subscribe to listen for named events with the `.on()` method and emit events with the `.emit()` method.
- Node allows for both *output*, data/feedback to a user-provided by a computer, and *input* data/feedback to the computer provided by the user. To handle errors during asynchronous operations, provided callback functions are expected to have an error as their first parameter.
- The `buffer` module provides global `Buffer` objects used to represent a fixed amount of memory that can’t be resized.
- The `timer` module provides functions that allow developers to execute callbacks at a specified point of time in the future.
- The Node `fs` core module is an API for interacting with the file system.
- *Streams* allow us to read or write data piece by piece instead of all at once.


# Modular Development with Node.js
## Implementing Modules in Node

### Implementing Modules in Node
Every JavaScript file that runs in a Node environment is treated as a distinct module. The functions and data defined within each module can be used by any other module, as long as those resources are properly *exported* and *imported*.

Suppose you wanted to write a simple program that would display the freezing point and boiling point of water in Fahrenheit. However, you only know the values in Celsius to be 0 (freezing) and 100 (boiling). Luckily you happen to know how to convert Celsius to Fahrenheit!

```js
/* water-limits.js */
function celsiusToFahrenheit(celsius) {
  return celsius * (9/5) + 32;
}
 
const freezingPointC = 0;
const boilingPointC = 100;
 
const freezingPointF = celsiusToFahrenheit(freezingPointC);
const boilingPointF = celsiusToFahrenheit(boilingPointC);
 
console.log(`The freezing point of water in Fahrenheit is ${freezingPointF}`);
console.log(`The boiling point of water in Fahrenheit is ${boilingPointF}`);
```

Now, you decide to write a second program. In this program, the user can input any temperature value in Celsius and the program responds by printing the input temperature converted to Fahrenheit.

```js
/* celsius-to-fahrenheit.js */
function celsiusToFahrenheit(celsius) {
    return celsius * (9/5) + 32;
}
 
const celsiusInput = process.argv[2]; // Get the 3rd input from the argument list
const fahrenheitValue = celsiusToFahrenheit(celsiusInput);
 
console.log(`${celsiusInput} degrees Celsius = ${fahrenheitValue} degrees Fahrenheit`);
```

Creating a module that exports a `celsiusToFahrenheit()` function that can be used by both of these programs would solve this repetitive code problem.

### module.exports
To create a module, you simply have to create a new file where the functions can be declared. Then, to make these functions available to other files, add them as properties to the built-in `module.exports` object:

```js
/* converters.js */
function celsiusToFahrenheit(celsius) {
  return celsius * (9/5) + 32;
}
 
module.exports.celsiusToFahrenheit = celsiusToFahrenheit;
 
module.exports.fahrenheitToCelsius = function(fahrenheit) {
  return (fahrenheit - 32) * (5/9);
};
```

`module.exports` is an object that is built-in to the Node.js runtime environment. Other files can now import this object, and make use of these two functions, with another feature that is built-in to the Node.js runtime environment: the `require()` function.

### require()
The `require()` function accepts a string as an argument. That string provides the file path to the module you would like to import.

```js
/* water-limits.js */
const converters = require('./converters.js');
 
const freezingPointC = 0;
const boilingPointC = 100;
 
const freezingPointF = converters.celsiusToFahrenheit(freezingPointC);
const boilingPointF = converters.celsiusToFahrenheit(boilingPointC);
 
console.log(`The freezing point of water in Fahrenheit is ${freezingPointF}`);
console.log(`The boiling point of water in Fahrenheit is ${boilingPointF}`);
```

When you use `require()`, the entire module.exports object is returned and stored in the variable `converters`. This means that both the `.celsiusToFahrenheit()` and `.fahrenheitToCelsius()` methods can be used in this program!

### Using Object Destructuring to be more Selective With require()
In many cases, modules will export a large number of functions but only one or two of them are needed. You can use object destructuring to extract only the needed functions.

```js
/* celsius-to-fahrenheit.js */
const { celsiusToFahrenheit } = require('./converters.js');
 
const celsiusInput = process.argv[2]; 
const fahrenheitValue = celsiusToFahrenheit(celsiusInput);
 
console.log(`${celsiusInput} degrees Celsius = ${fahrenheitValue} degrees Fahrenheit`);
```


## Node Package Manager

### Dependencies: A Sea of Shared Modules
In addition to core Node.js modules, developers can also take advantage of modules created by other developers, many of which are shared freely. These third-party modules often solve common problems and simplify the development process. When we use these modules in our code, they are referred to as *dependencies*.

### Package Management
Most of the time, these dependencies are installed in *packages* handled by a *package manager*. A package is simply a third-party module wrapped up with the list of that module’s own dependencies.

A package manager:

- downloads and installs the packages to be used as dependencies on a project.
- checks the packages to make sure they don’t have any known vulnerabilities.
- checks if packages can be updated to a newer version.
- handles all of the packages’ sub-dependencies.
- cleanly removes all the files of a package when it’s no longer needed.
- provides a repeatable and consistent process of installing dependencies for you and your teammates

The most popular package manager is Node Package Manager which is the default package manager for Node.js. Its command-line tool, `npm`, is even included in the Node.js installation process. This tool enables developers to download and manage packages via the terminal.

```shell
npm -v
```

### Initialization
To initialize a Node.js app, we open up a terminal and enter the command:

```bash
npm init
```

This will result in a series of prompts asking us for information about our project, including our project’s name, version number, description and much more. Once the prompts have been completed, a package.json file will be generated with the information listed in JSON format!

If you’re looking to get initialized quickly, you can add the flag `-y` to the end of the initialization command to skip the prompts.

```bash
npm init -y
```

Importantly, as you install new dependencies using npm, this file will be automatically updated so as to maintain the most up-to-date picture of the packages used in the application.

### Installing
A popular Node.js package is `nodemon`, a tool used to automatically restart a program when a file changes, alleviating the need to do so manually each time you save a file. 

```bash
npm i nodemon
```

`i` is actually an alias for `install`, and either `npm i` or `npm install` can be used when installing a package. 

The `npm i <package name>` command installs a package locally in a folder called **node_modules/** which is created in the project directory that you ran the command from. In addition, the newly installed package will be added to the **package.json** file.

### Package Scopes
Generally, most npm packages should be installed locally—this way, among other reasons, each project can control which specific versions of its dependencies it uses. That being said, there are a few other ways you might install packages.

#### devDependencies
While most dependencies play a direct role in the functionality of your application, *development dependencies* are used for the purpose of making development easier or more efficient.

In fact, the `nodemon` package is actually better suited as a development dependency since it makes developers’ lives easier but makes no changes to the app itself. To install nodemon as a development dependency, we can add the `--save-dev` flag, or its alias, `-D`.

```bash
npm install nodemon --save-dev
```

Development dependencies are listed in the "devDependencies" field of the **package.json** file. This indicates that the package is being used specifically for development and will not be included in a production release of the project.

Like local packages, development dependencies are also stored in the local **node_modules/** folder.

#### Global Packages
Some packages can be installed *globally* meaning they are available system-wide, without the need to install it each time you create a new application. Typically, packages installed this way will be used in the command-line rather than imported into a project’s code. One such example is the `http-server` package which allows you to spin up a zero-configuration server from anywhere in the command-line.

To install a package globally, use the `-g` flag with the installation command:

```bash
npm install http-server -g
```

Unlike local package dependencies or development dependencies, packages installed globally will not be listed in a projects **package.json** file and they will be stored in a separate global **node_modules/** folder.

#### npm install
You may have noticed that, as we install third-party packages from npm, we are creating a **package.json** file for our own project. Doing so turns our own project into a package, just one that isn’t published in the npm registry (yet).

While you may never end up publishing your project as a public package, having this **package.json** file enables you to easily collaborate with other developers. Anyone who wishes to work with you on your project can simply download your **package.json** and run the command:

```bash
npm i
```

Running this command will automatically install all packages listed as dependencies or development dependencies. If you wish to leave out development dependencies, you can run the command with the `--production` flag.

```bash
npm i --production
```

Because of this convenient command, it is recommended that you do not include your local **node_modules/** folder in any repository that you use to store and share your code to avoid taking up precious storage resources.


# Getting User Input in Node.js

## Synchronous Input
Node.js allows you to run JavaScript code outside of a browser window, offering powerful tools to interact with a computer filesystem, run web servers, and create terminal applications. Node handles these tasks by running asynchronously, which means that reading user input from a terminal isn’t as simple as calling a `getInput()` function. 

## Working with Input
Node.js provides a few ways to handle interactions, including the built-in process object and readline module. While these are powerful tools, they rely on callback functions.

```js
const readline = require('readline').createInterface({
  input: process.stdin,
  output: process.stdout
});

readline.question('Who are you?', name => {
  console.log(`Hey there ${name}!`);
  readline.close();
});
```

## Using prompt-sync
The prompt-sync Node module provides an easy-to-use alternative to this callback-based syntax.

```bash
npm install prompt-sync
```

```js
const prompt = require('prompt-sync')();
```

Notice the extra `()` after `require()`. The `prompt-sync` module is a function that creates prompting functions, so you need to call `prompt-sync` in order to get your actual prompting function.

```js
const prompt = require('prompt-sync')();

const name = prompt('What is your name?');
console.log(`Hey there ${name}`);
```

The `prompt()` function returns the user feedback, so simply store that return value to a variable to use it later. 

### Letting Users Exit
By default, most terminal programs will exit with Ctrl + C (This sends a SIGINT, or “signal interrupt” message indicating that a user wants to exit a program). With `prompt-sync`, in order to make sure that your users can exit at will, add a configuration object with `sigint: true` when invoking the `prompt-sync` function:

```js
const prompt = require('prompt-sync')({sigint: true});
```

### Working with Numbers
All user input will be read as a String, so in order to treat user input as numbers, you’ll need to convert the input:

```js
const num = prompt('Enter a number: ');
console.log('Your number + 4 =');
console.log(Number(num) + 4);
```


# Cheatsheets

## Back-End JavaScript with Node.js
![[backend_javascript_with_nodejs.pdf]]