---
layout: post
title:      "Hello World App for React/Redux"
date:       2021-06-12 20:16:58 +0000
permalink:  hello_world_app_for_react_redux
---


So I was thoroughly confused with basics of React-Redux but managed to get the final project working somehow & even somehow had some semblance of clarity during the review (code review). But now that all the immediacy is in the past & redux and react etc. are less relevant things are not so clear. Thanksfully I was able to run into some sources which helped me create a very rudimentary hello world React-Redux app to allow me to grasp the essentials again (and hopefully may help others too).

So following is the most basic react-redux application source code. A detailed step by step setup is in the pdf file in the github repo "[React Redux Notes.pdf](https://github.com/mrarthurwhite/react_redux_demo/blob/master/React%20Redux%20Notes.pdf)" . [[src](https://github.com/mrarthurwhite/react_redux_demo)]

```
import React from "react";
import ReactDOM from "react-dom";
import "./styles.css";

import { Provider, useSelector, useDispatch } from 'react-redux'

import { createStore } from 'redux'

const rootReducer = (state = { count: 0 }, action) => {
  switch(action.type) {
    case 'COUNT_UP': 
      return { ...state, count: state.count + 1 }
    default:
      return state
  }
}

const store = createStore(rootReducer)

function Counter () {
  const count = useSelector(state => state.count)
  const dispatch = useDispatch()

  const countUp = { type: 'COUNT_UP' }

  return <div>
    <p>Count: {count}</p>
    <button onClick={() => dispatch(countUp)}>Count Up</button>
  </div>
}

function App() {
  return (
    <Provider store={store}>
      <div className="App">
        <h1>Redux</h1>
        <Counter />
      </div>
    </Provider>
  );
}

const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);


```

