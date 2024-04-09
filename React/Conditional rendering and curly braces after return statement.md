---
date created: 2024-05-10
last updated: 2024-05-10
programming language: javascript
library or framework: react
tags:
---
⬆ [[_React_]]

In React, when you're returning JSX within a component, you don't need to wrap it in curly braces `{}` if it's directly within the `return` statement. The JSX syntax is recognized by the transpiler (like Babel) and doesn't require explicit JavaScript object notation. 

A failing code snippet (The entire ternary expression is inside curly braces `{}` which isn't necessary. ):
```js
export default function Input({ richText, ...props }) {     
  return (
  {richText ? <textarea {...props} /> : <input {...props} /> }
  )  
 } 
```

The corrected code:
```js
export default function Input({ richText, ...props }) {
  return (
  richText ? <textarea {...props} /> : <input {...props} /> 
  ); 
}
```

---
🏷 Tags: #🌱 