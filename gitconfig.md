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
	shp = stash show -p
	shs = stash save
	shd = stash drop 
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
	ckf = ck -f
	ckb = ck -b
	# Cherry
	cp = cherry-pick
	cpc = cp --continue
	# Various
	ap = add -p
	alias = config --get-regexp alias
	st = status -sb
	fc = fetch --all --prune
	lg = log --graph --date=format:'%d/%m/%Y %H:%M:%S' --pretty=tformat:'%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%an %ad)%Creset'
	lgn = lg --oneline -n
	last = lgn 1
	clear = remote prune origin
	dw = diff --ignore-space-at-eol -b -w --ignore-blank-lines
	dc = dw --cached
	contributor = shortlog -sne
	url = remote show origin
	name = show --name-only
	
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
[branch "master"]
  remote = origin
  merge = refs/heads/master

[merge]
  conflictstyle = diff3

[push]
	default = current
[credential]
	helper = manager
```