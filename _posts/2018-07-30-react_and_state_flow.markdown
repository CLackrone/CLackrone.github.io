---
layout: post
title:      "React and state flow"
date:       2018-07-30 17:07:27 +0000
permalink:  react_and_state_flow
---


React is tough. Having built a few apps using it, I enjoy it. But it can be tricky to get a feel for how it all fits together. 

React is a library that allows you to compose complex user interface from smaller components. This makes React convenient for its reusability and customization. However, once you start passing around actual data, it becomes a real juggling act. 

If you are new to React, I’d like to go over a library for managing the state of your app called Redux. Redux essentially takes all of your data and stores it in one place, passing it around as needed. However, it is critical that you understand the flow of data when using Redux in order to ensure your data is going where you need it to go. 

To get started using [Redux](http://redux.js.org), let’s go over some of the vocabulary you’ll need to understand. 

Store: holds the state of the application
Dispatcher: store method for dispatching actions
Action: payloads of data sent from application to store
Action creator: functions that create actions
Reducer: specify how the application state changes in response to an action

Using Redux, the basic flow is as follows:

- The store passes state to React components. 
- React components can manipulate data 
- Data from components is passed via the dispatch method into an action creator
- Action creators do the heavy lifting (think API calls, persistence)
- Action creators send newly fetched/persisted data as action payload to a reducer
- Reducers take the new data and combine them with the current store and replace the current store with the newly updated store

Okay, okay, I understand that may not make a lot of sense if you have never used it. Once you put it into action, you will start to see how the flow works. 

One method I learned that helped me understand state flow using Redux was to insert a trail of console.logs into my code and then try to predict the order in which they would log before I triggered an update to state. 

As you dive into React/Redux, I hope this helps you wrap your head around all the moving parts that make up this fascinating pattern.
