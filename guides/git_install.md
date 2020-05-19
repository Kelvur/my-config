# Git Install

## Reason

Git is a software for the control of versions, usually used in code can also be used in documents, images and other media types.
Git has become so popular which it's considered the default software for version control

## How To

### Install

```bash
sudo apt-get install git
```

### Show the current branch in the terminal

Open a terminal, and go to `$HOME`

```bash
# If you just type cd that will take you to your $HOME
cd
```

Open the file `.bashrc`

```bash
nano .bashrc
```

Search for the line `if [ -n "$force_color_prompt" ]; then` and copy this before:

```bash
# add git branch if its present to PS1
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
```

Search for the line `if [ "$color_prompt" = yes ]; then` and in the next line you will see a `PS1='${debian_chroot...`; replace that assignment for this:

```bash
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\] \[\033[01;31m\]$(parse_git_branch)\[\033[00m\]\$ '
```

Restart the console
