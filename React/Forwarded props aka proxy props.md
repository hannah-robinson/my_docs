---
date created: 2024-04-09
last updated: 2024-04-09
programming language: javascript
library or framework: react
tags: 
---
⬆ [[_React_]]

### Problem
When you set props (attributes) on a custom component, they are not automatically forwarded to the JSX code inside the component. This could trip you up, when you swap an HTML tag for a component e.g.
```html
<menu id="nav"> 
```
has an id of nav that can be used in CSS, but
```JSX
<Menu id="nav">
```
just has a prop called `id`, which can't be targeted with CSS.

You could forward props for id and class and so on to an element inside the component, but there might be lots of props to be forwarded and could become unwieldy.

### Solution
You can use JS's rest property: `...props` to group all remaining object properties into a new object named `props` and then JS's spread operator to use them `...props`.  The order the `props` are in doesn't matter because they are named and in an object not an array. Any `props` not already  explicitly destructured will be aded to `...props`. So, this syntax is a way to pass any additional props that are not being explicitly destructured.

e.g
```jsx
export default function Section({title, children, ...props}) {
  return (
    <section {...props}>
    <h4>{title}</h4>
      {children}
    </section>
  )
}
```

```jsx
<Section title="Dogs" id="dogs" className="dogs"> {/* all props here that are not extracted like x, y and children are merged in to the props object and added to the <nav> tag in the code snippet above tis one  */}
    <ul>
      <li>
      {/* etc. */}
<Section/> 
```

This is useful for building wrapper components like `<Card/>` `<TabButton/>` or `<Section/>`

```jsx
export default function TabButton({isSelected, children, ...props}) {
  return (
    <li>
      <button
        className={isSelected ? 'active' : undefined}
        {...props}
      >
        {children}
      </button>
    </li>
  )
}
```

```jsx
<TabButton isSelected={selectedTopic === 'components'}
onClick={() => handleSelect('components')}>
```

---
🏷 Tags: #🌱 #react-props

🖇 Related links:
[[React - The Complete Guide 2023 (including React Router and Redux)]] by [[@Maximilian Schwarzmüller]]

Videos: https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39659750#overview

https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39659752#overview

