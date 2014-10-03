---
layout: post
title: "Switching to CodeMirror"
category: development
related: ["Bash Productivity Tips", "The Technology Behind Datazenit: Part 1", "Awesome Scala"]
image: /images/blog/code-mirror-screenshot.png
---

From the beginning of time [Datazenit](https://datazenit.com/) was using [Ace
editor](http://ace.c9.io/) as raw query editor. Ace is really great and all that, especially because it has proved itself as a component in several cloud IDEs and large projects ([projects using Ace](http://ace.c9.io/#nav=production)). However it is a massive and complex tool, and for us it introduces too much overhead, because we are using just a small portion of its capabilities.

![CodeMirror Screenshot](/images/blog/code-mirror-screenshot.png)

<p class="caption">CodeMirror Screenshot</p>

<!-- more -->

Few years ago [CodeMirror](http://codemirror.net/) didn't seem stable enough,
but when I checked it recently it seemed to be mature and stable, so I decided
to switch Datazenit to CodeMirror. It is lightweight compared to Ace and offers
all the features we need. It was really easy to configure auto-complete and SQL mode resulting in a seamless transition. I would say that CodeMirror is more straightforward and simpler to use than Ace.

To make things even better turns out that there is an undocumented feature in CodeMirror, that enables auto complete for tables and columns with a simple configuration parameter.

{% highlight js %}
hintOptions: {
	tables: {
		"some_table": ["id", "foo", "bar", "other_column"]
	}
}
{% endhighlight %}
