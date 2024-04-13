---
date created: 2024-05-09
last updated: 2024-05-09
programming language: javascript
library or framework: react
tags: 
---
⬆ [[_React_]]

In cases like this one where we [[Allow an HTML tag type to be set when the component is used]], we might want to set a default value so that we are not forced to give a value every time we use the component.

```jsx
export default function Tabs({ children, buttons, ButtonsContainer = 'menu' }) {
  return (
    <>
      <ButtonsContainer>{buttons}</ButtonsContainer>
      {children}
    </>
  )
}
```

### Note: 
If you wanted to use the identifier for a custom component instead of an identifier for an HTML element, you'd use this syntax instead, not a string:
e.g. 
`ButtonsContainer= Menu`
versus
`ButtonsContainer='menu'`

---
🏷 Tags:  #react-props

🖇 Related links:
[[React - The Complete Guide 2023 (including React Router and Redux)]]
by [[@Maximilian Schwarzmüller]]

Videos: https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39659758#questions/20973938