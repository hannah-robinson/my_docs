---
date created: 2024-05-09
last updated: 2024-05-09
programming language: javascript
library or framework: react
tags: 
---
⬆ [[_React_]]

To make components more flexible, you can allow an HTML tag type to be set when the component is used.

e.g. In this Tabs component, we added a `buttonsContainer` prop for the instance of the component to pass back what HTML element it wants to use. The identifier for the HTML tag type needs to be passed as a string. When it is received, the value needs to be assigned to a constant which begins with a capital letter so that it can be used as a custom component. The code in the example will render this HTML:
```html
<menu>[HTML for the buttons will be here]</menu>
```

```jsx
 <Tabs buttonsContainer='menu'//more props... 
 >
```

```jsx
export default function Tabs({ children, buttons, buttonsContainer }) {
  const ButtonsContainer = buttonsContainer
  return (
    <>
      <ButtonsContainer>{buttons}</ButtonsContainer>
      {children}
    </>
  )
}
```

It could also be done like this, capitalising `ButtonsContainer` from the beginning, skipping the `const` step.

```jsx
 <Tabs ButtonsContainer='menu' //more props... 
 >
```

```jsx
export default function Tabs({ children, buttons, ButtonsContainer }) {
  // const ButtonsContainer = buttonsContainer
  return (
    <>
      <ButtonsContainer>{buttons}</ButtonsContainer>
      {children}
    </>
  )
}
```

### Note: 
If you wanted to pass a the identifier for a custom component instead of the identifier for an HTML element, you'd use curly braces instead of a string.
e.g. 
`ButtonsContainer={Menu}`
versus
`ButtonsContainer='menu'`

---
🏷 Tags:  #react-props

🖇 Related links:
[[React - The Complete Guide 2023 (including React Router and Redux)]]
by [[@Maximilian Schwarzmüller]]

Videos: https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39659756#questions/20973938