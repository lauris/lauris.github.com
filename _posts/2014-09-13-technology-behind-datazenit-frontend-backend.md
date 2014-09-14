---
layout: post
title: "The Technology Behind Datazenit: Part 1"
category: development
permalink: /technology-behind-datazenit-frontend-backend
image: /images/blog/datazenit-on-ipad.png
---

Datazenit is a [web-based database administration tool](http://datazenit.com/). It is a standalone app, that doesn't require installation - just download and run it. You can then access Datazenit via any browser through specific address, e.g., http://localhost:9000/. It is somewhat similar to the model used by phpMyAdmin. Datazenit becomes most useful when deployed on a server, because from there all your team can access it, share connections, queries, datasets and charts. This is something other database tools lack. 

<!-- more -->

## Backend

The backend of Datazenit is built in Scala. I have written about our [decision to choose Scala](http://datazenit.com/blog/2014/05/19/datazenit-scala/) earlier (there is even a [case study by Typesafe](http://lauris.github.io/datazenit/2014/08/28/typesafe-case-study-about-datazenit/)), but the main benefits are that it is a great functional language and it compiles down to Java bytecode which can be run practically anywhere. It allows us to target many different platforms and users will have easier setup.

[![Datazenit screenshot](/images/blog/datazenit-screenshot.png)](http://datazenit.com/)

<p class="caption">Datazenit screenshot</p>

We chose [Play framework](https://www.playframework.com/) as the next layer in our backend, because it is a mature framework, great productivity wise and provides all the necessary ingredients to build a RESTful, modular and safe backend. Another important part of the backend is JDBC abstraction layer, a database access library [ScalikeJDBC](http://scalikejdbc.org/). JDBC is Java-based database connector that supports a wide variety of database management systems, especially relational ones which are our main target for initial release. Working directly with JDBC can be often a tedious task, and this is where ScalikeJDBC helps us. It provides an easy to use and robust API over JDBC.

## Frontend

The frontend of Datazenit is much bigger than the backend and is also a way more complex. It is built on top of [Backbone.js framework](http://backbonejs.org/) that is hands down the best JS framework I have used. I really enjoy its simplicity, the fact that it doesn't try to interfere with you in any way and just provides the bare essentials. It is a solid foundation that doesn't introduce overhead or complexity. We also use Require.js to make everything modular and it works extremely well with Backbone.js. 

Datazenit makes use of several open source JS libraries, for example, raw query editor is built on top [Ace editor](http://ace.c9.io/#nav=about), queries are generated with the help of [Squel.js](http://hiddentao.github.io/squel/) and [c3.js](http://c3js.org/) is used as an abstraction over D3.js to make charts more reusable. [Underscore.js](http://underscorejs.org/)/[lodash](http://lodash.com/) is also a very useful utility library that introduces ideas from functional programming.

Recently we started development of [Sensei Grid](https://github.com/datazenit/sensei-grid), an open source data grid in JS/HTML. The development has just started, but the library is already looking quite promising. The integration between Sensei Grid and Datazenit is much tighter than with a third party solution, and we are also happy to give something back to the open source community.

[![Sensei Grid screenshot](/images/blog/sensei-grid-screenshot.png)](https://github.com/datazenit/sensei-grid)

<p class="caption">Sensei Grid screenshot</p>

Datazenit is my first startup where I decided to use [Bootstrap](http://getbootstrap.com/) as the CSS framework and this far I have only been happy about it. I personally liked the 2nd version of Bootstrap a bit better than the 3rd (latest), but they both are great and have significantly boosted our productivity. We have customized and themed the default Bootstrap styles and a passerby wouldn't even notice any similarities to Boostrap. 

## What's next?

This was the first part of article series about the development of Datazenit. I would also like to share our deployement and integration practices, but that's up for the next time. Meanwhile check out [Datazenit](http://datazenit.com/) and sign up for beta!

[![Datazenit Beta](/images/blog/datazenit-on-ipad-large.png)](http://datazenit.com/)