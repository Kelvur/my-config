# APT Proxy

## Reason

APT doesn't use the proxy configurated in the SO, so it's probably you need to add some configuration if you work in a intranet

## How To

Go to `/ect/apt/apt.config.d/`

```bash
cd /ect/apt/apt.config.d/
```

If the file `proxy.conf` doesn't exists, create it

```bash
sudo touch proxy.conf
```

Open the file `proxy.conf`

```bash
sudo nano proxy.conf
```

Append the following:

```bash
Acquire {
  HTTP::proxy "http://${PROXY_SERVER}:${PROXY_PORT}";
  HTTPS::proxy "http://${PROXY_SERVER}:${PROXY_PORT}";
}
```