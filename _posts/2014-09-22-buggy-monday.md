---
layout: post
title: "Buggy Monday"
category: development
image: /images/blog/bootstrap.png
related: ["Work and open source", "Work and open source #2: Sensei Grid", "First public release of Sensei Grid"]
---

I was feeling productive today, but all that energy was wasted on a single bug, that caused 1px text alignment misperfection in Firefox. 

<!-- more -->

![bootstrap/firefox bug](/images/blog/bootstrap.png)

<p class="caption">The 1px issue</p>

The subject was a table with some casual styling (part of [Sensei Grid](https://github.com/datazenit/sensei-grid)). By default it rendered great both in Chrome and Firefox. However when Twitter Bootstrap stylesheet was added to the document, **text in table cells gets moved by 1px in Firefox**. However I wasn't even adding Bootstrap's ".table" class to my table. I tested different cases and it seems that it was caused by something global in bootstrap.css instead of a table related style. I was only able to determine that the bug was tied to line-height. 

I tried to override the line-height rule for every element in my table, but it didn't help.

{% highlight css %}
.my-table *,
.my-table *:before,
.my-table *:after {
    line-height: normal !important;
}
{% endhighlight %}

It gets really strange, because when I add a global line-height fix, my table finally renders properly. Also when adding this line-height rule only to body or table, it has no effect.

{% highlight css %}
* {
    line-height: normal !important;
}
{% endhighlight %}

I tried comparing both versions with devtools and even computed styles, but there didn't seem to be any difference between styles applied to the table when boostrap.css is loaded. 

Thanks to [some user on StackOverflow](http://stackoverflow.com/questions/25975751/strange-1px-bug-in-firefox-with-bootstrap-css?noredirect=1#comment40677648_25975751) I managed to find the root of the problem. It was the line-height of a H1 element. The strange part is that the H1 element wasn't even in the table, but in another wrapper few elements above the table. HTML structure was valid and there wasn't even any floats or other usual suspects of problem causing. 

I still don't know why the line-height of a H1 element caused this, but I had already spent so much time on this, that I was fed up with all this and just fixed the issue.

While developing Sensei Grid I have stumbled on several Firefox specific bugs that made me think that Firefox is the new IE. I found some bugs on Firefox's bug tracker that are open for several years and it seems that they will stay open forever. Meanwhile on I see announcements and blog posts about new Firefox features every other week. This looks like a popular trend among many open source projects - not fixing old bugs, but instead releasing new fancy features that I don't care about.

