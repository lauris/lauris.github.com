---
layout: post
title: "Building MySQL column definition with Scala"
category: database
permalink: /database/building-mysql-column-definition-scala
related: [
  "\"Alter Column\" differences between MySQL and PostgreSQL", 
  "Database drivers in a commercial product",
  "The Technology Behind Datazenit: Part 1"
]
---

Yesterday I wrote about [differences between Alter Column commands in MySQL and PostgreSQL](https://lauris.github.io/database/alter-column-differences-between-mysql-postgresql/). To change even a single parameter of a column, MySQL requires the whole definition of column to be specified. I decided to write the definition building login in Scala not SQL. 

<!-- more -->

Scala's pattern matching comes in handy and after a long session of trial and error I had a flexible method to create column definitions for any table. I have also learned about a dozen ways how to not solve this problem.

{% highlight scala %}
// pseudo code for val column = Query("SHOW FULL COLUMNS FROM `some_table`").head
column.map {
  case (key, value) =>
    key match {
      case "Field" => value.map(x => s"`$x`").getOrElse("")
      case "Type" => value.map(x => s"TYPE $x").getOrElse("")
      case "Collation" => value.map(x => s"CHARACTER SET $x").getOrElse("")
      case "Null" if value == Some("NO") => "NOT NULL"
      case "Null" if value == Some("YES") => "DEFAULT NULL"
      case "Default" => value.map(x => s"DEFAULT $x").getOrElse("")
      case "Comment" => value.map(x => s"COMMENT $x").getOrElse("")
      case _ => ""
    }
}.filter(_.nonEmpty).mkString(" ")
{% endhighlight %}

The code yields a column definition that can be later used to create an ALTER COLUMN statement.

{% highlight sql %}
`title` TYPE varchar(200) CHARACTER SET latin1_swedish_ci NOT NULL
{% endhighlight %}

A side note: ListMap must be used to preserve the order of a map. The order is important in my case, because otherwise it would result in a invalid column definition. 
