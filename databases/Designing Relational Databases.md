# Triggers

## Database Triggers

### What is a trigger?
According to Wikipedia, “a [database trigger](https://en.wikipedia.org/wiki/Database_trigger) is procedural code that is automatically executed in response to certain events on a particular table or view in a database. The trigger is mostly used for maintaining the integrity of the information on the database.”

What that means is that when you want something to happen every time someone makes a specific change to a table or view, a trigger is placed on that table or view. That trigger will call a function when the conditions for the trigger are met.

In short, adding a trigger saves people from forgetting to do that action, and ensures consistent rules are applied.

Of course, nothing comes without a cost. Triggers have overhead and there might be times when you don’t want it to fire and you have to work around it. But if properly designed, these situations should be rare — often in very specific situations where there is a valid reason to make the exception.

### How are Triggers Activated?
Triggers are very customizable. You have control over when they get called, when they run, along with what happens when they are called. For now we will keep things simple and go with a trigger that calls a function when a table is updated.

```postgresql
CREATE TRIGGER <trigger_name>
BEFORE UPDATE ON <table_name>
FOR EACH ROW
EXECUTE PROCEDURE<function>;
```

As a note here, you may see newer versions of PostgreSQL use `EXECUTE FUNCTION` rather than `EXECUTE PROCEDURE`. These are logically equivalent and both call a trigger function.

For a specific example, say you had your own trigger function you (or someone else) created called `check_account_update()` that might be written like

```postgresql
CREATE OR REPLACE FUNCTION check_account_update() RETURNS TRIGGER AS $$
    BEGIN
        NEW.active:= 1;
        RETURN NEW;
    END;
$$ LANGUAGE PLPGSQL;
```

You could set this function as the target of your trigger like this:

```postgresql
CREATE TRIGGER check_update
    BEFORE UPDATE ON accounts
    FOR EACH ROW
    EXECUTE PROCEDURE check_account_update();
```

So in this case, no matter what your `UPDATE` statement did to the `accounts` table, the modified rows would have their `active` column set to 1 (presumably indicating true).

You are not limited to setting a trigger only on an `UPDATE`, it can be set for `UPDATE`, `INSERT`, `DELETE` and `TRUNCATE`.

### When is a Trigger Activated?
Let’s take a look at when a trigger can be activated in relation to the query that activates it. There are two common options: `BEFORE` and `AFTER`.

We have already used `BEFORE` — this calls your trigger before the query that fired the trigger runs, allowing you to apply the actions in the function previous to the query. Specifically letting you modify the row that is being modified when using an `INSERT` or `UPDATE`.

`AFTER` occurs once the query finishes its work. This allows your trigger to activate once the query it was activated by has finished its work. This will not let you modify the row that is being modified as the process has already finished. This is quite useful for logging purposes, such as inserting into an audit table to track who did a change and when.

### What Records are modified by a Trigger?
When using `FOR EACH ROW`, the trigger will fire and call the function for every row that is impacted by the related query. The other option is to have it set to `FOR EACH STATEMENT`. `FOR EACH STATEMENT` calls the function in the trigger once for each query, not for each record.

This option might seem simplistic but depending on the situation, it could have large impacts on efficiency and data integrity.

### Can I focus my Triggers?
You will be happy to find out that you can use a `WHEN` clause to filter when a trigger calls its related function.

As a note, with the `WHEN` clause, you can use `NEW` and `OLD` to get records from the table before and after the query. Logically, `INSERT` can not refer to `OLD` (nothing existed before the insert) and `DELETE` can not refer to `NEW` (nothing exists after the delete).

For example the `INSERT` triggers might look like:

```postgresql
CREATE TRIGGER insert_trigger_high
BEFORE INSERT ON clients
FOR EACH ROW
WHEN (NEW.total_spent >= 1000)
EXECUTE PROCEDURE high_spender();
```

and

```postgresql
CREATE TRIGGER insert_trigger_low
BEFORE INSERT ON clients
FOR EACH ROW
WHEN (NEW.total_spent < 1000)
EXECUTE PROCEDURE not_a_high_spender();
```

### Things to consider
in PostgreSQL, multiple triggers of the same kind can exist on the same table. If a statement causes multiple triggers to fire, they are triggered in alphabetical order.

Another point to be aware of is that in PostgreSQL, since `SELECT` statements do not modify rows, no trigger can be set on a `SELECT` statement.

Finally, let’s consider the concept that one SQL command can trigger more than one kind of trigger. For example, an `INSERT` can fire a trigger that calls a function that updates another record(s), firing an `UPDATE` trigger.

### Removing Triggers
Just like everything else in your database, triggers need to be maintained, and sometimes that means pruning obsolete triggers. You can use `DROP TRIGGER` to accomplish this.

```postgresql
DROP TRIGGER insert_trigger ON customers;
```

In addition to dropping triggers, it can be useful to know what triggers exist. To find that, you just need to look at the `information_schema.triggers` table.

```postgresql
SELECT * FROM information_schema.triggers;
```

### Review
- Triggers are associated with a specific table, view or foreign table.
- Triggers execute a specified function when certain operations are performed on the table (`INSERT`, `UPDATE`, `DELETE`, `TRUNCATE`).
- Triggers can run before, after or instead of the operation attempts to alter the row.
- A trigger set `FOR EACH ROW` is called once for every row modified.
- `FOR EACH STATEMENT` executes once for the entire operation (0 modified rows would still trigger this).
- Triggers can specify a boolean `WHEN` condition to see when they should be fired.
- Multiple triggers of the same kind can exist on the same table. If so they are triggered in alphabetical order.
- `SELECT` statements do not modify rows so no trigger can be set on a `SELECT` statement.
- One SQL command can trigger more than one kind of trigger.
- Use the `DROP TRIGGER` command to remove a trigger.
- You can query the `information_schema.triggers` table to get a list of triggers in the system.
 

# Creating an Organized Database

## Representing a Schema with Entity Relationship Diagrams

### What is a schema?
When designing a database, the most common thing seen among most teams will be a _database schema_. Database schemas are often drawn as diagrams — big pictures showing every table and how they are connected. These schemas will usually include the columns in each database and arrows showing how a table relates to another table. There are a few different ways to draw out these diagrams, but in this article, we’ll cover an Entity Relationship Diagram, which is a slightly higher level than a basic database schema.

### Why use a schema?
When working with a database, especially larger databases, it can become very difficult to track each relation within the database due to the size and scope of the database. To assist in keeping track of the database, a schema can be used to help visualize the database and all of its relations. These schemas can be as simple as just naming each table and drawing a line to each connected table.

![[Pasted image 20230620164405.png]]

### What’s an Entity Relationship Diagram?
An _Entity Relationship Diagram_, or _ERD_, is a method of diagramming a database with a little more description put into it to allow a designer to better understand the database and the relationships between the tables. This is done by using several different items within the schema. Including:

- _Entities_. Entities are usually represented as rectangles and indicate the table’s name.
- _Attributes_. Attributes can be found in one of two places, either inside of the entity’s rectangles as rows or outside of the entity represented by an oval that is connected to the entity. In both places, an attribute means the same thing and is the individual columns that will be found within that table or entity.
- _Actions_. Actions are seen as diamonds within the ERD and describe the relationships between different entities. For instance, if we have two entities, a Customer and a Credit Card that are both connected, we can put an action in between those two that says “has” to show the designer that a Customer has a Credit Card.
- _Connecting Lines_. These lines, just like in a basic schema, are used to show the connection between each entity, action, and attribute.

![[Pasted image 20230620164546.png]]

### Connecting Lines in More Detail
We can represent the _cardinality_ of entities by using symbols on the lines connecting the entities. Using these symbols, we can represent relationships such as many to many, many to one, one to one, and so forth.

The only complication that comes from cardinality is that several different styles currently exist to display these relationships, including Information Engineering Style, Chen Style, Bachman Style, and more. These different styles all still represent the same information, and can be learned about more [here](https://www.lucidchart.com/pages/er-diagrams/#section_5).

### How To Create a Schema
Some online tools to help build a schema online can be seen below.

- [dbdiagram.io](https://dbdiagram.io/home). This website helps with designing ERDs while also providing a script to help create the database.
- [dbdesigner.net](https://www.dbdesigner.net/). This online design tool allows us to create diagram schemas with simple tools while also creating a script for database creation in several different languages.
- [lucidchart.com](https://www.lucidchart.com/pages/examples/database-design-tool). This website allows us to create database schemas with the same tools used to create different charts. A large amount of freedom lets us create highly detailed database schemas while also providing an export option to several different database options.

### Other Schema Types
For example, some lower level schema types are the hierarchical model, the network model, and the relational model. Most schemas will use the relational model. If a higher level is needed than ERD we could use the star schema or the snowflake schema. These higher levels deal more with the design of the database and making it more efficient rather than trying to display more information about the schema.


## Three Tier Architecture

### What is a three tier application?
When discussing a new application or program that will be built, the number of tiers an application will need is going to likely be discussed. A _tier_ is used to help separate the different processes that will be used within an application. This can be through the use of different tech stacks or by simply dividing into separate teams for each tier.

Now that we know what a tier is, we can look at a _three tier application_. In this framework, the three tiers are the presentation tier, application tier, and data tier. These tiers will be discussed in more detail later, but for now, we just need to understand that these tiers can run on their own infrastructure. This allows for easier scalability when expanding the application.

### The Presentation Tier
This tier is the one most people will be familiar with as it represents items such as the user interface or GUI. It represents how the user will interact with the application.

This tier consists mostly of markup languages including HTML, JavaScript, and CSS. This is because this tier is mainly for presenting and gathering information from the user, and less about processing the data in this tier.

### The Data Tier
This is the tier that stores all of the data. Data at this level is not manipulated and is strictly for storage. This is usually just a database to store the data on. The data tier can only interact with the application tier, and is unable to communicate directly to the presentation tier. This is because of the fact that the data tier is strictly for storage and not manipulation.

The data tier of applications is usually a database, meaning that services like SQL, MongoDB, and PostgreSQL are used to create the database and assist with querying later. However, any querying done to the database is not considered to be a part of the data tier and is instead a part of the application tier.

### The Application Tier
This is where the bulk of the application will go. This tier will deal with processing data gathered from the presentation tier and modifies the data within the data tier. It acts like a bridge connecting the two other tiers.

Most of the work performed inside of the application tier will be done in programming languages such as Java, Python, Perl, and other popular programming languages. This is because they are best at manipulating the data into a number of different forms.

### Why use tiered architecture?
Tiered architecture is beneficial in development for a number of reasons. The biggest being the added assistance in designing and development and the ease of scaling up programs as use grows over time. The added assistance with designing and development makes it easier to create separate teams to focus on individual parts of the project. A project can be split into a number of teams each focusing on a different tier within the application.

This also assists with scaling for when the project starts to gather larger users. These layers are typically on their own tech stacks, meaning that when it comes time to upgrade a server, change the user interface, or modify how data is handled, it can all be modified without having to make too many changes to the other tiers.

### Other tiered architectures
A three tiered architecture is not the only choice when it comes to deciding the number of tiers inside of an application. Two tiered architecture exists within the development world and contains only a presentation tier and a data tier. This means data is directly displayed to the user, and also means that the logic and data manipulation is limited. This means that two tiered applications are usually very simple in their operations.

Applications can also contain more than three tiers as well. In fact, an application can contain as many tiers as necessary and is usually referenced as an _n tier application_ due to the fact that there is no true limit to the number of tiers an application can contain. As more tiers are added though, it can become harder to maintain the project and can even slow it down due to all of the tiers the project has to manage.

### Conclusion
A three tiered application is a nice middle ground for building a project. It allows for complex applications without slowing down the application. Through the use of a presentation tier, application tier, and data tier, full projects can be built and managed with different teams. The different tiers also help allow for improved scalability for when an application grows and is easier to manage than higher tiered application.
 
