---
published: true
title: 'Understanding Redux'
cover_image: 'https://raw.githubusercontent.com/ramclen/documenting-dev/master/blog-posts/understanding-redux/assets/redux-architecture.png'
description: 'Answering questions about redux'
tags: redux, javascript
series:
canonical_url:
---

First, this post is not to learn redux, it is to clarify few key concepts. So its about resolving doubts more than trying to explain Redux. I would recommend [Redux documentation](https://redux.js.org/basics) if you are trying to find a resource to start learning redux.

## What is redux?

I will try to keep simple. Redux is a small library to store the central state and make it predictable. For that purpose it use functional programming paradigm concepts.

It keeps control of how you manipulate the state giving you three basics concepts for it, `Actions`, `Reducers` and `Store`.

Redux just let you follow a unidirectional data flow state modifications, and it starts by `Actions`. `Actions` send the data to the correct `Reducer` and `Reducers` modify the state.

## Wait wait... actions? reducers? state?

Ok, I will try to give you few keys to understand this concepts:

- [Actions](https://redux.js.org/basics/actions) are basically the definition of the change that you are going to make in the state. They are the responsible to take and pass the information to the proper reducer. For that actions, return a plain javascript object. The only value needed by redux is `Type`, the rest of them are up to you. Type is used by Redux to identify the correct reducer.

```ts
// Example of a plain object returned by an Action
const SET_USER = 'SET_USER'

...

{
  type: SET_USER,
  payload: {id:2, username: 'John'}
}
```

---

**BONUS**

It is a good practice define our action types because they are going to be used around our application.

---

- [Reducers](https://redux.js.org/basics/reducers), here is where we said to redux how the state is going to be changed. Reducers receive the information obtained by actions and return the new state. Redux give us one restriction here and it is that Reducers have to be `Pure Functions`.

```ts
function setUser(state, action) {
  return Object.assign({}, state, {
    user: {
      username: action.payload.username,
      id: action.payload.id,
    },
  });
}
```

- [Store](https://redux.js.org/basics/store) is the object that keep control over the state. So if you need, update the sate, listen changes, etc. the state is your guy. It is a singleton, that means that we only have one in our application.

## Pu... Pure Functions?

Pure functions is a term that comes from functional programming. This term means that a function should do not produce any external side effect (Change or read global values, make API calls, write or read files, etc).

That means that pure functions are [deterministic](https://en.wikipedia.org/wiki/Deterministic_system). In other words, you can know the output from specific inputs. This is key when you want to keep something like your application state under control.

## Ehm, What is functional programming?

This may take more time to explain it, but I will give you few things to understand a bit what we are talking about.

Functional programming is a paradigm that avoid changing state and mutable data. It create solutions treating the software as compound of mathematical functions (or pure functions).

So if you compare with Object Oriented is probably really different. If you would like to know more about Functional Programming [here](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0) is a place to start.

## I feel its too much, Do we really need it?

It depends...

If you are creating a really small app the answer is no, but if you are creating a big application and you have a central changeable state this is probably the solution to your problems.

Another thumb rule is giving by Dan Abramov:

`I would like to amend this: don't use Redux until you have problems with vanilla React.`

So, basically, if you are reading about redux and it does not help with your headaches, it is probably because it is not the answer.

## I do not like it, Do you have something better?

I do not know if they are better, but I have few options that you could check. Probably depending of your needs you will find them more helpful in your situation.

- [Mobx](https://mobx.js.org/README.html#getting-started)
- [RefluxJS](https://github.com/reflux/refluxjs)
- [Relay](https://relay.dev/)

# Found a typo?

If you've found a typo, a sentence that could be improved or anything else that should be updated on this blog post, you can access it through a git repository and make a pull request. Instead of posting a comment, please go directly to [my github repository](https://github.com/ramclen/documenting-dev) and open a new pull request with your changes.
