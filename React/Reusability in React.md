---
date created: 2024-02-17
last updated: 2024-02-17
programming language: javascript
library or framework: react
tags:
---
⬆ [[_React_]]

Source: https://www.youtube.com/watch?v=397259iiZ6M

>If you want to reuse jsx or markup logic, create a separate component. 
  If you want to reuse simple JavaScript logic, create a utility function.
  If you want to reuse logic with react hooks in there, create a custom .hook.

e.g. utility function to capitalise first letter of a string

utils.ts
```typescript
	export function capitalise(str: string) {
	  return str.CharAt(0).toUpperCase() + str.slice(1)
	}
```

blog.jsx
```jsx
<h1>{capitalise(item.title)}</h1>
```
```js
export function capitalise(str: string) {
  const words = str.split(" ");
  return words.map((word) => { 
    return word[0].toUpperCase() + word.substring(1); 
  }).join(" ");
}																		
```

Instead of setting the initial state of useState() to something like an array or string, you can set it as a function. The function will only run once, not every time you re-render the component, so if it only needs to run once anyway, this is better for performance.
```jsx
export function ItemList() {
  const [items, setItems] = useState(() => {
  return localStorage.getItem("items")})
  
  //...
}
```

React hooks have constraints that normal utility functions don't have, so you can't make a utility function that uses a hook. Instead you should create a custom hook.
React Hooks
- Have to be at the top of the component
- Can't be used inside conditionals

When naming your custom hook, always start the name with `use` to indicate it's a hook not a utility function.

hooks.ts
```ts
export function useLocalStorage(key: string) {
  const [value, setValue] = useState(() => {
    return JSON.parse(localStorage.getItem(key))
  });
  useEffect(() => {
    localStorage.setItem(key, JSON.stringify(value))
  }, [value, key]);
}

// Now in other files it can be important and called like this:
useLocalStorage("items")
```

---
🏷 Tags: #🌱

🖇 Related links:


