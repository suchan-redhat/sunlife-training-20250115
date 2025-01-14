# Lab 03 - Managing Remote Repositories

In this exercise, you will learn how to use and manage remote Git repositories and how to review changes by using pull requests.

### Outcomes

You should be able to set up a remote repository, push code to and pull code from the remote repository and use pull requests to review changes.
&nbsp;
&nbsp;
&nbsp;

## Instructions

------------
### 1. Initialize a local repository.
&nbsp;
#### 1.1. Create a new folder named hello-remote. This folder will contain your repository.

```bash
mkdir hello-remote
```

#### 1.2. Navigate to the hello-remote folder and initialize a new repository:
```bash
cd hello-remote
git init .
```
```shell
Initialized empty Git repository in ...output omitted...~/hello-remote/.git/
```
#### 1.3. Create the helloworld.py file with the following content:
```python
print("Hello world!")
```
#### 1.4. Stage and commit the file:
```bash
git add helloworld.py
git commit -m "added helloworld"
```

#### 1.5. Rename the current branch master to main:
```bash
git branch -M main
```
&nbsp;
&nbsp;
------------
### 2. Create a new repository in GitHub.
&nbsp;
#### 2.1. Open a web browser and navigate to https://github.com.
&nbsp;
#### 2.2. Sign in with your GitHub credentials. If you do not have an account, then create one.
&nbsp;
#### 2.3. Click + > New repository in the upper right of the window.
&nbsp;
#### 2.4. Fill in the Repository name field with the hello-remote value. Do not change any other field. Click Create repository.
&nbsp;
&nbsp;
------------
### 3. Add the remote to the local repository.
&nbsp;
#### 3.1. Switch to the command line and check you are in the hello-remote folder.
&nbsp;
#### 3.2. Verify that no remotes exist:
```bash
git remote -v
```
```shell

```
#### 3.3. Use the git remote add command to add the remote repository:
```bash
git remote add origin https://github.com/YOUR_GITHUB_USER/hello-remote.git
```
#### 3.4. Verify that the remote has been added:
```bash
git remote -v
```
```shell
origin https://github.com/your_github_user/hello-remote.git (fetch) 
origin https://github.com/your_github_user/hello-remote.git (push)
```
#### 3.5. Set the upstream branch and push to the remote repository. Notice the use of the --set-upstream parameter to set the upstream branch. You must provide your username and personal access token to push changes to the GitHub remote repository.
```bash
git push --set-upstream origin main
```
```shell
Username for 'https://github.com': YOUR_GITHUB_USER
Password for 'https://
your_github_user@github.com': YOUR_GITHUB_PERSONAL_ACCESS_TOKEN Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 247 bytes | 247.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/your_github_user/hello-remote.git
 * [new branch]      main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
```
#### 3.6. In a web browser, navigate to https://github.com/YOUR_GITHUB_USER/hello- remote. Check your changes are visible in GitHub.

------------
### 4. Create a feature branch to personalize the greeting message. The program must read your name as a command-line parameter and show it in the greeting message.
&nbsp;
#### 4.1. Create a new branch named improve-greeting:
```bash
git branch improve-greeting
```

#### 4.2. Checkout the improve-greeting branch:
```bash
git checkout improve-greeting
```
```shell
Switched to branch 'improve-greeting'
```

#### 4.3. Modify the helloworld.py file with the following contents:
```python
import sys

print("Hello {}!".format(sys.argv[1]))
```

#### 4.4. Run the program:
```bash
python helloworld.py Student
```

#### 4.5. Use the git status command to check the status of the repository:
```bash
git status
```
```shell
On branch improve-greeting
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
  
	modified:   helloworld.py
    
no changes added to commit (use "git add" and/or "git commit -a")
```
> Although Git detects the changes, you must stage them for commit.


#### 4.6. Stagethechangesbyusingthegit addcommand.Next,runthegit status command again to check that the changes have been staged for commit:
```bash
git add helloworld.py
git status
```
```shell
On branch improve-greeting
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)
  
	modified:   helloworld.py
    
```

#### 4.7. Commit the changes:
```bash
git commit -m "added parameter to greeting message"
```
```shell
[improve-greeting 6b5013e] added parameter to greeting message
 1 file changed, 3 insertions(+), 1 deletion(-)
```

#### 4.8. Set the branch upstream and push the branch to GitHub:
```bash
git push --set-upstream origin improve-greeting
```
```shell
...output omitted...
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 12 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 316 bytes | 316.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
remote:
remote: Create a pull request for 'improve-greeting' on GitHub by visiting:
remote:      https://github.com/your_github_user/hello-remote/pull/new/improve-
greeting
remote:
To https://github.com/your_github_user/hello-remote.git
 * [new branch]      improve-greeting -> improve-greeting
Branch 'improve-greeting' set up to track remote branch 'improve-greeting' from
'origin'.
```

> Note how the improve-greeting branch is created in the remote GitHub repository. Also notice how GitHub provides you with a URL to create a pull request for this new branch.



#### 4.9. In a web browser, navigate to https://github.com/YOUR_GITHUB_USER/hello- remote/tree/improve-greeting to verify that the branch and the changes have been pushed to GitHub.

&nbsp;

------------
### 5. Review the changes introduced in the feature branch by using a pull request. After reviewing the code, merge the pull request to integrate the new feature into the main branch.

&nbsp;
#### 5.1. In a web browser, navigate to https://github.com/YOUR_GITHUB_USER/hello- remote.
&nbsp;

#### 5.2. Click Pull requests to navigate to the pull requests page. In the pull requests page, click New pull request.
&nbsp;

#### 5.3. In the branches selection area, click the compare: main selector to select the improve-greeting branch.

> Next, click the Create pull request button to open the pull request creation form. In the pull request creation form, click Create pull request.
&nbsp;

#### 5.4. Click Assignees to assign the pull request to yourself. Click Reviewers to request reviews from other people.
&nbsp;
#### 5.5. Click the Files changed tab to observe the changes introduced in the improve- greeting branch, compared to the main branch.
&nbsp;
#### 5.6. Add a comment to suggest the extraction of the sys.argv[1] expression to a variable. Click the + button, which displays when you hover the mouse over the print("Hello {}!".format(sys.argv[1])) line. Write the comment and click Start a review.
> Click Finish your review > Submit review to finish the review with the comment.
&nbsp;

------------
### 6. Update the code to address the comment from the pull request and update the pull request.
&nbsp;
#### 6.1. Open the helloworld.py file and modify the code to extract sys.argv[1] into a variable. The file content should look like this:

```python
import sys

name = sys.argv[1]
print("Hello {}!".format(name))

```

#### 6.2. Verify that the program runs successfully:
```bash
python helloworld.py Student
```
```shell
Hello Student!
```

#### 6.3. Stage, commit and push the changes. The -a parameter adds the modified files to the stage before creating the commit
```bash
git commit -a -m "extracted cli argument to variable"
```
```shell
[improve-greeting 2a54571] extracted cli argument to variable
1 file changed, 2 insertions(+), 1 deletion(-)
```
```bash
git push
```
```shell
...output omitted...
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 12 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 306 bytes | 306.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/your_github_user/hello-remote.git
   6b5013e..2a54571  improve-greeting -> improve-greeting
   
```

#### 6.4. Go back to GitHub, refresh the pull request page and verify that the changes show up. The previous comment should show up as Outdated.



------------
### 7. Merge the pull request.
&nbsp;
#### 7.1. In GitHub, navigate to the pull request page if you are not already there and click the Merge pull request button. Click Confirm merge on the confirmation form that shows up.
&nbsp;

#### 7.2. A Delete branch button is displayed immediately after the merge. Click this button to delete the improve-greeting remote branch.
&nbsp;

#### 7.3. In the local repository, checkout the main branch:
```bash
git checkout main
```
```shell
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
```

> Note the checkout message. The local repository is not aware of the remote changes.

#### 7.4. Check that the changes you just merged are not in the main remote tracking branch.

```bash
git log origin/main
```

#### 7.5. Fetch changes from the remote repository.

```bash
git fetch -p
```
```shell
remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
Unpacking objects: 100% (1/1), done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0 From https://github.com/your_github_user/hello-remote
   2a0444d..ada565e  main     -> origin/main
```

> The -p parameter prunes remote-tracking branches that do not exist in the remote repository anymore, causing the removal of the origin/improve-greeting branch.


#### 7.6. Check that the merged commits have been fetched. Run the git log command again:

```bash
git log origin/main
```
> The log view should show the latest commits fetched from the remote main branch:
```shell
commit ...output omitted... (origin/main) 
Merge: ...output omitted...
Author: ...output omitted...
Date: Fri Sep 25 17:15:23 2020 +0200

	Merge pull request #1 from ...output omitted...
    
    added parameter to greeting message
commit ...output omitted... (origin/improve-greeting, improve-greeting) 
Author: ...output omitted...
Date: Fri Sep 25 17:11:18 2020 +0200

	extracted cli argument to variable

commit ...output omitted...
Author: ...output omitted...
Date: Fri Sep 25 14:39:19 2020 +0200

	added parameter to greeting message

commit ...output omitted... (HEAD -> main) Author: ...output omitted...
Date: Fri Sep 25 13:37:44 2020 +0200
    
    added helloworld
    
```

> If Git shows the output by using a pager, then press q to quit the log screen.

#### 7.7. Run git log against the main branch.

```bash
git log
```

> The log should only show one commit in the local main branch.

```shell
commit ...output omitted... (HEAD -> main) 
Author: ...output omitted...
Date: Fri Sep 25 13:37:44 2020 +0200

	added helloworld
    
```

> If Git shows the output by using a pager, then press q to quit the log screen.


#### 7.8. Merge the remote-tracking origin/main branch into the local main branch.
```bash
git merge origin/main
```

```shell
Updating 2a0444d..ada565e
Fast-forward
 helloworld.py | 5 ++++-
 1 file changed, 4 insertions(+), 1 deletion(-)
```

#### 7.9. Delete the local feature branch:
```bash
git branch -d improve-greeting
```

```shell
Deleted branch improve-greeting (was 2a54571).
```

#### 7.10. Run git log to show the commits on the main branch. All the commits should be in this branch now.
```shell
commit ...output omitted... (HEAD -> main, origin/main) 
Merge: ...output omitted...
Author: ...output omitted...
Date: Fri Sep 25 17:15:23 2020 +0200

	Merge pull request #1 from ...output omitted...
    
    added parameter to greeting message
    
commit ...output omitted...
Author: ...output omitted...
Date: Fri Sep 25 17:11:18 2020 +0200
    
    extracted cli argument to variable
    
commit ...output omitted...
Author: ...output omitted...
Date: Fri Sep 25 14:39:19 2020 +0200
    
    added parameter to greeting message

commit ...output omitted... 
Author: ...output omitted...
Date:   Fri Sep 25 13:37:44 2020 +0200

	added helloworld
    
```

> If Git shows the output by using a pager, then press q to quit the log screen.


------------
### 8. Return to the workspace directory:

```bash
cd ..
```

&nbsp;
&nbsp;
&nbsp;
## This concludes the lab.

&nbsp;
&nbsp;
&nbsp;
