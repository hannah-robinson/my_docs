---
date created: 2024-06-12
last updated: 2024-06-12
programming language: css
library or framework: react
programme: 
platform: 
tags:
---
⬆ [[Styling React Apps - Static and Dynamic Styling]]

Not a default browser or JS solution. You use the build tool to do. the build tool transforms your class names to names that will be unique per file. 
`Header.module.css` the module keyword is a signal to the build process.

`import classes from ./Header.module.css`
You don't have to call it classes when you import it, but you do have to call it something and that's a logical name.

`<p className={classes.paragraph}>`

Can also apply it conditionally
`<p className={1 === 1 ? classes.paragraph : undefined}>`

and use template literals just like with Vanilla CSS
`<label className={`label ${emailNotValid ? 'classes.invalid' : ''} ${gmailAddress ? 'classes.gmail' : ''}`}>Email</label>`

## Pro
It's scoped to the component

## Con 
You may end up with lots of small files

---
🏷 Tags: #🌱

🖇 Related links:
