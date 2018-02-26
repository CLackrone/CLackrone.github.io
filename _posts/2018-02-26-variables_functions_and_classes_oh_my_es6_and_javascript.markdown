---
layout: post
title:      "Variables, Functions, and Classes... Oh My: ES6 and Javascript"
date:       2018-02-26 17:06:32 +0000
permalink:  variables_functions_and_classes_oh_my_es6_and_javascript
---



ES6 brought many big updates to Javascript. Learning Javascript in a post-ES6 world has been much easier for me than my introduction to the language, which did not include this edition. I’d like to go over a few of the new features you can now enjoy when coding in Javascript. 

The introduction of new variable declarations, const and let, have, in essence, replaced the old standard, var in order to bring greater clarity and logic to Javascript code. In the old days, you had var and only var. var is a well-loved, yet somewhat flawed variable declaration. 

First, var is scoped to its execution context - either its enclosing function or the global context.  This seems to be unnecessary, as many variables to not need to be accessed outside of the block in which they were declared. By contrast, let and const are both block-scoped, making them more appropriate for most use cases. 

Second, var does not give an error if it is redeclared within the same scope. I can see how this could create a lot of confusion as it would make it difficult to predict the value of a given variable at the point where it is called. ES6 answers this problem in two ways: let gives an error if it is declared twice and since the value of const is constant, it cannot be redeclared. 

```
var foo = 'bar'
//undefined

var foo = 'bam'
//undefined

foo
//"bam"

let abc = 'def'
//undefined

let abc = 'ghi'
//Uncaught SyntaxError: Identifier 'abc' has already been declared
```

So when should you use var, let, and const? Much of the reading I have done indicates that you should avoid using var anymore as either let or const is almost always a better choice. let is useful for declaring variables in cases such as looping and iteration, as the value will continue to change as the code is executed. const should be your default declaration. The best advice I have read is that you should always begin with const and change your declaration to let down the road if you find that the value of your variable will need to change. 

Another feature introduced in ES6 is the arrow function. Arrow functions are a simplified syntax for writing functions. They are declared using the new token, =>, like this: 

```
const anArrowFunction = () => {
  return 'This is amazing!'
}
//undefined

anArrowFunction()
//"This is amazing!"
```

Better yet, when a function contains only one expression, it can be declared without curly brackets and provides an implicit return. 

```
const anArrowFunction = () => ('This is even more amazing!')
//undefined

anArrowFunction()
//'This is even more amazing!'

const myMultiplierFunc = (a, b) => (a*b)
//undefined

myMultiplierFunc(2, 3)

//6
```

Arrow functions are convenient for callbacks because they are always anonymous and they save developers quite a few keystrokes!

Finally, I would like to touch on the ES6 introduction of classes for Javascript. Javascript classes are unlike classes from other class-based programming languages in that they do not actually create Javascript objects. They are simply “syntactical sugar” over the existing prototype-style object creation Javascript already uses. One great feature of Javascript classes is that you can add a constructor function, which instantiates a new instance of an object for you. 

```
class Car {
    
    constructor (make, model, year) {
        this.make = make;
        this.model = model;
        this.year = year;
    }
    
    goVroomVroom () {
        return 'Vroomn vroom!!'
    }
}
//undefined
```

New objects are declared in the same way as they are without the use of class syntax and methods are called in the same way as they are when using a prototype: 

```
const crv = new Car('Honda', 'CRV', 2017)
//undefined

crv
//Car {make: "Honda", model: "CRV", year: 2017}

crv.goVroomVroom()
//"Vroomn vroom!!"
```


These are just a few of the new features ES6 brought to Javascript, but as a new developer, I find that they have been some of the most important in making the language easier for me to learn and use. 
