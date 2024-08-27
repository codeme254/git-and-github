# git tags

In git, we can tag/label commits by creating a tag/reference to a moment in time.  
We can use tags to mark version releases to a project and a lot of other things.  

## Types of tags
There are two types of tags:
- **Lightweight tags** - they are just a name and a label that points to a particular point in time.
- **annotated tags** - store extra metadata including author's name and email, the date and a tagging message (like a commit message).

The primary use of tags is to version our projects.

## Semantic version
Semantic versioning spec outlines a standardized versioning system for software releases. It provides a consistent way for developers to give meaning to their software releases.  
The system is three numbers with two dots between them eg 3.8.2.
- **The right-most digit (2) represents patch release:** patch releases do not contain new features or significant changes. They typically signify bug fixes and other changes that do not impact how the code is used. Increment by 1 for every patch release.  
- **The middle digit represents minor release:** minor releases signify new features and functionality, everything is still backwards compatible. No breaking changes. The new functionality is optional and should not force users to rewrite their code.
- **The left digit represents major release:** major releases are for significant changes that are no longer backwards compatible. Features may be removed or changed substantially.

You can learn more about semantic version [in the official website](https://semver.org)

## Viewing tags
To view all the tags in the current repository, we can use the command:
```Bash
git tag
```

## Searching tags that match a particular pattern
We can search for tags that match a specific pattern by passing the -l flag to ```git tag``` and then pass the pattern as a string:
```Bash
git tag -l "PATTERN"
```
for example, to view all tags starting with digit 17:
```Bash
git tag -l "17*"
```

## Checking out tags
To look at the state of the repo at a particular tag:
```Bash
git checkout TAG
```
For example:
```Bash
git checkout 17.0.0
```
this will show us how the repo/project looked like at tag 17.0.0.

## Creating a lightweight tag
To create a lightweight tag, use:
```Bash
git tag TAGNAME
```
![lightweight tagging](git_tag.png)

## Creating annotated tags
We pass -a flag to ```git tag``` to create annotated tags.  
This will open the default git editor (vi, VS Code, notepad et.c) and wait for you to type detailed description of the tag, when you close that file, the tag creation will be completed.  
```Bash
git tag -a TAGNAME
```
![annotated tag waiting for the user to type and close the file](annotated_tag_1.png)

![typing annotated tag](annotated_tag_2.png)

## Tagging previous commits
We can tag previous commits using:
```Bash
git tag -a TAGNAME COMMIT_HASH
```
![Tagging previous commits](tagging_previous_commits.png)

## Deleting tags
To delete a tag -d flag to ```git tag``` and then specify the tag.  
```Bash
git tag -d TAGNAME
```
![deleting a tag](delete_a_tag.png)

## Reusing tags
If we try to reuse tags, git will give us an error.  
However, if you still want to reuse a tag, you can pass the -f flag to ```git tag``` command:

```Bash
git tag -f TAGNAME
```
![reusing a tag](reuse_tag.png)

## Pushing tags
By default, when pushing, the tags will not be included.  
To allow tags to be pushed, we pass the --tags flag:
```Bash
git push --tags
```
To push a single tag, we specify the remote name and the tag-name
```Bash
git push REMOTE_NAME TAGNAME
```
for example
```Bash
git push origin v1.1.1
```
GitHub will show you how many tags your project has:

![tags shown](pushed_tags.png)

We can click on that label to view all the tags.
