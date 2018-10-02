---
layout: post
title:      "React - Why do we need keys?"
date:       2018-10-01 23:38:59 -0400
permalink:  react_-_why_do_we_need_keys
---


## What is a key?

 A “key” is a special attribute you need to include when iterating through a list of elements in React like an array of numbers.  Keys help React identify which items have changed, added, or removed to decide if it should re-render. Keys should be used inside your map() call to give the elements a unique identifier.

## Back to the Basics:
Every individual component in React gets automatically assigned a key to the elements based on the render order. 

```
<div>
       <h1> Understanding </h1>
			 <h2> Keys </h2>
</div>

<div>
       <h1> In </h1>
		   <h2> React </h2>
</div>

```

React assigns keys to every element in your component like this:

```
div: 0   
h1: 0.0   
h2: 0.1

div: 1   
h1: 1.0   
h2: 1.1
```


Using these keys, React knows exactly what to re-render and what not to in the virtual DOM. A change in key tells React that there has been a change in the element’s identity and thus a re-render is triggered. In most cases, Reacts takes care of the dirty work of assigning keys to every element in our component. The only time, you have to specifiy a key for your elements is when you are rendering a list of elements. When React sees a list of elements, it smartly assumes that the elements in the list at some point is going to change. It assumes that at some point, you are going to do something to that list of elements; delete an element, insert new elements, etc. To help React with this, we need to provide keys to our elements. React will reprimand us (via a warning) if we do not do this. 

![](https://i.imgur.com/7wuzfXTh.png)

## How do we pick a key? 

The best way to go about this, is to use a string that uniquely identifies an element in the list among its other siblings. So, for example, the `id` of your data would be used as the key. 

If you don’t have a unique `id` for rendered elements, you may use the element's `index` as a key but this should only be done if you have absolutely no other options. The reason for this is, if the order of the items gets modified (eg; if you add a new item to the front of your list, the index 0 now points to that element), React will identity elements incorrectly and this will cause issues with the component state.  

![](https://i.imgur.com/wJgzeJth.png)




