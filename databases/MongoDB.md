#mongodb
# Database Basics

## Introduction to databases

### What is a Database?
In software engineering, [**databases**](https://www.codecademy.com/resources/docs/general/database) are systems that store, modify, and access collections of information electronically.

### Why Databases?
Almost any type of software application needs a way of storing data. Without them, developers would have no way to meaningfully persist information that is important for the application’s functionality.

When we are looking to interact with a database, we are actually looking to interact with a **database management system**.

### Database Management Systems (DBMS)
Suppose a database is a bucket that stores our data. In that case, a DBMS is the software that encapsulates said bucket (our database(s)) and lets us work with the database using a programming language or easy-to-use graphical interface (GUI).

Since each DBMS is unique, they vary in their implementation and, as such, provide different advantages and disadvantages.

### Relational Databases
One of the most common classes of databases is a **relational database**. [Relational databases](https://www.codecademy.com/resources/docs/general/relational-database), commonly referred to as SQL databases, structure data in **tabular form**. This means data is grouped into tables, using rows and columns to organize and store individual records of data.

Relational databases are unique because they are based on presenting data in terms of relationships. To accomplish this, relational databases enable associations between tables to be defined, the most common associations being “one-to-one”, “one-to-many”, and “many-to-many”.

Lastly, note the following important properties of relational databases:

- **Pre-defined Schema**: Relational databases are unique because the **database schema** - the “blueprint” of the database structure - is typically determined before any data is ever inserted. This would mean we would likely decide the specific tables, and their associated relationships, before even inserting any data into them.
- **SQL Use**: Developers communicate with a relational database using **SQL** (Structured Query Language). [SQL](https://www.codecademy.com/resources/docs/sql/about-sql) is an industry-standard database language that has been used for decades. The dependence of relational databases on SQL is why some developers and documentation sometimes refer to relational databases as SQL databases.
- **Relational Database Management System**: Any relational database is managed by a relational database management system (RDBMS). This type of DBMS allows the data to follow a relational model (e.g., setup relationships) and manage the data using SQL. Two of the most popular RDBMSs are [PostgreSQL](https://www.postgresql.org/) and [MySQL](https://www.mysql.com/).
- **Unique Disadvantages**: At the enterprise level, where data sets are massive, setting up a relational database can be costly, and the expenses required to maintain and scale it can compound significantly over time. Furthermore, rows and columns consume a great deal of physical space which can lead to implications for performance and cost.

### Non-Relational Databases
The second most common class of databases is **non-relational databases**. A non-relational database, commonly referred to as a NoSQL database, is any database that does not follow the relational model. This means these types of databases typically don’t store data in tables, but more importantly, data isn’t strictly represented with relationships. Under the umbrella of non-relational databases are many different types of databases, each with its own framework for organizing data. Some examples are [document databases](https://en.wikipedia.org/wiki/Document-oriented_database), [graph databases](https://en.wikipedia.org/wiki/Graph_database), and [key-value databases](https://en.wikipedia.org/wiki/Key%E2%80%93value_database). Collectively, non-relational databases specialize in storing unstructured data that doesn’t fit neatly into rows and columns.

Additionally, note the following properties of non-relational databases:

- **Flexibility and Scalability**: Non-relational database’s unstructured nature facilitates the design of flexible schemas (schemas that do not need to be defined beforehand) and makes these types of databases highly adaptable to the changing needs of an application. Additionally, non-relational databases are well suited for expansion or scalability and are relatively inexpensive to maintain compared to relational databases.
- **Custom Query Language**: Unlike relational databases that all use SQL as a standard query language, most NoSQL databases have their own custom language.
- **Unique Disadvantages**: Since the data in non-relational databases is mainly unstructured, data can often become hard to maintain and keep track of. Additionally, since every NoSQL database uses its own custom query language, there is a new learning curve for each one we choose to work with.

### Wrap Up
- Databases
    - Databases are systems that store, modify, and access structured collections of information electronically.
    - Database Management Systems (DBMS) allow developers to communicate via code or a graphical user interface with a database.
    - Databases can store a wide range of data types, including text, numbers, dates and times, and files of various types.
- Relational Databases
    - Relational databases, a common database class, organize data into tables of rows and columns of information and rely on relationships to organize data.
    - A relational database schema is typically pre-defined before data is entered.
    - All relational databases use SQL to allow developers to communicate with the database using a common language.
    - Relational databases can be costly to set up and scale. Performance and cost are big factors in using a relational database in an application.
- Non-Relational Databases
    - Non-relational databases, another common database class, refer to any database that does not follow the relational model.
    - Non-relational databases typically have a more flexible schema and are more easily scaled than relational databases. However, the unstructured nature of the data can make it difficult to maintain, and each non-relational database has its own query language.


# Introduction to MongoDB

## Introduction to MongoDB

### What is MongoDB?
First released in 2009 and updated regularly with new releases, MongoDB is a database system that allows users to store data using the **document model**. The document model is a term used to describe a database that primarily stores data in documents and collections. The data stored inside documents is typically stored in hierarchical structures like JSON, BSON, and YAML.

Documents are stored inside of a collection.

### Advantages of Using MongoDB

#### Flexibility and Scalability
One of the main advantages of using MongoDB, and most other document databases, is the flexible way data can be stored. For example, with a relational database, changing the column of a single table, impacts every entry inside of it. This can mean one change to a single table can impact thousands if not millions of entries. With document databases, we avoid this entirely. Changes to a single document have no effect on any other document in the collection.

Additionally, as our applications grow, the database we store information with must be able to grow as well. In technical terms, we call this scalability. MongoDB offers multiple easy-to-use options for users to scale their database to accommodate growth.

#### Developer-Friendly
MongoDB has a number of different traits, which make it incredibly developer-friendly.

- MongoDB databases support a variety of different use-cases. To name a few, MongoDB can be used to build web, mobile, and desktop applications. MongoDB also has features that support [data analytics](https://www.mongodb.com/atlas/data-lake?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) and [data visualization](https://www.mongodb.com/products/charts?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral).
- Given MongoDB’s popularity, a large community has formed around the technology. This means there are a plethora of resources (e.g., forums, articles, conferences) available for developers at any level.
- MongoDB has a significant amount of detailed documentation and educational tools (like [MongoDB University](https://university.mongodb.com/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral)) to help developers learn about all of MongoDB’s unique features.

#### Diverse Cloud Tooling
A third major advantage of using MongoDB is the wide array of cloud tools. These cloud tools help provide solutions for a variety of different use cases. Let’s look at two popular cloud tools: Atlas and Realm.

[MongoDB Atlas](https://www.mongodb.com/atlas?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) is MongoDB’s multi-cloud database service. Atlas allows developers to create, manage, and deploy MongoDB databases with just a few clicks. All of the databases are stored in the cloud, and Atlas does not require developers to have MongoDB set up on their computers to use it. Developers can interface with a database using an online dashboard.

Additionally, MongoDB offers a product called [MongoDB Realm](https://www.mongodb.com/docs/realm/introduction/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral). Realm is another cloud offering that helps developers rapidly build various applications that are fully integrated with MongoDB. Potential uses for Realm range from mobile, to internet-of-things, to standard desktop applications. For example, if we were building a mobile app, we could use Realm to create a database on each of the phones that the app is installed on and seamlessly synchronize data between devices and the database. Realm can also facilitate complex tasks like authentication (e.g., login functionality) for us!

### Wrap up
- MongoDB is a NoSQL document database. This means that data entries in the database are stored inside documents within collections.
- Choosing to use MongoDB has some key benefits:
    - Flexibility and Scalability
    - Developer Friendly
    - Diverse Cloud Tooling


## MongoDB Data

### Collections and Documents
To help better visualize the document model, let’s imagine we are using MongoDB to run our camera store.

At the highest level, we have our database – an instance of MongoDB that contains all the various data our store needs to operate.

Within this instance of MongoDB are collections. Collections are subsets of our data. So, assuming our database contains three types of data – purchase data, inventory, and customer info – each of these would have its own collection.

Within each collection, we store individual records called documents. These documents all belong to that particular subset of our data. So, for example, within the customer collection, we could store personal information about each of our customers. Every customer would have their own document within the collection.

To summarize, a document is simply a record that stores information about a particular entity. A collection, in turn, is just a group of documents containing similar information. And finally, a MongoDB database is just a number of collections assembled together to store data for a specific use case.

### Data as JSON
One of the main advantages of using a document database is the flexibility it provides with respect to how data is stored. In the case of MongoDB, this flexibility comes partly from a data format called Javascript Object Notation, or JSON (jay-sahn). [JSON](https://www.mongodb.com/json-and-bson?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) is simply a text format for storing data. Here is what JSON looks like:

```json
{ 
  "name": "Rodney", 
  "occupation": "photographer",
  "years_of_experience": 7
}
```

Note that JSON stores data as what is known as “key-value” pairs, which are always within a pair of curly braces (“`{ }`“). MongoDB and various online resources also refer to these pairs as “field-value” or “name-value” pairs. Here is a breakdown of what fields and values mean in the context of JSON:

- Fields: A field is a unique identifier for a data point; it tells us what kind of data is being stored. In the job application JSON we just examined, the fields are `"name"`, `"occupation"`, and `"years_of_experience"`. Note that JSON field names must be double-quoted (“ “).
- Values: Every field has an associated value. The values are the data points themselves. In our camera store applicant example, the values are `"Rodney"`, `"photographer"`, and `7`, each of which corresponds to their respective field. Note that JSON can host a variety of data types in value fields such as strings, numbers, arrays, or even nested data. Additionally, each of these field-value pairs must be separated by a comma (“ , “).

The primary advantage of JSON is readability and flexibility. Data is stored in an easily editable format that is totally comprehensible to humans as well as our computers. However, convenience ultimately comes at a price.

There are three main drawbacks to storing data as JSON:

1. JSON is inefficient from a computational perspective as text is time-consuming to parse.
2. Its readability as text also means that it is not efficient storage-wise. For example, it might be helpful for us to have descriptive names of fields, but they tend to be longer and, for that reason, take up more space.
3. JSON only supports a very limited number of data types – dates, for instance, are not supported natively.

While there are some clear advantages to using JSON to format data, these drawbacks make JSON a poor choice as a primary storage format inside databases. That is why MongoDB invented BSON.

### BSON - MongoDB’s Storage Format
Binary Javascript Object Notation, or BSON (bee-sahn), is the format that MongoDB uses to store data. BSON is different than JSON in three fundamental ways:

1. BSON is not human-readable.
2. BSON is far more efficient storage-wise.
3. BSON supports a number of data formats that JSON does not - like dates.

Our same JSON object from earlier looks like this in BSON:

```BSON
\x00\x00\x00\x02name\x00\a\x00\x00\x00Rodney\x00\x02occupation\x00\r\x00\x00\x00photographer\x00\x10year_of_experience\x00\a\x00\x00\x00\x00
```

While it may not be legible, MongoDB wrote the [BSON specification](https://bsonspec.org/) and invented the format to bridge the gap between JSON’s flexibility and readability and the required performance of a large database. MongoDB stores data as BSON internally but allows users to create and manipulate database data as JSON. This allows for both efficient data storage and a great developer experience!

### Wrap up
- A MongoDB instance can contain many databases, and within a database are collections of similar data. Collections contain individual records called documents that are stored as field-value pairs.
- JSON is a human-readable but inefficient format for storing data; conversely, BSON is not human-readable but is highly efficient.
- MongoDB users can easily store and manipulate data as JSON – even though internally, that data is stored as BSON.

To continue learning and get a more in-depth overview of MongoDB data, check out the following two guides on JSON/BSON from MongoDB:

- [JSON and BSON Guide](https://www.mongodb.com/json-and-bson?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral)
- [Explaining BSON with Examples](https://www.mongodb.com/basics/bson?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral)


## MongoDB Data Modeling Basics

### Introduction
The absence of a schema-based structure means we will have to think even more deeply about how we will structure our data. This concept is called _data modeling_.

Data modeling as a practice is the process of developing and choosing a way to structure our data and its relationships. The way we choose to organize our data has long-lasting implications on a database’s scalability, maintainability, and performance.

### The Importance of Data Modeling
A data model is like a blueprint for our data. A good data model can provide structure and organization to what might be a diverse and complex set of information. A bad model can make even simple data challenging to work with.

### Modeling Relationships in MongoDB
In addition to deciding the overall structure of our collections, another consideration is how to represent relationships between data.

To establish these types of relationships in MongoDB, we have two options: embedded documents or references.

#### Embedded documents
One way to establish a relationship in MongoDB is to use embedded documents. This method allows us to nest data related to a document directly inside of it! These nested documents are called _sub-documents_.

```
// Car Document
{
  car_id: 48273
  model_name: "Corvette",
  engine: {
    engine_power: 490,
    engine_type: "V8",
    acceleration: "High"
  }
}
```

This type of data model where we find related data lumped together into a single collection is known as a _denormalized_ data model.

Additionally, the following scenarios are good use-cases for embedded documents:

- Modeling relationships where one entity _contains_ another, also known as a _one-to-one_ relationship. For example, we can think of a database storing data with a relationship between a car and its unique license plate. Each record of a car has only one license plate.
- Modeling relationships that map one entity to many sub-entities, also known as an _one-to-many_ relationship. For example, we can think of a database storing data with a relationship between a car owner and their multiple-owned cars. Each record of a car owner can own multiple instances of a car.

#### References
In addition to embedded documents, we can define relationships by creating links between data. These links are called references. Using references, we can split our data into multiple documents and maintain their relationships.

```
//Car Document
{
  car_id: 48273
  model_name: "Corvette",
  engine_id: 2165
}
 
// Engine Document
{
  id: 2165
  engine_power: 490,
  engine_type: "V8",
  acceleration: "High"
}
```

This type of data model where we find related data via a link is known as a _normalized_ data model and typically mimics how a relational database creates relationships between data.

Additionally, the following scenario is a good use case for references:

- Modeling relationships where many instances of one entity can be mapped to many instances of another entity, also known as _many-to-many_ relationships. For example, we can think of the relationship between car rentals and individuals renting the cars. A car can be rented by multiple individuals, and an individual can rent multiple cars.

### Choosing The Right Model
**Case A: A time management application that stores one user per task. We want to store details about the task, such as the task name, the task due date, and the user assigned to the task (and their associated details). There can only be one person assigned to each task.**

In this case, since we can only have one person assigned to each task, we are modeling a one-to-one relationship. Assuming we will often need the data for the user in addition to the task details, it _might_ be preferable to use an embedded document since the information can be retrieved together in one query.

```
{
  task: "Review Rough Outline",
  due: "2022/09/03 09:00",
  assignee: {
    name: "Alex",
    role: "SME",
    contact: "alex@example.com"
  }
}
```

**Case B: A contact information management application that can store multiple addresses per user. The application would store important details for the person such as their name, as well as their associated addresses.**

In this case, since a single user can have multiple associated addresses, we are modeling a one-to-many relationship. There are two distinct ways we can implement the data model.

First, we could use embedded documents. Our documents might look something like this:

```
{
  first_name: "Alex",
  last_name: "Smith",
  addresses: [
    { label: "home", value: { address: "123 4th Street", city: "Toronto", region: "ON", country: "Canada", postcode: "M1S 2J8" } },
    { label: "work", value: { address: "1633 Broadway 38th floor", city: "New York", region: "NY", country: "USA", postcode: "10019" } },
    "
  ]
}
```

The embedded documents model above would be preferable if we are making many queries on the `addresses` field since we would only need to query a single document to receive our results. However, if we later down the line had many instances of users sharing an address, we might end up with the following collection:

```
{
  first_name: "Alex",
  last_name: "Smith",
  addresses: [
    { label: "home", value: { address: "123 4th Street", city: "Toronto", region: "ON", country: "Canada", postcode: "M1S 2J8" } },
    { label: "work", value: { address: "1633 Broadway 38th floor", city: "New York", region: "NY", country: "USA", postcode: "10019" } }
  ]
},
{
  first_name: "Josh",
  last_name: "Gold",
  addresses: [
    { label: "home", value: { address: "123 4th Street", city: "Toronto", region: "ON", country: "Canada", postcode: "M1S 2J8" } }
    "
  ]
},
{
  first_name: "Timbo",
  last_name: "Gray",
  addresses: [
    { label: "home", value: { address: "123 4th Street", city: "Toronto", region: "ON", country: "Canada", postcode: "M1S 2J8" } }
  ]
}
```

In this situation, where we notice that embedded documents are starting to repeat, we may consider using references instead. By using references, our collection could look like this instead:

```
// Addresses Collection
{
  _id: 123456789
  address: {     
    street: "123 4th Street", 
    city: "Toronto", 
    region: "ON", 
    country: "Canada", 
    postcode: "M1S 2J8" 
  }
},
{ 
  _id: 9292944,
  address: { 
    street: "1633 Broadway 38th floor",
    city: "New York", 
    region: "NY", 
    country: "USA", 
    postcode: "10019" 
  } 
}
```

```
// User Collection 
{
  first_name: "Alex",
  last_name: "Smith"
  addresses: [ 123456789, 9292944 ] 
},
{
  first_name: "Josh",
  last_name: "Gold",
  addresses: [ 123456789 ] 
},
{
  first_name: "Timbo",
  last_name: "Gray",
  addresses: [ 123456789 ]
}
```

While the above example shows one case where we _might_ use references, its important to note that we need to consider how frequently we are accessing the address information and how large it is before making a data modeling decision.

**Case C: A school registration application that manages multiple students. Each student can be in multiple classes. Each class record can easily identify which students are registered and each student record can quickly find any associated classes.**

In this application, we have many students sharing a relationship with many classes. Here, we need to model a many-to-many relationship. In this case, references _might_ be preferred. Our collections would look similar to this:

```
// Students Collection
 
 
{     
  _id: 1, 
  name: "Alex",
  average_grade: 3.9, 
  course_ids: [ 1, 2, 4 ] 
},
{
  _id: 2, 
  name: "Bob", 
  average_grade: 2.4, 
  course_ids: [ 3, 4 ] 
}
```

```
// Classes Collection
{ 
  _id: 1, 
  name: "Intro to MongoDB", 
  student_ids: [ 1 ] 
},
{     
  _id: 2, 
  name: "Programming 101", 
  student_ids: [ 1 ]
 },
{     
  _id: 3, 
  name: "Networking Concepts", 
  student_ids: [ 2 ]
 },
{     
  _id: 4, 
  name: "Understanding Distributed Systems", 
  student_ids: [ 1, 2 ] 
}
```

### Wrap up
- Data modeling is the practice of developing an organizational structure for the data in our database.
- Choosing a data model can have lasting implications on the database and its long-term performance, maintainability, and usability.
- Embedded documents and references are two of the most common ways to model data. These two methods help define the relationships between the data in collections.
- Reference-based data models are normalized; they use links inside of the data (typically via the `_id` field) to create relationships.
- Embedded data models are denormalized; they use nested documents inside of collections to create relationships.


# MongoDB CRUD I

## Finding Documents

### Browsing and Selecting Collections
MongoDB can easily be run in a terminal using the [MongoDB Shell](https://www.mongodb.com/docs/mongodb-shell/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) (`mongosh` for short). MongoDB allows us to store multiple databases inside of a single running instance.

To see all of our databases, we can run the command `show dbs`. This will output a list of all the databases in our current instance and the disk space each takes up.

Looking at the example output above, notice three unique databases: `admin`, [`config`](https://www.mongodb.com/docs/manual/reference/config-database/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral), and [`local`](https://www.mongodb.com/docs/manual/reference/local-database/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral). These databases are included by MongoDB to help configure our instance.

To navigate to a particular database, we can run the `use <db>` command. For example, if we wanted to use our e-commerce database, we’d run `use online_plant_shop`. This would place us inside our `online_plant_shop` database, where we have the option to view and manage all of its collections. It’s important to note, that if the database we specify does not exist, MongoDB will create it, and place us inside of that database.

Notice that the terminal will list the current database we are in before a `>` symbol. When we switch databases, we should see the name of the database we switched into displayed there instead.

If at any point we lose track of what database we are in, we can orient ourselves by running the command, `db`. This will output the name of the database we are currently using.

### Introduction to Querying
In the world of databases, [persistence](https://en.wikipedia.org/wiki/Persistent_data) describes a database’s ability to store data that is stable and enduring. There are four essential functions that a persistent database must be able to perform: _create_ new data entries, and _read_, _update_ and _delete_ existing entries. We can summarize these four operations with the acronym CRUD.

Querying is the process by which we request data from the database. The most common way to query data in MongoDB is to use the [`.find()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.find/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) method.

```sh
db.<collection>.find()
```

Notice the `.find()` method must be called on a specific collection. When we call `.find()` without arguments, it will match all of the documents in the specified collection. If our query is successful, MongoDB will return a [**cursor**](https://www.mongodb.com/docs/v5.3/tutorial/iterate-a-cursor/), an object that points to the documents matched by our query. Because our queries could potentially match large numbers of documents, MongoDB uses cursors to return our results in batches.

In other words, when we query collections using the `.find()` method, MongoDB will return up to the first set of matching documents. If we want to see the next batch of documents, we use the `it` keyword (short for iterate).

---

To see a list of all collections in a database, you can type the command `show collections`.

### Querying Collections
If we are looking for a specific document or set of documents, we can pass a query to the `.find()` method as its first argument (inside of the parenthesis `( )`). With the `query` argument, we can list selection criteria, and only return documents in the collection that match those specifications.

The query argument is formatted as a document with field-value pairs that we want to match.

```
db.<collection>.find(
  {
    <field>: <value>,
    <second_field>: <value>
    ...
  }
);
```

We can have as many field-value pairs as we want in our query! To see the query in action, consider the following collection (shortened for brevity) of automobile makers in a collection named `auto_makers`:

```
{
  maker: "Honda",
  country: "Japan",
  models: [
    { name: "Accord" },
    { name: "Civic" },
    { name: "Pilot },
    …
  ]
},
 
{
  maker: "Toyota",
  country: "Japan",
  models: [
    { name: "4Runner" },
    { name: "Corolla" },
    { name: "Rav4" },
    …
  ]
},
{
  maker: "Ford",
  country: "USA",
  models: [
    { name: "F-150" },
    { name: "Bronco"},
    { name: "Escape"},
    …
  ]
}
```

Imagine we wanted to query this collection to find all of the vehicles that are manufactured in `"Japan"`.

```sh
db.auto_makers.find({ country: "Japan" });
```
 
Note: Query fields and their associated values are case and space sensitive. So, a query for a value `"Corolla"` would not be valid for a lowercase version like `"corolla"`. This also applies if we accidentally included spaces. So, `" corolla"` would also not be valid if the value was `"corolla"`.

Under the hood, `find()` is actually using an **operator** to find matches to our query. Operators are special syntax that specifies some logical action we want to perform when our method executes. In the case of the `.find()` method, it uses the implicit equality operator, [`$eq`](https://www.mongodb.com/docs/manual/reference/operator/query/eq/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral), to match documents that include the specified field and value.

If we wanted to explicitly include the equality operator in our query document, we could do so with the following field-value pair:

```
{
  <field>: { $eq: <value> }
}
```

Fortunately, MongoDB handles implicit equality for us, so we can simply use the shorthand syntax for basic queries.

### Querying Embedded Documents
When we are working with MongoDB databases, sometimes we’ll want to draw connections between multiple documents. MongoDB lets us embed documents directly within a parent document. These nested documents are known as **sub-documents**, and help us establish relationships between our data. For example, take a look at a single record from our `auto_makers` collection:

```
{
  maker: "Honda",
  country: "Japan",
  models: [
    { name: "Accord" },
    { name: "Civic" },
    { name: "Pilot" },
    …
  ]
},
…
```

Notice how inside of this document, we have a field named `models` that nests data about a maker’s specific model names. Here, we are establishing that the car maker `"Honda"` has multiple models that are associated with it. Once again, we can use the `.find()` method to query these types of documents, by using [dot notation](https://www.mongodb.com/docs/manual/core/document/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral#dot-notation) (`.`), to access the embedded field.

Let’s take a look at the syntax for querying on fields in embedded documents:

```
db.<collection>.find(
  { 
    "<parent_field>.<embedded_field>": <value> 
  }
)
```

Note two important parts of the syntax:

1. To query embedded documents, we must use a parent field (the name of the field wrapping the embedded document), followed by the dot (`.`) notation, and the embedded field we are looking for.
2. To query embedded documents, we must wrap the parent and embedded fields in quotation marks.

If we wanted to find the document with `"Pilot"` listed as a model, we would write the following command:

```
db.auto_makers.find({ "models.name" : "Pilot" })
```

### Comparison Operators: $gt and $lt
The greater than operator, [`$gt`](https://www.mongodb.com/docs/manual/reference/operator/query/gt/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral), is used in queries to match documents where the value for a particular field is greater than a specified value.

```
db.<collection>.find( { <field>: { $gt: <value> } } )
```

To see the `$gt` operator in action, consider the following collection of US National Parks:

```
{
 name: "Yosemite National Park",
 state: "California",
 founded: 1890
},
{
 name: Crater Lake National Park,
 state: "Oregon",
 founded: 1902
},
{
 name: "Mesa Verde National Park",
 state: "Colorado",
 founded: 1906
},
{
 name: "Olympic National Park",
 state: "Washington",
 founded: 1909
},
…
```

To find all parks that were founded after the year 1900, we could execute the following query:

```mongosh
db.national_parks.find({ founded: { $gt: 1900 }});
```

Note: If we wanted to include the year `1900` in our query, we could use the [`$gte`](https://www.mongodb.com/docs/manual/reference/operator/query/gte/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral), which will match all values that are greater than _or equal to_ the specified value.

We can also match documents that are less than a given value, by using the less than operator, [`$lt`](https://www.mongodb.com/docs/manual/reference/operator/query/lt/). For example, if we reference our `national_parks` example above, we could select all parks that were founded before `1900` with the following query:

```mongosh
db.national_parks.find({ founded: { $lt: 1900 }});
```

Note: Similar to the `$gte` operator, we can use [`$lte`](https://www.mongodb.com/docs/manual/reference/operator/query/lte/) if we want to match all values that are less than _or equal to_ the specified value.

While the examples we examined in this exercise match numerical values, it’s worth noting that these comparison operators can be used with any data type (e.g., letters).

### Sorting Documents
When working with a MongoDB collection, there will likely be instances when we want to sort our query results by a particular field or set of fields. Conveniently, MongoDB allows us to sort our query results before they are returned to us.

To sort our documents, we must append the [`.sort()`](https://www.mongodb.com/docs/manual/reference/method/cursor.sort/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) method to our query. The `.sort()` method takes one argument, a document specifying the fields we want to sort by, where their respective value is the sort order.

Take a look at the syntax for sorting a query below:

```
db.<collection>.find().sort(
  {
    <field>: <value>,
    <second_field>: <value>,
    …
  }
)
```

There are two values we can provide for the fields: `1` or `-1`. Specifying a value of `1` sorts the field in ascending order, and `-1` sorts in descending order. For datetime and string values, a value of `1` would sort the fields, and their corresponding documents, in chronological and alphabetical order, respectively, while `-1` would sort those fields in the reverse order.

Let’s look at an example to see the `.sort()` method in action. Imagine we are developing an e-commerce site that sells vintage records, and our application needs to retrieve a list of inventoried records by their release year. We could run the following command to sort our records by the year they were released:

```mongosh
db.records.find().sort({ "release_year": 1 });
```

It’s important to note that when we sort on fields that have duplicate values, documents that have those values may be returned in any order. Notice in our example above, that we have two documents with the `release_year` `1984`. If we were to run this exact query multiple times, documents would get returned in numerical order by `release_year`, but the two documents that have `1984` as their `release_year` value, might be returned in a different order each time.

We can also specify additional fields to sort on to receive more consistent results. For example, we can execute the following query to sort first by `release_year` and then by `artist`.

```mongosh
db.records.find().sort({ "release_year": 1,  "artist": 1 });
```

### Query Projections
MongoDB allows us to store some pretty large, detailed documents in our collections. When we run queries on these collections, MongoDB returns whole documents to us by default. These documents may store deeply nested arrays or other embedded documents, and because of the flexible nature of MongoDB data, each might have a unique structure. All of this complexity can make these documents a challenge to parse, especially if we’re only looking to read the data of a few fields.

Fortunately, MongoDB allows us to use **projections** in our queries to specify the exact fields we want to return from our matching documents. To include a projection, we can pass a second argument to the `.find()` method, a `projection` document that specifies the fields we want to include, or exclude, in our returned documents. Fields can have a value of `1`, to include that field, or `0` to exclude it.

Let’s take a closer look at the syntax for [`projection`](https://www.mongodb.com/docs/manual/tutorial/project-fields-from-query-results/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) documents below:

```
db.<collection>.find(
  <query>, 
  { 
    <projection_field_1>: <0 or 1>, 
    <projection_field_2>: <0 or 1>,
    …
  }
)
```

Consider a document from the `listingsAndReviews` collection that we’ve been working with. Each document in the collection shares a similar structure to the one below:

```
{
  _id: ObjectId("5eb3d668b31de5d588f4292a"),
  address: {
    building: '2780',
    coord: [ -73.98241999999999, 40.579505 ],
    street: 'Stillwell Avenue',
    zipcode: '11224'
  },
  borough: 'Brooklyn',
  cuisine: 'American',
  grades: [
    { date: ISODate("2014-06-10T00:00:00.000Z"), grade: 'A', score: 5 },
    { date: ISODate("2013-06-05T00:00:00.000Z"), grade: 'A', score: 7 },
    {
      date: ISODate("2012-04-13T00:00:00.000Z"),
      grade: 'A',
      score: 12
    },
    {
      date: ISODate("2011-10-12T00:00:00.000Z"),
      grade: 'A',
      score: 12
    }
  ],
  name: 'Riviera Caterer',
  restaurant_id: '40356018'
}
```

If we were to query this collection and were just interested in viewing the `address` and `name` fields, we could run the following query that includes a projection:

```mongosh
db.listingsAndReviews.find( {}, {address: 1, name: 1} )
```

This would return the `address` and `name` fields for any documents that match our query.

```
{
  _id: ObjectId("5eb3d668b31de5d588f4292a"),
  address: {
    building: '2780',
    coord: [ -73.98241999999999, 40.579505 ],
    street: 'Stillwell Avenue',
    zipcode: '11224'
  },
  name: 'Riviera Caterer'
}
```

Notice how, by default, the `_id` field is included in our projection, even if we do not specify to include it.

But what if we’re not interested in seeing the `_id` field? We can omit it from our results by specifying the `_id` field in our `projection` document. Instead of setting its value to `1`, we’d set it to a value of `0` to exclude it from our return documents.

```mongosh
db.listingsAndReviews.find( {}, {address: 1, name: 1, _id: 0} )
```

In some scenarios, we may need our query to return all the fields, except a select few. Rather than listing the fields we want to return, we can use a projection to define which fields we want to exclude from our matching documents by assigning the fields a value of `0`. For example, if we wanted to query our collection and see all fields _but_ the `grades` field, we could run the following command:

```mongosh
db.restaurants.find( {}, {grades: 0} )
```

It is important to note that except for the `_id` field, it is not possible to combine inclusion and exclusion statements in a single projection document. For example, the following query with a projection would be invalid, and return a `MongoServerError`:

```mongosh
db.restaurants.find({}, {grades: 0, address: 1 })
```

### Review
- We can view a list of all our databases by running the `show dbs` command.
- We can navigate to a particular database, or see which database we are currently using with the `use <db>`, and `db` commands, respectively.
- We can use the `.find()` method to query a collection. Excluding a `query` argument matches all documents from the collection.
- We can match documents on particular field values by passing a `query` argument to the `.find()` method.
- When a collection’s record has an embedded document, we can query the fields inside of it using dot notation (`.`) and wrapping the fields in quotation marks.
- The `$gt` and `$lt` comparison operators allow our query to match documents where the value for a particular field is greater than or less than a given value, respectively.
- We can use the `.sort()` method to sort our query results by a particular field in ascending or descending order.
- We can include a projection in our query to include or exclude certain fields from our returned documents.

In addition to the methods and operators we’ve covered in this lesson, MongoDB provides us with even more syntax that can be useful to us when performing queries:

- The [`.count()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.count/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) method returns the number of documents that match a query.
- The [`.limit()`](https://www.mongodb.com/docs/manual/reference/method/cursor.limit/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) method can be chained to the `.find()` method, and specifies the maximum number of documents a query will output.
- The [`$exists`](https://www.mongodb.com/docs/manual/reference/operator/query/exists/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) operator can be included in a query filter to only match documents that contain the given field.
- The [`$ne`](https://www.mongodb.com/docs/v6.0/reference/operator/query/ne/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) operator helps check if a field is not equal to a specified value.
- The [`$and`](https://www.mongodb.com/docs/manual/reference/operator/query/and/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) and [`$or`](https://www.mongodb.com/docs/manual/reference/operator/query/or/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) operators help perform AND or OR logic operators.

Lastly, if you are looking for a way to make query outputs look a bit more “pretty”, you can use the [`.pretty()`](https://www.mongodb.com/docs/manual/reference/method/cursor.pretty/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) method!


## Querying on Array Fields

### Querying for An Entire Array
Consider a collection called `books` where each document shares a similar structure to the following:

```
{
  _id: ObjectId(...),
  title: "Alice in Wonderland",
  author: "Lewis Carroll",
  year_published: 1865,
  genres: ["childrens", "fantasy", "literary nonsense"]
}
```

Imagine we are looking for a new book to dive into – specifically, one that spans the young adult, fantasy, and adventure genres. We can query the collection for an array containing these exact values by using the `.find()` method and passing in a query argument that includes the field and array we want to match:

```mongosh
db.books.find({ genres: ["young adult", "fantasy", "adventure"] })
```

This query would return documents where the `genres` field is an array containing exactly three values, `"young adult"`, `"fantasy"`, and `"adventure"`. For example, we would get a result that might look like this:

```
{
  _id: ObjectId(...),
  title: "Harry Potter and The Sorcerer's Stone",
  author: "JK Rowling",
  year_published: 1997,
  genres: ["young adult", "fantasy", "adventure"]
},
{
  _id: ObjectId(...),
  title: "The Gilded Ones",
  author: "Namina Forna",
  year_published: 2021,
  genres: ["young adult", "fantasy", "adventure"]
}
```

Note that this query would only return documents where the array field contains precisely the values included in the query in the specified order.

### Matching Individual Array Elements
Imagine we know we want to find a book that has the genre `"young adult"`, but are otherwise open to any genre. Instead of providing the entire array as a query argument, we could provide just the value we want to match, like so:

```mongosh
db.books.find({ genres: "young adult" })
```

This would return all documents that have a `genres` field that is an array that contains the value `"young adult"`, in addition to any other genres.

### Matching Multiple Array Elements with $all
We can use the [`$all`](https://www.mongodb.com/docs/manual/reference/operator/query/all/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) operator to match documents for an array field that includes all the specified elements, without regard for the order of the elements or additional elements in the array.

For example, let’s say we’ve finished our young adult novel and are ready to move on to something that spans the science fiction and adventure genres. We could use the `$all` operator to perform this query, like so:

```mongosh
db.books.find({ genres: { $all: [ "science fiction", "adventure" ] } })
```

Notice that using the `$all` operator will match documents where the given array field contains all the specified elements in _any_ order, not necessarily the order provided in the query. Furthermore, our search returns documents where the `genres` array includes other elements, in addition to the ones specified in our query.

### Querying on Compound Filter Conditions
In addition to querying array fields for exact matches and individual elements, we can use comparison operators to search for documents where elements in an array field meet some condition or range of conditions.

For example, imagine we have a collection of tennis athletes, called `tennis_players`, with each document having a similar structure:

```
{
  _id: ObjectId(...),
  name: "Serena Williams",
  country: "United States",
  wimbledon_singles_wins: [2002, 2003, 2009, 2010, 2012, 2015, 2016]
}
```

If we wanted to search this collection for all athletes who have been Wimbledon Singles Champions from the year 2000 onward, we could run the following query:

```mongosh
db.tennis_players.find({ wimbledon_singles_wins: { $gte: 2000 } });
```

This would return all documents where the `wimbledon_singles_wins` array has at least one element with a value of `2000` or greater.

We can also query based on compound conditions. Let’s consider that we want to search our `tennis_players` collection to find all athletes who won a Wimbledon Singles Championship either before 1935, in the first 50 years of the championship, or after 1971, in the 50 most recent years of the tournament. We could achieve this with the following query:

```mongosh
db.tennis_players.find({ wimbledon_singles_wins: { $gt: 1971, $lt: 1935 } })
```

Note that this query would match documents where the array contains elements that satisfy the query conditions in some combination. One element could satisfy the greater than `1971` condition, while another could satisfy the less than `1935` condition. And if the ranges overlapped, a single element could satisfy both conditions. However, using this syntax, it is not necessary that a single element satisfies all conditions.

### Querying for all conditions with $elemMatch
The [`$elemMatch`](https://www.mongodb.com/docs/manual/reference/operator/query/elemMatch/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) operator is used in queries to specify multiple criteria on the elements of an array field, such that any returned documents have at least one array element that satisfies all the specified criteria.

Imagine that we want to search our collection again, this time, for any athletes who have won the Wimbledon Singles Championship in the current millennium, between the years 2000 and 2019.

```mongosh
db.tennis_players.find({ 
 wimbledon_singles_wins: { $elemMatch: { $gte: 2000, $lt: 2020 } } 
})
```

This would only return documents whose `wimbledon_singles_wins` field is an array containing at least one element that is both greater than or equal to `2000` _and_ less than `2020`.

```
{
  _id: ObjectId(...),
  name: "Pete Sampras",
  country: "United States",
  wimbledon_singles_wins: [1993, 1994, 1995, 1997, 1998, 1999, 2000]
},
{
  _id: ObjectId(...),
  name: "Serena Williams",
  country: "United States",
  wimbledon_singles_wins: [2002, 2003, 2009, 2010, 2012, 2015, 2016]
},
{
  _id: ObjectId(...),
  name: "Roger Federer",
  country: "Switzerland",
  wimbledon_singles_wins: [2003, 2004, 2005, 2006, 2007, 2009, 2012, 2017]
}
```

Note that while any matching documents _must_ contain at least one value in the `wimbledon_singles_wins` array that is between the range of `2000` and `2020`, this array can also include values that fall outside that range.

### Querying an Array of Embedded Documents
It’s common for a collection to have an array of documents rather than individual values. For instance, take our `tennis_players` collection again, but now with a slightly different structure:

```
{
  _id: ObjectId(...),
  name: "Miyu Kato",
  country: "Japan",
  wimbledon_doubles_placements: 
  [{ 
    year: 2016,
    place: 2
  }, 
  { 
    year: 2017,
    place: 1
  },
  { 
    year: 2018,
    place: 1
  },
  { 
    year: 2019,
    place: 1
  }]
}
```

First, let’s see how we can do an exact match on the _entire_ embedded document. For example, if we wanted to query our `tennis_players` collection for players who placed 2nd in 2019:

```mongosh
db.tennis_players.find( { "wimbledon_doubles_placements": { year: 2019, place: 2 } } )
```

In the above query, the field order must be exactly the order we are looking for, with the exact field values. This query would match the below document because the order and values are exactly the same as the one in the query:

```
{
  _id: ObjectId(...),
  name: "Gabriela Dabrowski",
  country: "Canada",
  wimbledon_doubles_placements: 
  [{ 
    year: 2019,
    place: 2
  }]
},
{
  _id: ObjectId(...),
  name: "Yifan Xu",
  country: “China”,
  wimbledon_doubles_placements: 
  [{ 
    year: 2019,
    place: 2
  }]
}…
```

We can also query based on a single field. For example, if we just wanted to query for any Wimbledon doubles winners in the year 2016, we can do the following:

```mongosh
db.tennis_players.find( { "wimbledon_doubles_placements.year": 2016 )
```

Notice that the syntax is exactly the same as when we were querying for non-array fields. The embedded document field and parent document field must be wrapped in quotation marks (single or double) and use the dot (`.`) notation. This query would return results like the following:

```
{
  _id: ObjectId(...),
  name: "Tímea Babos",
  country: "Hungary",
  wimbledon_doubles_placements: 
  [{ 
    year: 2015,
    place: 4
   },
   {
    year: 2016,
    place: 2
  }]
{
  _id: ObjectId(...),
  name: "Yaroslava Shvedova",
  country: "Kazakhstan",
  wimbledon_doubles_placements: 
  [{ 
    year: 2010,
    place: 1
   },
   {
    year: 2016,
    place: 2
  }]
}…
```

Here, our query result has all the documents that have an embedded document with a `year` field with the value of `2016`.
 
  It’s important to note we can even combine these queries with query operators and even do multiple query conditions using `$elemMatch`.

### Review
- We can query documents for exact array matches by using the `.find()` method and passing in a query document containing the field name, and its array as the value.
- We can match a single array element by using the `.find()` method and passing in a query document containing the field name, and the element we want to match as its value.
- To match multiple elements in an array, we can apply the `$all` operator to the `.find()` method.
- The `$all` operator will match any document where the given array field contains all the specified values, in any order and regardless of other elements in the array.
- We can use the `.find()` method with comparison operators to match documents where the array contains one or more elements that satisfy the query conditions in some combination.
- To match documents where the array contains one or more elements that satisfy _all_ the query conditions, we can apply the `$elemMatch` operator to the `.find()` method.
- We can query embedded documents in an array field by querying for either an exact match (with the exact order) or by querying for a single field.

In addition to the syntax we’ve covered in this lesson, MongoDB provides us with even more operators that can be useful to us when querying on array fields:

- The [`$size`](https://www.mongodb.com/docs/manual/reference/operator/query/size/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) operator is used with `.find()` to match any array with the specified number of elements.
- The [`$in`](https://www.mongodb.com/docs/manual/reference/operator/query/in/) operator can be included in queries to match documents where the field is an array that contains at least one element in the specified array.
- The [`$nin`](https://www.mongodb.com/docs/manual/reference/operator/query/nin/) operator can be included in queries to match documents where the field is an array that contains no elements mentioned in the given array.


# MongoDB CRUD II

## Inserting and Updating

### The `_id` Field
As you continue to work with documents in MongoDB, you may notice one field that exists across every document: the [`_id`](https://www.mongodb.com/docs/manual/core/document/#the-_id-field/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) field. It might look similar to this:

```
_id: ObjectId("5eb3d668b31de5d588f4305b")
```

The `_id` field plays a vital role in every document inside of a MongoDB collection, and it has a few distinct characteristics:

- The `_id` field is required for every document in a collection and must be unique.
- MongoDB automatically generates an `ObjectId` for the `_id` field if no value is provided.
- Developers can specify the `_id` with something other than an `ObjectId` such as a number or random string, if desired.
- The `_id` field is immutable, and once a document has an assigned `_id`, it cannot be updated or changed.

The `ObjectId` is a 12-byte data type that is commonly used for the `_id` field. When generated automatically, each `ObjectId` contains an embedded timestamp which is generally unique. This allows documents to be inserted in order of creation time (or very close to it) and for users to roughly sort their results by creation time if necessary. While we won’t explicitly need the `_id` field to update or create new documents, it’s important to note that this is how MongoDB identifies each unique document that is inserted or updated in a collection.

### Inserting a Single Document
In MongoDB, we can use the [`.insertOne()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.insertOne/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) method to insert a single new document!

The syntax for the method looks as follows:

```
db.<collection>.insertOne(
  <new_document>, 
  {
    writeConcern: <document>,
  }
);
```

The `.insertOne()` method has a single required parameter, the document to be inserted, and a second optional parameter named `writeConcern`. We won’t be working with the `writeConcern` parameter in this course, but more details about the parameter can be found in the official [MongoDB documentation](https://www.mongodb.com/docs/manual/reference/write-concern/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral). For now, know that it’s an optional parameter that allows us to specify how we want our write requests to be acknowledged by MongoDB.

Let’s take a look at an example where we insert a single document into a `videogames` collection:

```mongosh
db.videogames.insertOne({
  title: "Elden Ring",
  year: 2022,
  company: "Fromsoftware"
});
```

When a document is successfully inserted with `.insertOne()`, the output is an object with a field named `acknowledged` (related to the `writeConcern` parameter we mentioned earlier) with the value `true` and a field named `insertedId` where the value is the `_id` field for the newly inserted document. Here is what it looks like:

```
{
  "acknowledged": true,
  "insertedId": ObjectId("5fd989674e6b9ceb8665c63d")
}
```

Note that if we try to insert into a specified collection that does not exist, MongoDB will create one and insert the document into the newly created collection.

### Inserting Multiple Documents
As its name suggests, `.insertMany()` will insert multiple documents into a collection. Much like `.insertOne()`, if the collection we’ve specified does not exist, one will be created.

The syntax for the method is as follows:

```
db.<collection>.insertMany(
  [<document1>, <document2>, ...],
  {
    writeConcern: <document>,
    ordered: <boolean>
  }
);
```

This method has three parameters:

1. An array of documents; the documents we want to add to the collection.
2. A parameter named `writeConcern`.
3. A parameter named `ordered`.

The `ordered` parameter can be handy since it allows us to specify if MongoDB should perform an ordered or unordered insert. If set to `false`, documents are inserted in an unordered format. If set to `true`, the default behavior, MongoDB will insert the documents in the order given in the array.

It’s worth noting that with ordered inserts, if a single document fails to be inserted, the entire insert operation will cease, and any remaining documents will not be inserted. On the other hand, unordered inserts will continue in the case of an insert failure and attempt to insert any remaining documents.

Let’s look at an example of `.insertMany()` on a collection named `students`:

```mongosh
db.students.insertMany([
  {
    name: "Mia Ramirez",
    age: 15
  },
  {
    name: "Kiv Huang",
    age: 17
  },
  {
    name: "Sam Soto",
    age: 16
  }
], { ordered: true })
```

### Updating a Single Document
In MongoDB, we can use the [`.updateOne()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.updateOne/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) method to update a single document. The method finds the first document that matches specific filter criteria and applies specified update modifications. Note that it updates the _first_ matching document, even if multiple documents match the criteria.

Let’s take a look at the syntax for the `.updateOne()` method:

```
db.<collection>.updateOne(<filter>, <update>, <options>)
```

The method has three parameters:

- `filter`: A document that provides selection criteria for the document to update.
- `update`: A document that specifies any modifications to be applied. This parameter gives us quite a bit of flexibility, allowing us to modify existing fields, insert new ones, or even replace an entire document.
- `options`: A document that includes any additional specifications for our update operation such as `upsert` and `writeConcern`.

To explore the importance of each of these parameters and how the `updateOne()` method works, consider a third-party retail store for used smartphones. The store keeps all their information in a collection called `products`, where each document holds information regarding a specific type of smartphone:

```
{ 
  _id: ObjectId("507f1fg7bcf865d799439h11"), 
  title: "iPhoneX", 
  price: 1000,
  stock: 25 
},
{ 
  _id: ObjectId("507f1fg7bcf865d799439h12"), 
  title: "iPhone7", 
  price: 600,
  stock: 25 
},
{ 
  _id: ObjectId("507f1fg7bcf865d799439h13"), 
  title: "iPhone6", 
  price: 500,
  stock: 25 
}
```

To start an update operation, we must first choose our filter. This is similar to when we used find() to retrieve a document based on specific criteria. So, for example, if we wanted to update only the document with the title "IPhoneX", we could specify the title as the filter:

```mongosh
db.products.updateOne({ title: "iPhoneX" }, <update>, <options> });
```

To update a document in MongoDB, we have to specify what fields we want to update and _how_ we want to update them. This is where the `update` parameter comes into play. To specify how we want to update a document, we can use [MongoDB update operators](https://www.mongodb.com/docs/manual/reference/operator/update/#std-label-update-operators/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral). MongoDB offers us several update operators that can perform a variety of modifications to document fields. In this exercise, we’ll focus on the [`$set`](https://www.mongodb.com/docs/manual/reference/operator/update/set/#mongodb-update-up.-set/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) update operator. This operator allows us to replace a field’s value with one that we provide.

To see this in action, imagine a new phone model is launching soon, and the price of the `"iPhoneX"` will need to be decreased in order to remain competitive. We want to update the price from `1000` to `679`. We can accomplish this by running the following command:

```mongosh
db.products.updateOne({ title: "iPhoneX" }, { $set: { price: 679 } });
```

If successful, the operation should return:

```
{ "acknowledged" : true, "matchedCount" : 1, "modifiedCount" : 1 }
```

In this case, querying on the `title` field works fine, assuming the value is unique for every document. Usually, we want to be as specific as possible with our filtering criteria, so we can include multiple fields to add more specificity to our search. Remember that even if multiple documents match the filter criteria, only a single one (the first match) will be updated.

### Updates on Embedded Documents and Arrays
Consider the following document within a collection named `furniture`:

```
{
  _id: ObjectId("3ldh1fg733kf65d7994393ld"),
  name: "bedframe",
  dimensions: {
    length: 75,
    width: 38
  }
}
```

Let’s say we wanted to update the `width` field inside the `dimensions` embedded document. We could run the following command:

```mongosh
db.furniture.updateOne(
  { name: "bedframe" },
  { $set: { "dimensions.width": 54 }}
);
```

We can successfully target the `width` field inside the `dimensions` embedded document using [dot notation](https://www.mongodb.com/docs/manual/core/document/#dot-notation/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral).

MongoDB also stores data inside of arrays! If we instead want to update a value within an array, we can use dot notation to access the index of the element we want to update. Let’s look at the following example document for a collection named `nbateams`:

```
{
  _id: ObjectId("402h1fg73cf865d799439k42"),
  team: "Chicago Bulls",
  championships: [1991, 1902, 1993, 1996, 1997, 1998]
}
```

If we want to update the 2nd element (1902) of the `championships` array to the correct year, `1992`, we could run the following command:

```mongosh
db.nbateams.updateOne(
  { team: "Chicago Bulls" }, 
  { $set: {"championships.1": 1992 }}
)
```

Once again, the embedded document’s name and the array index must be wrapped in quotations for the command to be successful. Note that we’re using the index of `1` since the year `1902` is the second element of the array, and arrays start at index `0`.

### Updating an Array with New Elements
The `$push` operator adds (or “pushes”) new elements to the end of an array. It can be used with the `.updateOne()` method with the following syntax:

```
db.<collection>.updateOne(
  <filter>,
  { $push: { <field1>: <value1>, ... } }
);
```

Consider a collection, `automobiles`, holding a document with data regarding specific car models:

```
{
  _id: ObjectId("627934bbfd6a8619040cc287"),
  make: "Audi",
  model: "A1",
  year: [2017, 2019]
}
```

If we wanted to add a new year into the array, we could use the `$push` operator to accomplish this:

```mongosh
db.vehicles.updateOne(
  { make: "Audi" },
  { $push: { year: 2020 }}
);
```

It’s important to note that if the mentioned field is absent in the document to update, the `$push` operator adds this field to the document as an array and includes the given value as its element.

### Upserting a Document
The `upsert` option is an optional parameter we can use with update methods such as `.updateOne()`. It accepts a boolean value, and if assigned to `true`, `upsert` will give our `.updateOne()` method the following behavior:

1. Update data if there is a matching document.
2. Insert a new document if there’s no match based on the query criteria.

Let’s take a look at its syntax below:

```
db.<collection>.updateOne(
  <filter>, 
  <update>, 
  { upsert: <boolean> }
);
```

The `upsert` parameter is false by default. If the property is omitted, the method will only update the documents that match the query. If no existing documents match the query, the operation will complete without making any changes to the data.

To see the `upsert` option in action, consider a collection named `pets`, holding a large number of documents with the following structure:

```
{
  _id: ObjectId(...),
  name: "Luna",
  type: "Cat",
  age: 2
}
```

Imagine it’s Luna’s birthday, and we want to be sure that we capture her current age, but we aren’t sure whether or not we have an existing document for her. This would be an excellent opportunity to use `upsert` since one of two things will happen:

- If Luna does not exist in the database, our command will create the document
- If Luna does exist, the document will be updated

To `upsert` our document for Luna, we can call the `.updateOne()` command as follows:

```mongosh
db.pets.updateOne(
  { name: "Luna", type: "Cat"},
  { $set: { age: 3 }},
  { upsert: true }
)
```
 
### Updating Multiple Documents
The `.updateMany()` method allows us to update all documents that satisfy a condition. The `.updateMany()` method looks and behaves similarly to `.updateOne()`, but instead of updating the first matching document, it updates all matching documents:

Let’s examine its syntax:

```
db.<collection>.updateMany(
  <filter>, 
  <update>, 
  <options>
);
```

Like before, we have three main parameters:

1. `filter`: The selection criteria for the update.
2. `update`: The modifications to apply.
3. `options`: Other options that could be applied, such as `upsert`.

Suppose a company sets a minimum salary for all employees. We want to update all employees with a salary of $75,000 to the new minimum of $80,000. Here is what our collection of `employees` might look like:

```
{
  _id: ObjectId(...),
  name: "Rose Nyland",
  department: "Information Technology",
  salary: 75000
},
{
  _id: ObjectId(...),
  name: "Dorothy Zbornak",
  department: "Human Resources",
  salary: 75000
},
{
  _id: ObjectId(...),
  name: "Sophia Petrillo",
  department: "Human Resources",
  salary: 75000
},
{
  _id: ObjectId(...),
  name: "Blanche Devereaux",
  department: "Sales",
  salary: 80000
}
```

We can use `.updateMany()` to target all employees with the same salary in order to increase it:

```mongosh
db.employees.updateMany(
  { salary: 75000 },
  { $set: { salary: 80000 }}
)
```

### Modifying Documents
In MongoDB, sometimes we may want to update a document but also return the document we modified. The [`.findAndModify()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.findAndModify/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) method modifies and _returns_ a single document. By default, the document it returns does not include the modifications made on the update. This method can be particularly useful if we want to see (or use) the state of an updated document after we perform an update operation. This method also has a lot of flexible optional parameters that aren’t available in other methods.

Let’s take a look at the syntax of the `.findAndModify()` method below:

```
db.<collection>.findAndModify({
  query: <document>,
  update: <document>,
  new: <boolean>,
  upsert: <boolean>,
  ...
});
```

Note that there are four commonly used fields:

1. `query`: Defines the selection criteria for which record needs modification.
2. `update`: A document that specifies the fields we want to update and the changes we want to make to them.
3. `new`: When `true`, this field returns the modified document rather than the original.
4. `upsert`: Creates a new document if the selection criteria fails to match a document.

Note: In addition to these fields, the `.findAndModify()` method accepts many other options. We will not be covering them here, but more details can be found in the documentation for the [`.findAndModify()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.findAndModify/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) method.

With this method, there are a lot of scenarios that can occur. First, let’s consider a collection called `foodTrucks` containing the following document:

```
{
  _id: ObjectId(...),
  name: "Criff Dogs",
  address: "15 Bedford Ave",
  shutdown: false
},
{
  _id: ObjectId(...),
  name: "Sals Pizza",
  address: "249 Otter Place",
  shutdown: false
}
```

The first scenario we can observe is if we wanted to update a document and see the updated document state pre-modification (before it was changed). This is the default behavior of the method. So, if we were to change the `shutdown` property of the document above with the name `"Criff Dogs"`, we can run the following command:

```mongosh
db.foodTrucks.findAndModify({
  query:  { name: "Criff Dogs" },
  update: { shutdown: true }
});
```

The output of this method would be the document _before_ it was modified.

The next scenario is similar but would use the `new` field to return a different output. If we ran the following query:

```mongosh
db.foodTrucks.findAndModify({
  query:  { name: "Criff Dogs" },
  update: { shutdown: true },
  new: true
});
```

We would be able to see the _new_ _modified_ document as the output.

Lastly, we can use the `upsert` field to be able to add documents if they do not currently exist in the database. So if we ran the following command:

```mongosh
db.foodTrucks.findAndModify({
  query:  { name: "Ben and Jerry", address: "17 Cliff Pl" },
  update: { shutdown: false },
  new: true,
  upsert: true
});
```

MongoDB would then search the collection `foodTrucks` based on the query argument, and if it didn’t find a match, it would create the document.

We might notice that `.updateOne()` and `.findAndModify()` behave quite similarly. Both will update a document in our database or create one if it doesn’t exist. So what are the main differences? Well, `.findAndModify()` returns the document that you modify, whereas `.updateOne()` does not. Moreover, `.findAndModify()` allows us to specify whether we want to return the old or new (modified version) of the updated document with the use of the `new` parameter.

### Review
- The `_id` field is a unique identifier for documents in a collection. By default, MongoDB assigns an `ObjectId` value to the `_id` field for each document.
- Individual documents can be added to a collection with `.insertOne()`, and the document to be inserted is provided as an argument.
- Multiple documents can be inserted into a collection with the `.insertMany()` method. An array containing all the documents to insert is passed in an argument.
- The `.updateOne()` method is used to update the first document within the collection that matches a given query.
- We can use `.updateMany()` to update multiple matching documents simultaneously.
- The `$push` operator appends a specified value to an array.
- The `.findAndModify()` method modifies and returns a single document in a collection. By default, it returns the original document, and if no matching document is found, a new one can be inserted by adding the upsert option.

In addition to the methods we’ve learned throughout this lesson, MongoDB offers us other syntax and commands that can be useful when inserting, updating, or replacing documents:

- The [`ordered`](https://www.mongodb.com/docs/manual/reference/method/db.collection.insertMany/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral#execution-of-operations) parameter can be provided to the `.insertMany()` method. It accepts a boolean value, and, if set to false, will insert the documents in an unordered format to increase performance.
- The [`$unset`](https://www.mongodb.com/docs/manual/reference/operator/update/unset/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) operator can be provided to the `.updateOne()` or `.updateMany()` method. It removes a particular field from a document.
- The [`.findOneAndUpdate()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.findOneAndUpdate/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) method is similar to `.updateOne()`, but instead of returning a document acknowledging the success or failure of our operation, it returns either the original or updated document.
- The [`.renameCollection()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.renameCollection/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) method allows us to update the name of our collection without modifying any of its documents.
- The [`.bulkWrite()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.bulkWrite/#definition) method allows us to perform multiple write operations (updating or inserting) with controls for order of execution.


## Deleting Documents

### Deleting a Document
In order to use `.deleteOne()`, we must provide specific filtering criteria to find the document we want to delete. MongoDB will look for the first document in the collection that matches the criteria and delete it. Let’s take a closer look at the syntax:

```
db.<collection>.deleteOne(<filter>, <options>);
```

Note in the syntax above, the `.deleteOne()` method takes two arguments:

- `filter`: A document that provides selection criteria for the document to delete.
- `options`: A document where we can include optional fields to provide more specifications to our operation, such as a [`writeConcern`](https://www.mongodb.com/docs/manual/reference/method/db.collection.deleteOne/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral#std-label-deleteOne-wc).

To see `.deleteOne()` in action, consider a collection, `monsters`, with the following documents:

```
{
  _id: ObjectId(...),
  name: "Luca",
  age: 100,
  type: "Hydra"
},
{
  _id: ObjectId(...),
  name: "Lola",
  age: 95,
  type: "Hydra"
},
{
  _id: ObjectId(...),
  name: "Igor",
  age: 95,
  type: "Chimera"
},
```

If we want to delete a single monster with an age of `95`, we can run the following command:

```mongosh
db.monsters.deleteOne({ age: 95 });
```

If the command is successful, MongoDB will confirm the document was deleted with the following output:

```
{ acknowledged: true, deletedCount: 1 }
```

Notice that only one of the documents in the collection with the `age` of `95` was deleted. When the filter criteria is non-unique, the document that gets deleted is the first one that MongoDB identifies when performing the operation. Which document is found first depends on several factors which can include insertion order and the presence of indexes relevant to the filter.

### Deleting Multiple Documents
The [`.deleteMany()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.deleteMany/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) method removes all documents from a collection that match a given filter. This method uses the following syntax:

```
db.<collection>.deleteMany(<filter>, <options>);
```

Note in the syntax above that the `.deleteMany()` method takes two arguments:

- `filter`: A document that provides selection criteria for the documents to delete.
- `options`: A document where we can include optional fields to provide more specifications to our operation, such as a `writeConcern`.

Warning: If no filter is provided to the `.deleteMany()` method, all documents from the collection will be deleted.

Let’s revisit the original `monsters` collection from the previous exercise. Consider a new monster with the name of `"Pat"` was recently added:

```
{
  _id: ObjectId("629a1e8c2bf029cc101c92d4"),
  name: "Luca",
  age: 100,
  type: "Hydra"
},
{
  _id: ObjectId("629a2245b8bd9cad32a210fa"),
  name: "Lola",
  age: 95,
  type: "Hydra"
},
{
  _id: ObjectId("629a225119915a53df5b428c"),
  name: "Igor",
  age: 85,
  type: "Hydra"
},
{
  _id: ObjectId("629a226c8982a4dd04e093ff"),
  name: "Pat",
  age: 85,
  type: "Dragon"
}
```

We now want to get rid of all the monsters with a `type` field with the value of `"Hydra"`. We could run the `.deleteOne()` method and pass in the filter `{type: "Hydra"}`, but we would need to execute the method multiple times. This could quickly get very tedious. Instead, let’s use `.deleteMany()`:

```mongosh
db.monsters.deleteMany({ type: "Hydra" });
```

Once executed, the operation will successfully delete all documents where the `type` field has the value of `"Hydra"`. MongoDB will confirm if the operation was successful and let us know how many documents were deleted with the following output:

```
{ acknowledged: true, deletedCount: 3 }
```

### Replacing a Document
We might encounter situations where we need to delete a document and immediately replace it with another one. We could achieve this by running two separate methods, `.deleteOne()`, then `.insertOne()`. Fortunately, MongoDB provides us with a single method, `.replaceOne()`, that can both delete and insert all at once!

The [`.replaceOne()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.replaceOne/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral/) method replaces the first document in a collection that matches the given filter. The syntax for this method looks as follows:

```
db.<collection>.replaceOne(
  <filter>, 
  <replacement>, 
  <options>
);
```

Note in the syntax above that the `.replaceOne()` method takes three arguments:

- `filter`: A document that provides selection criteria for the document to replace.
- `replacement`: The replacement document.
- `options`: A document where we can include optional fields to provide more specifications to our operation, such as `upsert`.

The replacement document can contain a subset of fields of the original document or entirely unique fields. To see it in action, consider a collection named `employees` with the following documents:

```
{
  _id: ObjectId(...),
  name: "Rohit Kohli",
  department: "Customer Analytics"
  position: "Senior Software Engineer"
},
{
  _id: ObjectId(...),
  name: "Rin Paterson",
  department: "People Operations",
  position: "Head of People Operations"
}
```

Imagine `"Rohit Kohli"` leaves the company. We still want to store their name, and update their position to `"N/A"` but no longer need a `department` field and value. We’d then need to replace Rohit’s current document with a new document that only contains two fields: `name`, and `position`. We can accomplish this with `.replaceOne()`:

```mongosh
db.employees.replaceOne(
  { name: "Rhoit Kohli" }, 
  { name: "Rohit Kohli", position: "N/A" }
);
```

If successful, this would produce the following output:

```
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
```

Notice how the other fields were completely removed. This is the key difference between `.replaceOne()` and `.updateOne()`. Whereas `.updateOne()` updates specific fields based on the update modifiers provided, `.replaceOne()` replaces the entire document and will only include fields specified in the `<replacement>` parameter.

### Review
- The `.deleteOne()` method deletes a single document from a collection. It accepts a filter document specifying which document to delete as the first parameter.
- The `.deleteOne()` method will only delete the _first_ matching document in the collection.
- The `.deleteMany()` method deletes all matching documents from a collection. It accepts a filter document specifying which document to delete as the first parameter.
- The `.replaceOne()` method replaces an entire document from a collection. It takes in filtering criteria specifying the document to replace as the first parameter and a replacement document as the second one.
- The `.replaceOne()` method will only replace the _first_ matching document in the collection.
- Since `.replaceOne()` replaces an entire document, only fields included in the second parameter will be present in the document after the operation executes.

In addition to the syntax we’ve learned throughout this lesson, MongoDB offers us other syntax and commands that can be useful when deleting or replacing documents:

- The [`.findOneAndReplace()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.findOneAndReplace/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) method is very similar to `.replaceOne()`. It replaces a document in a collection based on filter criteria, but instead of returning a document that acknowledges the operation, it returns either the original document or the replacement document.
- The [`.findOneAndDelete()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.findOneAndDelete/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) method deletes a document, and returns the deleted document.
 

# Indexing in MongoDB

## Indexing in MongoDB

### What is Indexing?
Imagine if, for every query in MongoDB, we had to search the entire database to find our desired result. At scale, this would be a huge expenditure of time, computing power, and money. Fortunately, there’s a tool that can help make certain queries much more efficient - indexing. An **index** is a special data structure that stores a small portion of the collection’s data set in an easy-to-traverse form.

Let’s use a real-world example to understand how indexing in MongoDB works. Suppose in your global history class your assignment is to write an essay about Japan. Naturally, you’ll want to find all references in your history textbook about the country. But how can you find all pages that mention Japan? One method would be to look meticulously through every page in the textbook. This method is tedious, exhausting, and a poor use of your time. Using an [index](https://www.masterclass.com/articles/how-to-write-a-book-index#what-is-a-book-index), however, you could go to the letter “J” in the index, locate Japan, and proceed to the corresponding pages listed.

Using an index to look up all references of the word “Japan” is a much more efficient way to search compared to a complete scan of the book. Indexes in MongoDB seek to capture that same efficiency and optimize query performance. Queries that don’t use indexes must parse every document in a collection to find the appropriate matches. For relatively small collections this is fine, but as a collection grows this can begin to weigh down performance.

### The Types of Indexes in MongoDB
MongoDB supports several different types of indexes. You can, for instance, create an index that references only one field of a document - also known as a **single-field index**. If, for example, a high school principal wanted to organize a reunion for alumni who studied abroad in Argentina, they would want to run a query on all alumni who studied internationally, specifically in Argentina. Rather than query the entire alumni collection, they could capture a subset of this data by creating a single-field index on a field that’s exclusive to these alumni, for example, `study_abroad_nation`.

The principal can now use this single field index to query specific study abroad countries, like Argentina. This index makes our query more economical because it allows us to scan a subset of data rather than every document in the collection. Furthermore, because indexes arrange data in ascending or descending order, our queries are able to more quickly locate matching documents, making them more optimized for speed.

You can also create indexes on multiple fields, called **compound indexes**, to support more specific queries. If that same high school principal wanted to organize these alumni based on the year they studied abroad, he or she could create a compound index that references the country where students studied abroad _and_ when they studied abroad. The principal can now use this index to query specific countries, and, since indexes are ordered they can easily sort that subset of matching students chronologically. Notably, the sorted nature of indexes can also improve the efficiency of range-based query operations, where we are seeking to match values that span a given range.

One last type of index worth mentioning is multikey indexes. These indexes support optimized queries on array fields by indexing each element in the array. Conveniently, MongoDB automatically creates a multikey index for us whenever we create an index on a field whose value is an array. Multikey indexes are compatible with both single field and compound indexes.

### Tradeoffs and Precautions When Working with Indexes
Indexes are not a cure-all for query optimization and some precautions should be kept in mind. Indexes are most beneficial when they support queries which are selective in nature (the result set represents a small portion of the data in the collection). We should also aim to be conservative, and plan ahead when creating indexes. Each index consumes valuable space. And while indexes can improve query performance, they do so at the cost of write performance. Each time we insert, remove, or update documents in a collection, MongoDB must reflect those changes for each index in the collection, ultimately slowing down the operation. With proper planning, indexes can greatly leverage the power of MongoDB and optimize your queries to improve computing performance, bandwidth, and time efficiency.

### Wrap Up
- Indexes are data structures that capture a subset of a collection’s data in an easy to traverse form.
- Indexes can support more efficient queries of large collections.
- Single field indexes reference one field from a document, while compound indexes reference multiple fields.
- The primary advantage of indexes is that they support faster queries. The greatest tradeoff of indexes is that they can marginally decrease write performance.


## Introduction to Indexing

### Single Field Index
In MongoDB, indexes play an important role in making sure our [database](https://www.codecademy.com/resources/docs/general/database) performs optimally. Recall, an [index](https://www.mongodb.com/docs/manual/indexes/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) is a special data structure that stores a small portion of the collection’s data in an easy-to-traverse form. We have already used indexes when we queried by the `_id` field since MongoDB creates a default index on the `_id` field for all our documents.

However, we can also create our own custom index by using the [`.createIndex()`](https://www.mongodb.com/docs/v5.3/reference/method/db.collection.createIndex/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) [method](https://www.codecademy.com/resources/docs/general/method). The syntax looks like this:

```
db.<collection>.createIndex({ <keys>, <options>, <commitQuorum>)}
```

We have three main parameters:

- `keys`: A document that contains the field and value pairs where the field is the index key and the value describes the type of index for that field.
- `options`: A document of various optional options that control index creation.
- `commitQuoroum`: A more advanced [parameter](https://www.codecademy.com/resources/docs/general/parameter) that gives control over replica sets. We won’t be working with this parameter in this lesson.

In this lesson, we will mostly work with the `keys` parameter. To learn more about the various other parameters, visit the [official documentation](https://www.mongodb.com/docs/v6.0/reference/method/db.collection.createIndex/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral). That said, our syntax will look closer to this:

```
db.<collection>.createIndex({ <field>: <type> });
```

For the `keys` parameters, we must pass a document with field-type pairs. Fields can be assigned a value of `1` or `-1`. A value of `1` will sort the index in ascending order, while a value of `-1` would sort the index in descending order. If the field contains a [string](https://www.codecademy.com/resources/docs/general/data-types/string) value, `1` will sort the documents in alphabetical order (A-Z), and `-1` will sort the documents in reverse order (Z-A).

To see `.createIndex()` in action, imagine as a university president, we have a collection of every student within your database, called `students`. A sample document from the `students` collection might look like this:

```
{ 
  _id: ObjectId(...),
  last_name: "Tapia",
  first_name: "Joseph",
  major: "architecture",
  birth_year: 1988,
  graduation_year: 2012,
  year_abroad: 2011
}
```

Perhaps we are organizing reunions for students who studied abroad and found ourselves frequently searching the database for students who studied internationally during a particular year. Rather than repeatedly querying the entire `students` collection by the `year_abroad` field, it would be beneficial to create an index based on this particular field, also known as a single field index. We could run the following command:

```mongosh
db.students.createIndex({ year_abroad: 1 });
```

The above command would create an index on all the documents in the student’s collection based on the `year_abroad` field, sorted in ascending order.

We can run a query on the indexed field to utilize the indexed `year_abroad` field. Here’s an example query that uses this new index to search for students who have studied abroad from 2020 onward:

```mongosh
db.students.find({ year_abroad: { $gt: 2019 }});
```

Creating a single field index can save us significant time in our query since we’d only be scanning the index for ordered values of the `year_abroad` field rather than browsing the entire collection and examining every document.

### Performance Insights with .explain()
Since indexing in MongoDB is tied closely to [database](https://www.codecademy.com/resources/docs/general/database) performance, it would be ideal to have a way to see how our indexes impact our queries. The [`.explain()`](https://www.mongodb.com/docs/manual/reference/method/cursor.explain/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral#mongodb-method-cursor.explain) [method](https://www.codecademy.com/resources/docs/general/method) can offer us insight into the performance implications of our indexes. The method has the following syntax:

```
db.<collection>.find(...).explain(<verbose>)
```

Note that the method is appended to the `.find()` method. It also takes one [string](https://www.codecademy.com/resources/docs/general/data-types/string) [parameter](https://www.codecademy.com/resources/docs/general/parameter) named `verbose` that specifies what the method should explain. The possible values are: [`"queryPlanner"`](https://www.mongodb.com/docs/manual/reference/method/cursor.explain/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral#queryplanner-mode), [`"executionStats"`](https://www.mongodb.com/docs/manual/reference/method/cursor.explain/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral#executionstats-mode), and [`"allPlansExecution"`](https://www.mongodb.com/docs/manual/reference/method/cursor.explain/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral#allplansexecution-mode). Each value offers meaningful insights on a query. To gain insights regarding the execution of the winning query plan for a query, we can use the `"executionStats"` option.

To see `.explain()` in action, let’s refer back to our study abroad example from the previous exercise. Let’s examine how to use this method by appending the `.explain()` method to our query from the previous exercise:

```mongosh
db.students.find({ year_abroad: { $gt: 2019 }}).explain('executionStats');
```

Running our query with `"executionStats"` outputs a series of objects containing detailed information about our operation. We won’t include the entire output below, but rather we’ll focus on a specific [object](https://www.codecademy.com/resources/docs/general/data-structures/object), called [`executionStats`](https://www.mongodb.com/docs/manual/reference/explain-results/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral#executionstats).

If we were to execute the `.explain()` method before creating our [index](https://www.codecademy.com/resources/docs/general/database/index) on the `year_abroad` field, the output might look something like this:

```
executionStats: {
  executionSuccess: true,
  nReturned: 1336,
  executionTimeMillis: 140,
  totalKeysExamined: 0,
  totalDocsExamined: 5555,
  executionStages: {
    …
  }
}
```

Examine the `nReturned`, `totalDocsExamined`, and `executionTimeMillis` fields. Notice that out of 5555 total documents, only 1336 were returned by our query, which took approximately 140 milliseconds.

Now let’s look at what the output of our query might look like after we index the `year_abroad` field:

```
executionStats: {
  executionSuccess: true,
  nReturned: 1336,
  executionTimeMillis: 107,
  totalKeysExamined: 1336,
  totalDocsExamined: 1336,
  executionStages: {
   …
  }
}
```

When we ran our query _after_ creating our index, we still returned 1336 documents, but instead of examining the entire collection, 5555 documents, we only examined the 1336 we returned. This is because our query first scanned the index to identify documents that matched our filter, then returned only the corresponding documents without browsing every document in the collection.

Take a look at the `executionTimeMillis` for each query. You’ll also notice that our query after creating the index took 107 milliseconds, while our query before creating the index took a bit longer, 140 milliseconds. This might not seem like much, but if we were working with a collection containing tens or hundreds of thousands of documents, the time difference would likely be much more significant.

### Compound Indexes
[Compound indexes](https://www.mongodb.com/docs/v5.0/core/index-compound/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) contain references to multiple fields within a document and support queries that match on multiple fields. Let’s have a look at the syntax for creating a compound index:

```
db.<collection>.createIndex({ 
  <field>: <type>, 
  <field2>: <type>, 
  …
})
```

Similar to single field indexes, MongoDB will scan our [index](https://www.codecademy.com/resources/docs/general/database/index) for matching values, then return the corresponding documents. With compound indexes, the order of fields is important. To understand why, let’s return to our example from the first exercise about the university president.

Imagine that as president we wanted to plan reunions not just for students who studied abroad during a particular year, but also for students who studied abroad in a particular country. We could create a compound index on two fields: `study_abroad_nation` and `year_abroad`, like so:

```mongosh
db.students.createIndex({ 
  study_abroad_nation: 1, 
  year_abroad: -1 
});
```

This creates a single index that references two fields: `study_abroad_nation` in ascending, or alphabetical order, and `year_abroad` in descending, or reverse chronological order.

Because of how the fields are ordered, references within this index will be sorted first by the `study_abroad_nation` field. Within each value of the `study_abroad_nation` field, references will be sorted by the `year_abroad` field. This is an important consideration in determining how well our indexes will be able to support sort operations in our queries.

Now that we’ve created this compound index, anytime we query on these two fields, MongoDB will automatically employ this index to support our search.

The below query would be a use case for our compound index:

```mongosh
db.students.find({ 
  study_abroad_nation: "Brazil", 
  year_abroad: 2012 
});
```

Compound indexes can also support queries on any [**prefix**](https://www.mongodb.com/docs/v5.0/core/index-compound/#prefixes), or a beginning subset of the indexed fields. For example, consider the following compound index:

```mongosh
db.students.createIndex({ 
  study_abroad_nation: 1, 
  year_abroad: -1, 
  graduation_year: 1 
});
```

In addition to supporting a query that matches on the `study_abroad_nation`, `year_abroad` and `graduation_year` fields, this index would also be able to support queries on the following fields:

- `study_abroad_nation`
- `study_abroad_nation` and `year_abroad`

This index would _not_, however, be able to support queries on the following fields:

- `year_abroad`
- `graduation_year`
- `year_abroad` and `graduation_year`

As each index must be updated as documents change, unnecessary indexes can affect the write speed to our [database](https://www.codecademy.com/resources/docs/general/database). Make sure to consider if a compound index would be more efficient than creating multiple distinct single-field indexes to support your queries.

### Multikey Index on Single Fields
How do MongoDB indexes handle fields whose values are arrays? Conveniently, MongoDB automatically creates what’s known as a [**multikey index**](https://www.mongodb.com/docs/manual/core/index-multikey/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) whenever an [index](https://www.codecademy.com/resources/docs/general/database/index) on a [array](https://www.codecademy.com/resources/docs/general/data-structures/array) field is created. Multikey indexes provide an index key for each element in the indexed array.

Suppose we had a document within the `students` collection that had a field, `sports` with an array as its value:

```
{ 
  _id: ObjectId(...),
  last_name: "Tapia",
  first_name: "Joseph",
  major: "architecture",
  birth_year: 1988,
  graduation_year: 2012 ,
  sports: ["rowing", "boxing"]
}
```

We could create a multikey index on this field in the same way we would create any other single-field index:

```mongosh
db.students.createIndex({ sports : 1 });
```

This would create an index that references the `sports` field for every document in the collection. Since `sports` is an array field, the resulting multikey index would contain individual references to each element in the array. We specified ascending order for our index so the values would be organized in alphabetical order.

### Multikey Index on Compound Fields
Is it possible to create a compound multikey [index](https://www.codecademy.com/resources/docs/general/database/index) in MongoDB? The answer is yes, with a [very important caveat](https://www.mongodb.com/docs/manual/core/index-multikey/#compound-multikey-indexes/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) - only _one_ of the indexed fields can have an [array](https://www.codecademy.com/resources/docs/general/data-structures/array) as its value.

For example, suppose we had a document within a `students` collection with two fields with arrays as their values: `sports` and `clubs`.

```
{ 
  _id: ObjectId(...),
  last_name: "Tapia",
  first_name: "Joseph",
  major: "architecture",
  birth_year: 1988,
  graduation_year: 2012 ,
  sports: ["rowing", "boxing"],
  clubs: [“Honor Society”, “Student Government”, “Yearbook Committee”]
}
```

A single compound index can not be created on _both_ the `sports` and `clubs` fields. We could, however, successfully create a compound multikey index on `sports` _or_ `clubs` along with any of the other fields.

For example, either of the following would successfully create a compound multikey index:

```mongosh
db.students.createIndex({ sports: 1, major: 1 });
db.students.createIndex({ clubs: -1, graduation_year: -1 });
```

If we wanted to index both the `sports` and `clubs` fields, we’d have to create two separate indexes for them.

### Deleting an Index
Each time we make changes to a collection, any indexes associated with that collection must also be updated. In this way, unnecessary indexes can slow down the performance of certain CRUD operations. This is why it is important to review our indexes and remove any that are redundant or not being used.

Suppose, after some reflection, we discovered that a compound [index](https://www.codecademy.com/resources/docs/general/database/index) can handle all the queries we need to make, instead of the single field indexes we originally were relying on. Once we’ve created the compound index, it would be a good idea to identify and remove any unnecessary indexes.

First, we can use the [`.getIndexes()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.getIndexes/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) [method](https://www.codecademy.com/resources/docs/general/method) to see all of the indexes that exist for a particular collection.

Consider a collection called `students` that has multiple indexes:

```mongosh
db.students.getIndexes();
```

Might output:

```
[
   {  v : 1,
      key : { _id : 1 },
      name : '_id_'
   },
   {
      v : 1,
      key : { sports : -1 },
      name : 'sports_-1'
   },
   {
      v : 1,
      key : { sports : -1, graduation year : -1 },
      name : 'sports_-1_graduation_year_-1'
   }
]
```

Now that we have a list of our indexes for the `students` collection, we can see that both the second and third indexes index the `sports` key in descending order. Since compound indexes can support queries on any of the prefixed fields, our third index, named `'sports_-1_graduation_year_-1'`, can support queries on both `sports` and `graduation_year`.

This means that our second index, `'sports_-1'`, is redundant. MongoDB gives us another method, [`.dropIndex()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.dropIndex/), that allows us to remove an index, without modifying the original collection. We can use it to delete the `'sports_-1'` index:

```mongosh
db.students.dropIndex('sports_-1');
```

Getting rid of unnecessary indexes can free up disk space and speed up the performance of write operations, so as you start to use indexes more, it is worth regularly scrutinizing them to see which, if any, you can remove.

### Review
- An [index](https://www.codecademy.com/resources/docs/general/database/index) is a data structure that captures a subset of a collection’s data in an easy-to-traverse form. We can use the `.createIndex()` [method](https://www.codecademy.com/resources/docs/general/method) to create an index.
- A single field index is an index that references one field from a document.
- We can use the `.explain()` method with the `"executionStats"` [argument](https://www.codecademy.com/resources/docs/general/argument) to gain insight into the performance implications of our index on our query.
- A compound index is an index that contains references to multiple fields within a document.
- Multikey indexes are automatically created whenever we create an index on a field that contains an [array](https://www.codecademy.com/resources/docs/general/data-structures/array) value. Multikey indexes create an index key for each element in the array.
- A compound index cannot support two multikey indexes.
- The `.dropIndex()` method deletes an index without modifying the original collection.

In addition to the syntax we’ve learned throughout this lesson, MongoDB offers us other syntax and commands that can be useful when indexing collections:

- [Partial Indexes](https://www.mongodb.com/docs/manual/core/index-partial/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) only index documents in a collection that meet specific filter criteria. By indexing a subset of a collection’s documents, partial indexes consume less storage and have improved performance.
- [Sparse Indexes](https://www.mongodb.com/docs/manual/core/index-sparse/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) only index documents that include the specified index field. Any documents that do not have the field will be excluded from the index. Much like partial indexes, these indexes can use significantly less storage and have relatively improved performance compared to non-sparse indexes.
- [TTL Indexes](https://www.mongodb.com/docs/manual/core/index-ttl/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) are special single-field indexes that MongoDB can use to automatically remove documents from a collection after a certain amount of time or at a specific clock time.
- [Unique Indexes](https://www.mongodb.com/docs/manual/indexes/#unique-indexes/?utm_campaign=academia_partners&utm_source=codecademy&utm_medium=referral) enforce unique values for the indexed fields. Creating a unique index on a collection will restrict the insertion or update of documents where the indexed field’s value matches an existing value in the index.
 

# Explore MongoDB

## Explore MongoDB Aggregation

### Aggregation Basics
In plain terms, to aggregate means to combine out of several parts. When we apply this concept to a MongoDB database, aggregation is the process by which we can sift through large amounts of data one step at a time and, at each step, perform some form of filtering or computation on the data. Then, after multiple steps, we return a final result. This process can help us to see our data in a new way and provide valuable insights. So, how do we actually perform aggregation? One of the primary ways to accomplish aggregation in MongoDB is to use an **aggregation pipeline**.

An aggregation pipeline is a channel through which data passes from point A (the start of the pipeline) to point B (the end of the pipeline). Imagine, though, that the pipe is split into a number of segments. Each of these segments in the aggregation pipeline is called a **stage**, and each stage performs a specific operation on the data, such as sorting or filtering.

### Getting Started with Aggregation
To start using aggregation via an aggregation pipeline in MongoDB, we can use the following [`.aggregate()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.aggregate/#mongodb-method-db.collection.aggregate) method like so:

```
db.<collection>.aggregate()
```

MongoDB requires that inside of the `aggregate()` method, our first argument is an array containing the pipeline stages we use. To see a pipeline stage in action, let’s imagine we had the following small collection called `movies`, with each record having a field with the movie name and an associated rating (using the USA-based [MPA rating system](https://en.wikipedia.org/wiki/Motion_Picture_Association_film_rating_system)):

```
{
  name: "Star Wars: Clone Wars" 
  rating: "PG"
},
{
  name: "Indiana Jones and the Temple of Doom"
  rating: "PG"
},
{
  name: "Despicable Me"
  rating: "PG"
},
{
  name: "The Godfather"
  rating: "R"
}
```

We saw earlier, that in order to build a pipeline, we will need to define the stages we want to use. There are [many](https://www.mongodb.com/docs/manual/reference/operator/aggregation-pipeline/#stages) stages in MongoDB that help accomplish various tasks in aggregation. For now, let’s use a common stage called [`$match`](https://www.mongodb.com/docs/manual/reference/operator/aggregation/match/) that returns all the documents containing the specified field and value. This is similar to when we used the `find()` method and provided a query argument to filter a document based on a specific criteria.

The syntax to accomplish this aggregation would be the following:

```mongosh
db.movies.aggregate([
  {
    $match: {rating: "R"}
  }
])
```

And our result would be:

```
{
  name: "The Godfather",
  rating: "R"
}
```

### Aggregation in Action: Building a Multi-Stage Aggregation Pipeline
Imagine we had a large data set (thousands of records) of students in a school. Each student document has the following structure:

```
{ 
  student_id: 94204,
  first_name: "Sun",
  last_name: "Ko",
  grade_level: 6,
  test_scores: [99, 97. 96, 99],
  average_test_score: 98.65
}
```

We are tasked with gaining insights on students that might qualify for a prestigious scholarship. We need to produce a _new_ collection in our database called `candidates` that has the following criteria:

- The collection must only contain students in the 6th grade with an average test score above 97.
- The students in the new collection must be sorted by their first name (`first_name` field).

We also want the records in the new collection to have a new field called `highest_score` with the value of the highest score in the `test_scores` array field. This type of task would be a great candidate for using the aggregation framework!

We can start our aggregation pipeline with a first stage that filters out only students in the 6th grade with an average test score above 97. Just like before, we can use the `$match` stage:

```mongosh
db.students.aggregate([
  {
    // First stage
    $match: {grade_level: 6, average_test_score: {$gt: 97}}
  }
])
```

This first stage with `$match` should give us all the students that meet the conditions to qualify.

Next, we want to sort our result. Thankfully, MongoDB provides a stage named [`$sort`](https://www.mongodb.com/docs/manual/reference/operator/aggregation/sort/). Similar to how the `.sort()` method works, we can specify -1 or 1 to sort in ascending or descending order for a field. Here is what our pipeline would look like if we added a sorting stage:

```mongosh
db.students.aggregate([
  {
    // First stage
    $match: {grade_level: 6, average_test_score: {$gt: 97}}
  },
  { 
    // Second Stage
    $sort: { first_name: 1} 
  }
])
```

This new stage would take the resulting collection from the first stage (where we used `$match`) and sort the documents in ascending order by the `first_name` field.

At this point, we might think, “Why use an aggregation pipeline when I can accomplish the same goal with `find()` and `sort()` much quicker?”. That is a valid point, and if you likely had to just do those two stages, using `find()` and `sort()` likely would be quicker. However, the next two stages are where aggregation would start to shine as a better alternative.

First, let’s accomplish adding a new field to our records called `highest_score` with the value of the student’s highest test score. We can do so using the [`$addFields`](https://www.mongodb.com/docs/manual/reference/operator/aggregation/addFields/) stage. Before we add it to our pipeline, let’s examine the syntax of this operator:

```
{ $addFields: { <newField>: <expression>, …}}
```

Notice that this stage uses what is known as a [**expression**](https://www.mongodb.com/docs/manual/meta/aggregation-quick-reference/#std-label-aggregation-expressions). Aggregation expressions are commonly used in stages to perform some type of logic such as arithmetic or comparisons. There are many types of expressions including: [literals](https://www.mongodb.com/docs/manual/meta/aggregation-quick-reference/#std-label-agg-quick-ref-literals), [system variables](https://www.mongodb.com/docs/manual/meta/aggregation-quick-reference/#std-label-agg-quick-ref-variables), [expression objects](https://www.mongodb.com/docs/manual/meta/aggregation-quick-reference/#std-label-agg-quick-ref-expression-objects), and [expression operators](https://www.mongodb.com/docs/manual/meta/aggregation-quick-reference/#std-label-agg-quick-ref-operator-expressions). Here is what our pipeline looks like if we needed to get the highest score and create a new field:

```mongosh
db.students.aggregate([
  {
    // First stage
    $match: {grade_level: 6, average_test_score: {$gt: 97}}
  },
  { 
    // Second Stage
    $sort: { first_name: 1} 
  },
  { 
    // Third Stage
    $addFields:  {
      highest_score: { $max: "$test_scores" }  
    }
  }
])
```

Here, we are using the `$addFields` stage with the [`$max`](https://www.mongodb.com/docs/manual/reference/operator/aggregation/max/) expression operator, a specific type of expression, which allows us to pull the max value of the `test_scores` field so we can use it in our new `highest_score` field. Note that our `test_scores` field is prefixed with a `$` to indicate it is a [**field path**](https://www.mongodb.com/docs/manual/meta/aggregation-quick-reference/#field-paths). Field paths are used to access a document’s fields inside of an expression. We will have to use field paths often when working with aggregation. In this case, it allows us to access the `test_scores` field from our documents to use with the `$max` expression operator.

If we left it as is, our result from our aggregation pipeline would have documents like this:

```
{ 
  student_id: 94204,
  first_name: " Sun",
  last_name: "Ko",
  grade_level: 5,
  test_scores: [99, 97. 96, 99],
  average_test_score: 87.5,
  highest_score: 99
}
```

So far, so good! We just have one final task in our pipeline: creating a new collection. Creating a new collection can be accomplished by using the [`$out`](https://www.mongodb.com/docs/manual/reference/operator/aggregation/out/#mongodb-pipeline-pipe.-out) stage. Here’s how our pipeline would look after adding the `$out` stage:

```mongosh
db.students.aggregate([
  {
    // First stage
    $match: {grade_level: 6, average_test_score: {$gt: 97}}
  },
  { 
    // Second Stage
    $sort: { first_name: 1} 
  },
  { 
    // Third Stage
    $addFields:  {
      highest_score: { $max: "$test_scores" }  
    }
  },
  {
    // Fourth Stage
    $out : "candidates"
  }
])
```

The `$out` stage can output the final result of an aggregation pipeline to a new database, a new collection, or both! For this reason, it is required that it is the last stage in a pipeline. In this case, our aggregation result would be plopped into a new collection named `candidates`.

### When to Use Aggregation
Most of the CRUD methods that MongoDB offers are operational in nature. Their role is to perform some specific operation on our data and that’s it. With aggregation pipelines, we are able to perform multiple operations together to curate data that is more analytical in nature. This helps us see our data in a bigger picture.

In essence, consider using aggregation when:

- There are no CRUD methods (or a combination of methods) that accomplishes the query that needs to be performed easily.
- We need to perform analysis on datasets such as grouping values from multiple documents, computations on data, and analyzing data changes over time.

### Wrap Up
- In MongoDB, we can perform aggregation as an alternative way to query data.
- One way of accomplishing aggregation is by using an aggregation pipeline via the `.aggregate()` method.
- Aggregation pipelines allow us to incrementally filter data through the use of stages, where each stage filters/modifies the data in a specific way and then passes that data to the next stage.
- We can build a pipeline using stages such as `$match` or `$sort`.
- Some stages can utilize different types of expressions such as expression operators like `$max`.
- To reference fields from the documents in our collections inside of expressions, we must use a field path.
- Aggregation is particularly useful when we have tasks that can’t be accomplished with common CRUD methods easily or when we are looking to perform complex analytics on datasets.


## Explore MongoDB Atlas

### What is MongoDB Atlas?
MongoDB Atlas is a developer data platform. It includes a suite of cloud databases and data services. For the purposes of working with databases, Atlas hosts a variety of features that help us quickly set up, deploy, and maintain a MongoDB database. Atlas allows us to store and manage our data in the cloud through an easy-to-use website interface. With Atlas, we can have a MongoDB database set up and running in just a few clicks!

On top of simply storing our data, Atlas offers several different integrated [features](https://www.mongodb.com/cloud) to help us make the most of our data. A few of these are:

- Atlas Search - which allows for quick and easy text-based queries of data stored in the cloud.
- Atlas Charts - provides data visualization, which is fully integrated with the data we store with Atlas.
- Atlas Data Lake - helps perform large-scale analytics on our data.

### Atlas Data Storage
In Atlas, we interact with our data in what is known as a **cluster**. We can think of clusters as a unit of storage that MongoDB uses to house data. Depending on the plan we choose for our account, we can end up using clusters in a slightly different way. Atlas offers three different plan types:

- Free: Atlas offers a free plan that allows users to get started quickly without any worry of payments or budget. The free plan comes with 0.5GB of free storage and a set of basic configuration options. This plan is great for learning and exploring MongoDB in a cloud environment.
- Serverless: This plan is Atlas’ serverless database offering, which means users can create a database for their application without having to worry about security, reliability, managing performance, or managing scale. Serverless offers operations-based pricing that charges based on reads, writes, and storage. It’s a great option for applications that might have sparse or infrequent traffic.
- Dedicated: This plan is Atlas’ dedicated multi-region cluster offering. Dedicated clusters can be customized and optimized for specific workload requirements (e.g. higher CPU speeds and more memory), and have predictable pricing. Advanced security and multi-region options make this a great option for individuals and businesses running critical applications.

### Setting Up an Atlas Deployment
To start setting up our own Atlas cluster, we will need to register for an account. Get started by visiting the MongoDB [MongoDB registration page](https://www.mongodb.com/cloud/atlas/register) page and signing up for an account.

Next, we will need to enable access for connecting to the MongoDB database via our computer. We can do so by adding our IP address to the Atlas security settings to allow us to access our cluster from our computer. Click the “Add My Current IP Address” button.

### Set Up an Atlas Database
It’s time to start navigating and working with our Atlas cluster. Let’s start by navigating to our database dashboard. Click the “Database” tab under the “Deployment” header on the left-hand side:

This dashboard is a central location for managing the database component of our cluster. This dashboard shows important information about our database, such as its size and connections.

Our database will start off empty, but MongoDB allows us to fill it with a sample dataset (or even our own data). To do so, click the “Browse Collection” button on the database cluster section.

From here, we will be able to load a sample dataset by clicking the “Load Sample Dataset” button.

From our dashboard, we can browse our databases and their respective collections and query those collections for specific data.

### Connecting to Atlas
Navigate back to the main dashboard for the database by clicking the database tab on the left-hand side again. From here, we have the option to connect to the Atlas cluster by clicking the “Connect” button.

The menu for the connection offers us several options to connect to Atlas. For this article, and since we are most familiar with the MongoDB shell, let’s select the “Connect with MongoDB Shell” option.

### Wrap Up
- MongoDB Atlas is MongoDB’s cloud toolset offering that allows us to store our data in MongoDB databases that run in the cloud.
- MongoDB Atlas provides various other solutions on top of a cloud database, including tools to perform analytics, visualization, and efficient searching.
- MongoDB Atlas manages our data within clusters.
- MongoDB Atlas allows us to connect to our cloud database on our local machine via a command line.


# Cheatsheets

## Database Basics

![[mongodb_database_basics.pdf]]

## Introduction to MongoDB

![[mongodb_introduction_to_mongodb.pdf]]

## MongoDB CRUD I

![[mongodb_mongodb_crud_1.pdf]]

## MongoDB CRUD II

![[mongodb_mongodb_crud_2.pdf]]

## Indexing in MongoDB

![[mongodb_indexing_in_mongodb.pdf]]

## Explore MongoDB

![[mongodb_explore_mongodb.pdf]]