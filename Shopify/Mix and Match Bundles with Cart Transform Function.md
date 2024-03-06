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
Cart Transformer - Function

In shopify.app.toml
```toml
[access_scopes]
access = "write_cart_transforms"
```

.graphqlqlrc.js file gives you autocomplete in the src/run.graphql file if you have an extension installed (GraphQL Language Feature Support) from GraphQL Foundation

A bundle is internally registered as a product. When you merge the items in the Cart Transform function you will need to specify a parent id. So create a new bundle container product for you bundle with inventory so that the customer cannot add it to the cart themselves. Get the default variant id. You'll need it soon.

The Function will receive all items in cart. To distinguish the bundle items in the cart we can use line item properties to add a bundleId property to the items that should be bundled together.

Create a new liquid bundle-builder section to 
![[Pasted image 20240306204835.png]]

![[Pasted image 20240306205340.png]]

![[Pasted image 20240306205019.png]]
In src/run.graphql
![[Pasted image 20240306205527.png]]
`npm run typegen`

src/run.ts
![[Pasted image 20240306205855.png]]
![[Pasted image 20240306205925.png]]
![[Pasted image 20240306205947.png]]
`npm run deploy` too update app scopes
`npm run dev`
Install Function on store when prompted

press `d` in CLI to open CLI's GraphiQL
Find the Function ID ![[Pasted image 20240306210426.png]]
![[Pasted image 20240306210739.png]]
to add a discount
src/run.ts 
![[Pasted image 20240306210950.png]]
to change the bundle name
![[Pasted image 20240306211221.png]]
In main cart items liquid file find `item.product.title` and do this:
![[Pasted image 20240306211455.png]]

To list bundle items in cart
![[Pasted image 20240306211927.png]]
This is just a regular line item so any properties in the line item object can be displayed e.g. product image

Add a custom image (to checkout only, won't show in cart - product image will)
![[Pasted image 20240306212213.png]]


---

🏷 Tags: #🌱

🖇 Related links:
[[Shopify Functions]]
