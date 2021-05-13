---
layout: post
title:      "Demonstrating A Call Back Function"
date:       2021-05-13 17:26:19 +0000
permalink:  demonstrating_a_call_back_function
---



When we pass a function expression (an anonymous function) or the pointer (variable name, declared function name) to a function as an argument, the passed function is called a callback. Since the receiving function will execute, or call that function at a later time; that is, it will call it back, it is called a callback.

So here is a more focused [example](https://github.com/mrarthurwhite/js_callback_explained/blob/master/a_callback_function.js):


```
function myDisplayer(number) {
    console.log("Displaying number : "+ number);
  }
  
  function myCalculator(number, myCallback) {
    myCallback(number);
  }
  
  myCalculator(100, myDisplayer); // displays the number 100
```

Using a callback, you could call the calculator function (myCalculator) with a callback, and let the calculator function run the callback after the calculation is finished. In the example above, *myDisplayer* is the name of a function.
It is passed to* myCalculator()* as an argument. When you pass a function as an argument, remember not to use parenthesis.


The reason why I posted this is  : I am a little unsure of call back functions because I don't use them that often (even though they seem very useful). The explanation in our curriculum is again not atomic (so I am removing extraneous details). The source code above is aimed at demonstrating just a call back function in a focused way without any flourishes.



