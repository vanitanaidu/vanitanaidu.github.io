---
layout: post
title:      "Creating Christmas Shopper App"
date:       2018-06-26 15:14:07 +0000
permalink:  creating_christmas_shopper_app
---


This lab was generally easy though tedious. I built an app for users to store their intended Christmas gifts. I created 2 databases: one for the user and the other for the gifts. The main logic of how to create, read update and edit (CRUD) was pretty easy to write. However, the small details became tedious.  


One of the helpful things I did was working in steps. 

1. On paper, I decided how many databases I would have. I chose their columns and mapped the relationships between them.
2.  I made the models.
3.  I ran PRY to check whether my databases worked by creating a user object and gift object and doing method calls.
4.  I then created the controllers and view files. I worked on one route and one view file at a time *(This was a challenge for me because I was used to jumping to between routes because I always had a spec test to depend on. This time I did things the proper way, and the process was more clear and organized.)*. I copied from previous labs and modified codes according to what my project needed. I was also constantly checking how my code displayed on the browser *(Again, since I had zero tests to depend on, I relied on checking my work on the browser for every line of code.)*.
5.   The process was mostly easy, but I was not able to log in with the username and password after signing up. I was asked to sign up each time I tried to log into my account which was solved because I simply forgot a `@` infront of my variable. Another issue I had was being able to create, view, and edit the list of gifts that didn’t belong to me. I worked with Learn instructor made me realize that I had forgotten to do an important step, which was to make use of the helper method `current_user` to ensure added security for users to not views other peoples gift.


#### Original Code:	
```
get "/gifts" do
    if logged_in?
 >  @gifts = Gift.all
      erb :"gifts/gifts"
    else
      flash[:error] = "Please log in"
      redirect to "/login"
    end
  end
```

#### Code after modification:
```
get "/gifts" do
    if logged_in?
 >  @gifts = current_user.gifts
       erb :"gifts/gifts"
    else
      flash[:error] = "Please log in"
      redirect to "/login"
    end
  end
```

The reason why I was seeing gifts I didn't create? `@gifts = Gift.all`(1st code snippet, line 3). By simply changing that line of code to `gifts = current_user.gifts`, the interpreter only displayed the current_user's ( assigned `session[user_id]` after signing up) gift list. 


<br>
CSS styling was another part that I enjoyed thoroughly. The process included not just looking at the pretty design, but anticipating the user experience and designing something intuitive. I feel that making intuitive, easy to understand design is the most important goal for me right now. I wanted the user to know where to look, what to do next, where to click. That took priority over “pretty” or “slick” web design.  I hope I achieved this.  I did user testing with my husband and he had nothing but praise for my app, so maybe next time I should try someone more critical (and not a relative).

<br>
Generally, I wrote the same codes over and over in my project. It made me appreciate the amount of painstaking work developers had to put in before Rails was created. I am looking forward to seeing how Rails encompasses all this Sinatra logic. All in all, I am so very proud of the app I made. Here is a preview:

 <br>
![Christmas Shopper](http://imgur.com/kee9iTG.jpg)

[**Link to my app**](https://github.com/learn-co-students/sinatra-cms-app-assessment-v-000)


