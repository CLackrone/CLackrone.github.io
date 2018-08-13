---
layout: post
title:      "Promises, Promises"
date:       2018-08-13 15:39:56 +0000
permalink:  promises_promises
---


Javascript Promise is pretty cool. When making asynchronous calls in JS, a Promise replaces the need to set up success or failure callbacks. It is a part of ECMS 6, so it is a relatively new feature in JS. 

How It Works

A Promise can have three states: 

* Pending: This is the essence of a promise. We’ve been told what will happen, but it has not happened yet.
* Fulfilled: Upon the success of our call, presumably what gets returned is what we desired, and we are able to do with it what we wish.
* Rejected: If our call was unsuccessful, there is a reason which is returned 

One interesting note I recently read was that once a Promise transitions out of its initial pending state, the state cannot be changed. A fulfillment cannot be rejected, and a rejection cannot be turned into a fulfillment. 

What It Looks Like

When I built Toy Library I used a Rails backend for the API and JavaScript/React for the frontend. Using fetch() to make calls to the API, I used promises to handle the JSON being returned. Here is one simple example of what a Promise looks like in action:


```
export const updateToyLikes = toy => {
	  const likedToy = {...toy, likes: toy.likes + 1}


	  return dispatch => {
	    return fetch(url + `/${toy.id}`, {
	      method: 'PUT',
	      headers: {
	        'Accept': 'application/json',
	        'Content-Type': 'application/json'
	      },
	      body: JSON.stringify(likedToy)
	    })
	    .then(res => res.json())
	    .then(toy => {
	      dispatch(editToy(toy))
	    })
	    .catch(error => console.log(error))
	  }
	}
```


I made the call using fetch(), and then attached a .then() function to handle the success of the call and a .catch() for error handling. 

One feature of this method that I enjoyed was that you can chain multiple Promises together to handle the manipulation of your JSON, passing the resolved data down the chain:

```
 .then(res => res.json())
 .then(toy => {
	   dispatch(editToy(toy))
	})
```

This makes for clean, readable code. 

If you want to learn more about Promises, you can visit the [MDN docs,](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) and [check out how to use the new async/await syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function). Happy Promise-ing!
