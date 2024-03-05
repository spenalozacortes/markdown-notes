#sqlite
# Manipulation
## Manipulation

### Introduction to SQL
SQL, Structured Query Language, is a programming language designed to manage data stored in relational databases. SQL operates through simple, declarative statements. This keeps data accurate and secure, and helps maintain the integrity of databases, regardless of size.

### Relational Databases
A *relational database* is a database that organizes information into one or more tables. 

A *table* is a collection of data organized into rows and columns. Tables are sometimes referred to as *relations*.

A *column* is a set of data values of a particular type.

A *row* is a single record in a table.

All data stored in a relational database is of a certain data type. Some of the most common data types are:

- `INTEGER`, a positive or negative whole number
- `TEXT`, a text string
- `DATE`, the date formatted as YYYY-MM-DD
- `REAL`, a decimal value

### Statements
A *statement* is text that the database recognizes as a valid command. Statements always end in a semicolon `;`.

```sqlite
CREATE TABLE table_name (
   column_1 data_type, 
   column_2 data_type, 
   column_3 data_type
);
```

Let’s break down the components of a statement:

1. `CREATE TABLE` is a *clause*. Clauses perform specific tasks in SQL. By convention, clauses are written in capital letters. Clauses can also be referred to as commands.
2. `table_name` refers to the name of the table that the command is applied to.
3. `(column_1 data_type, column_2 data_type, column_3 data_type)` is a *parameter*. A parameter is a list of columns, data types, or values that are passed to a clause as an argument.

The structure of SQL statements vary. The number of lines used does not matter. A statement can be written all on one line, or split up across multiple lines if it makes it easier to read.

### Create
`CREATE` statements allow us to create a new table in the database. You can use the `CREATE` statement anytime you want to create a new table from scratch. 

```sqlite
CREATE TABLE celebs (
   id INTEGER, 
   name TEXT, 
   age INTEGER
);
```

### Insert
The `INSERT` statement inserts a new row into a table.

```sqlite
INSERT INTO celebs (id, name, age) 
VALUES (1, 'Justin Bieber', 22);
```

Text strings require quotes around them, while numbers don’t.

### Select
`SELECT` statements are used to fetch data from a database.

In the statement below, `SELECT` returns all data in the `name` column of the `celebs` table.

```sqlite
SELECT name FROM celebs;
```

You can also query data from all columns in a table with `SELECT`.

```sqlite
SELECT * FROM celebs;
```

`*` is a special wildcard character that we have been using. It allows you to select every column in a table without having to name each one individually.

`SELECT` statements always return a new table called the *result set*.

### Alter
The `ALTER TABLE` statement adds a new column to a table.

```sqlite
ALTER TABLE celebs 
ADD COLUMN twitter_handle TEXT;
```

`NULL` is a special value in SQL that represents missing or unknown data. Here, the rows that existed before the column was added have `NULL` (∅) values for `twitter_handle`.

### Update
The `UPDATE` statement edits a row in a table.

```sqlite
UPDATE celebs 
SET twitter_handle = '@taylorswift13' 
WHERE id = 4; 
```

### Delete
The `DELETE FROM` statement deletes one or more rows from a table.

```sqlite
DELETE FROM celebs 
WHERE twitter_handle IS NULL;
```

### Constraints
*Constraints* that add information about how a column can be used are invoked after specifying the data type for a column. They can be used to tell the database to reject inserted data that does not adhere to a certain restriction.

```sqlite
CREATE TABLE celebs (
   id INTEGER PRIMARY KEY, 
   name TEXT UNIQUE,
   date_of_birth TEXT NOT NULL,
   date_of_death TEXT DEFAULT 'Not Applicable'
);
```

`PRIMARY KEY` columns can be used to uniquely identify the row. Attempts to insert a row with an identical value to a row already in the table will result in a *constraint violation* which will not allow you to insert the new row.

`UNIQUE` columns have a different value for every row. This is similar to `PRIMARY KEY` except a table can have many different `UNIQUE` columns.

`NOT NULL` columns must have a value. Attempts to insert a row without a value for a `NOT NULL` column will result in a constraint violation and the new row will not be inserted.

`DEFAULT` columns take an additional argument that will be the assumed value for an inserted row if the new row does not specify a value for that column.

### Review
SQL is a programming language designed to manipulate and manage data stored in relational databases.

- A *relational database* is a database that organizes information into one or more tables.
- A *table* is a collection of data organized into rows and columns.

A *statement* is a string of characters that the database recognizes as a valid command.

- `CREATE TABLE` creates a new table.
- `INSERT INTO` adds a new row to a table.
- `SELECT` queries data from a table.
- `ALTER TABLE` changes an existing table.
- `UPDATE` edits a row in a table.
- `DELETE FROM` deletes rows from a table.

*Constraints* add information about how a column can be used.

## What is SQLite?

### What is SQLite?
SQLite is a database engine. It is software that allows users to interact with a relational database. In SQLite, a database is stored in a single file — a trait that distinguishes it from other database engines. This fact allows for a great deal of accessibility: copying a database is no more complicated than copying the file that stores the data, sharing a database can mean sending an email attachment.

#### Drawbacks to SQLite
SQLite’s signature portability unfortunately makes it a poor choice when many different users are updating the table at the same time (to maintain integrity of data, only one user can write to the file at a time). It also may require some more work to ensure the security of private data due to the same features that make SQLite accessible. Furthermore, SQLite does not offer the same exact functionality as many other database systems, limiting some advanced features other relational database systems offer. Lastly, SQLite does not validate data types. Where many other database software would reject data that does not conform to a table’s schema, SQLite allows users to store data of any type into any column.

SQLite creates schemas, which constrain the type of data in each column, but it does not enforce them. We could accidentally insert the wrong data types in the columns. Storing different data types in the same column is a bad habit that can lead to errors that are difficult to fix, so it’s important to be strict about your schema even though SQLite will not enforce it.

# Queries
## Queries

### Introduction
One of the core purposes of the SQL language is to retrieve information stored in a database. This is commonly referred to as querying. Queries allow us to communicate with the database by asking questions and returning a result set with data relevant to the question.

Fun fact: IBM started out SQL as SEQUEL (Structured English QUEry Language) in the 1970’s to query databases.

### Select
We can select individual columns by their names (separated by a comma):

```sqlite
SELECT column1, column2 
FROM table_name;
```

### As
`AS` is a keyword in SQL that allows you to rename a column or table using an alias. The new name can be anything you want as long as you put it inside of single quotes.

```sqlite
SELECT name AS 'Titles'
FROM movies;
```

Some important things to note:

- Although it’s not always necessary, it’s best practice to surround your aliases with single quotes.
- When using `AS`, the columns are not being renamed in the table. The aliases only appear in the result.

### Distinct
`DISTINCT` is used to return unique values in the output. It filters out all duplicate values in the specified column(s).

```sqlite
SELECT DISTINCT tools 
FROM inventory;
```

### Where
We can restrict our query results using the `WHERE` clause in order to obtain only the information we want.

```sqlite
SELECT *
FROM movies
WHERE imdb_rating > 8;
```

Comparison operators used with the WHERE clause are:

- `=` equal to
- `!=` not equal to
- `>` greater than
- `<` less than
- `>=` greater than or equal to
- `<=` less than or equal to

### Like I
`LIKE` can be a useful operator when you want to compare similar values.

How could we select all movies that start with ‘Se’ and end with ‘en’ and have exactly one character in the middle?

```sqlite
SELECT * 
FROM movies
WHERE name LIKE 'Se_en';
```

`LIKE` is a special operator used with the `WHERE` clause to search for a specific pattern in a column.

The `_` means you can substitute any individual character here without breaking the pattern.

### Like II
The percentage sign `%` is another wildcard character that can be used with `LIKE`.

This statement below filters the result set to only include movies with names that begin with the letter ‘A’:

```sqlite
SELECT * 
FROM movies
WHERE name LIKE 'A%';
```

`%` is a wildcard character that matches zero or more missing letters in the pattern.

We can also use `%` both before and after a pattern:

```sqlite
SELECT * 
FROM movies 
WHERE name LIKE '%man%';
```

`LIKE` is not case sensitive. ‘Batman’ and ‘Man of Steel’ will both appear in the result of the query above.

### Is Null
Unknown values are indicated by `NULL`.

It is not possible to test for `NULL` values with comparison operators, such as `=` and `!=`.

Instead, we will have to use these operators:

- `IS NULL`
- `IS NOT NULL`

```sqlite
SELECT name
FROM movies 
WHERE imdb_rating IS NOT NULL;
```

### Between
The `BETWEEN` operator is used in a `WHERE` clause to filter the result set within a certain range. It accepts two values that are either numbers, text or dates.

For example, this statement filters the result set to only include movies with years from 1990 up to, and *including* 1999.

```sqlite
SELECT *
FROM movies
WHERE year BETWEEN 1990 AND 1999;
```

When the values are text, `BETWEEN` filters the result set for within the alphabetical range.

In this statement, `BETWEEN` filters the result set to only include movies with names that begin with the letter ‘A’ up to, but *not including* ones that begin with ‘J’.

```sqlite
SELECT *
FROM movies
WHERE name BETWEEN 'A' AND 'J';
```

However, if a movie has a name of simply ‘J’, it would actually match. This is because `BETWEEN` goes up to the second value — up to ‘J’. So the movie named ‘J’ would be included in the result set but not ‘Jaws’.

`BETWEEN` is case-sensitive. If the condition is `BETWEEN 'a' AND 'z'`, it would only return lowercase (a-z) results and not uppercase (A-Z).

### And
Sometimes we want to *combine multiple conditions* in a `WHERE` clause to make the result set more specific and useful.

One way of doing this is to use the `AND` operator.

```sqlite
SELECT * 
FROM movies
WHERE year BETWEEN 1990 AND 1999
   AND genre = 'romance';
```

With `AND`, *both* conditions must be true for the row to be included in the result.

### Or
Similar to `AND`, the `OR` operator can also be used to combine multiple conditions in `WHERE`, but there is a fundamental difference:

- `AND` operator displays a row if all the conditions are true.
- `OR` operator displays a row if any condition is true.

```sqlite
SELECT *
FROM movies
WHERE year > 2014
   OR genre = 'action';
```

With `OR`, if *any* of the conditions are true, then the row is added to the result.

### Order By
We can *sort* the results using `ORDER BY`, either alphabetically or numerically.

```sqlite
SELECT *
FROM movies
ORDER BY name;
```
 
Sometimes we want to sort things in a decreasing order.

```sqlite
SELECT *
FROM movies
WHERE imdb_rating > 8
ORDER BY year DESC;
```

- `DESC` is a keyword used in `ORDER BY` to sort the results in *descending* order (high to low or Z-A).
- `ASC` is a keyword used in `ORDER BY` to sort the results in ascending order (low to high or A-Z).

The column that we `ORDER BY` doesn’t even have to be one of the columns that we’re displaying.

Note: `ORDER BY` always goes after `WHERE` (if `WHERE` is present).

### Limit
`LIMIT` is a clause that lets you specify the maximum number of rows the result set will have. This saves space on our screen and makes our queries run faster.

```sqlite
SELECT *
FROM movies
LIMIT 10;
```

`LIMIT` always goes at the very end of the query. Also, it is not supported in all SQL databases.

### Case
A `CASE` statement allows us to create different outputs (usually in the `SELECT` statement). It is SQL’s way of handling if-then logic.

```sqlite
SELECT name,
 CASE
  WHEN imdb_rating > 8 THEN 'Fantastic'
  WHEN imdb_rating > 6 THEN 'Poorly Received'
  ELSE 'Avoid at All Costs'
 END
FROM movies;
```

In the result, you have to scroll right because the column name is very long. To shorten it, we can rename the column to ‘Review’ using `AS`:

```sqlite
SELECT name,
 CASE
  WHEN imdb_rating > 8 THEN 'Fantastic'
  WHEN imdb_rating > 6 THEN 'Poorly Received'
  ELSE 'Avoid at All Costs'
 END AS 'Review'
FROM movies;
```

### Review
- `SELECT` is the clause we use every time we want to query information from a database.
- `AS` renames a column or table.
- `DISTINCT` return unique values.
- `WHERE` is a popular command that lets you filter the results of the query based on conditions that you specify.
- `LIKE` and `BETWEEN` are special operators.
- `AND` and `OR` combines multiple conditions.
- `ORDER BY` sorts the result.
- `LIMIT` specifies the maximum number of rows that the query will return.
- `CASE` creates different outputs.

# Aggregate Functions
## Aggregate Functions

### Introduction
We’ve learned how to write queries to retrieve information from the database. Now, we are going to learn how to perform calculations using SQL.

Calculations performed on multiple rows of a table are called *aggregates*.

- `COUNT()`: count the number of rows
- `SUM()`: the sum of the values in a column
- `MAX()`/`MIN()`: the largest/smallest value
- `AVG()`: the average of the values in a column
- `ROUND()`: round the values in the column

### Count
The fastest way to calculate how many rows are in a table is to use the `COUNT()` function.

`COUNT()` is a function that takes the name of a column as an argument and counts the number of non-empty values in that column.

```sqlite
SELECT COUNT(*)
FROM table_name;
```

### Sum
`SUM()` is a function that takes the name of a column as an argument and returns the sum of all the values in that column.

```sqlite
SELECT SUM(downloads)
FROM fake_apps;
```

### Max / Min
The `MAX()` and `MIN()` functions return the highest and lowest values in a column, respectively.

```sqlite
SELECT MAX(downloads)
FROM fake_apps;
```

### Average
SQL uses the `AVG()` function to quickly calculate the average value of a particular column.

```sqlite
SELECT AVG(downloads)
FROM fake_apps;
```

### Round
`ROUND()` function takes two arguments inside the parenthesis:

- a column name
- an integer

It rounds the values in the column to the number of decimal places specified by the integer.

```sqlite
SELECT ROUND(price, 0)
FROM fake_apps;
```

SQL rounds the values in the column to 0 decimal places in the output.

### Group By I
Oftentimes, we will want to calculate an aggregate for data with certain characteristics.

For instance, we might want to know the mean IMDb ratings for all movies each year. We could calculate each number by a series of queries with different `WHERE` statements, like so:

```sqlite
SELECT AVG(imdb_rating)
FROM movies
WHERE year = 1999;
 
SELECT AVG(imdb_rating)
FROM movies
WHERE year = 2000;
 
SELECT AVG(imdb_rating)
FROM movies
WHERE year = 2001;
```

We can use `GROUP BY` to do this in a single step:

```sqlite
SELECT year,
   AVG(imdb_rating)
FROM movies
GROUP BY year
ORDER BY year;
```

`GROUP BY` is a clause in SQL that is used with aggregate functions. It is used in collaboration with the `SELECT` statement to arrange identical data into *groups*.

The `GROUP BY` statement comes after any `WHERE` statements, but before `ORDER BY` or `LIMIT`.

### Group By II
Sometimes, we want to `GROUP BY` a calculation done on a column.

For instance, we might want to know how many movies have IMDb ratings that round to 1, 2, 3, 4, 5.

```sqlite
SELECT ROUND(imdb_rating),
   COUNT(name)
FROM movies
GROUP BY ROUND(imdb_rating)
ORDER BY ROUND(imdb_rating);
```

SQL lets us use column reference(s) in our `GROUP BY` that will make our lives easier.

- `1` is the first column selected
- `2` is the second column selected
- `3` is the third column selected

and so on.

```sqlite
SELECT ROUND(imdb_rating),
   COUNT(name)
FROM movies
GROUP BY 1
ORDER BY 1;
```

### Having
In addition to being able to group data using `GROUP BY`, SQL also allows you to filter which groups to include and which to exclude.

For instance, imagine that we want to see how many movies of different genres were produced each year, but we only care about years and genres with at least 10 movies.

We can’t use `WHERE` here because we don’t want to filter the rows; we want to *filter groups*.

`HAVING` is very similar to `WHERE`. In fact, all types of `WHERE` clauses you learned about thus far can be used with `HAVING`.

```sqlite
SELECT year,
   genre,
   COUNT(name)
FROM movies
GROUP BY 1, 2
HAVING COUNT(name) > 10;
```

`HAVING` statement always comes after `GROUP BY`, but before `ORDER BY` and `LIMIT`.

### Review
- `COUNT()`: count the number of rows
- `SUM()`: the sum of the values in a column
- `MAX()`/`MIN()`: the largest/smallest value
- `AVG()`: the average of the values in a column
- `ROUND()`: round the values in the column

Aggregate functions combine multiple rows together to form a single value of more meaningful information.

- `GROUP BY` is a clause used with aggregate functions to combine data from one or more columns.
- `HAVING` limit the results of a query based on an aggregate property.


SQLite comes with a `strftime()` function - a very powerful function that allows you to return a formatted date.

It takes two arguments: `strftime(format, column)`


# Multiple Tables
## Multiple Tables

### Introduction
In order to efficiently store data, we often spread related information across multiple tables.

### Combining Tables with SQL
Combining tables manually is time-consuming. Luckily, SQL gives us an easy sequence for this: it’s called a `JOIN`.

```sqlite
SELECT *
FROM orders
JOIN customers
  ON orders.customer_id = customers.customer_id;
```

Because column names are often repeated across multiple tables, we use the syntax `table_name.column_name` to be sure that our requests for columns are unambiguous.

```sqlite
SELECT orders.order_id,
   customers.customer_name
FROM orders
JOIN customers
  ON orders.customer_id = customers.customer_id;
```

### Inner Joins
When we perform a simple `JOIN` (often called an *inner join*) our result only includes rows that match our `ON` condition.

### Left Joins
What if we want to combine two tables and keep some of the un-matched rows?

SQL lets us do this through a command called `LEFT JOIN`. A *left join* will keep all rows from the first table, regardless of whether there is a matching row in the second table.

```sqlite
SELECT *
FROM table1
LEFT JOIN table2
  ON table1.c2 = table2.c2;
```

### Primary Key vs Foreign Key
Let’s return to our example of the magazine subscriptions. Recall that we had three tables: orders, subscriptions, and customers.

Each of these tables has a column that uniquely identifies each row of that table:

- `order_id` for orders
- `subscription_id` for subscriptions
- `customer_id` for customers

These special columns are called *primary keys*.

Primary keys have a few requirements:

- None of the values can be `NULL`.
- Each value must be unique (i.e., you can’t have two customers with the same `customer_id` in the customers table).
- A table can not have more than one primary key column.

When the primary key for one table appears in a different table, it is called a *foreign key*.

Generally, the primary key will just be called `id`. Foreign keys will have more descriptive names.

The most common types of joins will be joining a foreign key from one table with the primary key from another table. 

### Cross Join
So far, we’ve focused on matching rows that have some information in common.

Sometimes, we just want to combine all rows of one table with all rows of another table.

```sqlite
SELECT shirts.shirt_color,
   pants.pants_color
FROM shirts
CROSS JOIN pants;
```

Notice that cross joins don’t require an `ON` statement.

A more common usage of `CROSS JOIN` is when we need to compare each row of a table to a list of values.

### Union
Sometimes we just want to stack one dataset on top of the other. Well, the `UNION` operator allows us to do that.

Suppose we have two tables and they have the same columns.

table1:

pokemon | type
--- | ---
Bulbasaur| Grass
Charmander | Fire
Squirtle | Water

table2:

pokemon | type
--- | ---
Snorlax | Normal

```sqlite
SELECT *
FROM table1
UNION
SELECT *
FROM table2;
```

The result would be:
pokemon | type
--- | ---
Bulbasaur | Grass
Charmander | Fire
Squirtle | Water
Snorlax | Normal

SQL has strict rules for appending data:

- Tables must have the same number of columns.
- The columns must have the same data types in the same order as the first table.

### With
Often times, we want to combine two tables, but one of the tables is the result of another calculation.

```sqlite
WITH previous_results AS (
   SELECT ...
   ...
   ...
   ...
)
SELECT *
FROM previous_results
JOIN customers
  ON _____ = _____;
```

The `WITH` statement allows us to perform a separate query (such as aggregating customer’s subscriptions).

`previous_results` is the alias that we will use to reference any columns from the query inside of the `WITH` clause.

We can then go on to do whatever we want with this temporary table (such as join the temporary table with another table).

Essentially, we are putting a whole first query inside the parentheses `()` and giving it a name. After that, we can use this name as if it’s a table and write a new query using the first query.

### Review
- `JOIN` will combine rows from different tables if the join condition is true.
- `LEFT JOIN` will return every row in the *left* table, and if the join condition is not met, `NULL` values are used to fill in the columns from the *right* table.
- *Primary key* is a column that serves a unique identifier for the rows in the table.
- *Foreign key* is a column that contains the primary key to another table.
- `CROSS JOIN` lets us combine all rows of one table with all rows of another table.
- `UNION` stacks one dataset on top of another.
- `WITH` allows us to define one or more temporary tables that can be used in the final query.
