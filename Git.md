### 1. [Divers](#divers)
### 2. [Reset](#reset)
### 3. [Stash](#stash)
### 4. [Log](#log)


## Divers
* Show Url:  
`git remote show origin`
* Delete orphean branch:  
`git remote prune origin`
* Delete remote branch:  
`git push -d origin <branch>`  
`git branch -d <branch>`
* Undo a commit and redo:  
```bash
git commit -m "Something terribly misguided"
git reset HEAD~
<< edit files as necessary >>
git add ...
git commit -c ORIG_HEAD
```
* rebase a merged branch (Preserve merge commits):  
`git rebase -i --rebase-merges HEAD~`
* Create a new branch:  
`git checkout -b [name_of_your_new_branch]`
* Revert specific file to specific commit:  
`git checkout 1abdf2ae -- file/to/restore`
* Show files of a commit:  
`git show --name-only 4d068191`
* Recover a dropped stash in Git:  
`git log --graph --oneline --decorate $( git fsck --no-reflog | awk '/dangling commit/ {print $3}' )`


## Reset
* Remove from stage:  
`git reset HEAD [path]`
* Remove file from add:  
`git reset <file>`
* Reset all modifications:  
`git reset --hard`


## Stash  
* Stash with message:  
`git stash save <message>`
* Stash untracked files:  
`git stash -u`
* List stash:  
`git stash list`
* Clean stash:  
`git stash clear`
* Stash specific file:  
`git stash push -m <name> <path>`
* Show full diff:  
`git stash show -p`


## Log
* Show history if files move:  
`git log --follow`
* Git history of directory:  
`git lg -- path/to/folder`
* Search in diff:  
`git log -p -S'' --name-only`
* Search in commit message:  
`git log --all --grep='text'`
