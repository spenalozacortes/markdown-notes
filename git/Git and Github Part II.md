# Git Branching
## Git Branching

### git branch
Up to this point, you’ve practiced in a single Git branch.

Git allows us to create _branches_ to experiment with versions of a project. Imagine you want to create a version of a story with a happy ending. You can create a new branch and make the happy ending changes to that branch only. It will have no effect on the `master` branch until you’re ready to merge the happy ending to the master branch.

You can use the command below to answer the question: “which branch am I on?”

```shell
git branch
```

--- 

In the output, the `*` (asterisk) is showing you what branch you’re on.

---

Right now, the Git project has only one branch: `master`.

To create a new branch, use:

```shell
git branch new_branch
```

Be sure to name your branch something that describes the purpose of the branch. Also, branch names can’t contain whitespaces: `new-branch` and `new_branch` are valid branch names, but `new branch` is not.

### git checkout
You can switch to the new branch with

```shell
git checkout branch_name
```

Once you switch branches, you will now be able to make commits on the branch that have no impact on `master`.

### commit on a new branch
You have switched to a new branch. All the commands you do on `master`, you can also do on this branch.

### git merge
What if you wanted to include all the changes made to the `fencing` branch on the `master` branch? We can easily accomplish this by _merging_ the branch into master with:

```shell
git merge branch_name
```

---

The merge is a “fast forward” because Git recognizes that `fencing` contains the most recent commit. Git _fast forwards_ `master` to be up to date with `fencing`.

### merge conflict
The merge was successful because `master` had not changed since we made a commit on `fencing`. Git knew to simply update `master` with changes on `fencing`.

What would happen if you made a commit on `master` _before_ you merged the two branches? Furthermore, what if the commit you made on `master` altered the same exact text you worked on in `fencing`? When you switch back to `master` and ask Git to merge the two branches, Git doesn’t know which changes you want to keep. This is called a _merge conflict_.

Let’s say you decide you’d like to merge the changes from `fencing` into `master`.

Here’s where the trouble begins!

You’ve made commits on separate branches that alter the same line in conflicting ways. Now, when you try to merge `fencing` into `master`, Git will not know which version of the file to keep.

----

Delete the content of the line as it appears in the `master` branch

Delete **all of Git’s special markings** including the words `HEAD` and `fencing`. If any of Git’s markings remain, for example, `>>>>>>>` and `=======`, the conflict remains.

### delete branch
In Git, branches are usually a means to an end. You create them to work on a new project feature, but the end goal is to merge that feature into the `master` branch. After the branch has been integrated into `master`, it has served its purpose and can be deleted.

The command will delete the specified branch from your Git project.

```shell
git branch -d branch_name
```

### Review
- Git _branching_ allows users to experiment with different versions of a project by checking out separate _branches_ to work on.

The following commands are useful in the Git branch workflow.

- `git branch`: Lists all a Git project’s branches.
- `git branch branch_name`: Creates a new branch.
- `git checkout branch_name`: Used to switch from one branch to another.
- `git merge branch_name`: Used to join file changes from one branch to another.
- `git branch -d branch_name`: Deletes the branch specified.

---

You’ll need the `-D` option, because these feature branches were never merged into `master`:

```shell
git branch -D branchname
```
 

# Git Teamwork
## Git Teamwork

### Overview
A *remote* is a shared Git repository that allows multiple collaborators to work on the same Git project from different locations. Collaborators work on the project independently, and merge changes together when they are ready to do so.

### git clone
Sally has created the remote repository, **science-quizzes** in the directory **curriculum**, which teachers on the school’s shared network have access to. In order to get your own replica of **science-quizzes**, you’ll need to _clone_ it with:

```shell
git clone remote_location clone_name
```

In this command:  

- `remote_location` tells Git where to go to find the remote. This could be a web address, or a filepath, such as:

```
/Users/teachers/Documents/some-remote
```

- `clone_name` is the name you give to the directory in which Git will clone the repository.

### git remote -v
One thing that Git does behind the scenes when you clone **science-quizzes** is give the remote address the name _origin_, so that you can refer to it more conveniently.

You can see a list of a Git project’s remotes with the command:

```shell
git remote -v
```

--- 

- Git lists the name of the remote, `origin`, as well as its location.
- Git automatically names this remote `origin`, because it refers to the remote repository of origin. However, it is possible to safely change its name.
- The remote is listed twice: once for `(fetch)` and once for `(push)`.

### git fetch
An easy way to see if changes have been made to the remote and bring the changes down to your local copy is with:

```shell
git fetch
```

This command will not _merge_ changes from the remote into your local repository. It brings those changes onto what’s called a _remote branch_.

### git merge
Even though Sally’s new commits have been fetched to your local copy of the Git project, those commits are on the `origin/master` branch. Your _local_ `master` branch has not been updated yet, so you can’t view or make changes to any of the work she has added.

Now we’ll use the `git merge` command to integrate `origin/master` into your local `master` branch.

```shell
git merge origin/master
```

### Git workflow
The workflow for Git collaborations typically follows this order:

1. Fetch and merge changes from the remote
2. Create a branch to work on a new project feature
3. Develop the feature on your branch and commit your work
4. Fetch and merge from the remote again (in case new commits were made while you were working)
5. _Push_ your branch up to the remote for review

Steps 1 and 4 are a safeguard against _merge conflicts_, which occur when two branches contain file changes that cannot be merged with the `git merge` command.

### git push
The command will push your branch up to the remote, `origin`.

```shell
git push origin <your_branch_name>
```

### Generalizations
- A _remote_ is a Git repository that lives _outside_ your Git project folder. Remotes can live on the web, on a shared network or even in a separate folder on your local computer.
- The _Git Collaborative Workflow_ are steps that enable smooth project development when multiple collaborators are working on the same Git project.

We also learned the following commands

- `git clone`: Creates a local copy of a remote.
- `git remote -v`: Lists a Git project’s remotes.
- `git fetch`: Fetches work from the remote into the local copy.
- `git merge origin/master`: Merges `origin/master` into your local branch.
- `git push origin <branch_name>`: Pushes a local branch to the `origin` remote.

Git projects are usually managed on Github, a website that hosts Git projects for millions of users. With Github you can access your projects from anywhere in the world by using the basic workflow you learned here.


# Best Practices for GitHub Repositories

## How To Write a Good Pull Request

### What Is a Pull Request?
A [pull request](https://docs.github.com/en/github/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) is a feature of GitHub and other source code management tools to review code before merging it from one branch to another, usually the main branch.

When Sonia creates a new pull request, her repository will automatically be set as the source repository and the project’s repository will be set as the destination repository. She will get the option to specify the source branch and the destination branch. She will be greeted with a preview of the changes between the two codebases and whether the branches can be merged automatically depending on code conflicts. In the Pull Request description field, Sonia must describe the code changes and what feature(s) this merge will add to the main branch.

Sonia’s proposed changes can then be accepted or rejected by her teammates. Each pull request has its own discussion forum, creating a place for collaborators to leave feedback. They will review Sonia’s code, suggest what should be removed or changed, and how her code can be simplified or improved. Any further commits Sonia makes to the source branch will automatically be reflected in the pull request. Once her changes are accepted by the project’s collaborators, her branch can be merged into the repository’s main branch. GitHub will keep this pull request in history as a record of the code change, Sonia’s contribution, and the discussion that took place.

This pull request process is not only a way to increase group knowledge or improve product quality but also an exceptional way to develop professional skills through group critique.

### How To Make a Good Pull Request

#### Follow a Pull Request Structure – What, Why, and How?
Concisely explain the purpose of the pull request in the title. If the pull request adds a new feature, go for something like “Add frontend component for settings page”. If it’s to fix a typo, be specific and say “Fix name typos on the Contact Us page”.

The description is where all the juicy details are. You want the reviewers to know the thought process behind code changes and the options you have considered. It also helps to embed screenshots, GIFs, or even videos of your application so reviewers can anticipate what the code change in the pull request looks like.

Some developers even have preconfigured templates or checklists on their repositories to ensure all pull requests contain just the relevant information.

#### Make Commit Messages Clear and Use Comments
Even having self-explanatory commit messages and comments in the code makes reviewers’ jobs much easier. Consider the commit message, “OMG! It finally worked” versus the message, “Fix typos: add missing @ symbols in emails”. Moreover, adding comments in the code is always a good practice to help other developers understand the function of specific lines. It helps the reviewer in this case!

One feature of GitHub pull requests on the web interface is the ability to add discussion comments to any single line of code or chunk of code. This allows separation of concerns over multiple discussions.

#### Keep Pull Requests Small and Fast
Reduce the size of pull requests and respond to reviews quickly. Splitting big features into smaller parts is the best way to speed up review time. Not only does it result in less wasted work if the pull request gets rejected, but it will be easier to merge and review more thoroughly. Quickly respond to any feedback or requested changes. You want to ship code fast and make sure reviewers aren’t stuck discussing an open pull request for ages!


## How To Use Git Rebase

### What is Git Rebase?
At a high level, rebasing can be understood as “moving the base of a branch onto a different position”. Think of it like a redo — “I meant to start here.”

Consider that a team just completed a production release. While working on a completely new feature branch called `new_feature`, a co-worker finds a bug in the production release (`main` branch). In order to fix this, a team member creates a `quick_fix` branch, squashes the bug, and merges their code in to the `main` branch. At this point, the `main` branch and the `new_feature` branch have diverged and they each have a different commit history.

![[Pasted image 20230616124601.png]]

If we want to bring the updated changes from `main` into `new_feature` one could use the `merge` command, but with `rebase` we can keep the Git commit history clean and easy to follow. By “rebasing” the `new_feature` branch onto the `main` one, we move all the changes made from `new_feature` to the front of `main` and incorporate the new commits by rewriting its history.

![[Pasted image 20230616124649.png]]

We can see above that the new “base” of our `new_feature` branch is the updated `main` branch with the previous changes from the bug fix implemented.

One of the major benefits of using Git rebase is that it eliminates unnecessary merge commits required by `git merge`. Most importantly, the history of the changes made in the main repository remains linear and follows a clear path of changes. This allows us to navigate the changes easier when viewing the changes in a `log` or `graph`.

### Merge vs Rebase
Although `git rebase` is an extremely useful tool to keep a Git repository clean and easy to follow, it doesn’t mean that one should _always_ stick to that command when integrating code changes. Let’s go over the definitions of `rebase` and `merge` one more time:

- Git rebase: Reapplies commits on top of another base branch.
- Git merge: joins two or more development histories together (creating a new merge commit).

In other words, Git merge preserves history as it happened, whereas rebase rewrites it.

Generally, if one is dealing with numerous branches, and the commit graph becomes really difficult to read, it can be very useful to use rebase instead of merge. Since Git rebase creates a linear history, it can be a lot easier to visualize the changes made and get a cleaner graph.

![[Pasted image 20230616124832.png]]

In the end, each team will develop their preferred method of integrating changes and preserving history. Generally, it’s useful to use `merge` whenever we want to add changes of a branch **back** into the base branch. And `rebase` is useful whenever we want to add **changes of a base branch** back to a branched out branch.

### Disadvantages of using rebase
As useful as Git rebase can be, it doesn’t come without risks. When using `git rebase` in our workflow it’s imperative to understand that rebase is a **destructive operation** and creates _new_ commits, which can make it complicated to track the context of any changes made. One common rule when using rebase is to only use it locally. That is to say, once something has been pushed then **do not** rebase it after that. Otherwise, things can get convoluted when rewriting history on a remote.

Since we’re rewriting history we will also have to solve more commit conflicts. When we merge a branch, we only need to solve the conflicts once straight into the merge commit. However, when using rebase we might end up having to solve similar conflicts in previous commits that are being rewritten because rebase practically cherry-picks each commit individually and attempts to merge it in. If a commit introduces a conflict, rebase will complain about it even if the conflict is fixed in subsequent commits. In order to reduce the number of merge conflicts, it’s suggested to rebase often and to also squash changes into one commit as much as possible.

Moreover, make sure that the branch we’re working on is not a shared branch. A shared branch meaning a branch that exists on the distant repository and that other people on our team could pull. Why should we avoid this? Well, remember that rebasing changes **commit history**. So if we share our commits publicly, and others start additional work based on those commits, our trees are no longer in sync after rebasing. As a golden rule, it’s important to only use rebase on a local branch that we’re working on individually.

---

You can use the following Git command to see a fuller picture of commits and progresses made in the branches:

```shell
git log --graph --decorate --oneline --all
```

And rebase Viraj’s branch with `main`:

```shell
git rebase main
```


## Managing a GitHub Repository

### GitHub Repository Settings
All GitHub settings can be accessed by clicking the ⚙️**Settings** tab on the main page of our repository.

#### The Options Tab
The Options tab allows us to change the basic repository information such as its name and social media banner. It’s where we can enable or disable certain GitHub features like Wikis, Issues, Discussions, and more. We can also change merge options to only allow certain types of merges, or automatically delete head branches. Most importantly, there’s the danger zone.

#### The Danger Zone
As the name suggests, the danger zone is where one should take caution when changing settings. We can make a repository private or public, transfer ownership to another user, and archive or delete the repository.

#### The Branches Tab
The settings’ Branches tab is where we can set a default branch. The default branch is the branch against which all pull requests and code commits are automatically made (typically this is already set to the `main` branch). We can also protect our branches by adding rules that prevent branches from being deleted, disable force pushing, or require a pull request to be made before merging to a branch.

### Managing Repository Access
By default, only the owner of the repository or the organization can configure the settings of a repository and access the tools. We have to go through the repository settings’ Manage Access tab to grant other users or teams access. The specificity of permissions differs greatly between a user repository and an organization repository.

As always, we should use caution when granting permissions especially to those outside of our immediate organization or team. They can make undesired changes to the code, host pages or packages on our behalf, or even leak private source code.

#### User Repository
For a user repository, the owner can easily add another user by clicking the “Add people” button, searching their full name, email address, or username. The user will then have to accept the invitation. While the added user doesn’t have the same permissions as the owner of the repository, the user can still rename a branch and publish packages among other things. For more information on the differences between the permission levels, check out [GitHub Docs](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-user-account/managing-user-account-settings/permission-levels-for-a-user-account-repository).

#### Organization Repository
GitHub Organizations provide its members a way to collaborate on multiple projects across multiple repositories. Owners or administrators of the organization can manage member access to the organization’s repositories. Adding a member to a repository is no different from the process in a user repository with the exception of adding teams. In a GitHub Organization, admins can group members into teams and reference users by team names. You can read more about organization roles and their varying abilities on the [GitHub Docs](https://docs.github.com/en/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization).

##### Repository Roles
Businesses and institutions usually have a hierarchy that defines levels of authority and responsibilities. The same principles can be applied in a GitHub repository or organization; we don’t want everyone to have admin privileges. Plus, it’s strategic and secure to map levels of access.

You can check out [GitHub Docs](https://docs.github.com/en/organizations/managing-access-to-your-organizations-repositories/repository-roles-for-an-organization) for a detailed breakdown of permissions for repository roles. You can also read about [creating custom repository roles](https://docs.github.com/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/managing-custom-repository-roles-for-an-organization) to have a configurable set of permissions with a role name of your choice.

### Other Repository Features and Tools
Each of the following features has a dedicated tab in the GitHub repository settings:

- **Security & Analysis**: We can enable or disable a variety of security features for our repository.
- [**Webhooks**](https://docs.github.com/en/developers/webhooks-and-events/webhooks/about-webhooks): We can use webhooks to get notifications when certain events happen.
- **Notifications**: We can receive email notifications when push events are triggered.
- **Integrations**: Any open source applications we use to extend our GitHub workflow or any third-party tools we integrate with GitHub will appear here. For example, Slack or CircleCI.
- [**Deploy Keys**](https://docs.github.com/en/developers/overview/managing-deploy-keys#deploy-keys): We can use the SSH keys generated here to grant servers access to a repository for deployment.
- **Actions**: [GitHub Actions](https://docs.github.com/en/actions) is a powerful tool to automate, customize, and execute software workflows such as testing The [Actions tab](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository) allows us to change the permissions.
- **Secrets**: Secrets are encrypted environment variables that can be used in Actions.
- **Pages**: GitHub [Pages](https://pages.github.com/) allows us to host simple web pages straight from the repository.


## Using a .gitignore File in Your GitHub Repository

### What is a .gitignore file?
**.gitignore** is a plain text file that tells Git to intentionally ignore changes in certain files.

### Why use a .gitignore file?
Each line in **.gitignore** corresponds to a file, directory, or pattern we would like to ignore when staging. Using a **.gitignore** file results in cleaner staging areas and prevent files containing sensitive information from being committed. Some of the files or folders we should ignore include:

- Configuration files with API or secret keys such as **.env**
- Compiled binary files or production directories such as **build** or **dist**
- Log files
- Dependencies downloaded from a package manager such as **node_modules**
- System files such as **thumbs.db** on Windows or **.DS_Store** on macOS

### .gitignore in action
Let’s say we run `git status` and see that operating system files, such as **thumbs.db** and **.DS_Store**, are staged and will be committed!

Let’s ignore those files using their exact names. For example, if we add these lines to our **.gitignore** file:

```
# Windows OS file
thumbs.db
 
# macOS OS file
.DS_Store
```

Git will ignore the special operating system files for Windows and macOS. These files will never be committed for this particular repository regardless of their location in this project. Note that in the file, blank lines are ignored and lines starting with `#` are treated as comments.

### Creating a .gitignore File
**.gitignore** is usually placed in the root directory of the repository. The filenames inside a **.gitignore** file can be written relative to the location of the **.gitignore** file.

### Ignore a directory with .gitignore
Sometimes we want to ignore entire directories or specify certain files in a directory. Common directories to leave out of a Git repository are **node_modules** or **logs** folder. We can ignore an entire directory by simply adding its name to **.gitignore**:

```
node_modules/
```

This will ignore the **node_modules** directory, and all subdirectories and files inside them. The forward slash `/` specifies that we are ignoring the directory.

### .gitignore Patterns
We can take advantage of [patterns](https://git-scm.com/docs/gitignore#_pattern_format) to match multiple filenames. These help us handle special cases such as ignoring specific file types or ignoring all but one file inside a directory.

- Wildcard `*` to match 0 or more characters except for `/`. For example, adding `*.html` to **.gitignore** would ignore all files ending with the `.html` extension. `example*` would match any file starting with `example` such as `example.txt` or `exampleHtmlFile.html`.
- Negation `!` as a prefix to negate any file that would otherwise be ignored. For example,

```
index*
!public/index.css
```

will ignore all files starting with `index` except for `src/index.css`. But, we cannot negate a file inside an ignored directory.

- Square brackets `[]` can be used to match a single character from a set of characters or a range of characters. Note that the range can be alphabetical: `[a-z]` or `[A-Z]`, numeric `[0-9]`, or a set of characters. If we added `index.[a-i]*` with both the square bracket and wildcard to **.gitignore**, we would ignore `index.css` and `index.html` but not `index.js`, since “j” is outside of the `[a-i]` range.
- Double asterisk `**` is used to match 0 or more directories. If we had a **temp** folder inside all of the folders in the root directory and we only wanted to match files with the `.log` extension, we could use the pattern `**/temp/*.log`.

### GitHub Provided Templates
When we create a new repository on GitHub, we have the option to add a **.gitignore** file from a list of templates. These templates are pulled from [GitHub’s gitignore repository](https://github.com/github/gitignore). For example, below is the template for Java projects.

```
# Compiled class file
*.class
 
# Log file
*.log
 
# BlueJ files
*.ctxt
 
# Mobile Tools for Java (J2ME)
.mtj.tmp/
 
# Package Files #
*.jar
*.war
*.nar
*.ear
*.zip
*.tar.gz
*.rar
```

