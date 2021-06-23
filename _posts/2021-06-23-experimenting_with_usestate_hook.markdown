---
layout: post
title:      "Experimenting with useState hook"
date:       2021-06-23 15:58:39 +0000
permalink:  experimenting_with_usestate_hook
---


So the hooks were not so clear due to a lack of proper documentation (or so I thought).

I looked at reactjs.org and the API it was helpful (but not as helpful). It is good to have explanations in the API but the API should also have an abbreviated version to it. 

```
import './App.css';
import React, { useState } from 'react';

function App() {

  // Declare a new state variable, which we'll call "count" & initialize it to 0
  let [count, setCount] = useState(0);
  const initialCount = count;
  let finalCount =count +1;
    if (count==0) {// this is needed to ensure setCount is called once only
    setCount(3);// this changes initialCount to 3 & finalCount to 4 in re render
  }
    count = 2; // this does not affect initialCount & finalCount

  return (
    <div>
      <p>Initially count was {initialCount}.</p>
      <p>Final count is: {finalCount}.</p>
      <p>Value of count is {count}.</p>
    </div>
  );
}

export default App;

```
Above is a very simple use of the `useState` hook. 
Notice I did not use `setCount`. The reason is that the moment I do all the variables immediately get updated to the latest value of `count` in the state apparently due to re-rendered values.  Therefore if I do call `setCount` in my code then the values of `initialCount` and `finalCount` are changed to include the latest value of `count` in the state object.

I can change the `count` variable by declaring it as a variable `let` as opposed to `const` & that works fine but calling `setCount` ends up updating all variables `count` is assigned to .

![the output]( https://mrarthurwhite.github.io/use_state_react_hooks_demo/imgs/screenshot1.jpg)
