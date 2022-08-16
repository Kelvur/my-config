# Vpn

## Reason

If you work from home maybe you has to configure a VPN to access the intranet of your company

## How To

### Install Openconnect

```bash
sudo apt-get install openconnect
```

### Connect with Openconnect

```bash
sudo openconnect --usergroup=${USER GROUP} --passwd-on-stdin ${VPN URL}
```

### Alias for Openconnect

Make alias of the command, so you don't have to type the command every time you want to connect to the VPN

- Open a console
- If the file `.bash_aliases` don't exists in `$HOME` create it

```bash
touch .bash_aliases
```
- Open `.bash_aliases`

```bash
nano .bash_aliases
```
- Append the following, replacing the vars `${}`:

```bash
alias myvpn='sudo openconnect --usergroup=${USER_GROUP} --passwd-on-stdin ${VPN_URL}'
```
- Save
- The new alias will not appear till the console is restarted