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
  


  
