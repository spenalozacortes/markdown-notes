The Document Object Model (DOM) represents the different parts of a website. Use JavaScript to manipulate the DOM and create a interactive site.

# JavaScript and the DOM

## The Script Element

### JavaScript and HTML
HTML defines the structure of a web page by using page elements as the building blocks. However, HTML by itself can not produce web page interactivity, that’s where JavaScript comes in.

Web programmers use JavaScript to make web pages dynamic and interactive. This powerful scripting language is encapsulated in its own HTML element: the ```<script>``` element. You can think of this ```<script>``` element as the door to JavaScript for HTML.

### The `<script>` tag
The ```<script>``` element allows you to add JavaScript code inside an HTML file.

```html
<h1>This is an embedded JS example</h1>
<script>
  function Hello() {
    alert ('Hello World');
  }
</script>
```

### The src attribute
Linking code is preferable because of a programming concept called Separation of Concerns (SoC). Instead of having messy code that is all in the same file, web developers separate their code into different files, making each “concern” easier to understand and more convenient when changes must be made.

If the file is in the same project folder, the ```src``` value will be a *relative path* name. 

```html
<script src="./exampleScript.js"></script>
```

If you must refer to JavaScript hosted externally, or in a CDN, you can also link to that file location.

### How are scripts loaded?
Browsers come equipped with *HTML parsers* that help browsers render the elements accordingly. Elements, including the ```<script>``` element, are by default, parsed in the order they appear in the HTML file. When the HTML parser encounters a ```<script>``` element, it loads the script then executes its contents before parsing the rest of the HTML.

- The HTML parser does NOT process the next element in the HTML file until it loads and executes the ```<script>``` element, thus leading to a delay in load time and resulting in a poor user experience.
- Additionally, scripts are loaded sequentially, so if one script depends on another script, they should be placed in that very order inside the HTML file.

### Defer attribute
HTML4 introduced the defer and async attributes of the ```<script>``` element to address the user wait-time in the website based on different scenarios.

The *defer attribute* specifies scripts should be executed after the HTML file is completely parsed. When the HTML parser encounters a `<script>` element with the `defer` attribute, it loads the script but defers the actual execution of the JavaScript until after it finishes parsing the rest of the elements in the HTML file.

```html
<script src="example.js" defer></script> 
```

When a script contains functionality that requires interaction with the DOM, the `defer` attribute is the way to go. This way, it ensures that the entire HTML file has been parsed before the script is executed.

### Async attribute
The `async` attribute loads and executes the script asynchronously with the rest of the webpage. This means that, similar to the `defer` attribute, the HTML parser will continue parsing the rest of the HTML as the script is downloaded in the background. However, with the `async` attribute, the script will not wait until the entire page is parsed: it will execute immediately after it has been downloaded.

```html
<script src="example.js" async></script>
```

`async` is useful for scripts that are independent of other scripts in order to function accordingly. Thus, if it does not matter exactly at which point the script file is executed, asynchronous loading is the most suitable option as it optimizes web page load time.

### Review
- HTML creates the skeleton of a webpage, but JavaScript introduces interactivity
- The `<script>` element has an opening and closing tag. You can embed JavaScript code inbetween the opening and closing `<script>` tags.
- You link to external JavaScript files with the `src` attribute in the opening `<script>` tag.
- By default, scripts are loaded and executed as soon as the HTML parser encounters them in the HTML file, the HTML parser waits to load the entire script before from proceeding to parse the rest of the page elements.
- The `defer` attribute ensures that the entire HTML file has been parsed before the script is executed.
- The `async` attribute will allow the HTML parser to continue parsing as the script is being downloaded, but will execute immediately after it has been downloaded.

The old convention was to put scripts right before the `</body>` tag to prevent the script from blocking the rest of the HTML content. Now, the convention is to put the script tag in the `<head>` element and to use the `defer` and `async` attributes.

## The Document Object Model

### What is the DOM?
The *Document Object Model*, abbreviated DOM, is a powerful tree-like structure that allows programmers to conceptualize hierarchy and access the elements on a web page.

We like to think of the DOM as the link between an HTML web page and scripting languages.

### The DOM as a Tree Structure
We define a *node* as an intersecting point in a tree that contains data.

In the DOM tree, the top-most node is called the *root node*, and it represents the HTML document.

### Parent Child Relationships in the DOM
A *parent node* is any node that is a direct ancestor of another node.

A *child node* is a direct descendant of another node, called the parent node.

### Nodes and Elements in the DOM
In our diagram, the node objects with the sharp-edge rectangles are *Element* nodes, while the rounded edge rectangles are *Text* nodes, because they represent the text inside the HTML paragraph elements.

When trying to modify a web page, the script will mostly interact with the DOM element nodes and occasionally text nodes.

### Review
- The DOM is a structural model of a web page that allows for scripting languages to access that page.
- The system of organization in the DOM mimics the nesting structure of an HTML document.
- Elements nested within another are referred to as the children of that element. The element they are nested within is called the parent element of those elements.
- The DOM also allows access to the attributes of an HTML element such as style, id, etc.

## JavaScript and the DOM

### The Document Keyword
The `document` object in JavaScript is the door to the DOM structure. The `document` object allows you to access the root node of the DOM tree. Before you can access a specific element in the page, first you must access the `document` structure itself. The document object allows scripts to access children of the DOM as properties.

For example, if you want to access the `<body>` element from your script, you can access it as a property of the `document` object by using `document.body`. This property will return the body element of that DOM.

[Comprehensive list of all document properties](https://developer.mozilla.org/en-US/docs/Web/API/Document)

### Tweak an Element
When using the DOM in your script to access an HTML element, whether it’s an `<li>` element or the entire `<body>` element, you also have access to all of that element’s properties.

This includes the ability to modify the contents of the element as well as its attributes and properties.

The `.innerHTML` property allows you to access and set the contents of an element.

Let’s take a look at how we can reassign the contents of the `<body>` element to the text `'The cat loves the dog'`:

```js
document.body.innerHTML = 'The cat loves the dog.';
```

The `.innerHTML` property can also add any valid HTML elements. 

```js
document.body.innerHTML = '<h2>This is a heading</h2>'; 
```

### Select and Modify Elements
The DOM interface allows us to access a specific element with CSS selectors.

Selectors can include a tag name, a class, or an ID.

The `.querySelector()` method allows us to specify a CSS selector as a string and returns the first element that matches that selector.

```js
document.querySelector('p');
```

If you want to access an element directly by its id, you can use the aptly named `.getElementById()` method.

```js
document.getElementById('bio').innerHTML = 'The description';
```

Notice that the ID is passed as a string, wrapped in quotation marks (' ').

There are also the `.getElementsByClassName()` and `.getElementsByTagName()` methods which return an array of elements, instead of just one element. You can use bracket notation to access individual elements of an array:

```js
// Set first element of .student class as 'Not yet registered'
document.getElementsByClassName('student')[0].innerHTML = 'Not yet registered';
 
// Set second <li> tag as 'Cedric Diggory'
document.getElementsByTagName('li')[1].innerHTML = 'Cedric Diggory`;
```

### Style an Element
The `.style` property of a DOM element provides access to the inline style of that HTML tag.

The syntax follows an `element.style.property` format, with the `property` representing a CSS property.

```js
let blueElement = document.querySelector('.blue');
blueElement.style.backgroundColor = 'blue';
```

Unlike CSS, the DOM `.style` property does not implement a hyphen such as `background-color`, but rather camel case notation, `backgroundColor`.

The following *chaining* syntax would also work:

```js
document.querySelector('.blue').style.fontFamily = 'Roboto';
```

### Traversing the DOM
Each element has a `.parentNode` and `.children` property. The `.parentNode` property returns the parent of the specified element in the DOM hierarchy. Note that the `document` element is the *root node* so its `.parentNode` property will return `null`. The `.children` property returns an array of the specified element’s children. If the element does not have any children, it will return `null`.

```html
<ul id='groceries'>
  <li id='must-have'>Toilet Paper</li>
  <li>Apples</li>
  <li>Chocolate</li>
  <li>Dumplings</li>
</ul>
```

```js
let parentElement = document.getElementById('must-have').parentNode; // returns <ul> element
let childElements = document.getElementById('groceries').children; // returns an array of <li> elements
```

### Create and Insert Elements
Just as the DOM allows scripts to modify existing elements, it also allows for the creation of new ones.

The `.createElement()` method creates a new element based on the specified tag name passed into it as an argument. However, it does not append it to the document. It creates an empty element with no inner HTML.

```js
let paragraph = document.createElement('p');
```

We can assign values to the properties of the newly created element like how we’ve done previously with existing elements.

```js
paragraph.id = 'info'; 
paragraph.innerHTML = 'The text inside the paragraph';
```

In order to create an element and add it to the web page, you must assign it to be the child of an element that already exists on the DOM, referred to as the parent element. We call this process *appending*. The `.appendChild()` method will add a child element as the parent element’s last child node.

```js
document.body.appendChild(paragraph);
```

The `.appendChild()` method does not replace the content inside of the parent, in this case, `body`. Rather, it appends the new element as the last child of that parent.

### Remove an Element
The `.removeChild()` method removes a specified child from a parent.

```js
let paragraph = document.querySelector('p');
document.body.removeChild(paragraph);
```

This removes the first paragraph from the document body.

If you want to hide an element rather than completely deleting it, the .hidden property allows you to hide it by setting the property as true or false:

```js
document.getElementById('sign').hidden = true;
```

### Add Click Interactivity
You can add interactivity to DOM elements by assigning a function to run based on an event. Events can include anything from a click to a user mousing over an element.

The `.onclick` property allows you to assign a function to run on when a click event happens on an element:

```js
let element = document.querySelector('button');
 
element.onclick = function() { 
  element.style.backgroundColor = 'blue' 
};
```

You can also assign the `.onclick` property to a function by name:

```js
let element = document.querySelector('button');
 
function turnBlue() {
   element.style.backgroundColor = 'blue';
}
 
element.onclick = turnBlue;
```

### Review
- The document keyword grants access to the root of the DOM in JavaScript.
- The DOM Interface allows you to select a specific element with CSS selectors by using the `.querySelector()` method.
- You can access an element directly by its ID with the `.getElementById()` method which returns a single element.
- You can access an array of elements with the `.getElementsByClassName()` and `.getElementsByTagName()` methods, then call a single element by referencing its placement in the array.
- The `.innerHTML` and `.style` properties allow you to modify an element by changing its contents or style respectively.
- You can create, append, and remove elements by using the `.createElement()`,`.appendChild()` and `.removeChild()` methods respectively.
- The `.onclick` property can add interactivity to a DOM element based on a click event.
- The `.children` property returns a list of an element’s children and the `.parentNode` property returns the element’s closest connected node in the direction towards the root.


# DOM Events with JavaScript
## DOM Events with JavaScript

### What is an Event?
Events on the web are user interactions and browser manipulations that you can program to trigger functionality. Some examples of events are:

- A mouse clicking on a button
- Webpage files loading in the browser
- A user swiping right on an image

When a user does any of the above actions, they’re causing the event to be *fired* or be *triggered*. 

Being able to respond to these events makes your website interactive and therefore *dynamic*.

### "Firing" Events
After a specific event fires on a specific element in the document object model (or DOM), an *event handler* function can be created to run as a response.

### Event Handler Registration
Using the `.addEventListener()` method, we can have a DOM element listen for a specific event and execute a block of code when the event is detected. The DOM element that listens for an event is called the *event target* and the block of code that runs when the event happens is called the *event handler*.

```js
let eventTarget = document.getElementById('targetElement');
 
eventTarget.addEventListener('click', function() {
  // this block of code will run when click event happens on eventTarget element
});
```

Instead of using an anonymous function as the event handler, it’s best practice to create a named event handler function. Your code will remain organized and reusable this way, even if your code gets complex.

```js
function eventHandlerFunction() {
  // this block of code will run when click event happens
}
 
eventTarget.addEventListener('click', eventHandlerFunction);
```

### Adding Event Handlers
Event Handlers can also be registered by setting an `.onevent` property on a DOM element (event target). The pattern for registering a specific event is to append an element with `.on` followed by the lowercased event type name.

```js
eventTarget.onclick = eventHandlerFunction;
```

It’s important to know that this `.onevent` property and `.addEventListener()` will both register event listeners. With `.onevent`, it allows for one event handler function to be attached to the event target. However, with the `.addEventListener()` method , we can add multiple event handler functions.

### Removing Event Handlers
The `.removeEventListener()` method is used to reverse the `.addEventListener()` method. This method stops the event target from “listening” for an event to fire when it no longer needs to. `.removeEventListener()` also takes two arguments:

- The event type as a string
- The event handler function

```js
eventTarget.removeEventListener('click', eventHandlerFunction);
```

Because there can be multiple event handler functions associated with a particular event, `.removeEventListener()` needs both the exact event type name and the name of the event handler you want to remove. If `.addEventListener()` was provided an anonymous function, then that event listener cannot be removed.

### Event Object Properties
JavaScript stores events as Event objects with their related data and functionalities as properties and methods. When an event is triggered, the event object can be passed as an argument to the event handler function.

```js
function eventHandlerFunction(event){
   console.log(event.timeStamp);
}
 
eventTarget.addEventListener('click', eventHandlerFunction);
```

There are pre-determined properties associated with event objects. 

- the `.target` property to reference the element that the event is registered to.
- the `.type` property to access the name of the event.
- the `.timeStamp` property to access the number of milliseconds that passed since the document loaded and the event was triggered.

### Event Types
It’s important to know *most* events in the DOM take place without being noticed because there are no event handlers connected to them.

It’s also important to know some registered events don’t depend on user interactions to fire. For instance, the `load` event fires after website files completely load in the browser.

### Mouse Events
The `mousedown` event is fired when the user presses a mouse button down. This is different from a `click` event because `mousedown` doesn’t need the mouse button to be released to fire.

The `mouseup` event is fired when the user releases the mouse button.

The `mouseover` event is fired when the mouse enters the content of an element.

The `mouseout` event is fired when the mouse leaves an element.

### Keyboard Events
*Keyboard events* are triggered by user interaction with keyboard keys in the browser.

The `keydown` event is fired while a user presses a key down.

The `keyup` event is fired while a user releases a key.

The `keypress` event is fired when a user presses a key down and releases it. This is different from using `keydown` and `keyup` events together, because those are two complete events and `keypress` is one complete event.

Keyboard events have unique properties assigned to their event objects like the `.key` property that stores the values of the key pressed by the user.

### Review
- You can register events to DOM elements using the `addEventListener()` method.
- The `addEventListener()` method takes two arguments: an event type and an event handler function.
- When an event is triggered on the event target, the registered event handler function executes.
- Event handler functions can also be registered as values of `onevent` properties of their event target.
- Event object properties like `.target`, `.type`, and `.timeStamp` are used to provide information about the event.
- The `addEventListener()` method can be used to add multiple event handler functions to a single event.
- The `removeEventListener()` method stops specific event handlers from “listening” for specific events firing.


# HTML Forms
## Introduction to Form Validation

### Introduction
User information is traditionally collected using HTML *forms*.

The process of checking that the information submitted through a form adheres to expectations is called *form validation*.

### Regular Expressions
Unlike humans, who can get this training passively over time, computers have to be precisely programmed to recognize patterns. To specify patterns for the computer to recognize, we use a special language called *regular expressions* — also known as regex or regexp. A regular expression is a sequence of characters representing a pattern. We can use that pattern to match a string, match parts of a string, confirm that data is formatted acceptably, or even replace parts of strings with different characters.

### Client-side Validation: HTML
The first technique we can use to validate form data is to prevent problematic inputs from being submitted in the first place. This is called *client-side validation*. The client is the process interacting with the server on behalf of a user—in the case of websites, the web browser is the client. The logic for validating the form is included with the code that displays the form on the user’s device. No interaction with the back-end is required to perform client-side validations.

Since form validation is so common, modern HTML provides some of these validation features built-in.

If any of the rules laid out in the HTML form validation aren’t followed, the user will not be able to submit their form, and they’ll receive an error message explaining why. With these checks in place, the back-end is less likely to be sent incorrect data. HTML form validation will also benefit the user—the client provides the user immediate feedback, without having to wait for time-consuming communication with the back-end.

### Client-side Validation: JavaScript
In order to truly customize validation or to perform more complex validations, we can incorporate JavaScript form validations. We can do this by either writing the JavaScript ourselves or by incorporating a JavaScript library.

If we’re creating a relatively simple website, it makes sense to code the form validation ourselves or use a simple vanilla JavaScript library—just-validate, for example. But most basic validation libraries will involve directly accessing or manipulating the DOM. This can get tricky when working with a framework that relies on a virtual DOM—like React or Vue. In those situations, it might be best to incorporate a library that works well with your specific framework. For example, the formik library is a lightweight library that simplifies validating forms in a React app.

### Back-end Validation
No matter how complete the front-end validation of a website or application seems, validations must also be completed on the back-end or server-side. Front-end validations are easy to bypass—a malicious user can simply turn off JavaScript on their browser, for example. There’s also the potential for middleman attacks in which data is changed after the request is submitted by a user but before it arrives at the server. As a rule, the back-end should never trust the data it receives.

As the developer, once data is in the back-end, we have complete control over it, luckily. Back-end validation has several advantages:

- It enables us to use validation code often on machines with more computing power.
- It allows us to write validation code that a user can’t see—if malicious users can’t see exactly how we validate the data, it’s much more difficult for them to find ways around it.
- We can validate the information against other data the front-end doesn’t have access to—for example, we can check our database to see if a given username is already in use.

There are two main ways to validate inputs on the server-side. The first takes place while the user is still inputting data into the form on the front-end. We can make asynchronous requests to the server with pieces of their data and send feedback directly to the user before they’ve submitted. This is slower than front-end validation and can be a design challenge from a user-experience perspective.

The second is once the form has been submitted. Back-end form validation is our application’s last defense against problematic data, and it’s essential to verify the validity and safety of data before adding it to a database. This is also an opportunity to “sanitize” the data: in order for our database to be useful, it’s important that all data within it is formatted consistently. This means that while we may want to be flexible about the formatting we require from a user, we likely want to transform inputs into a strict format before entering them in the database.

### Review
- Modern websites require a lot of information from their users and they collect a lot of this information through HTML forms.
- It’s essential to validate the data submitted through forms to keep websites secure and to make sure they function correctly.
- Regular expressions are sequences of characters that define patterns to look for in text. They are an important tool used in validating input.
- Modern HTML comes with useful built-in methods for form validation.
- Custom and complicated client-side validation can be accomplished with JavaScript.
- Asynchronous requests to the server can perform back-end validations before a form has been submitted.
- A final back-end validation of all data is required to ensure an application’s security and sanitize all data.

## HTML Forms

### How a Form Works
We can think of the internet as a network of computers which send and receive information. Computers need an *HTTP request* to know how to communicate. The HTTP request instructs the receiving computer how to handle the incoming information. 

The `<form>` element is a great tool for collecting information, but then we need to send that information somewhere else for processing. We need to supply the `<form>` element with both the location of where the `<form>`‘s information goes and what HTTP request to make.

```html
<form action="/example.html" method="POST">
</form>
```

In the above example, we’ve created the skeleton for a `<form>` that will send information to **example.html** as a POST request.

Note: HTTP verbs like POST do not need to be capitalized for the request to work, but it’s done so out of convention. In the example above we could have written `method="post"` and it would still work.

The `<form>` element can also contain child elements. For instance, it would be helpful to provide a header so that users know what this `<form>` is about. We could also add a paragraph to provide even more detail. 

```html
<form action="/example.html" method="POST">
  <h1>Creating a form</h1>
  <p>Looks like you want to learn how to create an HTML form. Well, the best way to learn is to play around with it.</p>
</form>
```

### Text Input
If we want to create an input field in our `<form>`, we’ll need the help of the `<input>` element.

The `<input>` element has a `type` attribute which determines how it renders on the web page and what kind of data it can accept.

When we create an `<input>` element with `type="text"`, it renders a text field that users can type into. Note that the default value of `type` is `"text"`. It’s also important that we include a `name` attribute for the `<input>` — without the `name` attribute, information in the `<input>` won’t be sent when the `<form>` is submitted. 

```html
<form action="/example.html" method="POST">
  <input type="text" name="first-text-field">
</form>
```

When initially loaded, it will be an empty box.

After users type into the `<input>` element, the value of the `value` attribute becomes what is typed into the text field. The value of the `value` attribute is paired with the value of the `name` attribute and sent as text when the form is submitted.

We could also assign a default value for the `value` attribute so that users have a pre-filled text field when they first see the rendered form.

```html
<form action="/example.html" method="POST">
  <input type="text" name="first-text-field" value="already pre-filled">
</form>
```

### Adding a Label
For a user to properly identify an `<input>` we use the appropriately named `<label>` element.

The `<label>` element has an opening and closing tag and displays text that is written between the opening and closing tags. To associate a `<label>` and an `<input>`, the `<input>` needs an `id` attribute. We then assign the `for` attribute of the `<label>` element with the value of the `id` attribute of `<input>`.

```html
<form action="/example.html" method="POST">
  <label for="meal">What do you want to eat?</label>
  <br>
  <input type="text" name="food" id="meal">
</form>
```

Another benefit for using the `<label>` element is when this element is clicked, the corresponding `<input>` is highlighted/selected.

### Password Input
An `<input type ="password">` element will replace input text with another character like an asterisk (`*`) or a dot (`•`).

```html
<form>
  <label for="user-password">Password: </label>
  <input type="password" id="user-password" name="user-password">
</form>
```

Even though the password field obscures the text of the password, when the form is submitted, the value of the text is sent. In other words, if “hunter2” is typed into the password field, “user-password=hunter2” is sent along with the other information on the form.

### Number Input
By setting `type="number"` for an `<input>` we can restrict what users type into the input field to just numbers (and a few special characters like -, +, and .). We can also provide a `step` attribute which creates arrows inside the input field to increase or decrease by the value of the `step` attribute. 

```html
<form>
  <label for="years"> Years of experience: </label>
  <input id="years" name="years" type="number" step="1">
</form>
```

### Range Input
If we wanted to limit what numbers our users could type we might consider using a different `type` value. Another option we could use is setting `type` to `"range"` which creates a slider.

To set the minimum and maximum values of the slider we assign values to the `min` and `max` attribute of the `<input>`. We could also control how smooth and fluid the slider works by assigning the `step` attribute a value. Smaller `step` values will make the slider move more fluidly, whereas larger `step` values will make the slider move more noticeably. 

```html
<form>
  <label for="volume"> Volume Control</label>
  <input id="volume" name="volume" type="range" min="0" max="100" step="1">
</form>
```

### Checkbox Input
So far the types of inputs we’ve allowed were all single choices. But, what if we presented multiple options to users and allow them to select any number of options? Sounds like we could use checkboxes! In a `<form>` we would use the `<input>` element and set `type="checkbox"`.

```html
<form>
  <p>Choose your pizza toppings:</p>
  <label for="cheese">Extra cheese</label>
  <input id="cheese" name="topping" type="checkbox" value="cheese">
  <br>
  <label for="pepperoni">Pepperoni</label>
  <input id="pepperoni" name="topping" type="checkbox" value="pepperoni">
  <br>
  <label for="anchovy">Anchovy</label>
  <input id="anchovy" name="topping" type="checkbox" value="anchovy">
</form>
```

Each `<input>` has the same value for the `name` attribute. Using the same `name` for each checkbox groups the `<input>`s together. However, each `<input>` has a unique `id` to pair with a `<label>`.

### Radio Button Input
Checkboxes work well if we want to present users with multiple options and let them choose one or more of the options. However, there are cases where we want to present multiple options and only allow for one selection.

```html
<form>
  <p>What is sum of 1 + 1?</p>
  <input type="radio" id="two" name="answer" value="2">
  <label for="two">2</label>
  <br>
  <input type="radio" id="eleven" name="answer" value="11">
  <label for="eleven">11</label>
</form>
```

To group radio buttons together, we assign them the same `name` and only one radio button from that group can be selected.

### Dropdown list
Radio buttons are great if we want our users to pick one option out of a few visible options, but imagine if we have a whole list of options! This situation could quickly lead to a lot of radio buttons to keep track of.

An alternative solution is to use a dropdown list to allow our users to choose one option from an organized list.

```html
<form>
  <label for="lunch">What's for lunch?</label>
  <select id="lunch" name="lunch">
    <option value="pizza">Pizza</option>
    <option value="curry">Curry</option>
    <option value="salad">Salad</option>
    <option value="ramen">Ramen</option>
    <option value="tacos">Tacos</option>
  </select>
</form>
```

By default, only one of these options can be selected.

The text rendered is the text included between the opening and closing `<option>` tags. However, it is the value of the `value` attribute that is used in `<form>` submission.

For instance, if a user selected Pizza from the dropdown list, the information would be sent as `"lunch=pizza"`.

### Datalist Input
Even if we have an organized dropdown list, if the list has a lot of options, it could be tedious for users to scroll through the entire list to locate one option.

The `<datalist>` is used with an `<input type="text">` element. The `<input>` creates a text field that users can type into and filter options from the `<datalist>`.

```html
<form>
  <label for="city">Ideal city to visit?</label>
  <input type="text" list="cities" id="city" name="city">
 
  <datalist id="cities">
    <option value="New York City"></option>
    <option value="Tokyo"></option>
    <option value="Barcelona"></option>
    <option value="Mexico City"></option>
    <option value="Melbourne"></option>
    <option value="Other"></option>  
  </datalist>
</form>
```

The `<input>` is associated to the `<datalist>` via the `<input>`‘s `list` attribute and the `id` of the `<datalist>`.

While `<select>` and `<datalist>` share some similarities, there are some major differences. In the associated `<input>` element, users can type in the input field to search for a particular option. If none of the `<option>`s match, the user can still use what they typed in. When the form is submitted, the value of the `<input>`‘s `name` and the `value` of the option selected, or what the user typed in, is sent as a pair.

### Textarea element
The `<textarea>` element is used to create a bigger text field for users to write more text. We can add the attributes `rows` and `cols` to determine the amount of rows and columns for the `<textarea>`.

```html
<form>
  <label for="blog">New Blog Post: </label>
  <br>
  <textarea id="blog" name="blog" rows="5" cols="30">
  </textarea>
</form>
```

If we want to add a default value to `<textarea>` we would include it within the opening and closing tags.

```html
<textarea>Adding default text</textarea>
```

### Submit Form
To make a submit button in a `<form>`, we’re going to use the reliable `<input>` element and set the type to `"submit"`.

```html
<form>
  <input type="submit" value="Send">
</form>
```

Notice in the code snippet that the value assigned to the `<input>` shows up as text on the submit button. If there isn’t a `value` attribute, the default text, **Submit** shows up on the button.

### Review

- The purpose of a `<form>` is to allow users to input information and send it.
- The `<form>`‘s action attribute determines where the form’s information goes.
- The `<form>`‘s method attribute determines how the information is sent and processed.
- To add fields for users to input information we use the `<input>` element and set the `type` attribute to a field of our choosing:
	- Setting `type` to `"text"` creates a single row field for text input.
	- Setting `type` to `"password"` creates a single row field that censors text input.
	- Setting `type` to `"number"` creates a single row field for number input.
	- Setting `type` to `"range"` creates a slider to select from a range of numbers.
	- Setting `type` to `"checkbox"` creates a single checkbox that can be paired with other checkboxes.
	- Setting `type` to `"radio"` creates a radio button that can be paired with other radio buttons.
	- Setting `type` to `"text"` and adding the `list` attribute will pair the `<input>` with a `<datalist>` element if the `list` of `<input>` and the `id` of `<datalist>` are the same.
	- Setting `type` to `"submit"` creates a submit button.
- A `<select>` element is populated with `<option>` elements and renders a dropdown list selection.
- A `<datalist>` element is populated with `<option>` elements and works with an `<input>` to search through choices.
- A `<textarea>` element is a text input field that has a customizable area.
- When a `<form>` is submitted, the name of the fields that accept input and the value of those fields are sent as `name=value` pairs.

## Form Validation

### Introduction to HTML Form Validation
*Validation* is the concept of checking user provided data against the required data.

There are different types of validation. One type is *server-side validation*, this happens when data is sent to another machine (typically a server) for validation.

On the other hand, we use *client-side validation* if we want to check the data on the browser (the client). This validation occurs before data is sent to the server. Different browsers implement client-side validation differently, but it leads to the same outcome.

Shared among the different browsers are the benefits of using HTML5’s built-in client-side validation. It saves us time from having to send information to the server and wait for the server to send back confirmation or rejection of the data. This can also help us protect our server from malicious code or data from a malicious user. It also allows us to quickly give feedback to users for specific fields rather than having them fill in a form again if the data they input into the form was rejected.

### Requiring an Input
Sometimes we have fields in our `<form>`s which are not optional, i.e. there must be information provided before we can submit it. To enforce this rule, we can add the `required` attribute to an `<input>` element.

```html
<form action="/example.html" method="POST">
  <label for="allergies">Do you have any dietary restrictions?</label>
  <br>
  <input id="allergies" name="allergies" type="text" required>
  <br>
  <input type="submit" value="Submit">
</form>
```

### Set a Minimum and Maximum
Another built-in validation we can use is to assign a minimum or maximum value for a number field, e.g. `<input type="number">` and `<input type="range">`. To set a minimum acceptable value, we use the `min` attribute and assign a value. On the flip side, to set a maximum acceptable value, we assign the `max` attribute a value. 

```html
<form action="/example.html" method="POST">
  <label for="guests">Enter # of guests:</label>
  <input id="guests" name="guests" type="number" min="1" max="4">
  <input type="submit" value="Submit">
</form>
```

### Checking Text Length
To set a minimum number of characters for a text field, we add the `minlength` attribute and a value to set a minimum value. Similarly, to set the maximum number of characters for a text field, we use the `maxlength` attribute and set a maximum value.

```html
<form action="/example.html" method="POST">
  <label for="summary">Summarize your feelings in less than 250 characters</label>
  <input id="summary" name="summary" type="text" minlength="5" maxlength="250" required>
  <input type="submit" value="Submit">
</form>
```

If a user tries to type in more than the maximum allowed number of characters, they don’t get a warning message, but they can’t type it in!

### Matching a Pattern
For cases when we want user input to follow specific guidelines, we use the `pattern` attribute and assign it a regular expression, or regex. Regular expressions are a sequence of characters that make up a search pattern. If the input matches the regex, the form can be submitted.

```html
<form action="/example.html" method="POST">
  <label for="payment">Credit Card Number (no spaces):</label>
  <br>
  <input id="payment" name="payment" type="text" required pattern="[0-9]{14,16}">
  <input type="submit" value="Submit">
</form>
```

### Review
- Client-side validations happen in the browser before information is sent to a server.
- Adding the `required` attribute to an input related element will validate that the input field has information in it.
- Assigning a value to the `min` attribute of a number input element will validate an acceptable minimum value.
- Assigning a value to the `max` attribute of a number input element will validate an acceptable maximum value.
- Assigning a value to the `minlength` attribute of a text input element will validate an acceptable minimum number of characters.
- Assigning a value to the `maxlength` attribute of a text input element will validate an acceptable maximum number of characters.
- Assigning a regex to `pattern` matches the input to the provided regex.
- If validations on a `<form>` do not pass, the user gets a message explaining why and the `<form>` cannot be submitted.


# Cheatsheets

## JavaScript and the DOM
![[javascript_javascript_and_the_dom.pdf]]

## DOM Events with JavaScript
![[javascript_dom_events_with_javascript.pdf]]

## HTML Forms
![[html_forms.pdf]]



