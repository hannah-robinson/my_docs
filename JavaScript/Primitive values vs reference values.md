---
date created: 2023-07-07
last updated: 2023-07-07
programming language: javascript
library or framework:
programme:
platform:
tags: 
---
⬆ [[_JavaScript_]]

Primitive values can never be edited. They are thrown away and a new one is created in its place.
```js
let userMessage = 'Tudo bem?'
userMessage = 'Ça va?' // produces new string, doesn't edit old string
userMessage.concat('??')  // produces new string, doesn't edit old string

```

Reference values (objects, including arrays) can be mutated.
```js
const hobbies = ['reading', 'music']
hobbies.push('capoeira')
console.log(hobbies)
// > ['reading', 'music','capoeira'] // This is not a new array. It has the same reference/address in memory. Its contents have just been mutated.
```

---
🏷 Tags: #🌱

🖇 Related links:
