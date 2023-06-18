---
date created: 2023-06-18
last updated: 2023-06-18
programming language: css
library or framework:
programme:
platform:
tags: css, menu, nav, navigation, mobile-nav, responsive-menu, scroll-issue, pvrc
---
⬆ [[_CSS_]]

To allow the mobile menu to scroll up and down
```css
@media (max-width:45em) {
	.primary-navigation[data-visible="true"] {
		overflow-y: auto;
	}
}
```

To stop page from scrolling while the mobile menu is open, add a class to the body tag like this:
```css
body.mobile-menu-visible {
	overflow: hidden;
}
```

If you stop the body from scrolling, it would be a good idea to put a backdrop on the body, behind the mobile menu eg.
```html
<div class="backdrop"></div>
```

```css
#mobile-nav-overlay {
  background-color: black;
  opcacity: 0;
  position: fixed;
  z-index: 2;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  /* etc */
}

.js-open-drawer-right #mobile-nav-overlay  {
transition: opacity .4s,width 0s linear 0s;
 opcacity: .4;
}
```

---
🏷 Tags: #🌲

🖇 Related links:
[[Responsive menu]]
[[PRVC site]]
