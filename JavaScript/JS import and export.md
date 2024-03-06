---
date created: 2023-07-04
last updated: 2023-07-04
programming language: javascript
tags: import, export, modules
aliases: 
---
⬆ [[_JavaScript_]] 

For import and export to work you must be using `type="module"`
```
<script> src="" type="module"</script>
```
(You don't need it in React because when it builds, it doesn't use import and export in the built code (better browser compatibility))

Named exports
```js
// util.js
export let apiKey = "sdhsaiohd&i"
export let abc = "xyz" // if you're not using default you can export as many things as you want in the same file.

// app.js
import { apiKey, abc } from './util.js' // in Vanilla JS the file ext is added, in React it's ommitted (due to build process adding it for us)
```

default export (common in React)
```js
// util.js
export default "sdhsaiohd&i"
// if you're using default you can only export one thing from the file and you shouldn't use let/const/var. You just export a value with no name.

// app.js
import apiKey from './util.js' // when importing default, don't use curly braces, do assign a name.
```
You can mix named exports with default exports, as long as you only have one default
```js
// util.js
export default "dsadhals"
export let apiKey = "sdhsaiohd&i"
export let abc = "xyz" // if you're not using default you can export as many things as you want in the same file.
```

Importing as an object
```js
// util.js
export default "dsadhals"
export let apiKey = "sdhsaiohd&i"
export let abc = "xyz" 

// app.js
import * as util from './util.js'
console.log(util.apiKey)
console.log(util.abc)
console.log(util.default)
```

Assigning aliases
```js
// util.js
export default "dsadhals"
export let apiKey = "sdhsaiohd&i"
export let abc = "xyz" 

// app.js
import { apiKey, abc as content } from './util.js' 
console.log(content)
```

---

Source: https://www.udemy.com/course/javascript-the-complete-guide-2020-beginner-advanced/learn/lecture/16029752#overview by [[@Maximilian Schwarzmüller]]

---
🏷 Tags: #🌱 

🖇 Related links:
[[this keyword]]
[[Events]]
[[Event listeners]]
[[Arrow functions]]
[[_JavaScript_]]
[[JavaScript - The Complete Guide 2023 (Beginner + Advanced)]]

