---
layout: post
title:      "Family Calendar: A Rails app with a jQuery Frontend"
date:       2018-02-02 18:41:33 +0000
permalink:  family_calendar_a_rails_app_with_a_jquery_frontend
---


For my fourth portfolio project I added a jQuery frontend to my existing Rails app - Family Calendar. I chose to add all new frontend features using my Event model since that is the focus of every good calendar. I thought that it would be nice to enhance the app by making it simpler for users to interact with events. 

I’d like to share with you the requirements for this project and the features I implemented for each: 

* Include an index page resource rendered using jQuery and an Active Model Serialization JSON backend
   * I chose to render Events in the index view using AJAX and formatting the content to insert into the DOM
* Include a show resource rendered using jQuery and an Active Model Serialization JSON backend
   * For this I decided to enable to user to view some details about a specific event on the index page so that they can get the information they need quickly without having to visit the event show view and return to the index view to see additional events.
   * As you can see, the code for this uses jQuery to make a GET request to the Rails API and formats the JSON data such that it will render as HTML in the index view without a page refresh:

```
$('#eventInfo').on('click', '.js-more', function(e) {
    e.preventDefault();
    var id = this.dataset.id;
    $.get('/events/' + id + '.json', function(data) {
      var eventDetails = "<div id='details-" + id + "'>"
      + "<a href='/events/" + id + "'>" + data.name + "</a>"
      + "<p>Time: " + data.time + "</p>" 
      + "<p>Location: " + data.location + "</p></div>";
      $('#event-' + id).html(eventDetails);
    })
  })

```



* Include at least one has_many relationship in information rendered via JSON and appended to the DOM
   * To implement this feature, I chose to add a new Comment model to my Rails app. Comments are a simple way for the user to add notes to a specific event. An Event has_many Comments and Comments belong_to an Event. Comments can be rendered in the Event show view via Active Model Serialization and a JSON backend.
* Use your Rails API and a form to create a resource and render the response without a page refresh.
   * In the Event show view, a new Comment form allows the user to create a new comment and render it immediately without a page refresh. 
* Translate JSON responses into JavaScript model objects. && At least one of the JavaScript model objects must have at least one method added by your code to the prototype.
   * I decided to take the response from the new Comment form and create new Comment objects with it. This enables me to capture the data and easily operate on it using a method on the Comment prototype. I wrote a method (shown below) called formatContent() on the prototype that formats the JSON response as HTML that can be inserted into the DOM.

```
Comment.prototype.formatContent = function() {
  var html = "";
  html += "<li>" + this.content + "</li>";
  $(".comments_container").append(html)
}
```


This project taught me a lot about using Javascript in conjunction with Rails to produce a better user experience. By using jQuery to operate on events produced on the backend, I was able to do much more with the data being requested and use it in much more robust ways. 

I am pleased with the new features I added to this project. In the future, I would like to implement more styling using bootstrap and possibly add options for uploading images and more interaction between users. As I wrap up this project I am looking forward to moving into the next phase of the curriculum and preparing to graduate!


