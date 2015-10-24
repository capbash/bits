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

Installs Erlang and Elixir on your system.  Available configurations include

```bash
ERLANG_VERSION=18.0-1
ELIXIR_VERSION=1.1.1
```
To install, run

```bash
curl -s https://raw.githubusercontent.com/capbash/bits/master/elixir.bits | bash
```
