---
date created: 2024-06-12
last updated: 2024-06-12
programming language: css
library or framework: react
programme: 
platform: 
tags:
---
⬆ [[Styling React Apps - Static and Dynamic Styling]]
# Using inline styles in React
Where in HTML you would write `style=" "`
in JSX you write `style={ }`
Those braces are the React braces you use to indicate a dynamic value.
You pass an object `{}` as the dynamic value:
`style={{}}`
The styles are key-value pairs inside the object:
`style={{color: 'red', textAlign: 'center'}}`
hyphenated keys need to be write in camel case instead as this is JS `text-align` => `textAlign`

## Conditionally styling with inline styles
`style={{backgroundColor: emailNotValid ? '#fed2d2' : '#d1d5db'}}`

```jsx
function App() {
    const [colour, setColour] = useState("white")
    return (
    <div id="app">
      <h1 style={{color: colour}}>CSS is great!</h1>
      <menu>
        <li>
          <button onClick={() => setColour("green")}>Yes</button>
        </li>
        <li>
          <button onClick={() => setColour("red")}>No</button>
        </li>
      </menu>
    </div>
  );
}

export default App;
```

```jsx
export default function App() {
    const [toggle, setToggle] = useState(false)
    
    return (
        <div>
            <p style={{color: toggle ? 'red' : 'white'}}>Style me!</p>
            <button onClick={() => setToggle(!toggle)}>Toggle style</button>
        </div>
    );
}
```

## Pros
- It's just CSS code
- Styles only affect the element they are applied to
- You could have another dev work on the CSS and deliver it to you while you just work on the component. They would only need a minimal amount of access to your JSX

## Cons
- You need to style each element individually
- CSS NOT decoupled from JSX code
- You couldn't easily have another dev work on the CSS and deliver it to you while you just work on the component. 

---
🏷 Tags: #🌱

🖇 Related links:
