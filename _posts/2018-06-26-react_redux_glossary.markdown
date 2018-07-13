---
layout: post
title:      "React Redux Glossary "
date:       2018-06-26 11:33:47 -0400
permalink:  react_redux_glossary
---


React Redux was a really tough one for me. I watched a ton of videos and read many articles to help me with the basics. However, there was one video that truly helped me solidify my understanding on React and Redux. It was a detailed course I found on Udemy by Stephen Grider. I took down notes while I went through the entire course. I am unable to share everything with you but I thought I would share some key concepts that is monumental in understanding React and Redux.


***React*** 

React is in charge of showing views.



***Redux*** 

Redux keeps track of the current state of the data that we get back from user input.
 
 

***React & Redux***

It is key to understand that React and Redux isn’t connected. To connect them we need to forge a connection by using the library `react-redux`.



***Action Creator***

A function that changes/does not change the redux state.

Example: when a user clicks on something and a action will be triggered and that action will be passed to all the reducers and the reducer will return the current redux state. That current redux state will be passed to the view.



***React State(component state) vs Redux State***

In redux, all of our data is placed in 1 place; the STATE. 
This state(which is just a plain old javascript object) is stored in the Redux store. We can access this state, by using the mapStateToProps in any of our components. So just remember that the redux state is stored globally in the Redux store.

However, the react state which is also commonly known as the component state,  stores our data in the component’s state itself.  If other components need to share this state, then you will have to pass it down through props, which means that your top level component in your app will hold the value of the state. If you want to learn more about the React and Redux state, I would recommend [this article](http://spin.atomicobject.com/2017/06/07/react-state-vs-redux-state/). The author Tyler Hoffman gives a very clear and detailed explanation differentiating the two types of states.



***Reducers***

Now that we understand that an action updates the state, how do we connect the action and the state? We make the connection through a function called reducer. A reducer is basically a function with a switch and case statement that returns a piece of the redux state. So the action updates the state and the reducer returns the updated state.



***mapStateToProps***

This is a helper function that helps you access the redux state from any of your targeted components.

Function mapStateToProps(state) {
    return { allbooks: state.books }
}
state in the argument refers to the redux state. By returning, state.books, you are actually accessing books in your redux state.



***mapDispatchToProps***

mapDispatchToProps is a helper function that helps your component to fire an action event 



***Containers***

Containers are smart. They have direct access to redux state



***Components***

Components are dumb. They have no direct access to the redux state



