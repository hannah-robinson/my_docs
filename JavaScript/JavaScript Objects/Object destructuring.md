---
date created: 2023-07-01
last updated: 2023-07-01
programming language: javascript
tags: objects
aliases: 
---
⬆ [[_JavaScript Objects_]]

Basic assignment
```js
const student = {
  id: 4234234,
  isEnrolled: true
};

const { id, isEnrolled } = student;

console.log(id); // 4234234
console.log(isEnrolled); // true
```

Assigning to new variable names `:`
```js
const student = { 
  id: 4234234,
  isEnrolled: true
};
  
const { id: studentNumber, isEnrolled: enrolled } = student;

console.log(studentNumber); // 4234234
console.log(enrolled); // true
```

Assigning to new variable names and providing default values `=`
```js
const { id: studentNumber = 000000, isEnrolled: enrolled = false } = { id: 4234235 };

console.log(studentNumber); // 4234235
console.log(enrolled); // false
```

Unpacking properties from objects passed as a function parameter
(c.f. passing props in [[_React_]])

```js
function studentId({ id }) {
  return id;
}

const student = {
  id: 428230,
  displayName: "Yukiko",
  fullName: {
    firstName: "Yukiko",
    lastName: "Tanaka",
  },
};


console.log(studentId(student)); // 428230
```

For more info see: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment

---

Source: https://www.udemy.com/course/javascript-the-complete-guide-2020-beginner-advanced/learn/lecture/16029736#overview by [[@Maximilian Schwarzmüller]]

---
🏷 Tags: 

🖇 Related links:
[[_JavaScript Objects_]]
[[Destructuring]]
[[_JavaScript_]]
[[JavaScript - The Complete Guide 2023 (Beginner + Advanced)]]