---
published: false
title: 'Your title'
cover_image: 'https://raw.githubusercontent.com/ramclen/documenting-dev/master/blog-posts/understanding-react/assets/react-logo.jpeg'
description: 'Description of the article'
tags: react, javascript, webdev
series:
canonical_url:
---

## Here we go again, what is react?

React is a powerful javascript library that helps us to create web applications. React focuses on how the appearance looks like and react to user interactions and creations of, what we call **components**.

The library was released on 2013 but it has been under development since 2011 by Jordan Walke a software engineer from Facebook.

## What are components in React?

A Component is a concept that developers use to isolate a part of the UI and encapsulate similar features to make easy to reuse and maintain. Components must be independent of the rest of the application.

At the end, a component is a piece of HTML and JS code that show and interact with the user. So a button is a component but you can also have a component that is a compilation of components. You can have components inside other components also, creating them one by one and bounding them together.

So, for example, a button could be a component itself, but you can add this small component with a input and create a new component.

## What is an application?

An application is a software that is created to final users. Yes, I know, it sounds ambiguous but it is what we have. So your android/iOS applications are that, applications, pieces of software made with a great UI/UX to everyone know how to use it (well... the good ones).

When we use React is to create Web Applications, applications are great because they run anywhere and it does not need to be store. Web applications have good points but also few bad ones. For example, they have reduced access to the operating system, performance issues, etc.

But good news, React have React Native, it reduces this kind of problems and lets us create great applications for mobiles using the same brilliant library.

## State and Lifecycle? What they are?

State is a javascript object that contains the data relative to an object. We use them because we can update the state from a component to rerender it.

We update the state object using the `setState()` function. We have to initialize state when we create a component. React state is only valid in class based components.

Every React based component has what we call lifecycle methods. It is like a series of events (or functions) that are going to be called automatically by React at certain points during this lifecycle.

It has three phases:

- Mounting: Puts elements into the DOM.

  - `constructor()`. This methods is called before anything else.

  - `render()` method it’s always required. Makes the content visible on the screen.

  - `componentDidMount()`. It’s called after the components will shows up. Good place to do data loading.

- Updating: A component is updated when the state or props is changed.

  - `componentDidUpdate()`: Even if you are on the updating phase, render will be call to show the content on screen when change is produced.

- Unmounting: Stop showing components on screen.
  `componentWillUnmount():`

## You always complicate things a lot, why I need it?

By using React, we can create Web applications with reusable components, and change data without reloading the page. So we can create large web applications easily.

# Found a typo?

If you've found a typo, a sentence that could be improved or anything else that should be updated on this blog post, you can access it through a git repository and make a pull request. Instead of posting a comment, please go directly to [my github repository](https://github.com/ramclen/documenting-dev) and open a new pull request with your changes.
