---
date created: 2024-03-25
last updated: 2024-03-25
programming language: liquid
library or framework: 
programme: 
platform: shopify
tags:
---
⬆ [[_Shopify_]]
```HTML
 {% assign file_object = product.metafields.custom.manual.value %} 

  {% assign file_url = file_object.url %}

{% assign file_name_with_shopify_extension = file_url | split: '/' | last %}

{% assign file_name = file_name_with_shopify_extension | split: '?' | first %}

{% assign file_name_prettified = file_name | replace: "_", " " %}
```
---
🏷 Tags: #🌱

🖇 Related links:
[[metafields]]