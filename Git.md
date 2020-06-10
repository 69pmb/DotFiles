### 1. [Divers](#divers)
### 2. [Reset](#reset)
### 3. [Stash](#stash)
### 4. [Log](#log)
### 5. [Dots](#dots)


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
`git checkout <rev> -- file/to/restore`
* Diff with no merge commit:  
`git log --no-merges master..`
* Show diff staged:  
`git diff --cached`
* Show files of a commit:  
`git show --name-only <rev>`
* Recover a dropped stash:  
`git log --graph --oneline --decorate $( git fsck --no-reflog | awk '/dangling commit/ {print $3}' )`
* The opposite of `git add -p`:  
`git checkout --patch`
* Blame:  
`git blame <file> <rev>`
* Readable blame:  
`git gui blame`
* Use `git` in another directory:  
`git <cmd> -C <path>`
* Remove untrack files:  
`git clean -f`
* Remove whitespace changes:  
```bash
git diff -w --no-color
git apply --cached --ignore-whitespace
git checkout -- .
git reset
```
* Rebase accepting all rebased branch conflicts:  
`git rebase -X theirs <branch>`

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


# Dots
```
<rev1>..<rev2>
	Include commits that are reachable from <rev2> 
	but exclude those that are reachable from <rev1>. 
	When either <rev1> or <rev2> is omitted, it defaults to HEAD.
<rev1>...<rev2>
	Include commits that are reachable from either <rev1> or <rev2>
	but exclude those that are reachable from both. 
	When either <rev1> or <rev2> is omitted, it defaults to HEAD.
```