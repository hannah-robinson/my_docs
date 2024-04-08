---
date created: 2024-05-08
last updated: 2024-05-08
programming language: liquid
library or framework: 
tags:
---
⬆ [[_Shopify_]]

  Use liquid to add CSS class to the last item in an array if it is in a row containing only 1 or 3 items.
  Useful: 
  `forloop.length` 
  `forloop.last`
  from [https://shopify.github.io/liquid/tags/iteration/](https://shopify.github.io/liquid/tags/iteration/)
  and
  `{%- <array> | modulo: 4 -%}`
  
``` html
{%- assign links_modulo_4 = link.links.size | modulo: 4 -%}

{% for child_link in link.links %}
<li class=" {% if forloop.length != 3 and links_modulo_4 == 3 and forloop.last %} menu-children--three-items-on-row{% endif %} {% if forloop.length != 1 and links_modulo_4 == 1 and forloop.last %} menu-children--single-item-on-row{% endif %}">
```
---
🏷 Tags: 

🖇 Related links: