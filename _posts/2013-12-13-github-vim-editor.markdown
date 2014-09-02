---
layout: post
title: Vim editor for Github
---
Today there was [a topic](https://news.ycombinator.com/item?id=6899072) on HN about [Vim.js](http://coolwanglu.github.io/vim.js/web/vim.html), a JavaScript port of Vim. Some people were [asking](https://news.ycombinator.com/item?id=6899374) about a way to integrate the Vim editor with Github.

<!-- more -->

Github currently uses [Ace editor](http://ace.c9.io/), and I remembered that it had a Vim mode from the time when I was implementing Ace with [Datazenit](http://datazenit.com). You can press ``CTRL+,`` or ``CMD+,`` (depends on your OS) to access Ace's settings menu and enable Vim mode there ([screenshot](https://www.dropbox.com/s/69m9u12d0696vb0/Screenshot%202013-12-13%2013.54.24.PNG)). The menu itself works ok, but sadly the Vim mode doesn't, because some required JavaScript files are not available from Github. However it can be easily fixed -- we just need to include the correct JS module and we get a working Vim editor in Github. Paste the following code (found on [SO](http://stackoverflow.com/questions/15485153/enable-vim-mode-in-gist-ace-editor)) in your developer tools console:

{% highlight js %}
ace.require("ace/lib/net").loadScript("https://raw.github.com/ajaxorg/ace-builds/master/src-min-noconflict/keybinding-vim.js", function() { 
  e = $(".file-contents").codeEditor().editor;
  e.setKeyboardHandler(ace.require("ace/keyboard/vim").handler); 
})
{% endhighlight %}

<b>Update!</b> Github changed some HTML code structure, so I have updated the snippet above.
