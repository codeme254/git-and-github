# git diff - comparing changes
We can use the git diff command to view changes between commits, branches, files, working directories et.c.  
We often use git diff alongside commands like git status and git log, to get a better picture of a repository and how it has changed over time.  
without additional options, git diff lists all the changes in our working directory that are not staged for the next commit.

```Bash
git diff
```
![Git diff](git-diff.png)

## Guide to reading diffs
In the first line of the diff output, we see:
```text
diff --git a/outline.txt b/outline.txt
```
This is git telling us what it is comparing, most of the time (but not all the time), it is usually two versions of the same file. It also declares one file as a and the other as b.

Next, we see:
```text
--- a/outline.txt
+++ b/outline.txt
```
This is git telling us that changes in file a will be indicated with - (before), and changes in file b will be indicated with + (after).

The next part is chunks, a diff won't show the entire file content, but instead only shows portions or chunks that were modified.  
The chunk will also include some lines before and after a change to provide some context.  
Each chunk will start with a chunk header found between @@ and @@.  
The chunk header will look as so:
```text
@@ -1,3 +1,5 @@
```
This is git telling us that from file a, it is going to extract 3 lines starting from line 1 (-1, 3) and from the file b it is going to extract 5 lines starting from line 1 (+1, 5).

Next is changes: every line that changed between the two files is marked with either + or - symbol.  
Lines that begin with - come from file a and those that begin with + come from file b.

## Viewing unstaged changes with git diff
Running ```git diff``` without passing any options will show the changes yet to be added to index/staging area (unstaged changes).
![Git diff](git-diff.png)

## Viewing working directory changes since your last commit
Passing HEAD to ```git diff``` will show all changes in the working tree since your last commit. This includes staged and unstaged changes.
```Bash
git diff HEAD
```

## Viewing staged changes
Passing --staged flag to ```git diff``` or --cached will list all changes between the staging area and the last commit.  
It's like asking git "show me what will be included in my commit if I run ```git commit``` right now".

```Bash
git diff --staged
```
![git diff --staged](git_diff_staged.png)

## Comparing branches
We can also compare changes between branches:
```Bash
git diff BRACH_NAME_1 BRANCH_NAME_2
```
It is important to note that the order of the branches matter

```Bash
git diff main chapter1
```
we can also separate the branch names using two periods:
```Bash
git diff main..chapter1
```

## Comparing changes between commits
We can also prepare changes between two commits.  
First use ```git log --oneline``` to list all the commits.  
Then copy the hashes of the two commits you want to compare and pass them to the ```git diff``` command as shown:

```Bash
git diff a871c7e 24c3f04
```

```Bash
git diff commit_1_hash commit_2_hash
```
![Diffing two commits](diffing_two_commits.png)
