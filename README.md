# GitLearning

## git project stages :->

A Git project can be thought of as having three parts:

A Working Directory: where you'll be doing all the work: creating, editing, deleting and organizing files.

A Staging Area: where you'll list changes you make to the working directory

A Repository: where Git permanently stores those changes as different versions of the project

## Basic Git Command:

Use Git commands to help keep track of changes made to a project:

**git init** creates a new Git repository

**git status** inspects the contents of the working directory and staging area

**git add** adds files from the working directory to the staging area

**git diff** shows the difference between the working directory and the staging area

**git commit** permanently stores file changes from the staging area in the repository

**git log** shows a list of all previous commits


The format of the log output is very flexible. For example to output each commit on a single line the command is 

`git log --pretty=format:"%h %an %ar - %s"`


# Git Stash 

Here are some of the useful tricks I learned about Git stash last week.

1. Git stash save
2. Git stash list
3. Git stash apply
4. Git stash pop
5. Git stash show
6. Git stash branch <name>
7. Git stash clear
8. Git stash drop
  
## Git stash save

This command is like Git stash. But this command comes with various options. I will discuss some important options in this post.

## Git stash with message

```
git stash save “Your stash message”.
```

## Stashing untracked files

 ### You can also stash untracked files.

```
git stash save -u 
or
git stash save --include-untracked
```

## Git stash list

```
git stash list
```

You can see the list of stashes made. And the most recent stash made is in the top.

## Git stash apply

This command takes the top most stash in the stack and applies it to the repo. In our case it is ```stash@{0}```

If you want to apply some other stash you can specify the stash id.

Here’s the example:

```
git stash apply stash@{1}
```

## Git stash pop

This command is very similar to stash apply but it deletes the stash from the stack after it is applied.

Likewise, if you want a particular stash to pop you can specify the stash id.

```
git stash pop stash@{1}
```

## Git stash show

This command shows the summary of the stash diffs. The above command considers only the latest stash.
 
 If you want to see the full diff, you can use

```
git stash show -p
```

Likewise with other commands, you can also specify the stash id to get the diff summary.

```
git stash show stash@{1}
```

## Git stash branch <name>
 
This command creates a new branch with the latest stash, and then deletes the latest stash ( like stash pop).

If you need a particular stash you can specify the stash id.

```
git stash branch <name> stash@{1}
```

## Git stash clear

This command deletes all the stashes made in the repo. It maybe impossible to revert.

## Git stash drop

This command deletes the latest stash from the stack. But use it with caution, it maybe be difficult to revert.

You can also specify the stash id.

```
git stash drop stash@{1}
```

## How to discard the last commit ?

- ```git reset --soft 852309``` will remove all commits after commit 852309 and will bring all changed code after that into the staging area. You don’t need to use the full hash of a commit. All commits after this commit are then removed from git history.

- ```git reset --mixed 852309``` will remove all commits after commit 852309 and will bring the changed code after that to the working area. This command is the same as git reset 852309.

- ```git reset --hard 852309``` will remove all commits after commit 852309 and destroy all changed code after that. This will also remove changed file in working or staging area. Hence git reset --hard HEAD is also used to get rid of all the changes whether it is inside the working area or the staging area. One important thing to remember is that all untracked files (newly created files) will not be removed.


## How to remove the mistakenly added file from the commit ?

- First use the soft reset and bring the commit chnages to the staging area using below command 

```git reset --soft HEAD^ 
```
or
```
git reset --soft HEAD~1
```

- Then reset the unwanted files in order to leave them out from the commit:

```
git reset HEAD path/to/unwanted_file
```

Now commit again, you can even re-use the same commit message:

```
git commit -c ORIG_HEAD  
```

Using above method you will be creating new commit.**If this is your last commit and you want to completely delete the file from your local and the remote repository, you can:**

- remove the file ```git rm <file>```
- commit with amend flag: ```git commit --amend```

*The amend flag tells git to commit again, but "merge" (not in the sense of merging two branches) this commit with the last commit.*





## How to correct the spelling mistake on branch name

We can rename the branch name on local using below command 

```
git branch -m feature-brunch feature-branch
```

If you have already pushed this branch, there are a couple of extra steps required. We need to delete the old branch from the remote and push up the new one:

```
git push origin --delete feature-brunch
git push origin feature-branch
```

## 

