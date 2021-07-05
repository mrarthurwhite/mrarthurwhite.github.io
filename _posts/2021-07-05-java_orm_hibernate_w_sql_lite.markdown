---
layout: post
title:      "Java ORM Hibernate W/ SQL Lite"
date:       2021-07-05 04:16:28 +0000
permalink:  java_orm_hibernate_w_sql_lite
---


If you have read my previous entries I tried to get java to interact with an in memory database previously & was able to somehow make it work here [blog [link](https://mrarthurwhite.github.io/getting_db_persistence_up_with_javas_orm_hibernate)]

I am unsure how much work it was because even the basic tasks require a bit more effort than is reasonable when it comes to Java & linux & anything that does not involve getting toyed with by Microsoft.

So I was happy that the in memory databases being used were titled something benign like `H2` (for hydrogen) and `hsql` (for hypersonic sql) since hydrogen and hypersonic go with java related IDEs like JetBrains Intellij (see there is a pattern of words indicating speed; atleast they are not using epithet or pejoratives or obscenities or graphically violent language, #grateful). 

However, getting anything done in Java has little to do with speed or ease. Any feedback about the developer unfriendly nature of Java & Linux or any other non-MS environment yields unkind comments like "well you get what you pay for" etc. As far as free quality products these people have never heard of ROR. 

So to the point of the post : why after having hibernate work with H2 did I try sql lite ? Well for one thing in order to view the data in H2 you need to run an h2 server with a dedicated port etc. It reminded me of `MySql` & `Tomcat` (the webserver) which often asks to install itself at a port and then suddenly stops working one day or slows the development machine down to an unappreciating level.

Sql Lite in comparison to h2 or oracle RDBMS or DB2 is refreshing. Its like a text file that bundles with your application & you can view it with its text viewer (without the viewer requiring installation of services hogging ports etc. & more configuration). It is seemless & minimizes developer interaction with the DB & allows a developer to focus on the business logic. 

However it took me days of hazy confusion to get a basic demo application with Java's ORM Hibernate to work with Sql Lite. It could have been longer but the trauma has perhaps compromised my memory.

Either I have it working here [[src](https://github.com/mrarthurwhite/SqlLiteWJavaORMDemo)]. The saga of my odyssey nay suffering is long but I will not elaborate upon it further. Instead I shall sleep upon this & tomorrow I shall write a post that may help others. 
