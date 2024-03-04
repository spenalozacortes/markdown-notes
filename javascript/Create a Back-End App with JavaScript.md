# JavaScript Conditionals and Functions
## Developing JavaScript Apps Locally
### Introduction to Testing with Mocha and Chai
 
#### Why write tests for code?
Tests are common in software engineering because they help to document the core functionality of the code and make sure that new features do not introduce breaking changes.

#### What is Unit Testing?
Unit testing means testing the behavior of code in small, independent units. Units are typically designed to be the smallest meaningful chunk of independently testable code. This is in comparison of integration testing, in which a set of modules are tested as a group.

#### Mocha and Chai, Test Suites and Test Cases
Mocha and Chai are two JavaScript frameworks commonly used together for unit testing.

Mocha is a testing framework that provides functions that are executed according in a specific order, and that logs their results to the terminal window.

When you read tests written in Mocha, you’ll see regular use of the keywords `describe` and `it`. These keywords, provided by Mocha, provide structure to the tests by batching them into test suites and test cases.

A _test suite_ is a collection of tests all relating to a single functionality or behavior. A _test case_ or a _unit test_ is a single description about the desired behavior of the code that either passes or fails. Test suites are batched underneath the `describe` keyword, and test cases are batched under the `it` keyword.

Additionally, Mocha provides tools for cleaning the state of the software being tested in order to insure that test cases are being run independently of each other. You might end up using other tools, to _stub_ or _mock_ the desired behaviors of other units that a given unit of code might interact with. The _independence of test cases_ is a key principle of unit testing, as it allows the cause of errors to be pinpointed more specifically if a test case fails, thereby speeding up the debugging process.

#### Assertions
The base component of test cases are _assertions_. Assertions are tied to particular values (whereas test cases are descriptions of behavior) and they will fail if the expected value does not match the actual value.

Every assertion in a test case must be met in order for the test case to pass.

Chai is an assertion library that is often used alongside Mocha. It provides functions and methods that help you compare the output of a certain test with its expected value.

Example of a Chai assertion: `expect(exampleArray).to.have.lengthOf(3);`

This code will check whether that the variable `exampleArray` has a length of three or not.

#### Failing and Passing Tests
Tests that will erroneously pass can be enormously misleading, and might lead to broken code getting merged and deployed.


### Reading Tests with Mocha and Chai

#### Example Tests
Let’s look through an abbreviated example test from the Rock, Paper, Scissors project to get some practice reading tests.

```js
describe('setPlayerMoves() - Main Functionality', function() { // this is a `describe` block, everything within this callback function is one test suite
  afterEach(clearMoves); // this is a `hook` that gets called between `it` blocks to reset the state
 
  it('a function called setPlayerMoves should exist', function() { // this is an `it` block, everything inside this function is a single test case
    should.equal(typeof setPlayerMoves, 'function'); // tests often start by checking that the right things exist and are of the right type
  });
 
  it('should set player one\'s moves with valid inputs', function() {
    setPlayerMoves('Player One', 'rock', 11); // here we call a function from the code we are testing that sets play one's move to rock with a value of 11
 
    should.equal(playerOneMoveOneType, 'rock'); // this is an assertion that tests that after the `setPlayerMoves()` function above is called, playerOneMoveOneType should equal `rock`
    should.equal(playerOneMoveOneValue, 11); // this assertion tests that setPlayerMoves can set the value of playerOneMoveOneValue
  });
})
```

#### Test Suites
Tests for one feature are grouped together in `describe` blocks. This group of tests, called a test suite, describes the “Main Functionality” of the `setPlayerMoves` function. Describe takes a string and a callback function: the string describes the feature or behavior being tested, and the callback function contains all of the code for the different tests being run.

You’ll see that inside the describe block, the `afterEach` function is called. This is called a hook, or a function that is called at certain points in the lifecycle of the process that it is running in. The afterEach function gets called right after each it block is run, and customizing this function allows us to reset things that we want to reset between different tests.

Here we call the function `clearMoves` which is a helper function that sets all of the moves back to undefined. It is written outside of any of the blocks, but used as a hook in many of them.

```js
function clearMoves() {
  playerOneMoveOneType = undefined;
  playerOneMoveOneValue = undefined;
  playerTwoMoveOneType = undefined;
  playerTwoMoveOneValue = undefined;
}
```

It’s important for tests to generally start from a clean slate and for each test to be independent of the others, because we want the errors that we get from our tests to give us a specific diagnosis of what is wrong with our code.

#### Test cases
Each `it` block describes more particular behavior to test. In the first `it` block, we test that `setPlayerMoves`actually exists and that it is a function so that it can correctly be used in the next block.

In the second `it` block, we call the function `setPlayerMoves`, which is a function from the code that we are testing from our Rock, Paper, Scissors game. After `setPlayerMoves` is called with the arguments, the variable `playerOneMoveOneType` should be equal to the string ‘rock’ and `playerOneMoveOneValue` should be equal to the number `11`.

#### Assertions
Any individual assertion where we are comparing the actual and expected values can be called an assertion. The words `should`, `expect`, and `assert` in the tests indicate that an assertion is being made.

Each `it` block test includes multiple assertions, because there are multiple scenarios and edge cases that we want to test for. The error messages that you get from failed tests will most likely point to one of these assertions.
 

### Running Tests and Interpreting Output with Mocha and Chai

#### How do I run tests?
To run tests for your projects, first open the root project directory in your terminal. If you haven’t already, run `npm install` to install all necessary testing dependencies. Finally, run `npm test` in your terminal. This command will run the code in your test script in the package json for your project.

#### I’m overwhelmed by the output!
Try appending `.only()` or `.skip()` to your describe or it blocks in order to only run certain tests or skip other certain tests. See the [mocha documentation](https://mochajs.org/#mochaopts) for more details.

#### What happens when my code itself throws an error?
If executing your code causes an error to be thrown, mocha will log that error in the place of an assertion error. Getting from an execution error to an assertion error usually means progress!

#### Edge Cases
Tests are often written for various edge cases. This is common, because poor handling of edge cases is responsible for a lot of bugs!

An example of a common edge case is: how does a function handle weird input? What happens if a function that expects to get a number is passed a string, or is passed no argument at all? Do we want to throw an error? Return undefined? Regardless, we want the decision to be consistent and well-documented.
 

# JavaScript Arrays, Loops, and Iterators

## Back-End Web Architecture
The front-end is the code that is executed on the client side. This code (typically HTML, CSS, and JavaScript) runs in the user’s browser and creates the user interface.

The back-end is the code that runs on the server, that receives requests from the clients, and contains the logic to send the appropriate data back to the client. The back-end also includes the database, which will persistently store all of the data for the application.

### What are the clients?
The clients are anything that send requests to the back-end. They are often browsers that make requests for the HTML and JavaScript code that they will execute to display websites to the end user. However, there are many different kinds of clients: they might be a mobile application, an application running on another server, or even a web enabled smart appliance.

### What is a back-end?
The back-end is all of the technology required to process the incoming request and generate and send the response to the client. This typically includes three major parts:

- The server. This is the computer that receives requests.
- The app. This is the application running on the server that listens for requests, retrieves information from the database, and sends a response.
- The database. Databases are used to organize and persist data.

### What is a server?
A server is simply a computer that listens for incoming requests. Though there are machines made and optimized for this particular purpose, any computer that is connected to a network can act as a server. In fact, you will often use your very own computer as server when developing apps.

### What are the core functions of the app?
The server runs an app that contains logic about how to respond to various requests based on the [HTTP verb](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods) and the [Uniform Resource Identifier (URI)](https://developer.mozilla.org/en-US/docs/Glossary/URI). The pair of an HTTP verb and a URI is called a _route_ and matching them based on a request is called _routing_.

Some of these handler functions will be _middleware_. In this context, middleware is any code that executes between the server receiving a request and sending a response. These middleware functions might modify the request object, query the database, or otherwise process the incoming request. Middleware functions typically end by passing control to the next middleware function, rather than by sending a response.

Eventually, a middleware function will be called that ends the request-response cycle by sending an HTTP response back to the client.

Often, programmers will use a framework like Express or [Ruby on Rails](https://www.codecademy.com/resources/blog/what-is-ruby-on-rails/) to simplify the logic of routing. For now, just think that each route can have one or many handler functions that are executed whenever a request to that route (HTTP verb and URI) is matched.

### What kinds of responses can a server send?
The data that the server sends back can come in different forms. For example, a server might serve up an HTML file, send data as JSON, or it might send back only an [HTTP status code](http://www.restapitutorial.com/httpstatuscodes.html). You’ve probably seen the status code “404 - Not Found” whenever you’ve tried navigating to a URI that doesn’t exist, but there are many more status codes that indicate what happened when the server received the request.

### What is a database, and why do we need to use them?
Databases are commonly used on the back-end of web applications. These databases provide an interface to save data in a persistent way to memory. Storing the data in a database both reduces the load on the main memory of the server [CPU](https://www.codecademy.com/resources/blog/what-is-a-cpu/) and allows the data to be retrieved if the server crashes or loses power.

Many requests sent to the server might require a database query. A client might request information that is stored in the database, or a client might submit data with their request to be added to the database.

### What is a Web API, really?
An API is a collection of clearly defined methods of communication between different software components.

More specifically, a _Web API_ is the interface created by the back-end: the collection of endpoints and the resources these endpoints expose.

A Web API is defined by the types of requests that it can handle, which is determined by the routes that it defines, and the types of responses that the clients can expect to receive after hitting those routes.

One Web API can be used to provide data for different front-ends. Since a Web API can provide data without really specifying how the data is viewed, multiple different HTML pages or mobile applications can be created to view the data from the Web API.

### Other principles of the request-response cycle
- The server typically cannot initiate responses without requests!
- Every request needs a response, even if it’s just a 404 status code indicating that the content was not found. Otherwise your client will be left _hanging_ (indefinitely waiting).
- The server should not send more than one response per request. This will throw errors in your code.

---

It’s worth noting that database queries are one of the slower steps in this process. Reading and writing from static memory is fairly slow, and the database might be on a different machine than the original server. This query itself might have to go across the internet!


# JavaScript Objects, Modules, and Browser Compatibility

## Browser Compatibility and Transpilation

### Browser Compatibility and Transpilation

#### Introduction
A website sends its code to a browser to be interpreted and run. People use different browser applications, each running a particular version, depending on when it was last updated.

As new features get added to JavaScript, browsers need to update to recognize and interpret those features. When a browser isn’t updated, it won’t see new syntax as valid JavaScript code, throwing an error. Users with outdated browsers can see a completely different (and likely broken) version of your site!

#### Browser Compatibility and Modern JavaScript Syntax
What JavaScript syntax is new? What is safe to use for any browser? How do we find this out?

These questions all have to do with _browser compatibility_, the idea that the browsers have to update to use the latest JavaScript features, some browsers haven’t done so yet, and some users haven’t updated their browser to the latest version. When we design a site for browser compatibility, we design our site to work correctly for as many different browsers and browser versions as possible. When thinking about browser compatibility, it is helpful to have a resource that will tell us which language features are supported by which browser versions.

Tools such as [caniuse.com](https://caniuse.com/) provide helpful browser compatibility information. On that site, you can search for language features and see:

- The browser versions that support those features
- Which browser versions don’t support those features
- What percentage of internet users are using these versions

#### Introduction to Transpilation
The newer features of JavaScript tend to make it easier to do things rather than add new features, a concept known as _syntactic sugar_. We can use older syntax to do the same things but it’s usually harder to write.

In order to make our new JavaScript syntax work on old browsers, we need to apply these kinds of transformations. Luckily, tools exist that can automate this process! While _compilation_ translates code from one language to another, _transpilation_ is a term for translating code to different formats of the same language. We can use a _transpiler_ to convert our modern code into a more compatible version.

Before we publish our code online, we take our source code and transpile it. This produces a set of output files that use more browser-compatible syntax. We publish the output files to our web server and can continue to develop our source code with any modern features we want to write!

#### Introduction to Babel
Babel is a popular transpiler for JavaScript that can be integrated into your projects!

---

In the terminal, do `npm run build`.

The build command transpiles the JavaScript files and stores the output in the **out** directory.

#### Babel Configuration
Babel is a Node package, so we would begin by initializing our npm project using `npm init -y`. This would set us up with a **package.json** file.

Next, we would want to install `@babel/cli` and `@babel/preset-env` as devDependences using `npm install --save-dev`. `@babel/cli` provides the main babel functionality as well as the command line interface. `@babel/preset-env` is a standard way of configuring Babel to transpile all of the common ES6 features, instead of having to list them one by one.

Babel is configured using a file named `.babelrc`. With `@babel/preset-env`, the content of this file is simple:

```
{
  "presets": ["@babel/preset-env"]
}
```

The **.babelrc** file is saying to use the `@babel/preset-env` configuration. This will transpile the latest adopted JavaScript features into code supported by older browsers.

Next, we want to define the command we will use to run Babel on our project. We will do this by defining a `build` command in the `scripts` section of our **package.json**:

```
"scripts" : {
  "build" : "babel src -d out"
}
```

This is using the `babel` command (from `@babel/cli`) with the first argument `src` specifying where the code is we want to run babel on. Then we provide the `-d` flag to specify where we want Babel to store the output, in this case, the **out** folder.

With the command defined, we can run Babel using the `build` command:

```shell
npm run build
```

#### Targeting Different Browsers
In addition to providing a fast way to configure Babel, `babel-preset-env` allows us to provide a list of browsers we want to be supported using a file named **.browserslistrc**.

Within this file there are many ways in which we can specify our target list of browsers. A good default configuration, which covers most of the browsers a developer could expect users to be on, can be specified with:

```
defaults
```

However, we can also customize this list. For example, we could make sure that our project is supported by the last two versions of Internet Explorer with:

```
last 2 Explorer versions
```

Or maybe you want to make sure your application supports 99.5% of the users of the internet:

```
cover 99.5%
```

The [browserslist documentation](https://github.com/browserslist/browserslist) provides additional syntax and examples for configuring **.browserslist**.

After defining **.browserslist**, you can list all browsers supported by your **.browserlist** file using the following command:

```shell
npx browserslist
```

#### Review
- Changes to JavaScript features over time can result in your modern website not working for users with older browsers, this issue is called _browser compatibility_.
- Modern JavaScript can be _transpiled_ into older syntax, making it run on older browser versions.
- A popular Node package for transpiling your project automatically is called _Babel_.
- Babel is configured to target a list of browsers or a percentage of internet users via a **.browserslistrc** file.

Babel can be set up by:

- Initializing your project with `npm init`
- Installing the necessary libraries as developer dependencies:
    - `@babel/cli`
    - `@babel/preset-env`
- Adding a `build` command in **package.json** specifying your source code directory and the output location.

Using Babel and transpilation, you can make your website more consistent across all of the ways users access the internet!
 

## What is CRUD?

### Create, Read, Update, Delete
When we are building APIs, we want our models to provide four basic types of functionality. The model must be able to Create, Read, Update, and Delete resources. Computer scientists often refer to these functions by the acronym CRUD. A model should have the ability to perform at most these four functions in order to be complete. If an action cannot be described by one of these four operations, then it should potentially be a model of its own.

The CRUD paradigm is common in constructing web applications, because it provides a memorable framework for reminding developers of how to construct full, usable models. For example, let’s imagine a system to keep track of library books. In this hypothetical library database, we can imagine that there would be a `books` resource, which would store `book` objects. Let’s say that the `book` object looks like this:

```
“book”: {
  "id": <Integer>,
  “title”: <String>,
  “author”: <String>,
  “isbn”: <Integer>
}
```

To make this library system usable, we would want to make sure there were clear mechanisms for completing the CRUD operations:

Create — This would consist of a function which we would call when a new library book is being added to the catalog. The program calling the function would supply the values for `“title”`, `“author”`, and `“isbn”`. After this function is called, there should be a new entry in the `books` resource corresponding to this new book. Additionally, the new entry is assigned a unique `id`, which can be used to access this resource later.

Read — This would consist of a function which would be called to see all of the books currently in the catalog. This function call would not alter the books in the catalog - it would simply retrieve the resource and display the results. We would also have a function to retrieve a single book, for which we could supply the title, author, or ISBN. Again, this book would not be modified, only retrieved.

Update — There should be a function to call when information about a book must be changed. The program calling the function would supply the new values for `“title”`, `“author”`, and `“isbn”`. After the function call, the corresponding entry in the `books` resource would contain the new fields supplied.

Delete — There should be a function to call to remove a library book from the catalog. The program calling the function would supply one or more values (`“title”`, `“author”`, and/or `“isbn”`) to identify the book, and then this book would be removed from the `books` resource. After this function is called, the `books` resource should contain all of the books it had before, except for the one just deleted.

### CRUD and REST
In a [REST environment](https://www.codecademy.com/article/what-is-rest), CRUD often corresponds to the HTTP methods POST, GET, PUT, and DELETE, respectively. These are the fundamental elements of a persistent storage system.

Imagine we are working with a system that is keeping track of meals and their corresponding prices for a restaurant. Let’s look at how we would implement CRUD operations.

#### Create
To create resources in a REST environment, we most commonly use the HTTP POST method. POST creates a new resource of the specified resource type.

For example, let’s imagine that we are adding a new food item to the stored list of dishes for this restaurant, and the `dish` objects are stored in a `dishes` resource. If we wanted to create the new item, we would use a POST request:

Request:

```
POST http://www.myrestaurant.com/dishes/
```

Body -

```
{
  "dish": {
    "name": “Avocado Toast”,
    "price": 8
  }
}
```

This creates a new item with a `name` value of `“Avocado Toast”` and a `price` value of 8. Upon successful creation, the server should return a header with a link to the newly-created resource, along with a HTTP response code of 201 (CREATED).

Response:

Status Code - 201 (CREATED)

Body -

```
{
  "dish": {
    "id": 1223,
    "name": “Avocado Toast”,
    "price": 8
  }
}
```

From this response, we see that the `dish` with `name` “Avocado Toast” and `price` 8 has been successfully created and added to the `dishes` resource.

#### Read
To read resources in a REST environment, we use the GET method. Reading a resource should never change any information - it should only retrieve it. If you call GET on the same information 10 times in a row, you should get the same response on the first call that you get on the last call.

GET can be used to read an entire list of items:

Request:

```
GET http://www.myrestaurant.com/dishes/
```

Response: Status Code - 200 (OK)

Body -

```
{
  "dishes": [
    {
      "id": 1,
      "name": “Spring Rolls”,
      "price": 6
    },
    {
      "id": 2,
      "name": “Mozzarella Sticks”,
      "price": 7
    },
    ...
    {
      "id": 1223,
      "name": “Avocado Toast”,
      "price": 8
    },
    {
      "id": 1224,
      "name": “Muesli and Yogurt”,
      "price": 5
    }
  ]
}
```

GET requests can also be used to read a specific item, when its `id` is specified in the request:

Request:

```
GET http://www.myrestaurant.com/dishes/1223
```

Response: Status Code - 200 (OK)

Body -

```
{
  "id": 1223,
  "name": “Avocado Toast”,
  "price": 8
}
```

After this request, no information has been changed in the database. The item with `id` 1223 has been retrieved from the `dishes` resource, and not modified. When there are no errors, GET will return the HTML or JSON of the desired resource, along with a 200 (OK) response code. If there is an error, it most often will return a 404 (NOT FOUND) response code.

#### Update
PUT is the HTTP method used for the CRUD operation, Update.

For example, if the price of Avocado Toast has gone up, we should go into the database and update that information. We can do this with a PUT request.

Request:

```
PUT http://www.myrestaurant.com/dishes/1223
```

Body -

```
{
  "dish": {
    "name": “Avocado Toast”,
    "price": 10
  }
}
```

This request should change the item with `id` 1223 to have the attributes supplied in the request body. This `dish` with `id` 1223 should now still have the `name` “Avocado Toast”, but the `price` value should now be 10, whereas before it was 8.

Response: Status Code - 200 (OK)

Body -

```
{
  "dish": {
    "name": “Avocado Toast”,
    "price": 10
  }
}
```

The response includes a Status Code of 200 (OK) to signify that the operation was successful. Optionally, the response could use a Status Code of 204 (NO CONTENT) and not include a response body. This decision depends on the context.

#### Delete
The CRUD operation Delete corresponds to the HTTP method DELETE. It is used to remove a resource from the system.

Let’s say that the world avocado shortage has reached a critical point, and we can no longer afford to serve this modern delicacy at all. We should go into the database and delete the item that corresponds to “Avocado Toast”, which we know has an `id` of 1223.

Request:

```
DELETE http://www.myrestaurant.com/dishes/1223
```

Such a call, if successful, returns a response code of 204 (NO CONTENT), with no response body. The `dishes` resource should no longer contain the `dish` object with `id` 1223.

Response: Status Code - 204 (NO CONTENT)

Body - None

Calling GET on the `dishes` resource after this DELETE call would return the original list of dishes with the `{"id": 1223, "name": “Avocado Toast”, "price": 10}` entry removed. All other `dish` objects in the `dishes` resource should remain unchanged. If we tried to call a GET on the item with `id` 1223, which we just deleted, we would receive a 404 (NOT FOUND) response code and the state of the system should remain unchanged.

Calling DELETE on a resource that does not exist should not change the state of the system. The call should return a 404 response code (NOT FOUND) and do nothing.
 

# SQL for Back-End Development

## Working with Multiple SQL Tables

### Multiple Tables Challenge

#### Code Challenge 8
Besides stacking one table on top of another, we can also use `UNION` to quickly make a “mini” dataset:

```sqlite
SELECT '2017-01-01' AS 'month'
UNION
SELECT '2017-02-01' AS 'month'
```

will produce:

|month| |
|---|---|
|2017-01-01 | |
|2017-02-01 | |


## Setting up SQLite

### Setting Up DB Browser

#### What is DB Browser
DB Browser is a visual tool used to organize commands sent to SQLite. With databases, it’s easy to lose track of commands that have been run. DB Browser lets you see exactly the sequence of commands you are executing before you run them. DB Browser will also allow you to see the column structure for the tables within the database you’re working with, so inserting data or other manipulation of data is more manageable and doesn’t require performing queries every time you need to remember the structure of your data.

#### Using DB Browser to Create a New Table
Steps: Creating a new database with DB Browser will open a `File` dialog box, where you can set where the SQLite database will live in your file structure. After creating a db, you will be presented with an interface for creating a table. Add a name for the table at the top, and then add and remove fields in the `Fields` window. Each field has a free-text name, a dropdown for its type, and four checkboxes for not-null, primary key, autoincrement, and unique attributes, as well as other parameters. You will see the SQL query that DB Browser executes to create this table update as you add information to this table. Update these and press “OK”. You will see the Database Structure tab of DB Browser refresh with the updated information. Note that no changes have been made to any database file yet, and queries are only executed by DB Browser when the “Write Changes” button is pressed. Press the “Write Changes” button and create your table.

#### Adding Data to a SQLite Table Using DB Browser
Steps: Switch from the Database Structure tab to the Browse Data tab. You can add a row to the table with the New Record button. Click it, and update the columns in the viewport as you would a spreadsheet. Remember that no data will be inserted into the SQLite database until the “Write Changes” button is pressed. Press that button and you will have successfully added a row to your table.


# Connecting JavaScript and SQL

## Learn Node-SQLite

### Learn Node SQLite

#### Opening A Database
The first order of business is to import the module that will facilitate this connection. Recall that to import a module in JavaScript we can use `require()` like so:

```js
const sqlite3 = require('sqlite3');
```

The code above gives us a JavaScript object, called `sqlite3` that we can interact with via _methods_. The first method we’re going to use on `sqlite3` is going to be the method that opens up a new database. In SQLite, a database corresponds to a single file, so the only argument required to open this database is the _path_ to the file that SQLite will use to save the database.

```js
const db = new sqlite3.Database('./db.sqlite');
```

This code will create a new database file, in the current folder, named `db.sqlite`. Then we’ll have a database to interact with!

#### Retrieving All Rows
To execute a query and retrieve all rows returned, we use `db.all()`, like so:

```js
db.all("SELECT * FROM Dog WHERE breed='Corgi'", (error, rows) => {
  printQueryResults(rows);
});
```

#### Retrieving A Single Row
`db.all()` is a useful tool to fetch all the data we have that meets certain criteria. But what if we only want to get a particular row? We could do something like this:

```js
db.all("SELECT * FROM Dog", (error, rows) => {
  printQueryResults(rows.find(row => row.id === 1));
});
```

In this example, we fetch all the rows from a database. Doing this populates a JavaScript variable, `rows`, that contains the results of our `SELECT` statement (all the rows from the database). We use JavaScript’s `.find()` method to find the row with an ID of 1. Then print out that row.

With a tiny database, this might be OK, but it will be a considerable and unnecessary load if the database is large in any sense. Luckily, we have a different method that will fetch a single row from a database: `db.get()`.

```js
db.get("SELECT * FROM Dog WHERE owner_name = 'Charlie'", (error, row) => {
  printQueryResults(row); 
});
```

Sometimes all we need to know is whether a record matching our query exists (for instance: the code above would answer the question “Does Charlie own a dog?” depending on whether or not `row` is `undefined`). Sometimes we know that there’s only a single row because we are searching for a specific ID. And sometimes we only want an example of a row that would match our description. In the code above we would only print information about one dog. To accomplish this, we use `db.get()` instead of `db.all()`.

It’s important to note that even if multiple rows match the query, `db.get()` will only return a single result. In the example above, if “Charlie” owns multiple dogs, the code provided will still only print information about one dog.

#### Using Placeholders
Now we know how to retrieve data from a database when we know exactly what we’re looking for. But we may not always know what values we will need to search for when writing our program. When we write a JavaScript function, we give the function _parameters_ that will have many different values when the function gets called. _Placeholders_ solve a similar problem in the world of SQL queries. Sometimes we’ll want to search our database based on a user’s submission. Or we might find ourselves wanting to perform a series of queries looping over some external data.

A placeholder is a part of our SQL query that we want to be _interpolated_ with a variable’s contents. We want the value of the JavaScript variable to be placed within the SQL query. To do this properly, we’ll need to pass a particular argument to our `db.run()` command that will tell it how to interpolate the query.

```js
const furLength1 = "short";
const furLength2 = "long";
const furColor1 = "brown";
const furColor2 = "grey";
 
const findDogByFur = (length, color) => {
  db.all(
    "SELECT * FROM Dog WHERE fur_length = $furLength AND fur_color = $furColor", 
    {
      $furLength: length,
      $furColor: color
    }, 
    (error, rows) => {
      printQueryResults(rows);
    }
  );
});
 
findDogByFur(furLength1, furColor1); // prints all dogs with short brown fur.
findDogByFur(furLength2, furColor1); // prints all dogs with long brown fur.
findDogByFur(furLength1, furColor2); // prints all dogs with short grey fur.
findDogByFur(furLength2, furColor2); // prints all dogs with long grey fur
```

As we can see in the example above, the power of placeholders is that we don’t need to know precisely the data we’re searching for at the time of writing our query. We can use these placeholders and then later, when we have values we want to find, we can plug them into the query. This is a highly effective tool that will allow us to harness our programming skills within our database queries.

#### Using db.run()
Not all SQL commands return rows, and in fact, some essential SQL commands do not. If we `INSERT` a row or `CREATE` a `TABLE` we will not receive a row in response. To perform SQL commands that do not return rows, we use `db.run()` to `run` the command. `db.run()` does not return a value, but, depending on the SQL command, it may attach properties to the `this` keyword within the scope of the callback. In some cases, like creating a table, `db.run()` will not modify `this`. In other cases, like when `INSERT`ing a row, a callback to `db.run()` will be able to access `this.lastID`, the ID of the last `INSERT`ed row.

```js
db.run('INSERT INTO TemperatureData (location, year) VALUES ($location, $year)', {
  $location: newRow.location,
  $year: newRow.year
}, function(error) {
  console.log(this.lastID);
});
```

#### Handling Errors Gracefully
Handling errors is an important part of the process when dealing with Node & SQL in particular. When our code throws an error, we should be able to handle it before it reaches our end users and incites panic and concern. We still want to know what happened, so that we can perform a suitable action based on the error that occurred — so we _catch_ the error.

For `db.run()`, `db.each()`, `db.get()`, and `db.all()`, the first argument to the callback will always be an `Error` object if an error occurred. If there is no error, this argument will be `null`. We can check if this error exists, and if it does exist, we can handle it.

```js
db.run('INSERT INTO TemperatureData (location, year, temp_avg) VALUES ($location, $year, $tempAvg)', {
  $location: newRow.location,
  $year: newRow.year,
  $tempAvg: newRow.tempAvg
}, function(error) {
  // handle errors here!
  if (error) {
    return console.log(error);
  }
  console.log(this.lastID);
  db.get("SELECT * FROM TemperatureData WHERE id = $id", {
    $id: this.lastID
  }, (error, row) => {
    printQueryResults(row);
  });
});
```

#### Using db.each()
While learning JavaScript, you likely learned about the powerful method `.forEach()` that allows us to process every element in an array separately. Now we will use a similar method that will enable us to process every row returned from a database query.

```js
db.each("SELECT * FROM Dog WHERE breed = 'Labrador'", 
  (error, row) => {
    // This gets called for every row our query returns
    console.log(`${row.name} is a good dog`);
  },
  (error, numberOfRows) => {
    // This gets called after each of our rows have been processed
    console.log(`There were ${numberOfRows} good dogs`);
});
```

In the code above we `SELECT` all the Labrador dogs from our `Dog` database. We offer affirmation to each of the animals individually and then announce how many received this praise in sum.

`db.each()` takes a query and a callback function that it performs on each row returned from the query. This is a useful technique for transforming or updating rows. This is also useful for memory management — we only have to look at one row at a time instead of trying to process every returned row at the same time. `db.each()` additionally takes an optional second callback function, which will be called when all of the queries are completed and processed.

#### Creating A New Table
Since creating a table is another operation that does not return a row, we can use the same `db.run()` we used to `INSERT` rows.

Notice there’s a statement declaring “DROP TABLE IF EXISTS” — this is because we want to make sure when we create our new table that we won’t run into an error telling us the table already exists (from previous times running our code).

#### Serial Queries
By default, the commands we issue to our database run in _parallel_. Every request we make gets sent to the database — which processes them all as quickly as it can, regardless of the order in which they got sent. This is usually a good thing because it means that we can get results faster, but in our case, we don’t want to try to `INSERT` data into a table that hasn’t been created yet. One way to avoid this issue is to write all of our code in nested callbacks, let’s take a look at how that might look:

```js
db.run("DROP TABLE Dog", error => {
  db.run("CREATE TABLE Dog", error => {
    db.run("INSERT INTO Dog (breed, name, owner, fur_color, fur_length) VALUES ('Dachschund', 'Spike', 'Elizabeth', 'Brown', 'Short')", error => {
    }
  }
}
```

As you can see, with this technique every command gets increasingly indented, which becomes a bit of an eyesore if we want to guarantee multiple things run chronologically. Another way of accomplishing this task is by using the `db.serialize()` method like so:

```js
db.serialize(() => {
  db.run("DROP TABLE Dog");
  db.run("CREATE TABLE Dog");
  db.run("INSERT INTO Dog (breed, name, owner, fur_color, fur_length) VALUES  ('Dachshund', 'Spike', 'Elizabeth', 'Brown', 'Short')");
});
```

In the previous example, we explicitly tell the database to:

- First, remove the table `Dog` if it exists.
- Second, create an empty table named `Dog`.
- Third, insert a new row into the table. In exactly that order without running any command until the previous one completes.

```js
const { calculateAverages, addClimateRowToObject, logNodeError, printQueryResults } = require('./utils');
const sqlite = require('sqlite3');

const db = new sqlite.Database('./db.sqlite');

const temperaturesByYear = {};

// start by wrapping all the code below in a serialize method
db.serialize(() => { 
  db.run('DROP TABLE IF EXISTS Average', error => {
    if (error) {
      throw error;
    }
  })
  db.run('CREATE TABLE Average (id INTEGER PRIMARY KEY, year INTEGER NOT NULL, temperature REAL NOT NULL)', logNodeError);
  db.each('SELECT * FROM TemperatureData',
    (error, row) => {
      if (error) {
        throw error;
      }
      addClimateRowToObject(row, temperaturesByYear);
    }, 
    error => {
      if (error) {
        throw error;
      }
      const averageTemperatureByYear = calculateAverages(temperaturesByYear);
      averageTemperatureByYear.forEach(row => {
        db.run('INSERT INTO Average (year, temperature) VALUES ($year, $temp)', {
          $year: row.year,
          $temp: row.temperature
        }, err => {
          if (err) {
            console.log(err);
          }
        });
      });
    db.all('SELECT * FROM Average',
    (error, row) => {
      printQueryResults(row)
    })
    });
  });
```

 
# Back-End Development Capstones

## X-Press Publishing

### Setup Project
1. Navigate to the root directory using a terminal and run `npm install`.

### Setup Server
2. In the project’s root directory, create a file named **server.js**.
3. Install and import the following packages: `body-parser`, `cors`, `errorhandler`, `morgan`, and `express`. When installing, ensure they get saved to the dependencies in **package.json**.
4. Create an instance of an Express app and save it to a variable.
5. Create a variable representing the port your server will listen on. This should be able to be optionally set to `process.env.PORT` if that value is set, for testing purposes. Otherwise, it should default to the port number of your choice (except `8081` as this is the port the test file uses).
6. Use the body-parser JSON, errorhandler, and CORS middleware functions for all routes in the server. Additionally consider setting up morgan logging to the dev setting for easier debugging.
7. Start your server using the port variable you declared earlier. Add a callback function that will log out a useful message to the console once your server is running.

### Create API Router
8. Since all routes in this project have paths starting at the `/api` subpath, we will create an API router that will prepend this path segment.
	Create a directory called **api/** in the root directory of the project. Within this directory, create a file called **api.js**.
9. Within **api.js**, import `express`. Then create an instance of an Express router and save it to a variable.
10. Export the router.
11. In **server.js**, import the API router and mount it at all routes starting at `/api`.

### Create Artist Table
12. Next, we will write the code to create the Artist table. In the root directory, open **migration.js**.
	Import `sqlite3`. It should already be installed from when you ran `npm install` at the beginning of the project.
13. Open the **database.sqlite** file as a sqlite3 database object and save it to a variable.
14. On the database object, run a SQLite command to create an Artist table (if it doesn’t already exist) with the following schema:

	- **id** - Integer, primary key, required
	- **name** - Text, required
	- **date_of_birth** - Text, required
	- **biography** - Text, required
	- **is_currently_employed** - Integer, defaults to `1`
15. Once you’ve finished writing the migration. Run `node migration.js` in a terminal to run the migration.
	Once the migration has finished running, open **database.sqlite** using DB Browser to ensure your table looks as expected. Then try inserting values into the table to ensure it works.

### Create Artist Routes
16. Now, let’s write the CRUD operations for `/api/artists`.
	Start by creating a file in the **api/** directory called **artists.js**. Within **artists.js**, import `express`, create an Express router, and export the Express router.
17. In **api.js**, import the artists router and mount it at `/artists`.
18. Back in **artists.js**, import `sqlite3` and open an instance of **database.sqlite**. 
19. Add a GET handler to the router for the `/` path (remember this router is already mounted at `/api/artists` so there is no need to add all of that boilerplate).
20. Within the GET `/` handler, execute a sqlite3 query that will retrieve all entries in the Artist table where `is_currently_employed` is equal to `1`. This will retrieve all currently-employed artists.
21. Within the callback of this query, check if there is an error. If so, pass it along the middleware chain to be dealt with by `errorhandler`.
	Otherwise, send a response containing a JSON body with a key of `artists` and a value of the retrieved artists, along with a status code of `200`.
22. Our GET, PUT, and DELETE route paths will have an `:artistId` parameter. For both, we will have to check that an artist with that ID exists and if not send a 404 response. Let’s add a router param to reduce boilerplate code.
	Add a router param of `artistId` to the router.
23. Within the artist param callback, execute a SQL query which will get the artist with the given ID.
24. Within the callback function of the sqlite3 query, send any SQL errors down the middleware chain. Otherwise, check if an artist was retrieved. If so, attach it to the request object as `artist` and move to the next function in the middleware chain. If not, send a 404 response.
25. Now we’re ready to write our GET `/api/artist/:artistId` handler.
	Register another GET handler at the above path segment. Our router param should already handle all of the necessary SQL and error-handling logic and attach the retrieved artist at `req.artist`.
	Within the handler’s callback function, return a 200 response with a JSON body containing a key of `artist` and a value of the retrieved artist.
26. Add a POST handler at the `/` path segment. Within the callback function of this handler, check that all required fields are present on the `artist` object of the request body (`name`, `dateOfBirth`, and `biography`). If not, send a `400` response.
27. Additionally check to see if `is_currently_employed` was set on the request’s `artist` object. If not, set it to `1`. This will simplify our SQL logic in the next step.
28. Next, execute a SQL query to create a new Artist with the supplied attributes.
29. In the callback function of this SQL query, check for errors and pass them down the middleware chain. If no errors are present, you will need to retrieve the newly-created artist from the database to return it in the response.
	Using the sqlite3 `lastID` attribute, write a SQL query to retrieve the new artist from the database. Then send it in the response body with a 201 status code.
30. Add a PUT handler at `/:artistId` to your router. Check to ensure all required fields are present in the request body, if not send a 400 response.
31. Execute a SQL statement to update the artist with the supplied artist ID to have the supplied updated attributes.
32. In the callback of the update statement, pass any errors down the middleware chain, if present. Otherwise, retrieve the newly-updated artist from the database and send it in the response with a 200 status code. 
33. Finally, let’s add our delete handler. This will be slightly different than a normal delete — instead of deleting the artist, we will mark them as unemployed.
	Add a delete handler at `/:artistId`. Within the handler’s callback function, run a SQL query to update the artist with the supplied artist ID to have `is_currently_employed` equal to `0`.
	Handle any errors and send successfully-updated artists with 200 responses.

### Create Series Table
34. Now, let’s move on to our next model. Open **migration.js** and write the code to create a new table called `Series`, if one doesn’t already exist. The table should have the following column properties:
	- **id** - Integer, primary key, required
	- **name** - Text, required
	- **description** - Text, required
35. Run **migration.js** via command line. Use DB Browser to ensure your table was properly set up - examining table properties and inserting data into the table.

### Create Series Routes
36. Let’s add our `/api/series` routes.
	Create **series.js** in the **api/** directory. In **series.js**, create and export an Express router.
	Import the router into **api.js** and mount it at `/series`.
37. In **series.js**, open a `sqlite3`database to your database or the provided test database.
38. Add a GET handler at `/` that will retrieve all existing series from the database.
	All errors should be properly handled and successfully retrieved series should be returned on the `series` property of the response object with a 200 status code.
39. Add a router param for handling the `seriesId` parameter. This router param should retrieve the specified series from the database and attach it as `series` on the request object. If a series with that ID does not exist, a 404 response should be sent.
40. Add a GET `/:seriesId` route. This route should return the retrieved series on the request object with a 200 status code.
41. Add a POST `/` route. This route should return a 400 response if any required fields are missing (`name` or `description`). Otherwise, it should add the new series to the database and return the newly-created series with a 201 status code, handling any errors along the way.
42. Add a PUT `/:seriesId` route. This route should return a 400 response if any required fields are missing (`name` or `description`). Otherwise, it should add the new series to the database and return the newly-updated series with a 200 status code, handling any errors along the way.
	We will wait to write the DELETE `/:seriesId` route until we’ve added issues, as checking for whether or not a series has issue prior to deletion is a large part of the logic.

### Create Issue Table
43. Let’s move on to our last model. Open **migration.js** and write the code to create a new table called `Issue`, if one doesn’t already exist. The table should have the following column properties:
	- **id** - Integer, primary key, required
	- **name** - Text, required
	- **issue_number** - Integer, required
	- **publication_date** - Text, required
	- **artist_id** - Integer, foreign key, required
	- **series_id** - Integer, foreign key, required
44. Run **migration.js** via command line. Use DB Browser to ensure your table was properly set up - examining table properties and inserting data into the table.

### Create Issue Routes
45. Let’s add our `/api/series/:seriesId/issues` routes.
	Create **issues.js** in the **api/** directory. In **issues.js**, create and export an Express router.
	Import the router into **series.js** and mount it at `/:seriesId/issues`.
	Since you’ll need to access information about the specified series from the issues router, you’ll need to merge parameters. Add the appropriate parameter to your issue router instantiation to enable merging parameters.
46. Add a GET handler at `/` that will retrieve all existing issues of the specified series from the database.
	All errors should be properly handled and successfully retrieved issues should be returned on the `issues` property of the response object with a 200 status code.
47. Add a POST `/` route. This route should return a 400 response if any required fields are missing (`name`, `issueNumber`, `publicationDate`, or `artistId`). Additionally, the route should return a 400 response if an artist with the provided artist ID does not exist. Otherwise, it should add the new issue to the database and return the newly-created series with a 201 status code, handling any errors along the way.
48. Add a route param for `:issueId`. This param should check to see if an issue with the supplied issue ID exists. If so, it should continue to the next middleware function in the middleware stack. If not, it should return a 404 response.
49. Add a PUT `/:issueId` route. This route should return a 400 response if any required fields are missing (`name`, `issueNumber`, `publicationDate`, or `artistId`). Additionally, the route should return a 400 response if an artist with the provided artist ID does not exist. Otherwise, it should update the issue in the database and return the newly-updated series with a 200 status code, handling any errors along the way.
50. Add a DELETE `/:issueId` route. This route should delete issue with the specified issue ID from the database. The route should handle any errors and send a 204 response upon successful deletion.
51. Finally, let’s write our DELETE `/api/series/:seriesId` route. In **series.js**, add a DELETE `/:seriesId` route. This route should check to ensure the specified series has no related issues in the database. If it does, the handler should return a 400 response. If not, the handler should delete the series from the database and send a 204 response.
