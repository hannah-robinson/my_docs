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

```js
function init() {
	function greet() {
		console.log("Kia ora!")
	}
	greet()
}

init() // calling init will cause greet to run and "Kia ora!" to be logged to the console.

// greet()
// You can't call greet here outside the init function because greet is scooped to the init function
```

---
🏷 Tags: #🌱

🖇 Related links:
[[_JavaScript_]]
[[Scope]]
