---
layout: post
title: "Fix Disqus comments on GitHub pages"
category: blog
permalink: /blog/fix-disqus-comments-github-pages
related: [
  "Jekyll related posts",
  "A tiny rant: Jekyll vs. Octopress",
  "Blog like there's nobody reading"
]
image: /images/blog/disqus-logo.png
---

GitHub is a decent company that offers free blog hosting with the benefits of
SSL. Everything is rainbows and sunshine, until you encounter a strange
behaviour from Disqus, a popular commenting system that is often used together
with GitHub pages, because they only support static sites. GitHub pages do not
support automatic redirect to HTTPS (also known as HTTPS only website) and
Disqus treats protocol as part of the website URL which is used to load
comments. See where this is going? Basically you end up with different groups of
comments - those who comment on HTTP and and those who comment on HTTPS. And you
are almost stuck with this.

There are two things you can do. Migrate comments at Disqus administration panel
from http://your_blog_here to https://your_blog_here. I don't know if it works
just yet, because my migration is not finished, but anyway it is more like one
time solution not something you would do on regular basis. Another solution is
to use a meta redirect with JavaScript. It is lame, but it is less lame than
manually migrating comments every time.

If you just want a quick code snippet that does the redirect, here is one I found in this blog post:
[GitHub Pages Now Supports HTTPS, So Use It](https://konklone.com/post/github-pages-now-supports-https-so-use-it)

{% highlight js %}
var host = "YOURDOMAIN.github.io";
if ((host == window.location.host) && (window.location.protocol != "https:")) {
    window.location.protocol = "https";
}
{% endhighlight %}

No matter what I still think that this is an issue Disqus should resolve. I will
try to contact them and see if there is anything they can do about it.
