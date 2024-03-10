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

## Front end (theme code)

### Create a new product
A bundle is internally registered as a product. When you merge the items in the Cart Transform function you will need to specify a parent id. So create a new bundle container product for you bundle (with 0 inventory so that the customer cannot add it to the cart themselves). Get its default variant id. You'll need it soon.

The Function will receive all items in cart. To distinguish the bundle items in the cart we can use line item properties to add a bundleId property to the items that should be bundled together.

### Create a new section for customer UI
Create a new liquid bundle-builder section to add to a page. The customers will use this to select their mix and match bundle items.

		`/sections/mix-n-match-bundles.liquid`
```html
<form id="bundles-form">
  <div>
    <label for="group-1">Group 1</label>
    <select name="group-1" id="group-1">
      {% for product in collections.all.products %}
        {% if product.tags contains 'group-1' %}
          {% assign variant = product.selected_or_first_available_variant %}
          <option value="{{ variant.id }}">{{ product.title }} – {{ variant.price | money }}</option>
        {% endif %}
      {% endfor %}
    </select>
  </div>
  <div>
    <label for="group-2">Group 2</label>
    <select name="group-2" id="group-2">
      {% for product in collections.all.products %}
        {% if product.tags contains 'group-2' %}
          {% assign variant = product.selected_or_first_available_variant %}
          <option value="{{ variant.id }}">{{ product.title }} – {{ variant.price | money }}</option>
        {% endif %}
      {% endfor %}
    </select>
  </div>
  <button>Submit</button>
</form>

<script>
  const form = getElementById('bundles-form');

  form.addEventListener('submit', async (e) => {
    e.preventDefault();
    const group1 = getElementById('group-1').value;
    const group2 = getElementById('group-2').value;

    bundleId = new Date().getTime();

    await fetch('/cart/add.js', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        items: [
          {
            id: group1,
            quantity: 1,
            properties: {
              _bundleId: bundleId,
            },
          },
          {
            id: group2,
            quantity: 1,
            properties: {
              _bundleId: bundleId,
            },
          },
        ],
      }),
    });
    window.location.reload();
  });
</script>

{% schema %}
{
  "name": "Bundle Mix Match",
  "settings": [],
  "presets": [
    {
      "name": "Bundle Mix Match"
    }
  ]
}
{% endschema %}

```

### To list bundle items on cart page
To list out bundle components on the cart page instead of just displaying the bundle container product, use code like this.
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

If in the back end you change the container product's name main cart items liquid file find `item.product.title` and do this:
```html
<a href="{{ item.url }}" class="cart-iitem__name">
  {% if item.item_components.size > 0 %}
    {{ item.title}}
  {% else %}
    {{ item.product.title | escape }}
  {% endif %}
</a>
```

---
## Back end (Shopify Function)

`npm init @shopify/app@latest`
`npm run generate extension`
Choose Cart Transformer - Function

In shopify.app.toml add this access scope
```toml
[access_scopes]
access = "write_cart_transforms"
```

.graphqlqlrc.js file gives you autocomplete in the src/run.graphql file if you have an extension installed (GraphQL Language Feature Support) from GraphQL Foundation

Change code in `src/run.graphq`l to:
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

`cd extensions/bundles-cart-transform/`
`npm run typegen`

 Change code in `src/run.ts` to: 
 ```JavaScript
import type {
  RunInput,
  FunctionRunResult,
  CartLine,
  CartOperation
} from "../generated/api";

export function run(input: RunInput): FunctionRunResult {
  const groupedItems: Record<string, Pick<CartLine, "id" | "quantity">[] > = {};
  
  input.cart.lines.forEach(line => {
    const bundleId = line.bundleId;
    if(bundleId && bundleId.value){
      if(!groupedItems[bundleId.value]){
        groupedItems[bundleId.value] = []
      }
      groupedItems[bundleId.value].push(line);
    }
  })
  return {
    operations: [
      ...Object.values(groupedItems).map(group => {
        const mergeOperation: CartOperation = {
          merge: {
            cartLines: group.map(line => {
              return { cartLineId: line.id,
                quantity: line.quantity
              }
            }),
            parentVariantId: "gid://shopify/ProductVariant/48071724564782"  
          }
        }
        return mergeOperation
      })
    ]
  };
};
```

`npm run deploy` to update app scopes
`npm run dev` and install Function on store when prompted

---
## press `g` in CLI to open CLI's GraphiQL

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
### To add a discount
In `src/run.ts` 
```
parentVariantId: "gid://shopify/ProductVariant/xxxxx",
price: {
  percentageDecrease: {
    value: 10,
  },
},
```

### To change the bundle name

In `src/run.ts`
```
parentVariantId: "gid://shopify/ProductVariant/xxxxx",
title: "My Customised Bundle Name",
price: {
  percentageDecrease: {
    value: 10,
  },
},
```

### Add a custom image 
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
