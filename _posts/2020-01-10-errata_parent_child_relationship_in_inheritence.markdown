---
layout: post
title:      "Errata: Parent , Child Relationship in Inheritance"
date:       2020-01-10 09:45:51 -0500
permalink:  errata_parent_child_relationship_in_inheritence
---


There is a [youtube video](https://youtu.be/iYcQ693LXck) that goes over some inheritence ideas.

At the mark 48:20 of the video above the legendary pedagogue and engineer extraordinaire says :
> "Whatever is the first object is always considered the parent. An Author is the parent of a story in that an author has many ; we tend to think of the singular as being the parent so authors have many stories. But in here given that story is the main object"
 
There is some confusion with regards to inheritence perhaps.
A parent is simply a super class and a child is merely a subclass.

A child IS-A progeny of a parent, just like a Car class IS-A Transport (here Transport is a parent/superclass and Car is a child/subclass).

Inheritence can be single(Java, Ruby etc.) or multiple (C++) meaning a child/subclass can have only one or many parents/superclasses.

The other idea has to do with *aggregation*.

Aggregation or composition is a HAS-A relationship where a class Car HAS-A Seating_Capacity (here an attribute) or a Car class HAS-A Dashboard (another class or entity with gauges, fuel indicators, radio panel, A/C knobs, GPS display etc.) and a class Car also HAS-A set of four wheels (or if class is Bike then it has a pair of wheels).

The 1:1 and 1:N (one-to-one or one-to-many) relationship applies to aggregated components of a class. In other words an Artist can have many Songs. Artist & Song class do NOT have a parent child relationship they just have a 1:N (one-to-many) relationship or an compositional reltionship (where an object of class Artist is *composed* of many Song class objects). In other words many Song objects may aggregate to form part of an Artist object - where an Artist object HAS-A collection of songs (0 or more). 

Now if you want an inheritence relationship or parent / child relationship then you can say that a class Actor, class Singer, class Director are all children/subclasses of the super class or parent class Artist. Here a parent may have many children and hence an Artist super class may have multiple sub classes (like Actor, Singer, Director etc.) Here 1:N or one-to-many relationship is implied but we don't really think of it that way because the parent/superclass does not have an array or collection of children/subclasses. On the other hand in a compositional relationship or in aggregation several classes aggregate to compose another class (where the notion of inheritence and polymorphism does not apply). 





