# Lab 01 - Building Automation with Git

In this exercise you will configure git, create a Python application, and use a code repository to manage the project source.
### Outcomes

You should be able to configure git, initialize a repository, manage the repository files, commit file changes, and undo changes to the files.
&nbsp;
&nbsp;
&nbsp;

## Instructions

------------
### 1. Configure your git identity at the user level in your machine.
&nbsp;
#### 1.1. Open a new terminal window on your workstation, and use the git config command to set up your user name.

```bash
[user@host]$ git config --global user.name "Your User Name"
```

#### 1.2. Use the git config command to set up your user email.
```bash
[user@host]$ git config --global user.email your@user.email
```
#### 1.3. Use the git config command to review your identity settings.
```bash
[user@host]$ git config --list 
```
```
user.name=Your User Name 
user.email=your@user.email
```
&nbsp;
&nbsp;
------------
### 2. Create a folder for the exercise files and then initialize a Git repository.
&nbsp;
#### 2.1. Create a folder named git-basics in your workspace directory.
```bash
[user@host]$ mkdir git-basics
```
#### 2.2. Navigate to the git-basics folder on the command terminal.
```bash
[user@host]$ mkdir git-basics
```
