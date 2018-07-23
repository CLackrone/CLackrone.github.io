---
layout: post
title:      "Rails, ActiveModel::Serializer, and Clean JSON"
date:       2018-07-23 15:46:48 +0000
permalink:  rails_activemodel_serializer_and_clean_json
---


JSON - what is it and how do you manage it? JSON stands for JavaScript Object Notation and it is commonly used to exchange data between the server and the browser. JSON is a human-readable text format that is also easily parsed by machines, making it ideal for use with APIs. 

So how do you deliver data as JSON? Ruby on Rails has a built-in method that allows you to render model data as JSON. It is as simple as including one line in your controller methods: 

```
def show
    render json: model
end
```

While this is quick and straightforward, it has a few drawbacks. 

- The render method, by default, creates a JSON response that includes all model attributes. 
- If your model is complex, serving up the entire list of attributes can needlessly bog down the server by transferring data that isn’t going to be used in the browser. 
- Let’s say, for example, that you are serving up user attributes - you may end up sending sensitive information (such as a user’s password) across the server when not necessary. 

The render method in Rails does include a few options you can use to customize the JSON response, including `include`, `only`, and `except`. However, to quote, well, pretty much everything I have read about this, customizing the render method even a little bit using these methods can ‘get really ugly really quick.’ 

But this is 2018. Surely there is a better way?

Enter ActiveModel::Serializer!

AMS, for short, provides an easy way to create highly customized JSON responses in Rails. Here’s how it works. If you have a model, you can generate a serializer. 

Start by adding the gem to your gemfile: 

`gem ‘active_model_serializers’`

Run `bundle install` and you’re ready to go. 

Now you’ll need to generate serializers for each model you need to customize. You can do this easily from your console: 

`rails g serializer model `

You’ll find your file at app/serializers/model_serializer.rb. 

The generated code will look like this: 

```
class ModelSerializer < ActiveModel::Serializer
	attributes :id
end
```

We can customize this easily by adding in any additional attributes we need for our response. From there, the built-in Rails render method will implicitly render JSON using the AMS we just generated. 

As you can see, using AMS is an easy way to keep the code in your controller clean and tailor your JSON response to keep it simple and readable.
