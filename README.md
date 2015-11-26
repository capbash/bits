bit
==============

An opinionated view on installing software.

A collection stand-alone bash scripts for provisionning a bare metal server.

# How to Install A Bit #

To install a bit with all default parameters, e.g. elixir.bits, run

```bash
curl -s https://raw.githubusercontent.com/capbash/bits/master/elixir.bits | bash
```

To override defaults, run

```bash
curl -s https://raw.githubusercontent.com/capbash/bits/master/elixir.bits | \
  ELIXIR_VERSION=1.1.0 bash
```

If you don't trust this project, please don't pipe into bash, and instead download the file,
inspect it and run it directly.

# Available Bits #

## elixir.bits ##

Installs Erlang and Elixir on your system.  Available configurations with defaults include

```bash
ERLANG_VERSION=18.0-1
ELIXIR_VERSION=1.1.1
```
To install, run

```bash
curl -s https://raw.githubusercontent.com/capbash/bits/master/elixir.bits | bash
```

## phoenix.bits ##

Installs Erlang, Elixir, Node and Phoenix on your system.  Available configurations with defaults include

```bash
ERLANG_VERSION=18.0-1
ELIXIR_VERSION=1.1.1
PHOENIX_VERSION=1.0.3
NODE_VERSION=4.2.2
```
To install, run

```bash
curl -s https://raw.githubusercontent.com/capbash/bits/master/phoenix.bits | bash
```

## gitconfig.bits ##

Configure a remote git to the desired settings.  Available configurations with defaults include

```bash
EMAIL=you@example.com
USERNAME="Ben Dover"
EDITOR=vi
PUSH=simple
```
To install, run

```bash
curl -s https://raw.githubusercontent.com/capbash/bits/master/gitconfig.bits | \
  EMAIL=yourname@example.com USERNAME=yourname bash
```

## gitclone.bits ##

Clone a git project.  Available configurations with defaults include

```bash
NAME=samplephp
URL=https://github.com/capbash/samplephp

INSTALL_DIR=/var/local/apps
USER_EMAIL=server@localhost}
USER_NAME=server
GIT_REMOTE=origin
BRANCH=master
TAG=master
```
To install, run

```bash
curl -s https://raw.githubusercontent.com/capbash/bits/master/gitclone.bits | \
  NAME=samplephp URL=https://github.com/capbash/samplephp TAG=v0.2 bash
```
