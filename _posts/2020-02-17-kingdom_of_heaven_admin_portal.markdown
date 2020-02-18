---
layout: post
title:      "Kingdom of Heaven Admin Portal"
date:       2020-02-17 20:44:44 -0500
permalink:  kingdom_of_heaven_admin_portal
---

This application was done hastily and is a proof of concept. It illustrates an administration portal in the Kingdom of Heaven where angels and archangels are on missions to spread love, joy, peace , goodness throughout the world. I wrote this app because the Kingdom of Heaven has lately been on my mind.

The app is a materialize CSS beautified MVC app using Sinatra with restful routes.

It allows angels on missions to add/update/delete missions that are their own.

It also allows the angels to see what the other angels are doing.

It has some basic validation and validation messaging (not extensive).

I did encounter some issues when I first started the application. One of the concerns was that the inherited controllers and ApplicationControllers were for some reason not being recognized. 

I asked the tech coaches for some guidance only to be informed that I would have to approach my cohort leads for assistance.

I ended up creating a new directory and starting a new project and carefully started adding the elements and this time it worked as I incrementally added the various components.


Another concern during development was that I had not used git extensively. This is because I am used to visual source control tools that are local as oppposed to writing git commands on the command line. I did end up making some 7 /8 git updates to demonstrate that I knew the commands and was able to use them to manage my source code.

One other minor source of concern was validation code. The requirements asked for validation and to display error messages as a bonus. I was fortunate to run into some hints in the documentation that illustrated how to use error messages from the model layer in the view layer. 

This particular feature can be viewed in the sign up page but validation is not universally implemented in my application. 

Overall it did not take very long to do the application since it was based on work I had already done.

The most rewarding aspect was perhaps the use of materialize CSS. Using the proper colors and buttons enriches not just the user experience but also the developer experience.


