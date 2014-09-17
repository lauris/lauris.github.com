---
layout: post
title: "Sensei Anywhere"
category: development
image: /images/blog/sensei-anywhere-screenshot.png
---

Developer productivity is very important for us at [Datazenit](http://datazenit.com). Database administration tools usually do not excel with great efficiency, but we are here to change that. I really enjoy quick navigation features in IDEs and code editors. For example, Sublime Text, IntelliJ IDEA and vim with [ctrlp](https://github.com/kien/ctrlp.vim) or [command-t](https://github.com/wincent/Command-T) plugins provide an exceptionally quick way to navigate between files, classes and methods. 

![Sublime Text Navigation](/images/blog/sublime-text-navigation.png)

<p class="caption">Sublime Text Goto Anything</p>

I want to introduce similar functionality to Datazenit. We have started development on [Sensei Anywhere](https://github.com/datazenit/sensei-anywhere), a navigation tool powered by fuzzy search. The best part of this is that Sensei Anywhere is fully open source. It is essentially a JS library that depends on jQuery and lodash/underscore.js. The library itself is very simple and uncomplicated, it just triggers callbacks that you can listen to and do anything from there. It also means that the library is very flexible and brings no overhead. Sensei Anywhere will be used in Datazenit to quickly navigate between connections, databases, tables and filters. 

The project is currently under heavy development, but you can check out [Sensei Anywhere demo](http://datazenit.com/static/sensei-anywhere/example/). Source code is available at [GitHub](https://github.com/datazenit/sensei-anywhere).

<a href="http://datazenit.com/static/sensei-anywhere/example/" target="_blank"><img style="margin:auto;" src="/images/blog/sensei-anywhere-screenshot.png" alt="Sensei Anywhere Screenshot"></a>

P.S. We recently announced another open source project – [Sensei Grid](https://github.com/datazenit/sensei-grid), simple and lightweight data grid in JS/HTML, that is also a part of Datazenit. 