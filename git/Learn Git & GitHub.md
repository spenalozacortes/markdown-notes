
# GitHub Features: Issues, CLI, & Actions

## Introducing Helpful GitHub Features

### GitHub Issues
GitHub Issues adds project management right to your repository. You can list tasks and organize them into which are open and in progress. These issues can also be referenced in pull requests and even other issues.

### GitHub CLI
The GitHub Command Line Interface (CLI) is a tool that allows you to directly access and. modify issues and pull requests right from your terminal!

### GitHub Actions
Want to add automated tests after a pull request is created? Want to trigger something after a branch is merged into `main`? We can use GitHub Actions!


## Project Management

### The Issues Tab
When looking at a GitHub repository, we see a tab called `Issues`. This is a built-in GitHub tracking tool for all the bugs, errors, and potential small feature changes for the project living inside the repository. In one view, collaborators of the repository can see what needs to be worked on (open issues) as well as which tasks were resolved (closed issues). Take a look at the [Codecademy docs Issue board](https://github.com/Codecademy/docs/issues).

The issue board acts as a forum for all the collaborators of the repository. In some instances, issue boards are public and users of a project can submit and discuss bugs they’ve encountered.

#### Labels
To help organize issues when more and more pop up in a project, we can use labels. `bug` and `feature` are common labels used to differentiate between errors and new features.

#### Creating an Issue
To create an Issue, we can click the `New Issue` button on top of the Issues board. This will take us to a new page where to set the title and content of the issue.

Issues are a bit like pull requests in that we want to keep the title specific but to the point. For descriptions, repositories often have their own guidelines (just like pull requests do) for including details.

Once the issue is posted and now open, collaborators and other GitHub users can add to the discussion and reference this issue by the `#` in other issues and pull requests.

### GitHub Project Management
GitHub projects is a beta feature (as of late 2021) for project management. While other project management tools exist, like JIRA or even handwritten post-its, GitHub projects allow direct integration within the repository, letting developers stay within the same ecosystem. We can also create automated project boards that trigger the status of issues and pull requests.

To try out projects, we can select the `New Project` option after clicking the `+` button on the upper right side of the GitHub dashboard. In most cases, projects are linked to repositories, which already have existing issues and pull requests, but in other cases, projects can be standalone.

After filling out the name and description of the new project, a drop-down will appear asking what Project template we want to use.

The options range from different types of Kanban boards that can host issues and pull requests to a Bug Triage, which gives details into which bugs are high priority, low priority, or need further investigation. Once the board is created, we will [add issues and pull requests](https://docs.github.com/en/issues/organizing-your-work-with-project-boards/tracking-work-with-project-boards/adding-issues-and-pull-requests-to-a-project-board) to it.

An example of a laid-out GitHub project board is [Github’s own public roadmap project](https://github.com/orgs/github/projects/4247/views/1).


## GitHub CLI
GitHub CLI is a powerful command-line tool that enables developers to handle several of the critical functionalities of GitHub from a terminal. We can see open issues, make pull requests, link pull requests to issues, and even merge pull requests without touching the GitHub UI.

### Installation
Download and execute the installer for your operating system from the GitHub CLI public webpage. Once the installation is complete, open a new terminal and verify the default configuration:

```shell
gh --version 
```

Review the list of the supported APIs and functionalities:

```shell
gh --help
```

Login to GitHub from your terminal using GitHub CLI and follow the instructions to complete the authentication.

```shell
gh auth login
```

Use the command line to create a GitHub Issue documenting the problem:

```shell
gh issue create --title "Fix magic8.py error" --body "The code for magic8.py uses the Python random library without importing it. This causes issues during runtime."
```

You can also use GitHub CLI to list all opened issues so far:

```shell
gh issue status
```

Let’s now create a new branch to actually fix the issue.

```shell
git checkout -b “fix-magic8 ”
```

You can use the command line to directly make a pull request:

```shell
gh pr create
```

Assuming that your pull request is good to go, you can merge your pull request using the following GitHub CLI command:

```shell
gh pr merge
```

Once the pull request is merged, check back the status of the issues and notice that the issue is now closed and no longer listed under the open issues:


## GitHub Actions & Automated Testing

### Introduction
Now imagine we could configure your [GitHub](https://www.codecademy.com/resources/docs/general/github) repository to automatically run tests to verify the functionality of the codebase after each code change. Well… we can, using **GitHub Actions**!

### GitHub Actions
[GitHub Actions](https://github.com/features/actions) is a powerful, advanced GitHub feature that enables users to define custom and automated workflows triggered on various types of events such as [pushing code](https://www.codecademy.com/resources/docs/git/push) or [creating a pull request](https://www.codecademy.com/resources/docs/git/pull-requests). The workflows execute inside a temporary container running in GitHub infrastructure.

### Tutorial: add automated testing to a repository

#### Run tests on code push
Once you clone your forked copy of the repository from your GitHub account onto your local computer, create a new branch.

In your new branch, create a new directory and name it `.github`. Note that the dot in the beginning of the directory name is important. This is a keyword known to GitHub.

Then create another directory inside the `.github` directory and name it `workflows`. GitHub looks for the definitions of GitHub Actions inside this directory.

Create a new `.yaml` file inside the directory. Let’s name it `unittests.yaml` and paste the following content inside the file. Note that the indentation and spacing are important.

```shell
name: Continuous Integration
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Set up Python
        uses: actions/setup-python@v2
        with:
          python-version: 3.10.0
          architecture: x64
      - name: Install dependencies
        run: pip install -r requirements.txt 
      - name: Run Tests
        run: python -m pytest
```

The file introduces a new GitHub Action named `Continuous Integration` that is triggered on `push`, meaning that everytime a developer pushes a code to a branch where this file exists. The action then runs the following steps in the order of their definition on an `ubuntu-latest` container:

1. Check out to the current Git branch.
2. Set up Python on the container.
3. Install the Python dependencies of the Bank Account app defined in `requirements.txt`.
4. Run the unit tests using Pytest.

Add and commit your changes, then push the branch out to your remote repository on your GitHub account:

Now open your repository in a browser and navigate under the Actions tab. You should see a new workflow started a few seconds ago.

Click on the workflow to show the details. The logs for every individual step are available.

Click through the steps to read the logs. Once the workflow finishes, you will see a green checkmark. If any of the unit tests fail, the workflow fails and you will see an email notification.

#### Run tests on pull request creation
Now let's make this GitHub Action workflow also run the tests when creating a new pull request.

Open `unittests.yaml` file and update the array of triggers to add `pull_request`:

```
on: [push, pull_request]
```