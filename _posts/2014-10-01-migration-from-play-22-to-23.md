---
layout: post
title: "Migrate Play framework from 2.2 to 2.3"
permalink: "/scala/migrate-play-framework-2.2-to-2.3"
category: development
related: ["The Technology Behind Datazenit: Part 1", "Awesome Scala", "Typesafe's case study about Datazenit", "Scala in Vim"]
image: /images/blog/play-framework-terminal.png
---

I am using Scala and Play framework to build [Datazenit](http://datazenit.com), a web-based database administration tool. Today I decided to upgrade Play framework to the latest stable release. The 2.3 version was already available for some time now, but I wanted to wait a bit to see if there are any problems with it. The latest version of the 2.3 branch is 2.3.4 and it seems to be stable enough.

<!-- more -->

Play framework has [official docs on migration](https://www.playframework.com/documentation/2.3.x/Migration23) from 2.2 version, but in my particular case the migration didn't went perfectly smooth, and it took some time to get the project working again. If someone happens to be in the same situation, here are some tips and a simplified guide to the migration. 

The migrations docs are quite verbose and covers many different topics, but the essential part to upgrade Play framework is to change Play sbt plugin version in **project/plugins.sbt** file.

{% highlight scala %}
addSbtPlugin("com.typesafe.play" % "sbt-plugin" % "2.3.4")
{% endhighlight %}

Also you need to change sbt version in **project/build.properties** file. 

{% highlight scala %}
sbt.version=0.13.5
{% endhighlight %}

Two biggest changes in **build.sbt** file are Scala version and Play auto-plugin. Scala version must be set explicitly, because Play now supports both 2.10 and 2.11 versions of Scala. The second line adds Play as auto-plugin. You should also remove a previously needed line ``play.Project.playScalaSettings``. More info about this can be found in the migration docs.

{% highlight scala %}
scalaVersion := "2.11.2"
lazy val root = (project in file(".")).enablePlugins(PlayScala)
// play.Project.playScalaSettings
{% endhighlight %}

After these changes you can run ``sbt update`` or launch activator, and it should update Play framework and all standard dependecies. However I had several other libraries added to my project and needed to bump their versions for them to work nicely with Play 2.3. My ``libraryDependencies`` (found in **build.sbt**) now looks approximately like this (irrelevant dependecies removed).

{% highlight scala %}
libraryDependencies ++= Seq(
	jdbc,
	"org.webjars" %% "webjars-play" % "2.3.0",
	"com.typesafe.play" %% "play-slick" % "0.8.0",
	"org.scalikejdbc" %% "scalikejdbc" % "2.1.2",
	"org.scalikejdbc" %% "scalikejdbc-play-plugin" % "2.3.2"
)
{% endhighlight %}

Play 2.3 requires Slick 2.1 instead of 2.0, and it caused another tiny hiccup. Slick has [migration docs](http://slick.typesafe.com/doc/2.1.0/upgrade.html) on their website that are reasonably well structured. I had to remove parentheses from ``list`` methods and change ``where`` to ``filter``, but that was about it. 

Now that I have written this small guide, everything seems pretty basic and straightforward, but in practice it took some time to get everything right. I was surprised when I checked performance after 2.3 upgrade – it seems that the average load times have increased from 20ms to around 50-70ms. This definitely needs more investigation, but I hope that it will be possible to resolve.