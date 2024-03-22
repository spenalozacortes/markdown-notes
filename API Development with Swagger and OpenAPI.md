# Introduction to API Development

## Introduction to the API Development Lifecycle

### What is the API development lifecycle?
While there are many frameworks and methodologies for the API lifecycle, there are typically five chronological stages:

1. Planning and Designing the API
2. Developing the API
3. Testing the API
4. Deploying and Managing the API
5. Retiring the API

### Planning and Designing the API
This stage involves ideating and mapping out the various resources and operations and their associated use cases before the API is fully implemented in code.

Typically business team members (or sometimes even engineers) will begin by mapping out the capabilities of the API and the data it should expose. This process usually captures the API audience’s needs and the requirements from various stakeholders.

When the API requirements are done being mapped out, engineering teams can then begin laying out the architecture of the API. Naming conventions, protocols, technology, and much more are debated and finalized.

### Developing the API
Once the requirements are mapped out and the engineering team has a plan, the development stage begins. This stage focuses on implementing the API based on the plan and design and is when engineering teams will do the necessary work to bring the API to life.

Typically this is also where the API is documented. Often when APIs are treated as a product (that the team or business makes revenue from), teams will spend just as much time documenting their API as they will on any of the other phases.

### Testing the API
In the testing phase, the API would be thoroughly tested and monitored for performance issues. This phase typically catches any issues so that engineering teams can refine the API before it is released to the _end-users_ (sometimes referred to as _end-consumers_) — the person or persons who will use the product (e.g., the API).

### Deploying and Managing the API
Ultimately, APIs must satisfy a use case for an end consumer, be it an internal developer team, a partner company, or the general public. After the testing phase, APIs are ready for release and are deployed to a secure environment to facilitate easy discovery and consumption.

On some occasions, mainly when APIs are public-facing, APIs are released into beta where end-users (sometimes only a small percentage) can test and experiment with the API and give feedback and report bugs. The beta helps finalize any outstanding issues as well as gain valuable feedback before a full API release.

This phase is also where APIs are managed for the rest of their lifetime to deliver guaranteed and high-quality API performance. Management includes but is not limited to performance tracking, usage analysis, community building, and a lot more!

### Retiring the API
Lastly, the final phase of the API lifecycle is deprecation. This phase is where support for an API’s version, or in many cases, an entire API itself, is discontinued.

Deprecation involves creating a detailed plan on migrating users away from the API and releasing the APIs resources. Deprecation needs to be handled with extreme care as it may impact many end-users and associated products that utilize the API.

## API Design Guide

### Defining API design and why it matters
API design is defined as the iterative collection of decisions that lead to a concrete plan for developing, implementing, and maintaining an API. The design process is not just about the developers who are building the API but also about understanding the API’s end-user, their needs, and how best the API can meet those needs. There are notable benefits in investing time and resources into the design phase of the API development lifecycle. Some of the benefits include:

- **Effective Implementation**: A detailed API design can significantly help in the APIs implementation (usually by developers) phase by preventing ambiguity.
- **Incremental Development**: Having a straightforward design helps know precisely which resource, or sub-resources, would need to be updated (or retired), preventing confusion and leading to less duplicated work.
- **Better Documentation**: A solid initial API design makes documenting the API faster and less error-prone.

### Characteristics of a Well-Designed API
Typically, a well-designed API will have the following characteristics:

- **Easy to read and work with**: A well-designed API will be easy to work with, and its resources and associated operations can quickly be memorized by developers who work with it regularly.
- **Hard to misuse**: Implementing and integrating with a well-designed API will be a straightforward process and less error-prone. It has informative feedback and doesn’t enforce strict guidelines on the API’s end-user.
- **Complete and concise**: A well-designed API is a complete API. This means the API exposes any data that the end-user expects it to expose. Most APIs are completed over a long period of time – implementing end-user feedback and releasing new versions along the way.
- **Well documented**: Finding any information about endpoints, integrations, and features should be simple with a well-designed API. The documentation will cover and explain all the available functionality of the API.
- **Reliable**: An API’s end-user will depend on an API to be available and functioning when they need it. They also expect functionality to not arbitrarily change without any proper notice.

Keep this application in mind as we will explore the best practices of three distinct parts of an APIs design:

- Collections, Resources, and Their URLs
- Requests
- Responses

### Collections, Resources, and Their URLs

#### Nouns are Your Best Friend
For any resource or collection that represents some data in an API, the base URL should always be neat, elegant, and, most importantly, intuitive. A long and difficult-to-read base URL is not just bad to look at but can also provide a more error-prone and challenging experience for the end-user.

|API Route|Purpose|HTTP Verb|
|---|---|---|
|/photos|Retrieve all photos|GET|
|/photos/1|Retrieve a single photo|GET|

#### Describe resource functionality with HTTP methods
Recall, RESTful APIs are comprised majorly of HTTP methods that have well-defined and unique actions for any resource. These methods help all APIs achieve a level of consistency in the type of operations end-users expect to occur when using an HTTP method.

|HTTP Verb|Description|Example|
|---|---|---|
|GET|Retrieve a resource|GET /photos/1|
|POST|Add a resource|POST /photos|
|PUT|Update a resource|PUT /photos/34|
|PATCH|Update a resource|PATCH /photos/4|
|DELETE|Delete a resource|DELETE /photos/12|

### Responses

#### Give Feedback to Help Developers Succeed
Providing good feedback to developers on how well they are using an API goes a long way in improving adoption and retention. Good feedback involves positive validation on correct implementations and an informative error on incorrect implementations that can help developers debug and correct how they use the API.

For APIs, errors (and relevant error codes) are a great way to provide context when things go wrong! In general, there are three possible error outcomes when using an API:

1. The client application behaved erroneously (client error - 4xx response code)
2. The API behaved erroneously (server error - 5xx response code)
3. The client and API worked (success - 2xx response code)

When designing an API, describe these error responses well, but keep them concise and neat. In addition, use specific response codes to detail errors accordingly in the API ([check out this great resource on error codes](http://www.restapitutorial.com/httpstatuscodes.html)). Lastly, provide enough information in the error codes for an end-user to start work on fixing the cause, and, if there’s more information needed, provide links to additional documentation.

### Requests

#### Handle complex requests elegantly
An API should be able to access many different types of data, so we want to be mindful of organizing it to best help our end-user. We want to make sure that our data is complete, available, and accounts for relationships between different types of data. In the interest of performance, we’d only want to surface the relevant data that an end-user needs and even consider limiting the amount of data they get in the response.

One way to account for specific properties and limit responses is to use a _query parameter_, adding a `?` with key-value pairs that list out what a user needs.

If the user wants to find the top 10 photos in Boston with a hashtag `#winter`, the call would be:

```
GET /photos?location=boston&hashtag=winter&limit=10
```

Also, when in doubt, leave it out. Developing and maintaining APIs is a continuous process, so we can wait for feedback from our end-users to see how we can improve our API. This way, we account for the immediate and future needs of the API.

## Introduction to API Documentation

### Defining API Documentation
API documentation is technical content containing instructions about how to effectively use and integrate with an API.

### Benefits of Well-Crafted API Documentation

- **Improved End-User Adoption:** Adoption patterns are already shifting towards developers in the technology sphere. One big reason for having good API documentation is that it improves the experience for developers using the API, which directly correlates with API adoption.
- **Improved Developer Experience (DX):** The third-party developer, typically one of many end-users for an API, is busy solving complex programming challenges. These developers want to integrate as quickly as possible to move forward in their software development, meaning they should immediately understand the value and usage of the API. The aggregate experience of the developer when discovering, learning to use, and finally integrating with an API is termed as _developer experience_ (DX) — and excellent API documentation is the key to a great DX.
- **Increased Awareness:** Satisfied end-users will be an APIs biggest advocates.
- **Saves Support Time and Costs:** In addition to driving increased awareness and adoption of an API, good documentation also decreases the amount of time spent onboarding new end-users, be it internal developers or external partners. Poor or no documentation means more frustrated users rely on a team to understand how to work with the API.
- **Easier Maintenance:** Documentation leads to good API maintenance. It helps internal teams know the details of an API’s resources, methods, and their associated requests and responses, making maintenance and updates quicker.

## API Documentation Best Practices

### Who is the API documentation for?
Most likely, an API is meant to solve real-world problems faced by companies in a specific industry and will directly be integrated into applications by software engineers. As such, there are two types of potential audiences of an API who will influence an API’s consumption and its adoption usage:

- **Decision-makers:** Decision-makers are the people who evaluate an APIs services and decide if it makes sense for the development team to spend time exploring the service. They are looking to use an API to solve potential challenges in their product or service strategy. In many cases, they don’t directly work with the API, but they are the main points of contact for influencing an organization’s decision to consume it. Examples of decision-makers are CTOs or Product Managers.
- **Users:** Users are the people who will be directly working with an API. They need to learn the ins and outs of the API and how it applies to their use case. This could mean learning how to call and integrate with many, or all, of the resources the API exposes. They are critical to the sustainability of an API. They are analytical, work on significant and complex engineering problems, and have a shortage of time. Hence, an API must be easy to use and have excellent documentation so these users can successfully integrate with an API as quickly as possible. Examples of API users are front-end and back-end developers.

Ideally, an API’s documentation needs to cater to both personas.

### Best Practices in API Documentation

#### Detailed Error Messages
Error messages are important because they tell end-users when they’re integrating with an API incorrectly. Explain error standards and provide solutions on how to overcome them when an end-user gets an error.

#### A List of All Exposed Resources
Resources are the core components of an API that end-users will constantly be interacting with. An API should list all of its exposed resources and understand how end-users may integrate with them.

#### A Terms of Use Agreement
Terms of use is a legal agreement between the end-user and an organization, defining how the end-user should ideally use the API’s services. These terms should include API limits under best practices, with terms and conditions. Constraints also need to be clearly stated so that end-users understand what API usage and practices are permitted, so they don’t accidentally have their access restricted.

#### A Changelog
A changelog is a document, usually published on an APIs website, that should detail updates and versions of an API and how it might affect API end-users. This will help end-users know the stability of the API and see if any changes need to be made to their integration with the API.

#### Less Technical Jargon
Keep in mind that many end-users working with an API may not have intimate knowledge of the domain to understand technical jargon. Documentation should cater to the “very technical” developer audience and the less technical decision-makers. A big mistake technical writing teams make is assuming their audience is entirely technical and has a complete understanding of how to work with APIs. If an API does have technical or domain-specific jargon, it is helpful to link those specific items to further documentation explaining the terms.

#### Examples of all Requests and Responses
An API call response is a guide for end-users, indicating whether they’re on the right track or are doing something wrong. An API end-user should know exactly what to expect from a successful API call. Ideally, an API provides examples for every single object it is supposed to return and examples of parameters that end-users can add for a successful call.

It is also best to describe the entire sample response body in every supported format. Think of standard formats like XML or JSON, but also HTTP headers, error codes, and messages.

#### An Authentication Guide
An API’s documentation should have a section dedicated to any authentication (if it exists) required to start consuming the API’s data. Most APIs have authentication schemes, and end-users have to authenticate before gaining access to the API.

### Arm Documentation with Resources

#### A Getting Started Guide
The getting started guide provides a detailed account of how to start working with the API quickly. The emphasis in the guide should be on ensuring end-users reach success with the API as soon as possible, hand-holding them throughout the journey.

#### SDKs and Libraries
Code libraries help developers quickly call different resources. Having quick and easy methods in different languages to work with an API allows developers to feel more comfortable working with it. _Software Development Kits_ (SDKs) - a set of libraries or tools that end-users can work with out of the box, are challenging to build, and aren’t crucial for launch, but can significantly improve API adoption.

#### A Interactive Console
One way to encourage end-users to test what they read in the API documentation immediately, is to provide an interactive API console. Experimentation is powerful, and a console makes getting started easy, with limited liability from the end-users perspective. An interactive console can go a long way in helping developers learn about an API’s value very quickly.

# Design First API Design

## Design First vs Code First

### Introduction
When it comes to using API development, two popular schools of thought have emerged: The “Design First” and the “Code First” approach to API development.

First, the concept of the API starts with a team (or individual) identifying an opportunity. The opportunity is analyzed, and a plan to capitalize on it is created in a text document by strategists, analysts, and other business folks. This document is then passed along to the development team, where the plan takes some tangible form. There are two possibilities from here on to develop the API:

1. **Design First:** The API design plan is converted to a human and machine-readable contract from which the code is built.
2. **Code First:** Based on a business plan, an API is directly coded, from which a human and machine-readable document can be generated.

Both approaches depend on a _API contract_ - a document, usually written in a human and machine-readable language (e.g., JSON, YAML) that describes the API’s capabilities, endpoints, and finer details. Typically the API contract serves both as a plan for the API implementation but also as the APIs documentation.

In the “Design-First” approach, the API contract serves as a blueprint for the APIs structure and features and guides the development process. In the “Code-First” approach, since the API is already implemented, it typically serves the role of documentation.

### Choosing the right approach
There are advantages and disadvantages associated with both approaches. Choosing the right approach boils down to a team’s immediate technological and strategic needs that they wish to solve with the API.

#### Design First Approach

##### When Developer Experience Matters
A well-designed API can do wonders for the adoption and consumption of the API, and good design is typically better achieved with the Design First approach (since it is in the earlier stages of the lifecycle). If an APIs strategy involves the need for high adoption and retention of users integrating with the API, then good Developers Experience (DX) matters.

##### When Delivering Mission Critical APIs
The biggest reason to adopt the Design First approach is when an APIs target audiences are external customers or partners. In such a case, the API is a crucial distribution channel so that end-users can consume the services we want to provide, and good design plays a key role in determining customer satisfaction.

##### When Ensuring Good Communication
The API contract can act as the central draft that keeps all team members aligned on an API’s objectives and how the API’s resources will be exposed. Identifying bugs and issues in the APIs architecture with a team becomes more straightforward when working with a human-readable design document such as the API contract. Spotting issues in the design before writing any code is a much more efficient and streamlined approach than doing so after the implementation is already in place.

#### Code First Approach

##### When Delivery Speedy Matters
Developers can start implementing an API much faster by coding the API directly from the requirements document. This is important if an APIs go-to-market strategy emphasizes speed and agility as essential factors for the success of the API program. The fact that automation is much easier in the code-first approach helps strengthen this case, with many libraries supporting scaffolding server code, functional testing, and deployment automation.

##### When Developing Internal APIs
The Code First approach affords speed, automation, and reduced process complexity, at the cost of good developer experience. If the API will only be consumed by the team or company building it, then the Code First approach is an ideal solution. This is especially true if the API developed is small, with only a few endpoints being used internally.

## Introduction to YAML

### Introduction
YAML is a standard format for storing data. It originally stood for Yet Another Markup Language but now stands for YAML Ain’t Markup Language. Because of its emphasis on human readability, YAML is increasingly relied upon for configuration files. It can also be used for log files, debugging complex data structures, interprocess messaging, and cross-language data sharing.

YAML is often compared to JSON due to their similarities. Both formats are human-readable and can represent complex data structures. However, there are some key differences. YAML is generally considered more human-readable due to its use of whitespace for separating objects rather than curly braces or brackets. It also offers additional features such as comments and object references. JSON, however, is superior when it comes to performance, specifically the speed at which a computer can parse it.

### YAML Structure

```yaml
---
# Our first YAML document
bottle: wine
capitals:
  Japan: Tokyo
  Argentina: Buenos Aires
oceans:
  - Indian
  - Atlantic
  - Arctic
  - Pacific
…
```

- A YAML document begins with three dashes (`---`) and ends with three dots (`…`). These characters can separate multiple YAML documents within a single file. In a YAML file with a singular document (e.g., the above example), most parsers treat these characters as optional.
- The second line begins with `#`, which makes it a comment. Comments are ignored by parsers but are helpful since YAML files are often shared by different developers and can provide insight into the document’s purpose.
- The bulk of this YAML document consists of mappings or key-value pairs, which are separated by a colon and a space (`:` ). Every key must be a string and must be unique. Values can be nested mappings, as is the case with the value of `capitals`. They can also be sequences, as with the value of `oceans`, or scalars, as with the value of `bottle`.
- The use of whitespace is a crucial aspect of YAML. Notice how a line break separates each mapping. When objects are nested, indentation indicates which objects are a part of the same value. Indentation must consist of one or more spaces. Tabs, however, are forbidden in YAML.
- While not explicitly shown, note that YAML files should end with the extension `.yaml` or `.yml`.

### Sequences
YAML sequences look a bit like lists or arrays in programming languages. They can contain any mix of data types, including nested sequences or mappings. Sequences are usually displayed on multiple lines, where each element begins with a dash, followed by a space, and ends with a line break.

```yaml
fish:
  - Tuna
  - Trout
  - Salmon
numbers:
  - pi
  - 7
  - 1.1
```

Sequences can also be written on a single line surrounded by brackets. In this case, elements are separated by a comma and a space, like this:

```yaml
planets: [Mercury, Venus, Mars]
```

### Scalars
All remaining data types in YAML are scalars, also known as single value data types. These include integers, floating-point numbers, booleans, null, and strings.

```yaml
scalars:
  - 1
  - 1.0
  - True
  - null
  - "string"
```

- **Numbers:** In YAML, numbers are classified by a single rule. Any number that doesn’t have a decimal point is an integer, while numbers that do are floats.
- **Booleans:** For booleans, the keywords `True`, `On`, and `Yes` evaluate to true. The keywords `False`, `Off`, and `No` will to false.

```yaml
elephant:
  - big: True
  - mammal: Yes
  - yellow: Off
```

- **Null:** A null value can be represented by either `~` or `null` (could also be written as `Null` or `NULL`), like this:

```yaml
nulls:
  - null
  - ~
```

- **Strings:** In YAML, strings generally do not need quotes. Two notable exceptions are as follows:
- Use single or double quotes to create a value that would normally be interpreted as a different data type to be a string, i.e., “10” or `"null"`
- Use double quotes to allow specific sequences to be escaped instead of treated as literals, such as `"\n"` representing a line break

```yaml
strings:
  - This string ends with a slash followed by n \n
  - "This string ends with a line break \n"
  - 'True'
```

## Introduction to the OpenAPI Specification

### Designing an API using OAS 3.0
The _OpenAPI Specification_ (_OAS_) is one of the most popular standards for designing human-readable API contracts. The OAS specifies the rules and syntax required to describe an API’s interface. The OAS has evolved to meet the needs of modern API teams and continues to introduce updates to make the specification simpler to use and easier for humans and computers to understand.

Here is the general structure of an OAS defined API contract using OAS 3.0:

![[Pasted image 20240314161250.png]]

### Info & OpenAPI
The `info` and `openapi` section of the API contract contains essential metadata. There are both required and optional fields such as contact information, license information, terms of service links, and more! Essentially, the info object should give an API’s end-users and internal developers a high-level overview of what the API does.

```yaml
openapi: 3.0.0
info:
  title: Simple Pet Store
  version: 1.0.0
  description: This is a sample server for a pet store.
  termsOfService: http://example.com/terms/
  contact:
    name: API Blogger
    email: support@example.com
    url: http://example.com/support
  license:
    name: Apache 2.0
    url: http://www.apache.org/licenses/LICENSE-2.0.html
```

### Servers
An API is a contract between the end-user and a server (usually the server hosting the API). The `servers` object can give a client information on where the API’s servers are located through its URL. Unlike the 2.0 version of the spec, which only allowed an API definition to have one server URL, OAS 3.0 supports multiple servers. This is useful since, in the real world, APIs exist in numerous environments, and each environment can have its own purpose.

```yaml
servers:
- url: https://development.gigantic-server.com/v1
  description: Development server
- url: https://staging.gigantic-server.com/v1
  description: Staging server
- url: https://api.gigantic-server.com/v1
  description: Production server
```

### Paths
An OAS contract’s `paths` object shows the various endpoints an API exposes and the corresponding HTTP methods. It’s also under each method that the actual request-response cycle is detailed. The requests are described by `parameter` objects and the responses by the `responses` objects. This section gives all parties a clear sense of the data the API will expose and helps with planning, documenting, and implementing the API.

```yaml
paths:
  /pet/{petId}:
    get:
      summary: Find pet by ID
      description: Returns a single pet
      parameters:
      - name: petId
        in: path
        description: ID of pet to return
        required: true
        schema:
          type: integer
          format: int64
      responses:
        200:
          description: successful operation
        400:
          description: Invalid ID supplied
          content: {}
        404:
          description: Pet not found
          content: {}
```

Notice two critical parts of the defined path:

- **Parameters:** Parameters are the variable parts of a request. There are four types of parameters that can be specified using the OAS 3.0:
    - path parameters, such as `/users/{id}`
    - query parameters, such as `/users?role=admin`
    - header parameters, such as `X-MyHeader: Value`
    - cookie parameters, which are passed in the Cookie header, such as `Cookie: debug=0; csrftoken=BUSe35dohU3O1MZvDCU`
- **Responses:** Responses are the objects returned on a request. Every response is defined by its HTTP status code, and the data is returned. The HTTP status codes are used to define whether the request was successful or unsuccessful.

For more information, take a look at the [paths object](https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.1.0.md#paths-object) in the official documentation.

### External Docs
Any additional information that an API can offer to ease consumption and integration with the API is always a good idea. OAS 3.0 allows an API to reference external documentation via the external documentation object.

```yaml
description: Find more info here
url: https://example.com
```

### Tags
Tags are friendly categories to group various API operations. This allows end-users of the API to better segment and identify what they want to use the API for. These tags can also be handled by other third-party tools which integrate or read the OAS.

Tags can automatically be added to every path operation using the tags object. Tags can also be given descriptions by adding an optional tags section in the root level of the API definition.

```yaml
paths:
  /pet/findByStatus:
    get:
      summary: Finds pets by Status
      tags:
        - pets
  /pet:
     post:
       summary: Adds a new pet to the store
       tags:
         - pets
tags:
- name: pets
  description: Everything about your Pets
```

### Components
As an API needs to expose more resources and operations, the contract can tend to get really long. The API may repeat a lot of existing parameters or response descriptions in many different paths and operations, and rewriting them every time makes them prone to inconsistent descriptions and can be very time-consuming.

The component object can hold a set of reusable objects for an APIs design. The reusable objects can be schemas, responses, parameters, examples, and more. The exact reusable component can then be referenced in any path item.

```yaml
paths:
  /pets/{petId}:
    get:
      summary: Get a pet by ID
      parameters:
        ...
      responses:
        '200':
          description: A single pet.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Pet'
  /pets:
    get:
      summary: Get all pets
      responses:
        '200':
          description: A list of pets.
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/Pet'
components:
  schemas:
    Pet:
      type: object
      properties:
        id:
          type: integer
        name:
          type: string
```


# Design and Document APIs with OpenAPI & Swagger

## Introduction to Swagger Tooling

### Introduction
[Swagger](https://swagger.io/tools/) is the name for a set of tools that help with each step of designing, developing, testing, and visualizing an API.

**_A note on Swagger_**:

The year 2017 marked the official release of OpenAPI 3.0, the latest version of the OpenAPI specification. OpenAPI 3.0 was the first official release of the specification since it was donated to the OpenAPI Initiative by SmartBear Software and renamed from the Swagger Specification to OpenAPI specification in 2015. This means there may be resources on the web that still refer to Swagger as a specification rather than a set of tools. The easiest way to understand the difference is:

- OpenAPI = Specification
- Swagger = Tools for implementing the specification

### Swagger Editor
As we noted earlier, our first step in designing our shiny new API would be to create an API contract. This is where the Swagger Editor tool comes into play. This tool is primarily used to design, define and document RESTful APIs. This editor accepts different OpenAPI versions, includes the option to convert a written specification to YAML (or JSON), and highlights any errors that might be occurring in the specification. The other two tools (Swagger Codegen and Swagger UI) can also be used directly from the Swagger Editor, but we will touch more on that later in this article.

The Swagger Editor can be accessed two ways:

- Via a web browser by visiting [Swagger’s online editor](https://editor.swagger.io/).
- Via a local machine by downloading the editor from [Swagger’s GitHub repository](https://github.com/swagger-api/swagger-editor).

### Swagger Codegen
Once our API specification has been designed, now it’s time for the grueling task of writing out the code for the backend logic and frontend interactions, right? Wrong! Using Swagger Codegen and a provided API specification, we can generate server and client-side code in many different languages. The generated code will even include documentation from the provided specification. Besides saving time by easily generating code, the Swagger Codegen tool provides more consistent code than writing it manually from scratch.

Since code generation typically occurs after the design process, the Swagger Editor tool allows you to generate the code directly through its options.

Swagger Codegen can also be downloaded via its [GitHub repository](https://github.com/swagger-api/swagger-codegen) and used locally through a Command Line Interface (CLI).

### Swagger UI
Lastly, once we have a specification in place, and have created (or generated) our server and client-side code, we will need to document the API. The Swagger UI tool allows anyone — be it a development team or end-users — to visualize and interact with an API’s resources without having any of the implementation logic in place. This means we don’t even have to have any code written for an end-user to see the APIs resources, end-points, and even execute mock API calls.

![[Pasted image 20240314163819.png]]

Swagger UI can primarily be accessed two ways:

- Via the online [Swagger Editor](https://editor.swagger.io/) tool. The right-hand side of the editor tool neatly displays any valid specification using Swagger UI. This means Swagger Editor already has Swagger UI built into it and generates the specification documentation live as it is created.
- Via a local machine by downloading from the [Swagger UI GitHub repo](https://github.com/swagger-api/swagger-ui).

## Designing and Documenting an API with Swagger

```yaml
openapi: 3.0.1
```

Insert -> Add info

Insert -> Add path item

Insert -> Add operation

Insert -> Add Example Response

```yaml
openapi: 3.0.1
info:
  title: Online Order API
  version: 1.0.0
  description: A basic API for working with the Swagger tools.
paths:
  /orders:
    summary: Get all of the order data.
    description: This path is used to retrieve order data form the orders.json file.
    get:
      summary: Gets the order data
      description: Retrieve the order information from the orders.json file.
      operationId: get_orders
      responses:
        '200':
          content:
            application/json:
              examples:
                orders:
                  value: >-
                    {"orders":[{"name":"Carey
                    Maynard","id":"001","state":"pending"},{"name":"Angelo
                    Ayala","id":"002","state":"canceled"},{"name":"Regina
                    Yates","id":"003","state":"pending"},{"name":"Elliott
                    Mcclure","id":"004","state":"pending"}]}
          description: Success
      tags:
        - Orders
  /neworder:
    summary: Add new orders
    description: This path is used to add new orders to the orders.json file.
    post:
      summary: Add a new order
      description: >-
        This operation adds a new order to the list of orders found in the
        orders.json file.
      operationId: new_order
      requestBody:
        description: A new order object
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/Order'
        required: true
      responses:
        '400':
          content:
            text/plain; charset=utf-8:
              examples:
                Error:
                  value: Invalid Argument
          description: Invalid Argument Provided
        '200':
          content:
            text/plain; charset=utf-8:
              examples:
                Message:
                  value: Success
          description: Success
      tags:
        - New Order
  /update/{id}:
    summary: Update the state of an order.
    description: >-
      This path is used to update the state of an order with a matching id in
      the orders.json file.
    put:
      summary: Update the state of an order
      description: >-
        This operation updates the `state` of an order with a matching id from
        the orders.json file.
      operationId: update_order
      parameters:
        - name: id
          in: path
          description: The id of the order.
          required: true
          schema:
            type: string
      requestBody:
        description: A state string
        content:
          text/plain:
            schema:
              type: string
      responses:
        '400':
          content:
            text/plain; charset=utf-8:
              examples:
                Error:
                  value: Invalid Argument
          description: Invalid Argument Provided
        '200':
          content:
            text/plain; charset=utf-8:
              examples:
                Message:
                  value: Success
          description: Success
      tags:
        - Update Order
  /delete/{id}:
    summary: Delete an order
    description: >-
      This path is used to delete an order with a matching id from the
      orders.json file.
    delete:
      summary: Deletes an order
      description: >-
        This operation deletes an order with a matching id from the orders.json
        file
      operationId: delete_order
      parameters:
        - name: id
          in: path
          description: The id of the order.
          required: true
          schema:
            type: string
      responses:
        '400':
          content:
            text/plain; charset=utf-8:
              examples:
                Error:
                  value: Invalid Argument
          description: Invalid Argument Provided
        '200':
          content:
            text/plain; charset=utf-8:
              examples:
                Message:
                  value: Success
          description: Success
        
      tags:
        - Delete Order
components:
  schemas:
    Order:
      type: object
      properties:
        name:
          type: string
        id:
          type: string
        state:
          type: string
      xml:
        name: Order
```

Generate Server -> nodejs-server