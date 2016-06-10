---
layout: post
title: "Nerves"
date: 2016-06-07T21:42:54-04:00
modified:
categories:
excerpt: Let's take a look at Nerves
tags: [nerves, elixir, ubuntu]
comments: true
image:
  feature:
---

[Nerves](http://nerves-project.org/) is a way to build embedded Linux systems using the [Elixir](http://elixir-lang.org/) programming language. I've decided to try it out and I'll be chronicling my experience with it here. I'm not sure where we're going or how

# Why Nerves?

I'm excited about Nerves because it combines a lot of things I'm interested in: Embedded Linux, Elixir, and [Erlang](http://www.erlang.org/)!

## Embedded Linux

I got a Raspberry Pi for Christmas and it's been gathering dust since then. I've worked on a variety of embedded systems, but never touched embedded Linux. Embedded Linux is cool because it's a happy medium between a bare-metal embedded software and a full blown desktop PC. You get a taste of both worlds!

## Elixir

Elixir is a [functional](https://en.wikipedia.org/wiki/Functional_programming) programming language, a far cry from the [imperative](https://en.wikipedia.org/wiki/Imperative_programming) approach of traditional C. While the handful of functional programming languages are far from mainstream, a variety of functional concepts are leaking into more traditional programming languages (like C++ and JavaScript) and leaving their mark on the ever-evolving doctrine how to create quality software. I have to try out some functional programming.

## Erlang

Elixir inherits a lot of concepts from Erlang and runs atop on the same virtual machine (BEAM). Erlang is known for its ability to produce highly concurrent, robust systems. These concepts are of growing importance to the embedded systems world and the software world at large. Erlang accomplishes this by handling concurrency itself instead of delegating those duties to an operating system. Distributed, fault tolerant systems are realized through Erlang's model for independent processes with isolated memory, asynchronous message passing, and error containment. If it sounds confusing, that's probably because I don't understand it.

# What are we going to build with Nerves?

I haven't figured that out yet. If you have any ideas, let me know!
