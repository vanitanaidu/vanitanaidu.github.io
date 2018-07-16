---
layout: post
title:      "Nested Form for an existing parent record.."
date:       2017-06-30 00:00:00 -0400
permalink:  nested_form_for_an_existing_parent_record
---




Nested form is the approach to take when we want a single form to manage and save multiple models that are associated with one another.  There are plenty of resources out there to help people build forms for new parent record via existing child record, but I struggled to find resources that helped with building forms for a new child via an existing parent. Mine was also a unique situation because I wanted to classify the parent record into 2 different types.

I was working on a form for my online flower shop whereby users could input their addresses and messages to recipients on the same form. User was an already existing parent record while Address and Message were new children records to be created and saved through nested forms. 

Let's start with the controller file.


## ***AddressesController.rb***



`address_type` was an attribute of the Address model and in this case I wanted to build a form for 2 different types of Addresses; `Shipping` & `Billing`. **Devise** gave me the helper method `current_user`. 

![](https://i.imgur.com/wUE26F2h.png)

## ***Form.html.erb***
![](https://i.imgur.com/zEJM2khh.png)


On line 11, I made sure the address object had an `id` before the form was generated. This line of code made sure that only 1 text field was displayed for each `address_type`. Line 12 was just making sure that the form would be split into 2 different types of addresses. However, this is only possible because of line 17 & 18 in the controller file.

## ***Form.html.erb (cont.)***
![](https://i.imgur.com/3M4sknIh.png)

This was the form that was generated:

![The Form](https://i.imgur.com/LGVTwBbh.png)



[Every Bulb](https://github.com/vanitanaidu/every-bulb)

