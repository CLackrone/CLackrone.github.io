---
layout: post
title:      "React/Redux Toy Library: Simply CRUDdy, built with love"
date:       2018-05-02 19:18:07 +0000
permalink:  react_redux_toy_library_simply_cruddy_built_with_love
---


“Can I watch a cartoon?” my 5-year-old will ask. 

“Get your sister and play with your toys,” I’ll suggest. 

“My toys aren’t that fun anymore.”

“Which toys have you played with today?”

“…”

After having this conversation many times with my children, I was inspired. I saw two problems. They think they like screen time more than any other activity and they can be too lazy to look through their own, abundant, collection of toys to figure out what they want to play. 

Why not build them an app that displays all of their available toys, scratch that itch for screen time, and inspire them to play with long forgotten toys and games?

I set out to build a toy library with a React/Redux frontend and a Rails API on the backend. I wanted a simple CRUD application where I could easily keep an up-to-date list of our toys and the kids could navigate easily when they are not inclined to open up the cabinets and actually view their toys.

I began my toy library by building out the backend in Rails with my database, models, and controllers. I seeded the database with pictures of several of my children’s toys and games and included some basic information. 

Once my backend was up and running, returning json objects, etc., I followed [this tutorial](https://www.fullstackreact.com/articles/how-to-get-create-react-app-to-work-with-your-rails-api/) to connect the backend with React. Using the Foreman gem, I was able to set up a proxy that enabled me to run both the Rails and Web pack servers concurrently and easily make my requests to the API.

Once that was done, I was ready to set up React. In order to use Redux to manage your app’s store, React requires quite a few dependencies in order to import many of the linking and routing features you will want to use to build out a robust single-page application. It was worth it, however, because in the end I was able to build an app that is simple to navigate and uses RESTful routing. 

React is comprised of components which are responsible for all the rendering in the DOM. That means your components have to be able to receive all the data from your API or what a user inputs. Because the Redux library aims to manage all of that information in one central store, it is crucial that you understand the flow of data in your application. Remember that because all data is stored centrally, it will be passed down from the top component through any child components that require it. I had a hard time understanding this until I saw it in action. 

![](https://imgur.com/lOI792B.png)

As you can see, the Provider component holds the store and passes it down through several child components in order for the necessary data to be rendered in the ToyForm when editing a toy object. 

Once I had determined the structure of my toy library and understood how data was passed to components, it was time to start using this data to make calls to my API and updating the store. Redux accomplishes these tasks through the use of action creators and reducers. Using fetch requests in my action, I was able to make all of the necessary GET, DELETE, and PUT requests to my backend. I was then able to pass those results to my reducers, which update the store with a new app state. 

It may sound simple, and ultimately it is. But there was still a lot of this along the way. 

“Cannot read property of undefined”

“Uncaught SyntaxError: Unexpected token”

“Uncaught TypeError: Cannot read property 'map' of undefined’”

OR 

![](https://imgur.com/o3TzhaL.png)



While building Toy Library I finally felt like I saw all of my learning come together. I no longer feel like Javascript is a nuisance and I stopped praying for a backend programming job! For the first time, when I hit snags with this project, I found the challenge fun, rather than daunting. Now that the features are built, I look forward to refactoring the code and adding more styling to the components. 
