`.toFixed(2)`

```JavaScript
let number = 10.1234;
let roundedNumber = number.toFixed(2); // Rounds to two decimal places
console.log(roundedNumber); // Output: "10.12"
```  
  
If decimals are being shown as 12.0, and you want 12.00 (e.g. to represent money), then you can use:

`parseFloat(pointsBalanceAvailable).toFixed(2)`

or just: 

`pointsBalanceAvailable.toFixed(2)`

if the variable is already a number.