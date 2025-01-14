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
git config --global user.name "Your User Name"
```

#### 1.2. Use the git config command to set up your user email.
```bash
git config --global user.email your@user.email
```
#### 1.3. Use the git config command to review your identity settings.
```bash
git config --list 
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
mkdir git-basics
```
#### 2.2. Navigate to the git-basics folder on the command terminal.
```bash
cd git-basics 

```
#### 2.3. Use the git init command to initialize the git repository in the current directory.
```bash
git init .
```
```
Initialized empty Git repository in ...output omitted...~/git-basics/.git/
```
------------
### 3. Create a Python application, add it to the repository, and verify the staged changes. Use a text editor such as VSCodium, which supports syntax highlighting for editing Python source files.
&nbsp;
#### 3.1. Create a Python file named person.py with the following content.
```python
class Person:
    def greet(self) -> None:
        print('Hello Red Hatter!')
pablo = Person()
pablo.greet()
```
#### 3.2. Create a Python file named person.py with the following content.
```bash
python person.py
```
```
Hello Red Hatter!
```
#### 3.3. Use the git add command to add the new file to the staging area.
```bash
git add person.py
```
#### 3.4. Run the git status command to check that the file changes are in the staging area.
```bash
git status
```
```
On branch master
No commits yet
Changes to be committed:
(use "git rm --cached <file>..." to unstage)
new file:   person.py
```
#### 3.5. Use the git commit command to commit the staged file, and assign to the commit a meaningful comment with the -m option.
```bash
git commit -m "Initial Person implementation"
```
```
[master (root-commit) b030555] Initial Person implementation
 1 file changed, 7 insertions(+)
 create mode 100644 person.py
```
> Every time you add a commit to a repository, git generates and associates a hash string to the commit in order to identify it. In this case, the hash string b030555 was generated and assigned to the initial commit.
Note that the hash strings assigned to your commits might differ from the examples.

#### 3.6. Rename the current branch master (the default in Git) to main
```bash
git branch -M main
```

#### 3.7. Run the git status command to visualize the current state of the repository.
```bash
git status
```
```
On branch main
nothing to commit, working tree clean
```
------------
### 4. Modify the person.py file to improve the greeting feature, review the changes, and commit the new version of the file.
&nbsp;
#### 4.1. Modify the person.py file to allow a personalized greeting and salute to Jaime and Guy. The person.py file should look like the following:
```python
class Person:
	def greet(self, name: str = 'Red Hatter') -> None:
		print('Hello {}!'.format(name)) 
pablo = Person()

pablo.greet('Jaime')
pablo.greet('Guy')
```
#### 4.2. Run the Python script to verify that it salutes Jaime and Guy.
```bash
python person.py
```
```
Hello Jaime!
Hello Guy!
```
#### 4.3. Run the git diff command to view the differences between the original version of the file, and the latest changes.
```bash
git diff
```
```
diff --git a/person.py b/person.py index 0652fa3..7750914 100644
--- a/person.py
+++ b/person.py
@@ -1,7 +1,7 @@
 class Person:
-    def greet(self) -> None:
-        print('Hello Red Hatter!')
+    def greet(self, name: str = 'Red Hatter') -> None:
+        print('Hello {}!'.format(name))
 pablo = Person()
-pablo.greet()
+pablo.greet('Jaime')
+pablo.greet('Guy')
```
> The git diff command highlights the changes made to the person.py file. The - character at the beginning of a line indicates that the line was removed. The + character at the beginning of a line indicates that the line was added.

#### 4.4. Use the git add command to add the changes to the staging area.
```bash
git add .
```
#### 4.5. Run the git status command to check that the file changes are in the staging area.
```bash
git status
```
```
On branch main
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)
 modified:   person.py
```
#### 4.6. Use the git commit command to commit the staged changes, and assign to the commit a meaningful comment with the -m option.
```bash
git commit -m "Enhanced greeting"
```
```
[main b567b44] Enhanced greeting
 1 file changed, 4 insertions(+), 3 deletions(-)
```
------------
### 5. Inspect the repository history of commits.
&nbsp;
#### 5.1. Run the git log command to inspect the commit history of the repository.
```bash
git log
```
```
commit b567b44b1fa64c428a199e9776c64fcb99c2b40d (HEAD -> main)
Author: Your User Name <your@user.email>
Date: Mon Sep 28 11:54:23 2020 +0200
    Enhanced greeting
commit fd86e63c430e5232e028bce4e8998ec3433859bd
Author: Your User Name <your@user.email>
Date:   Mon Sep 28 11:24:07 2020 +0200
    Initial Person implementation
```
> The git log command shows all the commits of the repository in chronological order. The default output includes the commit hash string, the author, the date of the commit, and the commit message.

#### 5.2. Run the git show command to view the latest commit, and the changes made in the repository files.
```bash
git show
```
```
commit b567b44b1fa64c428a199e9776c64fcb99c2b40d (HEAD -> main)
Author: Your User Name <your@user.email>
Date: Mon Sep 28 11:54:23 2020 +0200
    Enhanced greeting
diff --git a/person.py b/person.py
index 0652fa3..634d287 100644
--- a/person.py
+++ b/person.py
@@ -1,7 +1,8 @@
 class Person:
-    def greet(self) -> None:
-        print('Hello Red Hatter!')
+    def greet(self, name: str = 'Red Hatter') -> None:
+        print('Hello {}!'.format(name))
 pablo = Person()
-pablo.greet()
+pablo.greet('Jaime')
+pablo.greet('Guy')
```
------------
### 6. Modify the person.py file to include a question in the greeting feature, stage the changes, and undo all the modifications.
&nbsp;
#### 6.1. Modify the person.py file to include a question after the greeting. The person.py file should look like the following:
```python
class Person:
    def greet(self, name: str = 'Red Hatter') -> None:
        print('Hello {}!'.format(name) ' How are you today?')
pablo = Person()
pablo.greet('Sam')
```
> Do not run the program yet.

#### 6.2. Use the git add command to add the file changes to the staging area.
```bash
git add person.py
```

#### 6.3. Run the Python script to verify that the question is added after the greeting.
```bash
python person.py
```
```
File "person.py", line 3
    print('Hello {}!'.format(name) ' How are you today?')
                                                       ^
SyntaxError: invalid syntax
```

> The latest changes introduced a bug in our Python script.

#### 6.4. The changes that introduced a bug in the Python script are in the staging area. Use the git reset command to unstage the changes.
```bash
git reset HEAD person.py
```
```
Unstaged changes after reset:
M person.py
```
#### 6.5. Run the git status command to check that the changes were unstaged.
```bash
git status
```
```
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
 modified:   person.py
no changes added to commit (use "git add" and/or "git commit -a")
```
#### 6.6. Use the git checkout command to undo the local changes of the person.py file.
```bash
git checkout -- person.py
```
> As covered in Creating Git Branches, git checkout is normally reserved for traversing the repository, but many of Git's subcommands have alternate uses.
This form of the checkout command restores the person.py file to its state at a specified commit or the current commit, by default. The -- parameter instructs Git to interpret any following arguments as files.

#### 6.7. Verify that the app continues running fine and return to the workspace directory.

```bash
python person.py
```
```
Hello Jaime!
Hello Guy!
```

&nbsp;
&nbsp;
&nbsp;
## This concludes the lab.

&nbsp;
&nbsp;
&nbsp;
