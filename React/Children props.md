---
date created: 2024-03-03
last updated: 2024-03-03
programming language: javascript
library or framework: react
tags:
---
⬆ [[_React_]]

All components have a props object, if you don't set any props the object will be fairly empty, but will always contain props.children, which is passed to every custom component by React. The content between an opening and closing component tag is used as a value for the children prop (could be text or a complex JSX structure.)

```jsx
export default function TabButtton(props) {
  return (
    <li>
      <button onClick={props.onSelect}>{props.children}</button>
    </li>
  )
}
```
or
```jsx
export default function TabButtton({children}) {
  return (
    <li>
      <button onClick={props.onSelect}>{children}</button>
    </li>
  )
}
```

---
🏷 Tags: #🌱 #react-props

🖇 Related links:
[[React - The Complete Guide 2023 (including React Router and Redux)]]
by [[@Maximilian Schwarzmüller]]