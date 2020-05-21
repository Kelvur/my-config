# Configurate NPM

## Reason

Maybe you need point to a registry, configurate a proxy, add a certificate authority, ...

## How To

### Configure Npm

Open a console

Create the file `.npmrc` in `$HOME`

```bash
touch .npmrc
```

Open the file and add the configuration necessary for you. Example:

```bash
nano .npmrc
```

```
# Proxy
proxy=http://proxy.company.domain/index.pac
https-proxy=http://proxy.company.domain/index.pac
# Certificate Authority
cafile=/certs/company.pem
# Registry
registry=https://nexus.company.domain/repository/npm-group/
```