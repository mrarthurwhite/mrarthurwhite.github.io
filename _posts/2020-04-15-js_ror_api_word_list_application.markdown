---
layout: post
title:      "JS ROR API Word List Application"
date:       2020-04-15 20:08:11 +0000
permalink:  js_ror_api_word_list_application
---


I am always happy to be able to make an app which does not require the "loading" or "downloading" or the rotating circle around the icon in the tab which indicates the application is "loading". 


The interaction is instantaneous and responses so immediate it feels like a desktop application and that is how applications ought to be.

I wrote small apps before when learning jquery and JSON/ Ajax but nothing with this level of complexity (an ROR backend and DB). I feel this application is perhaps worth the months of going through the fundamentals again (which as a professional you rarely get the chance to do: its always find a solution/ recipe/ fix / chip away at the problem, test, and deploy and then go back to square one which is not a very pleasant experience; there ought to be oft made quantum leaps in the solutions we provide).

So the JS ROR application is based on the  notion that student learning the SATs ought to be able to do so more easily with an application. This is a benefit I did not have even though there are a plethora of such flash card apps my approach is intended to be unique (which is not reflected in this rudmentary application) but it is a start.

I begain with scaffolding out the models and the controllers. Then I seeded the data after tweaking the migrations. After the seeding of the data I proceeded to demonstrate to myself that the API on the rails end was working.

Once that was in place I proceeded to begin building the JS client side end. Once that was barely functional and I was getting a list of the seeded words from the DB I implemented post/add word requests. I also immediately proceeded to incorporate materialize because it makes the experience for me as a developer a lot more pleasant (to look at pretty colors). However, materialize would end up hampering development because the peculiar way it works adds a level of complexity which seemed to manifest itself in the form of a bug. This delayed my applying for a review.

As always git gave a bit of concern because it would not integrate properly with my RubyMine and Webstorm IDE. It works with VS Code but I rarely use that IDE except as a way of browsing previous projects. 

I finally got some semblance of a project loaded to git (after the Visual IDE would not cooperate / did not have time to go over video of how Enoch integrated GIT with VS Code). 

Then I had concerns about the drop down select not working. I implemented the 3rd Ajax call (a show/index & add) and a fourth get for categories. I proceeded to then attend office hours to resolve this (and it worked on my 3rd try; 1st office hours with Enoch, then Howard open office hours & then finally Enoch again).  Turns out that what materialize calls "initializing" a select component is really just perhaps finalizing it and it would like to have the select's options preloaded and ready before it "initializes" the select component.

I have to write some lines for the definitions of the verbal portion of the review but that ought to take no longer than 30 mins.

I would like to implement a jquery tabbed version for the display of the words. Maybe a has_many relationship for sentences (and not just categories) followed by has_many for word's function (NOTE TO SELF : parts of speech, don't use *function* since its a JS keyword).

I was fortunate enough to start modularizing the code in an OO fashion from the beginning with JS and required little refactoring. 

I would like to double check the naming conventions with JS & write notes about it so I may ensure consistency.






