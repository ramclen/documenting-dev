---
published: false
title: 'Starting with typescript'
cover_image: 'https://raw.githubusercontent.com/ramclen/documenting-dev/master/blog-posts/starting-with-typescritp/assets/typescript-logo.png'
description: 'Basic introduction to Typescript'
tags: typescript, javascript, dev
series:
canonical_url:
---

I am going share with you few things to try learn easy and fast how to use typescript in your projects. This is only an abstract about how to use typescript and basics things if you need more information about I recommend you to go to the official [handbook](https://www.typescriptlang.org/docs/handbook/intro.html). There you will find more and very good explain concepts and examples.

But lets start.

## The primitives

So the primitives are the simplest units of data that Typescript give us to build the rest of our objects. Here the most used ones

- boolean: it could contains True or False value.
- number: Well not too much to explain about this, a number.
- string: A concatenation of characters together, humans usually call it text.
- Array: You could store multiple values of same type by order.
- Enum: A friendly set of values.
- Any: If you hate typescript and love JS you will love this type (bad pattern alert). This type could be any of the rest of types
- Void: It means actually that, not really useful because only can store `undefined` and `null`. Used mostly as a return type on function that return nothing

here an example:

```ts
// Basic variable types
const isBoolean: boolean = true;
const numbers: number[] = [1, 2, 3, 4]; // This is how you declare an array of numbers

// Enums
enum GREETING {
  HELLO = 'HELLO WORLD',
}

// Function and void type
function sayHi(): void {
  console.log(GREETING.HELLO);
}
```

## Strange Types

_If you just want to have a quick look to Typescript jump to next section._

"Do we really need those types?" That the question could come to your mind when you see next types for first time, but in some scenarios are needed. Probably you will not use this types but if you find yourself in any of this scenario you will know what to do.

### Undefined and Null

It only can be their own value ( `null` or `undefined` ). It looks are not pretty useful by their own, like void, but if you want to use `--strictNullChecks` ( [more info](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-2-0.html#--strictnullchecks) ) it would help you to specify when a variable or type could be undefined or null.

### Unknown:

It exactly means that, a type that is unknown. When you receive a value from a function that you do not know what type is, we use the unknown type.

The main difference with any is that any let you use random attributes that the object could have. Using any property with unknown will throw a error.

if you want to know more about it [here](https://mariusschulz.com/blog/the-unknown-type-in-typescript) is a deeper explanation and distinction from the any type.

### Never:

It is a type for something that never happen or should not exists. it is used in functions that returns exceptions or one that never returns like a infinity loop.

Here few examples:

```ts
function buildError(msg: string): never {
  throw new Error(msg);
}

function infiniteLoop(): never {
  while (true) {}
}
```

### Difference between string/number/boolean/object and String/Number/Boolean/Object

If you are here just trying to learn and do not care much about what is what. As a rule of thumb you should try to avoid using uppercase ones.

If you are like me, you will probably want to know a bit more, so it is an easy explanation to have both ones. Typescript is a language that has been built over Javascript so it needs compatibility with types or objects that already exists.

You probably remember that we have things like this in Javascript:

```js
var str = new String('My new string');
var nmbr = new Number(3);
```

So thats it is actually what represent that upper case types on Typescript. It is usually a bad pattern use them to create new types on Typescript. So you should avoid them as much as possible.

Go [here](https://www.typescriptlang.org/docs/handbook/declaration-files/do-s-and-don-ts.html#number-string-boolean-symbol-and-object) if you want to know more about this.

# Classes, interfaces, types

- Classes:
  So classes are the same one that was introduced in javascript ES6. The good point of TS is that let you create your own types of objects. Here a basic example

```ts
class Dog {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  eat(): void {
    console.log('Glump');
  }
}
```

- Interface is like the structure of a class, it do not implement how things work, only define the API that a objects or class are going to have. Here is an example:

```ts
interface Animal {
  name: string;
  eat(): void;
}
```

here an example of a class implementing the interface Animal and a function that returns that interface.

```ts
class Human implements Animal {
  name: string = 'John';

  eat(): void {
    console.log('gluh');
  }
}

class Bird implements Animal {
  name: string = 'Parrot';

  eat(): void {
    console.log('glip');
  }
}

function bornAnimal(type: string): Animal {
  if (type === 'BIRD') {
    return new Bird();
  }

  if (type === 'HUMAN') {
    return new Human();
  }
}
```

So Interfaces let us use objects without knowing exactly how it is implemented or his entire API, only understanding the part that is exposed by the interface.

- Types: It is really similar to an interface, they are used to define the structure of an object but it has some difference, for now lets show how to use it

```ts
type Animal = {
  name: string;
  eat(): void;
};
```

if you want to know more about differences about interfaces and types [here is a good post about it](https://medium.com/@martin_hotell/interface-vs-type-alias-in-typescript-2-7-2a8f1777af4c). To keep it simple lets say that its usually used to define literal object and for more compact definitions, for example to define states and props in React with Typescript.

## Modifiers : private, public, protected

The modifiers define how a property of an object can be access. So lets show with examples an short explanations

- public: It can be used by everyone, it is part of the public API of an object.
- protected: Only classes that extend that object can use this property.
- private: It is only usable inside the object, not accessible from outside of object not even from subclasses.

```ts
class Human {
  public name: string;
  protected gender: string;
  private genes: string;
}

class John extends Human {
  name = 'John';
  gender = 'male';
  genes = 'ABXBSA'; // this is not allowed

  constructor(genes) {
    this.genes = genes;
  }
}

const foo: Human = new John();
console.log(foo.name);
console.log(foo.gender); // this is not allowed
```

## Types composing || and &

# Found a typo?

If you've found a typo, a sentence that could be improved or anything else that should be updated on this blog post, you can access it through a git repository and make a pull request. Instead of posting a comment, please go directly to [my github repository](https://github.com/ramclen/documenting-dev) and open a new pull request with your changes.
