---
title: Git config
---

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
	sslVerify = false
[core]
	autocrlf = input
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
	#cbr = "!f() { git rev-parse --abbrev-ref HEAD | sed 's/\//(/g' | sed 's/-/): /2' | sed 's/-/ /g' | sed 's/ /-/1' | xargs -I % git co % ;}; f"
	co = commit -m
	coa = "!f() { git add . && git co $1 ;}; f"
	ca = commit --amend
	fix = commit --fixup
	reco = commit -c ORIG_HEAD
	oops = ca --no-edit
	gloops = "!f() { git add . && git oops && git pf;}; f"
	glops = "!f() { git add $@ && git oops && git pf;}; f"
	fixme = "!f() { git add . && git fix $1 && git ras $1~;}; f"

	# Stash
	sh = stash
	list = stash list --date=format:'%d/%m/%Y %H:%M:%S' --pretty=tformat:'%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%ad)%Creset'
	shl = list
	pop = sh pop
	shp = sh show -p
	shs = sh save
	shpo = "!sh -c 'git pop stash@{$1}' -"
	drop = sh drop
	shd = sh drop
	shc = sh clear

	# Rebase
	pl = pull --rebase --autostash
	re = rebase
	rea = re --abort
	rec = -c core.editor=true re --continue
	rei = re --interactive
	res = re --skip
	ras = rei --autosquash
	fck = "!f() { git fc && git ck $1 && git pl;}; f"
	main = "!f() { git default | xargs -I % git fck % ;}; f"
	red = "!f() { git main && git ck - && git up && git default | xargs -I % git re $1 ;}; f"

	# Reflog
	rl = reflog --date=relative
	rln = rl -n

	# Branch
	br = branch -a --format=\"%(color:green)%(refname:short)\t%(color:blue)%(authordate:relative)\t%(color:red)%(authorname)\t%(color:white)%(objectname:short)\t%(color:yellow)%(contents:subject)\" --sort=-committerdate
	brr = branch -r --format=\"%(color:green)%(refname:short)\t%(color:blue)%(authordate:relative)\t%(color:red)%(authorname)\t%(color:white)%(objectname:short)\t%(color:yellow)%(contents:subject)\" --sort=-committerdate
	brv = for-each-ref --sort=-committerdate --format=\"%(color:blue)%(authordate:relative)\t%(color:red)%(authorname)\t%(color:white)%(color:bold)%(refname:short)\" refs/remotes
	brd = branch -D
	brm = branch -m
	curr = branch --show-current
	up = "!f() { git rev-parse --abbrev-ref HEAD | xargs -I % git branch --set-upstream-to=origin/% && git pl ;}; f"
	bclean = "!f() { main=$(git default); git branch --merged ${1-$main} | grep -v " ${1-$main}$" | xargs -r git branch -d; }; f"
	default = "!f() { git branch -rl '*/HEAD' | awk -F/ '{print $NF}'; }; f"

	# Checkout
	ck = checkout
	ckf = ck -f
	ckb = ck -b
	ckp = ck -p

	# Cherry
	cp = cherry-pick
	cpc = cp --continue
	cpa = cp --abort
	cps = cp --skip

	# Show
	sw = show  --ignore-space-at-eol -b -w --ignore-blank-lines
	name = show --name-only
	names = name
	nw = sw --name-only

	# Remote
	url = remote show origin
	clear = remote prune origin
	set-url = remote set-url origin

	# Various
	ap = add -p
	erase = "!f() { git add $@ && git reset $@ && git ck $@ ;}; f"
	alias = "!f() { git config --get-regexp alias | cut -c 7- | sort; }; f"
	st = status -sb
	fc = fetch --all --prune --tags
	lg = log --graph --date=format:'%d/%m/%Y %H:%M:%S' --pretty=tformat:'%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%an - %ad)%Creset'
	lgn = lg -n
	last = lgn 1
	lt = last
	tags = tag
	rp = reset -p
	undo=reset --soft HEAD^
	dw = diff --ignore-space-at-eol -b -w --ignore-blank-lines
	dc = dw --cached
	contributor = shortlog -sne -c
	adds = "!f() { find . -name "$1" -not -path '*node_modules*' | xargs git add ;}; f"

[pull]
	rebase = true

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
	branch = auto
	diff = auto
	status = auto
	ui = true

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
[branch "main"]
  remote = origin
  merge = refs/heads/main

[merge]
  conflictstyle = diff3

[push]
	default = current
[credential]
	helper = manager
```
