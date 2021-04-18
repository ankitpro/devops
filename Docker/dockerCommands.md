# Ankit Agarwal
## __Docker_ Commands, Most Used_

[![N|Solid](https://icons.iconarchive.com/icons/tatice/operating-systems/256/Linux-icon.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)


- [About Docker](#about-docker)
- [How Git Works?](#how-git-works)
- [Basic Commands](#basic-commands)
- [Everyday use](#everyday-use)
- [Processing files and data](#processing-files-and-data)
- [System debugging](#system-debugging)
- [One-liners](#one-liners)
- [Obscure but useful](#obscure-but-useful)
- [macOS only](#macos-only)
- [Windows only](#windows-only)
- [More resources](#more-resources)
- [Disclaimer](#disclaimer)



# About Docker
Docker is a set of platform as a service products that use OS-level virtualization to deliver software in packages called containers. Containers are isolated from one another and bundle their own software, libraries and configuration files; they can communicate with each other through well-defined channels. 

# Working with Docker
## The Basics
### Initialization [The Basic Workflow]







### Create Docker image
To create a docker image from a running container.
Command: $ docker commit <container name>
```
$ docker commit cont1
sha256:a96866c1fdc940981fb322e941947ec102117910a955677887897008db03fbb4
```

```
Output:
REPOSITORY           TAG       IMAGE ID       CREATED         SIZE
<none>               <none>    a96866c1fdc9   7 seconds ago   2.35GB
ubuntu_with_gitlab   latest    9c0d7ae2ff5b   36 hours ago    245MB
web-host             latest    c0d96e23670c   39 hours ago    196MB
ubuntu               latest    26b77e58432b   2 weeks ago     72.9MB
centos               latest    300e315adb2f   4 months ago    209MB
```

----

### Tag the image 
To tag the image created from the container
```
$ docker tag a96866c1fdc9  ubuntu_with_gitlab_full

```
```
Output:
REPOSITORY                TAG       IMAGE ID       CREATED         SIZE
ubuntu_with_gitlab_full   latest    a96866c1fdc9   2 minutes ago   2.35GB
ubuntu_with_gitlab        latest    9c0d7ae2ff5b   36 hours ago    245MB
web-host                  latest    c0d96e23670c   39 hours ago    196MB
ubuntu                    latest    26b77e58432b   2 weeks ago     72.9MB
centos                    latest    300e315adb2f   4 months ago    209MB
```









To check your present working directory.
```
$ pwd
/Users/training/projects
```
----

To create a new project of your desired name (in my case am using demo) and initialise with git use the following command. The below command will create a demo project with a .git folder.
```
$ git init demo
Initialized empty Git repository in /Users/training/projects/demo/.git/
```
----

To enter into the git project and check the files and folders enter the below command.
```
$ cd demo
$ ls -al
Mode                LastWriteTime         Length        Name
----                -------------         ------        ----
drwxr-xr-x        2/26/2021   8:31 PM                   .
drwxr-xr-x         4/1/2021   2:32 PM                   ..
drwxr-xr-x         4/1/2021   2:32 PM                   .git
```
Here if you observe you see nothing other than the default ".git" folder, which is the actual Git repository.

----

### First Commit [The Basic Workflow]

Anytime you want to know whats going on with Git repository simply use "git status".
```
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```
As this is a brand new repository we are moving towards the initial commit. Initially while creating the Git repo for the first time we'll be in the branch "Master" by default.

----
To create a file in the current project use the below command (you can use any other editor you wish to use).
```
$ touch README.md
```
The above command will open the default text editor and you can edit the text in the file and save it.

----
Now that we created a new file let's check the file
```
$ ls
README.md
```
----

Let's check the status of the files with the following command.
```
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)
```
Now if you observe Git tells us that we are on master branch and we have untracked files, specifically the "README.md" file.

----

To add the untracked files to the local git repo use the following command.
```
$ git add README.md
```

The above command moves our "README.md" file from working directory to Git staging area.

----

Let's verify the status again with the following command.
```
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md
```
Now the "README.md" file is added to the staging area and is ready to be commited.

----

Now that the file is added in staging we got to commit it to the Git local repo using the following command. If we want to also add a message to the commit we'll use "-m" parameter
```
$ git commit -m "Initial Commit"
[master (root-commit) 88d240d] initial commit
1 file changed, 2 insertions(+)
create mode 100644 README.md
```
The above command says that we changed 1 file with 2 insertions.

----

Now If I do git status am in the master branch, but this time we'll not have anything to commit or add.
```
$ git status
On branch master
nothing to commit, working tree clean
```

----

### Repository [The Git Folder]
> **⚠ WARNING: We have ".git" directory where we have all git related files and folders. It has several files and folders which are used and managed exclusively by Git. It is highly recommended to stay away from this folder unless you know what you are doing.**  

Let's try to delete the .git folder and see what happens.
```
$ rm -rf .git
```

----

Let's check what files and folders we have now (Ideally the .git folder should be removed) .
```
$ ls -al
Mode                LastWriteTime           Name
----                -------------           ------
drwxr-xr-x          2/26/2021   8:31 PM     .
drwxr-xr-x          4/1/2021    2:32 PM     ..
-rw-r--r--          4/1/2021    2:32 PM     README.md
```

----

Now let's check the status of the repo.
```
$ git status
fatal: not a git repository (or any of the parent directories): .git
```
The above message is received as we don't have any .git folder.

----

### Initialization [With Existing Files]
Now let's get into the folder where we want version control. In my case I want git in my demo folder (Am already in my demo folder). So i'll first get into the demo folder and then i'll initialize git.
```
$ pwd
/Users/training/projects/demo
$ git init .
Initialized empty Git repository in /Users/training/projects/demo/.git/
```

----

Let's find the git status to check the files info which is tracked and commited, if any.
```
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)
```
In the above output we see that Git says we have 1 untracked file which is "README.md" and it also says that we are in master branch.
We see this message as it was tracked in our previous git repository but then as we deleted that repository we have a brand new git repository, starting completely fresh,

----

### Commits and messages
Let's create another file.
```
$ touch LICENSE.md
```

----

Now let's check the status of new file created and the old file which we didn't commit.
```
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        LICENSE.md
        README.md

nothing added to commit but untracked files present (use "git add" to track)
```
Now Git says that we have 2 untracked files and it also says that we are in the master branch.

----

Now instead of adding a specific file, let's add all the files at once with one single command.
```
$ git add .
```
The above comand adds all the files to the staging area.

----

Now let's check the status of the files again.
```
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   LICENSE.md
        new file:   README.md
```
In the above output we see that both the files are added to the git staging area.

----
Now let's commit whatever we have added to the repo with a commit message using "-m" parameter.
```
$ git commit -m "Initial Commit"
[master (root-commit) 4dbb0be] Initial Commit
2 files changed, 3 insertions(+)
 create mode 100644 LICENSE.md
 create mode 100644 README.md
```

### Log and show commit details
To get our listing of commits we can use "git log".
```
$ git log
commit 4dbb0beff5cbcdc35c84c822487b7c30943b9a96 (HEAD -> master)
Author: Ankit Agarwal <ankitagarwalpro@gmail.com> 
Date:   Tue Apr 13 18:37:15 2021 +0200

    Initial Commit
```
In the above output you see a long unique identifier which is a SHA-1 identifier.
Then we have a commit id then we have an author which is me, the date and time of commit and the message of commit.

----
We can get similar info, infact little extra info with the "git show command".
```
$ git show
commit 4dbb0beff5cbcdc35c84c822487b7c30943b9a96 (HEAD -> master)
Author: Ankit Agarwal <ankitagarwalpro@gmail.com> 
Date:   Tue Apr 13 18:37:15 2021 +0200

    Initial Commit
    
diff --git a/LICENSE.md b/LICENSE.md
new file mode 100644
index 0000000..30d74d2
--- /dev/null
+++ b/LICENSE.md
@@ -0,0 +1 @@
+test
\ No newline at end of file
diff --git a/README.md b/README.md
new file mode 100644
index 0000000..91a594f
--- /dev/null
+++ b/README.md
@@ -0,0 +1,2 @@
+#Demo project
+This is a test project
\ No newline at end of file
```
The above command shows the last commit and the diff containing all the changes.



Continue from video 22
C:\Users\aar6b78\Videos\Courses\Udemy Courses\github-ultimate\04 The Basics