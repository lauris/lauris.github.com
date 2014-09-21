---
layout: post
title: "Bash Productivity Tips"
permalink: "/bash-productivity-tips"
category: development
related: ["Git aliases", "5 Productivity Tips for Developers", "Work and open source #2: Sensei Grid", "The Technology Behind Datazenit: Part 1"]
---

I want to share a few tips for better Bash productivity. You will be surprised that not a single one of them is "Just install zsh".

<!-- more -->

## History searching

``CTRL+R`` is cool, but you know what is even cooler? The ability to complete commands from history with up/down arrows. For example, enter ``cd``, press up and it gets autocompleted with ``cd ~/your/last/directory/change/``. This little snippet below must be put into ``~/.inputrc`` and you are good to go.

{% highlight bash %}
"\e[A": history-search-backward
"\e[B": history-search-forward
set show-all-if-ambiguous on
set completion-ignore-case on
{% endhighlight %}

## Execute previous command

This one is also history related, and I use it countless times every day. Use ``!!`` to get the most recent command. For example, ``sudo !!`` will execute your previous command as sudo. Also ``!$`` can be handy, because it allows to re-use last parameter from previous command. I actually use an even quicker shortcut for this: ``ESC+.``. However the shortcut may be terminal/OS dependant.

## Jump between current and previous directory

Change your directory to the last directory you were in with a simple ``cd -``. This way you can quickly switch between two working directories. 

## Display file size in a human readable format

If you have executed a command that returns files together with file sizes, there is a great chance, that adding ``-h`` option to the command will return the file sizes in a more readable format. Take for an example the good old ``ls -la``. By default it returns file size in bytes. Just add "h" to the options ``ls -lah``, and you have file sizes in megabytes.

## Essential shortcuts

I hope that everyone nows about ``CTRL+arrows`` to jump between words, but there are a few other shortcuts that are as important as ``CTRL+arrows``. Full list can be found online, e.g., on Wikipedia: [Bash#Keyboard_shortcuts](http://en.wikipedia.org/wiki/Bash_(Unix_shell)#Keyboard_shortcuts).

* ``CTRL+a`` jump to the beginning of line
* ``CTRL+e`` jump to to the end of line
* ``CTRL+w`` will delete a word backwards
* ``CTRL+z`` pause a command
* ``CTRL+l`` clear the screen
* ``CTRL+d`` exit current shell

## Quickly transfer your key to a remote host for a password-less login

This is not a tip for every day situations, but occasionally it saves a few commands. Use ``ssh-copy-id user@remote_host`` to quickly copy the identity file to the remote host to enable password-less login. Passwords should be avoided for ssh anyway. 