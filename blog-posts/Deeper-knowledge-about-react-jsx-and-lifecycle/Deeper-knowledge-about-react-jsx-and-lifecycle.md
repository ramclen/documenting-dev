---
published: false
title: 'Deeper knowledge about ReactJS and Lifecycle'
cover_image: 'https://raw.githubusercontent.com/ramclen/documenting-dev/master/blog-posts/Deeper-knowledge-about-react-jsx-and-lifecycle/assets/cover.jpg'
description: ''
tags: react, javascript, webdev
series:
canonical_url:
---

I would like to talk about typical things coming with ReactJS that you could miss when learning React. If you are in the process, this is going to help you to understand better JSX and Lifecycle. So let's start!

## What is JSX?

JSX is the language that React offers to embed UI logic and render interfaces. JSX is really similar to HTML but is not the same. It runs inside of Javascript, for that reason I am going to give few tips to boost your knowledge about JSX and differentiate to html:

- Properties and attributes names use camelCase instead of kebab-case found on HTML
  - Example: tab-index => tabIndex
- It Changes reserved words in js for a substitute
  - Example: class => className
- It always need a closed tag and it could be one line tag
  - example: `<input >` => `<input />`
  - example: `<div> </div>` => `<div />`
- Style is a Javascript object:
  - example: `<div style:{ {backgroundColor: 'blue'} }></div>`

Do not think that JSX is transformed to HTML directly, JSX is syntactic sugar for react element creation. This React Element is whose deal, following your instruction, to transform that into HTML. [Here](https://reactjs.org/docs/jsx-in-depth.html) you will find more info about this topic in React official documentation.

## Why should we use it?

There are a lot of reasons why you should use JSX, the first one and more important is because you are using React and you probably do not want to be creating elements like in the link from React documentation shown in the previous section.

But, if this is a point where you are thinking about using React or not let me try to convince you.

- You will have more typo errors (helping you to find errors on UI)
- It will give you the opportunity to create complex UI interfaces with a lot less code and less headaches
- It is secure, JSX prevent injection attack because React DOM escapes any values embedded in JSX before rendering them.

When you are going to create an application/web page these points are really helpful. It reduces complexity and improves your productivity and the security of your project.

## What is Lifecycle on React?

Lifecycles are the different stages that our component pass during his life in the DOM. The life of our component pass through three main phases:

- Mounting
- Updating
- Unmounting

When our component is passing a specific phase it will call the correct function. In those functions, we could tell to the components to behave in a specific way (Download data, prepare the state, release resources...)

## Cool, but what are those methods?

Ok, to keep it simple let me show you the more used methods

- **Building** our component before showed in the application.
  - `constructor()` Yep, famous constructor method, that method is to focus on state and properties set up. The reason behind this is that we want to show our component as soon as possible. Also, this is actually the only place where you are going to be able to assign `this.state`. Another thing to have in mind is that you must always call `super()` to send properties to React Component parent class.
- **Showing** or render our component.
  - `render()` here is where we are going to focus on tell to react how our component is going to looks like, for that purpose we use JSX.
- Component **is Mounted** in the DOM.
  - `componentDidMount()` This is a perfect method to execute code that require more processing (for example running requests) and it is going to be needed only at the beginning of the component lifecycle.
- Component **is Updated**. It means that the state or props has changed.
  - `componentDidUpdate(previousProps, previousState)` So this method is used when we are concern about how our component is evolving and we want to react differently depending of how our state or props are changing.
- **Unmounting** our component. This happens when our component is removed from the DOM.
  - `componentWillUnmount():` this method is useful when we want to clear or free some resources.

Here is a graph to understand better the order and in which phase is every method:
![lifecycle graph](https://raw.githubusercontent.com/ramclen/documenting-dev/master/blog-posts/Deeper-knowledge-about-react-jsx-and-lifecycle/assets/lifecycle.png)

# Found a typo?

If you've found a typo, a sentence that could be improved or anything else that should be updated on this blog post, you can access it through a git repository and make a pull request. Instead of posting a comment, please go directly to [my github repository](https://github.com/ramclen/documenting-dev) and open a new pull request with your changes.
