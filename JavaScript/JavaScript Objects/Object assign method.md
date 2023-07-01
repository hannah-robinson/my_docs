---
date created: 2023-07-01
last updated: 2023-07-01
programming language: javascript
tags: objects
aliases: 
---
⬆ [[_JavaScript Objects_]]

Use `Object.assign()` to create a ***shallow*** clone of an object
```js
const person = {name: "Valerii", age: 30, hobbies: ['sports', 'reading']}

const person2 = Object.assign({}, person) 
```
See also: [[Use spread operator with object]]. (Spread operator is newer and more convenient (shorter) than `Object.assign()` so use spread operator if you don't need to worry about browser support)

For a deep clone see [[structuredClone method]] or [[Use spread operator with object]] note shows a way it can be done with the spread operator. (Note: spread operator used in the basic way is also a ***shallow*** clone)

```js
// Merge more than one object
const target = { a: 1, b: 2 };
const source = { b: 4, c: 5 };

const returnedTarget = Object.assign(target, source);

console.log(target);
// Expected output: Object { a: 1, b: 4, c: 5 }
// Target object itself is changed.

console.log(returnedTarget);
// Expected output: Object { a: 1, b: 4, c: 5 }

console.log(returnedTarget === target);
// Expected output: true
```
See more merge examples here: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign

---

Source: https://www.udemy.com/course/javascript-the-complete-guide-2020-beginner-advanced/learn/lecture/16029732#overview by [[@Maximilian Schwarzmüller]]

---
🏷 Tags: 

🖇 Related links:
[[_JavaScript Objects_]]
[[Spread operator]]
[[_JavaScript_]]
[[JavaScript - The Complete Guide 2023 (Beginner + Advanced)]]

