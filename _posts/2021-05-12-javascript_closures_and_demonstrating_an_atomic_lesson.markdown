---
layout: post
title:      "Javascript Closures & Demonstrating an atomic lesson"
date:       2021-05-12 13:12:52 -0400
permalink:  javascript_closures_and_demonstrating_an_atomic_lesson
---


So it seems that JS closures are not very properly (atomically & in a utilitarian fashion) explained in our curriculum.

So without further ado the five lines of code are [here](https://github.com/mrarthurwhite/js_closure_demonstration/blob/master/closure_demo.js) :
```

function aName() {
  let name = "Arthur";
  function displayName() {
      console.log(name);
  }
  displayName(); 
}

aNname(); // displays Arthur
```

 

*displayName* is a function. 
The "wonderful" part is that it can access the *name* variable in the parent scope.
This is called a JavaScript closure. It makes it possible for a function to have "private" variables.
The name variable is protected by the scope of the *aName* function, and can only be accessed using the *aName*() function.
You cannot in other words modify the inner variable "*name*".

The concept of closures and private variables does not seem very usual to people coming from an OO background (like me) however this is how JS allows for private variables. In other words the variable is allowed access through an "interface" of sorts & only permits certain functions to be executed upon it.


I had to look for information about closures online and then come up with an example which was "atomic" & utilitarian. Atomic lessons take only one unit of learning & express that as opposed to including multiple units of learning (which the reader may or may not be familiar with) and then inundating the reader with it thereby confusing or discouraging the learner. 

This is a placeholder for the concept of closures, which I am still unsure how or when to use (just figured out the concept). But more later once I figure out why precisely this is useful & when anyone would use it. The above is only a modified example from another online source, I do not take credit for the source code nor lay any claim to its originality.

Some references : 
[[1](http://skilldrick.co.uk/2010/11/a-brief-introduction-to-closures/)]
[[2](https://blog.bitsrc.io/closures-in-javascript-why-do-we-need-them-2097f5317daf)]
[[3](https://medium.com/@dis_is_patrick/practical-uses-for-closures-c65640ae7304)]

