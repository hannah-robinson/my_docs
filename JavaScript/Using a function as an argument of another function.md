---
date created: 2023-07-07
last updated: 2023-07-07
programming language: javascript
library or framework:
programme:
platform:
tags: functions
---
⬆ [[JS Functions]]
If you are passing a function into a function for it to execute, don't add () to the argument. Just pass in the function name.
```js
function greet() {
	console.log('Hola!')
}

function greeter(greetFn) {
  greetFn()
}

greeter(greet)
// > Hola!

greeter(() => console.log('Guten Tag!'))
// > Guten Tag!
```

If you want to pass the value that a function returns as the argument to another function, add ()
```js
function add2Nums(a, b) {
  return a + b
}

function multiply2Nums(a, b) {
  return a * b
}

multiply2Nums(add2Nums(2, 3), 5)
// > 25
```
---
🏷 Tags: #🌱

🖇 Related links:
[[Functions]]
[[_JavaScript_]]

