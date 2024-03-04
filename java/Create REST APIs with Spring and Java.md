# Web and Spring Basics

## How the Web Works

### HTTP Requests

#### What is HTTP?
HTTP stands for Hypertext Transfer Protocol and is used to structure requests and responses over the internet. HTTP requires data to be transferred from one point to another over the network.

The transfer of resources happens using TCP (Transmission Control Protocol). In viewing this webpage, TCP manages the channels between your browser and the server (in this case, codecademy.com). TCP is used to manage many types of internet connections in which one computer or device wants to send something to another. HTTP is the command language that the devices on both sides of the connection must follow in order to communicate.

#### HTTP & TCP: How it Works
When you type an address such as [www.codecademy.com](https://codecademy.com/) into your browser, you are commanding it to open a TCP channel to the server that responds to that URL (or Uniform Resource Locator). A URL is like your home address or phone number because it describes how to reach you.

In this situation, your computer, which is making the request, is called the client. The URL you are requesting is the address that belongs to the server. Once the TCP connection is established, the client sends a HTTP _GET_ request to the server to retrieve the webpage it should display. After the server has sent the response, it closes the TCP connection. If you open the website in your browser again, or if your browser automatically requests something from the server, a new connection is opened which follows the same process described above. GET requests are one kind of HTTP method a client can call. You can learn more about the other common ones (_POST_, _PUT_ and _DELETE_) in [this article](https://www.codecademy.com/articles/what-is-rest).

Suppose you want to check out the latest course offerings from [http://codecademy.com](http://codecademy.com/). After you type the URL into your browser, your browser will extract the `http` part and recognize that it is the name of the network protocol to use. Then, it takes the domain name from the URL, in this case “codecademy.com”, and asks the internet Domain Name Server to return an Internet Protocol (IP) address.

Now the client knows the destination’s IP address. It then opens a connection to the server at that address, using the `http` protocol as specified. It will initiate a GET request to the server which contains the IP address of the host and optionally a data payload. The GET request contains the following text:

```
GET / HTTP/1.1
Host: www.codecademy.com
```

This identifies the type of request, the path on [www.codecademy.com](https://codecademy.com/) (in this case, “/“) and the protocol “HTTP/1.1.” HTTP/1.1 is a revision of the first HTTP, which is now called HTTP/1.0. In HTTP/1.0, every resource request requires a separate connection to the server. HTTP/1.1 uses one connection more than once, so that additional content (like images or stylesheets) is retrieved even after the page has been retrieved. As a result, requests using HTTP/1.1 have less delay than those using HTTP/1.0.

The second line of the request contains the address of the server which is `"www.codecademy.com"`. There may be additional lines as well depending on what data your browser chooses to send.

If the server is able to locate the path requested, the server might respond with the header:

```
HTTP/1.1 200 OK
Content-Type: text/html
```

This header is followed by the content requested, which in this case is the information needed to render [www.codecademy.com](https://codecademy.com/).

The first line of the header, `HTTP/1.1 200 OK`, is confirmation that the server understands the protocol that the client wants to communicate with (`HTTP/1.1`), and an [HTTP status code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) signifying that the resource was found on the server. The third line, `Content-Type: text/html`, shows the type of content that it will be sending to the client.

If the server is not able to locate the path requested by the client, it will respond with the header:

```
HTTP/1.1 404 NOT FOUND
```

In this case, the server identifies that it understands the HTTP protocol, but the `404 NOT FOUND` status code signifies that the specific piece of content requested was not found. This might happen if the content was moved or if you typed in the URL path incorrectly or if the page was removed.

#### What is HTTPS?
Since your HTTP request can be read by anyone at certain network junctures, it might not be a good idea to deliver information such as your credit card or password using this protocol. Fortunately, many servers support HTTPS, short for HTTP Secure, which allows you to encrypt data that you send and receive.

HTTPS is important to use when passing sensitive or personal information to and from websites. However, it is up to the businesses maintaining the servers to set it up. In order to support HTTPS, the business must apply for a certificate from a [Certificate Authority](https://en.wikipedia.org/wiki/Certificate_authority).

## How Spring Works

### Hello Spring

#### What is Spring?
Spring is an open-source Java framework that is useful, among other things, for building RESTful web applications. Like any web framework, Spring comes with an established set of code conventions and patterns, such as predefined templates, databases, and functions. These generic code conventions provide reusable infrastructural support, enabling developers to easily build a variety of applications without reinventing the wheel at the start of every project. Spring focuses on project “scaffolding” so that developers can concentrate on the core logic of applications (you can think of Spring as a Node.js, Django, or Ruby on Rails but for Java!).

Indeed, Spring contains templates for many different kinds of applications, or “Spring Projects”, (including Spring Cloud, Spring Web Services, Spring Security, etc.). Spring Boot is one of the easiest ways to build Spring web projects, enabling applications to run with minimal configuration.

So how does a Spring web application actually work?

1. The client sends a GET request to the Spring web server (i.e. the Spring application).
2. The server sends a data request to the data store to retrieve the information requested by the client.
3. The data store sends the requested data back to the server, if available.
4. The server sends that data – the HTTP Response – back to the client and displays it on the browser.

It’s important to note that this is just one scenario of a browser-based client initiating a GET request to retrieve some information from the data store. Depending on the application scenario, we might not always want or need to interact with the data store. For example, in the case of DELETE, it’s possible that the data store won’t return any data to the server. Moreover, a client is not limited to being the browser; a client can also be a desktop or mobile app, or tools and scripts.

#### Making GET Requests with a Web Browser
Whenever a user navigates to a website or clicks on a URL link, for example, they are initiating a GET request.

Imagine we are working with an online system that is keeping track of dog patient intakes for a pet clinic. The website address is `http://www.mypetclinic.com/dogs/` , where `dogs` is the resource containing a list of `dog` objects. In REST environments, the client can access the `dogs` resource through this GET request:

```
GET http://www.mypetclinic.com/dogs/ 
```

The server, upon receiving this GET request, should return a response that looks something like this:

```
{
  "dogs": [
    {
      "id": 1,
      "name": "Bella",
      "breed": "Golden Retriever"
    },
    {
      "id": 2,
      "name": "Max",
      "breed": "Bulldog"
    },
    {
      "id": 3,
      "name": "Ruby",
      "breed": "Poodle"
    },
  ]
}
```

One common way to send a GET request is by typing the URL – the HTTP endpoint – into your local web browser. For example, when a user types `http://www.mypetclinic.com/dogs/` into the address bar, the browser

1. Makes a GET request (`GET http://www.mypetclinic.com/dogs/`) that retrieves the `dogs` resource (i.e. the file containing the list of dog intakes) and
2. Displays the response on the browser page. In doing so, the user confirms that the HTTP endpoint is working – that the GET request is retrieving the requested resources from the Spring server.

Let’s imagine we’re building a web application that allows users to search for restaurants based on their food allergies. In order to send a GET request that returns a complete list of restaurants in our database, we first need to add an internal GET method to our Spring code.

```java
@GetMapping
public Iterable<Restaurant> getAllRestaurants() {
  return restaurantRepository.findAll();
}
```

#### Making GET Requests with Curl
Alternatively, we can make GET requests using curl. Curl, short for Client for URLs, is a command line tool that allows us to transfer data to and from a server. It supports multiple protocols, including HTTP.

Curl is also useful for testing HTTP request methods from your local command line. Let’s say we want to test the HTTP endpoint `http://www.mypetclinic.com/dogs/`. We would use the curl command…

```shell
curl http://www.mypetclinic.com/dogs/
```

…which uses the GET request as the default method to retrieve the `dogs` resource from that URL; the `dogs` resource is displayed in the terminal rather than the browser. In doing so, we again confirm that our server is returning and displaying the information that we expect it to.

#### Making POST Requests with a Web Browser
As with GET requests, we can use our local browser to make POST requests, a method that adds new data to a receiving web application.

A common way to append data to an application is by submitting an HTML form. Let’s say we want to add a new German Shepherd named “Charlie” to our list of dog intakes. We simply fill out a form that asks for the `name` of the pet (“Charlie”) and `breed` (“German Shepherd”). After clicking the “submit” button, the browser sends a POST request with that data to the application. The Spring application then uses this inputted form data to create and add a new `dog` object to our existing `dogs` resource.

```java
@PostMapping
@ResponseStatus(HttpStatus.CREATED)
public Restaurant addRestaurant(@RequestBody Restaurant restaurant) {
  validateNewRestaurant(restaurant);
  return restaurantRepository.save(restaurant);
}
```

#### Making POST Requests with Curl
In addition, we can make POST requests using the curl command. Let’s again imagine that we are adding Charlie the German Shepherd as a dog intake patient for our imaginary pet clinic. We would use this curl syntax:

```shell
curl -X POST -d "{\"name\":\"Charlie\", \"breed\":\"German Shepherd\"}" -H "Content-Type: application/json" http://www.mypetclinic.com/dogs/ 
```

- `-X POST` tells the server that the client is making a POST request, where `-X` is the curl parameter specifying the type of request method to use.
- `-d` (short for `--data`) indicates to the server that the client is sending new data to an existing application.
- The content inside `"{ }"`, `\"name\":\"Charlie\", \"breed\":\"German Shepherd\"` , is the data that the client wants to send (as indicated by the preceding `-d`). We use the `{\"key1\":\"value1\", \"key2\":\"value2\"}` syntax, where `name` and `breed` are the names of the two keys that define the dog object, and “Charlie” and “German Shepherd” are the values corresponding to those keys respectively.
- `-H "Content-Type: application/json"` specifies that we are sending data in JSON format.
- Finally, the URL `http://www.mypetclinic.com/dogs/` tells the server where to send this new data. In this case, the newly-created `dog` object will be posted under the `dogs` resource.

#### Review
In this lesson, we covered two different ways to make GET requests, an HTTP method that retrieves data from the server and sends it back to the application.

1. Using the browser: type the URL `https://example.com/abc` into the address bar.
2. Using curl: type `curl https://example.com/abc` into your local command line

In addition, we made POST requests, an HTTP method that adds new data to the web application. We can make POST requests using either curl or the browser.

1. Using the browser: submit an HTML form that is setup to hit the `https://www.example.com/abc` endpoint.
2. Using curl: type `curl -X POST -d "{\"key1\":\"value1\", \"key2\":\"value2\"}" -H "Content-Type: application/json" https://example.com/abc` into the command line.


### Spring Project Layout and Running Locally

#### Step 1: Start a New Spring Project
First, navigate to **start.spring.io** to start a new Spring Boot web project.

**start.spring.io** is a website that hosts Spring Initializr, a tool used to initialize Spring Boot applications. Spring Boot is an embedded Spring framework that allows web applications to run with minimal configuration and code. After defining your Java version, build tool, and dependencies, Spring Initializr will generate a downloadable starter template for your Spring web project.

1. Check off “Maven Project”. [Maven](https://maven.apache.org/what-is-maven.html) is a developer tool that simplifies building and running a Java project, as well as managing dependencies.
2. Choose the latest version of Spring Boot.
3. Next to “Artifact” under “Project Metadata”, type “mySpringProject”. This will automatically update the “Name” and “Package name” of your Spring project.
4. Use the default version of Java (the one already marked off on the template).
5. Click on “Add Dependencies” and choose “Spring Web”. The Spring Web dependency ensures that Maven will build your web application using Spring MVC – a framework that organizes application code by their function (to learn more about MVC, check out [this article](https://www.codecademy.com/articles/mvc)) – and the Apache Tomcat Server, a popular web server for Java applications.
6. Click “Generate” to download the project.

#### Step 2: Explore the Folder Structure
Spring Boot projects are organized by a predefined Maven folder structure – a folder system that all Maven projects follow.

```
mySpringProject/
├── mySpringProject.iml
├── pom.xml
├── HELP.md
├── mvnw.cmd
├── mvnw
└── src/
    ├── test
    └── main/
        ├── resources/
        │   ├── application.properties
        │   ├── static
        │   └── templates
        └── java/
            └── com/
                └── example/
                    └── mySpringProject/
                        └── MySpringProjectApplication.java
```

##### pom.xml
Directly under the main folder “mySpringProject” is a file named **pom.xml**. POM stands for Project Object Model – an XML file that specifies and loads important project data, such as configuration, build profiles, and dependencies. All Maven projects are built using its own POM.

##### application.properties
Under **src/main/resources** navigate to and open the file **application.properties**. **application.properties** is a configuration file that specifies the properties of your Spring application. Examples of application properties can include JSON properties, data properties, server properties, and more. A Spring application will read and load properties specified in **application.properties** during project build.

##### `[ProjectName]Application.java`
Under the folder **src/main/java/com/example/mySpringProject**, navigate to and open the file **MySpringProjectApplication.java**. As you can see, the file contains the project’s `main` method, the entry point that allows a JVM (Java Virtual Machine – it comes with the JDK you installed at the beginning of this article) to execute the Java code.

#### Step 3: Implement Spring Code
1. Under the folder **src/main/java/com/example/mySpringProject** make a separate **controller** folder and make a new file **HelloController.java**.
2. Copy-and-paste the code below into **HelloController.java**.

```java
package com.example.mySpringProject.controller;
 
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;
 
@RestController
public class HelloController {
 
  @GetMapping("/helloworld")
  public String helloWorld() {
    return "Hello World!";
  }
}
```

##### A Note about Annotations
In the code snippet above, `@RestController` and `@GetMapping` are examples of different kinds of _annotations_. Annotations, recognized by their starting `@` symbol, are built-in units of Spring code that make complex functionality readily available in Spring applications. For example, the `@GetMapping("/helloworld")` annotation means that the annotated method will be executed every time the app receives a GET request to the `/helloworld` endpoint.

#### Step 4: Run Project
So how do all of these different files and annotations work together to build and run a Spring application? To put it simply, Spring Boot checks **pom.xml** and downloads its various dependencies, reads through all the annotations to determine how the code should function, and looks for the main method in the **[ProjectName]Application.java** file to run the application.

It’s now time to test out our app! In this step, we’re going to introduce two different ways to run our Spring application: (1) with a local web browser and (2) with the curl command.

In your IDE, open the terminal at the bottom and type `./mvnw spring-boot:run` (for Windows, use `mvnw spring-boot:run`). This command builds and runs your Spring Boot application with Maven.


### What is curl?
`curl` is a command-line tool for transferring data from or to a server. It supports multiple protocols, including HTTP.

`curl` provides an easy way to make requests to a server from the command line or from inside a script. It is especially helpful for testing APIs while building applications because making a request with `curl` allows you to hit endpoints for which the corresponding user interfaces do not yet exist.

For example, say you are building a cryptocurrency trading app. If you built the back-end API first, you could access your exchange rate data before even building a webpage:

```
$ curl https://api.coinbase.com/v2/prices/BTC-USD/buy  
  
{  
  "data": {  
    "base": "BTC",  
    "currency": "USD",  
    "amount": "33006.51"  
  }  
}
```

To check that `curl` is installed on your machine, simply run `curl` from the command line. If it is installed, you’ll see a message instructing you to enter `'curl --help'` to display a list of commands.

#### Making GET Requests
The most basic `curl` command is:

```shell
curl http://example.com/abc
```

This will send an HTTP `GET` request to `http://example.com/abc` and display the server’s response in the command shell.

#### Specifying a Request’s HTTP Method Using -X
By default, `curl` makes `GET` requests, but you can use the `-X` option (short for `--request`) followed by the HTTP verb (eg. `PUT`, `POST`, `DELETE`, etc.) of your choice to make other types of requests.

For example, to make a `DELETE` request to `http://sample-api.com/sample-resource/id`, you would run:

```shell
curl -X DELETE http://sample-api.com/sample-resource/id
```

or

```shell
curl --request DELETE http://sample-api.com/sample-resource/id
```

#### Adding Data to the Request Body Using -d
To send data in the body of a request made with `curl`, you can use the `-d` option (short for `--data`) followed by the data you wish to send. For example, to update the name of the user with `id=1`, run:

```shell
curl -X PUT -d "username=Lily" http://sample-api.com/users/1
```

Additional key-value pairs can be added with the ampersand `&` symbol:

```shell
curl -X PUT -d "username=Lily&height=180" http://sample-api.com/users/1
```

Note that if you include the `-d` option and do not specify an HTTP verb, `curl` will default to sending a `POST` request. That means that

```shell
curl -X POST -d "username=Lily" http://sample-api.com/users
```

and

```shell
curl -d "username=Lily" http://sample-api.com/users
```

are equivalent.

#### Setting the Request’s Content Type Using -H
By default, `curl` sends `POST/PUT` requests with the content-type `application/x-www-form-urlencoded`. If you are using `curl` to make a request to an API that expects to receive data in JSON format, you must set the request’s content-type to `application/json` by adding a request header.

Use the `-H` (short for `--header`) option, followed by the header you wish to add to your request, to specify the request’s content-type like so:

```shell
curl -d "{ \"username\": \"Lily\" }" -H "Content-Type: application/json" http://sample-api.com/users
```

The above `curl` command essentially makes the same request as the previous one but sends the data as JSON instead of a `key=value` pair. Within the command line, the data is demarcated with double quotes (`" "`). However, JSON also contains double quotes, so we use `\` to escape them.

#### Parsing Server Responses Using -i
When you make a request with `curl`, `curl` will default to only outputting the response body to the command shell. This can make it difficult to debug when your requests produce unexpected or undesirable results.

Adding the `-i` option (short for `--include`) to your `curl` commands will cause `curl` to print the response header to the command shell in addition to the response body. Knowing how to parse the response header can help you to effectively diagnose and solve problems with your requests (and/or with the server-side code that handles them).

The most instructive part of the response header is the first line, which includes the response’s [status code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status). If your request was successful (eg. a resource was successfully fetched, updated, created, or deleted) you should see a status code in the 200s.

```
 $ curl -i https://api.coinbase.com/v2/prices/BTC-USD/buy
 
HTTP/2 200
date: ...
content-type: ...
...
```

If your request was unsuccessful, you’ll want to know whether the failure was due to an error with the server-side code, or with the structure of the request itself. Status codes in the [500s](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#server_error_responses) indicate server errors, whereas status codes in the [400s](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#client_error_responses) indicate client errors.

Some of the client errors you are most likely to encounter include

- 401, which indicates that the client is not authenticated and therefore not allowed to access the specified resource
- 403, which indicates that the client is authenticated but not permitted to view the specified resource
- 404, which indicates that the specified resource cannot be found on the server


# Responding to Requests

## Spring Controllers

### Responding to Requests with Spring

#### Introduction
The Spring framework is an incredible resource to help us quickly build RESTful applications. The core functionality of these applications lies in their ability to receive requests, route them accordingly, and provide a proper response.

#### Mapping Requests in Spring
The term REST stands for REpresentational State Transfer, and it describes the architectural technique used to facilitate communication between different systems via the web. Stateless requests are sent from a client to either retrieve or make changes to a resource stored on a server. The server provides a response based on the information received in the request.

In order to provide a response to a request, the server maps the request to an endpoint. In Spring, a class is marked as a controller and each of its methods is associated with an endpoint. The method is called to formulate a response to each request. This is facilitated by two important annotations:

- The `@RestController` annotation is used to declare a class as a controller that can provide application-specific types of data as part of an HTTP response
- The `@RequestMapping` annotation is used to wire request types and endpoints to specific class methods.

The `@RestController` annotation should be added to each class that will handle responses to HTTP requests. The `@RestController` combines the functionality of two separate annotations, `@Controller` and `@ResponseBody`.

- `@Controller` is used to make a class identifiable to Spring as a component of the web application.
- `@ResponseBody` tells Spring to convert the return values of a controller’s methods to JSON and bind that JSON to the HTTP response body. Since almost every major programming language offers some type of JSON (JavaScript Object Notation) support, we can easily take an object created in Spring and translate it to JSON which can be easily parsed in the HTML and displayed on the page.

`@RequestMapping` accepts several arguments. The first, and perhaps most important, is the `path`. The path argument is used to determine where requests are mapped. For example, if a user makes a request to get a “book” resource, the server will send the request to a method with the annotation `@RequestMapping(path = "/book")` and that method would provide the response.

The `@RequestMapping` annotation also accepts several other arguments including `method`, `params`, and `consumes`.

- `method`: allows the developer to specify which HTTP method should be used when accessing the controller method. The most common are `RequestMethod.GET`, `...POST`, `...PUT`, and `...DELETE`. Since this is an optional argument, if we do not specify an HTTP method it will be defaulted to GET.
- `params`: filters requests based on given parameters.
- `consumes`: used to specify which media type can be consumed; some common media types are `"text/plain"`, `"application/JSON"`, etc.

```java
@Controller
public class VirtualLibrary{
 
  @RequestMapping("/books/all", RequestMethod.GET)
  public Book getAllBooks() {
    return getBook();
  }
 
}
```

---
We will need to declare a controller to do this. Before we can do that, we need to add an import statement that will allow us to use Spring annotations.

Add this import statement above your class declaration:

```java
import org.springframework.web.bind.annotation.RestController;
```

Add the import statement above the class declaration:

```java
import org.springframework.web.bind.annotation.RequestMapping
```

```java
package com.codecademy.ccapplication;
import java.util.List;
import java.lang.Iterable;
import java.util.Date;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.bind.annotation.RequestMapping;

@RestController
public class SuperHeroController {

  private final SuperHeroRepository superHeroRepository;
  private final SuperReportRepository superReportRepository;

  public SuperHeroController(SuperHeroRepository superHeroRepository, SuperReportRepository superReportRepository) {
    this.superHeroRepository = superHeroRepository;
    this.superReportRepository = superReportRepository;
  }

  @RequestMapping("/superHeroes")
	public Iterable<SuperHero> getSuperHeros() {
    Iterable<SuperHero> superHeroes = superHeroRepository.findAll();
    return superHeroes;
	}

}
```

#### Defining Base Paths
When the `@RequestMapping` data annotation is used at the class level, the specified path argument will become the base path. For example, a class with the data annotation `@RequestMapping("/books")` will map all appropriate requests to this class, and in this case, “/books” becomes the base path. Methods in this class can be further mapped, as shown in the previous exercise. In the example shown below, “/books” is now the base path and the `getBookThumbnails` method is associated with the endpoint “/books/thumbnails”:

```java
@RestController
@RequestMapping("/books")
public class VirtualLibrary
{
  @RequestMapping(value = "/thumbnails", method = RequestMethod.GET)
  public String[] getBookThumbnails() {
    //returns thumbnails for all available titles
  }
}
```

Note: When specifying a selection from the `RequestMethod` enum, be sure to import the annotation using:

```java
org.springframework.web.bind.annotation.RequestMethod
```

#### Using HTTP Method Annotations
In addition to using the method argument of the `@RequestMapping` annotation, Spring also offers several annotations which can be used to map to common request types. These annotations perform the same function as `@RequestMapping`. As shown in the example below, using the path and method argument of the `@RequestMapping` annotation is equivalent to just passing in a path to one of the HTTP method annotations. The four common HTTP methods we use to interact with resources are GET, POST, PUT, and DELETE.

```java
@RequestMapping("/about", method = RequestMethod.GET)
```

…is equivalent to…

```java
@GetMapping("/about")
```

See below for a table of helper methods and the requests to which they map.

|HTTP Method Annotation|Usage|
|---|---|
|`@GetMapping`|Used to specify GET requests to retrieve resources|
|`@PostMapping`|Used to specify POST requests to create new resources|
|`@PutMapping`|Used to specify PUT requests to update existing resources|
|`@DeleteMapping`|Used to specify DELETE requests to remove specific resources|

---

Make sure to import the annotations using the following statements:

```java
import org.springframework.web.bind.annotation.GetMapping; 
import org.springframework.web.bind.annotation.PostMapping;
```

#### Using Query Parameters
When users need to pass data to the server, the term we use to describe the process is called binding. The prime example of binding data from a user’s request to an endpoint occurs when a user needs to submit data. Imagine an application where you enter a book’s ISBN and the response returned is either a `yes`, indicating the book is available for checkout, or a `no`, indicating the book is not available. When the user submits their request, we need a way to bind their entry to the endpoint that will provide the response.

`@RequestParam` is an annotation that can be used at the method parameter level. It allows us to parse query parameters and capture those parameters as method arguments. This is incredibly helpful because we can take values passed in from the HTTP request, parse them, and then bind the values to a controller method for further processing. We also have the option of defining a default value for the method argument in case a value is not received from the client.

In this example, let’s say the user submits their request for a book with 2 authors and a publishing year of 1995.

```
libraryapp.com/book?author_count=2&published_year=1995
```

The `author_count` and `published_year` values would map to the method parameters as follows:

```java
@GetMapping("/book")
public Book isBookAvailable(@RequestParam int author_count, @RequestParam int published_year) {
  return books.find(author_count, published_year);
}
```

---

Add the following import statement:

```java
import org.springframework.web.bind.annotation.RequestParam
```

#### Using Template Path Variables
`@RequestParam` is perfect to use when we want to filter the results or return several resources. However, when we want to return more specific entities we can use the `@PathVariable` annotation.

`@PathVariable` maps template variables in the request URI directly to a method’s parameters. For example, we could define a template path

```
/books/{id}
```

and use the URI

```
localhost:4001/books/28937
```

to pass the path variable “28937” to a method’s `id` parameter. On the server side, we would have an endpoint that looks up books by ID as follows:

```java
@GetMapping("/{id}")
public Book isBookAvailable(@PathVariable int id)  {
  return book.findByID(id);
}
```

We’ve seen two ways to capture parameters from a request URI. `@RequestParam` captures the `id` included in the URI `/books?id=28937` and `@PathVariable` captures the `id` included in the URI `/books/28937` as long as the path includes the `{id}` variable in `books/{id}`.

---

Don’t forget to include the appropriate import statement `org.springframework.web.bind.annotation.PathVariable`.

#### Deserializing into Objects
So far we have seen how methods accept HTTP requests and how they pass data from those requests to method parameters. However, occasionally, the requests received will need to be more complex. For example, instead of receiving the first name as a string parameter from an HTTP request, perhaps we may need to receive an entire form object.

We can use the `@RequestBody` annotation on the parameters of a method. When used, this annotation allows Spring to automatically deserialize the HTTP request body into a Java object which can be bound to the method and further processed. The objects can be created by matching attributes with values in JSON.

For example, we can rewrite the previous book example with `@RequestBody` if we define a `Book` object:

```java
class Book {
  public int authorCount;
  public int publishedYear;
}
```

The new controller will have a single `Book` parameter instead of separate `authorCount` and `publishedYear` parameters:

```java
@GetMapping("/book")
public Book isBookAvailable(@RequestBody Book book) {
  return book.find(book.authorCount, book.publishedYear);
}
```

Finally, the request would need to have `authorCount` and `publishedYear` in its body (rather than the previous URL query parameters `?author_count=2&published_year=1995`):

```
curl -X POST --data
  '{\"authorCount\": \"2\", \"publishedYear\": \"1995\"}' "https://localhost:8080/.../book"
```

#### Clarifying with HTTP Status Codes
Anytime an HTTP response is transmitted, a status code is included in the response. HTTP status codes are used to determine if the request was successful or if some type of error occurred and every code has a specific meaning.

The Spring framework uses an `HttpStatus` enumeration (enum) to represent different HTTP status codes. If you are not familiar with enums in Java, you can learn about them in the [Oracle documentation](https://docs.oracle.com/javase/tutorial/java/javaOO/enum.html). See the below table for HTTP status code ranges and what each range represents.

The actual constants in the `HttpStatus` enum loosely match the status code name, e.g. a 201 Created code corresponds to `HttpStatus.CREATED` and a 400 Bad Request code corresponds to `HttpStatus.BAD_REQUEST`. [The full list is on GitHub](https://github.com/spring-projects/spring-framework/blob/main/spring-web/src/main/java/org/springframework/http/HttpStatus.java).

![[Pasted image 20230814105155.png]]

#### Fine Tuning Responses with @ResponseStatus
We know HTTP status codes can be used to determine if a request was successfully processed or if an error was generated. However, we may want to fine-tune the HTTP response to give the user more information about what occurred.

The `@ResponseStatus` annotation can be applied to methods to help with fine-tuning HTTP responses. The annotation accepts parameters for the status `code` and `reason`.

This can be used to customize messages in both failure and success responses. Consider the scenario when an admin adds a new book to the collection. When they enter all of the required information and click submit, we can use `@ResponseStatus` to return an HTTP status showing the request was successful and a reason indicating the entry was created.

```java
@PutMapping(path="/book")
@ResponseStatus(code = HttpStatus.CREATED, reason = "Book was successfully added")
public string addNewBook(@RequestParam string title) {
 
}
```

#### Exception Handling in Spring
In the previous exercise, we discussed the use of `@ResponseStatus` to apply custom HTTP status codes and reasons to an HTTP response. However, if an error is encountered, we can use `ResponseStatusException` to exert even more control over the exception handling process.

`ResponseStatusException` accepts up to 3 arguments:

- `HttpStatus code`
- `String reason`
- `Throwable cause`

In a previous exercise, we looked at a method that returns books based on the client’s ISBN submission. Clearly, the method is expecting a number, but if the client’s submission includes a character other than a number, an exception could be thrown.

In the example below, we are accepting the ID from the client as a string and parsing it into an integer. If the parse fails, a `NumberFormatException` will be thrown. This type of exception may not be so helpful if it is returned to the client. Therefore, we are catching this exception and throwing a new `ResponseStatusException` that will contain more detailed information. In this way, we have exercised more control over the exception handling process and we can let the user know why the error occurred and/or what they can do to resolve the issue.

```java
@GetMapping("/{id}")
public Book isBookAvailable(@PathVariable string id) 
{
  if (id.isNumeric()) {
    int id_int = Integer.parseInt(id)
    return book.findByID(id_int)
  } 
  else {
    throw new ResponseStatusException(HttpStatus.BAD_REQUEST, "The ID contained a non-numerical value.");
  }
}
```

Both the `ResponseStatusException` class and `@ResponseStatus` annotation can be used to specify an HTTP status code. `ResponseStatusException` is used to create specific responses dynamically, while a `@ResponseStatus` determines the status code for any response returned by the method.

```java
import org.springframework.web.server.ResponseStatusException;
import org.springframework.http.HttpStatus;
```

#### Review
- Map HTTP requests to controllers and methods (`@RestController` and `@RequestMapping`)
- Specify a path attribute to become a base path (`@RequestMapping` at the class level)
- Declare request types using HTTP method annotations (`@GetMapping`, `@PostMapping`, `@PutMapping`, and `@DeleteMapping`)
- Access request parameters in a method (`@RequestParam`)
- Bind data using template variables (`@PathVariable`)
- Fine-tune the status code returned by a method (`@ResponseStatus`)

All of these annotations and `ResponseStatusException` are imported from the `org.springframework.web.bind.annotation` package.
 

# Spring Context

## Boots and Beans

### What is a Spring Bean?

#### Introduction
The Spring framework defines a _Spring bean_ as an object managed by the Spring [Inversion of Control (IoC) container](https://docs.spring.io/spring-framework/docs/3.2.x/spring-framework-reference/html/beans.html).

The Spring IoC container’s management of beans includes several responsibilities. Perhaps the most significant of which include bean instantiation/assembly and the management of dependency injections.

#### Bean-stantiation
Imagine we are designing a racing game. For each round of the race we need a race track and drivers. We could create a class for both as shown below.

```java
public class RaceTrack {
  private String location;
  private int miles;
  private String trackType;
}
 
public class Driver {
  private String name;
  private String team;
  private int yearsExperience;
}
```

Now let’s create a class that can be used for each round of the race.

```java
public class RaceRound {
  private String startTime;
  private RaceTrack currentRaceTrack = new RaceTrack();
  private Driver currentDriver = new Driver();
}
```

For each round of the race we would need to instantiate a `RaceTrack` and a `Driver`, so we would use the `new` keyword to handle those instantiations. Any changes to those two classes would require additional changes in the `RaceRound` class.

Now let’s take a look at how instantiating the nested objects would work with Spring beans. We would first mark our `RaceTrack` and `Driver` classes as Spring beans using the `@Component` annotation:

```java
@Component
public class RaceTrack {
  private String location;
  private int miles;
  private String trackType;
}
 
@Component
public class Driver {
  private String name;
  private String team;
  private int yearsExperience;
}
```

Then we remove the actual instantiation code from `RaceRound`, instead using the `@Autowired` annotation:

```java
public class RaceRound {
  private String startTime;
  @Autowired
  private RaceTrack currentRaceTrack;
  @Autowired
  private Driver currentDriver;
}
```

Notice we are no longer using the `new` keyword when creating instances of `RaceTrack` and `Driver`.

We marked our dependent classes `RaceTrack` and `Driver` as Spring beans, which allows the IoC container to manage them, i.e. instantiate them and inject them into our `RaceRound` class.

As an additional bonus, we didn’t have to edit the existing code in our `RaceTrack` and `Driver` classes to turn them into Spring beans. All we had to add was the `@Component` annotation. There is an additional, older way to do this with XML configuration, but we’ll focus on the more modern annotations approach.

**Note**: `@Component` and `@Autowired` are just two of many annotations for working with Spring beans and the IoC container.

#### Auto-beans loading…
The fully-automatic annotations approach is facilitated using three annotations:

- `@Configuration`, which notifies the framework that beans may be created via the annotated class.
- `@ComponentScan`, which tells the framework to scan our code for components such as classes, controllers, services, etc.
- `@EnableAutoConfiguration`, which tells the container to auto-create beans from the found components.

Together these three annotations tell the framework where to start looking, how to search our code, and automatically instantiate beans from the found components.

The `@SpringBootApplication` annotation is a compilation of `@Configuration`, `@ComponentScan`, and `@EnableAutoConfiguration`. When we apply the `@SpringBootApplication` annotation to the class containing our main method, our application runs with all of this built-in functionality. Therefore, when our application starts up the container scans our code for components from which beans should be instantiated.

You can find this annotation provided in most default Spring projects:

```java
@SpringBootApplication
public class RecipeApplication {
 
  public static void main(String[] args) {
    SpringApplication.run(RecipeApplication.class, args);
  }
}
```

#### Cooking with Beans
The Spring framework represents beans as a `BeanDefinition` object. The `BeanDefinition` object has several properties, but two are particularly interesting. There is a property named `class` and there is a property named `properties`.

When we define classes, we give them a particular name, such as `RaceRound`. When the container instantiates a bean from this class it populates the `class` property of that bean with the fully qualified name we have provided. So, if the fully qualified name of our class is `com.package.RacingGame.RaceRound`, the `class` property of the bean becomes `com.package.RacingGame.RaceRound`. The `class` property is Spring’s way of representing the bean’s underlying Java type so it knows what to instantiate.

The `properties` property of the bean is populated from the properties of our class. If we have used a built-in type such as an int or a string, the container converts the property of our class into the same type of property for the bean. However, if we have used a custom type, such as `RaceTrack` or `Driver`, this is a dependency and the container now has to create a `BeanDefinition` object for each of these types as well. Ultimately, the classes we create become part of a recipe for the container to use when creating beans.

When a class encapsulates other objects, the referenced objects become a dependency for the outer class. In other words, these other objects must be created so the outer class can use it. The container takes a look at our classes and, depending on the method you choose, instantiates beans from the referenced objects (`RaceTrack` and `Driver`) before it instantiates a bean from the outer classes (`RaceRound`). Spring implements a way for the objects needed by another object to be provided as beans for others to reference. This process is known as dependency injection; Our classes no longer have to instantiate their own dependencies. Therefore, we can say the control of dependencies has been inverted back to the container, and this is why we call it an Inversion of Control (IoC) container.

#### Bean there, done that
In our previous examples, we declared our dependencies in `RaceRound` with fields and annotated them with `@Autowired`. In other Spring applications, you’ll often see dependencies injected via the constructor (which doesn’t require an annotation). In this example, the dependency is `CoffeeRepository`:

```java
public class CoffeeController {
 
  private final CoffeeRepository coffeeRepository;
 
  public CoffeeController(CoffeeRepository coffeeRepo) {
    this.coffeeRepository = coffeeRepo;
  }
}
```


### What is Spring Boot?

#### What We’ll Be Learning
In a [previous article](https://www.codecademy.com/paths/create-rest-apis-with-spring-and-java/tracks/spring-apis-spring-context/modules/boots-and-beans/articles/what-is-a-spring-bean), we learned how components of a Spring application are configured as Spring beans and injected as dependencies into other components by the Inversion of Control (IoC) container. For example, one component of web applications is the controller, and we can mark a class as a controller using the `@RestController` annotation.

```java
import org.springframework.web.bind.annotation.*;
 
@RequestMapping("/restaurants")
@RestController
public class RestaurantController {
}
```

When our app is run, this controller class will be registered as a bean and used to define routes available in our API.

If you run the application and look closely at the terminal output, you’ll notice that our app is doing a lot more than running the controller code we defined. For example:

- A `Spring Data JPA` repository is bootstrapped
- A `Tomcat` server is initialized
- A `WebApplicationContext` is initialized
- An `H2Dialect` is used
- We see an option to `Explicitly configure spring.jpa.open-in-view`
- The Tomcat server is started on `port(s): 4000`

Spring Boot is a collection of tools that extends the Spring framework and makes it easier to build applications quickly. There are too many Spring Boot tools to cover in one article, so we will focus on these four:

1. “Starters”
2. Auto-configuration
3. Custom configurations with **application.properties**
4. Distribution of your application

#### Starters
If you look at the **pom.xml** of our Spring Boot application, you’ll see the `spring-boot-start-jpa` and `spring-boot-starter-web` dependencies.

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

These are called [Spring Boot “starters”](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#using.build-systems.starters). Each one represents a set of dependencies with which to run our application. For example, the `spring-boot-starter-web` dependency instructs Spring Boot to configure Tomcat for running a server and Spring MVC (Model-View-Controller) for routing HTTP requests. `spring-boot-starter-data-jpa` sets up JPA and Hibernate for database access.

There are other starters like `spring-boot-starter-test` which includes common testing libraries such as JUnit Jupiter, Hamcrest, and Mockito, and `spring-boot-starter-parent`, which provides the `spring-boot:run` command.

#### Auto-Configuration
We understand where dependencies like Tomcat are defined, but how are they hooked into our application?

If we look at the two imports at the top of **SpringCapstoneApplication.java**, we’ll see the `SpringApplication` class and `@SpringBootApplication` annotation from the `org.springframework.boot` package:

```java
package com.codecademy.springcap;
 
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
 
@SpringBootApplication
public class SpringCapstoneApplication {
 
  public static void main(String[] args) {
    SpringApplication.run(SpringCapstoneApplication.class, args);
  }
 
}
```

#### SpringApplication
Remember when we said that the Spring IoC container configures beans for us? The `SpringApplication` class is responsible for starting up that container. We can see that in the line:

```
........ Initializing Spring embedded WebApplicationContext
```

In Java, the IoC container is represented by an _application context_. This is the thing that receives beans and enables Spring to inject them into other components. In Java, the application context appears as a `ApplicationContext` interface. In our specific case, this app is using the class `WebApplicationContext`, a web-specific implementation of `ApplicationContext`.

#### @SpringBootApplication
The `@SpringBootApplication` annotation is equivalent to `@Configuration`, `@ComponentScan`, and `@EnableAutoConfiguration`. The first two are from the Spring framework, but the third, `@EnableAutoConfiguration`, is from Spring Boot.

This annotation enables Spring Boot to review our dependencies (such as `spring-boot-starter-jpa` and `h2`) and assume the intended purpose of the application. It will configure and run the application to best fit the assumed purpose.

This explains the `Spring Data JPA`, `Tomcat`, and `H2Dialect` lines in our original code snippet: Spring Boot knows to bootstrap JPA repositories, start a `Tomcat` server, and use an H2 dialect because `spring-boot-starter-jpa`, `spring-boot-starter-web`, and `h2` are listed as dependencies in the **pom.xml**.

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
<dependency>
    <groupId>com.h2database</groupId>
    <artifactId>h2</artifactId>
    <scope>runtime</scope>
</dependency>
```

Here’s another way to explain it, from the Spring documentation:

`@EnableAutoConfiguration`…tells Spring Boot to “guess” how you want to configure Spring, based on the jar dependencies that you have added. Since spring-boot-starter-web added Tomcat and Spring MVC, the auto-configuration assumes that you are developing a web application and sets up Spring accordingly.

#### Custom Configuration with application.properties
In our original terminal output, we saw the lines:

```
........ Explicitly configure spring.jpa.open-in-view to disable this warning
........ Tomcat started on port(s): 4000 (http) with context path ''
```

When we start our application with `./mvnw spring-boot:run`, Spring Boot does some tasks by default: it makes some assumptions, like using port 8080, but it also checks for additional configuration instructions in the **application.properties** file. This allows us to make high-level changes to our application without writing any Java code.

For example, you can override the default 8080 port using:

```
server.port=4000
```

You can disable JPA warnings:

```
spring.jpa.open-in-view=false
```

Or customize the level of logging in your application:

```
logging.level.org.springframework=DEBUG
```

In the case of the downloadable application we provided, the **application.properties** file customizes the database behavior, such as the local file to use for storage:

```
spring.datasource.url=jdbc:h2:file:~/springcap
```

[A longer list of application properties are available in the Spring docs](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#application-properties).

#### Distribution
Java applications are often packaged into an executable file called a `jar`. Spring Boot provides an easy way to bundle your code and dependencies into a jar via the `spring-boot-maven-plugin` dependency. This is included by default when we download a project from [start.spring.io](https://start.spring.io/).

```xml
<build>
  <plugins>
    <plugin>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-maven-plugin</artifactId>
    </plugin>
  </plugins>
</build>
```

Note that there are other Spring Boot deployment tools such as [Spring Boot Actuator](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#actuator).


# Data with JPA

## Data Strategies

### Spring Data Options

#### Spring Data JPA and JDBC
With Spring, adding a database is easy to do with the help of a library called Spring Data JPA. _JPA_ stands for Java Persistence API, which is the underlying standard used to translate objects from Java into queries that can be sent directly to the underlying database.

Spring Data JPA “wraps” around an implementation of the JPA to make it a seamless process to integrate a database into your Spring Boot Application.

JPA does this by wrapping around another standard, JDBC (Java Database Connectivity). This is the layer that sends raw database queries to the underlying database.

JPA is a standard that can be implemented by an _ORM_ (_object-relational mapping_). The purpose of an ORM is to allow application developers to implement the required interactions with the underlying database without having to actually write database queries themselves. Instead, developers are able to work with easy-to-understand objects in their code, that the ORM “translates” or maps into queries against the underlying database relations.

For example, instead of defining a database table in SQL…

```sql
CREATE TABLE plants (
  name varchar,
  type varchar,
);
```

…we can define a plain-old Java class:

```java
public class Plant {
  private string name;
  private string type;
}
```

Instead of writing SQL queries…

```sql
SELECT name
FROM plants
WHERE name='ficus';
```

…we can use Java methods:

```java
Plant ficusName = plantRepository.findByName('ficus').name;
```

#### Hibernate, an ORM
The ORM most commonly used with Spring Data JPA is called Hibernate, and it comes packaged along with Spring Data JPA as part of the dependency, `spring-boot-starter-data-jpa`.

You will not need to know the details of the relationship between Spring Data JPA, the Hibernate ORM, and the JDBC to write a database-integrated application. Spring Data JPA allows developers to ignore all the complexity of the internals. Instead, they can call straightforward methods on objects to achieve the required interactions with the database. Using Spring Data JPA, an application developer won’t need to know any SQL at all, but can still build a rich application backed by a database.

#### Database Types
Spring Data JPA supports many different kinds of databases right out of the box. This means that, even if the underlying database technology changes, the code may remain the same.

For example, we could start with a database like MySQL, but if we eventually change the database behind your application to be PostgreSQL instead, we won’t have to change anything about your application logic. The application developer would simply update the configuration of the Spring Boot application to point to the new database.

This convenience is all thanks to the JPA standard. As long as [appropriate JDBC drivers exist for a given database](https://github.com/spring-projects/spring-boot/blob/main/spring-boot-project/spring-boot/src/main/java/org/springframework/boot/jdbc/DatabaseDriver.java), implementations of the JPA will be able to translate Java objects to the right SQL queries, which may be different between databases.

Typically, a database will run separately from an application, in a different physical location than where the application runs. This is because databases have different requirements than applications in terms of what it takes to keep them running and resilient. _Infrastructure_ is the generic term for the machines that applications and databases run on.

#### H2, a Database Type
One such database is H2. H2 is a relational database written entirely in Java. One convenient feature of H2 is that it can run on the same kind of infrastructure as your application and can run entirely “in-memory”. This makes it easy to use to test your Spring Boot application on your machine, without having to obtain a database server from elsewhere for your application to use. H2 can run alongside your application, running in the background when your application starts up. This is all made possible without the developer having to do any additional work to set it up.

To connect to an embedded H2 database using Spring Data JPA, we’ll need to update your application’s _properties_. Spring uses a properties file to store information that your application depends on. The type of information that is typically stored inside properties files includes:

- the database URL
- the number of logs your application should produce
- the “port” your application runs on

When our Spring Boot application starts, it will check the properties file, located at **src/main/resources/application.properties**, for any information that it might require to configure your application correctly. This example adds a `plants.db` database, which might be used by a botanist to track their inventory.

```
spring.datasource.url=jdbc:h2:~/plants.db
spring.datasource.driverClassName=org.h2.Driver
```

#### Conclusion
- _Spring Data JPA_ is available in the `spring-boot-starter-data-jpa` dependency
- Spring Data JPA is an implementation of the Java Persistence API, or JPA
- The object-relational mapping tool, or _ORM_, provided by Spring Data JPA is called Hibernate. It provides Java methods that can be translated into SQL queries
- The standard that defines the relationship between Java code and SQL queries is called Java Database Connectivity, or _JDBC_.
- There are many different databases that Spring Data JPA can work with. _H2_ is one of those. It differs from the other databases in that it can run in-memory, meaning that developers don’t have to set up and connect to a separate database to get their app working.
- The database type is specified in **application.properties**


## Spring Data and JPA

### Add a Database with JPA

#### What is Spring Data JPA?
Spring Data JPA is a library for Spring that helps to integrate a database into your REST API.

---

To be able to use `spring-boot-starter-data-jpa` in your project, you’ll have to add that dependency to your **pom.xml**, where all the dependencies for the project are kept.

Add the following block underneath the `<dependencies>` tag in the **pom.xml**:

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
```

#### Connecting to a Database
To connect to an embedded H2 database using Spring Data JPA, we’ll need to update your application’s _properties_. Spring uses a **properties file** to store information that your application depends on. The type of information that is typically stored inside properties files includes:

- the database URL
- the amount of logs your application should produce
- the “port” your application runs on

When our Spring Boot application starts, it will check the properties file, located at **src/main/resources/application.properties**, for any information that it might require to configure our application correctly.

---

To use the embedded H2 database, we’ll first need to add it as a dependency. In the same way that you added the `spring-boot-starter-data-jpa` dependency, add another dependency:

```xml
<dependency>
  <groupId>com.h2database</groupId>
  <artifactId>h2</artifactId>
  <scope>runtime</scope>
</dependency>
```

To connect to an embedded H2 database to run our application with, we will need to add the correct properties to the properties file.

Find the properties file for our application, and add the following lines:

```
spring.datasource.url=jdbc:h2:~/plants.db
spring.datasource.driverClassName=org.h2.Driver
```

This will tell Spring both where the database is stored, as well as what library it should use to “translate” our Java objects into SQL queries that H2 can understand.

#### Create a Model
As mentioned earlier, Spring Data JPA is an _abstraction_ layer that allows us to interact with objects in your code rather than write SQL queries.

These objects, in this context, are referred to as _models_ (or _entities_). Typically, we write Java classes and use annotations to identify them as models to Spring Data JPA. Then, Spring Data JPA sends instructions to the Hibernate ORM to execute the correct SQL statements depending on the methods that we’ve called on our model and the annotations we’ve put on its fields.

You can imagine that a model corresponds to a database table, and a field in a model corresponds to a column in that table. An application developer will use annotations to indicate how the model name and field names translate to the underlying table name and column names, respectively.

Below, you’ll see a **P**lain **O**ld **J**ava **O**bject (a _POJO_) that represents a person, storing their attributes as _fields_ of our POJO.

```java
// Person, a Plain Old Java Object (POJO), that we use to represent a person.
public class Person {
 
  // An ID to uniquely identify the person we are storing in our db
  private Integer id;
 
  private String name;
  private Integer age;
  private String eyeColor;
}
```

Now that we have a baseline representation of what a `Person` is and what we wish to store about them, we can add annotations from JPA that help define how our Java object will map to a database relation.

```java
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.Id;
import javax.persistence.Column;
import javax.persistence.Table;
 
@Entity
@Table(name="PEOPLE")
public class Person {
 
    @Id
    @GeneratedValue
    private Integer id;
 
    @Column(name="NAME")
    private String name;
 
    @Column(name="AGE")
    private Integer age;
 
    @Column(name="EYE_COLOR")
    private String eyeColor;
 
}
```

In the example, we start with importing all of the annotations that we’ll need. These annotations come from the JPA library, which comes along with the `spring-boot-starter-data-jpa` dependency.

Then, we add in all the required annotations that define the translation between our POJO and our database relation:

- `@Entity`: tells the ORM that this model will be used to represent a table or relation in our database
- `@Table`: tells the ORM what table name in the underlying database that this model corresponds to. Here, it is used to say that the `Person` entity represents a single entry in the `"PEOPLE"` table of the underlying database.
- `@Id`: tells the ORM that this field (`id`) will be used to uniquely identify a single entry in our `"PEOPLE"` relation
- `@GeneratedValue`: tells the ORM that the developer will not be supplying the value for this field themselves. Instead, it should be “auto-generated” by the database. Typically, an `@Id` field for an entity will be auto-generated in this way, so that we can leverage the database to guarantee that the ID will always be unique.
- `@Column`: tells the ORM what column in the underlying relation that the annotated field corresponds to. For example, the `eyeColor` field of our entity corresponds to the `"EYE_COLOR"` column in the `"PEOPLE"` relation.

There are many more annotations that JPA provides to help define more complex relationships between a model and its underlying relation in the database. You can read more about them [here](https://docs.oracle.com/javaee/7/api/javax/persistence/package-summary.html) under the _Annotation Types Summary_ heading.

When the ORM interacts with your model, it depends on “getter” and “setter” methods that have been appropriately named based on the fields. For the `Person` class, we would additionally need to add getter and setter methods for every field to ensure that the ORM can access and modify fields in the model as required.

We won’t write out the whole class again, but you can imagine that the `age` field, for example, would have a getter and setter like this:

```java
@Column(name="AGE")
private Integer age;
 
public Integer getAge() {
  return this.age;
}
 
public void setAge(Integer age) {
  this.age = age;
}
```

#### Create a Repository
Now that we have learned how data models are defined, the next step is to determine how to use the model to interact with the database. Spring Data JPA uses _repositories_ to accomplish this. A repository is a data access and manipulation layer that wraps around your data model. A repository will come with methods to call on instances of your data model like `.save()`, or `.findAll()`, or `.findById()`, enabling a no-code solution to interacting with a data model in a Spring Boot application.

When developers build APIs that interact with or manage an underlying data model, there are usually some common functionalities that they want to enable. An API that manages a data model should be able to **C**reate, **R**ead, **U**pdate, and **D**elete instances of the model. For this reason, these kinds of APIs are called **CRUD** APIs.

Since this kind of functionality is so common, Spring Data JPA comes with a special kind of repository interface that gives you full CRUD functionality for your model. To use it, an application developer simply imports the repository interface, tells it what model it should wrap around, and it is good to use!

Here’s an example of how the `CrudRepository` interface would work with the `Person` class from the previous exercise:

```java
import org.springframework.data.repository.CrudRepository;
 
import com.codecademy.people.entities.Person;
 
// creating an extension of the CrudRepository that can manage our Person model
public interface PersonRepository extends CrudRepository<Person, Integer> {
  // no method declarations are required! }
```

In this example, we create a new interface that extends the `CrudRepository`, and parameterize it with our `Person` model and the type of its ID field, `Integer`.

The angle brackets (`< >`) are a special kind of syntax used in Java to provide more specific type information to a class, using [type parameters](https://docs.oracle.com/javase/tutorial/java/generics/types.html). You may have seen these used when we have a `List` of things in Java, like `List<Integer>`. In this example, the first type parameter is used to ensure that our `PersonRepository` knows it is responsible for managing instances of the `Person` object. The second type parameter is used to tell the repository the type of the `ID` field, which enables methods like `.findById`.

Some methods that the `CrudRepository` interface offers us to enable CRUD functionality are:

- `.findById(Integer id)`: allows you to query the database to find an instance of your model by its ID field
- `.findAll()`: allows you to retrieve ALL the entries in the database for a given model
- `.save(Person p)`: allows you to create AND modify instances of your model in the database
- `.delete(Person p)`: allows you to delete instances of your model from the database

#### Connect Your Repository to a Controller
The repository interfaces provided by Spring Data JPA, such as `CrudRepository`, are very powerful for managing data without having to write too much code. However, they are not of much use without a way for an end user of your API to interact with them.

When a user wishes to interact with your API, they do so by making **REST** calls to a `RestController`. A `RestController` is used as the layer of the application that takes requests from the user and accordingly sends commands to the repository or data access layer to accomplish what task the user requested in their REST call.

The repository must be a dependency of the controller, and you can make the repository _bean_ available to the controller class using _dependency injection_.

Since the extension of the `CrudRepository` will be used in the “Spring context,” it is implicitly a _bean_.

To make a bean available to a class that depends on it, you can simply add it as a field of the class and include it in the constructor. Spring Boot will automatically “wire” in the dependency when it discovers the dependency in the Spring context. For the `PersonRepository` example, we could have a `PersonController` that looks like:

```java
import org.springframework.web.bind.annotation.RestController;
 
import com.codecademy.people.repositories.PersonRepository;
 
@RestController
public class PersonController {
  private final PersonRepository personRepository;
 
  public PersonController(final PersonRepository personRepository) {
    this.personRepository = personRepository;
  }
 
  // ... all REST endpoint mappings
}
```

To make the `PersonRepository` available to the `PersonController` as a dependency, all that had to be done was:

- Import the `PersonRepository` from the correct package
- Add the `PersonRepository` as a field in the `PersonController` class
- Add the `PersonRepository` to the constructor and assign it to the field appropriately

#### Make Queries to Your Database: findAll
Now that you can communicate between your controller and your data access layer, you’ve bridged the gap between an end user of your API and the database.

One of the fastest ways to test this functionality is by implementing some `GET` endpoints in the controller. The `GET` request should be used to retrieve information out of your database, so it makes sense that a `GET` request should trigger repository methods like `.findAll()` or `.findById(Integer id)`.

Continuing the example of the `Person` model, our `PersonController` may include some `@GetMapping`s to accomplish this:

```java
import java.lang.Iterable;
import java.util.Optional;

import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.bind.annotation.GetMapping;

import com.codecademy.people.entities.Person;
import com.codecademy.people.repositories.PersonRepository;

@RestController
public class PersonController {

  private final PersonRepository personRepository;

  public PersonController(final PersonRepository personRepository) {
    this.personRepository = personRepository;
  }

  @GetMapping("/people")
  public Iterable<Person> getAllPeople() {
    return this.personRepository.findAll();
  }

  @GetMapping("/people/{id}")
  public Optional<Person> getPersonById(@PathVariable("id") Integer id) {
    return this.personRepository.findById(id);
  }

}
```

In this example, the `"/people"` endpoint of this API will fetch all `Person` entries from the `PersonRepository` using the `.findAll()` method offered by the `CrudRepository`. It returns an `Iterable`, which is just a simplified interface for a collection in Java. Note that the `Iterable` has a _type parameter_, `Person`.

#### Make Queries to Your Database: findById
Rather than get all items, our API users may want to find a specific entity in the database. For this kind of request, we can use `CrudRepository` methods like `.findById(Integer id)`.

Continuing the example of the `Person` model, we would add this endpoint to our `PersonController`:

```java
import java.util.Optional;
// Other imports and class scaffolding omitted

@GetMapping("/people/{id}")
public Optional<Person> getPersonById(@PathVariable("id") Integer id) {
  return this.personRepository.findById(id);
}
```

Note that this method returns an `Optional<Person>`. This is because the user may pass an ID that does not exist in the database. The `Optional` type from Java will allow the response to gracefully return `null` in the response body if the `id` supplied could not be found in the database.

#### Create a New Database Entry
Conventionally, a `GET` request is used when you wish to GET information from the database. Similarly, a `POST` request is used when we wish to create new information in the database.

With Spring Data JPA’s `CrudRepository`, you can use the `.save()` method to create records in the database. The `.save()` method accepts your model as a parameter, and uses all the annotations you added to indicate the columns as its basis when it uses the ORM to create the underlying SQL `INSERT` statement.

```java
@PostMapping("/people")
public Person createNewPerson(@RequestBody Person person) {
  Person newPerson = this.personRepository.save(person);
  return newPerson;
}
```

In this example, the end user of the API would pass in a `Person` using the body of their `POST` request. To save this person to our database, we use the `.save` method from the `PersonRepository`. The `.save` method returns a `Person` as well, and the only difference between this `newPerson` and the original `person` passed by the user is that the `newPerson` will have an `id` field, generated by means of the `@GeneratedValue` annotation from the model definition.

Lastly, this `newPerson` is returned in the response body, so that the end user can know the ID that was assigned to the new entry they created in the database.

#### Update a Database Entry
The `.save` method from the `CrudRepository` interface can be used both for creating new entries in the database as well as updating existing entries.

A common flow is to fetch an entry from the database by its ID, update some attribute of the entry, and then call `.save` again to persist the change.

Like how `GET` requests are used for reading entries from the database, and `POST` requests are used for creating new entries in the database, convention dictates that you should use `PUT` requests to update entries in the database.

```java
@PutMapping("/people/{id}")
public Person updatePerson(@PathVariable("id") Integer id, @RequestBody Person p) {
  Optional<Person> personToUpdateOptional = this.personRepository.findById(id);
  if (!personToUpdateOptional.isPresent()) {
    return null;
  }

  // Since isPresent() was true, we can .get() the Person object out of the Optional
  Person personToUpdate = personToUpdateOptional.get();

  if (p.getName() != null) {
    personToUpdate.setName(p.getName());
  }
  if (p.getAge() != null) {
    personToUpdate.setAge(p.getAge());
  }
  if (p.getEyeColor() != null) {
    personToUpdate.setEyeColor(p.getEyeColor());
  }

  Person updatedPerson = this.personRepository.save(personToUpdate);
  return updatedPerson;
}
```

The `Person` object passed in the request body is used to store the new field values that should be used to update the targeted entry. It does not need to have ALL the fields that a `Person` has. When Spring Boot (via Jackson) converts the request body to a `Person` object, it simply sets any fields that are missing to `null`. Because of this, we are able to use a single endpoint to update any field of the `Person`. We can use `if` statements to update a field of the target database entry ONLY IF the corresponding field in the request body object was not null.

#### Delete a Database Entry
Implementing a `DELETE` endpoint that can **D**elete a database entry is straightforward. The `CrudRepository` offers a `delete` method that accepts the instance of the model that you wish to delete.

```java
@DeleteMapping("/people/{id}")
public Person deletePerson(@PathVariable("id") Integer id) {
  Optional<Person> personToDeleteOptional = this.personRepository.findById(id);
  if (!personToDeleteOptional.isPresent()) {
    return null;
  }
  Person personToDelete = personToDeleteOptional.get();
  this.personRepository.delete(personToDelete);
  return personToDelete;
}
```

Notice that the `.delete` method differs slightly from the `.save` method that we have seen, in that it does not `return` anything. Instead of depending on the output of the `.delete` method to give a response back to the user of the API, we capture the object before it is deleted using `.findById`, and return that object to the user after the `personToDelete` has been deleted.

As was the case for getting and updating a plant by ID, we should use the `Optional` methods to check to see if the `id` supplied was valid, and terminate the method early by returning `null` if it was not present in the database.

#### Review
- **C**reate plants in the database by making **POST** requests and the `.save` method of `CrudRepository`
- **R**ead plants in the database by making **GET** requests and the `.findAll()` and `.findById()` methods of `CrudRepository`
- **U**pdate plants in the database by using getters and setters to check and modify fields in the `Plant` **entity**, and the `.save` method of `CrudRepository`
- **D**elete plants in the database by using the `.delete` method of the `CrudRepository`.


### Custom Queries with JPA

#### Introduction
Spring Data JPA’s `CrudRepository` interface is even more powerful than basic `findAll` and `findById` queries. We can add custom filter queries to our extension of the `CrudRepository` simply by adding a properly formatted method name to the interface. You don’t even have to implement the method!

For example, say we have a `Person` entity with a `String eyeColor` field, and we wish to query people in the database that have a certain `eyeColor`. We can simply add a method declaration to the `PersonRepository`:

```java
package com.codecademy.people.repositories;

import java.util.List;

import org.springframework.data.repository.CrudRepository;

import com.codecademy.people.entities.Person;

public interface PersonRepository extends CrudRepository<Person, Integer> {
  // this declaration is all we need!
  List<Person> findByEyeColor(String eyeColor); 
}
```

Based on how the method is named (`findByEyeColor`), Spring Data JPA will automatically generate the “implementation” of the method when your application is compiled.

To use our newly defined `findByEyeColor` method, we could implement a new `GET /people/search` endpoint in the `PersonController`.

```java
@GetMapping("/people/search")
public List<Person> searchPeople(
  @RequestParam(name = "eyeColor", required = false) String eyeColor
) {
  if (eyeColor != null) {
    return this.personRepository.findByEyeColor(eyeColor)
  } else {
    return new ArrayList<>();
  }
}
```

In the endpoint implementation above, we use query parameters with the `@RequestParam` annotation. This is the common convention in REST APIs when passing in parameters used for searching or filtering.

1. The naming of the method declarations is extremely important here. The rules for the method names are detailed in [the Spring documentation here](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#jpa.query-methods.query-creation).
2. We added `required = false` inside the `@RequestParam` annotation.

---

```java
public interface PlantRepository extends CrudRepository<Plant, Integer> {
  List<Plant> findByHasFruitTrue();
}
```

#### Advanced Custom Queries
Notice that we added `required = false` inside our previous `@RequestParam` annotation. This allows us to optionally add more query parameters if the user would like to search by a different field value instead. For example, we could extend the `PersonRepository` interface with another method:

```java
List<Person> findByAgeLessThan(Integer age);
```

and update the `searchPeople` method accordingly:

```java
@GetMapping("/people/search")
public List<Person> searchPeople(
  @RequestParam(name = "eyeColor", required = false) String eyeColor,
  @RequestParam(name = "maxAge", required = false) Integer maxAge 
) {
  if (eyeColor != null) {
    return this.personRepository.findByEyeColor(eyeColor)
  } else if (maxAge != null) {
    return this.personRepository.findByAgeLessThan(maxAge);
  } else {
    return new ArrayList<>();
  }
}
```

You can get even more advanced using `And` queries, so that you could query the `PEOPLE` table by both `eyeColor` and `maxAge` at the same time. The new method declaration in the interface would look like:

```java
List<Person> findByEyeColorAndAgeLessThan(String eyeColor, Integer age);
```

The updated `searchPeople` method would look like:

```java
@GetMapping("/people/search")
public List<Person> searchPeople(
  @RequestParam(name = "eyeColor", required = false) String eyeColor,
  @RequestParam(name = "maxAge", required = false) Integer maxAge 
) {
  if (eyeColor != null && maxAge != null) {
    return this.personRepository.findByEyeColorAndAgeLessThan(eyeColor, maxAge);
  } else if (eyeColor != null) {
    return this.personRepository.findByEyeColor(eyeColor);
  } else if (maxAge != null) {
    return this.personRepository.findByAgeLessThan(maxAge);
  } else {
    return new ArrayList<>();
  }
}
```

---

As a reminder, `@RequestParam` is case-sensitive. `hasFruit=true` will work but `hasfruit=true` will not.

#### Review
- We can add custom filter queries to our extension of the `CrudRepository` simply by adding a properly formatted method name to the interface
- We do not need to write the method bodies
- The rules for defining custom queries is in [the Spring documentation](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#jpa.query-methods.query-creation)
- We can create advanced query logic by adding phrases such as `And` and `LessThan` into the method name

---

Lastly, add one more annotation to the `type` field:

```java
@Enumerated(EnumType.STRING)
```

This is used to ensure that Spring Data JPA knows that a `BootType` is just a `String`.


### Working with the H2 Console

https://www.baeldung.com/spring-boot-h2-database
 






