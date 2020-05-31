---
layout: post
title:      "React Redux Word List Application Final Project"
date:       2020-05-31 23:03:02 +0000
permalink:  react_redux_word_list_application_final_project
---


So I finally completed the requirements for the final application using Reac-Redux with a rails API backend.

Assimilating information about Redux (with react) can be a little perplexing particularly if you are also trying to ace classes in other competitive programs at another university.

Either way, I kept thinking thoughout - why is getting a global store's state variable and updating it so difficult and why does it require so much wiring and indirection? I should have asked my cohort leads this question but I did not get around to it.

The final project was a rather hasty attempt at finishing it up and having until June 1st was a boon. 

Until this morning I was not sure I would be able to meet the deadline of June 1st (this morning being May 31 2020). 
It was only until a few minutes ago that I had some breakthroughs. 

One of the biggest hurdles that slowed my progress was this : I was trying to make an API call to the rails backend for every /words/:id (show) restful route. This was resulting in a bug in the code where click on a word on the word list only displayed the detail view for one word and that is it.

This caused some consternation and soul searching as I frantically reviewed the lessons and thank goodness for the recorded lessons of the teaching fellows because relying solely on the lessons I would not have been able to put this application together. 

The lessons are great but there are still a few things missing. Going over the various permutations of the application and how to create it helps immensely. 

The stakes were really high because I got absolutely zero help from the cohort leads, and I could not even contact them at this late stage with questions since they had already departed. (not that I had to at any point in the past but it was reassuring to know).

My speed of development was of the greatest concern to me. Although I usually finish my projects within a day or two getting to that stage requires longer and my progress through the course itself was not as consistently rapid, perhaps.

Anyways, this afternoon's breakthrough was how suddenly in the very first try adding words worked. Usually it was taking a while to get minor things up and running due to the massive amount of indirection (with actions and reducers etc. just to update state). Again, it would be much easier to just provide a dictionary object or hash object or JS object which we can set and get state on which is available if imported.  Is that so not easy React developers?

What I loved about the framework was how OO it is. What a relief to finally have a framework with so much front end OO capability. 



