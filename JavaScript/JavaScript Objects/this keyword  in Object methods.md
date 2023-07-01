---
date created: 2023-07-01
last updated: 2023-07-01
programming language: javascript
tags: objects, this
aliases: 
---
⬆ [[_JavaScript Objects_]]

![[Using arrow functions inside object methods#Don't use arrow functions as object methods]]

**For everything that follows in this note, assume we are not using an arrow function. But see "exception" at end of note

The `this` keyword (if used inside of a function) refers to whatever calls that function (whatever was responsible for executing that function). 

When `this` is used inside an object method, it's typically going to be the object that calls the method, so `this` would refer to the object. 

If you are the one directly executing your code (i.e. not an event listener, ``.apply()`` or `.call()`), then the thing that calls the function is going to be the thing in front of it e.g.
```js
let text = movie.getFormattedTitle() // where movie is an object and getFormattedTitle is one of its methods
// movie is the thing which is resposible for executing that function/method. `this` refers to `movie`
```

But if we destructure the method, there is nothing in front of the method and `this` refers to the wrong thing
```js
const { getFormattedTitle } = movie
let text = getFormattedTitle() // now  the thing responsible for executing the function is our global execution context – in non-strict mode, this will be the window object. In strict mode it will be undefined. 
```

We could fix this with `.bind()`, but if you look at the code, you'll see it's a bit redundant. `.bind()` is intended for preparing a function for ***future*** execution.
```js
let { getFormattedTitle } = movie
getFormattedTitle = getFormattedTitle.bind(movie)
let text = getFormattedTitle() // now it works again. The first argument of the bind method always sets what `this` should refer to. Now we've said `this` shouldn't refer to what calls the method but to `movie`, which is the object
```

A better solution is `.call()` or `.apply()` which execute ***now*** rather than prepping for the future. i.e. they execute the function for you while allowing you to specify what `this` refers to.
For both the first argument of the method always sets what `this` should refer to. The difference is for subsequent arguments –   with `.call()` you pass them in one after the other `.call(movie, arg2, arg3, arg4)` but with `.apply()` you pass them in as an array `.apply(movie, [arg2, arg3, arg4])` . Here there are no additional arguments so which we use makes no difference
```js
let { getFormattedTitle } = movie
let text = getFormattedTitle.call(movie) // now it works again. The first argument of the call method always sets what `this` should refer to. Now we've said `this` shouldn't refer to what calls the method but to `movie`, which is the object.
```

```js
let { getFormattedTitle } = movie
let text = getFormattedTitle.apply(movie) // now it works again. The first argument of the apply method always sets what `this` should refer to. Now we've said `this` shouldn't refer to what calls the method but to `movie`, which is the object.
```

![[Using arrow functions inside object methods#Use case for arrow functions *inside* object methods]]

---

Source: https://www.udemy.com/course/javascript-the-complete-guide-2020-beginner-advanced/learn/lecture/16029750#overview by [[@Maximilian Schwarzmüller]]

---
🏷 Tags: 

🖇 Related links:
[[_JavaScript Objects_]]
[[this keyword]]
[[bind method]]
[[call method]]
[[apply method]]
[[_JavaScript_]]
[[JavaScript - The Complete Guide 2023 (Beginner + Advanced)]]

