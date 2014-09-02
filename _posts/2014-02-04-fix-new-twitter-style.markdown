---
layout: post
title: Fix for the new twitter design
---
I don't like the new twitter design update, but the goods news are that it is very easy to fix. My biggest complaint is about the width of navigation bar -- it is wider than the main content and it doesn't make any sense. IMO the width should be the same for both navigation bar and content in this case. 

<!-- more -->

[Stylish, a browser extension for Chrome & Firefox](http://userstyles.org/) will help us to change the design with just few lines of CSS. You need to add a new rule in Stylish, which applies to a domain <b>twitter.com</b>, and add style rules which you can see below. Check code comments for clues what the code does.

{% highlight css %}
/** Fix navigation bar width */
.global-nav .container { max-width: 910px; }
 
/** Hide Me & DM menu items */
.global-nav li.profile, .global-nav .dm-nav { display: none; }
 
/** Remove bottom border from active menu item and just set text color to black instead */
#global-actions > li > a { border-bottom: none; }
#global-actions > li:hover > a, #global-actions>li.active>a { color: black; }
{% endhighlight %}

This is how it looked before:
![Twitter fucked](/images/blog/twitter-fucked.png)

And after:
![Twitter fixed](/images/blog/twitter-fixed.png)
