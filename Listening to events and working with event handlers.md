---
date created: 2024-03-03
last updated: 2024-03-03
programming language: javascript
library or framework: react
tags:
---
⬆ [[_React_]]

Don't use declarative vanilla JavaScript, with `.getElementById()` and .`addEventListener()` for example.

React has built in event listeners you can use e.g. `onClick`
``` jsx
 <button onClick={handleClick}>Press me</button>
```
Note it's `onClick={handleClick}` and NOT `onClick={handleClick()}`with parentheses calling the function.

If you have to add an argument to the function, put the function inside another function
``` jsx
 <button onClick={() => {handleClick}('dog')}>Press me</button>
```

But, you must handle the event in the component that manages the data that should be changed. So, below, we are going to declare this `handleSelect` function in the App component where the tabbed content displays and pass the function as a value to the component that's going to use it - the TabButton component that has the onClick event in it.

App.jsx
```jsx

function App() {
  function handleSelect(selectedButton) {
    console.log(selectedButton) // will log "dogs" when button below clicked
  }
// ...
return (
  <TabButton onSelect={() => handleSelect('dogs')}>Components</TabButton>
)
```
TabButton.jsx
``` jsx
export default function TabButtton(props) {
  return (
    <button onClick={props.onSelect}>{props.children}</button>
  )
  ```

---
🏷 Tags: #🌱

🖇 Related links:
[[React - The Complete Guide 2023 (including React Router and Redux)]]
by [[@Maximilian Schwarzmüller]]