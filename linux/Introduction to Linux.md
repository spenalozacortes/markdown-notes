# What is Linux?
## What is Linux?

### Introduction to Linux
Linux runs on over 95% of web servers. Today, Linux runs 85% of smartphones (Android is built on top of the Linux kernel).

### Unix history
To understand how Linux came to be, we must look back to the early days in computing, when Ken Thompson and Dennis Ritchie of Bell Laboratories began working on UNIX, the first ever portable operating system. The year was 1969. UNIX could run on a range of devices and was widely used as proprietary software. Then, Richard Stallman started the *GNU Project* in 1983 with goals to create a free operating system. At the time, the free software movement was advocating for the freedom for users to modify and share copies of software. The project created the GNU General Public License (GPL), a widely used free software license, which set the background for the Linux operating system.

In 1991 there was not yet a free operating system, so a Finnish computer science student named Linus Torvalds began developing an operating system as a hobby. He released the code under GPL and slowly, the community around Linux grew as more and more developers contributed to the base code.

Today, Linux refers to the many versions of operating systems built on top of the base code. This means anyone can create their own version of a Linux operating system!

### Open Source Software
Open-source software is software with source code that anybody can look at or contribute to and distribute based on the terms of the license. It grew out of the Free Software Movement which guarantees certain freedoms to software users. The two movements overlap significantly and the terms are often used interchangeably, but they are respectively defined by the non-profit organizations, Open Source Initiative and the Free Software Foundation.

The Free Software Foundation first published the GNU Public License (GPL) in 1989. The GPL is a copyleft (as opposed to copyright) license, which means that any derivative software must be distributed under the same or equivalent license terms. Linus Torvalds released the Linux operating system under GPL license in 1992. This non-proprietary way of sharing code has since been described as a “defining factor of Linux’s success” as more and more developers began to contribute to the project. Over time, a rich Linux eco-system with different versions (called *distributions* ) of the operating system and many open-source applications has developed.

### OS vs Linux Kernel vs Shell
First, let’s explain what an operating system is. It is a system program that provides an interface between the user and the hardware. When a computer boots up, the operating system is the first program that loads and manages all of the other application programs on a computer.

The *kernel* is the most important part of the operating system. It performs a variety of tasks:

- process management
- managing hardware devices
- task scheduling

The kernel controls all the major functions of the hardware, whether it’s a phone, laptop, or server. When we talked about what Linus Torvalds first published in 1991, it was the kernel.

The *shell* is the interface between the user and kernel. At its barest, it is a command-line interpreter where a user can enter commands which are interpreted by the computer to perform a certain task. In Linux, the shell language is called Bash.

### What's in a Linux distribution?
Linux refers to the family of operating systems based on the Linux kernel and each operating system is packaged as a *distribution*, or *distro*, of Linux. A Linux distribution is made from a software collection including the Linux kernel, GNU tools, and default software.

Here is a short list of some of the most popular distributions:

- *Debian* is one of the oldest distributions of Linux, first developed in 1993. It is a stable Linux operating system, and software updates are frequent but small.
- *Ubuntu* is the most popular distribution of Linux and is based on Debian Linux. It’s widely used and supported and looks most like other operating systems like OSX and Windows in terms of usability.
- *Linux Mint* is a distribution that is based off of Ubuntu that comes with less pre-installed software than Ubuntu.
- *Red Hat Enterprise Linux* , also known as RHEL, is a distribution of Linux developed by Red Hat. It has strict rules around its trademark which prevent free distribution, but it is mostly used in enterprise environments on servers.
- *Fedora* is an open-source community-driven distribution of Linux that is backed by Red Hat. Think of it as the Ubuntu equivalent to Red Hat.
- *Arch* is a rolling release distribution of Linux that is 100% developed by its community. It has a steeper learning curve than other distributions but it is a great lightweight distribution of Linux.


# Introduction to Operating Systems
## How Computers Work

### Processing
Once we have some data, we need to process it so that our computer can figure out what we’re asking it to do and how to execute those requests. The job of processing information is given to the central processing unit, or CPU.

The CPU controls all the different components between hardware and software. We can think of it as the “brain” of the computer! The CPU also holds the responsibility of establishing communication between hardware and software.

### Memory
Computer memory refers to the system or device used to store computer-based data temporarily or permanently.

#### Primary Memory
When a command to run a program is sent to the CPU, the CPU retrieves data from Random Access Memory, or RAM, in order to access what instructions it needs to execute. Accessing data from RAM is significantly faster than accessing data from other memory systems.

This type of data is also only stored temporarily; once we exit a program or turn off the computer, the data is lost.

#### Secondary Memory
If we upload 150 photos to our computer, the computer needs a space to permanently store the data associated with the images so that we could access the pictures anytime. This type of data would most likely be saved onto our computer’s hard drive.

### Review
- Input is data we give to our computers
- Processing is comprised of the translation of input and the instructions given for output
- Memory is used to store either temporary or permanent information
- Output is the information that gets returned by the computer


## Basics of Operating Systems

### What is an operating system?
An Operating System, or OS, is system software that’s responsible for handling the basic functionalities of a computer. Some examples of popular OSs are:

- Windows
- Linux
- Mac
- Android
- iOS

Every computer contains at least one operating system which starts working the moment a computer is turned on. The OS has control over both the software and hardware resources of a computer. At the core of an operating system is the *kernel* which manages all the interactions between the hardware and software components of a computer.

### Functions of an OS
- Process Management
- Memory Management
- File Management
- IO Management
- Multitasking
- Networking
- Security
- Providing a user interface

#### Process Management
When we run a program, the instance of that execution is represented by a process. Operating systems handle the responsibility of managing active processes.

#### Memory Management
We utilize a significant amount of memory in order to store data in our computers; however, not all data is treated the same! Some data, like pictures, need to be stored permanently. Other data, like the information we need to run a process, only needs to be stored temporarily while the application is in use. This temporary memory is known as primary, or main, memory. While hardware like hard disks are used to store permanent data, the operating system is responsible for the management of primary memory stored in RAM.

#### File System Management
The operating system manages information about individual files as well as the directories they belong in. The OS is also responsible for maintaining file systems by being able to perform tasks such as creating, deleting, renaming, and copying files and/or directories.

#### IO Management
IO stands for Input/Output and represents the devices used for interaction. The operating system plays a large role in managing IO by ensuring communication between IO hardware and IO software.

### Review
- The operating system (OS) is system software that manages the basic functionalities of a computer.
- Every computer has at least one operating system. The operating system starts running as soon as a computer is turned on.
- Some of the tasks that an OS is responsible for are process management, memory management, file system management, and IO management.


# Features of the Linux Desktop Environment
## The Linux Filesystem

### Linux Filesystem
Linux OS’s have a secure, multi-user filesystem. Its directory structure is organized to maintain a good balance between security and functionality. Directories accessible to the user are separated from directories needed by the administrator.

Linux generally follows the Filesystem Hierarchy Standard (FHS). This standard reference (developed in 1994) describes the common layout conventions used by most UNIX and UNIX variant systems. It consists of a single primary (or root) directory with multiple branching sub-directories.

#### Root Directory ( / )
The root directory / is the starting point for the entire Linux filesystem hierarchical tree. It is the top-most directory from which all other file systems are mounted at system boot up. All files and folders will branch from the root directory even if the data is stored in different places physically.

The root directory is owned by the root user (admin) and its permissions are tightly controlled to allow only administrators to add, remove, or modify files and folders in this directory.

#### Sub-Directories
By convention, Linux has several important sub-directories, each with its own specific purpose and permissions. Some of these sub-directories are accessible to anyone (i.e. **/tmp**) while others are only accessible to the administrator (i.e. **/etc**).

SUB-DIRECTORY | PURPOSE
--- | ---
/bin	| common binary executables used by all users
/boot	| files associated with boot loader
/dev	| attached devices (usb, cdrom, mouse, keyboard)
/etc	| configuration files
/home	| personal directories for each user account
/lib	| shared system libraries
/media	| directory for mounting removable devices (floppy drive, cdrom)
/mnt	| directory for mounting filesystems (nfs, smb)
/opt	| optional vendor add-on software
/proc	| virtual filesystem for system processes/resources information
/root	| home directory for administrator account
/run	| storage for runtime information
/sbin	| binary executables used by administrator
/srv	| data for server services
/sys	| virtual filesystem for hardware/driver information
/tmp	| temporary files purged on reboot
/usr	| utilities and read-only user data/programs
/var	| variable and log files

### Linux versus Other Filesystems (macOS and Windows)

#### Coming from Windows
In contrast to Windows’ single-user system, Linux has a multi-user design. While Windows uses separate data drives like `C:\WINDOWS` and `D:\DATA`, Linux uses a tree-like hierarchy structure with everything branching off of the root. On Windows, program and system files are saved in the same path (`C:\Program Files`) and application files are kept in `C:\Program Files\Application`. In Linux, the program, system, and application files are all separated (i.e. /bin, /boot, /usr/bin).

#### Coming from macOS
Apple’s macOS owes its heritage to Unix and BSD operating systems so its core file structure is similar to Linux. Like Linux’s file structure, it too has a single primary directory with all sub-directories branching of the root (/) directory.


# Linux Bash Utilities
## Linux Shell Utilities

### Access Documentation in Linux
We can access documentation in the terminal itself using these files and commands:

- The `/usr/share/doc/` directory
- The `man` command
- The `info` command

The `/usr/share/doc/` directory contains README files, simple text files that describe a program, for many installed packages in your Linux distribution. You can explore the documentation available there using the command below.

```bash
ls /usr/share/doc
```

The `man` command is used to access the manual pages, the traditional way of distributing documentation for all bash programs.

```
man [options] <command_name>
```

```bash
man cat
```

For full and detailed documentation, we can use the `info` command which also contains more recent information about programs than `man`. 

```
info [options] <command_name>
```

```bash
info cat
```

### Compression Utilities
Three popular compression commands are:

- `gzip`: retains the original file’s ownership modes, access, and modification timestamps. Compressed files have the .gz extension.
- `bzip2`: compressed files have the .bz2 extension.
- `xz`: compressed files have the .xz extension.

```
<compression_utility> [options] <file_name>
```

### Archive Utilities
Archiving allows us to consolidate multiple files or directories into a single archived file. Two of the popular archive commands on Linux, `zip` and `tar`, have the ability to compress and archive files. 

#### zip

```
zip <archive_name>.zip <file1> <file2> …
```

Directories can be easily archived with the `-r` option. Archived files can be extracted and decompressed using the `unzip` command and providing paths to one or more .zipfiles.

#### tar
While a `zip` archive is more popular across platforms, it is recommended to use `tar` when distributing archives among Linux-based systems. This is because tar archives store Unix file attributes, retaining file permissions and other metadata.

```
tar -cf <archive_name>.tar <files or directories>
```

creates an *uncompressed* .tar archive. A .tar file can be referred to as a tarball.

```bash
tar -cf example.tar index.html script.js style.css
```

To extract the files in a .tar archive, we can use the `-xf` option.

```
tar -xf <archive_name>.tar
```

### Compressing .tar Files
- `-z` : Compress the resulting archive using gzip. Resulting file extension: .tar.gz.
- `-j` : Compress the resulting archive using bzip2. Resulting file extension: .tar.bz2.
- `-J` : Compress the resulting archive using xz. Resulting file extension: .tar.xz.

```bash
tar -cjf videos.tar.bz2 video1.mp4 video2.mkv
```

Make sure the extension of the archive name corresponds with the compression option.

#### Decompressing and Extracting .tar Files
To extract and decompress a compressed .tar archive, we change the option `-c` to `-x`:

```bash
tar -xjf videos.tar.bz2
```

### Network Utilities

#### Interacting with Files Hosted Online
There are two commands that allow us to do just that: `curl` and `wget`. Either command lets us establish a connection with a server. We can also use them to download the file at the destination.

```
curl <URL in quotes>
```

displays the contents of the file at the URL in terminal.

The option `-o` or `-output` combined with a desired name

```
curl <URL> --output <desired_filename>
```

lets us write the contents of the online file to the filename.

```bash
curl -O "https://www.google.com" --output frontpage.html
```

#### Checking Network Connectivity
How can we check whether two devices connected to the same network can communicate with one another? We use a command called `ping`, short for Packet INternet Groper. The command

```
ping [options] <target domain or IP>
```

sends packets to the target host and waits for replies. If the `ping` command returns with a failure, that means the target is unreachable.

#### DNS Resolution
What if we wanted to find out the IP address for any given domain name or vice versa? This process is known as DNS lookup or DNS resolution and the `host` command lets us do exactly that. The basic syntax for the host command is: `host <domain or IP>`.

#### Network Interface Status
The `ifconfig` command, or interface configurator, is one of the network inspection commands available on Linux. Running it will display IP addresses, MAC addresses, and some more relevant details.

### Review

#### Documentation
Documentation is a great way to learn about installed utilities.

- The `/usr/share/doc/` directory contains README files and other documents for installed commands.
- `man` is a command to access reference manual pages for all installed commands. Usage: `man <command_name>`.
- `info` is a command to access full-detailed information pages for all installed commands. Usage: `info <command_name>`.

#### Compression
Compression reduces file sizes. Three popular compression commands are `gzip`, `bzip2`, and `xz`. To compress, run commands like so: `<compression_utility> [options] <file_name>`. To decompress, include the `-d` option: `<compression_utility> -d <compressed_file_name>`. `gzip` also supports the `-r` option to compress all files in a directory.

#### Archive
`zip` and `tar` are two archiving utilities that package multiple files into a single archive file. `zip`: archives and compresses files.

- Archive: `zip <archive_name>.zip <file1> <file2>`... Use `-r` option for directories.
- Extract: `unzip <archive_name>.zip`.

`tar`: only archives files by default but has options to utilize compression utilities. Unlike `zip`, it preserves Unix file attributes like file permissions.

- Archive: `tar -cf <archive_name>.tar <files or directory>`.
- Extract: `tar -xf <archive_name>.tar`.
- Add options `-z`, `-j`, or `-J` to compress via `gzip`, `bzip2`, or `xz` respectively.

#### Networking
Basic network commands:

- `curl` or `wget`: Interacts with a webpage or file hosted online.
- `ping <target domain or IP>`: Checks connectivity between two devices on the same network.
- `host <domain or IP>`: Performs DNS lookups.
- `ifconfig`: Shows network interface information.


# Bash Scripting
## Learn Bash Scripting

### Introduction to Bash Scripting
Bash (or shell) scripting is a great way to automate repetitive tasks and can save you a ton of time as a developer. Bash scripts execute within a Bash shell interpreter terminal. Any command you can run in your terminal can be run in a Bash script. When you have a command or set of commands that you will be using frequently, consider writing a Bash script to perform it.

There are some conventions to follow to ensure that your computer is able to find and execute your Bash scripts. The beginning of your script file should start with `#!/bin/bash` on its own line. This tells the computer which type of interpreter to use for the script. When saving the script file, it is good practice to place commonly used scripts in the `~/bin/` directory.

The script files also need to have the “execute” permission to allow them to be run. To add this permission to a file with filename **script.sh** use:

```bash
chmod +x script.sh
```

Your terminal runs a file every time it is opened to load its configuration. On Linux style shells, this is `~/.bashrc` and on OSX, this is `~/.bash_profile`. To ensure that scripts in `~/bin/` are available, you must add this directory to your `PATH` within your configuration file: `PATH=~/bin:$PATH`

Now any scripts in the `~/bin` directory can be run from anywhere by typing the filename.

### Variables
Within bash scripts (or the terminal for that matter), variables are declared by setting the variable name equal to another value.

```bash
greeting="Hello"
```

Note that there is no space between the variable name, the equals sign, or “Hello”.

To access the value of a variable, we use the variable name prepended with a dollar sign (`$`).

```bash
echo $greeting
```

### Conditionals
When bash scripting, you can use conditionals to control which set of commands within the script run. Use `if` to start the conditional, followed by the condition in square brackets (`[ ]`). Make sure you leave a space between a bracket and the conditional statement! `then` begins the code that will run if the condition is met. `else` begins the code that will run if the condition is not met. Lastly, the conditional is closed with a backwards `if`, `fi`.

```bash
if [ $index -lt 5 ]
then
  echo $index
else
  echo 5
fi
```

Bash scripts use a specific list of operators for comparison:

- Equal: `-eq`
- Not equal: `-ne`
- Less than or equal: `-le`
- Less than: `-lt`
- Greater than or equal: `-ge`
- Greater than: `-gt`
- Is null: `-z`

When comparing strings, it is best practice to put the variable into quotes (`"`). This prevents errors if the variable is null or contains spaces. The common operators for comparing strings are:

- Equal: `==`
- Not equal: `!=`

```bash
if [ "$foo" == "$bar" ]
```

### Loops
There are 3 different ways to loop within a bash script: `for`, `while` and `until`.

A for loop is used to iterate through a list and execute an action at each step.

```bash
for word in $paragraph
do
  echo $word
done
```

Note that `word` is being “defined” at the top of the for loop so there is no `$` prepended.

Within bash scripting `until` and `while` are very similar. `while` loops keep looping while the provided condition is true whereas `until` loops loop until the condition is true. Conditions are established the same way as they are within an `if` block, between square brackets.

```bash
while [ $index -lt 5 ]
do
  echo $index
  index=$((index + 1))
done
```

Note that arithmetic in bash scripting uses the `$((...))` syntax and within the brackets the variable name is not prepended with a `$`.

The same loop could also be written as an `until` loop as follows:

```bash
until [ $index -eq 5 ]
do
  echo $index
  index=$((index + 1))
done
```

### Inputs
To make bash scripts more useful, we need to be able to access data external to the bash script file itself. The first way to do this is by prompting the user for input. For this, we use the `read` syntax. 

```bash
echo "Guess a number"
read number
echo "You guessed $number"
```

The command `read` can be used to split a string into an array using the `-a` argument. The syntax for splitting a string `foo` into an array `bar` is:

```bash
read -a bar <<< $foo
```

The syntax for accessing the value at `index` of an array `foo` is:

```bash
${foo[index]}
```

Another way to access external data is to have the user add input arguments when they run your script. These arguments are entered after the script name and are separated by spaces.

```bash
saycolors red green blue
```

Within the script, these are accessed using `$1`, `$2`, etc, where `$1` is the first argument (here, “red”) and so on. Note that these are 1 indexed.

If your script needs to accept an indefinite number of input arguments, you can iterate over them using the "`$@`" syntax.

```bash
for color in "$@"
do
  echo $color
done
```

Lastly, we can access external files to our script. You can assign a set of files to a variable name using standard bash pattern matching using regular expressions. For example, to get all files in a directory, you can use the `*` character:

```bash
files=/some/directory/*
```

You can then iterate through each file and do something. Here, lets just print the full path and filename:

```bash
for file in $files
do
  echo $file
done
```

### Aliases
You can set up aliases for your bash scripts within your .**bashrc** or **.bash_profile** file to allow calling your scripts without the full filename. For example, if we have our **saycolors.sh** script, we can alias it to the word **saycolors** using the following syntax:

```bash
alias saycolors='./saycolors.sh'
```

You can even add standard input arguments to your alias. For example, if we always want “green” to be included as the first input to **saycolors**, we could modify our alias to:

```bash
alias saycolors='./saycolors.sh "green"'
```

### Review
- Any command that can be run in the terminal can be run in a bash script.
- Variables are assigned using an equals sign with no space (`greeting="hello"`).
- Variables are accessed using a dollar sign (`echo $greeting`).
- Conditionals use `if`, `then`, `else`, `fi` syntax.
- Three types of loops can be used: `for`, `while`, and `until`.
- Bash scripts use a unique set of comparison operators:
	- Equal: `-eq`
	- Not equal: `-ne`
	- Less than or equal: `-le`
	- Less than: `-lt`
	- Greater than or equal: `-ge`
	- Greater than: `-gt`
	- Is null: `-z`
- Input arguments can be passed to a bash script after the script name, separated by spaces (`myScript.sh “hello” “how are you”`).
- Input can be requested from the script user with the `read` keyword.
- Aliases can be created in the **.bashrc** or **.bash_profile** using the `alias` keyword.

### Project: Build a Build Script
One common use of bash scripts is for releasing a “build” of your source code. Sometimes your private source code may contain developer resources or private information that you don’t want to release in the published version.

In this project, you’ll create a release script to copy certain files from a **source** directory into a **build** directory.

```bash
#!/bin/bash
echo "Hello!"

firstline=$(head -n 1 source/changelog.md)
read -a splitfirstline <<< $firstline
version=${splitfirstline[1]}
echo "You are building version $version"

echo "Do you want to continue? (enter 1 for yes, 0 for no)"
read versioncontinue

if [ $versioncontinue -eq 1 ]
then
  for filename in source/*
  do
    if [ "$filename" == "source/secretinfo.md" ]
    then
      echo "Not copying" $filename
    else
      echo "Copying" $filename
      cp $filename build
    fi
  done
  cd build
  echo "Build version $version contains:"
  ls 
  cd ..
else
  echo "Please come back when you are ready"
fi
```


# Linux Users & Permissions
## Users, Groups, and Permissions in Linux

### Introduction
Linux is designed from the ground up to prevent individual users from accessing areas of the file structure they shouldn’t access. Linux environment administrators have to define separate accounts and permissions to determine who can access specific files, directories, applications, and resources.

### Types of Linux Users
Linux is a highly secure operating system that depends on strict file permissions dictating which users and groups can access them.

#### Admin or Non-admin?
A Linux user is either an administrator or non-administrator. The administrator is a superuser (or root user) with full control over the entire system. With that in mind, it is important to ensure that only a very limited number of folks have read and write permissions on all the files in the entire system. In contrast, a non-administrator by default has limited (or no) access to certain system/configuration files.

#### Normal user
A majority of the accounts will be non-administrators. These users can be divided into two subtypes: normal user or system user. Normal users are real people. The individual is given a user account for login and limited access to computer applications, files, and resources.

#### System user
A system user is typically a non-human or computer-generated account. System users are created to run a specific program or process/daemon such as a web server or backup program. This type of “user” is limited in control and is assigned only enough access to manage its particular process.

### Users and Groups in Linux
On a Linux system, all users added are assigned a name, unique user identification (UID), group, and group identification (GID). When a user is initially created, a new UID and matching GID are assigned.

UID and matching GID numbers are assigned based on the type of user:

- Administrator (root): UID and GID = 0
- System user (computer-generated): UID and GID assigned from 1 to 999
- Normal users (real people): UID and GID = 1000 or greater, incremented with every new user

The new user is by default assigned a matching group name (and typically a matching GID) so that the user will be a member of their own group. For example, a user **stephen** (UID = 1000) will also be assigned to the group **stephen** (GID = 1000).

We can create groups and add users to them. Users can also exist in more than one group as well.

We can use the `id` and `groups` commands in the terminal to check our `uid` and `gid`.

Admin users can also view and modify the user and group information stored in the read-only **/etc/passwd** and **/etc/group** files.

### File Permissions in Linux
In Linux, everything is based on file permissions. Each file or directory has an owner and a group (or groups) that usually has more permissions to read, write, or execute than users not in the owner or in the permission group.

```
-rw-rw-r--
```

The first character identifies the resource as either a directory (`d`) or file (`-`).

The following nine characters should actually be read as triplets: `rw-` for the file owner, `rw-` for the group(s) that have permission to the file, and `r--` for all others.

- read (`r`) = contents can be viewed but not edited, renamed, added, or deleted
- write (`w`) = contents can be viewed, edited, renamed, added, and deleted
- execute (`x`) = contents can run as a program or script
- (`-`) = permissions don’t apply

Read-write-execute permissions can also be written as numbers, with each being a power of two. Each set of triplets can be expressed as the sum of the permissions that apply.

PERMISSION | NUMBER | LETTER
--- | --- | ---
read | 4 | r
write | 2 | w
execute | 1 | x

For example, a file’s permission being `777` is equivalent to `rwxrwxrwx`, whereas a file’s permission being `755` is equivalent to `rwxr-xr-x`.

#### Default Permissions
When a normal user creates a folder, the default owner for the user and group is set to the username. The default permissions are typically set to 755 (or “rwx” for the user, “rx” for the group, and “rx” for others). These defaults are designed to restrict access until deliberately granted!

When a user then creates a file inside the folder, the default owner for the user and group is again set to the username while the permissions for that file are set to 644 (or “rw” for the user, “r” for the group, and “r” for others).

Use the `chmod` command to update permissions for the user, group, and others.

### Elevating Privileges (sudo)
Good security practices suggest that administrator/root access be limited. Typical day-to-day activities such as word processing, web browsing, or listening to music should never be done using the administrator account.

However, there are times when an administrator account is required to perform specific tasks, like adding and modifying permissions and configuring system software.

The Linux shell has the `sudo` command that can temporarily elevate privileges to a user that is a member of the administrator group.

```bash
sudo chown debbie sketches.ppt
```

### Modifying Users, Groups, and Permissions
Linux provides users the ability to elevate or relax access permissions on any files where they are an owner. Of course, an administrator can make changes anywhere in the system, including creating users and groups, modifying them, and elevating or reducing any permissions for files.

#### Adding and Modifying Users and Groups
- `useradd` creates a new user
- `groupadd` creates a new group
- `usermod` and `groupmod` can be used to modify users and groups
- `userdel` and `groupdel` can be used to delete users and groups.

#### Modifying Owners and Permissions
`chown` and `chgrp` allow the superuser/admin to change who owns the resource, file, or directory while `chmod` changes the read-write-execute permission levels.

```bash
chown peter designs.doc
chmod 777 designs.doc
chmod u=rwx,g=rwx,o=rwx designs.doc
```

Note: We need to be the owner of the file or admin to use `chmod`.

#### Viewing and Modifying Permissions Outside of the Terminal
We can view and modify permissions in the file manager application on a Linux Ubuntu desktop as well. Just right-click on the file, select properties from the drop-down, and choose the permissions tab. All the users/groups and permissions are easily selected from the drop-down menus.
