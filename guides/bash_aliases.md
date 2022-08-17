# Bash Aliases

## Reason

Creating your own bash alias help you to realize task faster and easier

In *Ubuntu* (I suppose in other distros too) there is a file in your `$HOME` called `.bashrc`, this file contains a piece of code as the following:

```bash
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

This means, if the file `.bash_aliases` exists, execute what is inside. The purpose of this file is to contain the user bash aliases.

## How To

### Create `.bash_aliases` file

Open a terminal and execute this:

```bash
touch ~/.bash_aliases
```

### Create an alias

Open a terminal and execute:

```bash
nano ~/.bash_aliases
```

Write there your alias, example:

```bash
alias st='npm start'
```

### Useful aliases

This is a list of useful aliases which I use:

```bash
# This alias allows to use sudo with other alias
alias sudo='sudo '

# This alias open the current folder in the GUI, It works in Ubuntu, I don't know if the same
# alias works in other distros
alias open='xdg-open .'
```