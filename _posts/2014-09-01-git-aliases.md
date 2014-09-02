---
layout: post
title: "Git aliases"
category: development
---

Git is the best version control system and one of my favorite development tools in general. It is small, fast and has some Linux-coolness to it. In this blog post I will share a few handy git commands that I have defined as aliases. Aliases can be defined in [.gitconfig](http://git-scm.com/docs/git-config) file located in your home directory. Aliases are basically shortcuts to frequently used or just long commands. The aliases listed in this post are in form ``<name of alias> = <git command>``. The same format is used in the ``.gitconfig`` file. Just prefix the ``<git command>`` with "git" and you can use it without setting an alias.

<!-- more -->

## Show unpushed changes

``unpushed = log --stat origin/master..HEAD``

Sometimes I want to know what commits and their respective changes have not yet been pushed. This little command helps with that.

## Grouped search

``gg = grep --break --heading -n``

Git grep is cool, but you know what is even cooler? Grouped git grep – it group matches by file name and make it very easy to overview the search results. 

![Git grouped grep](/images/blog/git-grouped-grep.png)

## Simple list of commits (colored)

``cl = log --graph --pretty=format:"%an: %s%C(yellow)%d%Creset %Cgreen(%cr)%Creset" --date=relative``

``cls = log --pretty=format:"%an (%ae): %C(yellow)%s%Creset" --shortstat``

There are different versions of this command, but I tend to use these two shown above. The first one is super short, each commit takes on line and displays a relative date after the commit message. The second one includes changed file overview.

## Shallow clone

``sc = clone --depth=1``

I have used shallow clone only a couple of times, but this can come in handy when you want to clone a repo without the baggage.

## Fix commit message

``fc = commit --amend -m``

Pretty often I notice a mistake in my commit message only after it is already commited. The previous commit can be modified with the ``--amend`` argument.

## Overview of file 

``fo = log --pretty=oneline --shortstat --abbrev-commit``

This command can be followed by the path to the file, but can also be used as a standalone command for short summary. It also has short commit hashes because of ``--abbrev-commit``.

## Interactive ``add``

``ic = add -p``

Even though this a very short command, it is a very useful one because it lets you interactively choose and review hunks of unstaged changes.

## Show a word diff

``diff = diff --word-diff``

Shows each change along with the replaced value. By default, words are delimited by whitespace.

<hr style="height:1px;">

Extra: ``git status`` is aliased to ``git st`` together with all the other standard commands because I am lazy and those few characters save me time every day.