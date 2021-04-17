# Ankit Agarwal
## __Git_ Commands, Most Used_

[![N|Solid](https://icons.iconarchive.com/icons/tatice/operating-systems/256/Linux-icon.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)


- [About Git](#about-git)
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



# About git
Git is a free and open source version control system, originally created by Linus Torvalds in 2005. Unlike older centralized version control systems such as SVN and CVS, Git is distributed: every developer has the full history of their code repository locally. This makes the initial clone of the repository slower, but subsequent operations such as commit, blame, diff, merge, and log dramatically faster.

Git also has excellent support for branching, merging, and rewriting repository history, which has lead to many innovative and powerful workflows and tools. Pull requests are one such popular tool that allow teams to collaborate on Git branches and efficiently review each others code. Git is the most widely used version control system in the world today and is considered the modern standard for software development.
## Origin
In Git, "origin" is a shorthand name for the remote repository that a project was originally cloned from. More precisely, it is used instead of that original repository's URL - and thereby makes referencing much easier. Note that origin is by no means a "magical" name, but just a standard convention.

# How Git works
Here is a basic overview of how Git works:

1. Create a "repository" (project) with a git hosting tool (like Bitbucket)
2. Copy (or clone) the repository to your local machine
3. Add a file to your local repo and "commit" (save) the changes
4. "Push" your changes to your master branch
5. Make a change to your file with a git hosting tool and commit
6. "Pull" the changes to your local machine
7. Create a "branch" (version), make a change, commit the change
8. Open a "pull request" (propose changes to the master branch)
9. "Merge" your branch to the master branch

# Working with Git
## The Basics
### Initialization [The Basic Workflow]

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

### Express Commit Combine Commands
Now let's try to modify an already created file. In our case let's modify "README.md" file.
```
$ touch README.md
```
Made some changes in the "README.md" file and saved it.

----

Now let's check the status of Git using the below command:
```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```
The above output says that we are in the master branch. If you observe in the before steps when you create a new file it'll be displayed as untracked but now we see it as modified file. This is how we see differences between tracked and untracked files in Git.

----

Now to see the files that Git is tracking let's use the below commands.
```
$ git ls-files
LICENSE.md
README.md
```
In the above output if you see Git tells us that we have 2 files being tracked, which is LICENSE file and README file.

----

Now let's create a new file to see what happens.
```
$ touch newfile.txt
$ ls
LICENSE.md README.md newfile
```
In the above output we see that now we have 3 files in the current directory.

----

Now let's see the status of the newly created file.
```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        newfile.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
Now if we observe Git tells us that now we have 1 modified file (README.md) and 1 Untracked file (newfile.txt).

----

Now let's check the files which Git is tracking.
```
$ git ls-files
LICENSE.md
README.md
```
Now in the above output we see that Git says that it only tracking LICENSE.md and README.md files but not the newfile.txt

----

Now let's remove the newly created file (newfile.txt) and get back to the initial state.
```
$ rm newfile.txt
```

----

Now let's check the status again.
```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```
Now after delting the newfile.txt we again see the status of the modified file which is README.md. The reason for creating and deleting the newfile.txt was for giving a clear understanding of tracked files and untracked files.

----

Till now we were adding files individually and then commiting it. Now we'll add and then commit it together with a single command. To add commit message we use "-m" parameter here and then enter our message.
```
$ git commit -a -m "updating README"
[master 25817c3] updating README
1 file changed, 3 insertions(+), 1 deletion(-)
```
Here I am adding the changes made in a file using "-a", then adding a commit message using "-m" and then commiting the file to the staging area.

----

Now let's check the Git logs
```
$ git log
commit 25817c34efaf4c912a0b9209aa0245e17556caa9 (HEAD ->master)
Author: Ankit Agarwal <ankitagarwalpro@gmail.com> 
Date:   Thu Apr 15 07:34:09 2021 +0200

  updating README
  
commit 4dbb0beff5cbcdc35c84c822487b7c30943b9a96
Author: Ankit Agarwal <ankitagarwalpro@gmail.com> 
Date:   Tue Apr 13 18:37:15 2021 +0200
  
  Initial Commit   
```
Now we see we have 2 commits so far being the most recent at the top.

----

### Backing Out [Recovering From Mistakes]
Let's Check if we are in our demo folder, then check git status, make changes to the README file and check the git status again.
```
$ pwd 
/Users/training/projects/demo
$ git status
On branch master
nothing to commit, working tree clean
$ touch README.md
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```
Now we see we have a modified file (README.md)

----

Let's add it to the staging area and check the status.
```
$ git add .
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md
```
Now we see we have modified file with changes to be commited.

----

Now I don't want those changes to be commited and so I will unstage those changes using "git reset" command.
```
$ git reset HEAD README.md
Unstaged changes after reset:
M       README.md
```
Using the above command we have unstaged the changes for README file. Git says that the stages have been reset.
Now in this case the newly added text will still be there as we've just unstaged it.

----

Now let's check the status
```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```
It says we have 1 modified file.

----

We don't need any of those changes. To discard those changes entirely and revert back to last known good state of that file which is in git repository let's use the following command.
```
$ git checkout -- README.md
```
If you don't see anything in the output, then that means the changes are reverted back correctly.

----

Now let's check the Git status again.
```
$ git status
On branch master
nothing to commit, working tree clean
```




