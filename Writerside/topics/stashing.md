# Stashing
Let's take a look at this scenario:
- You are working on a repository.
- You make some commits in the master/main branch.
- You then create a new branch called 'feature' and switch to it.
- You do some work on this 'feature' branch, but before you are done, your boss calls you and asks you to fix a spelling error in another branch called 'bugfix'.
- You are not yet ready to commit the work in the 'feature' branch, and you urgently need to fix this spelling error in the 'bugfix' branch, so what do you do?

If you decide to switch to the 'bugfix' branch without committing the latest changes in 'feature' branch, two things might happen:
- Changes from 'feature' branch will come with you to the 'bugfix' branch if there are no conflicts _(bad practice)_.
- Git won't let you switch if it detects potential conflicts.

We can decide to commit the changes in the 'feature' branch but remember, we are not yet ready to commit these changes, so what do we do?

## Stashing to the rescue
Git provides an easy way of stashing these uncommitted changes so that we can return to them later without having to make unnecessary commits.

```git stash``` is a command that helps you save changes that you are not ready to commit.  
You can stash these changes and come to them later.

To stash your changes, simply run:
```Bash
git stash
```
or
```Bash
git stash save
```
And that's it! You can now switch to the 'bugfix' branch and fix that spelling error without having to make unnecessary commits in your feature branch!

![git stash](git_stash.png)

## git stash pop
You are done fixing the spelling error in the 'bugfix' branch. You are now ready to continue working in the 'feature' branch.  
When you switch back to the 'feature' branch, you won't see the stashed changes.  
This is perfectly ok, nothing has broken, you just need to 'bring back' the stashed changes, that's exactly what our next command does.

```Bash
git stash pop
```
This command removes the most recently stashed changes in your stash and re-apply them to your working copy.
![git stash pop](git_stash_pop.png)

## Stashing multiple times
You can add multiple stashes onto a stack of stashes.  
They will be stashed in the order you added them.  
You can view what is in the stash using the command:
```Bash
git stash list
```
![git stash list](git_stash_list.png)

To apply a specific stash:
```Bash
git stash apply stash@{ID}
```
Replace ID with your specific stash id, for example, if we want to apply the stash with ID 3:
```Bash
git stash apply stash@{3}
```
![git stash apply](git_stash_apply.png)

## Dropping stashes
We can delete a particular stash if we want using the command:
```Bash
git stash drop stash@{ID}
```
Replace ID with the id of the stash you want to delete, for example, if you want to delete stash with ID 2:
```Bash
git stash drop stash@{2}
```
![git stash drop](git_stash_drop.png)

## Dropping the entire stash
We can remove everything from the stash using the command:
```Bash
git stash clear
```