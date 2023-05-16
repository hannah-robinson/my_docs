```javascript
// Fetch products using API
async function getProducts() {
  try {
    const response = await fetch(apiUrl);
    products = await response.json();
    displayProducts();
  } catch (error) {
    // Catch Error 
  }
}

// Check to see if scrolling near bottom of page, and load more products
window.addEventListener('scroll', () => {
  if (window.innerHeight + window.scrollY >= document.body.offsetHeight - 1000) {
    getProducts();
    console.log('load more prroducts');
  }
});

// On Load
getProducts();
```

