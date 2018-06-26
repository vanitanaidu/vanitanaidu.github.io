---
layout: post
title:      "What is a Promise"
date:       2018-06-26 15:34:54 +0000
permalink:  what_is_a_promise
---



**What is a promise? **

A promise is a function that returns a value in the future.

A promise can be in 1 of the 3 states.

(1)	Pending – The promise’s outcome isn’t being determined yet, because the asynchronous operation has not been
                           completed yet.
													 
(2)	Fulfilled – The asynchronous operation has been completed and the promise returns a value.

(3)	Rejected – The promise was not fulfilled and as a result the asynchronous operation failed. In this state, the promise 
                             returns to you the reason why the operation failed.
														 
Let me furthur explain this in layman term so we can demystify what this whole `promise` thing is about. Let us take this scenario as an example. You promise your kid that you will go to his soccer match next week. In this scenario, there is a pending promise that would either be fulfilled or rejected in the coming week. The return value will either be, you going to his soccer match or it will be a reason as to why you could not keep up to your promise eg: “I had to attend your sister’s piano recital instead”. So just remember that a promise is basically a function that returns a value sometime in the future. The return value could be a fulfilled value or it could be the reason for the rejected value like a network error. 


Let’s take this code as an example 

```
 callApi() {
   fetch('/api/users')
   .then(response => { return response.json() })
   .then(users => console.log(users))
   .catch(err => console.log(err))
 }
```

We have a promise function that is going to fetch data from our backend rails api. The first `then` on line 3, is the promise that is being returned, at this moment we DO NOT have a return value yet just the promise that something will be returned. We take that promise and we tell it that whenever the promise is resolved, we want the return value to be in a json format. The second `.then` is the return value. We attach the 2nd `.then` to the promise and ask it to console.log the fulfilled promise to the browser. `.catch` is mentioned in case the promise comes back with a rejected promise. In that case, we would “catch” whatever errors the promise gives us back and console log the error to the browser.

That’s about all promise does. 

Take a look at this code and guess what the return result would be?
 

 ```
 callApi() {
    console.log('a')
    fetch('/api/users')
    .then(response => { 
      console.log('b') 
      return response.json() 
    })
    .then(users => console.log('c', users))
    .catch(err => console.log('d', err))
    console.log('e')
 }
```

(1) In what order will the alphabets be returned if the promise was fulfilled?

(2) In what order will the alphabets be returned if the promise was rejected and there was an error?

</br>

The answer is  …………...........

</br> 
</br> 
</br> 
</br>

***a,b,e,c*** -  If the promise was fullfilled

***a,b,e,d*** -  If the promise was rejected

</br>

**How did we arrive at this answer?**

The first letter to be displayed is definitely going to be `a` as that’s on the first line of the function. The second letter would be `b` because the response will be the promise function that will be returned to us. You might have thought that the third letter will be `c`. If you didn’t, good job, if you did, read on. The reason why `c` does not appear next is because `c` is attached to the 2nd `.then`. The 2nd `.then` is when the asynchronous operaton is being executed in the background. Again, in a synchronous program execution, your program is executed line by line, one line at a time. Each time a function is called, the program waits until that function returns a value before continuing to the next line of code. However, in a asynchronous execution, the program does not wait for the function to be executed, it moves on to the next line of code and once the asynchronous operation is completed, it returns to us a value. So based on how asynchronous operations work, `c` will not be returned right after ‘b’. The program is going to move on to the next line of code until that asynchronous operation has been executed. What is the next alphabet then? 

If you guessed `e`, you are absolutely right! After `e`, the function comes to an end, guess what will be the next letter all ready to be displayed? Yes, `c`. Well, actually, it depends. `c` if our promise returns a fulfilled value or `d` if it returns an error. So `a,b,e,c` if the promise was fulfilled and `a,b,e,d` if the promise was rejected.

