# Lab 04 - Releasing Code

In this exercise you will learn how to use tags, releases, and forks.

To set up the scenario necessary to complete this exercise, first you must create a new GitHub organization with your GitHub account. Next, you will create a repository in the organization by forking the source code we've been using. The repository forked in your organization will simulate a third-party project in which to contribute

With the organization set up as a hypothetical third-party project, you will practice a common contribution workflow, forking the third-party project into your username account and creating pull requests back to the third-party project to propose code changes.

### Outcomes

With the organization set up as a hypothetical third-party project, you will practice a common contribution workflow, forking the third-party project into your username account and creating pull requests back to the third-party project to propose code changes.
&nbsp;
&nbsp;
&nbsp;

## Instructions

------------
### 1. Create your own GitHub organization. This organization will host your simulated third-party project.
&nbsp;
#### 1.1. Open a web browser and navigate to https://github.com.

&nbsp;

#### 1.2. Sign in with your GitHub credentials. If you do not have an account, then create one.

&nbsp;

#### 1.3. Click + > New organization in the upper right of the window.

&nbsp;

#### 1.4. Choose the Free plan. Click Join for free.

&nbsp;

#### 1.5. Configure your new organization. Fill in the Organization account name field with the YOUR_GITHUB_USER-org value. Type your email in the Contact email field. Select My personal account as the owner. Click Next.

&nbsp;

#### 1.6. In the confirmation screen, click Complete setup. You must provide your password to complete this step.

&nbsp;
&nbsp;
------------
### 2. Create a repository in your organization by forking the go-training/helloworld repository. The newly created repository in your organization simulates a third-party project in which to contribute.

&nbsp;
#### 2.1. In a web browser, navigate to the repository located at https://github.com/go-training/helloworld
&nbsp;
#### 2.2. Click Fork in the upper right and select the YOUR_GITHUB_USER-org organization as the namespace. This creates the YOUR_GITHUB_USER-org/helloworld repository
> At this point, you have set up the scenario to contribute to a third-party project.
You will treat the repository you have just created as the upstream repository, meaning that you will consider this repository as the third-party project you send your contributions to.
&nbsp;

------------
### 3. Fork the upstream repository to start contributing to the upstream project. Fork the YOUR_GITHUB_USER-org/helloworld repository to your username account and clone the forked repository located at https://github.com/ YOUR_GITHUB_USER/helloworld.
&nbsp;
#### 3.1. From the upstream repository main page located at https://github.com/ YOUR_GITHUB_USER-org/helloworld, click Fork and select your username as the namespace.
> The new fork is located at https://github.com/YOUR_GITHUB_USER/helloworld. In this exercise, you will contribute to the upstream by sending pull requests from this fork to the organization upstream repository.

&nbsp;
#### 3.2. Click the Code button and copy the HTTPS URL.
&nbsp;
#### 3.3. Switch to the command line and navigate to your workspace folder.
```bash
cd lab
```
#### 3.4. Clone the repository by using the git clone command and the copied URL. Enter your GitHub username and personal access token when prompted.
```bash
git clone https://github.com/YOUR_GITHUB_USER/helloworld
```
```shell
Username for 'https://github.com': YOUR_GITHUB_USER
Password for 'https://your_github_user@github.com': YOUR_GITHUB_PERSONAL_ACCESS_TOKEN Cloning into 'helloworld'...
remote: Enumerating objects: 151, done.
remote: Total 151 (delta 0), reused 0 (delta 0), pack-reused 151 Receiving objects: 100% (151/151), 149.14 KiB | 208.00 KiB/s, done. Resolving deltas: 100% (58/58), done.
```
> By default, the git clone creates a folder with the same name as the repository and clones the code inside the created folder. You can change the folder by adding the folder name as a parameter of the git clone command.

&nbsp;

------------
### 4. Create a tag. Next, create a release by using the created tag.
&nbsp;
#### 4.1. Navigate to the repository folder and create the 1.0.0 tag by using the git tag
command:
```bash
cd helloworld
git tag 1.0.0
```

#### 4.2. Use the git tag command to verify that the tag has been created:
```bash
git tag
```


#### 4.3. Use git push origin --tags to push the tag to your username fork on GitHub. By default, Git does not push tags to the remote. To push tags, you must use the --tags parameter. If prompted, enter your GitHub username and personal access token.
```bash
git push origin --tags
```
```shell
Username for 'https://github.com': YOUR_GITHUB_USER
Password for 'https://your_github_user@github.com': YOUR_GITHUB_PERSONAL_ACCESS_TOKEN Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/your_github_user/DO400-apps-external.git
 * [new tag]         1.0.0 -> 1.0.0
 
```
#### 4.4. Switch back to the web browser and navigate to the main GitHub page for your fork located at https://github.com/YOUR_GITHUB_USER/helloworld. Click the Releases link in the right pane.

&nbsp;

#### 4.5. On the releases page, click Draft a new release.
&nbsp;

#### 4.6. Start typing 1.0.0 in the Tag version field and select 1.0.0. This is the tag that you just created. Do not change the Target: main selector.

&nbsp;

#### 4.7. Enter a value in the Release title field. The Existing tag label should appear under the tag field, confirming that you are using the 1.0.0 tag that you created.
> Finally, click Publish release to create the release. This takes you to the newly created release page.
&nbsp;
&nbsp;



------------
### 5. Create and merge a pull request from your username fork (origin) to your organization repository (upstream).

&nbsp;
#### 5.1. In your terminal, create a new branch named hello-redhat:
```bash
git checkout -b hello-redhat
```
```shell
Switched to a new branch 'hello-redhat'
```

#### 5.2. Inside the hello folder, create a new file hellorh.py with the following content:
```python
print("Hello Red Hat!")
```

#### 5.3. Stage and commit the hello/hellorh.py file:
```bash
git add hello
git commit -m "added hello Red Hat"
```
```shell
[hello-redhat 60db2e8] added hello Red Hat
 1 file changed, 1 insertion(+)
 create mode 100644 hello/hellorh.py
```


#### 5.4. Push the new branch to the username fork by using git push -u origin hello- redhat. The -u parameter is an alias of --set-upstream and it is used to set the upstream branch. Enter your GitHub username and password if prompted.

```bash
git push -u origin hello-redhat
```
```shell
...output omitted...
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 12 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 308 bytes | 308.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote:
remote: Create a pull request for 'hello-redhat' on GitHub by visiting:
remote:      https://github.com/your_github_user/DO400-apps-external/pull/new/
hello-redhat
remote:
To https://github.com/your_github_user/DO400-apps-external.git
 * [new branch]      hello-redhat -> hello-redhat
Branch 'hello-redhat' set up to track remote branch 'hello-redhat' from 'origin'.
```
#### 5.5. Switch back to the web browser and navigate to the GitHub page of your fork located at https://github.com/YOUR_GITHUB_USER/helloworld. Click Pull requests to navigate to the pull requests page. In the pull requests page, click New pull request.
&nbsp;
#### 5.6. In the branches selection area, click the compare: main selector to select the hello-redhat branch. Observe how you are merging your changes from the hello-redhat branch of your username fork (YOUR_GITHUB_USER/helloworld) into the main branch of the organization upstream repository (YOUR_GITHUB_USER-org/helloworld). Next, click the Create pull request button to open the pull request creation form.
&nbsp;

#### 5.7. In the pull request creation form, click Create pull request to submit the form and open the pull request.
&nbsp;

#### 5.8. Review your changes and merge the pull request into the main branch of the upstream organization repository. Click Merge pull request. Click Confirm merge on the confirmation form that shows up.
&nbsp;

#### 5.9. A Delete branch button is displayed immediately after the merge. The branch hello-redhat is unnecessary now because all of its changes have been merged into the main branch. Click Delete branch to delete the hello-redhat remote branch.
&nbsp;

------------
### 6. Pull changes from your username fork. Check that the main branch is not updated.
&nbsp;
#### 6.1. On the command line, switch to the main branch:

```bash
git checkout main
```
```shell
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
```

#### 6.2. Pull the changes from the origin remote. The origin remote refers to the repository forked in your username account (YOUR_GITHUB_USER/helloworld). Enter your GitHub username and password if prompted.
```bash
git pull origin main
```
```shell
...output omitted...
From https://github.com/your_github_user/helloworld
 * branch            main     -> FETCH_HEAD
Already up to date.
```

#### 6.3. Run git log and notice that your changes from the hello-redhat branch were not incorporated.
```bash
git log
```
```shell
commit c34ac6fcb5eea6ed4c62b665f0bb3b6c18f9a579 (HEAD -> main, tag: 1.0.0, origin/ main, origin/HEAD)
...output omitted...
```
> Note how the last commit in the main branch is still the commit tagged as 1.0.0. This is because you merged the pull request to the upstream repository (YOUR_GITHUB_USER-org/helloworld) and not the username fork (YOUR_GITHUB_USER/helloworld).

&nbsp;

------------
### 7. Configure and pull from the upstream remote.
&nbsp;
#### 7.1. In the web browser, navigate to the main page of your organization upstream repository, located at: https://github.com/YOUR_GITHUB_USER-org/helloworld. Click the Code button and copy the HTTPS URL.
&nbsp;

#### 7.2. Configure a new remote called upstream to point to your organization repository:
```bash
git remote add upstream https://github.com/YOUR_GITHUB_USER-org/helloworld.git
```

#### 7.3. Pullfromtheupstreamremotebyusinggit pull upstream main -p.Enter your GitHub username and password if prompted.
```bash
git pull upstream main
```
```shell
...output omitted...
remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (1/1), done.
From https://github.com/your_github_user-org/helloworld
 * branch            main     -> FETCH_HEAD
 * [new branch]      main     -> upstream/main
Updating 6459e50..d4492a5
Fast-forward
 hello/hellorh.py | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 hello/hellorh.py
```
#### 7.4. Run git logtoseethelocalmainbranchhasbeenupdated:

```bash
git log
```
```shell
commit d4492a5546f3088af378ef287dd272970ac3eb5d (HEAD -> main, upstream/main) Merge: 6459e50 60db2e8
Author: Your User Name <your.email@example.com>
Date: Thu Oct 1 12:54:59 2020 +0200
    
    Merge pull request #1 from your_github_user/hello-redhat
    
    added hello Red Hat
    
commit 60db2e8b62bad2320e66aa94e147c66aefc71139 (origin/hello-redhat, hello-
redhat)
Author: Your User Name <your.email@example.com>
Date:   Thu Oct 1 12:38:01 2020 +0200
    
    added hello Red Hat

...output omitted...
```
> Notice how both the local and the upstream main branches point to the same commit.


------------
### 8. Create a new release from GitHub.
&nbsp;
&nbsp;

#### 8.1. Push the changes on main to the forked repository with git push origin main. Enter your GitHub username and password if prompted.

```bash
git push origin main
```
```shell
...output omitted...
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/your_github_user/DO400-apps-external.git
   6459e50..d4492a5  main -> main
```

#### 8.2. Refresh the GitHub page for your username fork located at https://github.com/YOUR_GITHUB_USER/helloworld. You should see the latest commit and changes.
&nbsp;

#### 8.3. Click Releases on the right.
&nbsp;

#### 8.4. On the releases page, click Draft a new release.
&nbsp;

#### 8.5. Enter 2.0.0 in the Tag version field and enter a value in the Release title field.
&nbsp;

#### 8.6. Click Publish release to create the release. You are taken to your release's page.
&nbsp;

#### 8.7. On the command line, run git pull --tags. Enter your GitHub username and password if prompted.
```bash
git pull --tags
```
```shell
...output omitted...
From https://github.com/your_github_user/helloworld
* [new tag] 2.0.0 -> 2.0.0 Already up to date.
```

------------
### 9. Rungit logtoseeyourupdatedchangesonmainandthenew2.0.0tag:
&nbsp;
&nbsp;
```bash
git log
```
```shell
commit d4492a5546f3088af378ef287dd272970ac3eb5d (HEAD -> main, tag: 2.0.0,
 upstream/main, origin/main, origin/HEAD)
Merge: 6459e50 60db2e8
Author: Your User Name <your.email@example.com>
Date:   Thu Oct 1 12:54:59 2020 +0200
    
    Merge pull request #1 from your_github_user/hello-redhat
    
    added hello Red Hat
    
...output omitted...
```

------------
### 10. Clean up your local files and the remote repositories and organization.
&nbsp;
&nbsp;
#### 10.1. Remove your local helloworld folder
&nbsp;
#### 10.2. Remove the downstream and upstream repositories.
&nbsp;
#### 10.3. Remove the organization.
&nbsp;
&nbsp;
&nbsp;
&nbsp;
## This concludes the lab.

&nbsp;
&nbsp;
&nbsp;
