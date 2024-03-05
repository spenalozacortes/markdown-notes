#git #github
# Basic Git Workflow
## Basic Git Workflow

### Hello Git
Git is a software that allows you to keep track of changes made to a project over time. Git works by recording the changes you make to a project, storing those changes, then allowing you to reference them as needed.

### git init
The word `init` means *initialize*. The command sets up all the tools Git needs to begin tracking changes made to the project.

```bash
git init
```

### Git Workflow
A Git project can be thought of as having three parts:

1. A *Working Directory*: where you’ll be doing all the work: creating, editing, deleting and organizing files.
2. A *Staging Area*: where you’ll list changes you make to the working directory.
3. A *Repository*: where Git permanently stores those changes as different versions of the project.

The Git workflow consists of editing files in the working directory, adding files to the staging area, and saving changes to a Git repository. In Git, we save changes with a *commit*.

### git status
You will be changing the contents of the working directory. You can check the status of those changes with:

```bash
git status
```

*Untracked* means that Git sees the file but has not started tracking changes yet.

### git add
In order for Git to start tracking, the file needs to be added to the staging area.

We can add a file to the staging area with:

```bash
git add filename
```

### git diff
Since the file is tracked, we can check the differences between the working directory and the staging area with:

```bash
git diff filename
```

### git commit
A *commit* is the last step in our Git workflow. A commit permanently stores changes from the staging area inside the repository.

```shell
git commit -m "Complete first line of dialogue"
```

Standard Conventions for Commit Messages:

- Must be in quotation marks
- Written in the present tense
- Should be brief (50 characters or less) when using `-m`

### git log
Commits are stored chronologically in the repository and can be viewed with:

```shell
git log
```

### Review
- Git is the industry-standard version control system for web developers
- Use Git commands to help keep track of changes made to a project:
	- `git init` creates a new Git repository
	- `git status` inspects the contents of the working directory and staging area
	- `git add` adds files from the working directory to the staging area
	- `git diff` shows the difference between the working directory and the staging area
	- `git commit` permanently stores file changes from the staging area in the repository
	- `git log` shows a list of all previous commits


# Important Git Operations
## How to Backtrack

### head commit
In Git, the commit you are currently on is known as the `HEAD` commit. In many cases, the most recently made commit is the `HEAD` commit.

To see the `HEAD` commit, enter:

```shell
git show HEAD
```

The output of this command will display everything the git log command displays for the `HEAD` commit, plus all the file changes that were committed.

### git checkout
The command `checkout` will restore the file in your working directory to look exactly as it did when you last made a commit.

```shell
git checkout HEAD filename
```

### more git add
In Git, it’s common to change many files, add those files to the staging area, and commit them to a repository in a single commit.

```shell
git add filename_1 filename_2
```

### git reset I
We can *unstage* a file from the staging area using:

```shell
git reset HEAD filename
```

This command *resets* the file in the staging area to be the same as the `HEAD` commit. It does not discard file changes from the working directory, it just removes them from the staging area.

### git reset II
Git enables you to rewind to the part before you made the wrong turn.

```shell
git reset commit_SHA
```

This command works by using the first 7 characters of the SHA of a previous commit. For example, if the SHA of the previous commit is `5d692065cf51a2f50ea8e7b19b5a7ae512f633ba`, use:

```shell
git reset 5d69206
```

`HEAD` is now set to that previous commit.
### Review
- `git checkout HEAD filename`: Discards changes in the working directory.
- `git reset HEAD filename`: Unstages file changes in the staging area.
- `git reset commit_SHA`: Resets to a previous commit in your commit history.

## Handy Git Operations

### Git stash
Let’s say you’re working on experimental code on a fresh branch and realize that you forgot to add something to a previous commit in order to continue your work. In order to go to a different branch, one must always be at a clean commit point. In this case you don’t want to commit your experimental code since it’s not ready but you also don’t want to lose all the code you’ve been working on.

A good way to handle this is by using git stash, which allows you to get back to a clean commit point with a synchronized working tree, and avoid losing your local changes in the process. You’re “stashing” your local work temporarily in order to update a previous commit and later on retrieve your work.

While working on a file, you find a small bug in a separate file from a previous commit that needs to be fixed before you continue.

```shell
git stash
```

Running the command above will store your work temporarily for later use in a hidden directory.

At this point, you can switch branches and do work elsewhere.

Once the bug is fixed, you want to retrieve the code you were working on previously, you can “pop” the work that was stored when you used `git stash`.

```shell
git stash pop
```

From here, you can continue your work and commit it when ready.

### Git log
Shows the list of commits in one line format:

```shell
git log --oneline
```

Displays a list of commits that contain the keyword in the message:

```shell
git log -S "keyword"
```

Displays a visual representation of how the branches and commits were created in order to help you make sense of your repository history. When used alone, the description can be very lengthy, so you can combine the command with `--oneline` in order to shorten the description.

```shell
git log --oneline --graph
```

### Git commit amend
Git’s `--amend` flag is extremely useful when updating a commit, it allows you to correct mistakes and edit commits easily instead of creating a completely new one.

Let’s say you finish working on a lengthy feature and everything seems to be working fine so you commit your work. Shortly after, you realize you missed a few semicolons in one of your functions. You could technically create a new commit, but ideally, you want to keep all commits specific, clean, and succinct. To avoid creating a new one, you could create your changes, stage them with `git add` and then type the command `git commit --amend` to update your previous commit.

It’s important to note that although it seems like `--amend` is simply updating the commit, what Git actually does is replace the whole previous commit. For this reason, when you execute the command `git commit --amend`, your terminal editor asks you to update your commit message.

However, if you want to keep the same commit message, you can simply add the flag `--no-edit`.

```shell
git commit --amend --no-edit
```

### Git alias commands
When grouping commands together, you can end up writing very long lines of Git commands in the terminal.

If you have a set of commands that you use regularly and want to save some time from typing them, you can easily set up an alias for each command using Git config.

```shell
git config --global alias.co "checkout"
git config --global alias.br "branch"
git config --global alias.glop "log --pretty=format:"%h %s" --graph"
```

Once the aliases are configured, next time you want to check out to another branch you could type the command:

```shell
git co example_branch
```


# Introduction to GitHub
## The GitHub Flow

### Introduction
The basic workflow used with GitHub:

1. Create a branch
2. Commit changes
3. Create a pull request
4. Review pull request
5. Merge and delete branch

### Managing Branches
With Git, each teammate can create their own branch off of the main project in order to work on bug-fixes, new features, experimental code, etc.

A branch is essentially a divergence from the main project. ​​When you branch out, git is essentially making a new state of your current code, upon which you can work, without affecting the important main state of the code. One can create as many branches as they wish and even create branches off of other branches.

By using separate branches, the main project remains intact and unaffected before the changes are reviewed and merged into the project.

Each repository can have one or more branches. The `main` branch — the one where all changes eventually get merged back into, is called main. The `main` branch is usually the working version of a project and contains the production code, so it’s very important to only merge clean and correct code into it!

When someone wants to create a new feature, fix a bug, or just experiment, they should always create their own branch with a descriptive name.

### Adding and Committing Changes
You clone (download) the entire app repository from GitHub and create a branch for your feature of the `main` branch, and begin coding a new file in your local Git environment.

After testing your code and ensuring that everything is running correctly, it’s time to push those changes with a commit!

### Creating a Pull Request
Pull Requests on GitHub allow collaborators to review and give feedback on proposed code changes before they are merged to the main branch. Through a process of discussion and potentially some extra code changes, the pull request can be ultimately approved, which means you can merge the changes into the official project on the `main` branch.

### Reviewing and Merging a Pull Request
Once you’ve created a pull request, other members in your team can review it up on GitHub.

### Deleting a Branch 
Once changes are merged, in order to keep things organized and managed, it’s imperative to only keep active branches and delete the closed ones.


# GitHub & Markdown
## What is Markdown?

### Markdown Tutorial
Since there are six heading tags for HTML, from `<h1>` through `<h6>`, you can simulate this with # through ###### in Markdown.

```markdown
# This is a H1 heading
## This is a H2 heading
### This is a H3 heading
#### This is a H4 heading
##### This is a H5 heading
###### This is a H6 heading
```

There are three different symbols you can use to mark a line item as a bullet: asterisk (\*), plus sign (+), or hyphen (-).

```markdown
* Markdown
+ HTML
- XML
```

The core Markdown syntax does not include nested lists (list within another list), but it allows adding paragraphs between list items. To do so, you need to add a blank line after a list item and indent 4 spaces or 1 tab before starting a paragraph. Some parsers are lenient and do not enforce 4 spaces but there should be some spacing.

```markdown
* Markdown
 
   Markdown is a lightweight markup language for styling text.
 
* HTML
 
   HTML stands for HyperText Markup Language.
``` 
