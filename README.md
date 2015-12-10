bit
==============

An opinionated view on installing software.

A collection of stand-alone bash scripts for provisioning a bare metal server.

# How to Install BITS CLI #

To install from scratch, run

```bash
curl -s https://raw.githubusercontent.com/capbash/bits/master/bits-installer | bash
```

This will install capbash into /usr/local/bin/bits.  To install it somewhere else, for example:

```bash
curl -s https://raw.githubusercontent.com/capbash/bits/master/bits-installer | bash -s -- --path ~/.bin
```

If you don't trust this project, please don't pipe into bash, and instead download the file,
inspect it and run it directly.

If you already have bits and want to upgrade to the altest, please run

```
bits update-self
```


# How to Install A Bit Directly #

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

Installs (Erlang)[http://www.erlang.org/] and (Elixir)[http://elixir-lang.org/] on your system.
Available configurations with defaults include

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

## libsass.bits ##

Installs libsass and sassc (needed by [node-sass](https://github.com/sass/node-sass)
and useful with (Phoenix)[http://www.phoenixframework.org/]).  A thank you to
edouard-lopez for the (fix)[https://gist.github.com/edouard-lopez/503d40a5c1a49cf8ae87].

To install, run

```bash
bash <(curl -s https://raw.githubusercontent.com/capbash/bits/master/libsass.bits)
```

## phoenix.bits ##

Installs (Erlang)[http://www.erlang.org/] and (Elixir)[http://elixir-lang.org/] (using elixir.bits),
and then Libsass (using libsass.bits)
Postgres (using postgres.bits), and then installs Phoenix and Node.
Available configurations with defaults include

```bash
# From elixir.bits
ERLANG_VERSION=18.0-1
ELIXIR_VERSION=1.1.1

# From gitconfig.bits
EMAIL=you@example.com
USERNAME="Ben Dover"
EDITOR=vi
PUSH=simple

# From postgres.bits
POSTGRES_VERSION=9.4
PGADMIN_VERSION=3

PHOENIX_VERSION=1.0.3
NODE_VERSION=4.2.2
```
To install, run

```bash
bash <(curl -s https://raw.githubusercontent.com/capbash/bits/master/phoenix.bits)
```

## phoenixapp.bits ##

You must ensure that your remote machine has the proper access to the
git server.  This could be done, by scp'ing a trusted public/private key
that is authorized by your git server.

For example,
```bash
scp $HOME/.ssh/id_rsa.pub <remote_server>:/root/.ssh/
scp $HOME/.ssh/id_rsa <remote_server>:/root/.ssh/
```

Installs (Erlang)[http://www.erlang.org/] and (Elixir)[http://elixir-lang.org/] (using elixir.bits), and then
Postgres (using postgres.bits), and Phoenix and Node (using phoenix.bits).
Then it will download a phoenix umbrella app where the phoenix web app
should be located at ./apps/webapp.  If you want to configure your app
differently, then just spin up a phoenix.bit and configure as you wish.

Available configurations with defaults include

```bash
# From elixir.bits
ERLANG_VERSION=18.0-1
ELIXIR_VERSION=1.1.1

# From gitconfig.bits
EMAIL=you@example.com
USERNAME="Ben Dover"
EDITOR=vi
PUSH=simple

# From postgres.bits
POSTGRES_VERSION=9.4
PGADMIN_VERSION=3

# From phoenix.bits
PHOENIX_VERSION=1.0.3
NODE_VERSION=4.2.2

SRC_DIR=/src
GIT_URL="git@bitbucket.org:capbash/samplephoenix.git"
PROJECT_NAME="samplephoenix"
```

To install, run

```bash
GIT_URL=git@github.com:capbash/samplephoenix.git \
  PROJECT_NAME=samplephoenix \
  bash <(curl -s https://raw.githubusercontent.com/capbash/bits/master/phoenixapp.bits)
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
