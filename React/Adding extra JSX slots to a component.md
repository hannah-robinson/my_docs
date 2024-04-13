---
date created: 2024-05-11
last updated: 2024-05-11
programming language: javascript
library or framework: react
tags:
---
⬆ [[_React_]]
You can pass JSX to components. This is a crucial pattern in React. This is a way to add multiple slots.

The `children` prop gives you slot to add elements to, but if you need more slots to add elements to separately from the `children` content, you can do it by adding another prop of any name. Then when use use the component, you can add JSX as the value of for that prop. The JSX should be between curly braces `{}`. 

The example below uses the prop named `bundle2` for the extra slot.

```jsx
export default function Puppies({
  title,
  bundle2,
  children,
  areGreat,
  ...props
}) {
  return (
    <section {...props}>
      <h2>{title}</h2>
      {areGreat ? <p>Puppies are great</p> : <p>Kittens are ok</p>}
      <div>{bundle2}</div>
      {children}
    </section>
  )
}
```

```jsx
<Puppies
  title='Puppies!'
  areGreat
  id='puppies'
  className='puppies_container'
  data-id='123345'
  bundle2={
    <>
      <h4>I bet you love puppies</h4>
      <p>Puppies are the best</p>
    </>
  }
>
  <h4>Puppy 1</h4>
  <h4>Puppy 2</h4>
  <h4>Puppy 3</h4>
  <h4>Puppy 4</h4>
  <Dogs active />
</Puppies>
```

---
🏷 Tags:  #react-props

🖇 Related links:
[[React - The Complete Guide 2023 (including React Router and Redux)]]
by [[@Maximilian Schwarzmüller]]

Videos: https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39659754#questions/20973938