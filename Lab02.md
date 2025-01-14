# Lab 02 - Creating Git Branches

In this exercise, you will create a feature branch and track new changes on that branch.
### Outcomes

You should be able to create branches, add commits to those branches, and switch between branches.
&nbsp;
&nbsp;
&nbsp;

## Instructions

------------
### 1. Initialize a new repository.
&nbsp;
#### 1.1. Create a new folder named hello-branches. This folder will contain your repository.

```bash
mkdir hello-branches
```

#### 1.2. Navigate to the hello-branches folder and initialize a new repository.
```bash
cd hello-branches
git init .
```
```shell
Initialized empty Git repository in ...output omitted...~/hello-branches/.git/
```
#### 1.3. Create the helloworld.py file with the following content:
```python
def say_hello(name):
    print(f"Hello, {name}!")
say_hello("world")
```
#### 1.4. Run the program:
```bash
python helloworld.py
```
```shell
Hello, world!
```
#### 1.5. Stage and commit the file:
```bash
git add helloworld.py
git commit -m "added helloworld"
```
```shell
[master (root-commit) d4e8453] added helloworld
 1 file changed, 4 insertions(+)
 create mode 100644 helloworld.py
```
> The -m flag is a shortcut used to set the commit message. Without it, the default editor opens in order to prompt for the message.
#### 1.6. Rename the current branch master to main
```bash
git branch -M main
```
&nbsp;
&nbsp;
------------
### 2. Create a new feature branch.
&nbsp;
#### 2.1. Create a new branch named different-name.
```bash
git checkout -b different-name
```
```shell
Switched to a new branch 'different-name'
```
> The -b flag is a shortcut to create the branch before switching to it.

#### 2.2. Check that your current branch is the newly created different-name.
```bash
git status
```
```shell
On branch different-name
nothing to commit, working tree clean
```
------------
### 3. Make and commit changes to the helloworld.py file.
&nbsp;
#### 3.1. Update the helloworld.py file to match:
```python
def say_hello(name):
    print(f"Hello, {name}!")
say_hello("Pablo")
```
#### 3.2. View the changes made to helloworld.py.
```bash
git diff
```
```shell
diff --git a/helloworld.py b/helloworld.py 
index 3c29293..f69eef6 100644
--- a/helloworld.py
+++ b/helloworld.py
@@ -1,4 +1,4 @@
 def say_hello(name):
     print(f"Hello, {name}!")
-say_hello("world")
+say_hello("Pablo")
```
#### 3.3. Stage and commit the changes to helloworld.py:
```bash
git add .
git commit -m 'change name'
```
```shell
[different-name daf5db4] change name
 1 file changed, 1 insertion(+), 1 deletion(-)
```


------------
### 4. Compare the commit history between the main and different-name branches.
&nbsp;
#### 4.1. View the commit history. The different-name branch has one more commit than the main branch.
```bash
git log
```
```shell
commit daf5db416ffd47ab6d95a16eaaf4dabbcfa2cb72 (HEAD -> different-name) 
Author: Your User Name <your.email@example.com>
Date: Mon Sep 28 16:42:04 2020 -0400

	change name

commit d4e8453f6bc58a757a15f5ace664b3cd9afb65f6 (main) 
Author: Your User Name <your.email@example.com>
Date: Mon Sep 28 16:32:52 2020 -0400
    added helloworld
```

------------
### 5. Compare and merge the my-feature-branch branch.
&nbsp;
#### 5.1. Switch to the main branch:
```bash
git checkout main
```
```shell
Switched to branch 'main'
```

#### 5.2. View the commit history of the main branch:
```bash
git log
```
```shell
commit d4e8453f6bc58a757a15f5ace664b3cd9afb65f6 (HEAD -> main) 
Author: Your User Name <your.email@example.com>
Date: Mon Sep 28 16:32:52 2020 -0400
    added helloworld
```
> There is one less commit than what was on the different-name branch.

#### 5.3. Open helloworld.py in your editor. The file is missing the changes that were made on the different-name branch. It should have these contents:
```python
def say_hello(name):
    print(f"Hello, {name}!")
say_hello("world")
```

#### 5.4. Merge the different-name branch into the main branch. This performs a "fast- forward" merge. A fast-forward merge does not create a "merge commit". Instead, the merge requires only the branch itself to be moved to a different commit.
```bash
git merge different-name
```
```shell
Updating d4e8453..daf5db4
Fast-forward
 helloworld.py | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```
#### 5.5. View the updated commit history of the main branch:
```bash
git log
```
```shell
commit daf5db416ffd47ab6d95a16eaaf4dabbcfa2cb72 (HEAD -> main, different-name) 
Author: Your User Name <your.email@example.com>
Date: Mon Sep 28 16:42:04 2020 -0400

	change name

commit d4e8453f6bc58a757a15f5ace664b3cd9afb65f6
Author: Your User Name <your.email@example.com>
Date:   Mon Sep 28 16:32:52 2020 -0400
    
    added helloworld
    
```

#### 5.6. Delete the different-name branch
```bash
git branch -d different-name
```
```shell
Deleted branch different-name (was daf5db4).
```
> The -d flag deletes the branch.

------------
### 6. Create a new branch and commit changes.
&nbsp;
#### 6.1. Create and check out a branch named goodbye-name:
```bash
git checkout -b goodbye-name
```

#### 6.2. Open helloworld.py in your editor and change Hello to Goodbye:
```python
def say_hello(name): 
	print(f"Goodbye, {name}!")

say_hello("Pablo")
```

#### 6.3. Stage and commit the changes:
```bash
git commit -a -m 'say goodbye'
```
```shell
[goodbye-name 9e43ceb] say goodbye
 1 file changed, 1 insertion(+), 1 deletion(-)
```
> Including the -a flag stages all local changes before creating the commit.


------------
### 7. Make a conflicting commit on the main branch
&nbsp;
#### 7.1. Run git checkout main Switch back to the main branch:
```bash
git checkout main
```
```shell
Switched to branch 'main'
```

#### 7.2. Open helloworld.py in your editor and change Hello to Welcome:
```python
def say_hello(name): 
	print(f"Welcome, {name}!")
    
say_hello("Pablo")
```

#### 7.3. Stage and commit the changes:
```bash
git commit -a -m 'say welcome'
```
```shell
[main c80d322] say welcome
 1 file changed, 1 insertion(+), 1 deletion(-)
```

------------
### 8. Compare and merge the goodbye-name branch.
&nbsp;
#### 8.1. View the differences between the contents of helloworld.py on the main and goodbye-name branches:
```bash
git diff goodbye-name
```
```shell
diff --git a/helloworld.py b/helloworld.py
index 4e8dd88..22604ac 100644
--- a/helloworld.py
+++ b/helloworld.py
@@ -1,4 +1,4 @@
 def say_hello(name):
-    print(f"Goodbye, {name}!")
+    print(f"Welcome, {name}!")

	say_hello("Pablo")
```

#### 8.2. Merge the goodbye-name branch into the main branch.
```bash
git merge goodbye-name
```
```shell
Auto-merging helloworld.py
CONFLICT (content): Merge conflict in helloworld.py
Automatic merge failed; fix conflicts and then commit the result.
```
> A conflict occurred while performing the merge. This is due to main and goodbye- name incorporating changes to the same line in the same file since the branches diverged.

#### 8.3. Open helloworld.py in your editor. This is how the file will first appear:
```python
def say_hello(name):
<<<<<<< HEAD
    print(f"Welcome, {name}!")
=======
    print(f"Goodbye, {name}!")
>>>>>>> goodbye-name
say_hello("Pablo")
```
> Git indicates the conflicting lines by using "conflict markers". These are lines beginning with sequences of <, >, and =. Specifically, the first block contains the changes from the main branch (HEAD), and the second block contains changes from the goodbye-name branch.

#### 8.4. Fix the conflict by removing the conflict markers and correcting the code to match:
```python
def say_hello(name):
    print(f"Goodbye, {name}!")
    
say_hello("Pablo")
```

#### 8.5. Run the program to ensure it is still working:

```bash
python helloworld.py
```
```shell
Goodbye, Pablo!
```

#### 8.6. In order to indicate to Git that you have resolved the conflicts, stage and commit the conflicting file:

```bash
git commit -a
```
```shell
...output omitted...
[main 32d7b8c] Merge branch 'goodbye-name' into main
```

> When a commit message is omitted upon committing to resolve a conflicting merge, Git will open the default editor with a default commit message.

#### 8.7. Remove the goodbye-name branch:

```bash
git branch -d goodbye-name
```
```shell
Deleted branch goodbye-name (was 9e43ceb).
```

### 9. View the commit history to see that main has all of the changes from both branches:
&nbsp;

```bash
git log
```
```shell
commit 32d7b8c9b28c9b41cd5f4a97e63e8cb284622c1e (HEAD -> main) 
Merge: c80d322 9e43ceb
Author: Your User Name <your.email@example.com>
Date: Tue Sep 29 18:45:02 2020 -0400

	Merge branch 'goodbye-name' into main

commit c80d32280f9b1165c9d74303b137c0bb0a8c59b5
Author: Your User Name <your.email@example.com>
Date:   Tue Sep 29 17:53:45 2020 -0400

	say welcome

commit 9e43ceb14b042fee5c08d41a2130a075b1c74113
Author: Your User Name <your.email@example.com>
Date:   Tue Sep 29 17:49:31 2020 -0400

	say goodbye

commit daf5db416ffd47ab6d95a16eaaf4dabbcfa2cb72
Author: Your User Name <your.email@example.com>
Date:   Mon Sep 28 16:42:04 2020 -0400

	change name

commit d4e8453f6bc58a757a15f5ace664b3cd9afb65f6
Author: Your User Name <your.email@example.com>
Date:   Mon Sep 28 16:32:52 2020 -0400

	added helloworld
    
```


&nbsp;
&nbsp;
&nbsp;
## This concludes the lab.

&nbsp;
&nbsp;
&nbsp;
