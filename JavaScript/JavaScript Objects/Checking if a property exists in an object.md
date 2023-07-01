---
date created: 2023-07-01
last updated: 2023-07-01
programming language: javascript
tags: objects
aliases: 
---
⬆ [[_JavaScript Objects_]]

You can use the `in` keyword to test if a property exists in an object
```js
const movie = {
  id: 32423, 
  info: {
    name: 'Whoami', 
    language: 'German'
  }
}

if('info'in movie) {
  // Do something
}

// or wrap in an extra pair of parenthesis and check the negative with !
if(!('info'in movie)) {
  // Do something
}
```

---

Source: https://www.udemy.com/course/javascript-the-complete-guide-2020-beginner-advanced/learn/lecture/16029740#overview by [[@Maximilian Schwarzmüller]]

---
🏷 Tags: 

🖇 Related links:
[[_JavaScript Objects_]]
[[_JavaScript_]]
[[JavaScript - The Complete Guide 2023 (Beginner + Advanced)]]