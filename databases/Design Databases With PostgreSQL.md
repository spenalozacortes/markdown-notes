# What Is A Database?
## Welcome to Design Databases with PostgreSQL
### What is a Relational Database Management System?

#### What is a Database?
A _database_ is a set of data stored in a computer. This data is usually structured in a way that makes the data easily accessible.

#### What is a Relational Database?
A _relational database_ is a type of database. It uses a structure that allows us to identify and access data _in relation_ to another piece of data in the database. Often, data in a relational database is organized into tables.

#### Tables: Rows and Columns
Tables can have hundreds, thousands, sometimes even millions of rows of data. These rows are often called _records_.

Tables can also have many _columns_ of data. Columns are labeled with a descriptive name (say, `age` for example) and have a specific _data type_.

The set of columns and data types make up the schema of this table.

#### What is a Relational Database Management System (RDBMS)?
A relational database management system (RDBMS) is a program that allows you to create, update, and administer a relational database. Most relational database management systems use the SQL language to access the database.

#### What is SQL?
SQL (**S**tructured **Q**uery **L**anguage) is a [programming language](https://www.codecademy.com/resources/blog/programming-languages/) used to communicate with data stored in a relational database management system.

Many RDBMSs use SQL (and variations of SQL) to access the data in tables. For example, SQLite is a relational database management system. SQLite contains a minimal set of SQL commands (which are the same across all RDBMSs). Other RDBMSs may use other variants.

#### Popular Relational Database Management Systems
SQL syntax may differ slightly depending on which RDBMS you are using.

##### MySQL
MySQL is the most popular open source SQL database. It is typically used for web application development, and often accessed using PHP.

The main advantages of MySQL are that it is easy to use, inexpensive, reliable (has been around since 1995), and has a large community of developers who can help answer questions.

Some of the disadvantages are that it has been known to suffer from poor performance when scaling, open source development has lagged since Oracle has taken control of MySQL, and it does not include some advanced features that developers may be used to.

##### PostgreSQL
PostgreSQL is an open source SQL database that is not controlled by any corporation. It is typically used for web application development.

PostgreSQL shares many of the same advantages of MySQL. It is easy to use, inexpensive, reliable and has a large community of developers. It also provides some additional features such as foreign key support without requiring complex configuration.

The main disadvantage of PostgreSQL is that it can be slower in performance than other databases such as MySQL. It is also slightly less popular than MySQL.

##### Oracle DB
Oracle Corporation owns Oracle Database, and the code is not open sourced.

Oracle DB is for large applications, particularly in the banking industry. Most of the world’s top banks run Oracle applications because Oracle offers a powerful combination of technology and comprehensive, pre-integrated business applications, including essential functionality built specifically for banks.

The main disadvantage of using Oracle is that it is not free to use like its open source competitors and can be quite expensive.

##### SQL Server
Microsoft owns SQL Server. Like Oracle DB, the code is close sourced.

Large enterprise applications mostly use SQL Server.

Microsoft offers a free entry-level version called _Express_ but can become very expensive as you scale your application.

##### SQLite
SQLite is a popular open source SQL database. It can store an entire database in a single file. One of the most significant advantages this provides is that all of the data can be stored locally without having to connect your database to a server.

SQLite is a popular choice for databases in cellphones, PDAs, MP3 players, set-top boxes, and other electronic gadgets.


## Using PostgreSQL On Your Own Computer
### Installing and Using PostgreSQL Locally

#### What is Postgres?
According to the [PostgreSQL website](https://www.postgresql.org/), Postgres is “a powerful, open-source object-relational database system with over 30 years of active development that has earned it a strong reputation for reliability, feature robustness, and performance.”

Postgres itself is a database “server.” There are several ways to connect to Postgres via “clients,” including [GUIs](https://en.wikipedia.org/wiki/Graphical_user_interface), [CLIs](https://en.wikipedia.org/wiki/Command-line_interface), and programming languages often via [ORMs](https://en.wikipedia.org/wiki/Object-relational_mapping). In order to run and use Postgres on your own computer, you will need to set up both a Postgres server and a client.

#### Setting Up Postgres (server)
##### Linux
Follow the instructions for [downloading Postgres for Linux](https://www.postgresql.org/download/linux/); we recommend using apt installation.
 

# How Do I Make And Populate My Own Database?
## Designing a Database Schema
### What is a Database Schema?

#### Introduction
Like an architectural blueprint, a database schema is documentation that helps its audience such as a database designer, administrator and other users interact with a database. It gives an overview of the purpose of the database along with the data that makes up the database, how the data is organized into tables, how the tables are internally structured and how they relate to one another.

When designing a database schema consider the following steps:

- Define the purpose of your database
- Find the information that make up the database
- Organize your information into tables
- Structure your tables into columns of information
- Avoid redundant data that leads to inaccuracy and waste in space
- Identify the relationships between your tables and implement them

The last two items ensure data accuracy and integrity anytime you need to add or update information in the database. It also makes querying the database much more efficient.

You can design database schemas by hand or by software. Here are a few examples of free online database design tools:

- [DbDiagram.io](http://dbdiagram.io/) - a free, simple tool to draw ER diagrams by just writing code, designed for developers and data analysts.
- [SQLDBM](http://sqldbm.com/home) - SQL Database Modeler
- [DB Designer](http://dbdesigner.net/) - online database schema design and modeling tool

Different database tools illustrate table relationships with different symbols.

Your database schema should contain the following:

- table names
- column names per table
- column types per table
- constraints per table, if any
- relationships between tables, if any

#### Creating Your Tables
A database table is made up of columns of information. Each column is assigned a name and data type.

To create a table in PostgreSQL, we would use the following SQL syntax:

```postgresql
CREATE TABLE person (
  first_name varchar(15),
  last_name varchar(15),
  age integer,
  ssn char(9)
);
```

Here is a summary of common data types, what they represent, their sample values and how they display on Postgres:

Data Type | Representation | Value | Display
--- | --- | --- | ---
integer | whole number | 617 | 617
decimal | floating-point number| 26.17345 | 26.17345
money | fixed floating-point number with 2 decimal places | 6.17 | $6.17
boolean | logic | TRUE, FALSE | t, f
char(n) | fixed-length string removes trailing blanks | ‘123 ‘ | ‘123’
varchar(n) | variable-length string | ‘123 ‘ | ‘123 ‘
text | unlimited-length string | ‘123 ‘ | ‘123 ‘

#### Querying Your Tables
To insert data into a PostgreSQL table, use this syntax:

```postgresql
INSERT INTO table_name VALUES (
  column_one_value,
  column_two_value,
  column_N_value
);
```

In order to have a useful schema, we need to prevent a database table from storing inaccurate data and returning multiple rows when we expect only one. We do this by constraining the table with the help of a primary key assigned to one or more columns. This will ensure that the column or combination of columns contains only unique values.


### What Are Database Keys?

#### Introduction
A database key is a column or group of columns in a table that uniquely identifies a row in a table.

Keys enable a database designer to place constraints on the data in a table. We want to enforce data integrity in our tables so that we avoid duplicity of information and strictly maintain relationships between tables. For example, a primary key will ensure that each row in a table is unique.

There are many types of keys: Super, Candidate, Primary, Foreign, Composite, and Secondary.

#### Primary Key
A primary key is a designation that applies to a column or multiple columns of a table that uniquely identifies each row in the table.

Designating a primary key on a particular column in a table ensures that this column data is always unique and not null.

To designate a primary key in a table, type the `PRIMARY KEY` keyword in all caps next to the selected column when creating a table.

```postgresql
CREATE TABLE recipe (
  id integer PRIMARY KEY,
  name varchar(20)
);
```

#### Key Validation
In this lesson, you will learn how to validate the keys that you have designated to specific column(s) in a database table. There are several ways to do so, however, we will focus on utilizing the information schema database that comes with PostgreSQL.

##### Information Schema
As part of an international SQL standard, the [information schema](https://www.postgresql.org/docs/9.1/information-schema.html) is a database containing meta information about objects in the database including tables, columns and constraints. This schema provides users with read-only views of many topics of interest.

For example, to determine if a column has been designated correctly as a primary key, we can query a special view, `key_column_usage`, generated from this database. This view identifies all columns in the current database that are restricted by some constraint such as primary key or foreign key.

Suppose you would like to find out the constraints that have been placed on certain columns in a table, such as `recipe`, you would type the following query.

```postgresql
SELECT
  constraint_name, table_name, column_name
FROM
  information_schema.key_column_usage
WHERE
  table_name = 'recipe';
```

This should display the following output:

```
 constraint_name | table_name | column_name 
-----------------+------------+-------------
 recipe_pkey     | recipe     | id
(1 row)
```

The `constraint_name` value, such as `recipe_pkey`, is generated by default to begin with a table name followed by the type of constraint. `pkey` refers to a primary key constraint, while `fkey` refers to a foreign key constraint.

#### Composite Primary Key
Sometimes, none of the columns in a table can uniquely identify a record. When this happens, we can designate multiple columns in a table to serve as the primary key, also known as a composite primary key. For example, we have a table, `popular_books` that contains the most popular books previewed and/or sold in a particular week.

`popular_books` will have these columns:

- book_title,
- author_name,
- number_sold
- number_previewed

Since an author can have many books and a book can have many authors, there could be repeated listings of a particular book or author in the table.

For example, a listing of `popular_books` sorted by book title may show the following:

```
  book_title      | author_name | number_sold | number_previewed 
----------------------+-------------+-------------+------------------
 Postgres Made Easy   | Liz Key     |          33 |               50
 Postgres Made Easy   | Tom Index   |          33 |               50
 Beginner Postgres    | Tom Index   |          55 |               75
 Postgres for Dummies | Liz Key     |          25 |               33
```

As we see from above, neither `book_title` nor `author_name` can be a unique column. A composite primary key, however, can be derived from the combination of both `book_title` and `author_name` that would make a row unique.

To designate multiple columns as a composite primary key, use this syntax:

```postgresql
PRIMARY KEY (column_one, column_two)
```

For example, if we were to designate both `recipe_id` and `ingredient_id` as the composite primary key for the `popular_recipes` table, we would write the `CREATE TABLE` statement for `popular_recipes` as follows.

```postgresql
CREATE TABLE popular_recipes (
  recipe_id varchar(20),
  ingredient_id varchar(20),
  downloaded integer,
  PRIMARY KEY (recipe_id, ingredient_id)
);
```

#### Foreign Key Part 1
When we have a situation where one table is related to another table in a database, we may want to bind those tables back together in a query. For example, let’s say we have a `person` table and an `email` table. If we want a list of names and associated emails, we would need to join these tables together.

To maintain data integrity and ensure that we can join tables together correctly, we can use another type of key called a foreign key. A foreign key is a key that references a column in another table.

Where do we place this foreign key? Should it be in the `person` table or `email` table? To answer this question, we need to figure out how `person` is related to `email`. Does creating a `person` record require that an `email` record exists as well? This is not usually the case. A person can have no email address or one or more email addresses. So when creating a record in the `person` table, we don’t insist that this person should have a record in the `email` table as well.

Does creating an `email` record require that a valid `person` record exists? This is usually the case, since we shouldn’t create an email address for a non-existent person. Hence, we should place the foreign key in the `email` table to ensure that a valid record in the `person` table must pre-exist before adding a record in the `email` table.

To designate a foreign key on a single column in PostgreSQL, we use the `REFERENCES` keyword:

```postgresql
CREATE TABLE person (
  id integer PRIMARY KEY,
  name varchar(20),
  age integer
);
 
CREATE TABLE email (
  email varchar(20) PRIMARY KEY,
  person_id integer REFERENCES person(id),
  storage integer,
  price money
);
```

#### Foreign Key Part 2
Now that you have related two tables together via a foreign key, you have ensured that you can correctly join the tables back together in a query.

For example, suppose that we want to join the `person` and `email` tables.

We could use the following query to return a table of names and associated emails:

```postgresql
SELECT person.name AS name, email.email AS email
FROM person, email
WHERE person.id = email.person_id;
```


### What Are Database Relationships?

#### Introduction
A database relationship establishes the way in which connected tables are dependent on one another.

There are three types: one-to-one, one-to-many and many-to-many.

#### One-to-One Relationship
In a one-to-one relationship, a row of table A is associated with exactly one row of table B and vice-versa. For example, a person may only have one passport assigned to them. Conversely, a passport may only be issued to one person.

Let’s say we have a `driver` table with the following columns:

- `name`
- `address`
- `date_of_birth`
- `license_id`

We also have a `license` table with the following columns:

- `id`
- `state_issued`
- `date_issued`
- `date_expired`

In the `driver` table, the primary key that uniquely identifies a driver would be the `license_id`. Similarly, the primary key that uniquely identifies a driver’s license in the `license` table would be the `id` itself. To establish a one-to-one relationship in PostgreSQL between these two tables, we need to designate a foreign key in one of the tables. We can pick the `license_id` from `driver` to be the foreign key in the `license` table. However, doing this is not enough to ensure that duplicate rows will not exist in the `license` table.

To enforce a strictly one-to-one relationship in PostgreSQL, we need another keyword, `UNIQUE`. By appending this keyword to the declaration of the foreign key, we should be all set.

```postgresql
license_id char(20) REFERENCES driver(license_id) UNIQUE
```

#### One-to-Many Relationship
As opposed to one-to-one, a one-to-many relationship cannot be represented in a single table. Why? Because there will be multiple rows that need to exist for a primary key and this will result in redundant data that breaks the constraint placed upon a primary key.

To resolve this, we need to represent a one-to-many relationship with two tables - a parent and a child table. Analogous to a parent-child relationship where a parent can have multiple children, a parent table will house a primary key and the child table will house both primary and foreign keys. The foreign key binds the child table to the parent table.

#### Many-to-Many Relationship Part 1
Consider the following examples of many to many relationships:

- A student can take many courses while a course can have enrollments from many students.
- A recipe can have many ingredients while an ingredient can belong to many different recipes.
- A customer can patronize many banks while a bank can service many different customers.

In each of the above examples, we see that a many-to-many relationship can be broken into two one-to-many relationships.

To implement a many-to-many relationship in a relational database, we would create a third cross-reference table also known as a join table. It will have these two constraints:

- foreign keys referencing the primary keys of the two member tables.
- a composite primary key made up of the two foreign keys.

Let’s say a `recipe` table has the following columns:

- `id` (primary key)
- `name`
- `serving_size`
- `preparation_time`
- `cook_time`

An `ingredient` table has the following columns:

- `id` (primary key)
- `name`
- `amount`

A third cross-reference table, `recipes_ingredients`, will support the following columns:

- `recipe_id` (foreign key referencing `recipe` table’s `id`)(primary key)
- `ingredient_id` (foreign key referencing `ingredient` table’s `id`) (primary key)

Both `recipe_id` and `ingredient_id` also serve as a composite primary key for `recipes_ingredients`.
 

# How Do I Make Sure My Database Stays Intact?
## Constraints
### PostgreSQL Constraints

#### Introduction
PostgreSQL offers methods to safeguard a database and maintain _data integrity_. One of these methods is called _constraints_. Constraints are rules defined as part of the data model to control what values are allowed in specific columns and tables.

Specifically, constraints:

- Reject inserts or updates containing values that shouldn’t be inserted into a database table, which can help with preserving data integrity and quality.
- Raise an error when they’re violated, which can help with debugging applications that write to the DB.

#### PostgreSQL Data Types
PostgreSQL offers several ways a DB engineer can ensure that correct data is entered into a column or table. One of the most basic methods is built into the `CREATE TABLE` syntax that you’ve probably already seen before.

In a `CREATE TABLE` statement we specify the _data type_ for each column of a table (e.g., `int`, `text`, `timestamp`, etc.). In doing so, we’re telling PostgreSQL which types of values can be inserted into each column in the table. You can refer to the complete list of available data types in the [PostgreSQL documentation](https://www.postgresql.org/docs/10/datatype.html).

|Name|Description|
|---|---|
|boolean|true/false|
|varchar or varchar(n)|text with variable length, up to n characters (if specified)|
|date|calendar date|
|integer|whole number value between -2147483648 and +2147483647|
|numeric(a, b)|decimal with total digits (a) and digits after the decimal point (b)|
|time|time of day (no time zone)|

To create a table that stores information about volunteers for the conference we could write the following:

```postgresql
CREATE TABLE volunteers (
    id integer,
    name varchar,
    hours_available integer,
    phone_number varchar(12),
    email varchar
);
```

However, data types don’t prevent all unexpected data from being inserted into a table. For example, we’ve defined `phone_number` as `varchar(12)` and might expect a 10-digit phone number formatted as `XXX-XXX-XXXX`. Consider the following issues that may arise:

- An incomplete value formatted like `XXX-XXXX` will be accepted because it’s under 12 characters.
- A value like `+X XXX-XXX-XXXX` will cause PostgreSQL to raise an error because it’s longer than 12 characters, even though it’s a valid entry.

Another potential issue caused by relying only on PostgreSQL data types stems from the fact that PostgreSQL will try to interpret incoming data as the data type the column has been defined as. This process, called _type casting_, can have mixed results.

- If one tries to insert `1.5` into our table’s `hours_available` column, PostgreSQL will cast this value to `integer`, round the data, and insert it into the table as `2`.
- If one tries to insert `1.5` into the `email` column, PostgreSQL will insert this into the database by casting `1.5` to `'1.5'` even though `'1.5'` is not a valid email address.

#### Nullability Constraints
In some cases, we might enter data into our database without including a value for every column in each row.

Missing (`NULL`) values in certain columns might make our data much less useful.

Suppose we insert a row that doesn’t contain all desired fields into our current `talks` table. We can do this with the statement below.

```postgresql
INSERT INTO talks (id, estimated_length)
VALUES (1, 30);
```

We can query this table to see how this row looks when inserted into PostgreSQL when there are no constraints in place.

```postgresql
SELECT * FROM talks
WHERE id = 1;
```

|id|title|speaker_id|estimated_length|session_timeslot|
|---|---|---|---|---|
|1|NULL|NULL|30|NULL|

With PostgreSQL, we can choose to reject inserts and updates that don’t include data for specific columns by adding a `NOT NULL` constraint on those columns. With this constraint in place, PostgreSQL will reject the insert statement that contains incomplete data. PostgreSQL will raise an error alerting us that these rows violate the constraint and that our insert or update couldn’t be completed.

Let’s consider how we might implement this constraint on the `talks` table. If we know which columns cannot be `NULL` before creating our table, we can add a `NOT NULL` constraint following the datatype in the table’s `CREATE TABLE` statement.

```postgresql
CREATE TABLE talks (
    id integer,
    title varchar NOT NULL,
    speaker_id integer NOT NULL,
    estimated_length integer,
    session_timeslot timestamp NOT NULL
);
```

#### Improving Tables with Constraints
Sometimes we’ve planned out a data model and inserted data before realizing that our model could benefit from the addition of a constraint. In PostgreSQL, we can use `ALTER TABLE` statements to add or remove constraints from existing tables.

Let’s imagine we’ve already populated our `talks` table with some data, but we haven’t included any constraints. Suppose that:

- The column `session_timeslot` contains no `NULL` values
- The column `title` contains about 50% `NULL` values

Since we’ve already created and inserted data into our table, we probably don’t want to re-create and re-populate it from scratch. Instead, we can add a `NOT NULL` constraint to a column using an `ALTER TABLE` statement. Let’s add a `NOT NULL` constraint on `session_timeslot` with the following statement.

```postgresql
ALTER TABLE talks
ALTER COLUMN session_timeslot SET NOT NULL;
```

If we later decide we no longer need this constraint, we can drop a `NOT NULL` constraint from an existing table with the following statement:

```postgresql
ALTER TABLE talks
ALTER COLUMN session_timeslot DROP NOT NULL
```

If we’d like to add a `NOT NULL` constraint to the `title` column, we can attempt to do so using the same syntax we used to add a constraint on `session_timeslot`.

```postgresql
ALTER TABLE talks
ALTER COLUMN title SET NOT NULL;
```

However, PostgreSQL will reject the addition of the constraint and raise the following error because `NULL` values are already present in the column.

```
SQL Error [23502]: ERROR: column "title" contains null values
```

If the table we’re attempting to add a constraint on doesn’t meet the constraint, we can _backfill_ the table so that it does adhere to the constraint. _Backfilling_ is a term occasionally used in DB engineering to refer to the process of adding or updating past values. In this case, we can fill our target column’s `NULL` values with a placeholder value using the query below.

```postgresql
UPDATE talks
SET title = 'TBD'
WHERE title IS NULL;
```

With the table updated so that there are no longer any nulls in `title`, and we can now apply the `NOT NULL` constraint.

#### Introduction to Check Constraints
In some situations, we might want to establish specific rules to determine what makes a row valid. For example, In our `talks` table, we might want to ensure that the `estimated_length` column is:

- An integer
- `NOT NULL`
- Positive

The first two rules can be implemented with a data type and `NOT NULL` constraint respectively, but the third will require additional logic to enforce. We can use `CHECK` statements to implement more precise constraints on our table. A `CHECK` constraint can be written into a `CREATE TABLE` statement, or added to an existing table with `ALTER TABLE`.

To use a check constraint, we list `CHECK (...)` following the data type in a `CREATE TABLE` statement and write the condition we’d like to test for inside the parentheses.

The condition tested for inside of parentheses of a `CHECK` statement must be a SQL statement that can be **evaluated as either true or false**. These statements are similar to the statements you may be familiar with in `WHERE` clauses when filtering rows from a table.

```postgresql
ALTER TABLE talks 
ADD CHECK (estimated_length > 0);
```

We can add additional constraints on a column with multiple `ALTER TABLE` statements.

Alternatively, If we know the constraints we’d like to include as we’re creating a table, we can list following the column name and datatype in a `CREATE TABLE` statement. To implement the constraints we’ve covered in this lesson you could write `estimated_length integer NOT NULL CHECK (estimated_length > 0)` into the `CREATE TABLE` statement for `talks`.

#### Check Constraints Continued
Inside a `CHECK` statement we can use a wide array of SQL syntax to create our conditions. For example, within our check constraint we can:

- Make comparisons between columns within the table
- Use logical operators like `AND` and `OR`
- Use other SQL operators you may be familiar with (`IN`, `LIKE`)

As a general rule, any logic that you might use in a `WHERE` statement to filter individual rows from an existing table can be applied within a `CHECK`, including logic that involves multiple columns or conditions. Suppose we’d like to add a check that all entries in `talks` have an `estimated_length` between 0 and 120 minutes.

```postgresql
ALTER TABLE talks 
ADD CHECK (estimated_length > 0 AND estimated_length < 120);
```

We can also apply constraints that apply to multiple columns. For example, suppose we want to enforce the following:

1. `estimated_length` less than 120 minutes
2. year of the talk should be 2020 (we can extract this value from `session_timeslot`)

We could do this by adding separate checks on each of the columns. Alternatively, we could add a single `CHECK` constraint that checks both conditions as shown below.

```postgresql
ALTER TABLE talks
ADD CHECK (estimated_length < 120 AND date_part('year', session_timeslot) = 2020);
```

The `date_part` function in PostgreSQL just returns a portion of the date as an integer (e.g. `date_part('year' ,'2020-08-01 00:00:00'::date)` = 2020).

#### Using Unique Constraints
When designing a PostgreSQL data model, it’s a good practice to structure tables such that rows are uniquely identifiable by some combination of attributes. Structuring your tables in this way leads to a few benefits:

- The structure of your data model and the contents of individual tables are more easily interpreted.
- Queries to access information from the table can be simpler. For example, if we’d like to query our `attendees` table to find out how many tickets an attendee has reserved, having a unique identifier for each attendee allows us to get a result without any intermediate aggregation.
- Identifying and implementing a `PRIMARY KEY` is easier on tables with `UNIQUE` constraints already in place.

In our `attendees` table, suppose that we’d like to make sure that no two people submit the same email address when they register. To do so we could apply a unique constraint on `email`.

To implement this constraint we could include it in our `CREATE TABLE` statement. To identify values in a single column as unique, we specify `UNIQUE` following the column name and datatype definitions, in this case we’d write `email varchar UNIQUE` in our `CREATE TABLE` statement.

Alternatively, we can add the constraint to an existing table using the following:

```postgresql
ALTER TABLE attendees 
ADD UNIQUE (email);
```

Returning to our `talks` table, suppose we’d like to use the combination of `speaker_id` and `session_timeslot` to ensure that a speaker is never booked for multiple talks at the same time. We can do this in the `CREATE TABLE` statement by specifying the columns that need to be jointly unique in parentheses on its own line following the column names and datatype definitions. In this case, we’d add a `UNIQUE (speaker_id, session_timeslot)` on it’s own line in the `CREATE TABLE` statement.

Just as with single column unique constraints, we can also and add the constraint with an `ALTER TABLE` statement.

```postgresql
ALTER TABLE talks
ADD UNIQUE (speaker_id, session_timeslot)
```

#### Introduction to Primary Keys
Having unique constraints is useful, but an important part of building a relational data model requires defining relationships between tables. _Primary keys_ are essential to defining these relationships.

A primary key is a column (or set of columns) that **uniquely identifies a row within a database table**. A table can only have one primary key, and in order to be selected as a primary key a column (or set of columns) should:

- Uniquely identify that row in the table (like a `UNIQUE` constraint)
- Contain no null values (like a `NOT NULL` constraint)

Implementing a `PRIMARY KEY` constraint is similar to simultaneously enforcing a `UNIQUE` and `NOT NULL` constraints on a column (or set of columns). Although `UNIQUE NOT NULL` and `PRIMARY KEY` constraints function very similarly, tables are limited to one `PRIMARY KEY`, but not limited in how many columns can have both `UNIQUE` and `NOT NULL` constraints.

In addition to defining relationships between tables, primary keys also improve your data model in several other ways:

- Many joins will use the primary key from one table to join data with another table
- Primary keys can improve query performance
- Primary keys help to enforce data integrity within a table by ensuring that rows can be uniquely identified

Recall that the `attendees` table has a column named `id` that uniquely identifies attendees. We have also already restricted the `name` and `email` columns to be `NOT NULL`“. Now let’s add `id` as our table’s `PRIMARY KEY`, we can do this with an `ALTER TABLE` statement.

```postgresql
ALTER TABLE attendees
ADD PRIMARY KEY (id); 
```

Even with a primary key, there’s still good reason to use a combination of `UNIQUE` and `NOT NULL` constraints to enforce data integrity on other columns. In this case, the combination of a `UNIQUE` and `NOT NULL` constraint on `email` can be used to validate that all attendees have a value for `email` and each unique email can only be matched to one attendee.

#### Introduction To Foreign Keys
In this model, the talks in `registrations` are meant to reference the talks described in `talks`. Because of this, we’d probably want to ensure that any `talk_id` entered into `registrations` references an `id` that already appears in `talks`.

When discussing relations between tables, you may see the terms _parent table_ and _child table_ to describe two tables that are related. More specifically, values inserted into _child table_ must be validated by data that’s already present in a _parent table_.

Formally, this property that ensures data can be validated by referencing another table in the data model is called _referential integrity_. Referential integrity can be enforced by adding a `FOREIGN KEY` on the child table that references the primary key of a parent table.

If the parent table doesn’t contain the data a user is attempting to insert, PostgreSQL will reject the insert or update and throw an error.

In our example above `registrations` is a child table of `talks` because entries in `registrations` must reference the primary key from `talks`. Suppose `talks` also has a column named `id` as a primary key. Now, we can update our registrations table with a foreign key using the following statement.

```postgresql
ALTER TABLE registrations
ADD FOREIGN KEY (talk_id)
REFERENCES talks (id);
```

Alternatively, if we’re creating a table from scratch, we can include the following line in the `CREATE TABLE` statement , `FOREIGN KEY (talk_id) REFERENCES talks (id)`

Suppose we now want to enter a registration for `talk_id = 100`, which does not yet exist in the `talks` table. Trying to insert a registration for this talk yields an error because there is not a corresponding entry in `talks` to reference yet. The error below lets us know the constraint is working and provides a helpful error message that indicates we need to add an entry to `talks` before this insert will succeed.

```postgresql
INSERT INTO registrations VALUES (100, 1, '2020-08-15 9:00:00', 1);
```

```
SQL Error [23503]: ERROR: insert or update on table "registrations" violates foreign key constraint "registrations_id_fkey"
Detail: Key (talk_id)=(100) is not present in table "talks".
```

#### Foreign Keys - Cascading Changes
In the previous lesson we discussed how foreign keys enforce referential integrity by preventing updates or deletes on the parent table until the child table is updated first. An engineer can specify the strategy PostgreSQL will use to maintain referential integrity as they define their foreign key constraint.

By default, a foreign key constraint will prevent an engineer from deleting or updating a row of a parent table that is referenced by some child table. This behavior is sometimes explicitly specified in a `CREATE TABLE` statement using `REFERENCES talks (id) ON DELETE RESTRICT` or `REFERENCES talks (id) ON UPDATE RESTRICT`.

However, another strategy you may consider is adding a `CASCADE` clause. Rather than preventing changes, `CASCADE` clauses (`ON UPDATE CASCADE`, `ON DELETE CASCADE`) **cause the updates or deletes to automatically be applied to any child tables**.

For example, suppose we’d like to set up our database to automatically unregister attendees from a talk that’s been cancelled. To do this we could apply `ON DELETE CASCADE` to our foreign key constraint.

```postgresql
ALTER TABLE registrations
ADD FOREIGN KEY (talk_id)
REFERENCES talks (id) ON DELETE CASCADE
```

When we try to delete a value from `talks`, we also notice that all registrations for talk_id = 1 are removed as well. This preserves referential integrity by removing any row associated with this talk.

In effect, `ON DELETE CASCADE` runs the required deletes on the child table behind the scenes and allows the user to simply run a single command to update a data model.

#### Review
_Constraints_ are rules a DB engineer defines as part of the data model to gain more control over what values are allowed in specific columns and tables.

Specifically, Constraints:

- Reject rows containing values that shouldn’t be inserted into a database table, which can help with preserving data integrity and quality.
- Raise an error when they’re violated, which can also help with debugging applications that write to the database.

There are quite a few types of constraints:

- Data types — Are your first line of defense, these rules aren’t constraints but can help reject incorrect data from your database.
- `NOT NULL` constraints — Reject incoming rows from your table when critical information is missing from a row.
- `CHECK` constraints — Give you more control over what rules you’d like to apply to your tables. These constraints will allow you to reject a row if it fails the criteria you’ve defined.
- `UNIQUE` constraints — Help with defining unique values in a table, they also create an index which can improve query and join performance.
- `PRIMARY KEY` constraints — A column or combination of columns that uniquely identify a row and are both `NOT NULL` and `UNIQUE`. `PRIMARY KEY`s are unique to a table, and will often be used in joins between tables.
- `FOREIGN KEY` constraints — Allow you to maintain _referential integrity_ between two tables by validating the entry in one also appears in the other. Referential integrity depends on `FOREIGN KEY` constraints.
 

# How Do I Make Sure My Database Stays Fast?
## Indexes
### Introduction to Indexes

#### What is an Index?
An index is an organization of the data in a table to help with performance when searching and filtering records. A table can have zero, one, or many indexes. There are some costs when using indexes.

Say you want to see what indexes exist on your `products` table you would run the following query:

```postgresql
SELECT *
FROM pg_Indexes
WHERE tablename = 'products';
```

`pg_Indexes` is a built-in view in PostgreSQL. Different database servers have different ways to see their indexes.

#### What is the benefit of an Index?
Indexing allows you to organize your database structure in such a way that it makes finding specific records much faster. By default it divides the possible matching records in half, then half, then half, and so on until the specific match you are searching for is found. This is known as a Binary Tree, or B-Tree.

If you are familiar with logarithms, the worst-case speed for a B-Tree to find a record is log2n, where without it you would have to check every record, so the read time would be n.

In small databases this is negligible, but as the datasets get larger this becomes more significant.

#### Impact of Indexes
To get insight into how PostgreSQL breaks down your statements into runnable parts, we can investigate the query plan by adding `EXPLAIN ANALYZE` before your query. Rather than returning the results of the query, it will return information _about_ the query.

```postgresql
EXPLAIN ANALYZE SELECT *
FROM customers;
```

If you would like to learn more, PostgreSQL’s official website has a full explanation of [EXPLAIN](https://www.postgresql.org/docs/current/sql-explain.html).

If you see “Seq Scan” this means that the system is scanning every record to find the specific records you are looking for. If you see “Index” (in our examples more specifically “Bitmap Index Scan”) you know that the server is taking advantage of an index to improve the speed of your search.

The other part to take note of is the “Planning time” and “Execution time”. The planning time is the amount of time the server spends deciding the best way to solve your query, should it use an index, or do a full scan of the table(s) for instance. The execution time is the amount of time the actual query takes to run after the server has decided on a plan of attack. You need to take both of these into consideration, and when examining your own indexes these are critical to understanding how effective your indexes are.

#### How to Build an Index
In PostgreSQL, the `CREATE INDEX` keywords can be used to create an index on a column of a table. Say you wanted to create an index called `customers_user_name_idx` on the `customers` table on the `user_name` column, this is how you would do that:

```postgresql
CREATE INDEX customers_user_name_idx ON customers (user_name);
```

Keep in mind that indexes are great for searching but like everything in life, nothing comes without a cost. In the case of indexes, it comes at the cost of increased runtime for any modification to the table data impacting the `user_name` column. Another cost is the space that the index takes up.

#### Index Filtering
When you are building indexes, keep in mind that they will be used for filtering your data quickly. Queries that filter data often use `WHERE` and `ON` clauses. If an index is created on the columns referenced in these clauses, the database server will examine the index to see if it will improve the speed of the query.

Say you were asked to get the number of orders placed by each person with the last name of `'Smith'` or `'Jones'`, you could get that by running the following query.

```postgresql
SELECT
    c.first_name,
    c.last_name,
    COUNT(o.order_id) AS NumOforders
FROM customers       AS c
INNER JOIN orders    AS o    
ON o.customer_id = c.customer_id
WHERE c.last_name IN ('Smith', 'Jones')
GROUP BY c.first_name, c.last_name;
```

In this script, the `WHERE` clause is filtering the possible customers by the `last_name`. If there is an index on `customers.last_name` the database server will use this to quickly find the specific customers to examine.

Another filter in this query is the `INNER JOIN` between `orders` and `customers` on the `customer_id`. If there are indexes on these columns (one on `orders.customer_id` and another for `customers.customer_id`) they could also be searched faster using the respective indexes.

---

Don’t forget the naming convention for indexes, `<table_name>_<column>_idx`.

#### Multicolumn Indexes
What if you have two or more columns that are always associated together. Can you combine them to make a more appropriate index? Much like constraints, you can combine multiple columns together as a single index. When using multicolumn indexes, the search structure will be based on the values found in all of the columns.

For example, an index on First and Last Name might be a good idea if it is common to search by both together in your situation. Consider a table where the last names `'Smith'` and `'Johnson'` appear many times. Having another filter for the first name can help you find someone named `'Sarah Smith'` much faster.

The index is built in the specific order listed at creation, so (`last_name`, `first_name`) is different from (`first_name`, `last_name`). Keep this in mind when you are building your indexes as the order will impact the efficiency of your searches.

Say you want to find `'David'`, `'Rachel'`, and `'Margaret'` from the `first_name` column with the `last_name` of `'Smith'`. If there is an index (`last_name`, `first_name`), the server would find everyone with the last name `'Smith'` then in that much smaller group, find the specific first names you are searching for. If the index is (`first_name`, `last_name`) the server would go to each of the `first_name` records you are interested in and then search for the last name `'Smith'` within each one. In general, there isn’t a right or wrong order, it’s about what is appropriate for your setup and what you expect the index to be used for. If there is a good use for it, you could create both indexes as well! If both are present, when you run your script, the database server will determine which index to use based on your query. But remember, indexes take up space, so you shouldn’t always create every index you can think of.

For a multicolumn index you only need to list out each of the columns in the order you wish them to be used.

```postgresql
CREATE INDEX customers_last_name_first_name_idx ON customers (last_name, first_name);
```

As a note, you might hear a multicolumn index referred to by other names as well, such as Composite or Compound.

#### Drop an Index
In PostgreSQL, the `DROP INDEX` command can be used to drop an existing index.

Note that we pair the `DROP` statement with the optional `IF EXISTS` to protect from execution errors.

```postgresql
DROP INDEX IF EXISTS customers_city_idx;
```

#### Why not Index every Column?
You might be asking yourself if indexes are so wonderful and help speed searches up, why not create an index on every column? The short answer is that everything has a cost. Indexes speed up searching and filtering, however, they slow down insert, update, and delete statements.

When you insert a record into a non-indexed table the database server simply adds the record(s) onto the end of the table. However, when we add a record to a table that has an index, the index itself must be modified by the server as well. Recall that at its core, an index is an organization of the data in a table. When new data is added, the index will be reshaped to fit that new data into its organization. This means that when you write a single statement to modify the records, the server will have to modify every index that would be impacted by this change. If you are adding a large amount of data to an existing table, it may be better to drop the index, add the data, and then recreate the index rather than having to update the index on each insertion.

Keep in mind that these drawbacks are for each index you have on your table. If you have multiple indexes on a single table and you insert a record, you will need to update each index associated with the table. This can make indexes very costly.

When deleting a record that is associated with an index, it might be faster to find the record — by leveraging the index’s ability to search. However, once the record is found, removing or editing it will result in the same issue as inserting a new record. The index itself will need to be redone. Note that if you’re updating a non-indexed column, that update will be unaffected by the index. So if you are updating a non-indexed column while filtering by one with an index, an update statement can actually be faster with an index.

Another place where an index falls short of perfection is that indexes take up space. The index data structures can sometimes take up as much space as the table itself. If you have not worked with large databases before you might be thinking to yourself, “who cares, storage space is cheap nowadays”. However, databases of decent size can easily get into the gigabyte size range quickly.

This means every time your Database Administrator does a full backup, all of that information, indexes included, are copied. Also consider copying the database to a different environment for testing/development, or running your database on different servers and at different physical locations. All of that data goes across the internet and some companies pay for data usage across networks on their plans.

If you wanted to examine the size of a table `products` you would run:

```postgresql
SELECT pg_size_pretty (pg_total_relation_size('products'));
```

#### When should I add an Index?
The simple answer is when the benefits of searching outweigh the burdens of storage size and Insert/Update/Delete speed. One thing to consider is whether searching will occur often enough to make the advantages worth the time and effort.

In the real world, this often becomes a grey area and one that you might have to go back to after trying for a while. You will want to look at what a table is used for and by who. As a very rough rule of thumb, think carefully about any index on a table that gets regular Insert/Update/Delete. In contrast, a table that is fairly stable but is searched regularly might be a good candidate for an index.

The higher the percentage of a table you are returning the less useful an index becomes. If we’re only searching for 1 record in 1,000,000, an index could be incredibly useful. However, if we are searching for 900,000 out of that same 1,000,000 the advantages of an index become useless. At higher percentages, the query planner might completely ignore your index and do a full table scan, making your index only a burden on the system.

Along this same line, if you are combining filtering conditions be aware of what you will be searching on. AND statements are normally fine and the query planner will try to use an indexed field before non-indexed fields to cut down on the total number of records needed to be searched. OR on the other hand, can be very dangerous; even if you have a single non-indexed condition, if it’s in an OR, the system will still have to check every record in your table, making your index useless.

#### Review
- How to see what indexes exist on a table

```postgresql
SELECT *FROM pg_indexesWHERE tablename = '<table_name>';
```
 
- `EXPLAIN ANALYZE` can be a powerful tool to see how your queries are impacted by an index.
- How to build an index

```postgresql
CREATE INDEX <index_name> ON <table_name> (column_name);
```

- Multicolumn indexes allow for more than one column to be used in combination as an index on a table

```postgresql
CREATE INDEX <index_name> ON <table_name> (<column_name1>, <column_name2>...);
```

- You can drop an index. This might be useful to do if you are modifying a large number of records on an indexed table.

```postgresql
DROP INDEX IF EXISTS <index_name>;
```

- To see the size of a database table you can run the script

```postgresql
SELECT pg_size_pretty (pg_total_relation_size('<table_name>'));
```
   
- Some of the benefits and burdens of indexes:
    - Increase in speed of searches/filtering
    - Increase in storage space
    - Increase in runtime for Insert/Update/Delete on impacted indexes.

 
### Intermediate Indexes

#### Partial Index
Many times companies have two sets of users in their databases, internal and external users. The numbers in each category tend to be far apart from each other, for example, Wells Fargo has 70 Million customers and 258 Thousand employees. If you were trying to get information about your internal employees, searching through all 70 million records would be a waste when you are looking for a group of users making up about 0.37% of the total. Even with a good index, with this many users, you are wasting time examining far more records than you are interested in.

A potential solution to this problem would be to put the internal and external users in separate tables. Unfortunately, this opens a whole can of worms. Every time you wanted users you would need to consider both tables and when looking for both types you would have to `UNION` them together. Any changes to the tables would have to be done to both, and in all relevant references to both, doubling the effort and risk to any change. So then, what’s the solution? We can create a partial index.

A partial index allows for indexing on a subset of a table, allowing searches to be conducted on just this group of records in the table. So in our example, you would be searching an index of ~258 Thousand instead of 70+ Million.

All you have to do is create an index like you normally would with a WHERE clause added on to specify the subgroup of data your index should encompass. Let’s assume that in our example the users are stored in a `users` table and we want an index based on `user_name`. If we know that all internal employees have an `email_address` ending in `'@wellsfargo.com'`, we would write the partial index like this:

```postgresql
CREATE INDEX users_user_name_internal_idx ON users (user_name)
WHERE email_address LIKE '%@wellsfargo.com';
```

Notice that the filtering of the index does not have to be for a column that is part of your index.

#### Order By
If you are commonly ordering your data in a specific way on an indexed column, you can add this information to the index itself and PostgreSQL will store the data in your desired order. By doing this, the results that are returned to you will already be sorted. You won’t need a second step of sorting them, saving time on your query.

To specify the order of an index, you can add on the order you want your index sorted in when you create the index. Say you have a `logins` table that tracks the `user_name` and `date_time` each time a login occurs. If you wanted to check to see who has been logging in recently to use your site you could run:

```postgresql
SELECT
    user_name,
    date_time
FROM logins
WHERE date_time >= (NOW() - INTERVAL'1 month')
ORDER BY date_time DESC;
```

If you were running this query regularly you could improve the speed by creating your index like this:

```postgresql
CREATE INDEX logins_date_time_idx ON logins (date_time DESC, user_name);
```

You could also use ASC to switch the direction. If your column contains NULLs you can also specify the order they appear by adding `NULLS FIRST` or `NULLS LAST` to fit your needs. By default, PostgreSQL orders indexes by ascending order with NULLs last, so if this is the order you desire, you do not need to do anything.

Another way to think of this is that every index we have created so far has had this ordering applied to it without you even knowing the server was doing this ordering.

#### Primary Keys and Indexes
PostgreSQL automatically creates a unique index on any primary key you have in your tables. It will also do this for any column you define as having a unique constraint. A unique index, primary key, and unique constraint all reject any attempt to have two records in a table that would have the same value (multicolumns versions of these would reject any record where all the columns are equal).

As a note, the primary key index standard is to end in `_pkey` instead of `_idx` to identify it as a specific type of index. It is also the way the system names it when created automatically.

#### Clustered Index
We learned in the previous lesson that an index is an organization of the data in a table. A table can have many indexes. To expand on this, all indexes are either a clustered index or a non-clustered index. For now, let’s focus on the clustered index. A clustered index is often tied to the table’s primary key.

When a clustered index is created for a table, the data is physically organized in the table structure to allow for improved search times. You can think of the clustered index like searching a dictionary. In a dictionary, the data (words) and all their related information (definition) are physically ordered by their index (words sorted alphabetically). Just like a dictionary, you can seek your word by quickly jumping to the letter in the alphabet the word you’re looking for starts with. Then, even within that letter, you can get a good idea how deep in that subset your word will probably be (`'bat'` will be near the front of the b’s while `'burgundy'` will be near the end).

This is how the clustered index physically organizes the data in your table, reorganizing it to allow faster searches. Because it is physically organizing the data in the table, there can only be one clustered index per table.

When the system creates, alters, or refreshes a clustered index, it takes all the records in your database table that are in memory and rearranges them to match the order of your clustered index, physically altering their location in storage. Then when you go to do your searches for records based on this index, the system can use this index to find your records faster.

Something to note that PostgreSQL does differently than other systems is that it does not maintain this order automatically. When inserting data into a table with a clustered index on other systems, those systems will place the new records and altered records in their correct location in the database order in memory. PostgreSQL keeps modified records where they are and adds new records to the end, regardless of sorting. If you want to maintain the order, you must run the `CLUSTER` command again on the index when there have been changes. This will “re-cluster” the index to put all of those new records in the correct place.

Because PostgreSQL does not automatically recluster on `INSERT`, `UPDATE` and `DELETE` statements, those statements might run faster than equivalent statements using a different system. The flip side of this coin though is that after time, the more your table is modified the less useful the cluster will be on your searches. Reclustering the table has a cost, so you will need to find a balance on when to recluster your table(s). There are tools that can be used to help you identify when this would be useful, but these tools fall outside of this lesson.

To cluster your database table using an existing index (say `products_product_name_idx`) on the `products` table you would use:

```postgresql
CLUSTER products USING products_product_name_idx;
```

If you have already established what index should be clustered on you can simply tell the system which table to apply the cluster on.

```postgresql
CLUSTER products;
```

And if you want to cluster every table in your database that has an identified index to use you can simply call

```postgresql
CLUSTER;
```

#### Non-Clustered Index
You can create many indexes on a table, but only one can be a clustered index, so what about the rest? They are known as non-clustered indexes.
 
Non-clustered indexes have records of the columns they are indexing and a pointer back to the actual data in the table. If you are searching for just the records in the non-clustered index, the system will simply seek for your query results and return them. When you search on a non-clustered index for more information than is in the indexed columns, there are two searches. The first to find the record in the index and another to find the record the pointer identifies. There are some things you can do, such as creating a multicolumn index, that in some cases can help cut down or eliminate the need for the look back to the main table in memory.

Previously we compared how a clustered index functions as a dictionary. You can think of all other indexes (non-clustered) more akin to an index in a book. The keywords you are looking for are organized (by type, alphabetically, by the number of appearances, etc) and can be found quickly. However, the index doesn’t contain information beyond that. Instead, it contains a pointer (page number, paragraph number, etc) to where the rest of the data can be found. This is the same way non-clustered indexes in databases work. You have a key that is sorted and a pointer to where to find the rest of the data if needed.

The main take away is that a clustered index contains all the information in your table and physically reorganizes the way it is stored in memory. A non-clustered index creates a key on the columns you indicate and a pointer back to the main table for any columns not part of the index.

---

PostgreSQL defaults all indexes to non-clustered unless you specify one to be clustered. So you do not need to do anything special when creating your index for it to be non-clustered.

#### Index-Only Scans
The lookup that a non-clustered index does back to the table after finding records has a cost. If referencing a small number of records this cost is negligible, however, it can add up if many records are needed. If all columns being used in a query are part of an index then no secondary lookup is done. Let’s examine the following multicolumn index.

```postgresql
CREATE INDEX customers_idx ON customers (last_name, first_name);
```

This will improve the speed when searching for customers by `last_name` and `first_name`. What happens when we frequently want to know the customers `email_address` as well? For each record found, it will use the index to find a pointer then look up the `email_address` matched to that record found in the index to return the `last_name`, `first_name`, and `email_address`. If you include the information that is regularly looked for, even if it isn’t used in the filtering, as part of the index, a secondary search can be avoided. So in this example, you could add `email_address` as another column in the index to prevent the lookup step. Remember the order the columns are in when creating the index should be whatever is most useful for your particular situation for searches and filtering.

#### Combining Indexes
Previously, we went over multicolumn indexes as a way PostrgeSQL can speed searches on multicolumn filtering, but if you don’t have an appropriate single index for a query, the server can combine indexes together to speed the filter.

Like anything automatically handled by a system, there are some things to keep in mind when using this convenience.

- A single multicolumn index is faster (if ordered well) than the server combining indexes.
- A multicolumn index is less efficient than a single index in cases where a single index is needed.
- You could create all of them (two single indexes and one multicolumn index), and then the server will try to use the best one in each case, but if they are all not used relatively often/equally then this is a misuse of indexes.

Take for example, searching for `first_name` and `last_name` in the `customers` table.

- If searches are most often for only one of the columns, then you should use that single index.
- If searches are most often `last_name` and `first_name`, then you should have a multicolumn index.
- If the searches are frequent and evenly spread among `first_name` alone, `last_name` alone, and the combination of the two; that is a situation where you would want to have all three indexes (two single indexes and one multicolumn index).

#### Indexes Based On Expressions
An index is not limited to just a column reference, it can use the result of a function or scalar expression computed from one or more columns.

For example, if you want to ensure the `company_name` in a `manufactures` table is unique, you can add the `UNIQUE` option to make a unique index constraint on the results on your index. Any duplicate will then be rejected. Using `UNIQUE` here tells the system that your index also needs to be a constraint and only allow one record in the system that matches the criteria for your index. In other words, by creating an index with `UNIQUE` the system will automatically create the constraint to match the logic in the index at the same time. Just like the creation of a constraint, if you try to create an index in this way where the data already in the table does not pass, the system will reject your creation and notify you of the issue.

Let’s look at our `UNIQUE` example a bit more. In PostgreSQL, `'ExampleCompany'` is NOT the same thing as `'examplecompany'` even though we would probably want to reject this as a duplicate. You can add a function on your index to convert all your `company_name` data to lower case by using `LOWER`. This ensures that `'ExampleCompany'` would be considered the same as `'examplecompany'`. This combination of the `UNIQUE` constraint and the use of the function `LOWER` would look like this:

```postgresql
CREATE UNIQUE INDEX unique_manufacture_company_name_idx ON manufacture(LOWER(company_name));
```

These special indexes compound the pros and cons of indexes. Because the results of the expression are stored in the index, it saves the search function from having to perform it on every row on future searches. However, every change in the table data that impacts the index means it has to do the expression again, making Inserts and Updates more expensive on these indexes than a basic index. Be especially thoughtful about when to use indexes that use functions or expressions.

#### Review
Indexes are very powerful tools and as a database engineer you have a lot of options on their implementation. With that customizability you have to be mindful not to misuse indexes. Make sure to carefully consider the indexes that you create in your database and don’t forget to review them to ensure continued benefit all around.

We covered:

- How to build a partial index

```postgresql
CREATE INDEX <index_name> ON <table_name> (<column_name>)WHERE <condition>;
```

- What a clustered index is and how to refresh one

```postgresql
CLUSTER <table_name> USING <index_name>;
```

- Indexes based on expressions

```postgresql
CREATE INDEX <index_name> ON <table_name>(<EXP>(<column_name>));
```


## Normalizing a Database
### Database Normalization with PostgreSQL

#### Introduction To Normalization
The process of restructuring a database in this way is called _normalization_. If you look up “database normalization,” you’ll see that there are formal names and definitions for different levels of restructuring; the most common are first, second, and third normal form (1NF, 2NF, 3NF). In practice, the formal vocabulary tends to be used in academic settings, and would be important to understand if you want to read a paper about how to optimize your database schema. Database engineers think about the underlying concepts of normalization on a day-to-day basis, but rarely use the technical names and definitions.

#### Duplicated Data
Let’s now examine the `college` table from exercise 1 more closely. The primary key of this table is `student_id` (a unique student identifier), and most of the columns describe characteristics of students, including their:

- name
- class year
- email
- major(s)
- advisor

This table also contains columns that do not describe students directly. For example, the columns `advisor_name`, `advisor_department`, `advisor_building`, and `advisor_email` describe further details about **advisors**; meanwhile, `major_1_credits_reqd` and `major_2_credits_reqd` describe further detail about **majors**.

When columns of a database table do not depend on (i.e., describe) the primary key, the same data may be duplicated in multiple places. For example, all students who share an advisor will have the same information listed in these four advisor-related columns.

#### Data Insertion Challenges
Let’s again consider the `college` table. In the last exercise, we saw how data duplication can complicate database modification. Unfortunately, there is another potential problem that can arise when all columns in a table do not depend on the primary key: new data cannot be inserted into the table until a primary key is known.

#### Restructuring the Advisor Columns
First, we saw that every student with the same advisor has identical information recorded in all advisor-related columns in the `college` table. One way to address this is by moving the four advisor-related columns into their own table, with only one row per unique advisor. This helps ensure every table has its own purpose or concern.

To create a new table from an existing one, we can precede any query with `CREATE TABLE new_table_name AS`. For example, the following code selects the unique values of `major_1` and `major_1_credits_reqd` from the original `college` table and inserts them into a newly created table called `majors`:

```postgresql
CREATE TABLE majors AS
SELECT distinct major_1, major_1_credits_reqd
FROM college;
```

We can also delete columns from our original table once we have moved them. For example, the following code drops the columns `major_1` and `major_1_credits_reqd` from the college table:

```postgresql
ALTER TABLE college
DROP COLUMN major_1, 
DROP COLUMN major_1_credits_reqd;
```

---

Note that we need to keep `advisor_email` (or some sort of advisor identifier) in the `college` table to ensure that we can still match advisors to students.

#### Restructuring the Major Columns
We saw in the previous exercises that there are two potential issues with the four major-related columns in the `college` table:

1. The two `_credits_reqd` columns describe the majors themselves, rather than the students, creating duplication
2. The repeating sets of columns make it challenging to search and sort our data by major.

To address these problems, we can extract the four major-related columns to create two new tables:

- A `majors` table listing each unique major and the number of credits required
- A cross-reference table that matches students with majors. Note that we need two additional tables (as opposed to one) because the relationship between students and majors is many-to-many (multiple students can have the same major and each student can have multiple majors), while each major has only one value of `credits_reqd`.

#### Creating Versus Modifying a Database Schema
In the last few exercises, we used columns in an existing database table (with data already inserted) to create three new tables, then dropped the redundant information from our original table. While this kind of table and schema modification can (and does) happen, it is much easier (and often preferable) to implement a schema design before data has been inserted into a database. This is because existing data might already violate constraints that we would like to impose under a new structure.

#### Database Structure and Use
While it often makes sense to break up large tables in this way, there are no universal rules about the best way to design a database schema. Sometimes, the most important design consideration is how a database will be used in the future. For example, if a particular column of data is never going to be modified, then data duplication in that column is less problematic.

---

In the last exercise, we saw how the normalized four-table database schema solved some important problems, but it’s worth noting that normalization does not exclusively make queries and modification easier. When we split a large database table into multiple smaller tables, some queries may actually become more complex. This generally happens when a particular question about the data now requires two or more tables to be joined back together. Usually, this added complexity is worth it in order to maintain simple database structure and data integrity via constraints, but it’s useful to understand the slight trade-off.

#### Review
- Repeating groups of columns and columns that are not dependent on the primary key of a table can cause problems related to:
    - Duplicated data
    - Data modification (updates/insertions)
    - Querying
- Database normalization is a process by which database tables are modified/restructured to address these problems
- Database design can be modified after data has been entered, but it is usually easiest to design a normalized schema up front
- It is important to keep database use in mind when designing an optimal database schema
 



