---
date created: 2023-07-07
last updated: 2023-07-07
programming language: javascript
library or framework: react
tags: 
---
⬆ [[_React_]]

A function that takes an argument is created in the parent component and passed down to the child component as props. When the child component provides the argument and executes the function, the parent  component is receiving data from the child component. In the example below the data is being passed from the child to the parent. The parent enriches the data with and id property and then passes the enriched object up to its own parent component using the same process.

Child component: ExpenseForm.js
```jsx
props.onSaveExpenseData(expenseData) // this is how we can lift the data UP to the parent component
```

Parent component: NewExpense.js
```jsx
const NewExpense = (props) => {
	const saveExpenseDataHandler = (enteredExpenseData) => {
		const expenseData = {
			...enteredExpenseData,
			id: Math.random().toString(), // Not a perfect id, but ok for this demo.
		}
		props.onAddExpense(expenseData) // We are forwarding the enriched expense data as the expenseData object to the parent component.
		console.log(expenseData)
	}
	return (
		<div className='new-expense'>
			<ExpenseForm onSaveExpenseData={saveExpenseDataHandler}></ExpenseForm>
		</div>
	)
}
```
"Grandparent" component: App.js
```jsx
function App() {
[...]
	const addExpenseHandler = (expense) => {
		console.log('In App.js')
		console.log(expense)
	}

	return (
		<div>
			<NewExpense onAddExpense={addExpenseHandler} />
			<Expenses items={expenses} />
		</div>
	)
}
```

Source: https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/25596020 by [[@Maximilian Schwarzmüller]]

---
🏷 Tags: #🌱

🖇 Related links:
[[Working with state]]
[[React - The Complete Guide 2023 (including React Router and Redux)]]