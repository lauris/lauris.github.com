---
layout: post
title: "The Technology Behind Datazenit"
category: development
---

Technology behind Datazenit. 

Datazenit is a [web-based database administration tool](http://datazenit.com/). It is a standalone app, that doesn't require installation - just download and run it. You can then access Datazenit via any browser through specific address, e.g., http://localhost:9000/. It is somewhat similar to the model used by phpMyAdmin and similar tools. Datazenit becomes most useful when deployed on a server, because from there all your team can access it, share connections, queries, datasets, charts, etc. This is something all other database tools lack. 

<!-- more -->

## Backend

The backend of Datazenit is built in Scala. I have written about our [decision to choose Scala](http://datazenit.com/blog/2014/05/19/datazenit-scala/) earlier (there is even a [case study by Typesafe](http://lauris.github.io/datazenit/2014/08/28/typesafe-case-study-about-datazenit/)), but the main benefits are that it is a great functional language and it compiles down to Java bytecode which can be run practically anywhere.

We chose [Play framework](https://www.playframework.com/) as the next layer in our backend, because it is a mature framework, great productivity wise and provides all the necessary ingredients to build a RESTful, modular and safe backend. Another important part of the backend is JDBC abstraction layer, a database access library [ScalikeJDBC](http://scalikejdbc.org/). JDBC is Java-based database connector that supports a wide variety of database management systems, especially relational ones which are our main target for initial releases. Working directly with JDBC can be often a tedious task, and this is where ScalikeJDBC helps us. It provides an easy to use and robust API over JDBC.

## Frontend

The frontend of Datazenit is much bigger than the backend and is also a way more complex. It is built on top of [Backbone.js framework](http://backbonejs.org/) that is hands down the best JS framework I have used. I really enjoy its simplicity, the fact that it doesn't try to interfere with you in any way and just provides the bare essentials. It is a solid foundation that doesn't introduce overhead or complexity. We also use Require.js to make everything modular and it works extremely well with Backbone.js. 

We use several open source JS libraries, for example, raw query editor is built on top [Ace editor](http://ace.c9.io/#nav=about), queries are generated with the help of [Squel.js](http://hiddentao.github.io/squel/) and [c3.js](http://c3js.org/) is used as an abstraction over D3.js to make charts more reusable. [Underscore.js](http://underscorejs.org/)/[lodash](http://lodash.com/) is also a very useful utility library that introduces ideas from functional programming.

Datazenit is my first startup where I decided to use [Bootstrap](http://getbootstrap.com/) as the CSS framework and this far I have only been happy about it. I personally liked the 2nd version of Bootstrap a bit better than the 3rd (latest), but they both are great and have significantly boosted our productivity. We have customized and themed the default Bootstrap styles and a passerby wouldn't even notice any similarities with Boostrap. 

[![Datazenit screenshotx](http://datazenit.com/static/img/screenshots/screen-1.png?v2)](http://datazenit.com/)

That's currently the end of story. I would also like to share our deployement and integration practices, but that's up for the next time. Meanwhile check out [Datazenit](http://datazenit.com/) and sign up for beta!
