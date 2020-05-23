# Install Go

## Reason

If you want to program in Go

## How To

### Install Go

Open a browser and go to [link](https://golang.org/dl/)

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

The following steps are necesary if when you execute `go get` get an error.

Execute the following in `$HOME`:

```bash
# Create a bin file where GO will install dependencies
mkdir bin
```

There is a file named `.profile` in your `$HOME`; Append the following to that file:

```bash
# Add the binaries of GO to $PATH
export PATH=$PATH:/usr/local/go/bin
# Establish the GOPATH as HOME, so all the projects under
# HOME can use the GO utilities
export GOPATH=$HOME
# Establish GOBIN
export GOBIN=$GOPATH/bin
# Also add GOBIN to PATH 
export PATH=$PATH:$GOBIN
```
