# Linux Setup for Front-End Development

Before start this guide check for updates
```bash
sudo apt-get update
sudo apt-get dist-upgrade
```

## Content
1. [Git](#git)
    * [Install git](#install-git)
    * [Configure git](#configure-git)
    * [Configure Git Repository](#configure-git-repository)
    * [Show current branch in the terminal](#show-current-branch-in-the-terminal)
1. [Google Chrome](#google-chrome)
    * [Install Google Chrome](#install-google-chrome)
    * [Log In Google Chrome](#log-in-google-chrome)
1. [VS Code](#vs-code)
    * [Install VS Code](#install-vs-code)
    * [Configure VS Code](#configure-vs-code)
    * [Install VS Code Extensions](#install-vs-code-extensions)
1. [Nvm](#nvm)
    * [Install Nvm](#install-nvm)
    * [Install Node and Npm with Nvm](#install-node-and-npm-with-nvm)
    * [Change default node with NVM](#change-default-node-with-nvm)
1. [Npm](#npm)
    * [Configure Npm](#configure-npm)
1. [Go](#go)
    * [Install Go](#install-go)
1. [Vpn](#vpn)
    * [Install Openconnect](#install-openconnect)
    * [Connect with Openconnect](#connect-with-openconnect)
    * [Alias for Openconnect](#alias-for-openconnect)
1. [Proxy](#proxy)
    * [Setup Proxy](#setup-proxy)
    * [APT Proxy](#apt-proxy)
1. [Git Repository](#git-repository)
    * [Create private/public keys for the git repository](#create-private/public-keys-for-the-git-repository)
1. [Office Suite](#office-suite)
    * [Install Office Suite](#install-office-suite)
1. [Miscelaneous](#miscelaneous)
    * [Create *Workspace* folder](#create-workspace-folder)
    * [Show hidden files](#show-hidden-files)
    * [Sort by type of file](#sort-by-type-of-file)
    * [Allow large number of watchers](#allow-large-number-of-watchers)


## Git
### Install git
```bash
sudo apt-get install git
```

### Configure git
```bash
git config --global user.name "${USER}"
git config --global user.email "${EMAIL}"
git config --global core.autocrlf false
git config --global push.default current
```

### Configure Git Repository
```bash
# Only if you want use SSH login but not a SSH Key and also don't write your credentials each time
# INSECURE!, Your credentials can be stolen from someone if they has access to your computer
git config credential.helper = 'store'
```

### Show current branch in the terminal

Copy in the file `.bashrc` the next function, copy it before the line `if [ -n "$force_color_prompt" ]; then`

```bash
# add git branch if its present to PS1
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
```

Replace the asignament of `PS1` by:
```bash
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\] \[\033[01;31m\]$(parse_git_branch)\[\033[00m\]\$ '
```

## Google Chrome
### Install Google Chrome

Go to [link](https://www.google.com/intl/es/chrome/)
```
https://www.google.com/intl/es/chrome/
```

### Log In Google Chrome

Only if you want synchronize your bookmarks and extensions with other computers

## VS Code
### Install VS Code

Go to [link](https://code.visualstudio.com/)
```
https://code.visualstudio.com/
```

### Configure VS Code

Go to `File -> Preferences -> Settings -> {}` and replace it with:
```json
{
    "diffEditor.ignoreTrimWhitespace": true,
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
    "editor.fontLigatures": true,
    "extensions.ignoreRecommendations": true,
    "jenkins.pipeline.linter.connector.pass": "${PASS}",
    "jenkins.pipeline.linter.connector.strictssl": false,
    "jenkins.pipeline.linter.connector.url": "https://jenkins.corp/pipeline-model-converter/validate",
    "jenkins.pipeline.linter.connector.user": "${USER}",
    "workbench.colorTheme": "Monokai",
    "workbench.startupEditor": "newUntitledFile"
}
```

Go to `File -> Preferences -> Keyboard Shortcuts -> {}` and replace it with:
```json
// Place your key bindings in this file to override the defaultsauto[]
[
    {
        "key": "ctrl+[Backslash]",
        "command": "editor.action.commentLine",
        "when": "editorTextFocus && !editorReadonly"
    },
    {
        "key": "ctrl+shift+7",
        "command": "-editor.action.commentLine",
        "when": "editorTextFocus && !editorReadonly"
    },
    {
        "key": "ctrl+d",
        "command": "editor.action.copyLinesUpAction",
        "when": "editorTextFocus && !editorReadonly"
    },
    {
        "key": "ctrl+shift+alt+up",
        "command": "-editor.action.copyLinesUpAction",
        "when": "editorTextFocus && !editorReadonly"
    }
]
```

### Install VS Code Extensions

- Color Highlight
- EditorConfig for VS Code
- ESLint
- Go
- Highlight Matching Tag
- Jenkins Pipeline Linter Connector
- SVG Viewer


## Nvm
### Install Nvm

- Go to [link](https://github.com/nvm-sh/nvm)
```
https://github.com/nvm-sh/nvm
```
- In the step of installation copy the `wget` command, Example:
```bash
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
```
- Paste it in the console
- Restart the console

### Install Node and Npm with Nvm

```bash
nvm install ${NODE VERSION}
```

### Change default node with NVM

```bash
nvm alias current ${NODE_VERSION}
```

## Npm
### Configure Npm

- Open the console, `Ctrl + Alt + t`
- Create the file `.npmrc` in `HOME`
```bash
touch .npmrc
```
- Add the configurations necessary for you, Example:
```bash
nano .npmrc
```
```bash
# Proxy
proxy=http://proxy.company.domain/index.pac
https-proxy=http://proxy.company.domain/index.pac
# Certificate Authority
cafile=/certs/company.pem
# Registry
registry=https://nexus.company.domain/repository/npm-group/
```

## Go
### Install Go

Go to [link](https://golang.org/dl/)
```
https://golang.org/dl/
```

Download the linux `tar.gz`, Example:
```
https://dl.google.com/go/go1.14.2.linux-amd64.tar.gz
```

Execute the following:
```bash
sudo tar -C /usr/local -xzf go$VERSION.$OS-$ARCH.tar.gz
# Example sudo tar -C /usr/local -xzf go1.14.2.linux-amd64.tar.gz
```

The following steps are necesary if when you execute `go get` get a error.

Execute the following in `$HOME`:
```bash
# Create a bin file where GO will install what you need
mkdir bin
```

There it's a file named `.profile` in your `$HOME`; Append the following to that file:
```bash
# Add the binaries of GO to $PATH
export PATH=$PATH:/usr/local/go/bin
# Stablish the GOPATH as HOME, so all the projects under
# HOME can use the GO utilities
export GOPATH=$HOME
# Stablish GOBIN
export GOBIN=$GOPATH/bin
# Also add GOBIN to PATH 
export PATH=$PATH:$GOBIN
```

## Vpn
### Install Openconnect
```bash
sudo apt-get install openconnect
```

### Connect with Openconnect
```bash
sudo openconnect --usergroup=${USER GROUP} --passwd-on-stdin ${VPN URL}
```
### Alias for Openconnect
Make alias of the command, so you don't have to type every time you want to connect to the vpn

- Open the console, `Ctrl + Alt + t`
- If the file `.bash_aliases` don't exists, create it
```bash
touch .bash_aliases
```
- Open `.bash_aliases`
```bash
nano .bash_aliases
```
- Paste the following:
```bash
alias myvpn='sudo openconnect --usergroup=${USER GROUP} --passwd-on-stdin ${VPN URL}'
```
- Save
- The new alias will not appear till the console is restarted

## Proxy
### Setup Proxy
- Go to: `Settings -> Network -> Network Proxy`
- Choose `Automatic` and type the proxy URL

### APT Proxy

This step is not necessary if you don't work behind a proxy

Apt don't use the OS proxy, you have to configurate it again

- Go to `/ect/apt/apt.config.d/`
```bash
cd /ect/apt/apt.config.d/
```

- Open the file `proxy.conf`
```bash
sudo nano proxy.conf
```

- Write the following:
```bash
Acquire {
  HTTP::proxy "http://server.com:port";
  HTTPS::proxy "http://server.com:port";
}
```


## Git Repository
### Create private/public keys for the git repository

```bash
ssh-keygen -t ${PROTOCOL} -b ${BITS} -C "${EMAIL}"
```

Copy the file `${KEY_FILE}.pub` in your settings account -> SSH Keys, or something similar

## Office Suite
### Install Office Suite
```bash
sudo apt install libreoffice
```

## Miscelaneous
### Create *workspace* folder

- Generelly created in `HOME`
```bash
mkdir workspace
```
- Is good to keep this folder sorted, one option is to create subfolders with categories, as:
```bash
/workspace
  /${MYSELF}
  /company
  /test
```

### Show hidden files

- Make the file explorer show you the hidden files

### Sort by type of file

- Make the file explorer show the folders sorted by type of file

### Allow large number of watchers

- To see how many watchers per user are:
```bash
cat /proc/sys/fs/inotify/max_user_watches
```
- To set how many watchers per user:
```bash
sudo nano /etc/sysctl.conf
# go to the line: fs.inotify.max_user_watches or go to the botton and type the number of watchers
fs.inotify.max_user_watches=524288
# save and load the value to make it effective
sudo sysctl -p
```
