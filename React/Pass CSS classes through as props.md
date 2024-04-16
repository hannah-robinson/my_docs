⬆ [[_React_]]

In this example, the Button component receives a CSS a "mode" prop which is part of a class name. (In the CSS file there are classes called filled-button, text-button, etc.) The full class name can be reconstructed with a template literal: 

``` js
let cssClasses = `button ${mode}-button`;
```

Other classes can be passed through using the App.js file's "className" prop.

These various classes can be concatenated and used in the Button.js component like this:
```jsx

   let cssClasses = `button ${mode}-button`;
 
    if (className) {
      cssClasses += ' ' + className;
    }
    
    if (Icon) {
      cssClasses += " icon-button";
    }
    
    return (
<button className={cssClasses}>
```
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
          <Button mode="filled" className="danger">Filled (Default)</Button>
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
  🏷 Tags: #🌱 #react-props #react-styling

🖇 Related links:
[[React - The Complete Guide 2023 (including React Router and Redux)]] by [[@Maximilian Schwarzmüller]]

Exercise: https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/quiz/6040010#questions/20746220
