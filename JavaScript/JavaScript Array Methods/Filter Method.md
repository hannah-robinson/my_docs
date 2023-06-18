---
last updated: 2023-06-17
programming language: javascript
library or framework:
programme:
platform:
tags: javascript, arrays, array-methods
---
⬆ [[_JS Array Methods_]]

Creates a new array with the elements of the old array that pass a given test/criteria

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
];

 const thrillerBargains = books.filter(
   (book) => book.genre == 'thriller' && book.price < 1000
 );

 console.log(thrillerBargains);
```

---
🏷 Tags: #🌱

🖇 Related links:

