---
layout: default
title: Common Git Commands
---
# Common Git Commands

|Command|Description|
| --- | --- |
|git init|Turns a directory into a git repository|
|git clone [https/ssh url] [optional: name]|Clones the repository|
|git status|Shows the state of repository|
|git commit -m "[Message]"|Commits the staged changes with a message|
|git commit -am|Adds and Commits the unstaged changes with a message|
|git add .|Adds all the currently modified files|
|git add -i|Launches interactive mode to add/remove/update modified/untracked files|
|git checkout -b [branch name]|Create a new branch from the current branch|
|git checkout .|Undo all local work and switch back to the head of the branch|
|git checkout <file>|Undo the file changes|
|git push origin <branch>|Push branch changes to the remote repository|
|git pull origin <branch>|Fetch and Merge remote repository branch into this branch|
|git reset --hard head|Reset to the head of the branch|
|git diff|Show new changes|
|git diff --cached|Show changes that are already staged|