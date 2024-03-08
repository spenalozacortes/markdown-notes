# How Do I Make Sure My Database Stays Intact?

## PostgreSQL Roles: Database Security

### Introduction to Database Permissions
When you create a new PostgreSQL database server there will be a single database and a single user (both usually named `postgres`) available. In PostgreSQL, you can run the following command to check the name of the current user:

```postgresql
SELECT current_user;
```

The `postgres` user (or any initial user) has the ability to create new databases, tables, users, etc. In PostgreSQL, the term for a user with these types of permissions is `superuser`. A `superuser` bypasses all permission checks that other users face before being allowed to perform an action.

`superuser` privileges are not restricted to a single user. In fact, the `superuser` designation can be passed along to any number of other users in the DB. However, the `superuser` designation is a dangerous privilege and should be used sparingly. In computing, there is a rule called the principle of least privilege that suggests all applications and users should have only the minimum permissions required for their function.

To adhere to this principle in PostgreSQL, you’d want to ensure that:

- Most user’s privileges are restricted
- `superuser`s are not performing routine database tasks
- Specialized roles are created with only the permissions they require

### Investigating Superuser Permissions
As a superuser you may want to check the permissions of users in your database to ensure that they have access to only what they need. The following tables and columns are particularly useful for understanding the state of any user’s permissions:

- `pg_catalog.pg_roles` — a listing of all users in the database and a description of what special permissions these users have.

|Column Name|Description|
|---|---|
|usename|role name|
|usecreatedb|Does the user have `CREATEDB` privileges?|
|usesuper|Does the user have `SUPERUSER` privileges?|

- `information_schema.table_privileges` — description of the permissions a user (`grantee`) has on a table. This table can be used to answer questions about who can `SELECT`, `INSERT`, `UPDATE`, etc. values on a table.

```postgresql
SELECT grantor, grantee, table_schema, table_name, privilege_type
FROM information_schema.table_privileges 
WHERE grantee = 'userB';
```

|grantor|grantee|table_schema|table_name|privilege_type|
|---|---|---|---|---|
|userA|userB|finance|sales|SELECT|
|userA|userB|finance|sales|UPDATE|

Each row of this response corresponds to a single permission. The name of the privilege is shown in the `privilege_type` column. The `grantor` column tells us name of the role that originally granted the privilege. Overall, this output tells us that `userB` has been given the ability to `SELECT` and `UPDATE` on a table named `finance.sales` by `userA`.

Alternatively, as a superuser, you can use `SET ROLE` to mimic the permissions of other users. For example, if a superuser runs `SET ROLE <test role>` and then attempts to perform an action that role couldn’t, they’d receive following message indicating that they don’t have permission.

```
ERROR:  permission denied for schema <schema name>
```

This behavior is identical to connecting to the database with that role from the start. As superuser, you can run `SET ROLE <superuser role>` to regain all superuser privileges.

### Creating and Modifying Database Roles
As a superuser, one of the permissions you have is the ability to create new roles. In PostgreSQL, roles can either be _login roles_ or _group roles_. Login roles are used for most routine database activity. Group roles typically do not have the ability to login themselves, but can hold other roles as “members” and allow access to certain shared permissions.

The `CREATE ROLE` statement takes a series of arguments that modify the specific parameters around the newly-created user’s permissions. You can create a new login role using `CREATE ROLE <name> WITH <list of permissions>;`

For example, to create a role with the most basic privileges you might use the following:

```postgresql
CREATE ROLE sampleusr WITH NOSUPERUSER LOGIN;
```

Some of the most commonly used permissions are described below. You can reference a full list of permissions available for `CREATE ROLE` [here](https://www.postgresql.org/docs/10/sql-createrole.html).

|Permission Name|Function|
|---|---|
|SUPERUSER|Is the role a `superuser`?|
|CREATEROLE|Is the role permitted to create additional roles?|
|CREATEDB|Is the role able to create databases?|
|LOGIN|Is the role able to login?|
|IN ROLE|List of existing roles that a role will be added  <br>to as a new member.|

Just like tables or schemas, roles can be altered. As a superuser, you can use the same syntax as `CREATE ROLE` to `ALTER` an existing role. The following statement alters a role, `miriam`, and gives them the ability to create new databases with `CREATEDB`.

```postgresql
ALTER ROLE miriam WITH CREATEDB
```

Sometimes you may see `CREATE USER` on older versions of PostgreSQL, `CREATE USER` is equivalent to `CREATE ROLE` except `CREATE USER` assumes `WITH LOGIN` while `CREATE ROLE` does not. It’s a better practice to use the more up to date syntax, `CREATE ROLE`, when using more recent PostgreSQL version.

### Modifying Permissions on Existing Schemas and Tables
In addition to being used to manage who can login and create new databases and roles, roles are also used to manage what schemas and tables users can see and modify. Every table or schema in a PostgreSQL database has an owner that can set the permissions on their tables.

As a superuser or table or schema owner, you may use `GRANT` and `REVOKE` statements to modify these permissions at the schema and table level.

To use a schema, a role must have a permission called `USAGE`. Without `USAGE` a role cannot access tables within that schema. Other schema level permissions include `CREATE` and `DROP`, which allow the grantee the ability to create or remove tables in that schema respectively.

To interact with a table, a role must have `USAGE` on the table’s schema. Additionally, a table owner must also grant `SELECT`, `UPDATE`, `DELETE`, `INSERT` etc. on a specific table to define how that role can interact with the table.

Let’s examine what this looks like in practice. As the owner of the schema `finance`, perhaps you’d like to grant the ability to `SELECT` and `UPDATE` a table named `finance.revenue` to a user named `analyst`. You could accomplish this with the following:

1. First by granting `USAGE` on the schema. In this example, `analyst` is also granted the ability to `CREATE` new tables in the schema.

```postgresql
GRANT USAGE, CREATE ON SCHEMA finance TO analyst;
```

2. Then by granting the table specific permissions.

```postgresql
GRANT SELECT, UPDATE ON finance.revenue TO analyst;
```

Notice that when granting permissions, the specific permissions can be listed successively as in the statements above.

Any `GRANT` statement can be reversed using quite similar syntax. First replacing `GRANT` with `REVOKE` and `TO` to `FROM`. For example, to revoke the ability to `UPDATE` given above, the owner of the table could use the following statement:

```postgresql
REVOKE UPDATE ON finance.revenue FROM analyst;
```

### Modifying Default Permissions
To make managing permissions easier, PostgreSQL introduced a feature called default permissions. With default permissions, a superuser can set permissions to be updated automatically when new objects are created in a schema.

Let’s work through an example. Perhaps we want to allow a role named `analyst` to be able to `SELECT` on all tables in a schema, `finance`, regardless if they’re the owner or not.

Default permissions only apply to objects created after the defaults are set, so we still need to ensure the following `GRANT` statements have given the role access to the schema and the tables that already exist in the schema.

```postgresql
GRANT USAGE ON finance TO analyst;
 
GRANT SELECT ON ALL TABLES IN finance TO analyst;
```

Without default privileges, anytime another user creates a table, that user or a superuser would need to execute `GRANT SELECT ON <table> TO analyst` before `analyst` could interact with the table. With default permissions, this process becomes much smoother. The following statement would allow `analyst` to `SELECT` on all newly-created tables in `finance` immediately after another user has created them:

```postgresql
ALTER DEFAULT PRIVILEGES IN SCHEMA finance
GRANT SELECT ON TABLES TO analyst;
```

Default permissions can be used to set permissions at the database level as well. For example, replacing `IN SCHEMA finance` with `IN DATABASE <database name>` in the query above would apply default permissions across a whole DB. In general, any permissions that could otherwise be set with a `GRANT` statement can be applied to newly created objects with `ALTER DEFAULT PRIVILEGES`.

However, There is not an equivalent to `ALTER DEFAULT PRIVILEGES` statement in all SQL databases — if you’re working on an older PostgreSQL system or with another database server you may still need to set permissions manually.

### Groups and Inheritance
In PostgreSQL, any role can be assigned to be a member of another role. For example, `alice`, `bob`, and `charlie` can each be login roles, and they can also all be members of a group role called `employees`. As members of a group role, these accounts can inherit certain permissions from `employees`. If a superuser granted `SELECT` on a table to `employees`, `alice`, `bob`, and `charlie` would also be able to `SELECT` on this table because they’re “members” of `employees`.

This is a useful feature for maintaining databases with many users, but only a few “types” of users. You could have a DB with hundreds of users, but if their permissions are managed through just a few group roles, the job of maintaining permissions is far simpler.

However, members in a group don’t necessarily all share the exact same permissions. Consider the example below, `alice` and `bob` are both members of `employees`. This grants them all the permissions granted to `employees`. `alice` (`marketing`) and `bob` (`marketing` and `sales`) are also both members of additional group roles. Because they’re members of these group roles, they also have all the permissions granted to these roles. Finally, they also have permissions granted only to their login role.

There are some “gotchas” with role inheritance that you should be aware of. For security reasons, PostgreSQL disallows the inheritance of certain powerful permissions such as `LOGIN`, `SUPERUSER`, `CREATEDB`, and `CREATEROLE`. This prevents a developer from accidentally granting high-level permissions to a wide group of users.

There are several ways to create a new group role:

- Using `CREATE ROLE` and the `WITH ROLE` option when creating a role — this automatically adds the listed names to the role.

```postgresql
CREATE ROLE marketing WITH NOLOGIN ROLE alice, bob;
```

- Using `CREATE ROLE` and a `GRANT` statement — this grants all the permissions of the newly created role to the listed names.

```postgresql
CREATE ROLE finance WITH NOLOGIN;
 
GRANT finance TO charlie;
```

You can also add users to group(s) on creation by specifying `IN ROLE` along with the `CREATE ROLE` statement.

```postgresql
CREATE ROLE fran WITH LOGIN IN ROLE employees, managers; 
```

### Column Level Security




## ACID properties

## SQL Injections




# How Do I Make Sure My Database Stays Fast?

## Seek vs Scan




# Normalizing a Database

## Academic Normalization




# Database Maintenance

## PostgreSQL Database Maintenance