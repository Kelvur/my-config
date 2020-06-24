# Install Docker

## Reason

Docker is util for create containers where you run programs you don't trust, software you don't want to install in your machine, servers and many other things

## How To

### Update

The first step is update your software

```bash
sudo apt update
sudo apt dist-upgrade
```

### Install dependencies

```bash
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```

### Add Docker GPG Key

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

### Verify Docker GPG Key

```bash
sudo apt-key fingerprint 0EBFCD88
```

You should be looking to somenthing like this:

```bash
pub   rsa4096 2017-02-22 [SCEA]
      9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
sub   rsa4096 2017-02-22 [S]
```

### Set Up the Repository

```bash
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

### Install Docker Engine

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

### Add your user to the docker group

If you want to use docker and don't relay in `sudo` one way to do it is add your user to the docker group

```bash
sudo usermod -aG docker $USER
```


### Verify that Docker Engine is installed

```bash
sudo docker run hello-world
```
