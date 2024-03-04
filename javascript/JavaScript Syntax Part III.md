# Learn JavaScript Syntax: Classes
## Classes

### Introduction to Classes
JavaScript is an *object-oriented programming* (OOP) language we can use to model real-world items. Classes are a tool that developers use to quickly produce similar objects.

Classes are a great way to reduce duplicate code and debugging time.

### Constructor
Although you may see similarities between class and object syntax, there is one important method that sets them apart. It’s called the *constructor* method. JavaScript calls the `constructor()` method every time it creates a new *instance* of a class.

```js
class Dog {
  constructor(name) {
    this.name = name;
    this.behavior = 0;
  }
}
```

By convention, we capitalize and CamelCase class names.

In the context of a class, `this` refers to an instance of that class.

### Instance
An *instance* is an object that contains the property names and methods of a class, but with unique property values.

```js
class Dog {
  constructor(name) {
    this.name = name;
    this.behavior = 0;
  } 
}
 
const halley = new Dog('Halley'); // Create new Dog instance
console.log(halley.name); // Log the name value saved to halley
// Output: 'Halley'
```

The `new` keyword calls the `constructor()`, runs the code inside of it, and then returns the new instance.

### Methods
Class method and getter syntax is the same as it is for objects **except you can not include commas between methods**.

```js
class Dog {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }
 
  get name() {
    return this._name;
  }
 
  get behavior() {
    return this._behavior;
  }
 
  incrementBehavior() {
    this._behavior++;
  }
}
```

### Method Calls
```js
class Dog {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }
 
  get name() {
    return this._name;
  }
 
  get behavior() {
    return this._behavior;
  }   
 
  incrementBehavior() {
    this._behavior++;
  }
}
 
const halley = new Dog('Halley');
```

The syntax for calling methods and getters on an instance is the same as calling them on an object — append the instance with a period, then the property or method name. For methods, you must also include opening and closing parentheses.

```js
let nikko = new Dog('Nikko'); // Create dog named Nikko
nikko.incrementBehavior(); // Add 1 to nikko instance's behavior
let bradford = new Dog('Bradford'); // Create dog name Bradford
console.log(nikko.behavior); // Logs 1 to the console
console.log(bradford.behavior); // Logs 0 to the console
```

### Inheritance I
Imagine our doggy daycare is so successful that we decide to expand the business and open a kitty daycare. Before the daycare opens, we need to create a `Cat` class so we can quickly generate `Cat` instances. We know that the properties in our `Cat` class (`name`, `behavior`) are similar to the properties in our `Dog` class, though, there will be some differences, because of course, cats are not dogs.

Let’s say that our `Cat` class looks like this:

```js
class Cat {
  constructor(name, usesLitter) {
    this._name = name;
    this._usesLitter = usesLitter;
    this._behavior = 0;
  }
 
  get name() {
    return this._name;
  }
 
  get usesLitter() {
    return this._usesLitter;
  }
 
  get behavior() {
    return this._behavior;
  }  
 
  incrementBehavior() {
    this._behavior++;
  }
}
```

When multiple classes share properties or methods, they become candidates for *inheritance* — a tool developers use to decrease the amount of code they need to write.

With inheritance, you can create a *parent* class (also known as a superclass) with properties and methods that multiple *child* classes (also known as subclasses) share. The child classes inherit the properties and methods from their parent class.

Let’s abstract the shared properties and methods from our `Cat` and `Dog` classes into a parent class called `Animal`.

```js
class Animal {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }
 
  get name() {
    return this._name;
  }
 
  get behavior() {
    return this._behavior;
  }   
 
  incrementBehavior() {
    this._behavior++;
  }
} 
```

### Inheritance III
Now that we have these shared properties and methods in the parent `Animal` class, we can extend them to the subclass, `Cat`.

```js
class Cat extends Animal {
  constructor(name, usesLitter) {
    super(name);
    this._usesLitter = usesLitter;
  }
}
```

The `extends` keyword makes the methods of the animal class available inside the cat class.

The `super` keyword calls the constructor of the parent class. In this case, `super(name)` passes the name argument of the `Cat` class to the constructor of the `Animal` class. When the `Animal` constructor runs, it sets `this._name = name;` for new `Cat` instances.

`_usesLitter` is a new property that is unique to the `Cat` class, so we set it in the `Cat` constructor.

In a `constructor()`, you must always call the `super` method before you can use the `this` keyword — if you do not, JavaScript will throw a reference error.

```js
const bryceCat = new Cat('Bryce', false); 
console.log(bryceCat._name); // output: Bryce
```

### Inheritance IV
When we call `extends` in a class declaration, all of the parent methods are available to the child class.

```js
class Animal {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }
 
  get name() {
    return this._name;
  }
 
  get behavior() {
    return this._behavior;
  }
 
  incrementBehavior() {
    this._behavior++;
  }
} 
 
 
class Cat extends Animal {
  constructor(name, usesLitter) {
    super(name);
    this._usesLitter = usesLitter;
  }
}
 
const bryceCat = new Cat('Bryce', false);

console.log(bryceCat.name);
```

### Inheritance V
In addition to the inherited features, child classes can contain their own properties, getters, setters, and methods.

The syntax for creating getters, setters, and methods is the same as it is in any other class.

```js
class Cat extends Animal {
  constructor(name, usesLitter) {
    super(name);
    this._usesLitter = usesLitter;
  }
 
  get usesLitter() {
    return this._usesLitter;
  }
}
```

One benefit is that when you need to change a method or property that multiple classes share, you can change the parent class, instead of each subclass.

### Static Methods
Sometimes you will want a class to have methods that aren’t available in individual instances, but that you can call directly from the class.

Take the `Date` class, for example — you can both create `Date` instances to represent whatever date you want, and call static methods, like `Date.now()` which returns the current date, directly from the class. The `.now()` method is static, so you can call it directly from the class, but not from an instance of the class.

```js
class Animal {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }
 
  static generateName() {
    const names = ['Angel', 'Spike', 'Buffy', 'Willow', 'Tara'];
    const randomNumber = Math.floor(Math.random()*5);
    return names[randomNumber];
  }
} 
```

Because of the `static` keyword, we can only access `.generateName()` by appending it to the `Animal` class.

```js
console.log(Animal.generateName()); // returns a name
```

You cannot access the `.generateName()` method from instances of the `Animal` class or instances of its subclasses.

```js
const tyson = new Animal('Tyson'); 
tyson.generateName(); // TypeError
```

### Review
- Classes are templates for objects.
- Javascript calls a constructor method when we create a new instance of a class.
- Inheritance is when we create a parent class with properties and methods that we can extend to child classes.
- We use the `extends` keyword to create a subclass.
- The `super` keyword calls the `constructor()` of a parent class.
- Static methods are called on the class, but not on instances of the class.

# Learn JavaScript Syntax: Modules
## Implementing Modules using ES6 Syntax

### What are Modules?
*Modules* are reusable pieces of code in a file that can be exported and then imported for use in another file. A *modular* program is one whose components can be separated, used individually, and recombined to create a complex system.

Note: The words “module” and “file” are often used interchangably.

### Implementations of Modules in JavaScript: Node.js vs ES6
It should be noted that there are multiple ways of implementing modules depending on the *runtime environment* in which your code is executed. In JavaScript, there are two runtime environments and each has a preferred module implementation.

1. The Node runtime environment and the `module.exports` and `require()` syntax.
2. The browser’s runtime environment and the ES6 `import`/`export` syntax.

### Implementing Modules in the Browser
Suppose you wanted to build a simple web application with some hidden text that is revealed when a button is pressed.

To create this website, you could create two files, **secret-messages.html** and **secret-messages.js**, and store them together in a folder called **secret-messages**:

```
secret-messages/
|-- secret-messages.html
|-- secret-messages.js
```

```html
<!-- secret-messages.html --> 
<html>
  <head>
    <title>Secret Messages</title>
  </head>
  <body>
    <button id="secret-button"> Press me... if you dare </button>
    <p id="secret-p" style="display: none"> Modules are fancy! </p>
    <script src="./secret-messages.js"> </script>
  </body>
</html>
```

The `./` before the file name is how you indicate that the file being referenced (**secret-messages.js**) is in the same folder as the file referencing it (**secret-messages.html**).

```js
/* secret-messages.js */
const buttonElement = document.getElementById('secret-button');
const pElement = document.getElementById('secret-p');
 
const toggleHiddenElement = (domElement) => {
    if (domElement.style.display === 'none') {
      domElement.style.display = 'block';
    } else {
      domElement.style.display = 'none';
    }
}
 
buttonElement.addEventListener('click', () => {
  toggleHiddenElement(pElement);
});
```

Now, suppose you wanted to create a second webpage with similar features. There is still a button, but this time clicking it reveals an image.

```
secret-image/
|-- secret-image.html
|-- secret-image.js
```

```html
<!-- secret-image.html --> 
<html>
  <head>
    <title>Secret Image</title>
  </head>
  <body>
    <button id="secret-button"> Want to see something cool? </button>
    <img id="secret-img" src="imageURL.jpg" style="display: none">
    <script src="./secret-image.js"> </script>
  </body>
</html>
```

```js
/* secret-image.js */
const buttonElement = document.getElementById('secret-button');
const imgElement = document.getElementById('secret-img');
 
const toggleHiddenElement = (domElement) => {
    if (domElement.style.display === 'none') {
      domElement.style.display = 'block';
    } else {
      domElement.style.display = 'none';
    }
}
 
buttonElement.addEventListener('click', () => {
  toggleHiddenElement(imgElement);
});
```

Having two identical, but separate, copies of a function can lead to maintenance issues in the future. For example, any bugs that may exist within the function would need to be fixed in two places rather than one.

Instead, creating a single copy of `toggleHiddenElement()` within a module that *exports* it would allow these two websites to *import* and use the exact same function.

### ES6 Named Export Syntax
A module must be entirely contained within a file. Since it needs to be used by both of these projects, you may want to put it in a mutually accessible location.

```
secret-image/
|-- secret-image.html
|-- secret-image.js
secret-messages/
|-- secret-messages.html
|-- secret-messages.js
modules/
|-- dom-functions.js    <-- new module file
```

Inside **dom-functions.js**, the functions you wish to reuse can be exported using the *named export* syntax. Using this syntax, the name of each exported resource is listed between curly braces and separated by commas.

```js
/* dom-functions.js */
const toggleHiddenElement = (domElement) => {
    if (domElement.style.display === 'none') {
      domElement.style.display = 'block';
    } else {
      domElement.style.display = 'none';
    }
}
 
const changeToFunkyColor = (domElement) => {
  const r = Math.random() * 255;
  const g = Math.random() * 255;
  const b = Math.random() * 255;
 
  domElement.style.background = `rgb(${r}, ${g}, ${b})`;
}
 
export { toggleHiddenElement, changeToFunkyColor };
```

These exported functions are now available to be imported and used by other files!

In addition to the syntax above, in which all named exports are listed together, individual values may be exported as named exports by simply placing the export keyword in front of the variable’s declaration.

```js
/* dom-functions.js */
export const toggleHiddenElement = (domElement) => {
  // logic omitted...
}
 
export const changeToFunkyColor = (domElement) => {
  // logic omitted...
}
```

### ES6 Import Syntax
Let’s update the **secret-messages** program such that it now imports functionality from **dom-functions.js**. Doing so requires two important steps. First, update **secret-messages.js**.

```js
/* secret-messages.js */
import { toggleHiddenElement, changeToFunkyColor } from '../modules/dom-functions.js';
 
const buttonElement = document.getElementById('secret-button');
const pElement = document.getElementById('secret-p');
 
buttonElement.addEventListener('click', () => {
  toggleHiddenElement(pElement);
  changeToFunkyColor(buttonElement);
});
```

The `../` indicates that the **modules/** folder is in the same folder as the parent folder, **secret-messages/**.

Now, you must also update **secret-messages.html**.

```html
<!-- secret-messages.html --> 
<html>
  <head>
    <title>Secret Messages</title>
  </head>
  <body>
    <button id="secret-button"> Press me... if you dare </button>
    <p id="secret-p" style="display: none"> Modules are fancy! </p>
    <script type="module" src="./secret-messages.js"> </script>
  </body>
</html>
```

In **secret-messages.html**, the only thing that changes is the addition of the attribute `type='module'` to the `<script>` element.

### Renaming Imports to Avoid Naming Collisions
Inevitably, you will run into a situation where the resources you wish to import share a name with some other value that already exists in your program (or from another imported module).

For example, suppose you had access to two modules, **greeterEspanol.js** and **greeterFrancais.js**. Each exports a function called `greet()`.

```js
/* inside greeterEspanol.js */
const greet = () => {
  console.log('hola');
}
export { greet };
 
/* inside greeterFrancais.js */
const greet = () => {
  console.log('bonjour');
}
export { greet };
```

Now, let’s say you wanted to use each of these functions in a program, called **main.js**, that simulates a conversation between a spanish-speaker and a french-speaker.

```js
import { greet } from 'greeterEspanol.js';
import { greet } from 'greeterFrancais.js';
```

The code above will throw an error on line 2 due to the fact that the identifier greet has already been defined on line 1. Thankfully, ES6 includes syntax for renaming imported resources by adding in the keyword `as`.

```js
/* main.js */
import { greet as greetEspanol } from 'greeterEspanol.js';
import { greet as greetFrancais } from 'greeterFrancais.js';
 
greetEspanol(); // Prints: hola
greetFrancais(); // Prints: bonjour
```

### Default Exports and Imports
Every module also has the option to export a single value to represent the entire module called the *default export*. Often, though not always, the default export value is an object containing the entire set of functions and/or data values of a module.

```js
const resources = { 
  valueA, 
  valueB 
}
export { resources as default };
```

At first glance, it looks like the resources object is being exported as a named export. However, the clause `as default` renames the exported object to default, a reserved identifier that can only be given to a single exported value.

You may also see this shorthand syntax where the value follows `export default` is the default value to be exported.

```js
const resources = {
  valueA,
  valueB
}
export default resources;
```

The syntax for importing default exports looks like this.

```js
import importedResources from 'module.js';
```

Notice that the curly braces are gone from the import statement. This syntax is actually shorthand for `import { default as importedResources }` from **module.js** and the imported `default` value may be given any name the programmer chooses.

It should be noted that if the `default` export is an object, the values inside cannot be extracted until after the object is imported.

```js
// This will work...
import resources from 'module.js'
const { valueA, valueB } = resources;
 
// This will not work...
import { valueA, valueB } from 'module.js'
```

The **dom-functions.js** module from above could be rewritten to use default exports.

```js
/* dom-functions.js */
const toggleHiddenElement = (domElement) => {
    if (domElement.style.display === 'none') {
      domElement.style.display = 'block';
    } else {
      domElement.style.display = 'none';
    }
}
 
const changeToFunkyColor = (domElement) => {
  const r = Math.random() * 255;
  const g = Math.random() * 255;
  const b = Math.random() * 255;
 
  domElement.style.background = `rgb(${r}, ${g}, ${b})`;
}
 
const resources = { 
  toggleHiddenElement, 
  changeToFunkyColor
}
export default resources;
```

This default exports object can now be used within **secret-messages.js**.

```js
import domFunctions from '../modules/dom-functions.js';
 
const { toggleHiddenElement, changeToFunkyColor } = domFunctions;
 
const buttonElement = document.getElementById('secret-button');
const pElement = document.getElementById('secret-p');
 
buttonElement.addEventListener('click', () => {
  toggleHiddenElement(pElement);
  changeToFunkyColor(buttonElement);
});
```

# Learn JavaScript Syntax: Error Handling
## Learn JavaScript: Error Handling

### Introduction to Error Handling
There are two categories of programming mistakes: those that don’t prevent our code from running and those that do.

We can’t always stop errors before they occur, but we can include a backup plan in our program to anticipate and respond to the errors to ensure that our program continues running. *Error handling* is the process of programmatically anticipating and addressing errors. In JavaScript, we handle errors using the keywords `try` and `catch`.

### Runtime Errors
When an error is thrown, our program stops running and the console displays the error message in red text.

When we execute code and a line of code throws an error, that error is referred to as a *runtime error*. In JavaScript, there are built-in error objects that have a `name` and `message` property which tell us what went wrong. Examples of built-in runtime errors include:

- ReferenceError: when a variable or function cannot be found.
- TypeError: when a value is not a valid type.

```js
const reminder = 'Reduce, Reuse, Recycle';
reminder = 'Save the world';
// TypeError: Assignment to constant variable.
console.log('This will never be printed!');
```

### Constructing an Error
JavaScript errors are objects that have a name and message property.

We could use the `Error` function to make our own error object with a message that is unique to our program.

```js
console.log(Error('Your password is too weak.'));
// Prints: Error: Your password is too weak.
```

The `Error` function takes an argument of a string which becomes the value of the error’s `message` property. 

You might also see errors created with the `new` keyword. Both methods will lead to the same functionality.

```js
console.log(new Error('Your password is too weak.'));
// Prints: Error: Your password is too weak.
```

Keep in mind that creating an error is not the same as throwing an error. A thrown error will cause the program to stop running. 

### The throw Keyword
To throw an error in JavaScript, we use the `throw` keyword.

```js
throw Error('Something wrong happened');
// Error: Something wrong happened
```

When we use the `throw` keyword, the error is thrown and code after the throw statement will not execute.

### The try...catch Statement
We have the ability to anticipate and *handle* these errors by writing code to address the error and allow our program to continue running.

In JavaScript, we use `try...catch` statement to anticipate and handle errors. 

```js
try {
  throw Error('This error will get caught');
} catch (e) {
  console.log(e);
}
// Prints: This error will get caught
 
console.log('The thrown error that was caught in the try...catch statement!');
// Prints: 'The thrown error that was caught in the try...catch statement!'
```

Inside the `try` block we insert code that we anticipate might throw an error.

Following the `try` block is the `catch` statement which accepts the thrown error from the `try` block . The `e` represents the thrown error.

The curly braces that follow `catch(e)` is known as the *catch block* and contains code that executes to handle the error.

Generally speaking, in a `try...catch` statement, we evaluate code in the `try` block and if the code throws an error, the code inside the `catch` block will handle the error for us. 


# Cheatsheets

## Classes
![[javascript_syntax_classes.pdf]]

## Error Handling
![[javascript_syntax_error_handling.pdf]]


