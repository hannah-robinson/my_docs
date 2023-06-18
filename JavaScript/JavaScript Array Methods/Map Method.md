---
last updated: 2023-06-17
programming language: javascript
library or framework:
programme:
platform:
tags: javascript, arrays, array-methods
---
⬆ [[_JS Array Methods_]]

Executes a function on every element in the array and creating a new array with the results.

Don't use `map` in these cases:
- You don't need a new array
- Your callback function doesn't return anything

```javascript
const books = [
  {
    title: 'Who did it?',
    genre: 'thriller',
    price: '2800'
  },
  { 
    title: 'True Love',
    genre: 'romance',
    price: '999'
  },
   { 
    title: 'Oh No!',
    genre: 'thriller',
    price: '2800'
  }
]

const titles = books.map((book) => book.title);
console.log(titles);

const pricesUSD = books.map((book) => book.price * 2);
console.log(pricesUSD);
```

---
🏷 Tags: #🌱

🖇 Related links: