# Git Config

## Reason

You had to add some configuration to git as user and email.
This guide will show how to have multiple git configurations for different folders and subfolders. However, exists a more simple way if you has the same configuration for all the projects, just adding a global configuration.

## How To

### Create the Global Git Configuration

Open a terminal and go to `$HOME`

```bash
# If you just type cd that will take you to your $HOME
cd
```

If the file `.gitconfig` doesn't exist create it

```bash
touch .gitconfig
```

Open the file `.gitconfig`

```bash
nano .gitconfig
```

If you have the same definition for all the posibles configurations add it to the first part of this file, example:

```
[core]
	autocrlf = false

[push]
	default = current
```

For each configuration you want add a block like this:

- This may no have sense to you now, please keep reading this guide.

```
[includeIf "gitdir:~/workspace/${YOURSELF}/"]
	path = ~/workspace/${YOURSELF}/.gitconfig
```

* [Reference](workspace.md)

In the end you will have a `.gitconfig` similar to this:

```
[core]
	autocrlf = false

[push]
	default = current

[includeIf "gitdir:~/workspace/${YOURSELF}/"]
	path = ~/workspace/${YOURSELF}/.gitconfig

[includeIf "gitdir:~/workspace/${COMPANY}/"]
	path = ~/workspace/${COMPANY}/.gitconfig

[includeIf "gitdir:~/workspace/${SOME_ORGANIZATION}/"]
	path = ~/workspace/${SOME_ORGANIZATION}/.gitconfig
```

You only need a `.gitconfig` for each different configuration, if 2 subfolders in `workspace` have the same configuration you can point to the same `.gitconfig`

### Add Git Configuration to a Folder and Subfolders

Open a terminal and go to `~/workspace/${YOURSELF}`

```bash
cd ./workspace/${YOURSELF}
```

Create a file named `.gitconfig`

```bash
touch .gitconfig
```

Open the file and add the configuration you like. Example:

```bash
[user]
	name = Miguel Osorio @Kelvur
	email = example@iana.com
```

### Remember Credentials

Only if you want use HTTPS and don't write your credentials each time
INSECURE!, Your credentials can be stolen from someone if they has access to your computer

```bash
git config credential.helper 'store'
```
