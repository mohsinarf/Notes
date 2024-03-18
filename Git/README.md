## Basic Git Commands


## Stash Command

### Temporarily store changes in a stash
`git stash`

### Apply the most recently stashed changes
`git stash pop`

### List all stashed changes
`git stash list`

## Cherry-pick

### Display condensed commit history for a specific branch
`git log <branch-name> --oneline`

### Apply changes from a specific commit to the current branch
`git cherry-pick <commit-hash>`

## Fetch Command

### Download objects and refs from another repository
`git fetch <remote_name>`

### Fetch changes from a specific remote branch
`git fetch <remote_name> <branch_name>`

### Merge Changes
`git merge`

## Rebase Command

### Reapply commits on top of another base tip
`git rebase <base-branch>`

### Rebase the current branch interactively
`git rebase -i <base-branch>`

### Initialize a Git repository
`git init`

### Clone a Git repository
`git clone <Repository_link>`

### Add changes to the staging area
`git add <filename>`  
or  
`git add .`

### Commit changes
`git commit -m "Change information"`

### Push changes to a remote repository
`git push <remote_name> <branch_name>`

### Check the status of the repository
`git status`

## Branch Operations

### Switch to the master branch
`git checkout master`

### Update the local master branch with changes from the remote repository
`git pull origin master`

### Merge a branch into the current branch
`git merge <branch-name>`

### Push merged changes to the remote master branch
`git push origin master`

### Rebase current branch onto another branch
`git rebase <base-branch>`

## Configuration

### Configure user name globally
`git config --global user.name "FIRST_NAME LAST_NAME"`

### Configure user email globally
`git config --global user.email "MY_NAME@example.com"`

## Branch Related Commands

### List all local branches
`git branch`

### List all remote branches
`git branch -r`

### List all local and remote branches
`git branch -a`

### Display commit history
`git log`

### Update remote-tracking branches
`git remote update`

### List Git configuration settings
`git config --list`

## Undoing Changes

### Revert the changes introduced by the last commit
`git revert <commit-to-revert>`

### Reset the current branch to a specific state
`git reset <commit-hash>`


