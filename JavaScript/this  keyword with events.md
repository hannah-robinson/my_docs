---
date created: 2023-07-01
last updated: 2023-07-01
programming language: javascript
tags: events, this
aliases: 
---
⬆ [[_JavaScript Objects_]]

If your method is called for you by an event listener, the browser binds `this` for you to the DOM element that triggered the event e.g. a button. So if you are not using an arrow function, `this` in the `addMovieHandler` function would refer to the button that triggered the event.
```js
const addMovieHandler = function() {
  console.log(this) // console output: <button id="add-btn">Add</button>
}

addMoviebtn.addEventListener('click', addMovieHandler) 
```

>[!warning] Arrow functions don't know `this`
>Functions created with the `function` keyword or the method shorthand have their own `this` bindings which ensure that `this` is bound to whatever is executing the function. Arrow functions don't bind `this` to anything, so `this` refers to the same thing it would refer to outside of the function (whether  or not you are in strict mode)

```js
const addMovieHandler = () => {
  console.log(this) // `this` is the window because this is an arrow function
}

addMoviebtn.addEventListener('click', addMovieHandler) 
```


---

Source: https://www.udemy.com/course/javascript-the-complete-guide-2020-beginner-advanced/learn/lecture/16029752#overview by [[@Maximilian Schwarzmüller]]

---
🏷 Tags: 

🖇 Related links:
[[this keyword]]
[[Events]]
[[Event listeners]]
[[Arrow functions]]
[[_JavaScript_]]
[[JavaScript - The Complete Guide 2023 (Beginner + Advanced)]]

