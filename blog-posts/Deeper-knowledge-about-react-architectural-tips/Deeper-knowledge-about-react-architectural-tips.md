---
published: false
title: 'Learning React: Key attribute, Component Isolation and Controlled Components'
cover_image: 'https://raw.githubusercontent.com/ramclen/documenting-dev/master/blog-posts/Deeper-knowledge-about-react-architectural-tips/assets/cover.pnga'
description: 'Description of the article'
tags: react, web-development, javascript
series:
canonical_url:
---

In this post, I would like to share few things that have nothing in common but it improves our comprehension about how we should structure react and why some things behave in some ways.

## Why we use key on lists?

Something that could bother you when you are creating a list in react is the key property and his tipical "unique key value" error. If you keep bothering you about this error and why react need this, let me give you an explanation. 

The main feature of react is UI changes at any time data does or detect changes. To do that efficiently it have to detect which things are changed are which ones do not. The key property help react detect what need to update/re-render and which one are not going to be needed. 

In order to do that, they use different heuristic to go throught the tree and react using smartly the limited resources that usually browser has. 

## Every component have to be isolated, doesn't depend on loaded data before

I know, something that you listen a lot (or not) but it really help you to increase the reusability of your code and reduce the amount of bugs. 

When we are using libraries to manage our state globally, as for example redux. We sometimes fall into the same typical error. We believed that at some point the data is already loaded into our application because... How are you going to be there without follow the same steps than me? (using an url...)

That could not produce the error at that point but you later that month decide to reuse this component in a different part of you application and then (with luck) you found that your component are not working as before when you follow some steps.

That is because you does not follow this rule, a component have to work just by himself. It is a really bad practice depend on global states. So every time that you create your component ask to your application to return/load the data that it needs.

## Uncontrolled - Controlled components

You probably heard about that before, and if not, I would like to share what it is because is a concept that is really useful in terms of design your application. 

So first, lets talk about what is an uncontrolled component. An **Uncontrolled Component** does not take the responsibility storing the data and decide how it is going to be shown. Tips to recognize or create an uncontrolled component:

1. It does not store the state.
2. It needs to access to the dom the know the state.
3. It reacts by changes/events that happens in the DOM.

They are useful, for example, for small and easy components that do not need anything more than just the default behaviour.

By the other hand, **Controlled Components** take all the responsibility storing the data in their state and they are `single source of truth`. So tips to recognize or create a controlled component: 
1. It does not store the state.
2. It needs to access to the dom the know the state.
3. It reacts by changes/events that happens in the DOM.

You need one of those when you have a complex component that needs to react in a determined manner or it access values frequently. They are the `recommended way to use forms` so keep them in mind. 



# Found a typo?

If you've found a typo, a sentence that could be improved or anything else that should be updated on this blog post, you can access it through a git repository and make a pull request. Instead of posting a comment, please go directly to [my github repository](https://github.com/ramclen/documenting-dev) and open a new pull request with your changes.
