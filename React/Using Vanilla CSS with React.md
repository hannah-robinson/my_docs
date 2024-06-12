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
## One CSS file
Add CSS styles to index.css and `import './index.css'` in main.jsx
The build tool e.g. Vite will inject the CSS styles into the the DOM as `<style></style>`.

## Multiple CSS files
Can split the CSS into files to colocate with the components they are for.
e.g. `import './Header.css'` in `Header.jsx`
The build tool will add multiple `<style></style>` tags to the DOM.
!!!This does NOT scope the styles to the components

## Pros
- No special conventions - it's just CSS code
- CSS decoupled from JSX code
- You could have another dev work on the CSS and deliver it to you while you just work on the component. They would only need a minimal amount of access to your JSX

## Cons
- CSS not scoped to components, so CSS rules could clash across components

## Conditionally styling with classes

### Conditionally adding one class or no class
Do this ( a ternary expression with `undefined`)
`className={emailNotValid ? 'invalid' : undefined}`
NOT this
`className={emailNotValid && 'invalid'}`
because if emailNotValid is false you are setting a boolean as a class name, which is invalid and will cause an error in the browser.

### Conditionally adding dynamic classes (or not) together with hardcoded classes

Use a template literal. You can add one or more dynamic classes

`<label className={`label ${emailNotValid ? 'invalid' : ''} ${gmailAddress ? 'gmail' : ''}`}>Email</label>`

```jsx
function App() {
  const [colour, setColour] = useState("")
  return (
    <div id="app">
      <h1 className={colour}>CSS is great!</h1>
      <menu>
        <li>
          <button onClick={() => setColour("highlight-green")}>Yes</button>
        </li>
        <li>
          <button onClick={() => setColour("highlight-red")}>No</button>
        </li>
      </menu>
    </div>
  );
}

export default App;
```


---
🏷 Tags: #🌱

🖇 Related links:
