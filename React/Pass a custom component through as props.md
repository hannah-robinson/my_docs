---
date created: 2024-04-17
last updated: 2024-04-17
programming language: javascript
library or framework: react
tags:
---
⬆ [[_React_]]

HomeIcon and PlusIcon are custom components (each containing and SVG inside a React functional component). They are imported into App.js and passed as props to Button.js, where they are render like this: `<PlusIcon/>` 

Button.js
```JSX
export default function Button({ Icon, mode = "filled", children, className, ...props }) {
    
    let cssClasses = `button ${mode}-button`;
 
    if (className) {
      cssClasses += ' ' + className;
    }
    
    if (Icon) {
      cssClasses += " icon-button";
    }

    
    return (
 <button className={cssClasses} {...props}>
  { Icon && (<span className="button-icon"><Icon /></span>)}
   <span>{children}</span>
 </button>
)
}
// Note that <Icon/> is used and not {Icon}

```

App.js
```JSX
import Button from './Button';
import HomeIcon from './HomeIcon';
import PlusIcon from './PlusIcon';

function App() {
  return (
     <div id="app">
      <section>
        <h2>Filled Button (Default)</h2>
        <p>
          <Button>Default</Button>
        </p>
        <p>
          <Button mode="filled">Filled (Default)</Button>
        </p>
      </section>
      <section>
        <h2>Button with Outline</h2>
        <p>
          <Button mode="outline">Outline</Button>
        </p>
      </section>
      <section>
        <h2>Text-only Button</h2>
        <p>
          <Button mode="text">Text</Button>
        </p>
      </section>
      <section>
        <h2>Button with Icon</h2>
        <p>
          <Button Icon={HomeIcon}>Home</Button>
        </p>
        <p>
          <Button Icon={PlusIcon} mode="text">
            Add
          </Button>
        </p>
      </section>
      <section>
        <h2>Buttons Should Support Any Props</h2>
        <p>
          <Button mode="filled" disabled>
            Disabled
          </Button>
        </p>
        <p>
          <Button onClick={() => console.log('Clicked!')}>Click me</Button>
        </p>
      </section>
    </div>
  );
}

export default App;

```

---
🏷 Tags: #🌱 #react-props

🖇 Related links:
[[React - The Complete Guide 2023 (including React Router and Redux)]] by [[@Maximilian Schwarzmüller]]

Exercise: https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/quiz/6040010#questions/20746220
