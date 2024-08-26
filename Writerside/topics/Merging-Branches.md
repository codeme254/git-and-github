# Merging Branches
Almost all the times, we want to incorporate things we've done in our branch/branches into another branch (destination branch).  
This destination branch is usually the source of truth for example the master branch, main branch et.c.  
To merge branches:
- First, we switch to the branch where we want to merge the current branch.  
- We use the command:
```Bash
git merge BRANCH_NAME
```
where BRANCH_NAME is the name of the branch we want to merge to the current active branch.  
Assuming our official branch is called 'main' and we have content in a branch called 'chapter1' that we want to merge into main:
- We start by switching to the main branch where we want to merge the changes from 'chapter1'.
```Bash
git switch main
```
- We then use the ```git merge``` to merge the content from chapter1 to main.
```Bash
git merge chapter1
```

![Git merge](git_merge.png)

## What is a Fast Forward merge technique?
Let's look at this scenario:
- You have two branches, 'main' and 'chapter1'.
- The 'main' branch has not had any changes or any new commits since you branched off to create the 'chapter1' branch.
- When you merge 'chapter1' back to 'main', git sees that 'main' can be 'fast-forwarded' to include all the commits from 'chapter1'.
- Git will simply update the 'main' branch pointer to point to the latest commit on the 'chapter1' branch.

## Merge commit (three-way merge)
Let's look at another scenario:
- You are working in the 'chapter1' branch.
- Bob, who is your co-worker makes changes to the 'main' branch and commits these changes before you merge 'chapter1' back to 'main'.
- This will now create a situation where, during merging, the 'main' branch has content that 'chapter1' branch doesn't have and 'chapter1' branch has content that 'main' doesn't have.
- This is common and there is nothing wrong with it, in this case, git will perform a three-way merge and git will prompt you to provide a merge commit.
- Git will open your default text editor (vi or VS Code or notepad et.c) and will wait for you to write the commit message there, when the file is closed, git will complete the commit.

![Three-way commit](git_three_way_commit.png)

## Merge conflicts
Merge conflicts occur when, during merging, git is unable to reconcile differences between two branches.  
### When Merge Conflicts occur:
- **Concurrent changes** - if two branches have changes to the same lines of a file, Git can't decide which change to keep.
- **Conflicting edits** - if one branch edits a file that the other branch deletes, Git can't automatically resolve the conflict.
- **Diverged Histories** - if the histories of the branches have diverged significantly, merge conflicts are more likely to occur.

## Conflict markers
- The content from your current HEAD (the branch you are trying to merge content into) is displayed between <<<<<HEAD and ======.
- The content from the branch you are trying to merge from is displayed between ========== and >>>>>>>>>BRANCH_NAME symbols where BRANCH_NAME is the name of the branch you are trying to merge from.

![Merge Conflict](merg_conflicts.png)

- Merge conflicts are normal and can be resolved, they don't mean there is something wrong with our repository.
- If there is a merge conflict, git will notify you in the command line.

![merge conflict in the command line](merge_conflicts_2.png)

## How to fix merge conflicts
- Open up the file(s) with merge conflicts.
- Edit the file(s) to remove the conflicts. Decide which branch's content you want to keep in each conflict or keep the content from both.
- Remove the conflict markers in the document.
- Add your changes and then make a commit.

In this case, let's keep both changes:

![Resolved Merge Conflict](resolved_merge_conflict.png)

We then add and commit changes to capture the content after resolving the conflict.

![adding and commit after resolving conflict](adding_and_committing_after_resolving_confilicts.png)
