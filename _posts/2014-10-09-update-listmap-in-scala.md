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

Scala offers several ways to deal with Maps and their order. There is the regular Map that doesn't preserve order of items at all, LinkedHashMap that preserves the order, but is not immutable. Luckily ListMap tries to save the situation. It is an implemenation of immutable maps using a list-based data structure that preserves insertion order. Everything is good until you try to create an updated version of a immutable ListMap. 

{% highlight scala %}
val a = ListMap(1 -> "foo", 2 -> "bar")
val b = a.updated(1, "foo2")
// b: ListMap[Int,String] = Map(2 -> bar, 1 -> foo2)
{% endhighlight %}

The updated ListMap instance loses the insertion order. To some extent it makes sense, because in the new ListMap ``(1 -> "foo2")`` was inserted after ``(2 -> "bar")``. 

Seems that there is not a built-in solution for this, so I chose to simply use a List that holds a static order of the Map items. It may introduce a small overhead, but is a simple and robust solution. My working set size is a very small one, meaning the small overhead won't even be noticable.