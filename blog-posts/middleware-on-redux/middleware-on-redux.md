---
published: false
title: "Middleware on redux"
cover_image: "https://raw.githubusercontent.com/ramclen/documenting-dev/master/blog-posts/middleware-on-redux/assets/redux.png"
description: "Answering questions about middleware on redux"
tags: redux, middleware, typescript, javascript
series:
canonical_url:
---

If you are start learning Redux, middlewares could be a pain know what it is and why we need them... So I am going to try to give you few keys (and links) to help you in your learning process.

## What is a middleware?

A middleware is usually called "Software glue". It is usually a piece of software that it is in the middle of two software, and it make easy the communication between them.

A middleware become popular with the beginning of Operating systems architecture. It made easy the way that engineers get/set data to operating system.

In [redux documentation](https://redux.js.org/advanced/middleware/) says:

`Provides a third-party extension point between dispatching an action, and the moment it reaches the reducer.`

So is basically a piece of code between actions and reducers.

## Why we need them?

Yes, I was thinking the same, why we have to complicate things that much? But hold on, it have good a reasons.

Actually, It is technically possible do it without middlewares. But, as a rule of thumb is a bad idea and you could mess things.

Redux try control access to state and reduce any problems. For that propose they try to give you few guidelines. They usually are aimed to reduce complexity and organize everything by single responsibility. The things that clarify me this were:

1. It made easy the process to create new kind of actions. The big thing here is we are going to probably send the dispatch to our new action. That have two disadvantages:

    1. Made the method signature complex and a bit difficult to read.
    2. Now we have two different ways to call actions.

2. We encapsulate this complexity from our UI Components. In that way every action is executed in the same way. If in the future we change that actions and it does not need any middleware Components does not need to know or change anything.
3. Middleware are composable in a chain.

Basically, This is a SOLID solution.

If you want to know more, Stackoverflow [has a great thread](https://stackoverflow.com/questions/34570758/why-do-we-need-middleware-for-async-flow-in-redux) talking about this doubts: 

## Cool but, Where is this exactly in Redux?

The architecture inside redux looks like this:

![middleware architecture](https://raw.githubusercontent.com/ramclen/documenting-dev/master/blog-posts/middleware-on-redux/assets/middleware-redux-architecture.png)

## Ehm but, How it works?

So easy, thinking on Thunk Redux, when you dispatch one of yours new ThunkActions, is going through redux environment, but not directly to reducers. It first pass through middlewares and there, Thunk detect this action as a ThunkAction because it takes only one argument, a Redux store.

After that, it will execute your "normal" actions in the order that they have been resolved. But this action will go finally to our reducers (But they could also pass through any other middleware)

I think [this post](https://medium.com/flutterpub/flutter-redux-thunk-27c2f2b80a3b) explain better.


## How I create my own middleware? 

As we say and see on what its a middleware and where it is, it is a piece of code between actions and reducers. 

Here a small example:

```ts
const awesomeMiddleware = store => next => action => {
  if(action.type === 'MY_ACTION') {
    console.log(`My awesome middleware is working!`);
    store.dispatch(action.payload.otherAction)
  }
  next(action);
}

const store = createStore(counter, applyMiddleware(awesomeMiddleware));
```

The code is not really good, but it works for what we are trying to show. The power of middlewares. Probably the only thing that you need a little explanation is about Next [(If you need more)](https://medium.com/netscape/creating-custom-middleware-in-react-redux-961570459ecb) . Next is a function that the middleware call when it finish with the assigned  task. This sends the action to our reducer or another middleware.




---
If you've found a typo, a sentence that could be improved or anything else that should be updated on this blog post, you can access it through a git repository and make a pull request. Instead of posting a comment, please go directly to <REPO URL> and open a new pull request with your changes.
