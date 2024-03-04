# What is the Back-End?
## What is the Back-End?

### Front and Back
To oversimplify a bit, the front-end is the parts of a webpage that a visitor can interact with and see.

Various tools and frameworks can be used to make a webpage, but, at its core, the front-end is composed of JavaScript, CSS, HTML, and other _static assets_, such as images or videos. Static assets are files that don’t change. When a visitor navigates to a webpage, these assets are sent to their browser.

You’ll sometimes hear front-end development referred to as _client-side_ development. Our instinct might be to think of the client as the human visitor or user of a website, but when referring to the client in web development, we’re usually referring to the non-human requester of content. In the case of visiting a website, the client is the browser, but in other circumstances, a client might be another application, a mobile device, or even a “smart” appliance!

While the front-end is the part of the website that makes it to the browser, the back-end consists of all the behind-the-scenes processes and data that make a website function and send resources to clients.

### The Web Server
We talked about how the front-end consists of the information sent to a client so that a user can see and interact with a website, but where does the information come from? The answer is a _web server_.

A _web server_ is a process running on a computer that listens for incoming requests for information over the internet and sends back responses. Each time a user navigates to a website on their browser, the browser makes a request to the web server of that website. Every website has at least one web server. A large company like Facebook has thousands of powerful computers running web servers in facilities located all around the world which are listening for requests, but we could also run a simple web server from our own computer!

The specific format of a request (and the resulting response) is called the _protocol_. You might be familiar with the protocol used to access websites: HTTP. When a visitor navigates to a website on their browser, similarly to how one places an order for takeout, they make [an HTTP request](https://www.codecademy.com/articles/http-requests) for the resources that make up that site.

For the simplest websites, a client makes a single request. The web server receives that request and sends the client a response containing everything needed to view the website. This is called a _static website_. This doesn’t mean the website is not interactive. As with the individual static assets, a website is static because once those files are received, they don’t change or move. A static website might be a good choice for a simple personal website with a short bio and family photos. A user navigating Twitter, however, wants access to new content as it’s created, which a static website couldn’t provide.

### So What is the Back-end?
When a user navigates to google.com, their request specifies the URL but not the filename for today’s [Google Doodle](https://en.wikipedia.org/wiki/Google_Doodle). The web application’s back-end will need to hold the logic for deciding which assets to send. Moreover, modern web applications often cater to the specific user rather than sending the same files to every visitor of a webpage. This is known as _dynamic content_.

The collection of programming logic required to deliver dynamic content to a client, manage security, process payments, and myriad other tasks is sometimes known as the “application” or _application server_. The application server can be responsible for anything from sending an email confirmation after a purchase to running the complicated algorithms a search engine uses to give us meaningful results.

### Storing Data
The back-ends of modern web applications include some sort of _database_, often more than one. Databases are collections of information. There are many different databases, but we can divide them into two types: [relational databases](https://www.codecademy.com/articles/what-is-rdbms-sql) and [non-relational databases (also known as NoSQL databases)](https://en.wikipedia.org/wiki/NoSQL). Whereas relational databases store information in tables with columns and rows, non-relational databases might use other systems such as key-value pairs or a document storage model. _SQL_, **S**tructured **Q**uery **L**anguage, is a programming language for accessing and changing data stored in relational databases. Popular relational databases include [MySQL](https://www.mysql.com/) and [PostgreSQL](https://www.postgresql.org/) while popular NoSQL databases include [MongoDB](https://www.mongodb.com/) and [Redis](https://redis.io/).

In addition to the database itself, the back-end needs a way to programmatically access, change, and analyze the data stored there.

### What is an API?
When a user navigates to a specific item for sale on an e-commerce site, the price listed for that item is stored in a database, and when they purchase it, the database will need to be updated with the correct inventory for that item type. In fact, much of what the back-end entails is reading, updating, or deleting information stored in a database.

In order to have consistent ways of interacting with data, a back-end will often include a _web API_. API stands for **A**pplication **P**rogramming **I**nterface and can mean a lot of different things, but a _web API_ is a collection of predefined ways of, or rules for, interacting with a web application’s data, often through an HTTP request-response cycle. Unlike the HTTP requests a client makes when a user navigates to a website’s URL, this type of request indicates how it would like to interact with a web application’s data (create new data, read existing data, update existing data, or delete existing data), and it receives some data back as a response.

### Authorization and Authentication
Two other concepts we’ll want our server-side logic to handle are _authentication_ and _authorization_.

_Authentication_ is the process of validating the identity of a user. One technique for authentication is to use logins with usernames and passwords. These credentials need to be securely stored in the back-end on a database and checked upon each visit. Web applications can also use external resources for authentication. You’ve likely logged into a website or application using your Facebook, Google, or Github credentials; that’s also an authentication process.

_Authorization_ controls which users have access to which resources and actions. Certain application views, like the page to edit a social media personal profile, are only accessible to that user. Other activities, like deleting a post, are often similarly restricted.

### Different Back-end Stacks
Unlike the front-end, which must be built using HTML, CSS, and JavaScript, there’s a lot of flexibility in which technologies can be used in order to create the back-end of a web application. Developers can construct back-ends in many different languages like PHP, Java, JavaScript, Python, and more.

You don’t need to reinvent the wheel to create a robust back-end. Instead, most developers make use of _frameworks_ which are collections of tools that shape the organization of your back-end and provide efficient ways of accomplishing otherwise difficult tasks.

There are numerous [back-end frameworks](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Web_frameworks#A_few_good_web_frameworks) from which developers can choose.

Framework | Language
--- | ---
[Laravel](https://laravel.com/) | [PHP](http://www.php.net/)
[Express.js](https://expressjs.com/) | [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript) (runs in the [Node environment](https://nodejs.org/en/))
[Ruby on Rails](https://rubyonrails.org/) | [Ruby](https://www.ruby-lang.org/en/)
[Spring](https://spring.io/) | [Java](https://www.oracle.com/java/)
[JSF](https://www.oracle.com/technetwork/java/javaee/javaserverfaces-139869.html) | [Java](https://www.oracle.com/java/)
[Flask](http://flask.pocoo.org/) | [Python](https://www.python.org/)
[Django](https://www.djangoproject.com/) | [Python](https://www.python.org/)
[ASP.NET](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet) | [C#](https://dotnet.microsoft.com/learn/csharp)

The collection of technologies used to create the front-end and back-end of a web application is referred to as a _stack_. This is where the term _full-stack developer_ comes from; rather than working in either the front-end or the back-end exclusively, a full-stack developer works in both.

For example, [the MEAN stack](https://en.wikipedia.org/wiki/MEAN_(software_bundle)) is a technology stack for building web applications that uses **M**ongoDB, **E**xpress.js, **A**ngularJS, and **N**ode.js: MongoDB is used as the database, Node.js with Express.js for the rest of the back-end, and Angular is used as a front-end framework. While the [LAMP Stack](https://en.wikipedia.org/wiki/LAMP_(software_bundle)), sometimes considered the archetypal stack, uses **L**inux, **A**pache, **M**ySQL, and **P**HP.

### Review
- The front-end of a website or application consists of the HTML, CSS, JavaScript, and static assets sent to a client, like a web browser.
- A web server is a process running on a computer somewhere that listens for incoming requests for information over the internet and sends back responses.
- Storing, accessing, and manipulating data is a large part of a web application’s back-end
- Data is stored in databases which can be relational databases or NoSQL databases.
- The server-side of a web application, sometimes called the application server, handles important tasks such as authorization and authentication.
- The back-end of web application often has a web API which is a way of interacting with an application’s data through HTTP requests and responses.
- Together the technologies used to build the front-end and back-end of a web application are known as the stack, and many different languages and frameworks can be used to build a robust back-end.


## JavaScript for Node.js

### Arrow Expressions
With the introduction of ES6 (ECMAScript) in 2015 came a new feature called _[arrow expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)_. Arrow expressions has allowed developers to omit parts of the function they don’t need. This means that it allows your code to become more maintainable and organized.

When using an arrow expression, we do not use the `function` declaration. To define an arrow expression you simply use: `() => { }`. You can pass arguments to an arrow expression between the parenthesis (`()`).

```js
// Defining an anonymous arrow expression that simply logs a string to the console.
console.log(() => console.log('Shhh, Im anonymous'));
 
// Defining a named function by creating an arrow expression and saving it to a const variable helloWorld. 
const helloWorld = (name) => {
  console.log(`Welcome ${name} to Codecademy, this is an arrow expression.`)
};
 
// Calling the helloWorld() function.
helloWorld('Codey'); //Output: Welcome Codey to Codecademy, this is an Arrow Function Expression.
```

### Asynchronous Concepts
When it comes to development in Node.js and JavaScript, we use a mix of synchronous code (blocking I/O), and [asynchronous code](https://nodejs.org/en/docs/guides/blocking-vs-non-blocking/) (non-blocking I/O). A common example of asynchronous code are Promises.

#### Promises
A [_Promise_](https://www.codecademy.com/courses/asynchronous-javascript/lessons/promises/exercises/introduction) is a JavaScript object that represents the eventual outcome of an asynchronous operation. A `Promise` has three different outcomes: pending (the result is undefined and the expression is waiting for a result), fulfilled (the promise has been completed successfully and returned a value), and rejected (the promise did not successfully complete, the result is an error object).

```js
// Creating a new Promise and saving it to the testLuck variable. Two arguments are being passed, one for when the promise resolves, and one for if the promise gets rejected.
const testLuck = new Promise((resolve, reject) => {
  if (Math.random() < 0.5) { 
    resolve('Lucky winner!')
  } else {
    reject(new Error('Unlucky!'))
  }
});
 
testLuck.then(message => {
  console.log(message) // Log the resolved value of the Promise
}).catch(error => {
  console.error(error) // Log the rejected error of the Promise
});
```

#### Async/Await
The [`async...await` syntax](https://www.codecademy.com/courses/asynchronous-javascript/lessons/async-await/exercises/introductio) allows developers to easily implement `Promise`-based code. The keyword `async` used in conjunction with a function declaration creates an _async function_ that returns a `Promise`. Async functions allow us to use the keyword `await` to block the event loop until a given `Promise` resolves or rejects. The `await` keyword also allows us to assign the resolved value of a `Promise` to a variable.

```js
// Creating a new promise that runs the function in the setTimeout after 5 seconds. 
const newPromise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("All done!"), 5000);
});
 
// Creating an asynchronous function using an arrow expression and saving it to a the variable asyncFunction. 
const asyncFunction = async () => {
  // Awaiting the promise to resolve and saving the result to the variable finalResult.
  const finalResult = await newPromise;
 
  // Logging the result of the promise to the console
  console.log(finalResult); // Output: All done!
}
 
asyncFunction();
```

#### setInterval() and setTimeout()
The [`setInterval()` function](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setInterval) executes a code block at a specified interval, in milliseconds. The `setInterval()` function requires two arguments: the name of the function (the code block that will be executed), and the number of milliseconds (how often the function will be executed). Optionally, we can pass additional arguments which will be supplied as parameters for the function that will be executed by `setInterval()`. The `setInterval()` function will continue to execute until the `clearInterval()` function is called or the node process is exited. 

```js
// Defining a function that instantiates setInterval
const showAlert = () => {
  // Calling setInterval() and passing a function that shows an alert every 5 seconds.
  setInterval(() => {
    alert('I show every 5 seconds!')
  }, 5000);
};
 
// Calling the newInterval() function that calls the setInterval
showAlert();
```

The [`setTimeout()` function](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setTimeout) executes a code block after a specified amount of time (in milliseconds) and is only executed once. The `setTimeout()` function accepts the same arguments as the `setInterval()` function. Using the `clearTimeout()` function will prevent the function specified from being executed.

```js
// Defining a function that calls setTimeout
const showTimeout = () => {
  // Calling setTimeout() that passes a function that shows an alert after 5 seconds.
  setTimeout(() => {
    alert('I only show once after 5 seconds!');
  }, 5000);
};
 
// Calling the showTimeout() function
showTimeout();
```


# Setting up a Server with HTTP
## Setting up a Server with HTTP

### Introduction to HTTP
HTTP, short for Hypertext Transfer Protocol, is a request-response protocol that serves as the foundation of data exchange and communication within the client-server computing model. What this means in simpler terms is that HTTP helps facilitate the exchange of information between a client (i.e. website, mobile app, etc.) and a server.

At a base level, the operation of HTTP can be explained quite simply in the following steps detailing the request-response paradigm between a client and a server: 1) The client submits an HTTP _request_ message to the server. 2) The server receives the HTTP request, performs some functions on behalf of the client according to the request. 3) The server returns a _response_ message to the client containing important information about the processing of the request.

### The Structure of HTTP
HTTP requests and responses have specific structures to help facilitate the exchange of information between a client and a server.

#### Requests
The core elements that can be expected are:

1) **HTTP Method**: The HTTP method is usually a verb, such as `GET` and `POST`, or a noun such as `OPTIONS` and `HEAD`. These methods inform the server of the intent of the request and are used in accurately routing and processing requests. For instance, an HTTP request containing a `GET` method implies that the client wants to fetch a resource. The list of supported HTTP methods can be found using the `http.METHODS` property.
2) **Path**: The path denotes the path of the resource relative to the root URL. For example, making a `GET` request to `https://codecademy.com/api/lessons` would strip common elements such as the protocol (`https://`) and domain (`codecademy.com`), leaving the path of `/api/lessons`.
3) **HTTP Protocol Version**: The version of the HTTP protocol (I.e. [HTTP/1.1](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol), [HTTP/2](https://en.wikipedia.org/wiki/HTTP/2), and [HTTP/3](https://en.wikipedia.org/wiki/HTTP/3)).
4) **Headers**: Headers are optional and are used to convey additional information that may be important in processing a request by a server. There is an extensive list of [standard headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers) that can be used, as well as custom headers that can be added on a per-application basis.
5) **Body**: The body contains data required to be sent to the server to process a request. The body is not leveraged for all request types. It is most common to see a body attached to requests with verbs such as `POST`, `PUT`, and `PATCH`.

#### Responses
The core elements that can be expected in a response are:

1) **HTTP Protocol Version**: The version of the HTTP protocol, similar to the request.
2) **Status Code**: The status code indicates if the request was successful and, if not, why it wasn’t successful.
3) **Status Message**: The status message provides a short description of the corresponding status code.
4) **Headers**: These response headers are similar to those provided in a request.
5) **Body**: The body of a response contains data corresponding to the fetched resource. The body is optional and contains data only when necessary to fulfill the request.

### The Movement of HTTP
Various transport protocols exist, but let’s take a look at the common ones that HTTP leverages to move around the web.

#### TCP
The most common transport protocol used in conjunction with HTTP is [TCP](https://developer.mozilla.org/en-US/docs/Glossary/TCP). TCP stands for _Transmission Control Protocol_ and allows two hosts to connect and exchange data streams, guaranteeing the delivery of data packets in the same order as they were sent. This means that TCP ensures that packets are delivered reliably and free from errors, positioning itself as an incredibly stable way to move data from one location to another.

#### UDP
[UDP](https://developer.mozilla.org/en-US/docs/Glossary/UDP), or _User Datagram Protocol_, is a less commonly used transport protocol. It operates using a connectionless communication model, requiring no “handshaking,” which can potentially lead to unreliability in the delivery of messages. As such, UDP has no mechanism by which to guarantee delivery or ordering of messages. While these are certainly drawbacks for some types of applications, other applications that want to prioritize transmission speed and efficiency over security and reliability may leverage UDP.

While these transport protocols are great for moving your requests to their destination, they lack any meaningful security to protect the data while in transit. In order to remedy this issue, encryption protocols are commonly used.

#### TLS
[TLS](https://www.cloudflare.com/learning/ssl/transport-layer-security-tls/), also known as _Transport Layer Security_, is a widely adopted security protocol designed to facilitate secure data transmission via encryption. TLS evolved out of the encryption protocol known as [SSL](https://www.cloudflare.com/learning/ssl/what-is-ssl/) (Secure Sockets Layer), which has since been deprecated in favor of TLS. While these two protocols are different, the terms are sometimes used interchangeably. Using TLS with HTTP will allow you to use `HTTPS` (_Hypertext Transfer Protocol Secure_), which helps denote the presence of the extra security.

In conjunction with the different transport protocols mentioned above, there also exist different versions of HTTP. These distinct versions at a baseline operate similarly in that they carry information between entities and maintain important distinctions.

#### HTTP/1.1
[HTTP/1.1](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) was one of the first versions of the HTTP protocol to be designed and implemented. It operates by sending messages in the form of text. HTTP/1.1 is commonly used over TCP and is the slowest of the HTTP versions regarding data transmission.

#### HTTP/2
[HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) is a major revision of HTTP/1.1, developed with the intent to try and reduce web page load latency. However, the most significant departure from HTTP/1.1 is the encapsulation of all messages in binary format rather than plain text. This allows HTTP/2 to apply different techniques for data transmission, including sending smaller packets of data for greater flexibility of data transfer. This also allows a single connection to be made between two communicating entities rather than multiple as required by HTTP/1.1. Similar to HTTP/1.1, HTTP/2 also leverages TCP for transport.

#### HTTP/3
[HTTP/3](https://en.wikipedia.org/wiki/HTTP/3) is the third major version of HTTP. While there are quite a few complex technological differences between HTTP/3 and the previous versions, one of the most important is how the protocol deals with lost packets. HTTP/3 also differs through its use of transport protocol, leveraging a transport protocol called [QUIC](https://en.wikipedia.org/wiki/QUIC), which applies specific controls over UDP. HTTP/3 is currently an [Internet Draft](https://en.wikipedia.org/wiki/Internet_Draft).

### The HTTP Module
To process HTTP requests in JavaScript and Node.js, we can use the built-in [`http` module](https://nodejs.dev/en/api/v19/http).

The `http` module comes with various methods that are useful when engaging with HTTP network requests. One of the most commonly used methods within the `http` module is the `.createServer()` method.

```js
const server = http.createServer((req, res) => {
  res.end('Server is running!');
});
 
server.listen(8080, () => {
  const { address, port } = server.address();
  console.log(`Server is listening on: http://${address}:${port}`);
})
```

The `req` object contains all of the information about an HTTP request ingested by the server. It exposes information such as the HTTP method (`GET`, `POST`, etc.), the pathname, headers, body, and so on. The `res` object contains methods and properties pertaining to the generation of a response by the HTTP server. This object contains methods such as `.setHeader()` (sets HTTP headers on the response), `.statusCode` (set the status code of the response), and `.end()` (dispatches the response to the client who made the request).

Once the `.createServer()` method has instantiated the server, it must begin listening for connections. This final step is accomplished by the `.listen()` method on the server instance. This method takes a [port](https://en.wikipedia.org/wiki/Port_(computer_networking)) number as the first argument, which tells the server to listen for connections at the given port number. In our example above, the server has been set to listen on port `8080`. Additionally, the `.listen()` method takes an optional callback function as a second argument, allowing it to carry out a task after the server has successfully started.

### The Anatomy of the URL
HTTP servers have to break down requests into their constituent parts to effectively process them and provide adequate responses. In that same vein, designing an [API](https://en.wikipedia.org/wiki/API) (Application Programming Interface) with endpoints intended to process specific requests in certain ways requires an understanding of the semantics of these requests, which are ultimately embodied within a [URL](https://en.wikipedia.org/wiki/URL) (Uniform Resource Locator).

A URL can provide a great deal of information about a request and how it is expected to behave. A URL is made up of the following parts:

1) **Protocol**: The protocol of the URL denotes what protocol is being used for this particular resource. For instance, a URL could have a protocol of HTTP or HTTPS.
2) **Domain**: The domain of the URL is a unique reference that identifies a website on the Internet.
3) **Path**: The path refers to a file or directory on the web server. Paths oftentimes contain path parameters that APIs can process as a way to provide additional data when processing. For instance, to request a resource for a user with ID number `15`, we can add the user’s ID to the URL like this: `/users/15`.
4) **Query**: The query is commonly found on pages that contain dynamic content. Queries are prefixed by a `?` and appear at the end of a URL. Queries can be comprised of multiple key/value pairs, separated by a `&`, with each key being assigned its corresponding value using a `=`. Queries are often used in conjunction with `GET` requests to pass filter parameters in order to provide specificity for the requested resource. For instance, to request all users that are active members, we could append a key/value pair of `active=true` to the end of our URL like this: `/users?active=true`.

### The URL Module
Typically, an HTTP server will require information from the request URL to accurately process a request. This request URL is located on the `url` property contained within the `req` object itself. To parse the different parts of this URL easily, Node.js provides the built-in [`url` module](https://nodejs.org/api/url.html). The core of the `url` module revolves around the `URL` class. A new `URL` object can be instantiated using the `URL` class as follows:

```js
const url = new URL('https://www.example.com/p/a/t/h?query=string');
```

Once instantiated, different parts of the URL can be accessed and modified via various properties, which include:

- `hostname`: Gets and sets the host name portion of the URL.
- `pathname`: Gets and sets the path portion of the URL.
- `searchParams`: Gets the search parameter object representing the query parameters contained within the URL. Returns an instance of the [URLSearchParams](https://nodejs.org/docs/latest-v14.x/api/url.html#url_class_urlsearchparams) class.

These classes are defined by the [WHATWG URL specification](https://url.spec.whatwg.org/). Both the browser and Node.js implement this API, which means developers can have a similar developer experience working with both client and server-side JavaScript.

Using these properties, one can break the URL down into easily usable parts for processing the request.

```js
const host = url.hostname; // example.com
const pathname = url.pathname; // /p/a/t/h
const searchParams = url.searchParams; // {query: 'string'}
```

While the `url` module can be used to deconstruct a URL into its constituent parts, it can also be used to construct a URL. Constructing a URL via this method relies on most of the same properties listed above to set values on the URL instead of retrieving them. This can be done by setting each of these values equal to a value for the newly constructed URL. Once all parts of the URL have been added, the composed URL can be obtained using the `.toString()` method.

```js
const createdUrl = new URL('https://www.example.com');
createdUrl.pathname = '/p/a/t/h';
createdUrl.search = '?query=string';
 
createUrl.toString(); // Creates https://www.example.com/p/a/t/h?query=string
```

### The Querystring Module
While the `url` module can handle query strings attached to URLs, it can also be done with the built-in [`querystring` module](https://nodejs.org/api/querystring.html#querystring_querystring_decode). The `querystring` module is dedicated to providing utilities solely focused on parsing and formatting URL query strings. As such, the module provides a much smaller number of methods to use. The core methods are listed below:

- `.parse()`: This method is used for parsing a URL query string into a collection of key-value pairs. The `.decode()` method does the same.

```js
const str = 'prop1=value1&prop2=value2';
querystring.parse(str); // Returns { prop1: value1, prop2: value2}
```

- `.stringify()`: This method is used for producing a URL query string from a given object via iteration of the object’s “own properties.” The `.encode()` method does the same.

```js
const props = { "prop1": value1, "prop2": value2};
querystring.stringify(props); // Returns 'prop1=value1&prop2=value2'
```

- `.escape()`: This method is used for performing [percent-encoding](https://developer.mozilla.org/en-US/docs/Glossary/percent-encoding) on a given query string.
- `.unescape()`: This method is used to decode percent-encoded characters within a given query string.

The `querystring` module is focused solely on manipulating URL query strings, so it requires the query string to have already been isolated from an incoming URL as part of a request. This means that some pre-processing of the URL is necessary before being able to use the module.

Additionally, it is worth noting that in the latest versions of Node (v16.x) the `querystring` module has become a legacy feature, with its core functionality having been absorbed into the `url` module via the `URLSearchParams` API. However, the features in the `querystring` module are still handy when using the long-term support versions of Node.js (v14.x).

### Routing
To process and respond to requests appropriately, servers need to do more than look at a request and dispatch a response. Internally, a server needs to maintain a way to handle each request based on specific criteria such as `method`, `pathname`, etc. The process of handling requests in specific ways based on the information provided within the request is known as _routing_.

The `method` is one important piece of information that can be used to route requests. Since each HTTP request contains a `method` such as `GET` and `POST`, it is a great way to discern different classes of requests based on the action intended for the server to carry out. Thus, all `GET` requests could be routed to a specific function for handling, while all `POST` requests are routed to another function to be handled. This also allows for the logical co-location of processing code with the specific verb to be handled.

```js
const server = http.createServer((req, res) => {
  const { method } = req;
 
  switch(method) {
    case 'GET':
      return handleGetRequest(req, res);
    case 'POST':
      return handlePostRequest(req, res);
    case 'DELETE':
      return handleDeleteRequest(req, res);
    case 'PUT':
      return handlePutRequest(req, res);
    default:
      throw new Error(`Unsupported request method: ${method}`);
  }
})
```

This is great at first glance, but it should soon become apparent that the routing is not specific enough. After all, how will one `GET` request be distinguished from another?

We can distinguish one request from another of the same method through the use of the `pathname`. The `pathname` allows the server to understand what resource is being targeted.

```js
function handleGetRequest(req, res) {
  const { pathname } = new URL(req.url);
  let data = {};
 
  if (pathname === '/projects') {
    data = await getProjects();
    res.setHeader('Content-Type', 'application/json');
    return res.end(JSON.stringify(data));
  }
 
  res.statusCode = 404;
  return res.end('Requested resource does not exist');
 
}
```

This pattern can be extrapolated to any number of conditional resource matches, allowing the server to handle many different types of requests to different resources.

### HTTP Status Codes
Once a request is processed, a response must be returned to the client to inform it of what happened. To build a response for the client, several pieces of information are required. One of these pieces of information is the [HTTP response status code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status), which is responsible for indicating whether a specific HTTP request has been successfully completed.

Response status codes are grouped into five classes:

1) [Informational](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#information_responses): Range from `100` to `199`.
2) [Successful](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#successful_responses): Range from `200` to `299`.
3) [Redirects](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#redirection_messages): Range from `300` to `399`.
4) [Client Errors](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#client_error_responses): Range from `400` to `499`.
5) [Server Errors](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#server_error_responses): Range from `500` to `599`.

Status codes are paired with a short text-based description to help elucidate the meaning of the code. Some common types of status codes that you are likely to encounter are `200 OK`, `400 Bad Request`, and `500 Internal Server Error`.

### Interacting with a Database
While we have encountered simple examples of servers handling HTTP requests, some requests require a bit more work than returning a simple string such as `'Hello World'`. In real-world applications, servers are responsible for helping to persist and retrieve data, usually through interaction with a database.

Databases are remote resources to which the server must make a request. When this happens, the server making the request functions as the client, sending HTTP messages to the database server. Databases usually have their own Software Development Kits (SDKs) and Object-Relational Mapping (ORMs) that can be used to connect to them easily. But with the right information, requests could potentially be made in a raw form directly from your server using something like the HTTP `.request()` method.

A single server often does not represent the final destination in processing a request from a client. Instead, a client sends a request, which is then processed partially, generating a separate HTTP request from the server to the database. When received, the server waits for the database’s response and will ultimately relay that information as a response back to the original caller.
 
### Interacting with Another Backend API
Just like with databases, sometimes servers need to make requests to external APIs to accomplish some goal. There are a variety of reasons to reach out to external services. Some common situations are payment processing, service integrations with other products, webhooks, and so on.

There are a few methods provided by the `http` module that facilitate making HTTP requests to external services. One of these methods is the `request()` method. The `request()` method takes two arguments; it takes a configuration object containing details about the request as well as a callback to handle the response.

```js
const options = {
  hostname: 'example.com',
  port: 8080,
  path: '/projects',
  method: 'GET',
  headers: {
    'Content-Type': 'application/json'
  }
}
 
const request = http.request(options, res => {
  // Handle response here
})
```

For convenience, the `http` module provides a convenient method for making `GET` requests in the form of the `get()` method. This method differs from the `request()` method in that it automatically sets the method to `GET` and calls `req.end()` automatically.

The fact that servers can make HTTP requests to other services opens up possibilities for different architecture designs for back-ends. One example of an architecture made possible by this ability is [microservice architectures](https://en.wikipedia.org/wiki/Microservices). Microservice architectures divide needs into separate lightweight services that communicate via HTTP over a network. As such, a single application can be comprised of dozens of microservices, which could all be written in different programming languages, but work together by communicating over HTTP.

Our HTTPS request needs to be set up to be able to receive the data properly. Data from the response will usually be received in chunks and pieced together. As such, we need to watch for these chunks of data and process them. We can do this by listening to the `data` event.

You can listen for events on the response of a request using the `.on()` method. The `.on()` method takes an event as the first argument and a callback as the second argument.

```js
    response.on('data', (chunk) => {
      data += chunk;
    })
```

To know when a response is finished, we can listen for the `end` event. When the `end` event is triggered, we can work with the data from the response.

You can dispatch a response to a caller using `res.end()`.

You can end an HTTPS request using `request.end()`.

```js
    response.on('end', () => {
      console.log(data);
      res.end(data);
    });
  });

  request.end();
```

```js
const http = require('http');
const https = require('https');

const handleGetRequest = (req, res) => {
  const options = {
    hostname: 'static-assets.codecademy.com',
    path: '/Courses/Learn-Node/http/data.json',
    method: 'GET',
    headers: {
      'Content-Type': 'application/json'
    }
  }
  
  const request = https.request(options, response => {
    let data = '';

    // Aggregate data chunks as they come in from the API
    response.on('data', (chunk) => {
      data += chunk;
    });

    // Handle the end of the request
    response.on('end', () => {
      console.log("Retrieved Data:", data);
      res.end(data);
    });
  });

  request.end();
}

// Creates server instance
const server = http.createServer((req, res) => {
  const { method } = req;
 
  switch(method) {
    case 'GET':
      return handleGetRequest(req, res);
    default:
      throw new Error(`Unsupported request method: ${method}`);
  }
});

// Starts server listening on specified port
server.listen(4001, () => {
  const { address, port } = server.address();
  console.log(`Server is listening on: http://${address}:${port}`);
});
```

---

`response.writeHead()` is a method in Node.js used to write HTTP headers to the response. It is typically used in a server-side script to send headers along with the response to an HTTP request.

The method takes two arguments: the HTTP status code to send and an object containing the headers to send. The headers object is optional.

```js
const http = require('http');

http.createServer(function(request, response) {
    response.writeHead(200, {'Content-Type': 'text/plain'});
    response.write('Hello World!');
    response.end();
}).listen(8080);
```

It's important to note that `response.writeHead()` must be called before any data is written to the response using `response.write()` or `response.end()`. If it is called after data has already been sent, it will throw an error.

[[Rock-Paper-Scissors]]
