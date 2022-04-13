---
title: Git commands
---

### 1. [Divers](#divers)

### 2. [Reset](#reset)

### 3. [Stash](#stash)

### 4. [Log](#log)

### 5. [Dots](#dots)

### 6. [Filter-repo](#filter-repo)

## Divers

-   Show Url:  
    `git remote show origin`
-   Delete orphean branch:  
    `git remote prune origin`
-   Delete remote branch:  
    `git push -d origin <branch>`  
    `git branch -d <branch>`
-   Undo a commit and redo:

```bash
git commit -m "Something terribly misguided"
git reset HEAD~
<< edit files as necessary >>
git add ...
git commit -c ORIG_HEAD
```

-   rebase a merged branch (Preserve merge commits):  
    `git rebase -i --rebase-merges HEAD~`
-   Create a new branch:  
    `git checkout -b [name_of_your_new_branch]`
-   Revert specific file to specific commit:  
    `git checkout <rev> -- file/to/restore`
-   Diff with no merge commit:  
    `git log --no-merges master..`
-   Show diff staged:  
    `git diff --cached`
-   Show files of a commit:  
    `git show --name-only <rev>`
-   Recover a dropped stash:  
    `git log --graph --oneline --decorate $( git fsck --no-reflog | awk '/dangling commit/ {print $3}' )`
-   The opposite of `git add -p`:  
    `git checkout --patch`
-   Blame:  
    `git blame <file> <rev>`
-   Readable blame:  
    `git gui blame`
-   Use `git` in another directory:  
    `git <cmd> -C <path>`
-   Mark file as unchanged, ie the file will be ignored but kept:  
    `git update-index --assume-unchanged <path>`
-   Find a bug in history:  
    `git bisect <last_good_hash>`
-   Add recursively files by pattern:  
    `git add ./\*.json`
-   Remove untrack files:  
    `git clean -f`
-   Remove whitespace changes:

```bash
git diff -w --no-color
git apply --cached --ignore-whitespace
git checkout -- .
git reset
```

-   Rebase accepting all rebased branch conflicts:  
    `git rebase -X theirs <branch>`
-   Resolves merge conflicts (with `ours` or `theirs`):  
    `git checkout --ours <file>`

## Reset

-   Remove from stage:  
    `git reset HEAD [path]`
-   Remove file from add:  
    `git reset <file>`
-   Reset all modifications:  
    `git reset --hard`
-   Reset a commit and keep file in stage:  
    `git reset <hash> --soft`

## Stash

-   Stash with message:  
    `git stash save <message>`
-   Stash untracked files:  
    `git stash -u`
-   List stash:  
    `git stash list`
-   Clean stash:  
    `git stash clear`
-   Stash specific file:  
    `git stash push -m <name> <path>`
-   Show full diff:  
    `git stash show -p`

## Log

-   Show history if files move:  
    `git log --follow`
-   Git history of directory:  
    `git log -- path/to/folder`
-   Search in diff:  
    `git log -i -Gtext --name-only`
-   Search in commit message:  
    `git log --all --grep='text'`

## Custom local configuration

Create a `.gitconfig` file in the repository root  
Then include manually the config file:  
`git config --local include.path "../.gitconfig"`

## Author Vs Committer

Author => write the code  
Committer => commit the code

> The author is the person who originally wrote the patch, whereas the committer is the person who last applied the patch

## Dots

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

## Filter-repo

-   Analyze repository:  
    `git filter-repo --analyze`  
    Report can be seen at `.git\filter-repo\analysis`  
    Deleted files sort by size are avaible in `path-deleted-sizes.txt`
-   Removes a file from history:  
    `git filter-repo --force --invert-paths --path-glob "path/to/file"`  
    To push, we must do `git remote add origin https://github.com/xxx/zzz.git` and then `git push --force`
-   Remapping committers and authors name and email:  
    `git filter-repo --mailmap mailmap.txt`  
    with mapping file:

```txt
Name For User <email@addre.ss>
<new@ema.il> <old1@ema.il>
New Name And <new@ema.il> <old2@ema.il>
New Name And <new@ema.il> Old Name And <old3@ema.il>
```

-   Replaces content:  
    `git filter-repo --replace-text exp.txt`  
    with `exp.txt` containing:

```txt
p455w0rd
foo==>bar
glob:*666*==>
regex:\r\n \* @author xxx==>
regex:\bdriver\b==>pilot
literal:MM/DD/YYYY==>YYYY-MM-DD
regex:([0-9]{2})/([0-9]{2})/([0-9]{4})==>\3-\1-\2
```

will go through and replace p455w0rd with **_REMOVED_**, foo with bar, any line containing 666 with a blank line, the word driver with pilot (but not if it has letters before or after; e.g. drivers will be unmodified), replace the exact text MM/DD/YYYY with YYYY-MM-DD and replace date strings of the form MM/DD/YYYY with ones of the form YYYY-MM-DD. Every line has a replacement, given by whatever is on the right of ==>. If ==> does not appear on the line, the default replacement is **_REMOVED_**. If multiple matches are found, all are replaced.

## BFG Cleaner

Download the jar here: https://rtyley.github.io/bfg-repo-cleaner/  
Clone the full repo, amke a copy of it:  
`git clone --mirror`  
Put the data to remove in a text file and then:  
`java -jar bfg.jar --replace-text passwords.txt`  
All the commits and branch will have this data removed except the HEAD.  
Pull requests will not be modified  
