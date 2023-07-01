---
date created: 2023-06-24
last updated: 2023-06-24
uuid: 202306241458
programming language: javascript
tags: objects
---
⬆  [[_JavaScript Objects_]]

To delete a property from an object, use the `delete` keyword.
```
delete person.age
console.log(person.age)
> undefined
```

If you  want to keep the property on the object, but just remove the value use `null`
```
person.age = null
console.log(person.age)
> null

console.log(person)
> {name: "Fred", age: null}
```
---

Source: https://www.udemy.com/course/javascript-the-complete-guide-2020-beginner-advanced/learn/lecture/16029700#overview by [[@Maximilian Schwarzmüller]]

---
🏷 Tags: 

🖇 Related links:
[[_JavaScript Objects_]]
[[_JavaScript_]]
[[JavaScript - The Complete Guide 2023 (Beginner + Advanced)]]

