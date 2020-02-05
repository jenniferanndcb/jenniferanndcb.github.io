---
layout: post
title:      "Learning JavaScript by Writing More JavaScript"
date:       2020-02-05 16:43:25 +0000
permalink:  learning_javascript_by_writing_more_javascript
---


When I was growing up, I enjoyed learning school. I enjoyed studying, writing copious notes and memorising. 

Learning programming in the last 8 months has not been quite the same. 

I thought it would involve learning and memorising syntax. To some extent, maybe so but not the most important thing. 

I realised quickly after building my first CLI project, that programming requires a different approach and mindset. I learned that through practice and building our own project, can we really apply all the concepts that we learn. 

As we worked through the curriculum, I struggled to grasp the concepts introduced in the JavaScipt section. One particular concept that took me a while to understand was `fetch( )` 

The `fetch( )` method allows us to interact with resources or data from an API. In doing so, it returns a Promise which needs to be parsed into something that JavaScript can read and use in our frontend. It is done so by:

`fetch("URL-of-API").then(res => res.json())`

As we called .json( ), this returns another Promise and so we call: 

`.then(data => {
console.log (data)
//we can now do code here
}`

So it took me a while to understand the concept of Promise and what it is. 

It helps to view it in the context of asynchronous execution model which allows browsers to handle bits of the code one bit at a time. 

For my project, I built a Single Page Application using HTML, CSS and JavaScript with data provided from a backend API that I built with Rails. 

It was a good learning curve as I finally got my head around other concepts such as: 

* event delegation 
* functions 
* `this`
* scope
* arrow functions  

If you are interested in having a peek, check out the github repo [here.](https://github.com/jenniferanndcb/bookclub_books_js)  

