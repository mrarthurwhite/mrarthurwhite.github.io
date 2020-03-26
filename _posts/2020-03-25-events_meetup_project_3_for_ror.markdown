---
layout: post
title:      "Events Meetup Project 3 for ROR"
date:       2020-03-25 17:36:28 -0400
permalink:  events_meetup_project_3_for_ror
---


I was a little behind in the lessons due to my midterm (I thankfully did well in it but not as good as I wanted to). The genesis of the project was thinking of what app to build. I had been thinking of a personal project but I did not have time (I was already a bit behind).

I was contemplating an app that helped people with their vocabulary. Then I set it aside for exposition of my favorite passages in literature and masterpieces from around the world. That I set aside to focus on users-<reviews>- products app. That I set aside for a users -< review >- posts because I wanted to make an e magazine but learned that the project was discouraged because it was already covered in the lessons and there were vague demands for extra features. 

This was until I thought some more and more and stumbled upon a dating app with users -< dates >-< reviews of dates >- user app. That did not pan out because I felt time was restricted and it would need images. 

So eventually I came up with a users -< parties/events >-< comments >- user.  This simplified to  users -< registrations >- events and I was on to something.

As I began I noticed that the requirement wanted the registration to have a user submittable attribute and the registration could have an RSVP / comment/request fields and it was perfect. I was now informally setting up my to do list and checklist.

I resourced as much of the code as I could. Then in a separate project I separately scaffolded the necessary files and just cut down and modified and removed any unnecessary code from the scaffold. I used a very restricted scaffold and that was only to avoid creating extra files. The very restrictive scaffolding options I used are : 
> --no-helper --no-jbuilder --no-javascripts --no-assets --no-scaffold-stylesheets --no-stylesheets --no-test-framework  --no-resource-route --no-migration

I spoke with Howard & he said it was ok to use scaffolds as long as removed any unnecessary code. My code/project is as lean as can be. Despite this, the beginning was really slow (as is with some applications though we don't expect it from rapid application development frameworks like ROR). I was initially working without authentication and authorization and just getting the workflow straight. User logsin and lands on their profile page and then is able to see their events that they are hosting and the events that they are going to attend. Then from this profile page you could see an index of all the events and from their index of events you could rsvp for any interesting events. 

After adding the rsvp field to the registration (a late addition due to the requirement) I set about authentication and authorization because I was beginning to see that i would need the user information to tailor the content. I was averse to using devise even though a lot of people had raved about it. I used my own code hence. 

Soon as I was working on the app I realized that I had inadvertently realized one of the rested routes (new registration) and it needed a minor tweak. 

After the nested routes and around that time I added a scope method to fulfill the requirement (see spec.md for details). The last thing that remained was the omniauth and I was hesitant about it because I had not exactly a great grasp of it but I was able to implement it in under an hour thanks to the wonderful instruction of my tech leads (thanks Howard & Enoch).

As I was going along I noticed that I had created a custom sign up form and it needed validation. At this point I decided to just chuck it for the scaffolded form_for because it had validations also built in. This was excellent because it really streamlined my code. My last priority was to set up a separate reference table consisting of the Yes/No/Maybe options for the RSVP (to be done maybe at some time in the future). 

I finished the index/show nested routes and moved to add fields_with_errors because it was not showing up despite using form_for and form_with. My laundry, groceries and room hygiene were due by this point. Alas I was almost complete. I cleaned up any extraneous code and started tackling the interface. I noticed that the earlier I could tackle the interface the more enjoyable the experience. So I incorporated the materialize.css very early right after the basic requirements were met.

After changing the links to voluptuous buttons I realized I had forgotten about one requirement the git commits. I hastily emailed my tech lead and he told me to ignore it because people forget it sometimes. I usually use a visual source code management tool and mostly  if it is in a team environment. Nonetheless on the last day I spent 3 hours just creating a new project and slowly adding the files and code and features one by one and adding git commits to the log. Meanwhile I was also doing my laundry (done).

I noticed that Ms. Mckenna suggestion to have music in the background helps with laborious tasks like git commits and recreating an entire project.

After the commits , the spec.md file and now the blog, followed by the video and assessment scheduling.

