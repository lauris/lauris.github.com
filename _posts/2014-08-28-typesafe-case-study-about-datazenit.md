---
layout: post
title: "Typesafe's case study about Datazenit"
category: datazenit
---

[Typesafe](http://typesafe.com) is occasionally publishing case studies about companies using Scala and their Reactive Platform. I was pleasantly surprised when they asked me to collaborate on a case study about [Datazenit](http://datazenit.com). Backend of Datazenit is developed in Scala and built on top of Play framework. I wrote about [switching from Python to Scala](http://datazenit.com/blog/2014/05/19/datazenit-scala/) a few months ago and the article gained some traction inside Scala community. Soon after that Typesafe reached out and wanted to learn more about how we use Scala. I was happy to share, and after several discussions and drafts a case study was born. The study covers the reasons why did we choose Scala, what were our expectations and the end result. You can read **[the full paper here](http://downloads.typesafe.com/website/casestudies/Datazenit-Final.pdf)** and check out other interesting case studies at [Typesafe's website](http://typesafe.com/company/casestudies). It is an honor to be amongst other tech giants like Twitter, LinkedIn and Foursquare.

<!-- more -->

<p><a href="http://typesafe.com/blog/code-size-is-down-performance-is-up--why-datazenit-went-reactive-"><img style="margin:10px auto;" src="/images/blog/datazenit-case-study-quote.png" alt="Datazenit case study"></a></p>

The Reactive Platform consists of several parts, most notably: Scala, a functional programming language, Akka toolkit, Play framework and Sbt, a Scala build tool. Most of these were used in the development of Datazenit, except for Akka. Even though we don't use Akka now, we will probably be using it in the future. Akka toolkit implements [the actor model](http://en.wikipedia.org/wiki/Actor_model) and makes concurrent programming a breeze. It is one of the most straightforward ways to build highly concurrent and distributed software. 

It was a pleasure to work with Typesafe, they are professionals in everything they do. Martin Odersky, the chairman of the board at Typesafe and also the author of Scala, is one of my programming idols. I had a chance to learn from him the fundamentals of functional programming in Coursera course ["Functional Programming Principles in Scala"](https://www.coursera.org/course/progfun). I highly recommend the course, it was well thought out and interesting, the lecture materials are handy even now. The course is just a few weeks long and covers quite a lot. 

So what are you waiting for? If you are interested in stepping up your programming skills and expanding your view, Scala can help you open the doors.

----

Case study: [Datazenit-Final.pdf](http://downloads.typesafe.com/website/casestudies/Datazenit-Final.pdf)