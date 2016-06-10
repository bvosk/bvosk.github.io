---
layout: post
title: "Getting Started With Nerves"
date: 2016-06-07T21:42:54-04:00
modified:
categories:
excerpt:
tags: [nerves, elixir, ubuntu]
comments: true
image:
  feature:
---

# What is Nerves?

[Nerves](http://nerves-project.org/) is a way to build embedded Linux systems using the [Elixir](http://elixir-lang.org/) programming language. I'm new to just about all of this, so here's a post to chronicle my experience.

# Why Nerves?

I'm excited about Nerves because it combines a lot of things I'm interested in: Embedded Linux, Elixir, and Erlang!

## Embedded Linux

I got a Raspberry Pi for Christmas and it's been gathering dust since then. I've worked on a variety of embedded systems, but never touched embedded Linux. Embedded Linux is cool because it's a happy medium between a bare-metal embedded software and a full blown desktop PC. You get a little bit of both worlds!

## Elixir

Elixir is a [functional](https://en.wikipedia.org/wiki/Functional_programming) programming language, a far cry from the [imperative](https://en.wikipedia.org/wiki/Imperative_programming) approach of traditional C. While the handful of functional programming languages are far from mainstream, a variety of functional concepts are leaking into more traditional programming languages (like C++ and JavaScript) and leaving their mark on the ever-changing doctrine what makes good software. I've been observing from afar for too long, it's time to get my hands dirty.

# Erlang

Elixir runs on top of BEAM, the Erlang VM. Erlang is known for it's ability to produce highly concurrent, robust systems. These concepts are of growing importance to the embedded systems world, and certainly the software world at large. Erlang accomplishes this by handling concurrency itself instead delegating that duty to an operating system. It enables the construction of distributed, fault tolerant systems by providing a model for independent processes with isolated memory, asynchronous message passing, and error containment.

# Installation

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
