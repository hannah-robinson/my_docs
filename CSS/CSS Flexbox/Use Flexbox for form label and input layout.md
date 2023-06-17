---
last updated: 2023-06-17
programming language: css
library or framework:
programme:
platform:
tags: css, flexbox, forms
---
⬆  [[_Flexbox_]]

``` HTML
<div class="form-group">
  <label>Search</label>
  <input type="text">
  <button type="submit">Search</button>
</div>
```

``` CSS
.form-group {
  display: flex;
}

.form-group input {
  flex-grow: 1;
  flex-shrink: 1;
}

.form-group label { 
  border: 2px solid #BEBEBE;
  padding: 10px;
}
```

---
🏷 Tags: #🌲

🖇 Related links:
[[Forms]]
[[_CSS_]]
[[_Flexbox_]]