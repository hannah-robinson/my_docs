---
date created: 2024-03-06
last updated: 2024-03-06
programming language: javascript
library or framework: 
program: 
platform: shopify
tags:
  - shopify
  - shopify-functions
---

⬆ [[_Shopify_]]
Reference: https://shopify.dev/docs/api/functions/reference/cart-transform

`npm init @shopify/app@latest`
`npm run generate extension`
Choose Cart Transformer - Function

In shopify.app.toml add this access scope
```toml
[access_scopes]
access = "write_cart_transforms"
```

.graphqlqlrc.js file gives you autocomplete in the src/run.graphql file if you have an extension installed (GraphQL Language Feature Support) from GraphQL Foundation

## Create a new product
A bundle is internally registered as a product. When you merge the items in the Cart Transform function you will need to specify a parent id. So create a new bundle container product for you bundle (with 0 inventory so that the customer cannot add it to the cart themselves). Get its default variant id. You'll need it soon.

The Function will receive all items in cart. To distinguish the bundle items in the cart we can use line item properties to add a bundleId property to the items that should be bundled together.

## Create a new section for customer UI

Create a new liquid bundle-builder section to add to a page. The customers will use this to select their mix and match bundle items.

![[Pasted image 20240306204835.png]]

![[Pasted image 20240306205340.png]]


```html
{% schema %}
 {
   "name": "Bundle Builder",
   "settings": [],
   "presets": [
     {
       "name": "Bundle Builder"
     }
   ]
 }
{% endschema %}
```

Change code in src/run.graphql to:
```graphql
query RunInput {
  cart {
    lines {
      id
      quantity
      bundleId: attribute(key: "_bundleId") {
        value
      }
    }
  }
}
```

`npm run typegen`

 Change code in src/run.ts to: 
![[Pasted image 20240306205855.png]]
![[Pasted image 20240306205925.png]]
![[Pasted image 20240306205947.png]]
`npm run deploy` to update app scopes
`npm run dev` and install Function on store when prompted

---
## press `d` in CLI to open CLI's GraphiQL

Find the Function ID 
```graphql
query {
  shopifyFunctions(first: 10) {
    edges {
      node {
        id
        title
      }
    }
  }
}
```

Use it to perform a mutation
```graphql
mutation {
  cartTransformCreate(functionId: "xxxx") {
    cartTransform {
      id 
    }
    userErrors {
      message
    }
  }
}
```
---
## To add a discount
src/run.ts 
```
parentVariantId: "gid://shopify/ProductVariant/xxxxx",
price: {
  percentageDecrease: {
    value: 10,
  },
},
```

## To change the bundle name

src/run.ts 
```
parentVariantId: "gid://shopify/ProductVariant/xxxxx",
title: "My Customised Bundle Name",
price: {
  percentageDecrease: {
    value: 10,
  },
},
```

In main cart items liquid file find `item.product.title` and do this:
```html
<a href="{{ item.url }}" class="cart-iitem__name">
  {% if item.item_components.size > 0 %}
    {{ item.title}}
  {% else %}
    {{ item.product.title | escape }}
  {% endif %}
</a>
```
## To list bundle items in cart

```html
{% if item.item_components.size > 0 %}
  {{ item.title}}
{% else %}
  {{ item.product.title | escape }}
{% endif %}

{% if item.item_components.size > 0 %}
  <ul>
  {% for component in item.item_components %}
    <li>{{ component.title }}</li>
  {% endfor %}
  </ul>
{% endif %}
```
This is just a regular line item so any properties in the line item object can be displayed e.g. product image

## Add a custom image 
(to checkout only, won't show in cart - product image will though, so stick to that for consistency?) You can upload the image to files iin Shopify Admin and paste link in code.

src/run.ts 
``` graphql
parentVariantId: "gid://shopify/ProductVariant/xxxxx",
title: "My Customised Bundle Name",
price: {
  percentageDecrease: {
    value: 10,
  },
},
image: {
  url: "https://cdn.shopify.com/files/xxxxxxxxxx"
}
```



---

🏷 Tags: #🌱

🖇 Related links:
[[Shopify Functions]]
