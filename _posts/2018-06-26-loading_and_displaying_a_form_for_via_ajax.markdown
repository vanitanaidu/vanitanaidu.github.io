---
layout: post
title:      "Loading and Displaying a form_for via AJAX"
date:       2018-06-26 11:16:12 -0400
permalink:  loading_and_displaying_a_form_for_via_ajax
---

 

In my product page, I was trying to display a textbox in the form of a form_for formbuilder, and later display the user input on the DOM. The first step was attaching a event handler to a “Click Here to Order” button tag. 

![Click Here to Order button]( https://i.imgur.com/85iFeQvm.png )
<br/>
<br/>

When that button was clicked, it fired a Ajax Get request which gave me back a response of a form with a hidden_field and text_field. 

![Quantity Input Text Box](https://i.imgur.com/FC2YQ1Fl.png)
<br/>
<br/>

On line 49, I am attaching the response in a html format to my show page inside a div with a id named `#textbox`. 


![Code](https://i.imgur.com/zWLltw5h.png)
<br/>
<br/>

That line of code gave me this output.

![Code](https://i.imgur.com/mSXTZN3l.png)
<br/>
<br/>

Once that was done, I had to somehow get access to the form once again. So I did that by grabbing the form element by it’s id name  `new-line_product`. On line 53, I attached a submit event handler to the form and called upon another function `submitForm(this)` with an argument of `this` so that the function had access to the form data. 


![Code](https://i.imgur.com/x3Pvwcvh.png)
<br/>


<br/>
![SubmitFormCode](https://i.imgur.com/pfuhVzkh.png)

As you can tell the submitForm function is sending a AJAX post request to the line_products index page. Here I opt to use the low level `$.ajax()` instead of the high level `$.post()` request because I had specific details to add like data, success and error and found using `$.ajax()` easier with those details. So `type` was a POST request, the `url` was where I wanted my form to be posted to and `data` was given a variable `formData` that basically serialized the form and gave me back a query string. I then went further to code what I wanted to happen if the response was a success or error. 
<br/>
<br/>

if it's successful: 


![if success in submitForm Function](https://i.imgur.com/gV3t0Eph.png)
<br/>
<br/>


The function `cartButtons(id)` will be called upon passing in the carts `id` as a argument. The `cartButton(id)` function basically did another Ajax Get request to the carts show page and spits that html page out onto the dorm. 


 ![cartButton Function](https://i.imgur.com/JrNFS7Dh.png)
<br/>
<br/>

if it's not successful: 

The error message will be put out to the dom. 


![if error in submitForm Function](https://i.imgur.com/MZGQSW7h.png)
<br/> 


All the logic for the AJAX process was done in the `line_products` and `carts` controller. To view the entire code please visit [my github](https://github.com/vanitanaidu/jquery-frontend)

