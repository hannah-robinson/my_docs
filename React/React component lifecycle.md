---
date created: 2024-03-03
last updated: 2024-05-08
programming language: javascript
library or framework: react
tags:
---
⬆ [[_React_]]

By default, a React component will only be evaluated once. If it has bits of UI that you want to update (e.g. when a user clicks a button), you need to use the `useState()` hook for those values instead of declaring them as normal JavaScript variables.

When a `useState()`hook, changes a "variable"'s state,  ALL the code in that component function is reevaluated (as is the code of components nested inside it). This is one reason to split components.

---
🏷 Tags: #🌱

🖇 Related links:
[[React - The Complete Guide 2023 (including React Router and Redux)]]
by [[@Maximilian Schwarzmüller]]