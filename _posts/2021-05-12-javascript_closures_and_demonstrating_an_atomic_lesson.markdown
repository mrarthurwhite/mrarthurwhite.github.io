---
layout: post
title:      "Javascript Closures & Demonstrating an atomic lesson"
date:       2021-05-12 17:12:52 +0000
permalink:  javascript_closures_and_demonstrating_an_atomic_lesson
---


So it seems that JS closures are not very properly explained in our syllabus.

So without further ado the five lines of code are [here](http://https://github.com/mrarthurwhite/js_closure_demonstration/blob/main/closure_demo.js) :
```
function add() {
    let counter = 0;
    function plus() 
		{counter += 1; return counter}
    return plus
  }

let doaddition= add(); // add is invoked which returns reference to function plus
doaddition(); // doaddition is now a reference to plus 
// hence doaddition()=plus()
doaddition(); // doaddition() is essentially invoking plus()
// the counter is now 2
```
 

The variable doaddition is assigned the return value of the  add function which is plus .
The  add function only runs once. It sets the counter to zero (0), and returns a function  plus .
This way doaddition becomes a function. The "wonderful" part is that it can access the counter in the parent scope.
This is called a JavaScript closure. It makes it possible for a function to have "private" variables.
The counter is protected by the scope of the add function, and can only be changed using the doaddition function.


I had to look for information about closures online and then come up with an example which was "atomic". Atomic lessons take only one unit of learning & express that as opposed to including multiple units of learning (which the reader may or may not be familiar with) and then inundating the reader with it thereby confusing or discouraging the learner. 


