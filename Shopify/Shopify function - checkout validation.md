---
date created: 2023-06-14
last updated: 2023-06-14
programming language: javascript, rust, graphql
library or framework:
programme:
platform: shopify
tags: shopify-functions, shopify, checkout-validation
---
⬆ [[Shopify Functions]]

Check if customer is known user. If not, don't allow purchases over a certain amount.

1. Create a development store 
	1. Choose "to test and build"
	2. Choose Developer Preview, Checkout Extensibility
	3. Start with test data
2. In a terminal with Shopify CLI installed:
	1. `cd ~/repos/shopify`
	2. `npm init @shopify/app@latest`
	3. Name app `my-app`
	4. Choose (1) node
	5. `cd ./my-app`
	6. `npm run dev`  helps with initial setup connecting it to the dev store
	7. authenticate
	8. Choose "yes, create it as a new app"
	9. App name `my-app`
4. Inside store follow prompt to install new app
5. Install Pre-release CLI version to the project `npm install @shopify/cli@pre @shopify/app@pre`
6. Install extension to app `npm run shopify app generate extension`
	1. Choose "Discounts and Checkout"
	2. Choose "Function - Cart and Checkout Validation"
	3. Set name for extension "checkout-validation"
	4. Choose JavaScript (developer preview) template
7. Open project in VSCode and go to /extensions/checkout-validation/input.graphql
8. Replace contents of file with code from Shopify tutorial: https://shopify.dev/docs/apps/checkout/validation/server-side
```graphql

query Input {
  cart {
    buyerIdentity {
      customer {
        numberOfOrders
      }
    }
    cost {
      subtotalAmount {
        amount
      }
    }
  }
}

```
10. Go into  /extensions/checkout-validation/ and run  `npm run shopify app function typegen` to generate these GraphQL types
11.    In /extensions/checkout-validation/source/index.js replace code code from Shopify tutorial: https://shopify.dev/docs/apps/checkout/validation/server-side
```js
// @ts-check
// Use JSDoc annotations for type safety
/**
* @typedef {import("../generated/api").InputQuery} InputQuery
* @typedef {import("../generated/api").FunctionResult} FunctionResult
*/
// The @shopify/shopify_function package will use the default export as your function entrypoint
export default /**
* @param {InputQuery} input
* @returns {FunctionResult}
*/
  (input) => {
    // The error
    const error = {
      localizedMessage:
          "There is an order maximum of $1,000 for customers without established order history",
      target: "cart"
    };
    // Parse the decimal (serialized as a string) into a float.
    const orderSubtotal = parseFloat(input.cart.cost.subtotalAmount.amount);
    const errors = [];

    // Orders with subtotals greater than $1,000 are available only to established customers.
    if (orderSubtotal > 1000.0) {
      if (input.cart.buyerIdentity && input.cart.buyerIdentity.customer) {
        // If the customer has ordered less than 5 times in the past,
        // then treat them as a new customer.
        if (input.cart.buyerIdentity.customer.numberOfOrders < 5) {
          errors.push(error);
        }
      } else {
        errors.push(error);
      }
    }

    return { errors };
  };

```
12.  Go back up to root directory my-app/ `npm run deploy`
	1. Choose yes and yes for the 2 questions
	2. Compiled to Shopify already
13. From the Shopify admin, go to **Settings** > **Checkout**.
14. In **Checkout Rules** section of the page click **Add rule**.  A dialog opens and shows the `checkout-validation` function
15. Select the function, set the status to **Active**, and click **Add Template**.

---

🏷 Tags: #🌱

🖇 Related links:
[[Shopify]]
[[GraphQL]]
[[Shopify Functions]]
[[_JavaScript_]]
