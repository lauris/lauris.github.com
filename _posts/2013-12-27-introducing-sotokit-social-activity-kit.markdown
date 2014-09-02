---
layout: post
title: "Introducing Sotokit: A Social Activity Kit"
---
When Christmas celebration was over, I decided to spend an afternoon to code a little idea I had. There was a left over domain **[Sotokit.com](http://sotokit.com)** from the times when we repeatedly changed the name of [Datazenit](http://datazenit.com), so luckily no time was wasted choosing the name - otherwise it would have been more than just an afternoon.

<!-- more -->

The idea was dead simple -- to gather social activity for any URL. Currently [Sotokit.com](http://sotokit.com) supports Hacker News, Reddit & Twitter. What's the use case? Well, I am planning to use this as a starting point for something more interesting -- the plan is to make the social activity feed embeddable in any website. It would take current URL or accept a keyword and show related social activity anywhere on the page. I will use this myself to replace the comments section in this blog because all the discussion is happening in the communities anyway. This functionality could be useful not only for blogs but also for product reviews & feedback, static websites and similar use cases. Maybe there are even better scenarios I haven't thought of.

A bit about the technical side -- the project was built on top of node.js with the following packages: express.js, async, request, twitter, forever. The packages + Twitter Bootstrap really helped to develop Sotokit rapidly and without headaches.  

[![Sotokit Screenshot](/images/blog/sotokit-screenshot.png)](http://sotokit.com)

What do you think? Share your thoughts on [HN](https://news.ycombinator.com/item?id=6969916), [Reddit](http://www.reddit.com/r/programming/comments/1tsp2w/introducing_sotokit_a_social_activity_kit/) or [Twitter](https://twitter.com/lauriswtf/status/416485942166167553). 
