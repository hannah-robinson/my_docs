---
last updated: 2023-06-17
programming language: javascript
library or framework:
programme:
platform:
tags: javascript, arrays, array-methods
---

⬆ [[_JS Array Methods_]]

Executes a function on each element in the array returning a single value.
Can be used to add up all the values in an array.

```javascript
const books = [
  {
    title: 'Who did it?',
    genre: 'thriller',
    price: '2800',
  },
  {
    title: 'True Love',
    genre: 'romance',
    price: '999',
  },
  {
    title: 'Oh No!',
    genre: 'thriller',
    price: '2800',
  },
]

const num = [0, 1, 2, 3, 4]

const sum = num.reduce((total, currentValue) => {
  console.log(`Total: ${total}`)
  console.log(`currentValue: ${currentValue}`)
  return total + currentValue
}, 0)

console.log(sum)

const reducer = (total, currentValue) => total + currentValue.price

let totalPriceAllBooks = books.reduce(reducer, 0)
console.log(totalPriceAllBooks)
```

---

🏷 Tags: #🌱

🖇 Related links:
