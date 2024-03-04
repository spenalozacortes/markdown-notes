#bash #postgresql 
# Learn Bash by Building a Boilerplate
Type `pwd` into the terminal and press enter to see the path of the folder. `pwd` stands for "print working directory". The output tells you where the folder you are in is located.

Type `ls` into the terminal to see what's in this folder. `ls` stands for "list". The output is showing everything in this folder.

You can use `cd <folder_name>` to go into a folder. `cd` stands for "change directory".

You can use `cd ..` to go back a folder level. The two dots will take you back one level. 

You can see what's in a file with `more <filename>`.

You can empty the terminal with `clear`.

You can add a **flag** to a command to use it different ways like this: `ls <flag>`. List the contents of the folder in "long list format". Do that by adding the `-l` flag to the "list" command. It is showing more details about each item in here and it's a little easier to read. 

You can go back two folders with `cd ../...` Each set of dots represents another folder level.

You can make a new folder with `mkdir <folder_name>`. `mkdir` stands for "make directory".

The `echo` command lets you print anything to the terminal. Just type what you want to print after it. 

You can use `touch <filename>` to create a new file. 

Most commands have a `--help` flag to show what the command can do.

The flag you are looking for is `--all`, or `-a` for short. List **all** the contents of the folder using the correct flag.

The `.` takes you to the folder you are in, and `..` takes you back, or up, a folder.

You can copy a file with `cp <file> <destination>`. `cp` stands for "copy".

You can remove a file with `rm <filename>`.

You can rename them with `mv` like this: `mv <filename> <new_filename>`. `mv` stands for "move", it can **rename or move** something.

You can use `find` to find things or view a file tree. You can use `find <folder_name>` to display the tree of a different folder. You can use it to search for something with `find -name <filename>`.

You can use `rmdir <directory_name>` to remove a folder. `rmdir` stands for "remove directory". 
 
There's a `-r` flag that says, "remove directories and their contents recursively". That will remove the folder and everything in it.

You can print to a file instead of the terminal with `echo text >> filename`. 

# Learn Relational Databases by Building a Mario Database
First thing to do is see what databases are here. Type `\l` into the prompt to list them.

The databases you see are there by default. You can make your own like this:

```postgreSQL
CREATE DATABASE database_name;
```

Note that all commands need a semi-colon at the end. If you don't get a message after entering a command, it means it's incomplete and you likely forgot the semi-colon. You can just add it on the next line and press enter to finish the command.

You can connect to a database by entering `\c database_name`. You need to connect to add information. 

A database is made of tables that hold your data. Enter `\d` to display the tables.

Similar to how you created a database, you can create a table like this:

```postgresql
CREATE TABLE table_name();
```

Note that the parenthesis are needed for this one. It will create the table in the database you are connected to.

You can view more details about a table by adding the table name after the display command like this: `\d table_name`. 

Tables need columns to describe the data in them, yours doesn't have any yet. Here's an example of how to add one:

```postgresql
ALTER TABLE table_name ADD COLUMN column_name DATATYPE;
```

Those are some good looking columns. You will probably need to know how to remove them. Here's an example:

```postgresql
ALTER TABLE table_name DROP COLUMN column_name;
```

A common data type is `VARCHAR`. It's a short string of characters. You need to give it a maximum length when using it like this: `VARCHAR(30)`.

Here's how you can rename a column:

```postgresql
ALTER TABLE table_name RENAME COLUMN column_name TO new_name;
```

Rows are the actual data in the table. You can add one like this:

```postgresql
INSERT INTO table_name(column_1, column_2) VALUES(value1, value2);
```

You can view the data in a table by querying it with the `SELECT` statement. Here's how it looks:

```postgresql
SELECT columns FROM table_name;
```

Here's an example of how to delete a row:

```postgresql
DELETE FROM table_name WHERE condition;
```

Drop a table from your database. Here's an example:

```postgresql
DROP TABLE table_name;
```

You can rename a database like this:

```postgresql
ALTER DATABASE database_name RENAME TO new_database_name;
```

Use the `DROP DATABASE` keywords to delete a database.

The `SERIAL` type will make your column an `INT` with a `NOT NULL` constraint, and automatically increment the integer when a new row is added.
 
Here's an example of how you could have added the previous three rows at once:

```postgresql
INSERT INTO characters(name, homeland, favorite_color)
VALUES('Mario', 'Mushroom Kingdom', 'Red'),
('Luigi', 'Mushroom Kingdom', 'Green'),
('Peach', 'Mushroom Kingdom', 'Pink');
```

You can change a value like this:

```postgresql
UPDATE table_name SET column_name=new_value WHERE condition;
```

Actually, you should put that in order. Here's an example:

```postgresql
SELECT columns FROM table_name ORDER BY column_name;
```

Next, you are going to add a **primary key**. It's a column that uniquely identifies each row in the table. Here's an example of how to set a PRIMARY KEY:

```postgresql
ALTER TABLE table_name ADD PRIMARY KEY(column_name);
```

You should set a primary key on every table and there can only be one per table.

Here's an example of how to drop a constraint:

```postgresql
ALTER TABLE table_name DROP CONSTRAINT constraint_name;
```

`NUMERIC(4, 1)` has up to four digits and one of them has to be to the right of the decimal.

To know what row is for a character, you need to set a foreign key so you can relate rows from this table to rows from your characters table. Here's an example that creates a column as a foreign key:

```postgresql
ALTER TABLE table_name ADD COLUMN column_name DATATYPE REFERENCES referenced_table_name(referenced_column_name);
```

These tables have a "one-to-one" relationship. One row in the characters table will be related to exactly one row in more_info and vice versa. Enforce that by adding the `UNIQUE` constraint to your foreign key. Here's an example:

```postgresql
ALTER TABLE table_name ADD UNIQUE(column_name);
```

The column should also be `NOT NULL` since you don't want to have a row that is for nobody. Here's an example:

```postgresql
ALTER TABLE table_name ALTER COLUMN column_name SET NOT NULL;
```

`DATE` values need a string with the format: `'YYYY-MM-DD'`.

Instead of viewing all the rows to find his id, you can just view his row with a `WHERE` condition. You used several earlier to delete and update rows. You can use it to view rows as well. Here's an example:

```postgresql
SELECT columns FROM table_name WHERE condition;
```

Inside those parenthesis you can put columns for a table so you don't need to add them with a separate command, like this:

```postgresql
CREATE TABLE table_name(column_name DATATYPE CONSTRAINTS);
```

"Many-to-many" relationships usually use a junction table to link two tables together, forming two "one-to-many" relationships.

You can set an existing column as a foreign key like this:

```postgresql
ALTER TABLE table_name ADD FOREIGN KEY(column_name) REFERENCES referenced_table(referenced_column);
```

Every table should have a primary key.  You can create a primary key from two columns, known as a composite primary key.

```postgresql
ALTER TABLE table_name ADD PRIMARY KEY(column1, column2);
```

You can get all the data from both tables with a `JOIN` command:

```postgresql
SELECT columns FROM table_1 FULL JOIN table_2 ON table_1.primary_key_column = table_2.foreign_key_column;
```

Here's an example that joins three tables:

```postgresql
SELECT columns FROM junction_table
FULL JOIN table_1 ON junction_table.foreign_key_column = table_1.primary_key_column
FULL JOIN table_2 ON junction_table.foreign_key_column = table_2.primary_key_column;
```

 
# Learn Bash Scripting by Building Five Programs
Using `sh` to run your script uses the `shell` interpreter.

`bash` stands for `bourne-again shell`.

Find out where the `bash` interpreter is located by entering `which bash` in the terminal.

That's the absolute path to the `bash` interpreter. You can tell your program to use it by placing a `shebang` at the very top of the file like this: `#!<path_to_interpreter>`. Add a `shebang` at the very top of your file, the one you want looks like this: `#!/bin/bash`.

Now, instead of using `sh` or `bash` to run your script. You can run it by executing the file and it will default to `bash`. Run your script by executing it with `./questionnaire.sh`

You should have got a permission denied message because you don't have permissions to execute the script.

Next to your file is `-rw-r--r--`. All but the first character (`-`) describe permissions different users have with the file. `r` means `read`, `w` means `write`, `x` means `execute`. I don't see an `x` anywhere, so nobody can execute it. Enter `chmod +x questionnaire.sh` in the terminal to give everyone executable permissions.

In your script, you can add any commands that you would be able to enter in the terminal.

You can create a variable with `VARIABLE_NAME=VALUE`. There cannot be any spaces around the equal (`=`) sign. If a variable has any spaces in it, place double quotes around it.

To use a variable, place `$` in front of it like this: `$VARIABLE_NAME`. Shell scripts run from top to bottom, so you can only use variable below where it's created.

Next, you want to be able to accept input from a user. You can do that with `read` like this: `read VARIABLE_NAME`. This will get user input and store it into a new variable.

`echo` will only print empty lines if the value is enclosed in quotes.

```sh
#!/bin/bash

QUESTION1="What's your name?"
QUESTION2="Where are you from?"
QUESTION3="What's your favorite coding website?"

echo -e "\n~~ Questionnaire ~~\n"

echo $QUESTION1
read NAME

echo $QUESTION2
read LOCATION

echo $QUESTION3
read WEBSITE

echo -e "\nHello $NAME from $LOCATION. I learned that your favorite coding website is $WEBSITE!"
```

Comments in `bash` look like this: `# <comment>`.

Programs can take arguments. You can access them a few different ways with `$`. Add `echo $*` in your script to print all arguments passed to it.

`$*` printed all the arguments passed to your script. To access any one of them, use `$<number>`. `arg2` could have been accessed with `$2`.

```bash
if [[ CONDITION ]]
then
  STATEMENTS
else
  STATEMENTS
fi
```

You can compare integers inside the brackets (`[[ ... ]]`) of your `if` with `-eq` (equal), `-ne` (not equal), `-lt` (less than), `-le` (less than or equal), `-gt` (greater than), `-ge` (greater than or equal).

Looks like you can use some, probably familiar, things like `!`, `&&`, and `||` to compare multiple expressions. There's also `==` and `!=` operators for an individual expression.

Each command has an exit status that can be accessed with `$?`. View the exit status of the **last command** with `echo $?`.

You can separate commands on a single line with `;`. Enter your last two commands on one line like this: `[[ 4 -ge 5 ]]; echo $?`. It will run the expression, then print the exit status of it since it was the last command.

You can think of an exit status of `0` as true. But it means that the command had zero errors. All commands have an exit status.

`command not found`, with an exit status of `127`. Anything but `0` means there was an error with the command.

```sh
for (( i = 10; i > 0; i-- ))
do
  echo $i
done
```

You can create a multiline comment like this:

```sh
: '
  comment here
  more comment here
'
```
 
```sh
while [[ CONDITION ]]
do
  STATEMENTS
done
```

You can subtract one from `I` with double parenthesis (`((...))`) and the `--` operator. In your while loop, add `(( I-- ))`.

```sh
#!/bin/bash

# Program that counts down to zero from a given argument

echo -e "\n~~ Countdown Timer ~~\n"

if [[ $1 -gt 0 ]]
then
  : '
  for (( i = $1; i >= 0; i-- ))
  do
    echo $i
    sleep 1
  done
  '
  I=$1
  while [[ $I -ge 0 ]]
  do
    echo $I
    (( I-- ))
    sleep 1
  done
else
  echo Include a positive integer as the first argument.
fi
```

A shell comes with environment variables. View them by entering `printenv` in the terminal.

These are all environment variables, they are predefined and loaded with each shell. Most of them aren’t very relevant, but it’s nice to know they’re there. One of them is `LANG`.

View all variables in the shell with `declare -p`. `-p` stands for `print`. This list includes all the environment variables, and any others that may have been created in the current shell. There's one named `RANDOM`.

The `RANDOM` variable will generate a random number between 0 and 32767. You can use the `modulus` operator to make it in the range you want.

Bash sees everything as a string so it just printed the `%75` part literally.

The double parenthesis performed the calculation.

Note that you don't need to prepend variables with `$` inside these parenthesis.

Using the double parenthesis like you have been is good for changing variable values or making comparisons. It makes the calculation in place and provides no output. If you want to make a calculation and do something with the result, add a `$` in front like this: `$(( ... ))`.

`$(( I + 4 ))` It should say, `bash: 15: command not found`. It replaced the command with the result of the calculation. Effectively, trying to run `15` as a command. Enter the same command, but put `echo` in front of it.

These double parenthesis with a `$` are how you can assign a variable to some calculation.

So, as a reminder, `(( ... ))` will perform a calculation or operation and output nothing. `$(( ... ))` will replace the calculation with the result of it.

`declare` can be used to create variables, but you are just going to use it to view them for now. If you scroll up a little, you should find your `I` and `J` variables in there. View `J` with `declare -p J`.

You used the double square brackets with your `if` statement in the last program, but you can use the double parenthesis with these operators as well.
 
`if` statements can have an "else if" area like this:

```sh
if (( CONDITION ))
then
  STATEMENTS
elif [[ CONDITION ]]
then
  STATEMENTS
fi
```

You can add as many `elif` sections to an `if` statement as you want.

```sh
#!/bin/bash

# Bingo Number Generator

echo -e "\n~~ Bingo Number Generator ~~\n"

NUMBER=$(( RANDOM % 75 + 1 ))
TEXT="The next number is, "

if (( NUMBER <= 15 ))
then
  echo $TEXT B:$NUMBER
elif [[ $NUMBER -le 30 ]]
then
  echo $TEXT I:$NUMBER
elif (( NUMBER < 46 ))
then
  echo $TEXT N:$NUMBER
elif [[ $NUMBER -lt 61 ]]
then
  echo $TEXT G:$NUMBER
else
  echo $TEXT O:$NUMBER
fi
```

In the terminal, create an array like this: `ARR=("a" "b" "c")`.

Each variable in the array is like any other variable, just combined into a single variable. In the terminal, print the second item in the array with `echo ${ARR[1]}`. Note that the first item would be index zero.

If you recall, you were able to print all the arguments to your `countdown.sh` script with `echo $*`. `echo $@` would have worked as well. Similarly, you can use the `*` or `@` to print your whole array.

It looks like you can create a function like this:

```sh
FUNCTION_NAME() {
  STATEMENTS
}
```

The `until` loop is very similar to the `while` loop you used. It will execute the loop until a condition is met. Here's an example:

```sh
until [[ CONDITION ]]
do
  STATEMENTS
done
```

You can test if two strings are the same with `==`.

An important operator in that menu is `=~`. It allows for pattern matching.

Your patterns have been checking for literal matches, `el` and `lo wor`. You can use regular expression characters as well, but you can't put the pattern in quotes when you do. Using the same syntax, check if `hello world` starts with an `h` by using `^h` as the pattern.

You can pass arguments to functions like you did with your script.

```sh
#!/bin/bash

# Program to tell a persons fortune

echo -e "\n~~ Fortune Teller ~~\n"

RESPONSES=("Yes" "No" "Maybe" "Outlook good" "Don't count on it" "Ask again later")
N=$(( RANDOM % 6 ))

GET_FORTUNE() {
  if [[ ! $1 ]]
  then
    echo Ask a yes or no question:
  else
    echo Try again. Make sure it ends with a question mark:
  fi
  read QUESTION
}

GET_FORTUNE

until [[ $QUESTION =~ \?$ ]]
do 
  GET_FORTUNE again
done

echo -e "\n"${RESPONSES[$N]}
```

It says you can view the type of a command with `type <command>`.

# Learn SQL by Building a Student Database: Part 1
`cat` is a terminal command for printing the contents of a file. Here's an example: `cat <filename>`.

Instead of printing the content, you can pipe that output into a while loop so you can go through the rows one at a time. It looks like this:

```sh
cat courses.csv | while read MAJOR COURSE
do
  <STATEMENTS>
done
```

Each new line will be read into the variables, `MAJOR` and `COURSE`.

There's a default `IFS` variable in bash. IFS stands for "Internal Field Separator". View it with `declare -p IFS`. This variable is used to determine word boundaries. It defaults to spaces, tabs, and new lines.

You used the `psql` command to log in and interact with the database. You can use it to just run a single command and exit. Above your loop, add a `PSQL` variable that looks like this: `PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c"`. This will allow you to query your database from your script. The important parts are the `username`, `dbname`, and the `-c` flag that is for running a single command and exiting. The rest of the flags are for formatting.

Now, you can query your database using the `PSQL` variable like this: `$($PSQL "<query_here>")`. The code in the parenthesis will run in a subshell, which is a separate bash process.

Below your first `if not found` comment, add an `if` condition that checks if the `MAJOR_ID` variable is empty. You can do that with this test: `[[ -z $MAJOR_ID ]]`.

You can use `TRUNCATE` to delete all data from a table. In the psql prompt, try to delete all the data in the majors table by entering `TRUNCATE majors;`

It says you "cannot truncate a table referenced in a foreign key constraint." The `students` and `majors_courses` tables use the `major_id` from `majors` as a foreign key. So if you want to delete the data from `majors`, you need to delete the data from those two tables at the same time. Use `TRUNCATE` to delete the data from those three tables. Separate the tables with commas.

```bash
#!/bin/bash

# Script to insert data from courses.csv and students.csv into students database

PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c"
echo $($PSQL "TRUNCATE students, majors, courses, majors_courses")

cat courses.csv | while IFS="," read MAJOR COURSE
do
  if [[ $MAJOR != "major" ]]
  then
    # get major_id
    MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")

    # if not found
    if [[ -z $MAJOR_ID ]]
    then
      # insert major
      INSERT_MAJOR_RESULT=$($PSQL "INSERT INTO majors(major) VALUES('$MAJOR')")
      if [[ $INSERT_MAJOR_RESULT == "INSERT 0 1" ]]
      then
        echo Inserted into majors, $MAJOR
      fi

      # get new major_id
      MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")
    fi

    # get course_id
    COURSE_ID=$($PSQL "SELECT course_id FROM courses WHERE course='$COURSE'")

    # if not found
    if [[ -z $COURSE_ID ]]
    then
      # insert course
      INSERT_COURSE_RESULT=$($PSQL "INSERT INTO courses(course) VALUES('$COURSE')")
      if [[ $INSERT_COURSE_RESULT == "INSERT 0 1" ]]
      then
        echo Inserted into courses, $COURSE
      fi

      # get new course_id
      COURSE_ID=$($PSQL "SELECT course_id FROM courses WHERE course='$COURSE'")
    fi

    # insert into majors_courses
    INSERT_MAJORS_COURSES_RESULT=$($PSQL "INSERT INTO majors_courses(major_id, course_id) VALUES($MAJOR_ID, $COURSE_ID)")
    if [[ $INSERT_MAJORS_COURSES_RESULT == "INSERT 0 1" ]]
    then
      echo Inserted into majors_courses, $MAJOR : $COURSE
    fi
  fi
done

cat students.csv | while IFS="," read FIRST LAST MAJOR GPA
do
  if [[ $FIRST != "first_name" ]]
  then
    # get major_id
    MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'") 

    # if not found
    if [[ -z $MAJOR_ID ]]
    then
      # set to null
      MAJOR_ID=null
    fi

    # insert student
    INSERT_STUDENT_RESULT=$($PSQL "INSERT INTO students(first_name, last_name, major_id, gpa) VALUES('$FIRST', '$LAST', $MAJOR_ID, $GPA)")
    if [[ $INSERT_STUDENT_RESULT == "INSERT 0 1" ]]
    then
      echo Inserted into students, $FIRST $LAST
    fi
  fi
done
```

# # Learn SQL by Building a Student Database: Part 2

enter `psql -U postgres < students.sql` in it to rebuild the database.

You can return only rows you want by adding `WHERE <condition>` to your query. A condition can consist of a column, an operator, and a value.

Some other operators are: `<`, `>`, `<=`, `>=`.

There's equal (`=`) and not equal (`!=`) operators as well.

The operators you used with numbers in the last section can be used on text as well. Don't forget that You need single quotes around text values.

You can use multiple conditions after `WHERE` with `AND` or `OR`, among others. Just add the keyword and another condition.

You can group conditions together with parenthesis like this: `WHERE <condition_1> AND (<condition_2> OR <condition_2>)`.
 
You can use `LIKE` to find patterns in text like this: `WHERE <column> LIKE '<pattern>'`. An underscore (`_`) in a pattern will return rows that have any character in that spot.

Another pattern character is `%`. It means anything can be there. To find names that start with `W`, you could use `W%`

You can use `NOT LIKE` to find things that don't match a pattern.

`ILIKE` will ignore the case of the letters when matching.

You can put `NOT` in front of `ILIKE` as well.

You can access them using `IS NULL` as a condition like this: `WHERE <column> IS NULL`.

Inversely, you can use `IS NOT NULL` to see rows that aren't null.

You can specify the order you want your results to be in by adding `ORDER BY <column_name>` at the end of a query.

When using `ORDER BY`, it will be in ascending (`ASC`) order by default. Add `DESC` (descending) at the end of the last query to put the highest ones at the top.

You can add more columns to the order by separating them with a comma like this: `ORDER BY <column_1>, <column_2>`. Any matching values in the first ordered column will then be ordered by the next.

Many times, you only want to return a certain number of rows. You can add `LIMIT <number>` at the end of the query to only get the amount you want.

The order of the keywords in your query matters. You cannot put `LIMIT` before `ORDER BY`, or either of them before `WHERE`.

There's a number of mathematic functions to use with numerical columns. One of them is `MIN`, you can use it when selecting a column like this: `SELECT MIN(<column>) FROM <table>`. It will find the lowest value in the column.

Another one is `MAX`.

In the same fashion, use a `SUM` function find out what all the values of the `major_id` column in the `students` table add up to.

`AVG` will give you the average of all the values in a column.

You can round decimals up or down to the nearest whole number with `CEIL` and `FLOOR`, respectively.

Or, you can round a number to the nearest whole number with `ROUND`.

You can round to a specific number of decimal places by adding a comma and number to `ROUND`, like this: `ROUND(<number_to_round>, <decimals_places>)`.

Another function is `COUNT`. You can use it like this: `COUNT(<column>)`. It will tell you how many entries are in a table for the column.

Using `major_id` didn't count the `null` values in that column.

`DISTINCT` is a function that will show you only unique values. You can use it like this: `DISTINCT(<column>)`.

There's six unique `major_id` values in the `students` table. You can get the same results with `GROUP BY`. Here's an example of how to use it: `SELECT <column> FROM <table> GROUP BY <column>`.

The output was the same as `DISTINCT`, but with `GROUP BY` you can add any of the aggregate functions (`MIN`, `MAX`, `COUNT`, etc) to it to find more information. For instance, if you wanted to see how many students were in each major you could use `SELECT COUNT(*) FROM students GROUP BY major_id`.

When using `GROUP BY`, any columns in the `SELECT` area must be included in the `GROUP BY` area. Other columns must be used with any of the aggregate functions (`MAX`, `AVG`, `COUNT`, etc).
 
Another option with `GROUP BY` is `HAVING`. You can add it at the end like this: `SELECT <column> FROM <table> GROUP BY <column> HAVING <condition>`. The condition must be an aggregate function with a test. An example to might be to use `HAVING COUNT(*) > 0` to only show what whatever column is grouped that have at least one row.

You can rename a column with `AS` like this: `SELECT <column> AS <new_column_name>`.

The `majors` and `students` table are linked with the `major_id` foreign key. If you want to see the name of a major that a student is taking, you need to `JOIN` the two tables into one. Here's an example of how to do that:  
`SELECT * FROM <table_1> FULL JOIN <table_2> ON <table_1>.<foreign_key_column> = <table_2>.<foreign_key_column>;`

The `FULL JOIN` you used will include **all** rows from both tables, whether or not they have a row using that foreign key in the other. From there, you could use any of the previous methods to narrow down, group, order, etc. 

A `LEFT JOIN` gets all rows from the left table, but only rows from the right table that are linked to from the left one. 

The right join showed all the rows from the right table (`majors`), but only rows from the left table (`students`) if they have a major.

The `INNER JOIN` only returned students if they have a major and majors that have a student. In other words, it only returned rows if they have a value in the foreign key column (`major_id`) of the opposite table.
 
You would need to specify what table you want the column from like this: `<table>.<column>`.
  
Earlier, you used `AS` to rename columns. You can use it to rename tables, or give them aliases, as well. Here's an example: `SELECT * FROM <table> AS <new_name>;`.

There's a shortcut keyword, `USING` to join tables if the foreign key column has the same name in both tables. Here's an example: `SELECT * FROM <table_1> FULL JOIN <table_2> USING(<column>);`

You can add a third table to a join like this: `SELECT * FROM <table_1> FULL JOIN <table_2> USING(<column>) FULL JOIN <table_3> USING(<column>)`. This example will join the first two tables into one, turning it into the left table for the second join.

What you're seeing is every unique combination of rows in the database.

[[Student Database Part 2]]
 
# Learn Advanced Bash by Building a Kitty Ipsum Translator
You can `redirect` that output to a file using `>`. Here’s an example: `<command> > <filename>`.

A single `>` will create or overwrite the file. Use the same command with `>>` to append to the file.

Enter `> stdout.txt` in the terminal to redirect nothing into the file. Effectively, emptying it.

There’s two types of output, `stdout` (standard out) for when a command is successful, and `stderr` (standard error) for when it’s not. Both of these will print to the terminal by default. `bad_command` was not a valid command, so it printed to `stderr`. You can redirect `stderr` with `2>`.

Similarily, you can use `1>` to redirect `stdout`.

`stdin` (standard in) is the third thing commands can use and is for getting input. The default is the keyboard.

The `read` command is looking at `stdin` for where to get input, which is pointing to the keyboard.

Just like you can redirect output, you can redirect `stdin` as well. Here's an example: `<command> < <filename_for_stdin>`.

Another way to set the `stdin` is by using the pipe (`|`). It will use the output from one command as input for another. Here's an example: `<command_1> | <command_2>`. This will take the `stdout` from `command_1` and use it as the `stdin` for `command_2`.

It worked, but it doesn't look like it. When you used the pipe (`|`) to set the input for `read`, it ran the command in a subshell or subprocess. Basically, another terminal instance within the one you see. The variable was set in there and didn't affect the one you had previously set. 

`cat` is another command that takes input. `cat` will print the contents of a file or input to `stdout`.
 
`wc` stands for `word count`. It showed you how many lines were in the file, how many words, and how many bytes. Use the `-l` flag to only output how many lines are in the file.

`grep` is a command for searching for patterns in text. You can use it like this: `grep '<pattern>' <filename>`.

```shell
grep 'meow' kitty_ipsum_1.txt 
```

It showed you all the lines that contain `meow` somewhere in them.

```shell
grep --color 'meow' kitty_ipsum_1.txt
```

Add the flag to show all the line numbers with the command.

```shell
grep --color -n 'meow' kitty_ipsum_1.txt
```

`grep` can use regular expressions, too. Enter the previous command, but change the pattern to `meow[a-z]*` to see all words that start with `meow`.

`grep` has a `-c` flag to give you a count.

```shell
grep -c 'meow[a-z]*' kitty_ipsum_1.txt
```

That gave you a count of the number lines that the pattern occurred on.

But there is a `-o` flag that will says it will put the matches on their own lines.

```shell
grep -o 'meow[a-z]*' kitty_ipsum_1.txt | wc -l
```

`wc` counted the lines in the output of the `grep`. That should be the count for how many times those words appear.

`sed` can replace text like this: `sed 's/<pattern_to_replace>/<text_to_replace_it_with>/' <filename>`. By default, it won't replace the text in the file. It will output it to `stdout`.

You can add regex flags after the last `/` in the `sed` argument. A `g`, for `global`, would replace all instances of a matched pattern, or an `i` to ignore the case of the pattern.

There's a flag to use extended regular expressions. Add it to that previous command that didn't work so it recognizes the `+` in your pattern.

```shell
grep -n 'meow[a-z]*' kitty_ipsum_1.txt | sed -E 's/[0-9]+/1/'
```

Next, you will use a capture group in the regex to capture the numbers so you can use them in the replacement area. Enter the same command but use `s/([0-9]+)/\1/` with `sed` to capture the numbers at the start. It will replace them with themselves for now.

All you need to do is match everything else on each line and replace it with only the numbers. Add `.*` at the end of the `sed` matching pattern so it matches everything, captures the numbers, and replaces everything with the captured numbers.

```shell
grep -n 'meow[a-z]*' kitty_ipsum_1.txt | sed -E 's/([0-9]+).*/\1/'
```

You can replace many patterns using `sed` like this: `sed 's/<pattern_1>/<replacement_1>/; s/<pattern_2>/<replacement_2>/'`. Note that you need the semi-colon between the two replacement patterns and they both need to be wrapped in the quotes.

Enter the same command, but add the flag to use extended regular expressions to the `grep` search so it recognizes the `|`.

`diff` is a command to view the difference between two files. You can use it like this: `diff <file_1> <file_2>`.

Use the flag to show the diff of the same two files in color.

```shell
diff kitty_ipsum_1.txt doggy_ipsum_1.txt --color
```

```shell
#!/bin/bash

cat $1 | sed -E 's/catnip/dogchow/g; s/cat/dog/g; s/meow|meowzer/woof/g' 
```

 
# Learn Bash and SQL by Building a Bike Rental Shop
You can use a `case` statement for this.

```sh
case EXPRESSION in
  PATTERN) STATEMENTS ;;
  PATTERN) STATEMENTS ;;
  PATTERN) STATEMENTS ;;
  *) STATEMENTS ;;
esac
```

```shell
case $MAIN_MENU_SELECTION in
   1) RENT_MENU ;;
   2) RETURN_MENU ;;
   3) EXIT ;;
   *) MAIN_MENU ;;
esac
```

So that pattern will match any positive integers.

```sh
[[ 11 =~ ^[0-9]+$ ]]; echo $?
```
 
What you put the in subshell (`$(...)`) will be executed, and the result of it will replace the subshell.

```sh
BIKE_INFO_FORMATTED=$(echo $BIKE_INFO | sed 's/ |/"/')
```
 
```sh
#!/bin/bash

PSQL="psql -X --username=freecodecamp --dbname=bikes --tuples-only -c"

echo -e "\n~~~~~ Bike Rental Shop ~~~~~\n"

MAIN_MENU() {
  if [[ $1 ]]
  then
    echo -e "\n$1"
  fi

  echo "How may I help you?" 
  echo -e "\n1. Rent a bike\n2. Return a bike\n3. Exit"
  read MAIN_MENU_SELECTION

  case $MAIN_MENU_SELECTION in
    1) RENT_MENU ;;
    2) RETURN_MENU ;;
    3) EXIT ;;
    *) MAIN_MENU "Please enter a valid option." ;;
  esac
}

RENT_MENU() {
  # get available bikes
  AVAILABLE_BIKES=$($PSQL "SELECT bike_id, type, size FROM bikes WHERE available = true ORDER BY bike_id")

  # if no bikes available
  if [[ -z $AVAILABLE_BIKES ]]
  then
    # send to main menu
    MAIN_MENU "Sorry, we don't have any bikes available right now."
  else
    # display available bikes
    echo -e "\nHere are the bikes we have available:"
    echo "$AVAILABLE_BIKES" | while read BIKE_ID BAR TYPE BAR SIZE
    do
      echo "$BIKE_ID) $SIZE\" $TYPE Bike"
    done

    # ask for bike to rent
    echo -e "\nWhich one would you like to rent?"
    read BIKE_ID_TO_RENT

    # if input is not a number
    if [[ ! $BIKE_ID_TO_RENT =~ ^[0-9]+$ ]]
    then
      # send to main menu
      MAIN_MENU "That is not a valid bike number."
    else
      # get bike availability
      BIKE_AVAILABILITY=$($PSQL "SELECT available FROM bikes WHERE bike_id = $BIKE_ID_TO_RENT AND available = true")

      # if not available
      if [[ -z $BIKE_AVAILABILITY ]]
      then
        # send to main menu
        MAIN_MENU "That bike is not available."
      else
        # get customer info
        echo -e "\nWhat's your phone number?"
        read PHONE_NUMBER

        CUSTOMER_NAME=$($PSQL "SELECT name FROM customers WHERE phone = '$PHONE_NUMBER'")

        # if customer doesn't exist
        if [[ -z $CUSTOMER_NAME ]]
        then
          # get new customer name
          echo -e "\nWhat's your name?"
          read CUSTOMER_NAME

          # insert new customer
          INSERT_CUSTOMER_RESULT=$($PSQL "INSERT INTO customers(name, phone) VALUES('$CUSTOMER_NAME', '$PHONE_NUMBER')") 
        fi

        # get customer_id
        CUSTOMER_ID=$($PSQL "SELECT customer_id FROM customers WHERE phone='$PHONE_NUMBER'")

        # insert bike rental
        INSERT_RENTAL_RESULT=$($PSQL "INSERT INTO rentals(customer_id, bike_id) VALUES($CUSTOMER_ID, $BIKE_ID_TO_RENT)")

        # set bike availability to false
        SET_TO_FALSE_RESULT=$($PSQL "UPDATE bikes SET available = false WHERE bike_id = $BIKE_ID_TO_RENT")

        # get bike info
        BIKE_INFO=$($PSQL "SELECT size, type FROM bikes WHERE bike_id = $BIKE_ID_TO_RENT")
        BIKE_INFO_FORMATTED=$(echo $BIKE_INFO | sed 's/ |/"/')
        
        # send to main menu
        MAIN_MENU "I have put you down for the $BIKE_INFO_FORMATTED Bike, $(echo $CUSTOMER_NAME | sed -r 's/^ *| *$//g')."
      fi
    fi
  fi
}

RETURN_MENU() {
  # get customer info
  echo -e "\nWhat's your phone number?"
  read PHONE_NUMBER

  CUSTOMER_ID=$($PSQL "SELECT customer_id FROM customers WHERE phone = '$PHONE_NUMBER'")

  # if not found
  if [[ -z $CUSTOMER_ID  ]]
  then
    # send to main menu
    MAIN_MENU "I could not find a record for that phone number."
  else
    # get customer's rentals
    CUSTOMER_RENTALS=$($PSQL "SELECT bike_id, type, size FROM bikes INNER JOIN rentals USING(bike_id) INNER JOIN customers USING(customer_id) WHERE phone = '$PHONE_NUMBER' AND date_returned IS NULL ORDER BY bike_id")

    # if no rentals
    if [[ -z $CUSTOMER_RENTALS  ]]
    then
      # send to main menu
      MAIN_MENU "You do not have any bikes rented."
    else
      # display rented bikes
      echo -e "\nHere are your rentals:"
      echo "$CUSTOMER_RENTALS" | while read BIKE_ID BAR TYPE BAR SIZE
      do
        echo "$BIKE_ID) $SIZE\" $TYPE Bike"
      done

      # ask for bike to return
      echo -e "\nWhich one would you like to return?"
      read BIKE_ID_TO_RETURN

      # if not a number
      if [[ ! $BIKE_ID_TO_RETURN =~ ^[0-9]+$ ]]
      then
        # send to main menu
        MAIN_MENU "That is not a valid bike number."
      else
        # check if input is rented
        RENTAL_ID=$($PSQL "SELECT rental_id FROM rentals INNER JOIN customers USING(customer_id) WHERE phone = '$PHONE_NUMBER' AND bike_id = $BIKE_ID_TO_RETURN AND date_returned IS NULL")
        # if input not rented
        if [[ -z $RENTAL_ID ]]
        then
        # send to main menu
        MAIN_MENU "You do not have that bike rented."
        else
          # update date_returned
          RETURN_BIKE_RESULT=$($PSQL "UPDATE rentals SET date_returned = NOW() WHERE rental_id = $RENTAL_ID")

          # set bike availability to true
          SET_TO_TRUE_RESULT=$($PSQL "UPDATE bikes SET available = true WHERE bike_id = $BIKE_ID_TO_RETURN")

          # send to main menu
          MAIN_MENU "Thank you for returning your bike."
        fi
      fi
    fi
  fi
}

EXIT() {
  echo -e "\nThank you for stopping in.\n"
}

MAIN_MENU
```
 
# Learn Nano by Building a Castle
Nano is a program for editing files that runs in the terminal. You can open a file with `nano filename`.

You can "cut" text with `control + k`. Move the cursor to the line with your text and remove the whole line. When you are done, save the file with `control + o`. Note that you cannot use a mouse to move your cursor.

The `M` at the beginning of the other commands at the bottom stands for "meta". It's a key that doesn't exist on most keyboards. If you're on OSX it means press `escape` then the letter. If you are on another system, press `ALT` then the letter.


# Learn Git by Building an SQL Reference Object
Git is a version control system that keeps track of all the changes you make to your codebase.

Git is a version control system to keep track of your code. This folder will be your git repository. Turn it into one by typing `git init` in the terminal from this folder.

The `git init` command created that `.git` folder for you. It's what keeps track of all the things in your repository. Use `git status` to see the status of where you are.

A git repository has branches to help keep track of things you are doing with your code. It's common to have a `main` branch which might be for your production code, and other branches for adding new features or fixing bugs. You can create and go to a new branch with `git checkout -b new_branch`. The `-b` stands for "branch".

The file you created has not been added to git yet so it is showing that it is untracked. There's two steps to make git keep track of it for you. First you need to add it to the staging area like this: `git add file_name`.

Now your file is in staging and will be added with the next commit.

Now you have two files in staging. To commit them, you can use `git commit -m "Initial commit"`. The `-m` stands for "message". Often times, the first commit of a repo will have the message "Initial commit".

When you make a commit, whatever is in the staging area will be added to your git history.

Your "working tree" is clean, the files were committed and there's no other new changes that git recognizes. You can see your commit history with `git log`.

You can see the commit you made. It shows the message you gave with the commit, along with your username, email, the date, and a commit hash.

Git recognizes new unstaged changes to your file. Notice that it says that file is modified instead of untracked because the file has been previously committed. You can see the changes you made with `git diff`.

The lines with `+` in front means that those lines were added.

Commit messages often start with `fix:` or `feat:`, among others, to help people understand what your commit was for.

Now there's two commits in your history, the newest one is at the top.

You have been making changes to your `main` branch. You actually want to try and avoid that. Type `git branch` to see the current branches in your repo.

You can create a branch with `git branch branch_name`. Branches often start with `fix/` or `feat/`, among others, like commit messages, but they use a forward slash and can't contain spaces.

Your new branch is a clone of the `main` branch since that's the branch you were on when you created it. It will have the same code and commit history as `main` did at the time of the branch creation.

You can see your new branch, but you are still on the `main` branch, as denoted with the `*`. To switch to a branch use: `git checkout branch_name`.

Like I said, you often don't want to make commits directly to the main branch of a repo. This branch will be for some new changes. What you will do is make the changes and commits here, then merge them into the `main` branch when they are ready.

Check the log again, but this time use the `--oneline` flag to condense the output so it's more readable.

You can use `git merge branch_name` to bring changes from a branch into the branch you are currently on.

You can delete a branch with `git branch -d branch_name`. `-d` stands for "delete". Since your changes were added, you can safely delete your feature branch.

Last time you created a branch and then switched to it. You can do both at the same time with `git checkout -b branch_name`.

The process is to create a branch, make the changes you want, commit them, and then merge the changes into branch you started on.

Here's a tip: you can use `git add .` to add all files to staging.

You created this branch and made a commit. Since then, a commit for a bug fix was added to `main`. This is common with many people working on a codebase simultaneously. You need to update this branch so it has the same commits from `main`, but you can't just merge that branch into this one. You need that bug fix commit to be in the same order here as it is on `main`, right after the "drop table" commit. You need to `rebase` this branch against `main` to do that. Enter `git rebase main` to rebase this branch.

The logs show that the bug fix commit from `main` was added, and then the commit from this branch was added on top of it. Now, when this branch is ready to be merged into `main`, it will have the same commit history. You should try to keep your branches up to date like this by rebasing them often.

Another commit was added to `main`, you should update this branch again. To be more specific, a rebase will "rewind" this branch to where it last matched `main`, then, add the commits from `main` that aren't here. After that, it adds the commits you made to this branch on top.

The conflict arose because the first commit you added to this branch changed the same lines as the commit from `main`. So it tried to add the commit, but couldn't because something was already there. There are sections, separated by characters (`<`, `>`, and `=`), that represent the commit you are on (`HEAD`) and the commit that is trying to be added (`feat: add column reference`).

It says that you are still in the middle of rebasing and there's one file that needs to be merged yet. Add the file to staging like you would any other commit.

You fixed the conflicts that arose from trying to add this commit and added them to staging. It says `all conflicts fixed: run "git rebase --continue"`. Run the suggested command to continue the rebase.

You can put your changes aside with `git stash`. Stash your changes so you can add them to a different branch.

The changes you made are stashed. View the things you have stashed with `git stash list`.

Bring the changes back with `git stash pop`.

The changes from the stash reappeared in the file and git showed the status for you. You are right where you left of before stashing the changes. Popping a stash like that will remove the most recent stash and apply it to your working tree.

View a condensed version of the changes in the **latest** stash with `git stash show`.

You can see what file was changed and how many lines were added and removed from the file. View the full changes of the latest stash with `git stash show -p`. `-p` stands for "patch".

You can add the latest stash while keeping it in the list with `git stash apply`.
  
Now there's two things stashed. You can use the name at the front of each stash (`stash@{#}`) with many of the stash commands to select one other than the latest one. The most recent stash is the one at the top, `stash@{0}`.

There's two identical items in your stash. Drop one of them with `git stash drop` or `git stash drop <stash_name>`.

I'm going to show you a few ways to remove or undo a commit. The first is to simply "travel back in time". You can use the `git reset` command to travel to any point in your commit history. Your current `HEAD` is a reference to the last commit you just made. Use `git reset HEAD~1` to go back one before `HEAD`.

This is a "mixed" reset and will put the changes from the commit you undid in your working tree. You can see that it says there's unstaged changes after the reset to your file.

And the changes from the reset are back in the working tree. So when you `reset` to one commit before `HEAD`, it removed the most recent commit, and put all the changes in the working tree. If you used the `--hard` flag with the reset, the changes would have not been added to the working tree and if you used the `--soft` flag, the changes would have been added to the working tree and to staging.

Reverting is a good way to undo a commit because you don't lose the commit from the history. You can revert the most recent commit (`HEAD`) with `git revert HEAD`.

Git put you into Nano and is asking you enter a commit message for the revert, but they added a default one for you. Don't change anything in Nano, just exit the file to use the default message.

Using revert to undo that commit added another commit that is the exact opposite of it. Enter `git show` into the terminal to see the last commit added (now `HEAD`) and its details.

Type `git show HEAD~1` to take a look at the details of the original commit that you reverted.

You've used rebase to update this branch, but you can enter an "interactive" mode to manipulate commits. Type `git rebase --interactive HEAD~2` into the terminal to enter this mode. The `HEAD~2` means you will have a chance to change the last two commits.

At the top of Nano, you can see the two commits with `pick` next to them. Below them, there's a list of options for working with them. `pick` means that it will use the commits as they were. At the bottom, it says, `d, drop = remove commit`. Replace the word `pick` preceeding your two commits with a `d` to drop them both.

Enter another `--interactive` rebase that goes back to the `--root` instead of `HEAD~2`. I am going to show you how to change a commit message. `--root` means that the rebase will go back to your very first commit.

You can see that the latest commit is at the bottom here. One of the options is `r, reword = use commit, but edit the commit message`. Replace `pick` with an `r` next to the commit. Git will put you in another Nano instance to reword the commit message.

The message was reworded, but there's a problem. Look at the commit hash for your `Initial commit` from the last two times you viewed the log, it's that string left of the log. They aren't the same anymore since you rebased back to the root. Same goes for the rest of the commits. When you rebase interactively it changes all those hashes, so git sees them as different commits. If you were to try and merge this into `main`, it wouldn't work because they don't share the same history anymore. For this reason, you don't want to do an interactive rebase where you go back passed commits unique to the branch you are on. Fortunately, you can fix this. Enter `git rebase main` to realign the history of the two branches.

Squashing commits means that you will take a bunch of commits and turn them into one. This is helpful to keep your commit history clean and something you want try to do. Replace `pick` with an `s` next to all your commits.

View the log again, but use `-1` instead of `--oneline` this time to view only the last commit.

You viewed the most recent log with a `-1` flag. You can view the last `x` number of commits with any number instead of `1`.

`.env` files are used to store environment variables for running code. Often times, there may be sensitive information in it. Add the text `SECRET=MY_SECRET` to the file.

Now the `.env` file is being ignored by git because you added it to the `.gitignore` file. There are often a number of things you don't want to include in a repository, especially if it's publicly visible.

Sensitive information can be stored in the `.env` file, but people need to know the variables that are in there so they can run a repository locally. Add `SECRET=` to `sample.env`. Now, when someone wants to run your repo, they will know that they need to create a `.env` file and add a value in it for `SECRET`.

```json
{
  "database": {
    "create": "CREATE DATABASE database_name;",
    "drop": "DROP DATABASE database_name;",
    "rename": "ALTER DATABASE database_name RENAME TO new_name;"
  },
  "table": {
    "create": "CREATE TABLE table_name();",
    "drop": "DROP TABLE table_name;",
    "rename": "ALTER TABLE table_name RENAME TO new_name;"
  },
  "row": {
    "insert": "INSERT INTO table_name(columns) VALUES(values);",
    "update": "UPDATE table_name SET column_name = new_value WHERE condition;",
    "delete": "DELETE FROM table_name WHERE condition;"
  },
  "column": {
    "add": "ALTER TABLE table_name ADD COLUMN column_name;",
    "drop": "ALTER TABLE table_name DROP COLUMN column_name;",
    "rename": "ALTER TABLE table_name RENAME COLUMN column_name TO new_name;",
    "primary_key": "ALTER TABLE table_name ADD PRIMARY KEY(column_name);",
    "foreign_key": "ALTER TABLE table_name ADD FOREIGN KEY(column_name) REFERENCES table_name(column_name);"
  }
}
```

