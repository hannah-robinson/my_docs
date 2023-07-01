---
date created: 2023-07-01
last updated: 2023-07-01
programming language: javascript
tags: objects
aliases: 
---
⬆ [[_JavaScript Objects_]]

```js
const person = {name: "Valerii", age: 30, hobbies: ['sports', 'reading']}

const person2 = { ...person } // spread operator creates a shallow clone, so the hobbies array is just the reference value/address for the original array

const person3 = { ...person, age: 29, hobbies: [...person.hobbies] } // You can overwrite properties of the original array like this and you if can use a 2nd spread operatorr like this to clone the orignal hobbies array, making a new one with its own reference value/address

```
See also [[Object assign method]]. (Spread operator is newer and more convenient (shorter) than `Object.assign()` so use spread operator if you don't need to worry about browser support)

---

Source: https://www.udemy.com/course/javascript-the-complete-guide-2020-beginner-advanced/learn/lecture/16029732#overview by [[@Maximilian Schwarzmüller]]

---
🏷 Tags: 

🖇 Related links:
[[_JavaScript Objects_]]
[[Spread operator]]
[[_JavaScript_]]
[[JavaScript - The Complete Guide 2023 (Beginner + Advanced)]]

