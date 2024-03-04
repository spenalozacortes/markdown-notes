Developers use HTML and CSS to control the content and styling of a page. And they use JavaScript to make that page interactive.

# Learn Basic JavaScript by Building a Role Playing Game
JavaScript is a powerful scripting language that you can use to make web pages interactive. It's one of the core technologies of the web, along with HTML and CSS. All modern browsers support JavaScript.

Begin by creating a `script` element. This element is used to load JavaScript into your HTML file. You should use an opening `<script>` and closing `</script>` tag.

```html
<script></script>
```

Add a `console.log("Hello World");` line between your `script` tags.

Then give your now empty `script` element a `src` attribute set to `./script.js`.

```html
<script src="./script.js"></script>
```

In JavaScript, a variable is used to hold a value. To use a variable, you must first declare it. For example, to declare a variable called `camperbot`, you would write:

```js
var camperbot;
```

The `var` keyword tells JavaScript you are declaring a variable.

Variables can be assigned a value. When you do this while you declare it, this is called initialization. For example:

```js
var camperbot = "Bot";
```

This would initialize the `camperbot` variable with a value of `Bot`, a string.

When a variable name has multiple words, the convention in JavaScript is to use what's called camelCase. The first word is lowercase, and the first letter of every following word is uppercase.

You have been declaring your variables with the `var` keyword. However, in modern JavaScript it is best practice to use the `let` keyword instead. This fixes several unusual behaviors with `var` that can make your code difficult to debug.

```js
let xp = 0;
```

Strings are used to store things like words or text. Strings are surrounded with double quotes, single quotes, or backticks. Here is an example of declaring a variable with a string:

```js
let developer = "Naomi";
```

An array can be used to hold multiple values. For example:

```js
let order = ["first", "second", "third"];
```

JavaScript interacts with the HTML using the Document Object Model, or DOM. The DOM is a tree of objects that represents the HTML. You can access the HTML using the `document` object, which represents your entire HTML document.

One method for finding specific elements in your HTML is using the `querySelector()` method. The `querySelector()` method takes a CSS selector as an argument and returns the first element that matches that selector. For example, to find the `<h1>` element in your HTML, you would write:

```js
let h1 = document.querySelector("h1");
```

Remember that CSS `id` selectors are prefixed with a `#`.

```js
let button1 = document.querySelector("#button1");
```

You are trying to query your page for a button element, but your `script` tag is in the `head` of your HTML. This means your code runs before the browser has finished reading the HTML, and your `document.querySelector()` will not see the button - because the browser hasn't processed it yet.

To fix this, move your `script` element out of the `head` element, and place it at the end of your `body` element (just before the closing `</body>` tag.)

`button1` is a variable that is not going to be reassigned. If you are not going to assign a new value to a variable, it is best practice to use the `const` keyword to declare it instead of the `let` keyword. This will tell JavaScript to throw an error if you accidentally reassign it.

```js
const button1 = document.querySelector("#button1");
```

Functions are special tools that allow you to run sections of code at specific times. You can declare functions using the `function` keyword. Here is an example of a function called `functionName` - note the opening and closing curly braces. These indicate the section of code that is within the function.

```js
function functionName() {

}
```

Comments allow you to add notes to your code. In JavaScript, single-line comments can be written with `//` and multi-line comments can be written with `/*` and `*/`. For example, here are single and multi-line comments that say "Hello World":

```js
// hello world

/*
  hello world
*/
```

`button1` represents your first `button` element. These elements have a special property called `onclick`, which you can use to determine what happens when someone clicks that button.

You can access properties in JavaScript a couple of different ways. The first is with dot notation. Accessing the `onclick` property of a button would look like:

```js
button.onclick
```

The `innerText` property controls the text that appears in an HTML element. For example:

```js
const info = document.querySelector("#info");
info.innerText = "Hello World";
```

This code would change the element assigned to the `info` variable to have the text `Hello World`.

Because your string is already wrapped in double quotes, you'll need to escape the quotes around `Store`. You can escape them with a backslash `\`. Here is an example:

```js
const escapedString = "Naomi likes to play \"Zelda\" sometimes.";
```

You have repetition in the `goTown` and `goStore` functions. When you have repetition in your code, this is a sign that you need another function. Functions can take parameters, which are values that are given to the function each time it is run. Here is a function that takes a parameter called `param`:

```js
function myFunction(param) {
    console.log(param);
}
```

You previously used an array to store strings. But arrays can store any data type.

Objects are indicated by curly braces. An empty object would look like `{}`.

Object properties are written as `key: value` pairs, where `key` is the name of the property (or the key), and `value` is the value that property holds. For example, here is an object with a key of `name` set to `Quincy Larson`.

```js
{
  name: "Quincy Larson"
}
```

Just like array values, object properties are separated by a comma.

Note that, because the property name has more than one word, you'll need to surround it in quotes. For example:

```js
{
  name: "Naomi",
  "favorite color": "purple"
}
```
#aqui 
Here is an example of calling a function named `myFunction`:

```js
myFunction();
```

You pass arguments by including them within the parentheses of the function call. For example, calling `myFunction` with an `arg` argument would look like:

```js
myFunction(arg);
```

Pass in only the first element of the `locations` array by adding `[0]` at the end of the variable. For example: `myFunction(arg[0]);`.

This is called bracket notation. Values in an array are accessed by index. Indices are numerical values and start at `0` - this is called zero-based indexing. `arg[0]` would be the first element in the `arg` array.

Here is an example of accessing the `name` property of an object called `person`:

```js
person.name
```

There is a shorthand way to add or subtract from a variable called compound assignment. For example, changing `num = num + 5` to compound assignment would look like `num += 5`.

When you want to run code conditionally, you can use the if statement.

An `if` statement is used to make decisions in code. The keyword `if` is followed by a condition in parentheses. If the condition is true, the code inside the curly braces `{}` is executed. If the condition is false, the code inside the curly braces is skipped.

Here is an example of an `if` statement:

```js
const num = 5;
if (num >= 3) {
  console.log("This code will run because num is greater than or equal to 3.");
}
```

Add an `else` statement where you can put code to run if a player does not have enough money.

Here is an example of an empty `else` statement:

```js
if (num >= 5) {

} else {

}
```