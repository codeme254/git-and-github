# Basics of adding and committing
Committing is the most important feature of git.  
A commit is a checkpoint in time, it is a snapshot of changes in your repository.  
The commit process involves recording snapshots of your project at various stages, allowing you to track progress, revert changes and collaborate with others efficiently.  
Before jumping to committing changes, which is a fundamental aspect of using Git, we need to first understand what a Git repo is.

## What is a Git Repo
A git repo is a workspace which tracks and manages files within a folder.  
Anytime we want to use Git with a project, app, et.c, we need to create a new git repository.  
We can have as many repos as we want on our machine all with separate history and content, however, it is important to note that a project should have a single Git repository.

## Creating/Initializing a Git repository
To initialize a git repository:
- Open the terminal or command prompt in your project directory, you can also open your command line tool and navigate to your project directory.
- Run the command:
```Bash
git init
```
- The command will initialize a git repository in the project folder, this is where git will track and manage changes to files in your project.  
NOTE: Initializing a git repository is something you do once per project. Running the command ```git init``` in a project that contains a git repository will make git initialize a repository within a repository.

_Tip: use ```git status``` to confirm whether your project has a git repository or not, more about ```git status``` later._
When you run the ```git status``` command and get the message "fatal: not a git repository..." being returned, then it means that the project does not have a git repository, you can go ahead and initialize one.  
If you get anything else back, then it means that the current directory contains a git repository, therefore no need to initialize one again.  
![Initializing a git repository](git_init.png)
_if our project does not contain a git repository, we initialize one, we simply use the ```git status``` command to check whether our project contains a git repository, if it doesn't,then we initialize one_

## Adding changes to the staging area
In Git, the staging area also known as the index is an intermediate space where you can organize changes before committing them to the repository.  
When you make changes to files in your working directory, those changes aren't immediately included in the next commit. Instead, you need to add these changes to the staging area using the ```git add``` command.  
Once you are satisfied with the changes, you can commit them to the repository.  
To add changes, run the command ```git add FILE_NAME``` to add changes to the staging area. Replace FILE_NAME with the name of the file, for example, in my project, I have a file chapter1.txt with changes that I would like to add to the staging area.  
```Bash
git add chapter1.txt
```
You can also add multiple files to the staging area, simply list all the files as shown:
```Bash
git add chapter1.txt chapter2.txt chapter3.txt chapter4.txt
```
If you want to add all the files in one go, you can use the period symbol or -A flag.
```Bash
git add -A
```
or
```Bash
git add .
```

## Committing changes
As discussed earlier, committing is the most fundamental aspect of git.  
A commit in git is basically a snapshot of your project at a particular point in time.  

### Key components of a commit
- **A hash**: a unique identifier for each commit
- **Commit message**: a descriptive message that explains the purpose of the commit.
- **Author**: the person who made the commit.
- **Timestamp**: the date and time when the commit was made.

Committing will only work if there are changes in the staging area.  
To commit, we use the ```git commit``` command.  
Running ```git commit``` without passing any options will open a text editor (vi by default) for you to type in the message.  
This approach is not beginner-friendly as most beginners find it hard to use vi, we can configure git to use a text editor of our choosing (more about this later).  
Luckily, there is a -m flag that allows us to pass a commit message directly without having to open a text editor.  
```Bash
git commit -m "MESSAGE"
```
Replace MESSAGE with a short descriptive commit message of your choosing, for example:
```Bash
git commit -m "write chapters 1 to 5"
```
![Git commit](git_commit.png)

## Changing the commit editor from vi to something else
In some projects, you will be required to use comprehensive commit messages and therefore passing the commit message using the -m flag will be very inefficient to write these huge commit messages.  
In such cases, we need a text editor to efficiently describe our commits in details, git uses vi text editor by default which is not beginner-friendly.  
We can change the default text editor to use VS Code for example or notepad in windows.  
To configure the default text editor, we use the ```git config --global core.editor``` command.

### Configuring VS Code as the core git editor for commit messages
```Bash
git config --global core.editor "code --wait"
```
now when we run ```git commit```, instead of git opening vi, it will open VS code for us to type our comprehensive commit message.  
the --wait flag is used to tell git to wait for us to make changes and close vs code before it continues.

### Configuring notepad as the core editor for commit messages
```Bash
git config --global core.editor "notepad"
```
now when we run ```git commit```, instead of git opening vi, it will open notepad, we can then type there our comprehensive commit message, when we close it, git will continue to the next step.

## Viewing past commits
We can view past commits and even travel back to these commits (more about this later).  
To view past commits, we use the command:
```Bash
git log
```
![Git log](git_log.png)

To view past commits in a summarized format, we pass the flag --oneline to the ```git log``` command.
```Bash
git log --oneline
```
![Git log oneline](git_log_2.png)

## Adding and commiting
Now that we are inside a git repository, each time we make changes and we are happy with these changes, we add the changes to the staging area and commit them to our git repository.  
Assume we edit chapter1.txt, to notify git of these changes, we add the changes to the index and commit the changes as shown:

![adding and committing](add_and_commit.png)

We can also add and commit using a shortcut:
```Bash
git commit -m "COMMIT_MESSAGE" FILE_NAME
```
![adding and commiting shortcut](add_and_commit-2.png)

We can also list files with the shortcut:

```Bash
git commit -m "COMMIT_MESSAGE" FILE_NAME_1 FILE_NAME_2 FILE_NAME_N
```

If we want to commit all the files in the working directory, there is another shortcut:

```Bash
git commit -am "COMMIT_MESSAGE"
```
![Adding and committing everything shortcut](add_and_commit_3.png)