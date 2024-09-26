---
title: Bash aliases
---  
```bash
alias cp='cp -i'
alias df='df -h'
alias du='du -h'
alias ll='ls -lahp'
alias ls='ls -p'
alias mv='mv -i'
alias rm='rm -i'
alias tailf='tail -f'
alias temp='vcgencmd measure_temp'
alias halt='sudo shutdown -h now'
alias dc='docker'
alias gti='git'
alias got='git'
alias gut='git'
alias gt='git'
alias curl='curl -s'
alias pm='pnpm'
alias up='pwd | grep -o "[^/]*$" |  xargs -I % npm update --prefix projects/%'
alias erase='pwd | grep -o "[^/]*$" |  xargs -I % git erase projects/%/package-lock.json'
```
