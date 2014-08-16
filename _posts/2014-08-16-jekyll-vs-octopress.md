---
layout: post
title: "A tiny rant: Jekyll vs. Octopress"
category: blogging
---

Before switching to [Jekyll](http://jekyllrb.com/), I tried out [Octopress](http://octopress.org/), a blogging framework built on top of Jekyll. I was really surprised to find out how much I disliked the experience with Octopress. I had an impression that it is a hacker friendly, simple and extensible blog platform, but it was the opposite of that. There are many layers of abstraction, themes are pretty complicated, it comes with many (19) pre-installed plugins out of the box, dozen depedencies (ruby gems), it uses Sass by default and so on. A fresh copy of Octopress blog consists of [staggering 29 directories and 144 files](https://gist.github.com/lauris/5ac34dd97b178b073ece). That's wordpress-much. 

Octopress works almost ok if you are willing to invest plenty of time to customize it or need to build something complex, but it wasn't my particular use case. The complexity of Octopress defeats the whole purpose of a simple, generated static site. But you know what is "hacker friendly, simple and extensible blog platform"? That's Jekyll! Jekyll is dead simple and practical. It was a pleasure to setup and customize the default theme. It took less than an hour to have a fully customized blog just the way I wanted. So I am staying with Jekyll this time. The directory structure is really simple and you start with the bare essentials, a simple layout and a CSS file. That's it! 

I tend to prefer simplicity and unix-like philosophy when it comes to choose every day tools for specific tasks. I can always extend, build and combine on top of that, when the time comes. 