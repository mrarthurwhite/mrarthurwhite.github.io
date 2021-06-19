---
layout: post
title:      "Fetching with React Hooks"
date:       2021-06-19 00:30:32 +0000
permalink:  fetching_with_react_hooks
---


So with class components there were a lot of `connect` method calls & calls to `mapStateToProps` & `mapDispatchToProps` along with the layers of indirection like actions and reducers. 

With hooks, things are a lot clearer and simpler. 

This is the source for a simple project that makes fetch calls via react hooks [[source](https://github.com/mrarthurwhite/fetch_hooks_react_demo)]. This is just the link to the source and some source code but I will elaborate upon the various details soon. This is just a placeholder for elaboration later.

And this is the source code : 

index.js
```
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';
import { createStore } from 'redux'; // this allows us to create store
import { Provider } from 'react-redux'; 
// we pass the store obj to top level container Provider
import rootReducer from './reducers/rootReducer.js';

const store = createStore(rootReducer);

const rootElement =   document.getElementById('root')
// added Provider to wrap around App
ReactDOM.render(
  <Provider store={store}>
      <App />
  </Provider> ,
  rootElement
);

```
App.js
```
import './App.css';
import { useSelector, useDispatch } from 'react-redux';
import {  useEffect, useState } from 'react';

import React from 'react';

function App() {
  const [words, setWords] = useState([]);

  useEffect(() => {
                    let mounted = true;
                    fetch('http://localhost:4000/words')
                    .then(response => response.json())
                    .then (data =>
                                      {
                                        if (mounted){
                                            setWords(data);
                                        }
                                      } 
                                    )
                      return () => mounted = false;
                  }, []
            )


    return (
    <>
    {
      words.map(w=> <div>{w.word}</div>)
    }
    </>
  );
}

export default App;

```

The json I am getting from the api is:

```
[
{
"id": 1,
"word": "abase",
"definition": "Lower ; humiliate.",
"sentence": "Defeated, Queen Zenobia was forced to abase herself before the conquering Romans, who made her march in chains before the emperor in the procession celebrating his triumph.",
"category_id": 1,
"category": {
"name": "3,500 Basic"
}
},
{
"id": 2,
"word": "abash",
"definition": "embarrass.",
"sentence": "He was not at all abashed by her open admiration.",
"category_id": 1,
"category": {
"name": "3,500 Basic"
}
},
{
"id": 3,
"word": "abate",
"definition": "subside; decrease, lessen.",
"sentence": "Rather than leaving immediately, they waited for the storm to abate.",
"category_id": 2,
"category": {
"name": "Hot Prospect"
}
},
{
"id": 4,
"word": "abridge",
"definition": "condense or shorten.",
"sentence": "Because the publishers felt the public wanted a shorter version of War and Peace, they proceeded to abridge the novel.",
"category_id": 3,
"category": {
"name": "High Frequency"
}
}
]
```


