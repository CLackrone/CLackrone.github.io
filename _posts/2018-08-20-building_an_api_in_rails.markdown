---
layout: post
title:      "Building an API in Rails"
date:       2018-08-20 15:17:05 +0000
permalink:  building_an_api_in_rails
---


I recently built an app to manage my kids’ playroom and wanted to use an API to handle the database. I decided to use Ruby on Rails because of its ease and simplicity. 

If you are not yet familiar with Rails, it is very easy to get started. Ruby on Rails is a ruby framework makes it easier for developers to build websites and applications because it ‘abstracts and simplifies common repetitive tasks’ ([BitZesty](https://bitzesty.com/2014/03/03/ruby-on-rails-what-it-is-and-why-we-use-it-for-web-applications/)). Rails’ strong suit is the convention that it brings to programming. The programmer spends far less time configuring files because Rails does much of that work for you. 

Rails is a MVC (model-view-controller) framework. To build my API, it was not necessary to build the views. In Rails I simply structured my database and programmed the controller. 

I wrote basic CRUD (create, read, update, delete) actions in the controller and programmed each action to render JSON data for the application to parse. 

```
def index
   toys = Toy.all.order('name ASC')
	 render json: toys
end
```


Once the API was built, all I had to do was run my Rails server and I was able to use JavaScript fetch() to make calls to retrieve the data from my endpoints. 
