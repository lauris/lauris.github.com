---
layout: post
title: "\"Alter Column\" differences between MySQL and PostgreSQL"
category: database
permalink: /database/alter-column-differences-between-mysql-postgresql
---

SQL is a standard that would make our lives easier if it was implemented consistently across major database back-ends. Beyond simple queries it is rarely the case, and one example is table alteration. Today I was writing an abstraction over JDBC that will be used behind [Datazenit](https://datazenit.com) Schema Builder, and I got reminded about those differences once again.

<!-- more -->

Postgres has a nice syntax to modify columns in a table. For example you can change each attribute separately. 

{% highlight sql %}
ALTER TABLE "my_table" ALTER COLUMN "foo" TYPE varchar(10);
{% endhighlight %}

MySQL is a bit more clumsy than Postgres and allows changing a column as only a whole. It means you must specify each attribute if you don't want to lose existing column settings.

{% highlight sql %}
ALTER TABLE `my_table` MODIFY COLUMN `foo` VARCHAR(10) 
CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL;
{% endhighlight %}

As you can see this introduces a lot of unnecessary paramaters to the query. You must also know all the attributes beforehand. Another thing you may have noticed is the difference between identifier quote symbols, but that's a topic for another time. 

How to get all settings for a column if MySQL requires them? There are several options, but an convenient way is a ``SHOW FULL COLUMNS`` query.

{% highlight sql %}
SHOW FULL COLUMNS FROM `my_table` WHERE Field = "foo";
{% endhighlight %}

The output will be similar to the table shown below except with even more info.

|Field|Type|Collation|Null|Default|
|---|---|---|---|---|
|foo|varchar(10)|utf8|YES|NULL|

You can use this data to build the definition of column on the server side. For those that prefer a one-liner, StackOverflows provides [a solution](http://stackoverflow.com/a/22914977/2047160). It is a single MySQL query that returns the final column definition. Below is a little bit modified version that uses CONCAT_WS instead of CONCAT with manual spaces and includes all column parameters.

{% highlight sql %}
SELECT 
  CONCAT_WS(
    ' ',
    COLUMN_NAME, 
    'NEW_TYPE', 
    IF(IS_NULLABLE = 'NO', 'NOT NULL', '')
    IF(COLUMN_DEFAULT IS NOT NULL, CONCAT('DEFAULT ', QUOTE(c.COLUMN_DEFAULT)), ''), , 
    EXTRA,
    IF(COLUMN_COMMENT IS NOT NULL, CONCAT('COMMENT ', QUOTE(c.COLUMN_COMMENT)), '')
  ) AS s
FROM 
  INFORMATION_SCHEMA.COLUMNS 
WHERE 
  TABLE_SCHEMA = 'test' 
  AND TABLE_NAME = 'my_table'
  AND COLUMN_NAME = 'foo'
{% endhighlight %}

Examine and test before using any of this. I will stick to manipulating the data from server side, because my Schema Builder must be able to change all parameters not just the type, and writing a large query for each parameter would be an overkill. Also Scala, the back-end language of [Datazenit](https://datazenit.com), provides more flexibility and abstraction than SQL. Obviously.