---
layout: post
title: "From C to Elixir"
date: 2016-07-23
excerpt: Observations about Elixir through the lens of a C programmer
tags: [elixir]
comments: true
---

Since my last post I've been playing around with [Elixir](http://elixir-lang.org/). If you're interested in learning about it, I recommend starting with the [official getting started guide](http://elixir-lang.org/getting-started/introduction.html).

Before we dive into some things I found interesting about Elixir, let's
discuss the most notable differences between Elixir and C:

1. Elixir is new

    Elixir 1.0 was released in 2014. C was doing some heavy lifting as early as
1972[^1].
As one would expect, the decades following the birth of C have afforded Elixir 
with the new ideas, successes, and failures of countless programming languages.
While this is important to keep in mind, it's difficult to isolate this
difference from the rest. I mention this mainly to give a tip of the hat to C
before I say some not-so-nice things about it.

    [^1]: There's a little more to this. [According to Wikipedia](https://en.wikipedia.org/wiki/C_(programming_language)#History), C was being used to develop Unix in 1972 and the famous K&R book was published in 1978. It wasn't until 1989 that C was formally standardized as ANSI C, but it would be disingenuous to suggest that its use wasn't already widespread at that time.

2. Elixir is functional

    Functional programming makes the developer think differently about how to
accomplish the task at hand. I want to focus on this because I think it's the
most interesting divergence from C, which takes an imperative approach.

3. Elixir is dynamically typed

    Dynamically typed languages are probably familiar to most at this point,
popularized by the rise of scripting languages like Python, JavaScript, and
Ruby. A C programmer will find this liberating, but at times dangerously
so. Not unlike a college freshman who finds herself free at last from the supervision
of her parents. At some point she realizes - perhaps while keeled over a garbage 
can - that they're usually right.

## Immutable Data

All data is immutable in Elixir. In other words, a variable's value cannot
change once it is assigned. Check it out:

```elixir
iex> name = "brian"
"brian"
iex> String.upcase(name)
"BRIAN"
iex> name
"brian"
```

This is puzzling if you're used to C. Didn't we make `name` uppercase? No, we
didn't. We performed a transformation on `name` which resulted in a new string.
The new string is a clone of `name`, except uppercase. It's a subtle, but
important difference.

When all the data is immutable, you never have to worry if a function will 
manipulate a variable you pass to it. This has the neat effect of making the 
code easier to conceptualize.

To demonstrate this point, take a look at this C code:

```c
char name[] = "brian";
some_function(name);
printf("Hello, %s!", name);
```

What's the value of `name` after we call `some_function` on it? The only correct answer here is, "Who knows?" The developer is forced to go lookup the details of `some_function` to find out if it manipulates `name`.

## Data Transformations

Functional programming offers a different perspective about what a program
ought to do. Let's take a look at take a look at three programming paradigms and
try to boil their philosophies down to a single sentence:

- **Imperative**: _Programs execute commands_
- **Object-Oriented**: _Programs manipulate objects_
- **Functional**: _Programs transform data_

So Elixir - taking a functional approach - touts data transformation, but all
data is immutable. After the first example, you may be thinking that creating copies of data can
get syntactically cumbersome. I'd agree. One can imagine countless lines of code that look like this:

```
function3(function2(function3(data)))
```
 
And indeed this is valid Elixir:

```elixir
iex> numbers = "one two three"
"one two three"
iex> Enum.join(String.split(numbers), "+")
"one+two+three"
```

But there's a better way. To support the precepts of functional programming while maintaining readability, Elixir provides special syntax to perform data transformations. Here's the same code using Elixir's pipe operator, `|>`:

```elixir
iex> numbers = "one two three"
"one two three"
iex> numbers |> String.split |> Enum.join("+")
"one+two+three"
```

That's better! The pipe operator simply passes the return value of the
left function as the first argument to right function. In this way, functions
can be chained together endlessly and read naturally from left to right in the
order that they're applied.

## Other Differences

There are plenty of other differences that I won't get into. Elixir is
garbage-collected, places a heavy emphasis on lists and recursion, and runs atop 
a virtual machine. These are significant, but the focus on data transformation
rather than procedural execution is the most profound change.

I'm having a ball with Elixir!
