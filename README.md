bit
==============

An opinionated view on installing software.

A collection stand-alone bash scripts for provisionning a bare metal server.

# How to Install A Bit #

To install a bit with all default parameters, e.g. elixir.bits, run

```bash
bash <(curl -s https://raw.githubusercontent.com/capbash/bits/master/elixir.bits)
```

To override defaults, run

```bash
ELIXIR_VERSION=1.1.0 bash <(curl -s https://raw.githubusercontent.com/capbash/bits/master/elixir.bits)
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
bash <(curl -s https://raw.githubusercontent.com/capbash/bits/master/elixir.bits)
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
NAME=samplephp \
  URL=https://github.com/capbash/samplephp \
  TAG=v0.2 \
  bash <(curl -s https://raw.githubusercontent.com/capbash/bits/master/gitclone.bits)
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
EMAIL=yourname@example.com \
  USERNAME=yourname \
  bash <(curl -s https://raw.githubusercontent.com/capbash/bits/master/gitconfig.bits)
```

## phoenix.bits ##

Installs Erlang and Elixir (using elixir.bits), and then
Postgres (using postgres.bits), and then installs Phoenix and Node.  
Available configurations with defaults include

```bash
PHOENIX_VERSION=1.0.3
NODE_VERSION=4.2.2
```
To install, run

```bash
bash <(curl -s https://raw.githubusercontent.com/capbash/bits/master/phoenix.bits)
```

## postgres.bits ##

Installs Postgres.
Available configurations with defaults include

```bash
POSTGRES_VERSION=9.4
PGADMIN_VERSION=3
```
To install, run

```bash
bash <(curl -s https://raw.githubusercontent.com/capbash/bits/master/postgres.bits)
```
