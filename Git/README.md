

## Basic Git Commands

`git init`

`git clone <Repsoitory_link>`          // Clone git repository


`git add <filename>`                  // Staging

or

`git add .`

`git commit -m "Change information"`  // Commit changes

`git push <remote_name> <branch_name>`

`git status`

## Merge branch

`git checkout master`

`git pull origin master`

`git merge <branch-name>`

`git push origin master`

## Configure

`git config --global user.name "FIRST_NAME LAST_NAME"`

`git config --global user.email "MY_NAME@example.com"`

## Branch related commands

`git branch`      // list all the local branches

`git branch -r`   // list all the remote branches   

`git branch -a`	  // list all the local and remote branches

`git log`

`git remote update`

`git config --list`

## Undo the Last commit
`git revert <commit-to-revert.`  // create a new commit that undo all the changes
