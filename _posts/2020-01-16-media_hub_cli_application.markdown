---
layout: post
title:      "Media Hub CLI Application"
date:       2020-01-16 23:30:02 -0500
permalink:  media_hub_cli_application
---


The least easy part of the application was to decide on whether to scrape vs. consuming an API. 

When it came to scraping data wikipedia was the top choice however the data I was interested in did not have clear identifying tags and I did not want to wrestle too much with merely extracting data.

The next logical step was to choose an API that provided formatted data. So I looked at the available APIs. Nearly all the interesting APIs had authorization keys and hiding the key looked rather involved (since the app was to be published online on github).

I finally came across TV Maze which had an extensive list of shows and a not so extensive cast/actors information. TV Maze is not as detailed or extensive as IMDB but it served my purposes. Somehow , I felt that I ought to write an application promoting a show I am watching currently on Netflix. I discovered this show recently and it was filmed in the 90s. 

*A quick review:* the show is boring and the writer(s) is/are unfamiliar with government and basic ideas (like the difference between authoritarianism and fascism and I am saying this when I never even took a single government class, unfortunately, if only the Most High God would have mercy upon me). If you dislike D.C. and if you want to run in the opposite direction of politics then watch the West Wing. It is filled with "pragmatic" moments where politicians wheel and deal , threaten & cajole legislators & judges and attorneys & a variety of professionals just to get some basic amendment or bill or political stance serviced.  I laugh helplessly at the absurdity & the pitiful nature of it. 

I watch it nonetheless because it is boring and better than some of the scary, not so wholesome, impious entertainment on network TV (better than the Witcher with its gratuitous sexuality & violence & acting, & yet redeemable due to Geralt's high morality). It also forecasts how the extreme left will begin to think & talk about politics particularly ANTIFA (who also don't get what fascism means while accusing everyone else of it) So the show seems to be a brain scan of ANTIFA and Brits who incidentally are also clueless about politics (primarily because of their fair government). It seems it is a show that is oft recommended by people hailing from S. Europe (& sympathizers) a people who are intimately aware of human nature & use the show to mislead the rest of us who are innocent of the dark side of human nature. I also watch the West Wing because of Ms. Malone (the slim, tall blonde lady) and Mr. Rob Lowe (the good looking talented actor) & the amazing performance by Mr. Martin Sheen and the other cast members like Bradley Whitford. Watching the show you realize why Martin Sheen is a super star and why he is blessed with two equally talented children (Charlie and Emilio).

Returning to the technical aspects of the application (*sigh*). Once I looked at the API by TV Maze I became increasingly confident that this was the API I wished to build an application around. It is user friendly, extensive, clean. 

The first concern was how muddled the hashes looked. I had to install pretty print or awesome print (Thanks Howard Devenish, my talented tech coach who can foretell what difficulties we may encounter). Once I had awesome print installed I could see more clearly what the hash was offering. I began with the API class which interacted with the exposed endpoints. 

Once the endpoints were working, I created the classes that were going to take input from the hashes. Again, Howard's advice about using a white list of variables instead of loading all the hash variables somehow made me feel warm and secure inside (darn you Howard!).

I quickly sketched the class hierarchy and the parent class relationship . At this point I had a foggy thought and had some terrible OO design thoughts. The thoughts were motivated by my desire to reuse code and I even fumed about my idea on reddit denouncing Ruby & Java's inability to handle multiple inheritence. Thank God for the sane people of the world who brought some sense into my head. Finally when I was working out in the gym I had a clear thought and realized that my OO design angle was incorrect and I had needlessly argued with people on the internet. Oh God! why the embarassment ? I apologized to the internet & everyone and felt unhappy with my misguided and irrational frame of mind (something I attributed to annoying people from developing countries). 

Alas, I realized that irrationality and misguidance is a result of insecurities, anxieties and stress and lack of courage and lack of sleep (somethings I was suffering from when I posted everywhere demanding why Java/ Ruby did not support multiple inheritance; I still feel multiple inheritance is better but I am ashamed of the example I picked to prove my point & the subsequent low opinion of people who disagreed with me. I believe this is due to decades of encountering contrarians who contradict whatever I have to say, which has in turn turned me into a contrarian myself where I feel uneasy if I am not met with resistance and I therefore end up picking the opposite side or finding flaw with another's argument. What a pitiful state and how unhappy an existence to live in an unfriendly microcosm of the world with a lessened sense of security, lessened  good will, empathy or understanding and to be twisted by that antagonism into a contrarian). Oh what loss of innocence and lessened righteousness. I now feel concern interacting with some peoples lest I lessen my own rectitude.

I encountered some unease when configuring my application and I got some help from the tech coaches in configuring it with gemfile, environment file and a working console. Thank you. That was helpful. 

After I had the objects  & API in place I moved to the CLI application which I finished in a day. The entire thing took me 2-2.5 days. I would make it 3-3.5 days the extra day spent on agonizing over what application to write given the time frame constraints. My decision was helped with the following line from the check list : *"●	You are not building the next twitter cli. You are creating a project to show your understanding. Do not make your project super complicated."*

Thank you to whoever wrote that.
