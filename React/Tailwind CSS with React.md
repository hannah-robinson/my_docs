---
date created: 2024-06-12
last updated: 2024-06-12
programming language: css
library or framework: react
programme: 
platform: 
tags:
  - talwind
---
⬆ [[Styling React Apps - Static and Dynamic Styling]]

Use instructions in docs to get set up: https://tailwindcss.com/docs/guides/vite

## Add your own classes

In tailwind.config.js
adding 
```js
fontFamily: {
  title: ['"Pacifico"', 'cursive']
}
```

to get
```js
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {
      fontFamily: {
        title: ['"Pacifico"', 'cursive']
      }
    },
  },
  plugins: [],
}
```

when we already have this

```html
<link
  href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap"
  rel="stylesheet"
/>
```

in index.html

Gives you a class called
`font-title`
that you can use

## Media queries
Add prefixes to utility classes to only apply them to certain screen sizes.
`mb-8 md:mb-16`
Uses 8 unless the screen size is at least medium in which case it uses 16.

`text-xl md:text-4xl`

## Targeting pseudo selectors
Use a prefix e.g. `hover:bg-amber-500`
`text-stone-900 bg-amber-400 hover:bg-amber-500`

## Dynamic and conditional styles with Tailwind

src/components/CustomInput.jsx
```jsx
export default function CustomInput({label, invalid, ...props}) {
  let labelClasses = "block mb-2 text-xs font-bold tracking-wide uppercase"
  let inputClasses = "w-full px-3 py-2 leading-tight border rounded shadow" 

  if(invalid) {
    labelClasses +=  " text-red-400"
    inputClasses += " bg-red-100 text-red-500 border-red-300"
  } else {
    labelClasses += ' text-stone-300';
    inputClasses += ' bg-stone-300 text-gray-700'
  }

  return <p>
    <label className={labelClasses}>{label}</label>
    <input className={inputClasses} {...props} />
  </p>
}
```

src/components/AuthInputs.jsx
```jsx
<CustomInput label="Email" invalid={emailNotValid} type="email" onChange={(event) => handleInputChange('email', event.target.value)} />
<CustomInput label="Password" type="password" invalid={passwordNotValid} onChange={(event) => handleInputChange('password', event.target.value)} />
```

### Cons
- Long class lists in your JSX
- Repetition of lots of utility classes (like doing inline styles) instead of reusable classes that contain more styles each
- The class names are not unique to an element or semantic so not useful for things like JS targeting of an element
- It's global styles clash with the theme's CSS e.g. `html`, `body`, `::after` etc.
- Any style changes require editing JSX code
- You end up with lots of small wrapper components or lots of copying and pasting

## Mitigating factor with React
- You can create utility components with the Tailwind styles in them so you aren't repeating the styles, just reusing the components (This is the idea of React) EMBRACE COMPONENTS

## Pros
- If your project only uses Tailwind (i.e. is not going to be embedded in a web page with its own styles) you avoid style clashes
- Highly configurable and extensible

## Check are devs using Tailwind component libraries "correctly"
They are copying and pasting the HTML of them, maybe into just a couple of files

---
🏷 Tags: #🌱

🖇 Related links:
