# Branches
In real world, we usually want to work in multiple contexts simultaneously:
- One co-worker is creating a chat functionality that we are not yet sure the client will want to use.
- Another co-worker is working on the search functionality.
- You are trying to fix a bug that is proving to be troublesome.
- The new colleague is still experimenting with the docs.
- The QA engineer is writing tests et.c.

If all these people work in a linear function, the project will be practically impossible as it would mean that one person will have to wait for the other one to finish what they are doing before they can pick up.  
This is where branches come to the rescue.  
> Branches are alternative timelines for a project, they allow you us to create separate contexts where we can try new things or even work on multiple ideas in parallel.  

Whatever happens in one branch does not affect the other branches.  
In git, we are always working inside a branch even if we don't specify a branch.

## The master branch
As discussed earlier, in git, we are always working in a branch.  
The default branch is the master branch.  
It doesn't do anything special or have any fancy powers, it's just like any other branches.  
In some projects however, the master branch is treated as the single source of truth or the official branch.

> To avoid offensive language, in 2020 GitHub renamed the default branch from master to main.
The default branch for git is still master though the Git team is exploring a potential change.

## What is HEAD?
While working with git, often times you will come across something like (HEAD -> master).  
We already know what master is (the default git branch) so what is HEAD?  
HEAD is simply a pointer that refers to the current "location" in your repository.  
At any given time in git, only one branch can be active. HEAD points to this branch.  
Switching to a different branch will make the head point to that branch.

## Viewing branches
Use the command ```git branch``` to view your existing branches.  
The active branch will have a little asterisk symbol (*) beside it and in some command line interfaces will be green in color.
![Git branch](git_branch.png)

## Creating Branches
To create a branch, we use the command:
```Bash
git branch BRANCH_NAME
```
Replace BRANCH_NAME with your preferred branch name, for example, if we want to create a branch called chapter1:
```Bash
git branch chapter1
```
This will simply create a branch but will not switch to it.  
We can prove this by running the ```git branch``` command:

![Git branching then viewing the active branches](git_new_branch.png)

We see that we now have two branches, chapter1 and master but master is the active one since it is the one with the asterisk symbol beside it.

## Switching branches
Switching branches means changing the active branch.  
To switch branches, we use the command:
```Bash
git switch BRANCH_NAME
```
Replace BRANCH_NAME with the name of the branch, for example, if we want to make chapter1 the active branch (switching to it):
```Bash
git switch chapter1
```
This will change the active branch from master to chapter1, we can prove this by running the ```git branch``` command:

![Git switch](git_switch.png)

We now see the asterisk symbol beside the chapter1 branch which means that this branch is the active branch.

## Switching branches with unstaged changes
It is always important to stage and commit changes before switching branches.  
Switching branches before adding changes to the staging area and commiting them will most likely give us an error.  
However, in some situations, we find ourselves wanting to switch branches, yet we are not yet ready to add and commit the current changes, this can be fixed using a technique called stashing (more on this later).  
For now, just understand that it is important you add and commit changes before switching branches, even if git doesn't give an error back when you try to do this, it is important to add and commit changes before changing branches to avoid carrying the changes to another branch.

## Deleting branches
After working on branches and merging the changes to the main branch (more about merging later), usually we don't need that branch anymore, and it is safe to delete it.  
To delete a branch, we use the git branch command and pass the -d flag.  
```Bash
git branch -d BRANCH_NAME
```
Replace BRANCH_NAME with the name of the branch you want to delete, for example, to delete the branch chapter1:
```Bash
git branch -d chapter1
```

![Deleting a branch](delete_a_branch.png)

Using -d flag to delete a branch that has not been merged might give us an error, if are sure we want to delete the branch, we can force git to delete it by passing -D flag to the ```git branch``` command:
```Bash
git branch -D BRANCH_NAME
```
Replace BRANCH_NAME with the name of the branch you want to force delete, for example, if the name of the branch is chapter1:

```Bash
git branch -D chapter1
```

## Renaming branches
To rename a branch, we pass the -m flag to the git branch command.  
For this to work, you need to be inside the branch.

```Bash
git branch -m NEW_BRANCH_NAME
```

Let's rename the master branch from 'master' to 'main':

- First, switch to the master branch:
```Bash
git switch master
```
- Rename the branch:
```Bash
git branch -m main
```
- We can confirm this has worked by running the ```git branch``` command to list the branches, and we will indeed see that master has been renamed to main.
