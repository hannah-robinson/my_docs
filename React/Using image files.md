---
date created: 2024-03-03
last updated: 2024-03-03
programming language: javascript
library or framework: react
tags:
---
⬆ [[_React_]]
Images should be imported into the file where they will be used, like this:

```jsx
import catImg from './assets/cat.png'
import dogImg from './assets/dog.png'
import horseImg from './assets/horse.png'
```
Then use the same name you used in the import statement when you refer to the image file path:

e.g. in Header.jsx
```jsx
 <header>
    <img src={dogImg} alt='dog' />
    <h1>Dogs</h1>
      <p>
        {description} 
      </p>
    </header>
```

e.g. in data.js (to later be imported into and mapped over in a component file)
```jsx
export const ANIMALS = [
  {
    image: dogImg,
    title: 'Dog',
    description:
      'The best animal friend',
  },
```

Doing this makes sure image is included where it's needed when React packages things up for deployment.

---
🏷 Tags: #🌱

🖇 Related links:
[[React - The Complete Guide 2023 (including React Router and Redux)]]
by [[@Maximilian Schwarzmüller]]