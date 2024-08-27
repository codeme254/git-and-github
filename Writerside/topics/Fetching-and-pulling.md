# Fetching and Pulling

## Remote Tracking Branches
When we clone a repository from GitHub, we will have the branch eg 'master' and we will also have 'origin/master' branch.  
The 'origin/master' is a 'remote tracking branch', it's a reference to the state of the master branch in the remote.  
We can't move this branch ourselves.  
These branches follow the pattern <remote_name>/<branch_name>  
To view these branches, we can use the command:
```Bash
git branch -r
```

![Remote branches](remote_branches.png)

## Checking out remote tracking branches
When we make changes and commit them, the local branch is what gets moved and not the remote tracking branch.  
This is the reason why often times we come across a message like "your branch is ahead of origin/master by 1 commit".

![Branch ahead](branch_ahead.png)

We can always travel back to the remote branch locally using:
```Bash
git switch REMOTE_BRANCH_NAME
```
for example:
```Bash
git switch origin/master
```

## Working with remote branches
Suppose we clone a repository that has multiple branches from GitHub, how do we work with these branches locally?  
Here is the thing, when we clone this repository and run ```git branch```, we will only see the 'master' branch. So how do we get to be able to work on the other branches?  

![git branch](git_branch_2.png)

Here is the simple answer: when you clone a repository, you will have all the data and history at the moment but that doesn't mean it's all in your workspace.  
Running ```git branch -r```, we will be able to see all of these branches.  

![viewing all the remote branches](git_branch_r.png)

Our local repo knows about all of these branches, and it has a remote tracking reference which can tell you where all of these branches are, but we can't see the local branches, ie, we can only see origin/chapter1, but we can't see chapter1.  
Now how do we create a branch locally to track 'origin/chapter1' for example?  
We could use:
```Bash
git checkout origin/chapter1
```
but that will put us in a detached HEAD.  
The solution is to use ```git switch BRANCH_NAME```:  
For example, if the remote is 'origin/chapter1' then the BRANCH_NAME will be replaced by 'chapter1', if the remote is 'origin/bugfix', then the BRANCH_NAME will be replaced with 'bugfix'.
```Bash
git switch chapter1
```
This is going to set up a local branch called 'chapter1' which will track the remote branch 'origin/chapter1'.

![git switch origin branches](git_switch_2.png)

and that's it, we now have a local branch 'chapter1' which we can work in without interfering with 'origin/chapter1' and push changes to 'origin/chapter1'.  

![editing in the branch](editing_in_branch.png)

## git fetch
```git fetch``` takes remote changes and brings them to the local repository, they are not automatically integrated into our working files.  
It will let you see what others have been working on without having to merge those changes into your local repo.  

```Bash
git fetch REMOTE
```
```Bash
git fetch
```
or
```Bash
git fetch origin
```
If we don't specify the remote, it will use 'origin' as the default.
![git fetch](git_fetch.png)

We can also fetch from a specific branch in which case we have to specify the branch name and the origin name.
```Bash
git fetch REMOTE_NAME BRANCH_NAME
```
Assuming we have a branch called chapter2 and the remote is called origin
```Bash
git fetch origin chapter2
```

## git pull
```git pull``` is another command we can use to retrieve changes from a remote repository.  
Unlike fetch, pull actually updates the head branch with whatever changes are retrieved from the remote and actually updates our working files.  
Where we run git pull matters, this is because the changes from git pull will be merged in our working directory in the specific branch the command was called from.  
```Bash
git pull REMOTE BRANCH
```
for example
```Bash
git pull origin chapter2
```
If we run git pull without specifying the branch and the origin, git will assume the following:
- Remote will default to origin.
- Branch will default to whatever tracking connection is configured for your current branch.

This means that if our remote is called origin for example, and we are currently in a branch called chapter2, and we want to pull from chapter 2 in the remote, we can simply run:
```Bash
git pull
```