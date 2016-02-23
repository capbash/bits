bits
==============

An opinionated view on installing software.

A collection of stand-alone bash scripts for provisioning a bare metal server.

# How to Install bits CLI #

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

```bash
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

## chromedriver.bits ##

Installs [Chrome Driver](https://sites.google.com/a/chromium.org/chromedriver/) on your system.
Available configurations with defaults include

```bash
CHROMEDRIVER_VERSION=2.21
```
To install, run

```bash
bits install chromedriver
```

## devboxdio.bits ##

Creates a [Digital Ocean](https://www.digitalocean.com/) droplet that is ready for
development.  It will create the specified IMAGE of a specific SIZE.

This bit requires [Dio](https://github.com/capbash/dio) installed locally, with a valid
TOKEN to access the [Digital Ocean API](https://developers.digitalocean.com/documentation/v2/).


```bash
NAME=devbox$TS
IMAGE=ubuntu-14-04-x64
SIZE=512mb
SLEEP=60
LOGFILE=/tmp/devbox_$NAME.log
```

To install, run

```bash
bits install devboxdio
```

## elixir.bits ##

Installs [Elixir](http://elixir-lang.org), which also needs [Erlang](http://www.erlang.org/), on your system.
Available configurations with defaults include

```bash
# From erlang.bits
ERLANG_VERSION=18.2-1

ELIXIR_VERSION=1.2.0
```
To install, run

```bash
bits install elixir
```

## erlang.bits ##

Installs [Erlang](http://www.erlang.org/) on your system.
Available configurations with defaults include

```bash
ERLANG_VERSION=18.2-1
```
To install, run

```bash
bits install erlang
```

## git.bits ##

Install git.

```bash
GIT_VERSION=latest
```
To install, run

```bash
bits install git
```

## gitclone.bits ##

Clone a git project.  Available configurations with defaults include

```bash
NAME=samplephp
URL=https://github.com/capbash/samplephp

INSTALL_DIR=/var/local/apps
USER_EMAIL=server@localhost
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

## gitprompt.bits ##

Configure your bash prompt to show important git branch information.  Once configured your prompt will look similar to:

```bash
11:35 /src/bits (master)$
```

To install, run

```bash
bits install gitprompt
```

## jumpcloud.bits ##

Configure a [JumpCloud](https://jumpcloud.com/) daemon on
your server.

To install, run

```bash
JUMPCLOUD_TOKEN=fill_me_in \
  bits install jumpcloud
```

## knownhosts.bits ##

Configure your server to trust all hosts so that you can, for example,
access services like GitHub and Bitbucket to download code.

To install, run

```bash
bits install knownhosts
```

## letsencrypt.bits

Installs [Let's Encyrpt](https://letsencrypt.org/). To install, run

```bash
bits install letsencrypt
```

## libsass.bits ##

Installs libsass and sassc (needed by [node-sass](https://github.com/sass/node-sass)
and useful with [Phoenix](http://www.phoenixframework.org/)).  A thank you to
edouard-lopez for the [fix](https://gist.github.com/edouard-lopez/503d40a5c1a49cf8ae87).

To install, run

```bash
bits install libsass
```

## nginx.bits

Install [Nginx](http://nginx.org/). Available configurations with defaults include

```
NGINX_VERSION=1.8.0
NGINX_UPDATERC=true
```

If NGINX_UPDATERC is set to true, it will register itself with update-rc to automatically start when booting up the system.

Once installed, you can see the availbale options by running

```
sudo service nginx
```

A huge thank you to [Jason Giedymin](https://github.com/JasonGiedymin/nginx-init-ubuntu) for the init.d script.


## mysql.bits ##

Installs [MySQL](https://www.mysql.com/). Available configurations with defaults include

```bash
MYSQL_VERSION=5.5.47
```

Available versions include

* 5.5.47
* 5.6.28
* 5.7.10

To install, run
```
bits install mysql
```

## pip.bits ##

Installs Pip.
Available configurations with defaults include

```bash
# From python.bits
PYTHON_VERSION=2.7.11
```

To install, run

```bash
bits install pip
```

## python.bits ##

Installs Python.
Available configurations with defaults include

```bash
PYTHON_VERSION=2.7.11
```

To install, run

```bash
bits install python
```

## phoenix.bits ##

Installs [Erlang](http://www.erlang.org/) (using erlang.bits) and [Elixir](http://elixir-lang.org/) (using elixir.bits),
Sass (using sass.bits), Libsass (through sass.bits), Ruby (through sass.bits), Postgres (using postgres.bits),
Node JS (using nodejs.bits) and then installs Phoenix. Available configurations with defaults include

```bash
# From erlang.bits
ERLANG_VERSION=18.2-1

# From elixir.bits
ELIXIR_VERSION=1.2.0

# From gitconfig.bits
EMAIL=you@example.com
USERNAME="Ben Dover"
EDITOR=vi
PUSH=simple

# From postgres.bits
POSTGRES_VERSION=9.4
PGADMIN_VERSION=3

# From ruby.bits (through sass.bits)
RUBY_VERSION=2.2.3

PHOENIX_VERSION=1.0.3
NODE_VERSION=5.3.0
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

Installs [Erlang](http://www.erlang.org/) (using erlang.bits) and [Elixir](http://elixir-lang.org/) (using elixir.bits), and then
Postgres (using postgres.bits), and Node JS (using nodejs.bits) and Phoenix (using phoenix.bits).
Then it will download a phoenix umbrella app where the phoenix web app
should be located at ./apps/webapp.  If you want to configure your app
differently, then just spin up a phoenix.bit and configure as you wish.

Available configurations with defaults include

```bash
# From erlang.bits
ERLANG_VERSION=18.2-1

# From elixir.bits
ELIXIR_VERSION=1.2.0

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
NODE_VERSION=5.3.0

SRC_DIR=/src
GIT_URL="git@bitbucket.org:capbash/samplephoenix.git"
GIT_BRANCH="master"
PROJECT_NAME="samplephoenix"
```

To install, run

```bash
GIT_URL=git@github.com:capbash/samplephoenix.git \
  PROJECT_NAME=samplephoenix \
  bits install phoenixapp
```

## phoenixdio.bits ##

Creates a [Digital Ocean](https://www.digitalocean.com/) private image with everything to quickly
spin up a phoenix ready development environment.  It does not expose all available configurations
(e.g. which version of ERLANG, or NODE_JS), so if you need something more customizable, then please
consider wrapping this functionality directly.

This bit requires [Dio](https://github.com/capbash/dio) installed locally, with a valid
TOKEN to access the [Digital Ocean API](https://developers.digitalocean.com/documentation/v2/).


```bash
ELIXIR_VERSION=1.2.2
PHOENIX_VERSION=1.1.3
NAME=elixir${ELIXIR_VERSION//./}phoenix${PHOENIX_VERSION//./}
LOGFILE=/tmp/$NAME.log
SIZE=512mb
SLEEP=60
```
To install, run

```bash
bits install phoenixdio
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

## redis.bits ##

Installs [Redis](http://redis.io/).
Available configurations with defaults include

```bash
REDIS_VERSION=stable
```
To install, run

```bash
bits install redis
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

## sass.bits ##

Installs SASS.
Available configurations with defaults include

```bash
RUBY_VERSION=2.2.3
```
To install, run

```bash
# From ruby.bits
RUBY_VERSION=2.2.3

bits install sass
```
