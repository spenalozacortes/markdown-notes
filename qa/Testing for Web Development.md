# Feature Testing with TDD

## TDD Feature-Level Tests

### Introduction
Starting at the feature level of the pyramid (going outside-in) means you begin by writing tests that inform implementation of the code that a user’s browser renders. These tests involve the aspects of your project that users will see and interact with.

### Feature Test Toolbelt

#### Chai
Node.js has a default assertion library that provides enough functionality to write basic test code. The [Chai testing library](http://chaijs.com/) extends the types of assertions we can make.

Chai is an assertion library for Node.js and browsers that can be paired with any JavaScript testing framework.

#### PhantomJS
[PhantomJS](http://phantomjs.org/) is a headless browser scriptable with a JavaScript API, which allows us to write tests that mimic user interaction and then evaluate the results. It does not require us to render the application in a browser.

A browser runs “headless” when it doesn’t render anything to the screen, but runs in the background.

#### WebdriverI/O
[WebdriverIO](https://webdriver.io/docs/what-is-webdriverio) provides [methods](https://www.codecademy.com/resources/docs/javascript/methods) that allow us to programmatically interact with the user-facing elements of our app in the headless browser that PhantomJS runs.

#### Toolbelt High-Level Summary
Phantom allows us to run an instance of a headless browser so you can run tests that mimic user interaction with a web application. WebdriverIO provides the methods to interact with browser values programmatically. We can make assertions against these tests using the Chai assertion library.

---

The first line of code, which makes Chai’s assertion library available for us to use in our tests.

```js
const {assert} = require("chai")
```

### Feature Test I
Feature tests exercise behavior by simulating a user navigating the application in a web browser.

Imagine we wanted to create a simple web-based poetry writing application.

The first feature test we want to write is to check our application’s _empty state_. The functionality we want to test is:

- When a `user visits the homepage`, the `poems section is empty`

We want to make sure that when there are no poems in the database, there are no poems rendered on the homepage. This is the application’s _empty state_.

The testing suite for our poetry app would begin with nested describe blocks like this:

```js
describe('Poetry web app', () => {
  describe('user visits root', () => {

  });
});
```

The term ‘root’, refers to our application’s entry point, which in this example is the home page that users will visit in their browser.

Next, we add an `it` block to describe the behavior we want to test in our app:

```js
describe('Poetry web app', () => {
  describe('user visits root', () => {
    it('page starts blank', () => {

    });  
  });
});
```

#### The Plumbing
Next, we reach for our feature testing toolbelt. We start by using the global `browser` variable that is provided by WebdriverI/O.

The `browser` variable is powerful because it gives us access to the browser that Phantom is running in the background. We can simulate a user interacting with our website by calling different [methods](https://www.codecademy.com/resources/docs/javascript/methods) on the global `browser` variable in our test suite.

For example, we can use `browser.url()` to simulate a user visiting the home page of our application, which is the first behavior we want to test.

The `.url` method navigates to the URL that is passed to it as an argument. The following line of code would navigate to the Codecademy website in the Phantom browser.

```js
browser.url('https://www.codecademy.com')
```

In the case of our poetry web app, we will pass in `'/'` as the argument, which will point the browser to the root file of our project, which in this case is our **index.html**.

```js
describe('poetry web app', () => {
  describe('user visits root', () => {
    it('page starts blank', () => {
      browser.url('/');
    });  
  });
});
```

### Feature Test I: Assert
The last thing our test needs is an assert statement to verify that the behavior we expect is equal to the actual behavior of our code.

We want to make sure our app is in an _empty state_.

We can write a test for this behavior by deciding that poems will be listed in an HTML element with an `id` attribute set to `poems`. Then, write an assert statement to verify that the element with the ID `poems` is empty.

We can do this using the Chai `assert.equal` method, which evaluates if the two arguments are equal.

```js
assert.equal(browser.getText('#poems'), '')
```

Because we will render the poetry onto the page as text, we can evaluate the contents of the HTML element as a string.

The `.getText` method, from WebdriverI/O, gets the text content from the selected DOM element.

Here we are using `browser.getText()` to evaluate if the text in the element with the ID `poems` is equal to an empty string.

```js
describe('User visits root', () => {
  describe('without existing poems', () => {
    it('page starts blank', () => {
      browser.url('/');

      assert.equal(browser.getText('#poems'), '');
    });
  });
});
```

### Feature Test I: Passing
Now that we have written our first test with an assert statement, we will run the test and use the error message to drive the next step in our development process.

When executing a feature test that fails, [errors](https://www.codecademy.com/resources/docs/javascript/errors) will have messages that discuss the failure in terms of HTML (i.e. that text or button that you said would be on the page isn’t on the page) or HTTP (i.e. the request that this page made resulted in a 404 HTTP status because the route you requested didn’t exist).

The error message describes the issue in terms of HTML elements and tells us that the element we are expecting does not exist on our page. This is because we have not yet created the HTML in our **index.html** file.

Using a strict TDD approach, we would write just enough HTML code to make our test pass.

```html
<section id="poems"></section>
```

### Feature Test II: Setup
Returning to our poetry app demo, we want to write a test to check if the application saves the title and text of a user’s poem when they press the submit button.

The functionality we want to test is:

1. The user enters text into a text input element (the poem)
2. The user enters text into a second text input element (the title of the poem)
3. The user presses a submit button

Adding the `describe` and `it` blocks for this second test would look like this:

```js
describe('demo poetry web app', () => { 
    it('saves the user poem and title', () => {

    });
  });
```

Next, we want to write the setup, exercise, and verification phases of our test.

In the setup phase for this test, we create [variables](https://www.codecademy.com/resources/docs/javascript/variables) to represent a user’s input to the title and poem fields on the home page.

```js
  const title = 'Words Birth Worlds';
     const poem = 'Our words are marvelous weapons with which we could behead the sun';
```

### Feature Test II: Exercise
We will use the `.setValue` method, which sends a sequence of keystrokes to an element, based on a string argument.

We will use `.setValue()` to mimic a user entering the title and poem into the corresponding HTML input elements at the root of our web app.

The first argument passed to `.setValue()` is the CSS selector that references an HTML element, and the second argument is the value you want to assign that element.

```js
browser.setValue('input[id=title]', title);
browser.setValue('textarea[id=poem]', poem);
```

In the example above, a text input with the ID of `title` will be set to a value of `title`. Also, the textarea with ID `poem` will be set to the value `poem`.

To complete the exercise phase of our test we would use the `.click` method to mimic a user clicking on a submit button.

```js
browser.click('input[type=submit]');
```

### Feature Test II: Verify
In the case of our poetry app, we want to verify that once a user submits a poem, the section of the app’s webpage that we have decided will display the poems includes that poem.

To add an `assert` statement to evaluate the behavior of our feature, we will use the `browser` variable, and `.getText()` to return the text contents of the element, with the `id` `poem`.

The Chai Assertion Library allows us to use the `.include` method to check if the string that is returned from `.getText()` includes the substrings of the title and poem that the user has submitted:

```js
assert.include(browser.getText('#poems'), title);
assert.include(browser.getText('#poems'), poem);
```

The `.include()` method works like this:

```js
assert.include(haystack, needle)
```

### Review
In this lesson, we have been writing tests at the top level of the TDD Testing Pyramid, which concerns the part of the app that users interact with. To make our feature test pass and get back into the green we need to drop down to the server level — which concerns the part of the application that makes ‘POST’ requests to the server.

- When developing a new feature and practicing outside-in development, feature tests are where we’ll typically start.
- Feature tests often incorporate every layer of the application and — using WebDriverI/O and Mocha — exercise features in the same way that a human user would. They’re a good tool for reproducing end-user behavior.
- WebDriverI/O is a Node package that interacts with a “headless” instance of PhantomJS.
- Feedback from feature tests is usually in terms of HTML (i.e. that text or button that you said would be on the page isn’t on the page).
- Because feature tests typically hit every layer of a developer’s stack, they are slower than tests at lower layers, and errors thrown in feature tests can be difficult to interpret and provide little guidance on what the developer can do to resolve them.
- Their value, however, is in developer confidence that the software functions as expected.


# Outside-in TDD

## The Testing Pyramid
Throughout this article, we will use the following example to illustrate the testing needs in each layer of a full stack web application.

_Imagine you are developing a movie blog and want to build a feature that allows users to comment on your posts. Any comment can be read by any other user on the website._

This is how a user may interact with your web application:

- _The browser renders comments below the blog post._
- _When a user wants to post a comment, they enter text into a box and click the Submit button._
- _Your web application transmits the comment to your server._
- _Your server checks if the POST has any errors. If it does not, it creates a new comment and saves it to the web application’s database._
- _The next user to arrive will see the last comment at the top of the list of comments._

### Integration Tests and Unit Tests
We call some web applications “full stack,” because we think of the view, server, and model/database as separate layers — each one sitting on top of and relying on the one below it. This structure impacts the types of tests that we can run against our web application.

Developers think of tests as fitting into a spectrum. The spectrum represents the amount of the web application that a test exercises.

![[Pasted image 20230830142354.png]]

_Unit tests_ are isolated and fast tests that check one small behavior within your web application.

For example, we want to test whether our database can save a comment. Saving does not involve the view or server. We can create a test that writes directly to the database, and the test itself doesn’t need to know about the other layers.

A test like this is fast, but only gives you confidence that a small slice of your system is working as intended.

**System tests** _System tests_ are a group of fully integrated tests that exercise your entire web application.

For example, we want to test whether our blog renders with the correct post and comments. We can write a test that checks whether a browser renders a stored blog post. This test exercises every layer of the web application:

- The database stores the blog post.
- The server sends the HTML to the browser.
- The browser renders the view.

A test like this is slow and less descriptive but provides you with confidence that a large slice of your system is working as intended. **Integration tests** _Integration tests_ include everything between unit tests and system tests. They exercise multiple parts of the web application, often in different layers.

For example, an integration test may check whether your web application can save a server-generated comment to the database. This test integrates two layers of your web application:

- The server receives the comment and sends it to the database.
- The database stores your comment.

Developers often call tests like the one above end-to-end tests, because they start in the browser (one end) and traverse the stack to the database (other end).

Integration tests are faster than system tests, but slower than unit tests. They provide less confidence (that your feature works as expected) than system tests and more confidence than unit tests.

### The Testing Pyramid
The testing pyramid is an approach to structuring your test suite.

Browser-level integration tests sit on the top of the pyramid. This layer is the narrowest because it should have the fewest number of tests — the slow nature of browser-level tests make them more expensive than server-level tests.

While server tests don’t need to interact with the browser, they usually exercise parts of the model or database. They sit close to the middle of the spectrum between unit and system tests. They provide a moderate level of confidence as they may exercise multiple layers of the stack. Server tests are more expensive and provide less specific error messages than model tests.

Compared to browser and server tests, model and database tests exercise a smaller portion of the stack. They provide the most specific feedback, but not much confidence that the whole system is working as expected. Because they are the cheapest, you can write a lot of them without significantly slowing the amount of time it takes to run your test suite.

![[Pasted image 20230831114119.png]]

### Example Testing Suite

Most sites that support user commenting set a limit on the number of comments that load when you arrive on the page. If an article has 300 comments, rendering the entire list would take too long and make the web page difficult to navigate.

Imagine that your web application already has a feature-level integration test that checks if the browser renders comments to the site.

Let’s consider the most efficient set of tests we could write to check that the browser renders only the last ten comments.

Because you already have a test at the feature layer, you decide to start by writing a server test. The test will check if:

- Calling a `Comments.latest` method returns a list of comments from your database that is ten items or less.

The server and feature level tests provide you with confidence that your web application returns comments that don’t exceed the maximum length. However, they don’t provide any information about which comments the model layer returns.

Once, you have the confidence that your model layer returns ten comments or less from your database, you can check the specifics of the `Comments.latest` method. You can check if:

- A database with more than ten comments returns only ten.
- A database with less than ten comments returns all of the comments.
- A database with zero comments returns zero comments.
- The list of comments is in reverse chronological order.

To support a ten-comment limit, we added one server test and four model tests. Notice, our tests provide greater detail as we get closer to the database. The tradeoff is that each test at the model layer provides us with less confidence that the system is working as expected.

### Conclusion
When making decisions about how to test a feature, you should ask yourself a few of these questions:

- Is a feature-level integration test necessary?
- Can I test the same behavior with server and model layer tests?
- How much confidence do I have with the server and model layer tests?
- How long does the feature test take? Will that impact my team’s workflow?


## Outside-In Test-Driven Development

### Red, Green, Refactor
Test-driven development (TDD) is the process of writing tests before implementation code. You use the feedback from your tests to inform the implementation of a feature or outcome.

A common approach to TDD is the red, green, refactor cycle. When you write a test before the implementation exists you start “in the red” phase, because your test fails and outputs a red error message. Next, you write the minimum implementation code to get your test to pass. This puts you “in the green” phase, because your test passes and outputs a green message.

Once you are in the green, you should consider whether your implementation is the best or most efficient approach. If you think your code could be written more efficiently or cleaner, then you enter the refactor phase. You can refactor your code with confidence, because you have tests that cover the expected behavior.

### Outside-in TDD
Outside-in TDD is an approach that developers use to build full-stack web applications. It leverages the same red, green, refactor steps that we covered above, but with one caveat — a failing test does not always inform you to write new implementation code. Instead, it may require that you implement new functionality at a different level.

You start at the top of the stack, the view, and write tests as you work your way towards the database layer.

If a test pushes you to a lower level, you restart your red, green, refactor cycle by writing a new test. This test informs the implementation at your new layer. You continue the TDD cycle at this lower level until:

- You need to drop another layer to implement the desired behavior
- You have addressed the reason for dropping to the current layer

Once you address the reason for dropping a layer, you can start working your way back up the testing pyramid. If you’re in the model/database layer, you step up to the server, and run your server tests to see if you get a different response. The response should be one of the following:

- The test passes — you can start another red, green, refactor cycle at the server level or step up to the view layer.
- The test fails — the server test that pushed you to the model layer fails, but for a different reason. This is common, and indicates that you’re making progress. This failure may indicate that you need to write additional implementation at the server level, or drop back to the model.

### Outside-in Example
We’re going to use the following as an example of how to develop a new feature with outside-in TDD: _You have a movie blog and want to develop a feature that renders user comments under your blog posts._ _The application should render no more than ten comments when a user lands on the web page._ _The application should present the comments in reverse chronological order (i.e. the most recent comment should be first)._

Let’s assume the web application generates HTML at the server — any updates to the view require implementation at the server level.

#### Feature Testing
The first step is to write a feature test that checks if your web application is rendering comments to the browser. Let’s use the following outside-in TDD approach:

1. Write a test that checks for the presence of a comment under a blog post.
2. The test fails, because your web application does not render comments.
3. Because your web application generates HTML at the server layer, you drop to the server to address the error.

Although we could continue to write feature tests to check for the number of rendered comments, we know server tests are cheaper, so we can test those details when we drop a layer.

#### Server Testing
At the server layer, we start by writing a test that informs the implementation of our server-generated HTML. Because our web application renders unique comments from the database, we want to check that the server-generated HTML is dynamic.

1. Write a test that checks for the presence of a dynamically generated comment element in the server HTML.
2. The test fails, so we add implementation for a server-generated comment.
3. Once we’re in the green and consider refactoring, we want to write a test that calls a method at the model layer, let’s call it `Comment.latest()`. At the server layer, we’ll check if the method returns comments from the database.
4. Because this method doesn’t exist, we must drop to the model/database layer.

#### Model and Database Testing
At the model layer, we start by writing a test that informs the implementation of our `Comment.latest` method. This method requires that you interface with the web application’s database.

1. Write a test that checks if the `Comment.latest` method returns ten comments when the database has eleven comments.
2. Implement the `Comment.latest` method to return ten comments, so the test is green.
3. Once you’ve considered refactoring, write a test that checks whether the method returns the last ten comments in reverse chronological order.
4. Implement and refactor
5. Write a test that checks if `Comment.latest()` returns an empty array when your database is empty.
6. Implement and refactor
7. Write a test that checks if `Comment.latest` returns the correct number and order of comments when your database has between zero and ten comments in it.
8. Implement and refactor

#### Taking Stock
At this point, your entire test suite should be green. You have written seven new tests, and the implementation code to make them pass — your web application should render the last ten comments from your database in reverse chronological order.

Let’s take stock of our seven new tests:

1. **Feature:** Comments are rendered to a user’s browser.
2. **Server:** The server generates an HTML field for comments.
3. **Server:** The server has access to ten comments from the database.
4. **Model:** The `Comment.latest` method returns ten comments from your database.
5. **Model:** The `Comment.latest` method returns the last ten comments in your database in reverse chronological order.
6. **Model:** The `Comment.latest` method returns an empty array when your database has zero comments.
7. **Model:** The `Comment.latest` method returns all of the comments when your database has between zero and ten comments.

#### Refactoring Your Test Suite
The way you approach refactoring will vary based on the size and types of tests in your suite. One guiding light in refactoring is to optimize the suite for confidence and speed. Because we used TDD to implement our comment feature, we should feel confident that our comments are working as expected, and the feature is fully covered.

Consider the questions below when deciding how to refactor your suite:

- How much longer does it take to run my test suite with these new tests?
- Is the additional amount of time that your test suite takes to run acceptable?
- Is there overlap between any of my new tests?
- Is there overlap between my new tests and existing tests?


# Model Testing with TDD

## Mongoose Fundamentals

### Intro To Databases
Mongoose is a Node package that interacts with a running MongoDB database.

#### What is Data?
Data in the context of software and web development is digital information.

#### What is a Database?
A database is a structured set of data held in a computer.

Databases support [storage](https://www.codecademy.com/resources/docs/javascript/storage) and manipulation of data. For a web application to have persistence, a developer uses a database to store data. The developer can write [methods](https://www.codecademy.com/resources/docs/javascript/methods) to create, read, update, and delete information in the database.

### Mongoose Collections & Documents
Mongo stores data in ‘binary’ [JSON](https://www.codecademy.com/resources/docs/javascript/json) (BSON) documents. BSON documents have a similar structure to JavaScript [objects](https://www.codecademy.com/resources/docs/javascript/objects).

MongoDB stores _documents_ in a _collection_. A MongoDB database is made up of these collections of documents.

A Mongo collection is like a table in a spreadsheet or relational database — each document is like a row in the spreadsheet.

Documents contain one or more key/value pairs. Each key has a corresponding value of a specified data type, like array, number, or string. MongoDB organizes documents with similar structure into collections.

### Schemas
Mongoose is a JavaScript library that provides [methods](https://www.codecademy.com/resources/docs/javascript/methods) to interact with a MongoDB database. Mongoose translates JavaScript [objects](https://www.codecademy.com/resources/docs/javascript/objects) (JSON) to BSON data in a MongoDB database, and vice versa.

Mongoose interactions are based on Schema and Model declarations.

- A _Schema_ defines the shape of the documents within that collection.
- A _Model_ maps to a MongoDB collection and its documents.

#### Mongoose Schema
Remember, each record in a MongoDB database is a document with key/value pairs as entries. Using Mongoose’s `Schema`, we can set the structure of those documents dynamically.

Imagine you were creating a Schema for the database of a web-based poetry application where you could both write and publish poems. Each key in our `poemSchema` will define a property in our documents which will be cast to its associated SchemaType.

```js
const poemSchema = new mongoose.Schema({
  title: String
})
```

Each document that is derived from the `poemSchema` above will have a `title` property with a string saved to it.

Mongoose will cast mismatched [data types](https://www.codecademy.com/resources/docs/javascript/data-types) to the specified SchemaType. For example, if we entered the number `1` as a title for a poem, Mongoose would cast the entry so that it entered that database as a string `"1"`. Using casting, Mongoose ensures that string properties are assigned [strings](https://www.codecademy.com/resources/docs/javascript/strings) values.

### Paths
The key-value pair in a schema is called a path. Paths define the name and type of fields in a MongoDB document.

```js
const poemSchema = new mongoose.Schema({
  title: String,
  body: [String],
  published: Boolean,
})
```

The `[String]` schema type, assigned to `body`, means a document that is derived from the `poemSchema` schema can store an array of strings to the `body` field.

[Paths in Mongoose can have many data types](http://mongoosejs.com/docs/schematypes.html). Besides data types like string, integer, boolean, and array, Mongoose also provides:

- Timestamp − timestamp. This can be handy for recording when a document has been modified or added.
- Object ID − This datatype is used to store the document’s ID.

### Validators
Often, we want to specify more than just the type of a path — we can use _validators_ to ensure other aspects of a document’s input value.

Data validation is intended to provide guarantees about user input. Mongoose has several built-in validators.

You can add required validators to our `Schema` in an object that you pass to the path:

```js
const poemSchema = new mongoose.Schema({
  title: {
    type: String,
    required: true
  },
  body: {
    type: [String],
    required: true
  },
  published: {
    type: Boolean,
    required: true
  },
})
```

If the `required` property is true, then it is a required field when you save to the database.

If you save a document with an invalid path value, you will receive this error message ``Path `title` is required.``. You can define a custom error message like this:

```js
const poemSchema = new mongoose.Schema({
  title: {
    type: String,
    required: 'Title is required!'
  }
})
```

[You can learn more about mongoose validators in their documentation.](http://mongoosejs.com/docs/validation.html)

### Models
To use our `poemSchema` definition we need to convert our `poemSchema` into a `Model` we can work with. `Schemas` provide the definition for a model. A model maps to a collection in your MongoDB database.

Models are defined by passing a Schema instance to `mongoose.model` like this:

```js
mongoose.model(modelName, schema):
```

The first argument is the singular name of the collection your model is for. The second argument is your previously created `Schema`. In the case of our poetry web app, turning our `schema` into a `model` would look like this:

```js
const Poem = mongoose.model('Poem', poemSchema); 
```

Models are [constructors](https://www.codecademy.com/resources/docs/javascript/constructors) that we define based on our `Schema`. They represent documents which can be saved and retrieved from our database. All document creation and retrieval from the database is handled by these models.

### Create
Our model is a class with properties that we define in our schema. We can construct documents as instances of our model. Creating documents and saving them to the database can be done by calling `.create()` on our model.

```js
const Poem = mongoose.model('Poem', poemSchema);

const poemProperties = {
    title: "Rewrite Reality" ,
    body: ["Re-imagine the consumption of the stagnant status quo", 
           "No matter how nice you dress", 
           "The emperor is still wearing no clothes"],
    published: false
}

runWithDatabase(async () => {
  // Create and save a document
  await Poem.create(poemProperties);
});
```

The `runWithDatabase` function is designed to accept a method as input, and run it after we connect to a database and before we disconnect from it. If you want to learn more about the [methods](https://www.codecademy.com/resources/docs/javascript/methods) in **database.js**, read the documentation for:

- [Connect](http://mongoosejs.com/docs/api.html#index_Mongoose-connect)
- [Drop](https://docs.mongodb.com/manual/reference/method/db.dropDatabase/)
- [Disconnect](http://mongoosejs.com/docs/api.html#index_Mongoose-disconnect)

This would create a new document in our database, with the paths and properties defined in the code above. 

### Queries
If we wanted to search for the poem that we saved to the database, we could write a Mongoose query and call `.findOne()` on our `Poem` model:

```js
runWithDatabase(async () => {
   Poem.create(poemProperties)

   const poemMatch = await Poem.findOne({ title: 'Rewrite Reality' });

   console.log(`Found poem: ${poemMatch.body}`);
});
```

`.findOne()` returns a document that has a `title` path with the value `'Rewrite Reality'`. We confirm this by using `console.log()` to see the value of the path `body` for the returned document.

This is good when we are looking for one document. What if we wanted to find all the documents that matched a specified criteria? We can use [`.find()`](https://www.codecademy.com/resources/docs/javascript/arrays/find), which returns an array of all the documents that match the argument passed to it.

```js
runWithDatabase(async () => {
  Poem.create(manyPoems);

  let publishedPoems = await Poem.find({ published: true })

  // Check that it works by logging the number of returned documents
  console.log(`Published Poems: ${publishedPoems.length}`)
});
```

---

`$lt` selects the documents where the value of the field is less than (i.e. <) the specified value. The syntax is:

`.find({field: {$lt: value} })`.

### Methods
Mongoose supports the creation of [methods](https://www.codecademy.com/resources/docs/javascript/methods) on both instances of documents and collections of documents (the model).

- `.statics()` adds static “class” methods to the model.
- `.methods()` adds an instance method to documents.

#### Model Methods — .statics()
For example, in our poetry app we could use `.statics()` to create a method named `firstAlphabetically`.

```js
const poemSchema = new mongoose.Schema({
...
)}

poemSchema.statics.firstAlphabetically = function(callback) {
  return this.findOne({}).sort('title').exec(callback);
}
```

The method is part of the model, which in this example would return the first document, after sorting the values of the `title` path alphabetically.

In order to use the new `.firstAlphabetically` method, we would call it inside `runWithDatabase()` on the `Poem` model like this:

```js
const Poem = mongoose.model('Poem', poemSchema);

runWithDatabase(async () => {
  Poem.create(properties));
  
  const firstAlpha = await Poem.firstAlphabetically();
  
  console.log(`The first poem alphabetically is: ${firstAlpha.title}. It goes like this: ${'\n'} ${firstAlpha.body}`);
  });
```

#### Document Methods — .methods()
Instances of a model are documents. Documents have many of their own built-in instance methods. It is also possible to create custom document instance methods. Below, we create a method for our poem example to change the `published` path value to `true` on any document in the database.

```js
const poemSchema = new mongoose.Schema({
...
)}

poemSchema.methods.publish = function(callback) {
  this.published = true

  return this.save();
}
```

`.save()` writes the current JavaScript object as a MongoDB document.

Inside `runWithDatabase()` we could call `.publish()` on a document like this:

```js
const Poem = mongoose.model('Poem', poemSchema);

runWithDatabase(async () => {
  Poem.create(properties));
  ...
  const publishIt = await Poem.findOne({ title: 'Rewrite Reality' });
  console.log(publishIt.published)
  
  await publishIt.publish();
  console.log(`${publishIt.title} has had its publish field changed to ${publishIt.published}`)
  });
```

Here we use `.findOne` to locate the poem, and then `console.log()` the initial `publish` value, which is false. We call `.publish()` on it and `console.log()` again to see that it changed.

### Review
- Mongoose is a Node package that interacts with a running MongoDB database.
- MongoDB stores documents in collections and collections of documents in databases. Each document has key-value pairs as entries.
- Using a `Schema`, we can set the structure of documents dynamically, using `paths` with schema types and validators.
- Models are JavaScript classes that we compile from our `Schema` definitions.
- You can use models to create, read, update, and delete documents from a database.
- You can query a database using [`.find()`](https://www.codecademy.com/resources/docs/javascript/arrays/find) and `.findOne()`. [Mongo also provides query operators to allow for more complex queries.](https://docs.mongodb.com/v3.4/reference/operator/query-comparison/)

Mongoose also allows for the creation of [methods](https://www.codecademy.com/resources/docs/javascript/methods) associated with a database:

- `.statics()` adds static “class” methods to the Models itself.
- `.methods()` adds an instance method to documents.


## Model Testing Patterns

### Introduction
Models represent the entities and interactions in a web application’s problem domain: the area of knowledge surrounding a problem. A chat app’s problem domain includes messages, users, and chat rooms; a restaurant’s includes customers, tables, and orders. A model can define each entity, describe the shape of the data stored for each entity, validate the data, store it in a database, and interact with it.

Just like any other software, you can develop models using Test-Driven Development (TDD).

### Path Definition
In test-driving the zoo application, you receive this error message in the server layer:

![[Pasted image 20230831140921.png]]

You’re in the red! To get to green you have to drop to the model layer and define the Dinosaur model.

You’ll need multiple model tests to satisfy this server test. Since they don’t touch HTML/CSS selectors nor HTTP actions/status codes, model tests are typically faster than feature-level and server-level tests. Driving the Dinosaur implementation with model tests — rather than feature or server tests — will make your test suite run faster. The model tests will confirm that:

1. the Dinosaur model is defined
2. the Dinosaur model has a path called `name`

Your first test will cover conditions 1 and 2 by creating an instance of a Dinosaur model with a `name`, then asserting that the `name` path (also referred to as field or property) can be retrieved.

### Hooks
Before each test, your `beforeEach` hook will [connect](http://mongoosejs.com/docs/api.html#index_Mongoose-connect) to the database and [drop](https://docs.mongodb.com/manual/reference/method/db.dropDatabase/) any old data using these method calls:

```js
await mongoose.connect(databaseUrl, options);
await mongoose.connection.db.dropDatabase();
```

After each test, your `afterEach` hook will [disconnect](http://mongoosejs.com/docs/api.html#index_Mongoose-disconnect) from the database with

```js
await mongoose.disconnect();
```

You can refactor these hooks by wrapping the three calls in two helper functions: `connectAndDrop` and `disconnect`. In your test file, import those functions and add them to your hooks.

### Path Validation
In this exercise you’ll be using a [custom validator function](http://mongoosejs.com/docs/api.html#schematype_SchemaType-validate). It receives the value to validate as its first argument. It returns a Boolean, which is `false` if the value fails validation. Avoid arrow notation `() =>`. Using `function()` notation preserves the proper binding of [`this`](https://www.codecademy.com/resources/docs/javascript/this).

```js
// Define validator
validate = function (value) {
  ...
}

// Add validator to Schema
const DinosaurSchema = new Schema({
  count: {
    type: Number,
    validate: [validator, 'custom err msg']
  }
});
```

Since validation is a model-level concern, you’ll need to test at the model layer. You can test validation like this:

1. Create an instance of a model with validators and execute the validations with the `validateSync` method. Any validation [errors](https://www.codecademy.com/resources/docs/javascript/errors) will be stored in `[instance].errors.[path]`, like `dino.errors.count`.
2. Make assertions on `[instance].errors.[path]` and its properties.

For more information on validators visit the Validation section of the Mongoose guide: [http://mongoosejs.com/docs/validation.html](http://mongoosejs.com/docs/validation.html).

Remember that validation error messages are defined in the schema like this:

```js
age: {
   type: Number,
   validate: [validator, 'Age must be above 9.']
}
```

And you can assert the value of multiple properties of `[instance].errors.[path]` like `message`, `path`, `kind`, and `name`. You can write out multiple assertions or use [`assert.include`](http://chaijs.com/api/assert/#method_include):

```js
const errorInfo = person.errors.age;
  assert.include(errorInfo, {
    message: 'Age must be above 9.',
    path: 'age',
    kind: 'user defined',
    name: 'ValidatorError'
  });
```

The complete list of validators are available here: [http://mongoosejs.com/docs/schematypes.html](http://mongoosejs.com/docs/schematypes.html).

---

The validator function can be replaced by a built-in validator provided by Mongoose, `max`. Replace the `validate` property with

```js
max: [10, 'Cannot hold more than 10 dinosaurs.']
```

### Methods
Mongoose schemas support

- _static methods_: methods called by a model. They typically operate on a collection of documents (instances of the model).
- _instance methods_: methods called by an instance of a model. They typically operate on the document (model instance) itself.

From the previous exercise, you might recognize `Dinosaur.findOne()` as a static method and `dino.save()` as an instance method.

Sometimes you need to define additional methods for your application, like if you see a server-level error such as this:

![[Pasted image 20230831171018.png]]

This server test is failing because there is no model method to find Dinosaurs by name. You’ll need to drop to the model layer and write more tests.

The desired query is performed on a collection of documents, so it requires a static method, which is defined in `[schema].statics` and called according to the example below.

```js
// static method - implementation
DinosaurSchema.statics.findByName = function(name, callback) {
  return this.findOne({ name: name }, callback);
};
// static method - call the method
await Dinosaur.findByName('Velociraptor')
```

Use `function()` notation instead of arrow `=>` notation to properly bind [`this`](https://www.codecademy.com/resources/docs/javascript/this).

You can test-drive the development of this method just like any other JavaScript method: Call the method and make assertions on its output.

Sometimes you need an instance method for your application, like if you see a server-level error such as this:

![[Pasted image 20230831172016.png]]

This server test expects an increase to the dinosaur `count`, which is a responsibility of the Dinosaur model. You’ll need to drop to the model layer and test for a `.breed()` method.

`.breed()` will increase the `count` of one dinosaur. This kind of method is specific to an instance of a model, so you’ll need to define it as an instance method. Do this by storing it in `[schema].methods` as shown below.

```js
// instance method - implementation
DinosaurSchema.methods.breed = function() {
  this.count = this.count + 1;
};
// instance method - call the method
dino.breed()
```

Use `function()` notation instead of arrow `=>` notation to properly bind [`this`](https://www.codecademy.com/resources/docs/javascript/this).

You can test-drive the development of this method just like any other JavaScript method: Call the method and make assertions on its output.

### Review 
- The _model layer_ represents entities and interactions in a web app’s problem domain.
- Model paths can be test-driven using validators. Call `validateSync` and make assertions on the properties of `[instance].errors.[path]`.
- The [storage](https://www.codecademy.com/resources/docs/javascript/storage) of data can be tested with [construction and updating methods](http://mongoosejs.com/docs/models.html) like `save` and `update`. Retrieval can be tested with [query methods](http://mongoosejs.com/docs/queries.html) like `find`, `findOne`, and `findby`.
- _Static methods_ are stored in `[schema].statics` and _instance methods_ are stored in `[schema].methods`. Both can be tested like any other JavaScript function.
 

# Server Testing with TDD

## Server Testing Stack

### Introduction
Server tests are used to test the server response only, not any front-end rendering of code or user interactions. We “disconnect” the browser and interact directly with the server using [requests](https://www.codecademy.com/resources/docs/javascript/requests). The tests define the expected behavior of the interactions and check the actual responses against what we expect.

Server tests are commonly used to test API responses, but we also use server tests for any server response that our application relies on. This can include checking status codes and error messages.
 
### Testing Framework: Chai
When writing tests, sometimes you’ll find that the tests require calculation steps or inline code to determine if the test is passing. For example, to test if an array `foo` includes an element `bar` using Mocha with the built-in Node assertion library, we use the JavaScript `includes` helper:

```js
assert.ok(foo.includes(bar));
```

To improve the readability and flow of our tests, we extend the built-in Node assertion library with Chai.

```js
const {assert} = require('chai');
```

The main function in Chai we are using is `.include()`. This allows us to rewrite the previous example as:

```js
assert.include(foo, bar);
```

Include also works to check that text contains certain values:

```js
assert.include('foobar', 'bar'); // Evaluates to true
```

The large set of assertion [methods](https://www.codecademy.com/resources/docs/javascript/methods) in the chai library enable us to write more expressive tests that are easy for developers to understand.

### Testing HTML Responses
Our back-end server is serving dynamic HTML to the user. It is possible to use `.include()` to verify that the HTML response contains certain [Strings](https://www.codecademy.com/resources/docs/javascript/strings), but gets cumbersome to verify the hierarchical relationships of DOM elements.

We can use the jsdom library to improve this type of assertion. It allows us to select elements of the DOM and check relationships and content. To increase the readability of our tests, we abstracted the jsdom functionality into a custom function, `parseTextFromHTML`:

```js
const parseTextFromHTML = (htmlAsString, selector) => {
  const selectedElement = jsdom(htmlAsString).querySelector(selector);
  if (selectedElement !== null) {
    return selectedElement.textContent;
  } else {
    throw new Error(`No element with selector ${selector} found in HTML string`);
  }
};
```

This function takes the HTML response as a string and the desired selector as inputs and returns the `textContent` of the corresponding element. If no element is found, it will return a TypeError.

### Async / Await
A server typically handles many [requests](https://www.codecademy.com/resources/docs/javascript/requests) at a time, but may be only capable of processing a subset of the requests concurrently. One side effect of this is that the server response time is neither instant nor predictable. If no other processes are occurring on the server, requests are handled quickly, but if the server is close to full capacity, the request can take a few seconds or even timeout.

We need a way to receive asynchronous responses from the server and then act on them. The async/await pattern introduced in Node 8 helps us write readable descriptions of the behavior of our application which is an important part of writing good tests.

To use this pattern, define the function with the `async` keyword. Then, within the function, use the `await` keyword in front of the asynchronous function you are calling.

```js
const foo = async () => {
  console.log(await someAsyncThing());
  return true;
}

foo();
```

Here, we are waiting for `someAsyncThing()` to return before logging the result to the console.

### SuperTest
As you may have noticed in the previous exercise, we are using the function `request` to make server calls to support our tests. This is actually a reference to the SuperTest library:

```js
const request = require('supertest');
```

This library was specifically designed for testing Node server responses and integrates well with Mocha and Chai. To use SuperTest, we pass the `app` object from our app into the `request` function. To make a GET request, we use [`.get()`](https://www.codecademy.com/resources/docs/javascript/map/get) with the desired route as the argument:

```js
await request(app)
          .get('/')
          .send();
```

It is also possible to perform a POST using SuperTest. We chain any desired properties or inputs to the HTTP call, and use `.send()` to make the request:

```js
await request(app)
          .post('/messages')
          .type('form')
          .send({author, message});
```

### Review
- _Chai_ - a library for extending the built in Node assertion library
- _jsdom_ - a library for interacting and testing the DOM returned by the server (this functionality is encapsulated in our `parseTextFromHTML` helper function).
- _async / await_ - a pattern for making asynchronous code more readable
- _SuperTest_ - a library for making Node server [requests](https://www.codecademy.com/resources/docs/javascript/requests) and testing their responses

```js
const {assert} = require('chai');
const request = require('supertest');
const {jsdom} = require('jsdom');

const app = require('../../app');

const parseTextFromHTML = (htmlAsString, selector) => {
    const selectedElement = jsdom(htmlAsString).querySelector(selector);
    if (selectedElement !== null) {
      return selectedElement.textContent;
    } else {
      throw new Error(`No element with selector ${selector} found in HTML string`);
    }
};

describe('the homepage', () => {
    it('the #page-title element contains the page title', async () => {
        const pageTitle = 'My Page';
        const response = await request(app).
        get('/').
        send();
        assert.include(parseTextFromHTML(response.text, '#page-title'), pageTitle);
    });
    
});
```


## Server Testing Patterns

### Introduction
As you develop an application, you may realize that you can replace feature tests or reduce them with equal coverage at a lower level. One question to ask when deciding between a full feature test versus a server test is:

“Is it worth trading a slow feature test for a faster server test that doesn’t test the UI?”

Server tests often provide feedback in terms of HTTP domain concepts, like status codes, header keys and values, and the content of the response body. Let’s take a look at a feature-level test and compare it to a corresponding server test in **messages-test.js** to the right:

```js
describe('posting a message', () => {
    it('saves the message with the author information', () => {
     const author = 'user name';
     const message ='feature testing with TDD makes me feel empowered to create a better workflow';

      browser.url('/');
      browser.setValue('input[id=author]', author);
      browser.setValue('textarea[id=message]', message);
      browser.click('input[type=submit]');

      assert.include(messagesText(), message);
      assert.include(messagesText(), author);
    });

    });
  });
```

```js
describe('when the Message is valid', () => {
    it('creates a new message', async () => {
      const author = 'user name';
      const message ='feature testing with TDD makes me feel empowered to create a better workflow';
      
      //save message
      const response = await request(app)
        .post('/messages')
        .type('form')
        .send({author, message});
      
      //check response to verify message is saved
      assert.include(parseTextFromHTML(response, '#messages'), message);
    });
});
```

When such a test fails due to a non-existent server implementation, the developer needs to dive into the server level and begin the TDD process to drive the server solution.

### Status Codes
Server tests are slightly faster than browser-driven feature tests. Since the web browser is cut out of the test, we are not testing how things are rendered for the user. Instead, we are focused on the server response.

One use of TDD at the server level is to ensure that the HTTP status codes are returned as expected. Verifying status codes provide the most basic level of confidence that the server is functioning correctly. Having a test suite that includes status codes provides a quick check when implementing a new feature that we haven’t accidentally caused a request for valid routes to respond not authorized (401) or not found (404).

To verify status codes, we are asserting that the response status is equal to the status code integer that our application requires:

```js
assert.equal(response.status, 200);
```

### Response Content
In the previous exercise, we checked that the server responded with specific status codes. Now we need to make sure the server is responding with the correct content. Specifically, we are looking at HTML responses that are rendered by the front-end.

Many servers return dynamic HTML content based on the user, the URL accessed, header values, and more. We use TDD to ensure the server responds correctly for each case. When designing our tests, it is important to consider both the intended and unintended user behavior.

We can organize our tests into two categories:

- tests that exercise the “Happy Path” — expected use cases of our application
- tests that exercise the “Sad Path” — unexpected or invalid use of our application

For our tests, once we retrieve the response from the server, we use `assert.include()` from the Chai library to check the response.

As an example, after requesting a valid profile page for “My Name”, you may receive the following response content:

```js
response.text = '<div><div id="my-name">My Name</div></div>';
```

You can retrieve the content of `#my-name` and check it using the following:

```js
assert.include(parseTextFromHTML(response.text, '#my-name'), "My Name"); //True
```

We could also write a separate test to check the corresponding “sad path”. Perhaps there is not yet a page for “Your Name”, so you should not receive a response containing similar HTML. We use `.notInclude()` to verify that the response is **not** including “Your Name” :

```js
assert.notInclude(parseTextFromHTML(response.text, '#my-name'), "Your Name"); //True
```

### Refactoring: Route Parameters
What if we want to create a profile page that is customized for each user?

A straightforward implementation would be to generate hard coded routes for every single user of our app. Think: `'welcome/alice' => '<h1>Your Name is alice</h1>'`, `'welcome/bob' => '<h1>Your Name is bob</h1>'`, etc.

Hopefully if you see repetitive code like this, you’ll have an urge to refactor it to something more elegant using a variable route parameter. This allows us to put any username into the url and have the server generate the appropriate response. Think: `'welcome/:username' => '<h1>Your Name is ' + req.params.username +'</h1>'`.

```js
router.get('/:username', (req, res) => {
    res.send('<h1 id="welcome-message">Welcome ' + req.params.username + '!</h1>');
});
```

### Refactoring: Handlebars
Sometimes during the reflection of the refactor phase, you will realize that you can implement something better or more efficiently. In the code so far, we have been responding with inline HTML [strings](https://www.codecademy.com/resources/docs/javascript/strings). On a large project, this could make it difficult for the front end developer to organize and maintain.

An improved approach to this is using a templating library like Handlebars to separate the HTML view from the JavaScript controller.

In the web app that you’ve built in this lesson, we’ve placed the templates in the `/views` folder and have an extension of `.handlebars`. Our controller will now use `render` to create the view and pass in any variables:

```js
const param = 'Foo';
res.render('templateName', {param});
```

The templates are written like regular HTML, but [variables](https://www.codecademy.com/resources/docs/javascript/variables) can be accessed within the view using double curly braces:

```html
<h1>{{ param }}</h1>
```

When the view is rendered, it will replace `{{ param }}` with its actual value:

```html
<h1>Foo</h1>
```

### API Errors
As mentioned earlier, one of the use cases for server testing is for checking API responses, especially the “sad path” where a user interacts with the server in an unexpected or disallowed manner. We need to make sure our server properly handles invalid passwords, form field [errors](https://www.codecademy.com/resources/docs/javascript/errors), etc.

Keep in mind that while there may only be one “happy path” for an interaction (user submits a valid password), there can be many corresponding “sad paths” (password is too short, doesn’t contain special characters, etc). By testing the majority of these on the server level, it saves us from testing them at a more resource intensive level including the user view.

---

Note that this API is returning JSON, so you will access the message content using:

`JSON.parse(response.text).message`

### Review
We used several technologies to write tests for both “happy” and “sad” paths of:

- Server status codes
- Server response content
- Error cases

```js
const {assert} = require('chai');
const request = require('supertest');
const {jsdom} = require('jsdom');

const app = require('../../app');

const parseTextFromHTML = (htmlAsString, selector) => {
  const selectedElement = jsdom(htmlAsString).querySelector(selector);
  if (selectedElement !== null) {
    return selectedElement.textContent;
  } else {
    throw new Error(`No element with selector ${selector} found in HTML string`);
  }
};

describe('/messages', () => {
  
  describe('POST', () => {
    describe('when the Message is valid', () => {
      it('redirects to the index', async () => {
        const author = 'Inquisitive User';
        const message = 'Why Test?';

        const response = await request(app)
          .post('/messages')
          .type('form')
          .send({author, message});

        assert.equal(response.status, 302);
        assert.equal(response.headers.location, '/');
      });
    });

    describe('when the author is blank', () => {
      it('renders an error message', async () => {
        const message = 'Server Testing';

        const response = await request(app)
          .post('/messages')
          .send({message});

        assert.equal(response.status, 400);
        assert.equal(JSON.parse(response.text).message, "Every message requires an author");
        });
    });

  });
});
```

