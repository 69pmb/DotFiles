```bash
[diff "astextplain"]
	textconv = astextplain
[filter "lfs"]
	clean = git-lfs clean -- %f
	smudge = git-lfs smudge -- %f
	process = git-lfs filter-process
	required = true
[http]
	sslBackend = openssl
	sslCAInfo = C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
[core]
	autocrlf = true
	fscache = true
	symlinks = false
	quotePath = false
	untrackedCache = true
	editor = \"C:\\\\Program Files\\\\Notepad++\\\\notepad++.exe\" -multiInst -notabbar -nosession -noPlugin

[user]
	email = xxx
	name = xxx

[alias]
	# Push
	ps = push
	pf = push --force-with-lease
	# Commit
	co = commit -m 
	fix = commit --fixup
	oops = commit --amend --no-edit
	# Stash
	sh = stash
	list = stash list
	pop = stash pop
	shs = stash show -p
	# Rebase
	pl = pull --rebase --autostash
	re = rebase
	rea = rebase --abort
	rec = rebase --continue
	rei = rebase --interactive
	res = rebase --skip
	ras = rebase -i --autosquash
	# Branch
	br = branch -a
	brs = branch --sort=-committerdate
	brv = for-each-ref --sort=-committerdate --format=\"%(color:blue)%(authordate:relative)\t%(color:red)%(authorname)\t%(color:white)%(color:bold)%(refname:short)\" refs/remotes
	# Checkout
	ck = checkout
	ckf = checkout -f
	ckb = checkout -b
	# Cherry
	cp = cherry-pick
	cpc = cherry-pick --continue
	# Various
	aliases = config --get-regexp alias
	st = status -sb
	fc = fetch --all --prune
	lg = log --graph --date=format:'%d/%m/%Y %H:%M:%S' --pretty=tformat:'%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%an %ad)%Creset'
	last = log -n 1 --oneline 
	clear = remote prune origin
	diffw = diff --ignore-space-at-eol -b -w --ignore-blank-lines
	contributor = shortlog --summary --numbered -c -e
	
[pull]
	# This is GREAT… when you know what you're doing and are careful
	# not to pull --no-rebase over a local line containing a true merge.
	rebase = true
	# WARNING! This option, which does away with the one gotcha of
	# auto-rebasing on pulls, is only available from 1.8.5 onwards.
	# rebase = preserve

[status]
	# Display submodule rev change summaries in status
	submoduleSummary = true
	# Recursively traverse untracked directories to display all contents
	showUntrackedFiles = all

[stash]
	showPatch = true

[diff]
	tool = code
	
[rebase]
	autoStash = true
	abbreviateCommands = true

[color]
	ui = auto

[color "branch"]
	# Blue on black is hard to read in git branch -vv: use cyan instead
	# upstream = cyan
	current = yellow reverse
	local = yellow
	remote = green

[color "diff"]
  meta = yellow bold
  frag = magenta bold
  old = red bold
  new = green bold

[color "status"]
  added = yellow
  changed = green
  untracked = cyan
  
# Use `origin` as the default remote on the `master` branch in all cases
[branch "master"]
  remote = origin
  merge = refs/heads/master
  
[push]
	default = current
[credential]
	helper = manager
```