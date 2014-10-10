---
layout: post
title: "Map order in Scala"
category: scala
permalink: /map-order-scala
related: [
  "Scala in Vim", 
  "Building MySQL column definition with Scala",
  "Typesafe's case study about Datazenit",
  "Awesome Scala"
]
---

Scala offers several ways to deal with Maps and their order. There is the regular Map that doesn't preserve order of items at all, LinkedHashMap that preserves the order, but is not immutable. Luckily ListMap tries to save the situation. It is an implemenation of immutable maps using a list-based data structure that preserves insertion order. Everything is good until you try to create an updated version of the ListMap. 

<!-- more -->

{% highlight scala %}
val a = ListMap("first" -> "foo", "second" -> "bar")
val b = a.updated("first", "foo2")
// b: ListMap[Int,String] = Map(second -> bar, first -> foo2)
{% endhighlight %}

The updated ListMap instance loses the insertion order. To some extent it makes sense, because in the new ListMap ``(first -> foo2)`` was inserted after ``(second -> bar)``. However the intention was an update.

Seems that there is not a built-in solution for this, so I have chosen to simply use a List that holds a static order of the Map items. It may introduce a small overhead, but is a simple and robust solution. In my particular use case the working set is a very small one, meaning that the tiny overhead won't be even noticable.