---
layout: post
title: "Nerves Blinky"
date: 2016-06-09T20:55:15-04:00
modified:
categories:
excerpt:
tags: []
image:
  feature:
---

# Dependencies

We'll need to grab some dependencies to get started building firmware with Nerves. Every post has to start somewhere, so I'll assume that (like me) you're using Ubuntu 14.04 and you're somewhat familiar with the Linux command line.

Following along with the [Nerves installation page](https://hexdocs.pm/nerves/installation.html), here are the things we'll need:

- [Elixir](http://elixir-lang.org/) - The programming language we'll be using
- [Erlang](http://www.erlang.org/) - The development platform on which Elixir runs
- [Hex](https://hex.pm/) - Erlang's package manager
- [Rebar](https://github.com/erlang/rebar3) - A tol used to create Erlang applications
- [fwup](https://github.com/fhunleth/fwup) - A firmware update utility for embedded Linux systems
- [gstat](http://manpages.ubuntu.com/manpages/wily/man1/gstat.1.html) - Used in Nerves scripts
- [squashfs-tools](http://packages.ubuntu.com/trusty/squashfs-tools) - Used in Nerves scripts

## Install Elixir & Erlang

We'll follow the [Elixir installation instructions](http://elixir-lang.org/install.html) to install Erlang and Elixir.

```bash
$ # Add the Erlang Solutions repository
$ wget https://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb && sudo dpkg -i erlang-solutions_1.0_all.deb
$ sudo apt-get update
$ sudo apt-get install esl-erlang       # Install Erlang
$ sudo apt-get install elixir           # Install Elixir
```

## Install Hex & Rebar
Install Hex by using the `Mix` build tool that comes with Elixir.

```bash
$ mix local.hex                         # Install Hex
$ mix local.rebar                       # Install Rebar
```

## Install fwup
Install fwup by downloading and installing the Debian package listed on the [fwup Github page](https://github.com/fhunleth/fwup#installing).

## Install gstat & squashfs-tools
The Nerves installation guide is a little vague about where to find these tools. A bit of research revealed that these are the correct packages to install on Ubuntu.

```bash
$ sudo apt-get install ganglia-monitor  # Install gstat
$ sudo apt-get install squashfs-tools   # Install squashfs-tools
```

## Install nerves_bootstrap
Last we install the nerves_bootstrap archive using `Mix`

```bash
$ mix archive.install https://github.com/nerves-project/archives/raw/master/nerves_bootstrap.ez
```

# References

Here's some relevant reading material I found useful:

- [Yet Another Introduction to Erlang](http://theerlangelist.blogspot.com/2012/12/yet-another-introduction-to-erlang.html)
