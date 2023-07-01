---
date created: 2023-07-01
last updated: 2023-07-01
programming language: javascript
tags: this
aliases: 
---
⬆ [[_JavaScript_]]

## Don't use arrow functions as object methods

>[!warning] Don't use an arrow function for  your object method because arrow functions don't know `this`
>Functions created with the `function` keyword or the method shorthand have their own `this` bindings which ensure that `this` is bound to whatever is executing the method/function. Arrow functions don't bind `this` to anything, so `this` refers to the same thing it would refer to outside of the function (whether  or not you are in strict mode). In the case of an object's method, this is the `Window`. **But see "exception" at end of note**

See code examples: [[this keyword  in Object methods]]

## Use case for arrow functions *inside* object methods
*Inside* the object method  you might want to use an arrow function. In this e.g. it is very useful.  Because `this.cohortName` is inside an arrow function and arrows functions don't know `this`, by default `this` refers to the same thing it does in the next thing up. The next thing up is the `getCohort` method. That is executed by the `cohort` object, so `this` is the `cohort` object.
```js
const cohort = {
  cohortName: 'Whai',
  tauira: ['Kim', 'Dan'],
  getCohort() {
     this.tauira.forEach(p => console.log(p + ' – ' + this.cohortName))
  }
}
cohort.getCohort()

// in console:
// Kim – Whai 
// Dan – Whai

```

## See also

---
🏷 Tags: 

🖇 Related links:
[[this keyword]]
[[Arrow functions]]
[[this keyword  in Object methods]]
[[_JavaScript_]]

