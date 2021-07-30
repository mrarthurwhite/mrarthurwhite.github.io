---
layout: post
title:      "Cleaner Fetching W/ Hooks , Await, Sync & Axios"
date:       2021-06-28 08:52:57 -0400
permalink:  cleaner_fetching_w_hooks_await_sync_and_axios
---


So previously we were able to do a very simple `fetch` with hooks as follows:

*App.js.* [src](https://github.com/mrarthurwhite/fetch_hooks_react_demo)
```

import './App.css';
import {  useEffect, useState } from 'react';

import React from 'react';

function App() {
  const [words, setWords] = useState([]);

  let fetchData = () => {
                          fetch('http://localhost:4000/words')
                          .then(response => response.json())
                          .then (data =>
                                            {
                                                  setWords(data);
                                            } 
                                          )
                        };

  useEffect(fetchData, [] );


    return (
    <>
    {
      words.map(w=> <div>{w.word}</div>)
    }
    </>
  );
}

export default App;
/**
 *
 * In functional components, you use the useEffect Hook to fetch data when the component loads or some information changes.  You’ll also need to save the results with the useState Hook.   
 */
```

So the above seems rather useful & concise but I would like to start using[ asynch & wait](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function) to avoid explicity chaining promises or to "explicitly configure promise chains" like so : 

`fetch (url).then (response=>response.json()).then(data=> work_with_data);`

Following is code with async & await [[src](https://github.com/mrarthurwhite/use_effect_react_hooks_demo/blob/master/use_effect_initial_demo/src/App.js)]: 

```
import './App.css';
import {  useEffect, useState } from 'react';

import React from 'react';

function App() {
  const [words, setWords] = useState([]);

  async function fetchData(){
    const response= await fetch('http://localhost:1111/wordlist');
    const result = await (response.json());
    setWords(result.data);
  };

  useEffect(() => {fetchData()}, [] );


    return (
    <>
    {
      words.map(w=> <div>{w.word}</div>)
    }
    </>
  );
}

export default App;
/**
 *
 * In functional components, you use the useEffect Hook to fetch data when the component loads or some information changes.  You’ll also need to save the results with the useState Hook.   
 */
```

So the above works. Let us see if we can incorporate Axios. Axios is an http client which makes fetching cleaner, it works both in the browser and with node.js & it automatically transforms json data (no need for `response.json()` followed by a promise chain obtaining the aforementioned json).

1. In your client directory install axios (in our case `use_effect_react_hooks_demo` directory  ):

`npm install axios`

2. note that axios has a response [template](https://axios-http.com/docs/res_schema):

```

axios.get("/user/12345")
  .then(function (response) {
    console.log(response.data);  // data is the response that was provided by the server
    console.log(response.status); // status is the HTTP status code from the server response

  });
	
```

Now for the actual source code : 
```
import './App.css';
import React, {  useEffect, useState } from 'react';
import axios from 'axios';

function GetWordsWAxiosNLoading() {
  const [words, setWords] = useState([]);
  const [isLoading, setIsLoading] = useState(true);
  async function fetchData() {
      const url = 'http://localhost:1111/wordlist';
      const result = await axios(url);
      setWords(result.data);
      setIsLoading(false);
  }
  useEffect(fetchData, []);
  return (
  <>
  {isLoading ? (
    <div>Loading . . . </div>
  ) : (
    words.map((w) => <div>{w.word}</div>)
  )}
   </>
  );
}

export default GetWordsWAxiosNLoading;

```

