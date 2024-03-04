# Introduction to Express.js
## Introduction to Server-Side Frameworks with Express.js

### What is a Server-Side Framework
Let’s first start with what a *framework* is — which is a collection of code to make it easier to accomplish a specific task. A framework is particular in that developers must follow the rules and syntax put forth by the framework to use it properly. With that in mind, a *server-side framework* is used to run web applications and handle web development workflows on the server-side or back-end. This workflow might include things like accessing databases, generating HTML, handling URL routing, and more!

#### Why Use a Server-Side Framework?
A server-side framework can handle a lot of the back-end responsibilities without you needing to come up with a custom solution, which saves a lot of time. Other benefits could include:

- access to libraries built to work with the framework
- existing resources and documentation for solving common problems
- improved security

There are some tradeoffs to consider as well — as noted earlier, you would need to learn the patterns of the framework.

### Node.js and Express.js
As you recall, Node.js is an open-source runtime environment for executing JavaScript outside of a browser. You can create a back-end entirely with Node.js. However, you can also use Express.js, a server-side framework written in JavaScript and built to work with Node.js. The Express.js framework comes with included code that makes implementing some core functionality much quicker than doing it from scratch. By using Express, you have a simpler developer experience and thus can focus more on business logic (functionality).

The code below sets up a route on a server:

```js
const express = require('express');
const app = express();
 
app.get('/', (req, res) => {
  res.send('<h1>Hello from your Express.js server!!</h1>');
});
 
app.listen(8000, () => {
  console.log('Server listening on port 8000');
});
```

Which would render load on localhost:8000.


# Learn Express: Routes
## Learn Express Routes

### Introduction
Express is a powerful but flexible Javascript framework for creating web servers and APIs. It can be used for everything from simple static file servers to JSON APIs to full production servers.

Create, Read, Update, and Delete Expressions. These four functionalities together are known as CRUD, and they form the backbone of many real-life APIs.

### Starting A Server
Express is a Node module, so in order to use it, we will need to import it into our program file. To create a server, the imported `express` function must be invoked.

```js
const express = require('express');
const app = express();
```

On the first line, we import the Express library with `require`. When invoked on the second line, it returns an instance of an Express application. This application can then be used to start a server and specify server behavior.

The purpose of a server is to listen for requests, perform whatever action is required to satisfy the request, and then return a response. In order for our server to start responding, we have to tell the server where to *listen* for new requests by providing a port number argument to a method called `app.listen()`. The server will then listen on the specified port and respond to any requests that come into it.

The second argument is a callback function that will be called once the server is running and ready to receive responses.

```js
const PORT = 4001;
app.listen(PORT, () => {
  console.log(`Server is listening on port ${PORT}`);
});
```

### Writing Your First Route
Once the Express server is listening, it can respond to any and all requests. But how does it know what to do with these requests? To tell our server how to deal with any given request, we register a series of *routes*. Routes define the control flow for requests based on the request’s *path* and HTTP verb.

For example, if your server receives a GET request at `/monsters`, we will use a route to define the appropriate functionality for that HTTP verb (GET) and path (`/monsters`).

The path is the part of a request URL after the hostname and port number, so in a request to `localhost:4001/monsters`, the path is `/monsters` (in this example, the hostname is `localhost`, the port number is `4001`).

The HTTP verb is always included in the request, and it is one of a finite number of options used to specify expected functionality. GET requests are used for retrieving resources from a server.

Express uses `app.get()` to register routes to match GET requests. Express routes (including `app.get()`) usually take two arguments, a path (usually a string), and a callback function to handle the request and send a response.

```js
const moods = [{ mood: 'excited about express!'}, { mood: 'route-tastic!' }];
app.get('/moods', (req, res, next) => {
  // Here we would send back the moods array in response
});
```

The route above will match any GET request to `'/moods'` and call the callback function, passing in two objects as the first two arguments. These objects represent the request sent to the server and the response that the Express server should eventually send to the client.

If no routes are matched on a client request, the Express server will handle sending a 404 Not Found response to the client.

### Sending A Response
HTTP follows a one request-one response cycle. Each client expects exactly one response per request, and each server should only send a single response back to the client per request. 

Express servers send responses using the `.send()` method on the response object. `.send()` will take any input and include it in the response body.

```js
const monsters = [
  { type: 'werewolf' }, 
  { type: 'hydra' }, 
  { type: 'chupacabra' }
];
app.get('/monsters', (req, res, next) => {
  res.send(monsters);
});
```

In addition to `.send()`, `.json()` can be used to explicitly send JSON-formatted responses. `.json()` sends any JavaScript object passed into it.

### Matching Route Paths
Express tries to match requests by route, meaning that if we send a request to `<server address>:<port number>/api-endpoint`, the Express server will search through any registered routes in order and try to match `/api-endpoint`.

Express searches through routes in the order that they are registered in your code. The first one that is matched will be used, and its callback will be called.

If there are no matching routes registered, or the Express server has not sent a response at the end of all matched routes, it will automatically send back a 404 Not Found response, meaning that no routes were matched or no response was ultimately sent by the registered routes.

### Getting A Single Expression
Routes become much more powerful when they can be used dynamically. Express servers provide this functionality with named *route parameters*. Parameters are route path segments that begin with `:` in their Express route definitions. They act as wildcards, matching any text at that path segment. For example `/monsters/:id` will match both `/monsters/1` and `/monsters/45`.

Express parses any parameters, extracts their actual values, and attaches them as an object to the request object: `req.params`. This object’s keys are any parameter names in the route, and each key’s value is the actual value of that field per request.

```js
const monsters = { 
  hydra: { height: 3, age: 4 }, 
  dragon: { height: 200, age: 350 } 
};
// GET /monsters/hydra
app.get('/monsters/:name', (req, res, next) => {
  console.log(req.params); // { name: 'hydra' }
  res.send(monsters[req.params.name]);
});
```

### Setting Status Codes
Express allows us to set the status code on responses before they are sent. Response codes provide information to clients about how their requests were handled. Until now, we have been allowing the Express server to set status codes for us. For example, any `res.send()` has by default sent a 200 OK status code.

The `res` object has a `.status()` method to allow us to set the status code, and other methods like `.send()` can be chained from it.

```js
const monsterStoreInventory = { fenrirs: 4, banshees: 1, jerseyDevils: 4, krakens: 3 };
app.get('/monsters-inventory/:name', (req, res, next) => {
  const monsterInventory = monsterStoreInventory[req.params.name];
  if (monsterInventory) {
    res.send(monsterInventory);
  } else {
    res.status(404).send('Monster not found');
  }
});
```

### Matching Longer Paths
In order for a request to match a route path, it must match the entire path.

### Other HTTP Methods
This course will cover three other important HTTP methods: `PUT`, `POST`, and `DELETE`. Express provides methods for each one: `app.put()`, `app.post()`, and `app.delete()`.

`PUT` requests are used for updating existing resources. For this reason, we will need to include a unique identifier as a route parameter to determine which specific resource to update.

### Using Queries
You may have noticed in the previous exercise that our `PUT` route had no information about how to update the specified expression, just the id of which expression to update. It turns out that there was more information in the request in the form of a _query string_. *Query strings* appear at the end of the path in URLs, and they are indicated with a `?` character. For instance, in `/monsters/1?name=chimera&age=1`, the query string is `name=chimera&age=1` and the path is `/monsters/1/`.
 
Query strings do not count as part of the route path. Instead, the Express server parses them into a JavaScript object and attaches it to the request body as the value of `req.query`. The key: value relationship is indicated by the `=` character in a query string, and key-value pairs are separated by `&`. In the above example route, the `req.query` object would be `{ name: 'chimera', age: '1' }`.

```js
const monsters = { '1': { name: 'cerberus', age: '4'  } };
// PUT /monsters/1?name=chimera&age=1
app.put('/monsters/:id', (req, res, next) => {
  const monsterUpdates = req.query;
  monsters[req.params.id] = monsterUpdates;
  res.send(monsters[req.params.id]);
});
```

When updating, many servers will send back the updated resource after the updates are applied so that the client has the exact same version of the resource as the server and database.

### Creating An Expression
`POST` is the HTTP method verb used for creating new resources. Because `POST` routes create new data, their paths do not end with a route parameter, but instead end with the type of resource to be created.

For example, to create a new monster, a client would make a `POST` request to `/monsters`. The client does not know the id of the monster until it is created and sent back by the server, therefore `POST /monsters/:id` doesn’t make sense because a client couldn’t know the unique id of a monster before it exists.

Express uses `.post()` as its method for `POST` requests. `POST` requests can use many ways of sending data to create new resources, including query strings.

The HTTP status code for a newly-created resource is 201 Created.

```js
app.post('/expressions', (req, res, next) => {
  const receivedExpression = createElement('expressions', req.query);
  if (receivedExpression) {
    expressions.push(receivedExpression);
    res.status(201).send(receivedExpression);
  } else {
    res.status(400).send();
  }
});
```

### Deleting Old Expressions
`DELETE` is the HTTP method verb used to delete resources. Because `DELETE` routes delete currently existing data, their paths should usually end with a route parameter to indicate which resource to delete.

Express uses `.delete()` as its method for `DELETE` requests.

Servers often send a 204 No Content status code if deletion occurs without error.

```js
app.delete('/expressions/:id', (req, res, next) => {
  const expressionIndex = getIndexById(req.params.id, expressions);
  if (expressionIndex !== -1) {
    expressions.splice(expressionIndex, 1);
    res.status(204).send();
  } else {
    res.status(404).send();
  }
});
```


## Learn Express Routers

### This File Is Too Big!
Routers are mini versions of Express applications — they provide functionality for handling route matching, requests, and sending responses, but they do not start a separate server or listen on their own ports. Routers use all the `.get()`, .`put()`, `.post()`, and `.delete()` routes that you know and love.

### Express.Router
An Express router provides a subset of Express methods. To create an instance of one, we invoke the `.Router()` method on the top-level Express import.

To use a router, we *mount* it at a certain path using `app.use()` and pass in the router as the second argument. This router will now be used for all paths that begin with that path segment.

```js
const express = require('express');
const app = express();
 
const monsters = {
  '1': {
    name: 'godzilla',
    age: 250000000
  },
  '2': {
    name: 'manticore',
    age: 21
  }
}
 
const monstersRouter = express.Router();
 
app.use('/monsters', monstersRouter);
 
monstersRouter.get('/:id', (req, res, next) => {
  const monster = monsters[req.params.id];
  if (monster) {
    res.send(monster);
  } else {
    res.status(404).send();
  }
});
```

Inside the `monstersRouter`, all matching routes are assumed to have `/monsters` prepended, as it is mounted at that path. `monstersRouter.get('/:id')` matches the full path `/monsters/:id`.

### Using Multiple Router Files
Generally, we will keep each router in its own file, and `require` them in the main application. This allows us to keep our code clean and our files short.

To do this with `monstersRouter`, we would create a new file **monsters.js** and move all code related to `/monsters` requests into it.

```js
// monsters.js
const express = require('express');
const monstersRouter = express.Router();
 
const monsters = {
  '1': {
    name: 'godzilla',
    age: 250000000
  },
  '2': {
    Name: 'manticore',
    age: 21
  }
}
 
monstersRouter.get('/:id', (req, res, next) => {
  const monster = monsters[req.params.id];
  if (monster) {
    res.send(monster);
  } else {
    res.status(404).send();
  }
});
 
module.exports = monstersRouter;
```

Our **main.js** file could then be refactored to import the `monstersRouter`:

```js
// main.js
const express = require('express');
const app = express();
const monstersRouter = require('./monsters.js');
 
app.use('/monsters', monstersRouter);
```


# Learn Express: Middleware
## Middleware

### Introduction
In programming in general, this often means putting the reused code into reusable containers like functions and objects. In Express specifically, this will also mean composing our desired functionality into a series of middleware functions.

### DRYing Code With Functions
Code that performs the same task in multiple places is repetitive, and the quality coder’s credo is “Don’t Repeat Yourself” (DRY). If a program performs similar tasks without refactoring into a function, it is said to “violate DRY”.

### DRYing Routes With app.use()
So how do we get code to run every time one of our Express routes is called without repeating ourselves? We write something called _middleware_. Middleware is code that executes between a server receiving a request and sending a response. It operates on the boundary, so to speak, between those two HTTP actions.

In Express, middleware is a function. Middleware can perform logic on the request and response objects, such as: inspecting a request, performing some logic based on the request, attaching information to the response, attaching a status to the response, sending the response back to the user, or simply passing the request and response to another middleware. Middleware can do any combination of those things or anything else a Javascript function can do.

```js
app.use((req, res, next) => {
  console.log('Request received');
});
```

The previous code snippet is an example of middleware in action. `app.use()` takes a callback function that it will call for every received request. In this example, every time the server receives a request, it will find the first registered middleware function and call it. In this case, the server will find the callback function specified above, call it, and print out `'Request received'`.

You might be wondering what else our application is responsible for that isn’t related to middleware. The answer is not much. To quote the [Express documentation](http://expressjs.com/en/guide/using-middleware.html):

_An Express application is essentially a series of middleware function calls._

In addition to performing the routing that allows us to communicate appropriate data for each separate endpoint, we can perform application logic we need by implementing the necessary middleware.

Its callback will be called before every route. Since we can access the `req` object, however, we can use the `req.method` property which will always be equal to the verb of the request!

### next()
We mentioned that most of Express’s functionality is chaining middleware. This chain of middleware is referred to as the _middleware stack_.

The middleware stack is processed in the order they appear in the application file, such that middleware defined later happens after middleware defined before. It’s important to note that this is regardless of method — an `app.use()` that occurs after an `app.get()` will get called after the `app.get()`.

```js
app.use((req, res, next) => {
  console.log("A sorcerer approaches!");
  next();
});
 
app.get('/magic/:spellname', (req, res, next) => {
  console.log("The sorcerer is casting a spell!");
  next();
});
 
app.get('/magic/:spellname', (req, res, next) => {
  console.log(`The sorcerer has cast ${req.params.spellname}`);
  res.status(200).send();
});
 
app.get('/magic/:spellname', (req, res, next) => {
  console.log("The sorcerer is leaving!");
});
 
// Accessing http://localhost:4001/magic/fireball 
// Console Output:
// "A sorcerer approaches!"
// "The sorcerer is casting a spell!"
// "The sorcerer has cast fireball"
```

In the above code, the routes are called in the order that they appear in the file, provided the previous route called `next()` and thus passed control to the next middleware. We can see that the final matching call was not printed. This is because the previous middleware did not invoke the `next()` function to run the following middleware.

An Express middleware is a function with three parameters: `(req, res, next)`. The sequence is expressed by a set of callback functions invoked progressively after each middleware performs its purpose. The third argument to a middleware function, `next`, should get explicitly called as the last part of the middleware’s body. This will hand off the processing of the request and the construction of the response to the next middleware in the stack.

### Request And Response Parameters
Recall the function signature of an Express middleware, i.e., `(req, res, next)`. You might recognize this signature as being the very same that we’ve used for Express routes in the past. Well there’s a perfectly good reason for that: Express routes are middleware. Every route created in Express is also a middleware function handling the request and response objects at that part of the stack. Express routes also have the option of sending a response body and status code and closing the connection. These two features are a byproduct of Express routes being middleware, because all Express middleware functions have access to the request, the response, and the next middleware in the stack.

### Route-Level app.use() - Single Path
Since this code isn’t shared by all of our routes, the previous syntax of `app.use()` won’t work. Let’s see what the [Express documentation](https://expressjs.com/en/4x/api.html) for `app.use()` has to say about this use case. This is the `app.use()` function signature:

`app.use([path,] callback [, callback...])`

In documentation for many programming languages, optional arguments for functions are placed in square brackets (`[]`). This means that `app.use()` takes an optional path parameter as its first argument. We can now write middleware that will run for every request at a specific path.

```js
app.use('/sorcerer', (req, res, next) => {
  console.log('User has hit endpoint /sorcerer');
  next();
});
```

In the example above the console will print `'User has hit endpoint /sorcerer'`, if someone visits our web page’s ‘/sorcerer’ endpoint. Since the method `app.use()` was used, it won’t matter if the user is performing a `GET`,a `POST`, or any other kind of HTTP request. Since the path was given as an argument to `app.use()`, this middleware function will not execute if the user hits a different path (for instance: `'/spells'` or `'/sorcerer/:sorcerer_id'`).

### Control Flow With next()
We’ve experienced writing middleware that performs its function and hands off the request and response objects to the next function in the stack, but why exactly do we have to write `next()` at the end of every middleware? If it always needs to be at the end of every function we write, it seems like an unnecessary piece of boilerplate. You might be surprised to learn that we aren’t going to introduce a way to automatically hand off the request and response objects without having to repeatedly write `next()`. Rather, we’re going to explore why it is useful to have `next()` as a separate function call. The biggest reason being we don’t always want to pass control to the next middleware in the stack.

For example, when designing a system with confidential information, we want to be able to selectively show that information to authorized users. In order to do that, we would create middleware that tests a user’s permissions. If the user has the permission necessary, we would continue through the middleware stack by calling `next()`. If it fails, we would want to let the user know that they’re not allowed to see the information they’re trying to access.

### Route-Level app.use() - Multiple Paths
Let’s take another look at the Express documentation for `app.use()`:

“_argument_: path

_description_: The path for which the middleware function is invoked; can be any of:

- A string representing a path.
- A path pattern.
- A regular expression pattern to match paths.
- An array of combinations of any of the above. “

So `app.use()` can take an array of paths!

### Middleware Stacks
Recall that middleware is just a function with a specific signature, namely `(req, res, next)`. We have, for the most part, been using anonymous function definitions for this because our middleware has only been relevant to the route invoking it. There is nothing stopping us from defining functions and using them as middleware though. That is to say:

```js
const logging = (req, res, next) => {
  console.log(req);
  next();
};
 
app.use(logging);
```

Up until this point we’ve only been giving each middleware-accepting method a single callback. With modular pieces like this, it is useful to know that methods such as `app.use()`, `app.get()`, `app.post()`, and so on all can take multiple callbacks as additional parameters.

```js
const authenticate = (req, res, next) => {
  ...
};
 
const validateData = (req, res, next) => {
  ...
};
 
const getSpell = (req, res, next) => {
  res.status(200).send(getSpellById(req.params.id));
};
 
const createSpell = (req, res, next) => {
  createSpellFromRequest(req);
  res.status(201).send();
};
 
const updateSpell = (req, res, next) => {
  updateSpellFromRequest(req);
  res.status(204).send();
}
 
app.get('/spells/:id', authenticate, getSpell);
 
app.post('/spells', authenticate, validateData, createSpell);
 
app.put('/spells/:id', authenticate, validateData, updateSpell);
```

In the above code sample, we created reusable middleware for authentication and data validation. We use the `authenticate()` middleware to verify a user is logged in before proceeding with the request and we use the `validateData()` middleware before performing the appropriate create or update function. Additional middleware can be placed at any point in this chain.

### Open-Source Middleware: Logging
If we find a solution we don’t need to write, however, it will allow us to work faster and more intelligently to focus on the problems that differentiate our application from others.

We will replace the logging code in the workspace with [morgan](https://github.com/expressjs/morgan), an open-source library for logging information about the HTTP request-response cycle in a server application. `morgan()` is a function that will _return a middleware function_, to reiterate: the return value of `morgan()` will be a function, that function will have the function signature `(req, res, next)` that can be inserted into an `app.use()`, and that function will be called before all following middleware functions. Morgan takes an argument to describe the formatting of the logging output. For example, `morgan('tiny')` will return a middleware function that does a “tiny” amount of logging. With morgan in place, we’ll be able to remove the existing logging code.

```js
const morgan = require('morgan');

app.use(morgan('dev'));
```

### Documentation
[Morgan documentation](https://github.com/expressjs/morgan#api).

### Open-Source Middleware: Body Parsing
An HTTP request can include a _body_, a set of information to be transmitted to the server for processing. This is useful when the end user needs to send information to the server. The lucky thing about using open-source middleware is that even though parsing the body of an HTTP request is a tricky operation requiring knowledge about network data transfer concepts, we easily manage it by importing a library to do it for us.

`bodyParser` has multiple [methods](https://github.com/expressjs/body-parser#api) for returning middleware functions. For now, let’s use `bodyParser.json()` to parse all request bodies in JSON format.

```js
const bodyParser = require('body-parser');

app.use(bodyParser.json());
```

---

`bodyParser` will automatically attach the parsed body object to `req.body`.

### Error-Handling Middleware
Error handling middleware needs to be the last `app.use()` in your file. If an error happens in any of our routes, we want to make sure it gets passed to our error handler. The middleware stack progresses through routes as they are presented in a file, therefore the error handler should sit at the bottom of the file.

```js
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```

Based on the code above, we can see that error-handling middleware is written much like other kinds of middleware. The biggest difference is that there is an additional parameter in our callback function, `err`. This represents the error object, and we can use it to investigate the error and perform different tasks depending on what kind of error was thrown.

Express has its own error-handler, which catches errors that we haven’t handled. But if we anticipate an operation might fail, we can invoke our error-handling middleware. We do this by passing an error object as an argument to `next()`. Usually, `next()` is called without arguments and will proceed through the middleware stack as expected. When called with an error as the first argument, however, it will call any applicable error-handling middleware.

```js
app.use((req, res, next) => {
  const newValue = possiblyProblematicOperation();
  if (newValue === undefined) {
    let undefinedError = new Error('newValue was not defined!');
    return next(undefinedError);
  }
  next();
});
 
app.use((err, req, res, next) => {
  const status = err.status || 500;
  res.status(status).send(err.message);
});
```

This prompts the error-handling middleware to send a response back to the user, but many other error-handling techniques could be employed (like logging, re-attempting the failed operation, and/or emailing the developer).

### Review
We learned what middleware is and we’ve used it to write cleaner, readable, adaptable, and maintainable code. We’ve written functions that are context aware and can have overlapping functionality without duplicating code. We can serve data by route, with each possible endpoint being treated as a separate relative of the family of our application. We learned to link these middleware using `next()` to continue to the next middleware in the stack. We’ve reduced complexity in our codebase by relying on external, open-source middleware.


## Router Parameters

### Introduction
When building interfaces with Express, we will run into the pattern of expecting certain information in a requested URL and using that information to identify the data that is being requested.

```js
app.get('/sorcerers/:sorcererName', (req, res, next) => {
  const sorcerer = Sorcerers[req.params.sorcererName];
  res.send(sorcerer.info);
});
 
app.get('/sorcerers/:sorcererName/spellhistory', (req, res, next) => {
  const sorcerer = Sorcerers[req.params.sorcererName];
  const spellHistory = Spells[sorcerer.id].history;
  res.send(spellHistory);
});
```

In the above code we need to extract the request parameter `:sorcererName` from the url in both instances, and end up duplicating the necessary code so that it appears in both routes. When working with routes that require parameters, we might find ourselves in a position where multiple different routes require the same parameter and use it to identify the same piece of data. While writing this duplicate code will get the job done, copy-and-pasting functionality does leave a bitter taste in the mouth of the principled developer.

### router.param()
Express, luckily, is mindful of the pain-point of replicated parameter-matching code and has a method specifically for this issue. When a specific parameter is present in a route, we can write a function that will perform the necessary lookup and attach it to the `req` object in subsequent middleware that is run.

```js
app.param('spellId', (req, res, next, id) => {
  let spellId = Number(id);
    try {
      const found = SpellBook.find((spell) => {
        return spellId === spell.id;
      })
      if (found) {
        req.spell = found;
        next();
      } else {
        next(new Error('Your magic spell was not found in any of our tomes'));
      };
    } catch (err) {
      next(err)
    }
});
```

In the code above we intercept any request to a route handler with the `:spellId` parameter. Note that in the `app.param` function signature, `'spellId'` does not have the leading `:`. The actual ID will be passed in as the fourth argument, `id` in this case, to the `app.param` callback function when a request arrives.

We look up the spell in our `SpellBook` array using the `.find()` method. If `SpellBook` does not exist, or some other error is thrown in this process, we pass the error to the following middleware (hopefully we’ve written some error-handling middleware, or included some externally-sourced error-handling middleware). If the `spell` exists in `SpellBook`, the `.find()` method will store the spell in `found`, and we attach it as a property of the request object (so future routes can reference it via `req.spell`). If the requested `spell` does not exist, `.find()` will store `undefined` in `found`, and we let future middlewares know there was an error with the request by creating a new `Error` object and passing it to `next()`.

Note that inside an `app.param` callback, you should use the fourth argument as the parameter’s value, not a key from the `req.params` object.

### Merge Parameters
When we want to create something complex in software, we model out our base components and use _composition_ to create these relationships.

When we’re building web endpoints, we might want to access some property of a complex object. In order to do this in Express, we can design a nested router. This would be a router that is invoked within another router. In order to pass parameters the parent router has access to, we pass a special configuration object when defining the router.

```js
const sorcererRouter = express.Router();
const familiarRouter = express.Router({mergeParams: true});
 
sorcererRouter.use('/:sorcererId/familiars', familiarRouter);
 
sorcererRouter.get('/', (req, res, next) => {
  res.status(200).send(Sorcerers);
  next();
});
 
sorcererRouter.param('sorcererId', (req, res, next, id) => {
  const sorcerer = getSorcererById(id);   
  req.sorcerer = sorcerer;
  next();
});
 
familiarRouter.get('/', (req, res, next) => {
  res.status(200).send(`Sorcerer ${req.sorcerer} has familiars ${getFamiliars(sorcerer)}`);
});
 
app.use('/sorcerer', sorcererRouter);
```

In the code above we define two endpoints: `/sorcerer` and `/sorcerer/:sorcererId/familiars`. The familiars are nested into the sorcerer endpoint — indicating the relationship that a sorcerer has multiple familiars. Take careful note of the `{mergeParameters: true}` argument that gets passed when creating the `familiarRouter`. This argument tells Express that the `familiarRouter` should have access to parents passed into its _parent_ router, that is, the `sorcererRouter`. We then tell express that the path for the `familiarRouter` is the same as the path for the `sorcererRouter` with the additional path `/:sorcererId/familiars`. We then can create a family of routes (a router) built by appending routes to `familiarRouter`‘s base: `/sorcerer/:sorcererId/familiars`.

[[programación/code/javascript/spices/app.js|app.js]]
[[spicesRouter.js]]

 
## What is CORS?

### What is a security policy?
Servers are used to host web pages, applications, images, fonts, and much more. When you use a web browser, you are likely attempting to access a distinct website (hosted on a server). Websites often request these hosted resources from different locations (servers) on the Internet. Security policies on servers mitigate the risks associated with requesting assets hosted on different server.

The same-origin policy is very restrictive. Under this policy, a document (i.e., like a web page) hosted on server A can only interact with other documents that are also on server A. In short, the same-origin policy enforces that documents that interact with each other have the same _origin_.

An origin is made up of the following three parts: the protocol, host, and port number.

Consider the following URL:

```
http://www.example.com/foo-bar.html
```

Let’s call it **URL1** (for short).

If you used a web browser to navigate from **URL1** to `http://www.example.com/hello-world.html`, you would be allowed to do so because the protocol (HTTP), host (example.com), and port (80) of each URL match one another. (Port 80 is the default port.) The same-origin policy requires that all parts of the origin match.

Navigating to `https://www.en.example.com/hello.html` from URL1, however, would not be allowed because of the different protocol (HTTPS) and host (en.example.com).

As you can see, not having a security policy can be risky, but a security policy like same-origin is a bit too restrictive. Thankfully, there are security policies that strike a mix of both, like _cross-origin_, which has evolved into the _cross-origin resource sharing_ standard, often abbreviated as CORS.

### What is CORS?
A request for a resource (like an image or a font) outside of the origin is known as a _cross-origin_ request. CORS (cross-origin resource sharing) manages cross-origin requests.

Once again, consider the following URL:

```
http://www.example.com/foo-bar.html
```

Let’s call it _URL1_ (for short).

Unlike same-origin, navigating to `https://www.ejemplo.com/hola.html` from **URL1** could be allowed with CORS. Allowing cross-origin requests is helpful, as many websites today load resources from different places on the Internet (stylesheets, scripts, images, and more).

Cross-origin requests, however, mean that servers must implement ways to handle requests from origins outside of their own. CORS allows servers to specify who (i.e., which origins) can access the assets on the server, among many other things.

You can think of these interactions as a building with a security entrance. For example, if you need to borrow a ladder, you could ask a neighbor in the building who has one. The building’s security would likely not have a problem with this request (i.e., same-origin). If you needed a particular tool, however, and you ordered it from an outside source like an online marketplace (i.e., cross-origin), the security at the entrance may request that the delivery person provide identification when your tool arrives.

### Why is CORS necessary?
The CORS standard is needed because it allows servers to specify not only who can access the assets, but also _how_ they can be accessed.

Cross-origin requests are made using the standard HTTP request methods. Most servers will allow `GET` requests, meaning they will allow resources from external origins (say, a web page) to read their assets. HTTP requests methods like `PATCH`, `PUT`, or `DELETE`, however, may be denied to prevent malicious behavior. For many servers, this is intentional. For example, it is likely that server A does not want servers B, C, or D to edit or delete its assets.

With CORS, a server can specify who can access its assets and which HTTP request methods are allowed from external resources.

### How does CORS manage requests from external resources?
An HTTP header is a piece of information associated with a request or a response. Headers are passed back and forth between your web browser (also referred to as a client) and a server when the web page you are on wants to use resources hosted on a different server. Headers are used to describe requests and responses. The CORS standard manages cross-origin requests by adding new HTTP headers to the standard list of headers. The following are the new HTTP headers added by the CORS standard:

- `Access-Control-Allow-Origin`
- `Access-Control-Allow-Credentials`
- `Access-Control-Allow-Headers`
- `Access-Control-Allow-Methods`
- `Access-Control-Expose-Headers`
- `Access-Control-Max-Age`
- `Access-Control-Request-Headers`
- `Access-Control-Request-Method`
- `Origin`

The `Access-Control-Allow-Origin` header allows servers to specify how their resources are shared with external domains. When a `GET` request is made to access a resource on Server A, Server A will respond with a value for the `Access-Control-Allow-Origin` header. Many times, this value will be `*`, meaning that Server A will share the requested resources with _any_ domain on the Internet. Other times, the value of this header may be set to a particular domain (or list of domains), meaning that Server A will share its resources with that specific domain (or list of domains). The `Access-Control-Allow-Origin` header is critical to resource security.

You can find a description of each CORS header at the following: [CORS Headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers#CORS).

### Pre-flight Requests
As mentioned before, most servers will allow `GET` requests but may block requests to modify resources on the server. Servers don’t just blindly block such requests though; they have a process in place that first checks and then communicates to the client (your web browser) which requests are allowed.

When a request is made using any of the following HTTP request methods, a standard _preflight_ request will be made before the original request.

- `PUT`
- `DELETE`
- `CONNECT`
- `OPTIONS`
- `TRACE`
- `PATCH`

Preflight requests use the `OPTIONS` header. The preflight request is sent _before_ the original request, hence the term “preflight.” The purpose of the preflight request is to determine whether or not the original request is safe (for example, a `DELETE` request). The server will respond to the preflight request and indicate whether or not the original request is safe. If the server specifies that the original request is safe, it will allow the original request. Otherwise, it will block the original request.

The request methods above aren’t the only thing that will trigger a preflight request. If any of the headers that are automatically set by your browser (i.e., user agent) are modified, that will also trigger a preflight request.

### How do I implement CORS?
Implementing the request headers to set up CORS correctly depends on the language and framework of the backend.

For example, if you are using Node, you can use `setHeader()`, as shown below:

```js
response.setHeader('Content-Type', 'text/html');
```

If you are using Express, you can use CORS middleware:

```bash
npm install cors
```

```js
var express = require('express');
var cors = require('cors');
var app = express();
 
app.use(cors());
 
app.get('/hello/:id', function (req, res, next) {
  res.json({msg: 'Hello world, we are CORS-enabled!'});
});
 
app.listen(80, function () {
  console.log('CORS-enabled web server is listening on port 80');
});
```

# Cheatsheets

![[introduction_to_expressjs.pdf]]
