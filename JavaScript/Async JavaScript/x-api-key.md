
```javascript
return fetch(url, {
    mode: 'cors', 
    headers: {
      'x-api-key': 'xxx',
      'User-Agent' : 'My-App',
      'Accept': '*/*',
    },
  })
  .then(response => response.json())
  .catch(error => console.log('Error while fetching:', error))
```
