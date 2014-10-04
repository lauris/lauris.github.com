---
layout: post
title: "Jekyll related posts"
category: blog
permalink: /blog/jekyll-related-posts
related: ["A tiny rant: Jekyll vs. Octopress", "6 Weeks of Daily Blogging", "Bash Productivity Tips"]
---

Jekyll has related posts functionality built in, but it is flawed, especially when deployed on GitHub pages, because related posts are the same for each post. I wanted to be able to add related posts manually, and after little tweaking it turned out to be pretty easy.  

<!-- more -->

I wanted to define related posts by title, but this can be easily changed. In your post template add this code snippet where you want the related posts to show up.

{% highlight liquid %}
{% raw %}
{% if content and page.related %}
    <h2>Related Posts</h2>
    <ul>
    {% for post in site.posts %}
        {% if page.related contains post.title %}
            <li><a href="{{ post.url }}">{{ post.title }}</a></li>
        {% endif %}
    {% endfor %}
    </ul>
{% endif %}
{% endraw %}
{% endhighlight %}

After you have added the code to your post template, just use ``related_posts`` parameter in your YAML front matter. An example from this blog post.

{% highlight yaml %}
---
layout: post
title: "Jekyll related posts"
category: blog
permalink: /blog/jekyll-related-posts
related: [
    "A tiny rant: Jekyll vs. Octopress", 
    "6 Weeks of Daily Blogging", 
    "Bash Productivity Tips"
]
---

Blog post content here.
{% endhighlight %}

If you want to change the way how related posts are defined, just change the post parameter in ``if`` condition: ``{% raw %}{% if page.related contains post.title %}{% endraw %}``. For example, if you want to define related posts by url, the code would look like this: ``{% raw %}{% if page.related contains post.url %}{% endraw %}``