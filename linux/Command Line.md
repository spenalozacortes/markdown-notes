# Viewing and Changing the File System

## Manipulation

### ls, revisited
The ls command lists all files and directories in the working directory. We can use ls as is, or attach an option. Options modify the behavior of commands.

```bash
ls -a
```

The command above displays the contents of the working directory in more detail. This command displays all the files and directories, including those starting with a dot (.). Files starting with a dot are normally hidden, and don’t appear when using ls alone.

In addition to -a, the ls command has several more options. Here are three common ones:

- -a - lists all contents, including hidden files and directories
- -l - (a lowercase “L”) lists all contents of a directory in long format, as well as the file permissions
- -t - orders files and directories by the time they were last modified.

### ls & Combining Options
The -l (lowercase “L”) option lists files and directories as a table.

1. Access rights. These indicate the read, write, and execute permissions on the file or directory allowed to the owner, the group, and all users.
2. Number of hard links. This represents the number of hard links to the file or directory. This number includes the parent directory link (..) and current directory link (.).
3. The username of the file’s owner. 
4. The name of the group that owns the file. 
5. The size of the file in bytes.
6. The date & time that the file was last modified.
7. The name of the file or directory.

In addition to using each option separately, like ls -a or ls -l, multiple options can be used together, like ls -alt.

ls -alt lists all contents, including hidden files and directories, in long format, ordered by the date and time they were last modified.

### cat
The cat command outputs the contents of a specified file.

```bash
cat genres.txt
```

This is a useful command for peeking at files without opening them, and confirming the result of other commands that change the contents of files.

We can also get output using paths to a specified file. 

```bash
cat action/batman.txt
```

### cp Part I
The cp command copies files or directories.

```bash
cp source.txt destination.txt 
```

NOTE: The “.bak“ file extension is commonly used to notate a file as a backup of a file with the same name.

We could also copy a file to a destination directory:

```bash
cp source.txt directory
```

If we wanted to rename the file as well, we would include the name in the path of the second argument:

```bash
cp the-office.txt slapstick/the-office-us.txt
```

### cp Part II
To copy multiple files into a directory, use cp with a list of source files as the first arguments, and the destination directory as the last argument.

```bash
cp file1.txt file2.txt my_directory/
```

### Wildcards
In addition to using exact filenames as arguments, we can use special characters like * to select groups of files. These special characters are called *wildcards*.

Here we use cp to copy all files in the current working directory into another directory.

```bash
cp * my_directory/
```

To move just the ‘.txt’ files you can use a wild card with a suffix:

```bash
cp *.txt my_directory/
```

In addition to suffixes, prefix text can be used with wildcards. Using w*.txt selects all files in the working directory starting with “w” (prefix) and ending with “.txt” (suffix), and copies them to my_directory/.

```bash
cp w*.txt my_directory/
```

### mv
The `mv` command moves files. It’s similar to `cp` in its usage, except `mv` moves a file without making a copy.

To move a file into a directory, use `mv` with the source file as the first argument and the destination directory as the second argument.

```bash
mv my_file.txt my_directory/
```

To move multiple files into a directory, use `mv` with a list of source files as the first arguments, and the destination directory as the last argument. 

```bash
mv my_file_1.txt my_file_2.txt my_directory/
```

`mv` can also be used to rename a file.

```bash
mv file_original.txt file_renamed.txt
```

### rm
The `rm` command deletes files and directories.

```bash
rm unwanted_file.txt
```

The -r (recursive) option is used to delete a directory and all of its child directories.

```bash
rm -r unwanted_directory
```

Be careful when you use `rm`! It deletes files and directories permanently. There isn’t an undelete command, so once you delete a file or directory with `rm`, it’s gone.

### Review
- Options modify the behavior of commands:
	- `ls -a` lists all contents of a directory, including hidden files and directories
	- `ls -l` lists all contents in long format
	- `ls -t` orders files and directories by the time they were last modified
	- Multiple options can be used together, like `ls -alt`
- From the command line, you can also copy, move, and remove files and directories:
	- `cp` copies files
	- `mv` moves and renames files
	- `rm` removes files
	- `rm -r` removes directories
- Wildcards are useful for selecting groups of files and directories


# Redirecting Input and Output
## Redirection

### Introduction
Through *redirection* you can direct the input and output of a command to and from other files and programs, and chain commands together in a pipeline.

```bash
echo "Hello"
```

The `echo` command accepts the string “Hello” as *standard input*, and echoes the string “Hello” back to the terminal as *standard output*.

1. *standard input*, abbreviated as `stdin`, is information inputted into the terminal through the keyboard or input device.
2. *standard output*, abbreviated as `stdout`, is the information outputted after a process is run.
3. *standard error*, abbreviated as `stderr`, is an error message outputted by a failed process.

Redirection reroutes standard input, standard output, and standard error to or from a different location.

### >
`>` takes the standard output of the command on the left, and redirects it to the file on the right.

```bash
cat deserts.txt > forests.txt
```

Note that `>` overwrites all original content in **forests.txt**.

### >>
`>>` takes the standard output of the command on the left and *appends* (adds) it to the file on the right.

```bash
cat deserts.txt >> forests.txt
```

### <
`<` takes the standard input from the file on the right and inputs it into the command on the left. Here, **deserts.txt** is the standard input for the `cat` command.

```bash
cat < deserts.txt
```

### |
`|` is a “pipe.” The `|` takes the standard output of the command on the left, and pipes it as standard input to the command on the right. You can think of this as “command to command” redirection.

To count the words in **volcanoes.txt** using the word count command `wc`:

```bash
cat volcanoes.txt | wc
```

Multiple `|`s can be chained together.

```bash
cat volcanoes.txt | wc | cat > count.txt 
```

### sort
`sort` takes the standard input and orders it alphabetically for the standard output (it doesn’t change the file itself).

```bash
sort continents.txt 
```

### uniq
`uniq` stands for “unique.” It filters out adjacent, duplicate lines in a file.

```bash
uniq deserts.txt
```

A more effective way to use `uniq` is to call `sort` to alphabetize a file, and “pipe” the standard output to `uniq`. By piping `sort` **deserts.txt** to `uniq`, all duplicate lines are alphabetized (and thereby made adjacent) and filtered out.

```bash
sort deserts.txt | uniq
```

### grep I
`grep` stands for “global regular expression print.” It searches files for lines that match a pattern and then returns the results. It is also case sensitive.

```bash
grep America continents.txt 
```

`grep -i` enables the command to be case insensitive.

```bash
grep -i America continents.txt
```

Note that we don’t use quotes in our command.

### grep II
`grep -R` searches all files in a directory and outputs filenames and lines containing matched results. `-R` stands for “recursive”.

```bash
grep -R Arctic /home/ccuser/workspace/geography
```

`grep -Rl` searches all files in a directory and outputs only filenames with matched results (so no lines). `l` (a lowercase L, not a capital i) stands for “files with matches.”

```bash
grep -Rl Arctic /home/ccuser/workspace/geography
```

### sed
`sed` stands for “stream editor.” It accepts standard input and modifies it based on an expression, before displaying it as output data. It is similar to “find and replace.”

```bash
sed 's/snow/rain/' forests.txt 
```

- `s`: stands for “substitution.” It is always used when using sed for substitution.
- `snow`: the search string, or the text to find.
- `rain`: the replacement string, or the text to add in place.

Importantly, the above command will only replace the first instance of “snow” on a line.

```shell
sed 's/snow/rain/g' forests.txt 
```

The above command uses the `g` expression, meaning “global.” Here `sed` searches **forests.txt** for the word “snow” and replaces it with “rain” *globally*. This means *all* instances of “snow” on a line will be turned to “rain.”

`sed` as we’ve used it will only rewrite the command line output and the actual file won’t be changed. In order to rewrite the actual file, we need to use `-i` at the beginning of the command:

```shell
sed -i 's/snow/rain/g' forests.txt
```

### Review
- Redirection reroutes standard input, standard output, and standard error.
- The common redirection commands are:
	- `>` redirects standard output of a command to a file, overwriting previous content.
	- `>>` redirects standard output of a command to a file, appending new content to old content.
	- `<` redirects standard input to a command.
	- `|` redirects standard output of a command to another command.
- A number of other commands are powerful when combined with redirection commands:
	- `sort`: sorts lines of text alphabetically.
	- `uniq`: filters duplicate, adjacent lines of text.
	- `grep`: searches for a text pattern and outputs it.
	- `sed` : searches for a text pattern, modifies it, and outputs it.


# Configuring the Environment
## Environment

### Intro to Environment
Each time we launch the terminal application, it creates a new session. The session immediately loads settings and preferences that make up the command line *environment*.

### Nano
*nano* is a command line text editor.

### Customization with .bash_profile
A bash profile is a file used to store environment settings for your terminal. On most computer systems, the file is in the home directory and is accessible by the name **.bash_profile**.

When a session starts, it loads the contents of the bash profile before executing commands.

The name **.bash_profile** is important since this is how the command line recognizes the bash profile.

To activate the changes made in **.bash_profile** for the current session, use the following command:

```shell
source .bash_profile
```

This makes the changes in the bash profile available right away without closing the terminal and needing to start a new session.

### Aliases I
The `alias` command allows you to create keyboard shortcuts, or aliases, for commonly used commands.

```shell
alias pd="pwd"
```

### Aliases II
We can add as many aliases as we want in a bash profile.

### Environment Variables
*Environment variables* are variables that can be used across commands and programs and hold information about the environment.

```shell
export USER="Jane Doe"
```

The line `USER="Jane Doe"` sets the environment variable USER to a name “Jane Doe”.

The line `export` makes the variable to be available to all child sessions initiated from the session you are in. This is a way to make the variable persist across programs.

At the command line, the command `echo $USER` returns the value of the variable. Note that `$` is always used when returning a variable’s value. 

### PS1 Environment Variable
`PS1` is an environment variable that defines the makeup and style of the command prompt.

```shell
export PS1=">> "
```

Here we change the default command prompt from `$` to `>>`.

### HOME Environment Variable
The `HOME` variable is an environment variable that displays the path of the home directory `~`.

```shell
echo $HOME 
```

### PATH Environment Variable
`PATH` is an environment variable that stores a list of directories separated by a colon.

The `PATH` variable simply lists which directories contain scripts.

```shell
echo $PATH
```

### env
The `env` command stands for “environment,” and returns a list of the environment variables for the current user.

```shell
env
```

To select the value of a particular environment variable, let’s say `PATH`, you can use the following command:

```shell
env | grep PATH 
```

Note that this is the same output as `echo $PATH`.

### Review
- The *environment* refers to the preferences and settings of the current user.
- The *nano* editor is a command line text editor used to configure the environment.
- **.bash_profile** is where environment settings are stored. You can edit this file with nano.
- *Environment variables* are variables that can be used across commands and programs and hold information about the environment.
	- `export VARIABLE="Value"` sets and exports an environment variable.
	- `USER` is the name of the current user.
	- `PS1` is the command prompt.
	- `HOME` is the home directory. It is usually not customized.
	- `PATH` returns a colon : separated list of file paths. It is customized in advanced cases.
	- `env` returns a list of environment variables. You can redirect the output, using `grep` to select the variable you want to see.


# Cheatsheets

## Navigating the File System
![[command_line_navigating_the_file_system.pdf]]

## Viewing and Changing the File System
![[command_line_viewing_and_changing_the_file_system.pdf]]

## Redirecting Input and Output
![[command_line_redirecting_input_and_output.pdf]]

## Configuring the Environment
![[command_line_configuring_the_environment.pdf]]

