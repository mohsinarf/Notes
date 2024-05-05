
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


```
1. 𝐠𝐢𝐭 𝐝𝐢𝐟𝐟: Show file differences not yet staged.
2. 𝐠𝐢𝐭 𝐜𝐨𝐦𝐦𝐢𝐭 -𝐚 -𝐦 "𝐜𝐨𝐦𝐦𝐢𝐭 𝐦𝐞𝐬𝐬𝐚𝐠𝐞": Commit all tracked changes with a message.
3. 𝐠𝐢𝐭 𝐬𝐭𝐚𝐭𝐮𝐬: Show the state of your working directory.
4. 𝐠𝐢𝐭 𝐚𝐝𝐝 𝐟𝐢𝐥𝐞_𝐩𝐚𝐭𝐡: Add file(s) to the staging area.
5. 𝐠𝐢𝐭 𝐜𝐡𝐞𝐜𝐤𝐨𝐮𝐭 -𝐛 𝐛𝐫𝐚𝐧𝐜𝐡_𝐧𝐚𝐦𝐞: Create and switch to a new branch.
6. 𝐠𝐢𝐭 𝐜𝐡𝐞𝐜𝐤𝐨𝐮𝐭 𝐛𝐫𝐚𝐧𝐜𝐡_𝐧𝐚𝐦𝐞: Switch to an existing branch.
7. 𝐠𝐢𝐭 𝐜𝐨𝐦𝐦𝐢𝐭 --𝐚𝐦𝐞𝐧𝐝: Modify the last commit.
8. 𝐠𝐢𝐭 𝐩𝐮𝐬𝐡 𝐨𝐫𝐢𝐠𝐢𝐧 𝐛𝐫𝐚𝐧𝐜𝐡_𝐧𝐚𝐦𝐞: Push a branch to a remote.
9. 𝐠𝐢𝐭 𝐩𝐮𝐥𝐥: Fetch and merge remote changes.
10. 𝐠𝐢𝐭 𝐫𝐞𝐛𝐚𝐬𝐞 -𝐢: Rebase interactively, rewrite commit history.
11. 𝐠𝐢𝐭 𝐜𝐥𝐨𝐧𝐞: Create a local copy of a remote repo.
12. 𝐠𝐢𝐭 𝐦𝐞𝐫𝐠𝐞: Merge branches together.
13. 𝐠𝐢𝐭 𝐥𝐨𝐠 --𝐬𝐭𝐚𝐭: Show commit logs with stats.
14. 𝐠𝐢𝐭 𝐬𝐭𝐚𝐬𝐡: Stash changes for later.
15. 𝐠𝐢𝐭 𝐬𝐭𝐚𝐬𝐡 𝐩𝐨𝐩: Apply and remove stashed changes.
16. 𝐠𝐢𝐭 𝐬𝐡𝐨𝐰 𝐜𝐨𝐦𝐦𝐢𝐭_𝐢𝐝: Show details about a commit.
17. 𝐠𝐢𝐭 𝐫𝐞𝐬𝐞𝐭 𝐇𝐄𝐀𝐃~1: Undo the last commit, preserving changes locally.
18. 𝐠𝐢𝐭 𝐟𝐨𝐫𝐦𝐚𝐭-𝐩𝐚𝐭𝐜𝐡 -1 𝐜𝐨𝐦𝐦𝐢𝐭_𝐢𝐝: Create a patch file for a specific commit.
19. 𝐠𝐢𝐭 𝐚𝐩𝐩𝐥𝐲 𝐩𝐚𝐭𝐜𝐡_𝐟𝐢𝐥𝐞_𝐧𝐚𝐦𝐞: Apply changes from a patch file.
20. 𝐠𝐢𝐭 𝐛𝐫𝐚𝐧𝐜𝐡 -𝐃 𝐛𝐫𝐚𝐧𝐜𝐡_𝐧𝐚𝐦𝐞: Delete a branch forcefully.
21. 𝐠𝐢𝐭 𝐫𝐞𝐬𝐞𝐭: Undo commits by moving branch reference.
22. 𝐠𝐢𝐭 𝐫𝐞𝐯𝐞𝐫𝐭: Undo commits by creating a new commit.
23. 𝐠𝐢𝐭 𝐜𝐡𝐞𝐫𝐫𝐲-𝐩𝐢𝐜𝐤 𝐜𝐨𝐦𝐦𝐢𝐭_𝐢𝐝: Apply changes from a specific commit.
24. 𝐠𝐢𝐭 𝐛𝐫𝐚𝐧𝐜𝐡: Lists branches.
25. 𝐠𝐢𝐭 𝐫𝐞𝐬𝐞𝐭 --𝐡𝐚𝐫𝐝: Resets everything to a previous commit, erasing all uncommitted changes.
```


