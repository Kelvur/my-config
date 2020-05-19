# Git SSH Keys

## Reason

It's handy delegate the authentication to SSH, so you don't have to type your user and passwork in each push.
This guide shows how to have multiple keys for direfent git servers

## How To

### Create a SSH config file

Open a terminal and go to the folder `.ssh` in your `$HOME`

```bash
cd
cd .ssh/
```

If the file `config` doesn't exist create it

```bash
touch config
```

For each Git Server add a block like this:

```bash
Host ${NAME} ${URL}
    HostName ${URL}
    IdentityFile ~/.ssh/${PRIVATE_KEY}
    User ${USERNAME}
```

Example:

```bash
Host github github.com
    HostName github.com
    IdentityFile ~/.ssh/id_rsa_kelvur
    User Kelvur
```

### Create a pair of keys

Execute:

```bash
ssh-keygen -t rsa -b 8192 -C "${DESCRIPTION}"
```

### Copy the public key in your Git Server

Copy the file `${PUBLIC_KEY}.pub` in your settings account -> SSH Keys, or something similar
