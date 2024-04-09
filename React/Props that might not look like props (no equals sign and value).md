---
date created: 2024-05-10
last updated: 2024-05-10
programming language: javascript
library or framework: react
tags:
---
⬆ [[_React_]]

```jsx
<Input richText placeholder="Your message" />
```

`richText` is also a prop here. If it's present `richText` will be truthy, if it's not it will be falsey, so can be used like this:

```jsx
export default function Input({ richText, ...props }) {
  if (richText) {
    return <textarea {...props} />;
  }
  return <input {...props} />;
}
```

---
🏷 Tags: #🌱 #react-props

🖇 Related links:
[[React - The Complete Guide 2023 (including React Router and Redux)]] by [[@Maximilian Schwarzmüller]]

