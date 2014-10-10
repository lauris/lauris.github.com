---
layout: post
title: "Up arrow in SBT"
category: scala
permalink: /scala/up-arrow-in-sbt
related: ["Bash Productivity Tips", "Git aliases", "Scala in Vim"]
---

For quite some time I didn't understand why the console in sbt, the scala built tool, is using up arrow for activating reverse-i-search (normally used in terminal with keyboard shortcut CTRL+R). This was one of those small bugs that are not annoying enough for you start searching for a solution straight away. After some time I got fed up and did some googling. Turns out it is not a bug within sbt, but a common side-effect caused by ``~/.inputrc`` configuration.

<!-- more --> 

Some time ago I had configured a sweet bash productivity feature that completes partial commands from history with the up arrow. I wrote about this and other [bash productivity tips](https://lauris.github.io/bash-productivity-tips/) a few weeks ago.

{% highlight bash %}
"\e[A": history-search-backward
"\e[B": history-search-forward
set show-all-if-ambiguous on
set completion-ignore-case on
{% endhighlight %}

Luckily this feature can be kept in bash, but disabled everywhere else. [The inputrc fix](https://groups.google.com/forum/#!msg/simple-build-tool/ShikT6VAd_g/HynXhvZuNZ8J) provided was originally posted by Paul Phillips on sbt google group. Just wrap the conflicting part of inputrc with a simple conditional.

{% highlight bash %}
$if Bash
  "\e[A": history-search-backward
  "\e[B": history-search-forward
$endif
{% endhighlight %}

Best of both worlds. Up arrow still works its magic in bash and the standard way in sbt console. Also CTRL-R can be used for history searching in sbt. 