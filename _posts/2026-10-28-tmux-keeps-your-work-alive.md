---
layout: post
title: "tmux keeps your work alive"
subtitle: "The terminal tool that doesn't forget when you close the window"
categories: [tech]
---

The first time i closed a terminal window by accident, i lost a command that had been running for a while. I had to start over from zero. Then my brother told me to use tmux, and i kept seeing it in tutorials and on other people's screens, but i never really knew what it was. All I knew was that it makes the terminal look like it's chopped into pieces. So I want to find out what tmux actually is, why people like it so much, and whether it's something i should learn too.

## What is tmux?

tmux stands for "terminal multiplexer". Big name, but the idea is simple: it lets you run a bunch of terminals inside one terminal window, and it keeps them running in the background even when you're not looking at them. It was written by Nicholas Marriott, and the first version came out in November 2007.[^wiki]

It has three pieces, and once I understood them, it all made sense:

- A **session** is the whole workspace. You can name it, like "blog" or "work".
- A **window** is like a tab inside the session.
- A **pane** is a piece of a window. This is the "chopped into pieces" look, where you can have a few terminals on one screen at once.

## Where it came from

Before tmux, there was a tool called GNU Screen that did the same kind of job. From what I read, Marriott was a long-time Screen user, and he wrote tmux from scratch because he didn't like how Screen was set up and documented.[^voss] The project described itself early on as a simple, modern alternative to Screen, with a license that lets anyone use it freely. It got added to OpenBSD in 2009, and these days you'll find it on pretty much every Linux machine and Mac.[^wiki]

## The part that makes it worth it

Here's the thing that fixes my "lost an hour of work" problem. tmux runs as a separate program in the background (a "server"), and your terminal window is just a viewer that connects to it. So if you close the window, or your internet drops while you're connected to another computer over SSH, the server keeps going with everything still running inside. The manual says it directly: each session is persistent and will survive an accidental disconnection.[^man]

When you come back, you reconnect and everything is right where you left it. It's like closing a laptop lid instead of shutting it down.

## The basics

I'm still new to this, so here are the few things I'd actually use, straight from the manual.[^man] Every shortcut starts with a "prefix", which is `Ctrl-b` by default. You press that first, let go, and then press the next key.

- `tmux new -s blog` starts a new session called "blog".
- `Ctrl-b d` detaches, which means you leave but everything keeps running.
- `tmux ls` lists your sessions.
- `tmux attach` gets you back in.
- `Ctrl-b c` opens a new window.
- `Ctrl-b %` splits the pane left and right, and `Ctrl-b "` splits it top and bottom.

One thing the manual doesn't promise: sessions survive a closed window or a dropped connection, but I didn't find anything saying they survive a computer restart. I'd assume they don't, since the server is just a program that stops when the machine does.

## Is it worth learning?

For me, the long-running stuff is the reason. If you ever run something that takes a while, or work on a server through SSH, tmux means a bad connection doesn't wipe out your work. The panes are nice too, but I could probably live without them.

The downside is the shortcuts. Having to press a prefix first before every command feels strange at the start, and it's easy to forget the keys. I think the way to learn it is to start small: just sessions, detach, and attach, then add the rest as I need it.

## References

[^wiki]: [Tmux](https://en.wikipedia.org/wiki/Tmux) (Wikipedia). Source for the first release date (20 November 2007) and the OpenBSD timing. Other pages say it was in OpenBSD 4.6, which came out in October 2009.
[^voss]: [Technical Beauty: tmux](https://vivianvoss.net/blog/technical-beauty-tmux) (Vivian Voss). This is one person's opinion piece, so the story about why Marriott wrote it is their telling and not something I checked anywhere else.
[^man]: [tmux manual page](https://man.archlinux.org/man/tmux.1.en.raw) (Arch Linux). Source for the default prefix, the commands above, and the line about sessions surviving disconnections. I only read the first part of this long page.
