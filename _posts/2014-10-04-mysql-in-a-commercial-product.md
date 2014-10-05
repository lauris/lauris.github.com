---
layout: post
title: "MySQL in a commercial product"
category: development
permalink: "/development/mysql-in-commercial-product"
related: ["Work and open source", "Datazenit Store and Pricing", "The Technology Behind Datazenit: Part 1", "My biggest challenges as a startup founder", "Moving away from the cloud"]
---

I am building a [software for database administration](https://datazenit.com), and it's important to be aware of database connector/driver licensing issues. For the initial releases I am aiming for MySQL and PostgreSQL support, later on SQL Server, Oracle Database and SQLite. I am using JDBC to connect to those database, because JDBC provides a stable API to access many relational databases. PostgreSQL is the most liberal of the mentioned databases, because PostgresQL connector for JDBC is licensed under BSD license that means I can do whatever I want. SQLite has several connectors and most of them are under BSD license too, however I haven't done a full research about SQLite just yet. Also Oracle and SQL Server provide free JDBC drivers that you can distribute with your software. There are some limitations and you should read their licenses carefully, but as far I as I know the drivers of Oracle and SQL Server can be used in a commercial software if you do not change the source code of the connector.

Guess what - MySQL is the biggest let down. Official drivers for MySQL are licensed under GPL license. If I want to distribute my application with official MySQL drivers, I must license my code under GPLv3 or a compatible license. You can also purchase a partner license that offers a MySQL driver under a different license. However there are several workarounds for this. I have seen other database tools using an interesting approach to this - they do not ship with the drivers, but present you with an option to download the drivers within the software. Basically you just press a button, the driver is downloaded from MySQL website and you are good to go. This way they avoid distributing the driver, but user can still use the software, because the drivers gets downloaded on the first run. 

Driver downloading on the first run didn't seem like the best solution for our customers, so I looked for other MySQL drivers that would be licensed more liberally. If you remember a somewhat recent fiasco about MySQL getting bought by Oracle, then you will also know about MySQL forks like MariaDB, Drizzle and others. Luckily both Drizzle and MariaDB offer JDBC connectors that are mostly compatible with the official one and are licensed under more permissive licenses: [DrizzleJDBC](https://github.com/krummas/DrizzleJDBC) and [MariaDB Java Client](https://launchpad.net/mariadb-java-client).

I still have to test them for edge cases and compability, but overall the situation looks promising. 

