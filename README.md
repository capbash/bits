bit
==============

An opinionated view on installing software.

A collection of stand-alone bash scripts for provisioning a bare metal server.

# How to Install BITS CLI #

To install from scratch, run

```bash
bash <(curl -s https://raw.githubusercontent.com/capbash/bits/master/bits-installer)
```

This will install capbash into /usr/local/bin/bits.  To install it somewhere else, for example:

```bash
bash <(curl -s https://raw.githubusercontent.com/capbash/bits/master/bits-installer) --path /tmp
```

If you don't trust this project, please don't pipe into bash, and instead download the file,
inspect it and run it directly.

If you already have bits and want to upgrade to the altest, please run

```
bits update-self
```

# How to Install a Bit #

Once your bits installed (from above), you can install other bits by running

```bash
bits install <BIT_NAME>
```

For example,

```bash
bits install elixir
```

All available configurations are managed through environment variables.  If you wanted a different
version of elixir, then you would run


```bash
ELIXIR_VERSION=1.1.0 bits install elixir
```


# How to Install A Bit Directly #

If you don't like the idea of installing the "bits" command line tool, then you can install
the bits directly using bash and curl.

For example

```bash
bash <(curl -s https://raw.githubusercontent.com/capbash/bits/master/elixir.bits)
```

To override defaults, set it as an environment variable

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
bits install elixir
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
  bits install gitclone
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
  bits install gitconfig
```

## libsass.bits ##

Installs libsass and sassc (needed by [node-sass](https://github.com/sass/node-sass)
and useful with (Phoenix)[http://www.phoenixframework.org/]).  A thank you to
edouard-lopez for the (fix)[https://gist.github.com/edouard-lopez/503d40a5c1a49cf8ae87].

To install, run

```bash
bits install libsass
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
bits install phoenix
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
  bits install phoenixapp
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
bits install postgres
```

## ruby.bits ##

Installs Ruby.
Available configurations with defaults include

```bash
RUBY_VERSION=2.2.3
```
To install, run

```bash
bits install ruby
```
