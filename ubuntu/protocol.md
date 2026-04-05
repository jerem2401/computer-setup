1. get personal scripts/settings from github

- install git
- create ssh key
- add ssh agent
- create `~/gitrepo` directory as root dir for git repos
- clone my scripts repo: `git clone git@github.com:jerem2401/scripts.git ~/gitrepo/scripts`

2. bashrc

Check current .bashrc and make sure the following setups are added and conflicting present settings are commented (and put to the end of the .bashrc):

```
# -------------------------------
# Infinite Bash history
# -------------------------------

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# Effectively unlimited history
HISTSIZE=
HISTFILESIZE=

# Remove duplicates
HISTCONTROL=ignoredups:erasedups

# Append to history file, don't overwrite
shopt -s histappend

# Timestamp each command (optional, but useful)
export HISTTIMEFORMAT="%F %T "

# Immediately write each command to history file and read new commands from it
# This ensures multiple terminals stay in sync
PROMPT_COMMAND="history -a; history -n; $PROMPT_COMMAND"

# -------------------------------
# Alias
# -------------------------------

alias cp='cp -i'
alias mv='mv -i'
alias ls='ls -ltr --color=auto'
alias gittree='git log --oneline --decorate --graph --all'
alias gfs='git status && git fetch'
alias code='cursor'

# -------------------------------
# Others
# -------------------------------

#cycling over choices given by complete
bind "TAB:menu-complete"
bind "set show-all-if-ambiguous on"

#disabling highlight when pasting in terminal (default is 'on' now from bash 5.1)
bind 'set enable-bracketed-paste off'
#get older directories that just the previous one with cd-
source ~/gitrepo/scripts/unix/acd_func.sh
```

3. inputrc

- create or edit the ~/.inputrc such that I can up/down arrow history:

```
"\e[A": history-search-backward
"\e[B": history-search-forward
```

4. cursor

- install cursor
- import settings or setup the following:
    - "terminal.integrated.middleClickBehavior": "paste"
    - "terminal.integrated.copyOnSelection": true
    - install vim extension
    - allows "jj" escape in insert mode by adding the following config:
    - install "Gruvbox Theme", and set theme to "light soft"

```
"vim.insertModeKeyBindings": [
    {
        "before": ["j", "j"],
        "after": ["<Esc>"]
    }
],
```

- deactivate git ctrl+K keybinding if sets to avoid conflict with AI generation


5. VIM

- install vim
- symlink my .simple_vimrc prsent in my git repo "scripts" cloned earlier

6. battery setting

- if my gnome version allows it out of the box set my battery start charge at 50% and end charge at 80%
- else use tlp (ideally make small bash script that allows to quickly swing from 50%-80% to 80%-95% so I can edit quicly when travelling from my terminal)

7.