---
layout: post
title:      "Fetching data from the rails backend server"
date:       2018-06-26 15:34:20 +0000
permalink:  fetching_data_from_the_rails_backend_server
---


![](https://i.imgur.com/wj6Hgnsh.png)


We have a function called `fetchUsers`. This function is going to be responsible for fetching a list of users from our rails backend. So let’s imagine we have already set our routes up in our routes.rb file that links to the index function on our controller. In this case, we will have a route “/api/users”. Let’s take a look at our rails UsersController.rb file. 
  

![](https://i.imgur.com/Q7mOBqhh.png)

In our users controller, we have a variable `@users` set to `User.all`. The function index will be responsible for giving us access to all the users in the database. Great! That’s what we want. Now on our react client-side, let’s 
take a look at what our code would look like.

![](https://i.imgur.com/WUP3Kfrh.png)

On line 18,  we use the method `fetch` to make a ajax request to fetch all the users from our database. On line  19-21 we are simply getting back the fetched data through an argument  and returning that value in a json format by attaching `.json` to the response argument. In short, we are asking for the data to be returned in a json format. Always remember, when we use fat arrows/arrow functions `=>`, the argument is on the left side of the arrow and the value is on the right of the arrow.  

Now, we attached a `.then` again. This time we have an argument of users that is going to be console logged to the browser. So why do we need two `.then` you may ask. Don’t forget that this is the ajax request, meaning the servers is making a asynchronous execution in the form of a promise. The first `.then` is going to return us a promise. A promise that is either going to return us a fulfilled value or a rejected value. The second `.then`  is basically a way of saying, once that promise is resolved, please return to us whatever the return value is. So the second `.then` is assuming that the return value is going to be a fulfilled one. What if the return value is a rejected one? In that case we can use `.catch` to capture the reason for the rejected value, the error. Please refer to 
[this article](http://vanitanaidueckert.com/what_is_a_promise) for a detailed explanation on what a promise is. 

So what does this ajax request return to us upon resolving the promise?? Let’s take a look. 

![](https://i.imgur.com/6SWxBFch.png)

Since we console logged it, we get back an object of the entire list of users with all their attributes on the browser.







