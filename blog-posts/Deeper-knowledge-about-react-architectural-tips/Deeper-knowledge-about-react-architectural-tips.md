---
published: false
title: 'Learning React: Key attribute, Component Isolation and Controlled Components'
cover_image: 'https://raw.githubusercontent.com/ramclen/documenting-dev/master/blog-posts/Deeper-knowledge-about-react-architectural-tips/assets/cover.png'
description: 'Description of the article'
tags: react, web-development, javascript
series:
canonical_url:
---

In this post, I would like to share few things that have nothing in common but they improve our comprehension about how we should structure React and why some things behave in some ways.

## Why we use key on lists?

Something that could bother you when you are creating a list in react is the key property and his tipical "unique key value" error. If you keep thinking about why React need this, let me give you an explanation.

The main feature of React is UI/data changes. To do that efficiently, React has to detect which things are changed and which ones are not. The key property help React detect what things need to be updated/re-rendered on the list and which ones not.

In order to do that, React uses different heuristics to go throught the DOM tree and reacts using smartly the limited resources that usually browser has.

## Every component has to be isolated, it doesn't depend on loaded data before

I know, it's something that you have listened a lot (or not) but it really help you to increase the reusability of your code and reduce a good amount of bugs.

When we are using libraries to manage our state globally, as for example redux, we sometimes fall into the same typical error. We believe that at some point the data is already loaded into our application because... "How are you going to be there without follow the same steps than me?"

This way of think could not produce the error at that point but later you decide to reuse this component in a different part of you application and then (luckily) you found that your component are not working as before when you follow some steps. That is because you are not following this rule.

Components have to work just by themselves. It is a really bad practice depend on global states. So every time that you create your component, ask to your application to return/load the data that it needs.

## Uncontrolled - Controlled components

You probably heard about that before, and if not, I would like to share what it is because it's a concept that is really useful when you are designing your application.

So first, lets talk about what is an uncontrolled component. An **Uncontrolled Component** does not take the responsibility storing the data and decide how it is going to be shown. Tips to recognize or create an uncontrolled component:

1. It does not store the state.
2. It needs to access to the DOM to know the state.
3. It reacts only by changes/events that happens in the DOM.

They are useful, for example, for small and easy components that do not need anything more than just the default behaviour.

On the other hand, **Controlled Components** take all the responsibility storing the data in their state and they are `the single source of truth`. So tips to recognize or create a controlled component:

1. It store the state.
2. It do not access to the DOM to know the state.

You need one of those when you have a complex component that needs to react in a determined way or access to values frequently. They are the `recommended way to use forms`, so keep them in mind.

# Found a typo?

If you've found a typo, a sentence that could be improved or anything else that should be updated on this blog post, you can access it through a git repository and make a pull request. Instead of posting a comment, please go directly to [my github repository](https://github.com/ramclen/documenting-dev) and open a new pull request with your changes.
