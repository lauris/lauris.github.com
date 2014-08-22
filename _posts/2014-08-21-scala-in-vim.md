---
layout: post
title: "Scala in Vim"
category: vim
---

I have been a long time Vim user, however in the last few years I have been using it less and less each day in favor of [IntelliJ IDEA](http://www.jetbrains.com/idea/), a superb, fully featured IDE that really does it all. Vim felt right after I got past its steep learning curve and for quite some time I was a true Vim junkie. I used it for everything and had installed [Vimperator plugin](https://addons.mozilla.org/en-US/firefox/addon/vimperator/) for Firefox and [Vimium](https://chrome.google.com/webstore/detail/vimium/dbepggeogbaibhgnhhndojpepiihcmeb?hl=en) for Chrome, configured my window manager [xmonad](http://xmonad.org/) to use Vim-like keybindings, enabled [vi editing mode in bash](http://www.catonmat.net/blog/bash-vi-editing-mode-cheat-sheet/) and so on.

Glorious times they were, but many advanced and useful features like autocomplete, refactoring, code hinting, debugging, integration with other development tools and most importantly a rapidly growing project code base of the time slowly allured me towards an IDE. I couldn't keep the code base in my head and needed tools to quickly explore and inspect the code. Maybe I just became lazier, but the IDE helped a lot. One of the best qualities of a great IDE is that everything just works out of the box and you don't need to spend an eternity to configure it. You can even spend some time on actual programming. But I still missed a lot from Vim, especially keybindings and an unbeatable performance.

Let's revisit Vim and this time particulary for Scala development. I am currently developing [Datazenit](http://datazenit.com) in Scala and I am loving it. Would love it even more if I could take my old friend with me.

<!-- more -->

## Syntax highlighting

There is a little nice package [vim-scala](https://github.com/derekwyatt/vim-scala) by Derek Wyatt. He was also the guy who convinved me to use Vim in the first place with his [Vim screencasts](https://vimeo.com/user1690209/videos). This plugin provides the bare essentials for Scala like syntax highlighting and file type detection, but also a few goodies like sorting of imports. Screenshot below.

<img src="/images/blog/scala-syntax-vim-screenshot.png" alt="Scala syntax highlighting in Vim">

## SBT integration

There is a plugin for SBT integration with Vim called [sbt-vim](https://github.com/ktvoelker/sbt-vim), but honestly it doesn't give you much and I just prefer doing all my SBT related activities in the terminal. 

## Autocomplete

Back in the day autocomplete was a huge problem with Vim because none of the plugins were working flawlessly and they were always a pain to set up. After a little research it seems that currently the best autocomplete plugin is [neocomplete.vim](https://github.com/Shougo/neocomplete.vim), a successor to neocomplcache, both of them made by Shougo. Sadly it does not provide support for Scala, so the next candidate is [YouCompleteMe](https://github.com/Valloric/YouCompleteMe) by Val Markovic. It is a bit better than other autocomplete plugins, mostly thanks to its client-server architecture and a compiled component. But bad news again - no serious Scala support out of box. 

The only way to get a real autocomplete for Scala is to use Eclim, which was also the only option when I last checked few years ago. Eclim is basically a headless instance of Eclipse integrated with Vim. I went this route once and it worked, but it just didn't feel right. There are some good things about Eclim, for example, it supports more Eclipse features than just autocomplete and you choose a wide variety of supported languages.

The conclusion is that nothing has changed much. Sure, autocomplete works for some languages, but there is still no silver bullet. 

<img src="/images/blog/scala-vim-eclim.png" alt="Scala Vim Eclim">

## Refactoring and other features

The story is pretty much the same as with autocomplete. Eclim provides some useful features like automatic imports, basic refactoring and code validation that works, but there is no other Vim plugin that does that. At least to my knowledge.

## Summary

If you are willing to use something like Eclim or just live without any intelligent features then Vim can be used for Scala development. In this case it has always been ready. But if you want something more, then you are out of luck. I can't imagine serious Scala development without those features. 

Some IDEs have plugins for Vim integration or at least support vi keybindings, but that's usually an even worse experience. Some people are trying to improve Vim and give it a second wind. One of those projects is [Neovim](https://github.com/neovim/neovim) – "a project that seeks to aggressively refactor Vim". I have no idea how it will turn out, but let's hope for the best.

Does all this mean that you shouldn't use Vim? Of course not! Vim is still the best text editor out there and for many use cases it is just perfect. I am still using it almost every day when I don't need IDE-like features or when I want to code really fast. You can also get a pretty decent experience programming Python, Ruby, C/C++ and other languages in Vim, just not so much Scala.