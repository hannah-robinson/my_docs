### Prerequisites
Before you begin, useful background knowledge for creating Shopify Functions:
- JavaScript (or preferably TypeScript)
- Node.js
- GraphQL

For your development environment setup you need to have installed: 
- [Node.js](https://nodejs.org/en/download) 16 or higher
- [npm](https://www.npmjs.com/get-npm) 
- If you previously installed Shopify CLI, then make sure you're using the [latest version](https://shopify.dev/docs/apps/tools/cli#upgrade-shopify-cli).

- You've created a [Partner account](https://www.shopify.com/partners).
- You've created a [development store](https://shopify.dev/docs/apps/tools/development-stores#create-a-development-store-to-test-your-app).

### Creating the Extension-only App to build your Function in
In your terminal, create a new folder for the project  and `cd` into that folder, then run:
`npm init @shopify/app@latest`
Then follow the prompts that will appear in your terminal:
- Name the app using the convention `<clientname>-extensions` e.g. `xyz-extensions`
- Choose: "Start by adding your first extension"

Then, `cd` into `/xyz-extensions` and run:
`npm run generate extension`
Then follow the prompts:
- This guide is for a client's first extension, so choose, "Yes, create it as a new app"
- Give the same app name again e.g. `xyz-extensions`
- Choose the option for  the extension you are creating. In this example we are creating a "Payment customisation - Function"
- Choose a name for the Function e.g.: `conditionally-hide-payment-options`
- Choose JavaScript (TypeScript would be the better choice if your team knows it)

Open the `xyz-extensions` app in your code editor. Shopify CLI should have created a `.gitignore` file for you. Double check that the `.env `file(s) in the project are listed in the `.gitignore `file. Shopify should have done this by default. (`.env` files contain secrets that should not be uploaded to GitHub, even in a private repo)

Set up a private GitHub repo using the naming convention "clientname-extensions" for the repo name e.g. `xyz-extensions` and upload your project files (all the files for the whole app, not just the Function).

In the terminal:
`cd` to the root of your app and run: 
`npm run deploy -- --no-release`
Choose: "Yes, create this new version"

Then run:
`npm run shopify app config push `
(You'll need to run this command again after every time you edit the `.toml` file)

### Exploring the scaffolded code
Now you are ready to write the code for your extension. Open the terminal in your code editor and `cd` into your Function directory, which you'll find in the `/extensions` directory e.g. mine is `/extensions/conditionally-hide-payment-options/`

Important files that you will work with are:
- `/extensions/conditionally-hide-payment-options/src/index.js`
- `/extensions/conditionally-hide-payment-options/src/index.test.js`
- `/extensions/conditionally-hide-payment-options/input.graphql`
- And you might use this one for reference:
 `/extensions/conditionally-hide-payment-options/schema.graphql`

### GraphQL
In your code editor, open:  `/extensions/conditionally-hide-payment-options/input.graphql`
You can see what's available to you from GraphQL in this app in file:  `/extensions/conditionally-hide-payment-options/schema.graphql`
Shopify provides helpful tutorials for a basic version of some of its Function types. The relevant tutorial for this type of Function is here: https://shopify.dev/docs/apps/checkout/payment-customizations/getting-started 
Replace the contents of the `input.graphql` file with this code:
```graphql
query Input {
  cart {
    cost {
      totalAmount {
        amount
      }
    }
  }
  paymentMethods {
    id
    name
  }
}
```

Now `cd` into `/extensions/conditionally-hide-payment-options/` and run: 
`npm run shopify app function typegen` 
to generate these GraphQL types

### Writing code for the Function's logic
In the `/src/index.js` file you'll write your logic using TypeScript or JavaScript depending on how you set your app up. The Shopify tutorial for writing payment Functions, provides boilerplate code for a Function where the Cash on Delivery payment method is hidden if the cart total is over $100. You can use this as an example and a starting point.  https://shopify.dev/docs/apps/checkout/payment-customizations/getting-started Here is the code for the `/src/index.js` from Shopify's tutorial:
```js
// @ts-check

// Use JSDoc annotations for type safety
/**
* @typedef {import("../generated/api").InputQuery} InputQuery
* @typedef {import("../generated/api").FunctionResult} FunctionResult
* @typedef {import("../generated/api").HideOperation} HideOperation
*/

/**
* @type {FunctionResult}
*/
const NO_CHANGES = {
  operations: [],
};

// The @shopify/shopify_function package will use the default export as your function entrypoint
export default /**
    * @param {InputQuery} input
    * @returns {FunctionResult}
    */
  (input) => {
    // Get the cart total from the function input, and return early if it's below 100
    const cartTotal = parseFloat(input.cart.cost.totalAmount.amount ?? "0.0");
    if (cartTotal < 100) {
      // You can use STDERR for debug logs in your function
      console.error("Cart total is not high enough, no need to hide the payment method.");
      return NO_CHANGES;
    }

    // Find the payment method to hide
    const hidePaymentMethod = input.paymentMethods
      .find(method => method.name.includes("Cash on Delivery"));

    if (!hidePaymentMethod) {
      return NO_CHANGES;
    }

    // The @shopify/shopify_function package applies JSON.stringify() to your function result
    // and writes it to STDOUT
    return {
      operations: [{
        hide: {
          paymentMethodId: hidePaymentMethod.id
        }
      }]
    };
  };
```
The logic for the Function we are making today is more complex. It contains logic for four different payment methods, each hidden based on separate conditions.
```js
// @ts-check
// Use JSDoc annotations for type safety
/**
 * @typedef {import("../generated/api").InputQuery} InputQuery
 * @typedef {import("../generated/api").FunctionResult} FunctionResult
 * @typedef {import("../generated/api").HideOperation} HideOperation
 */
/**
 * @type {FunctionResult}
 */
const NO_CHANGES = {
  operations: [],
}

const PAYMENT_METHODS_TO_HIDE = []

// The @shopify/shopify_function package will use the default export as your function entrypoint
export default /**
 * @param {InputQuery} input
 * @returns {FunctionResult}
 */

(input) => {
  // Get the cart total from the function input
  const cartTotal = parseFloat(input.cart.cost.totalAmount.amount ?? '0.0')
  
  // Set up Buy Now Pay Later (BNPL) availability conditions
  let afterpay = true
  let laybuy = true
  let zip = true
  let klarna = true

  if (cartTotal < 100 || cartTotal > 150000) { afterpay = false; }
  if (cartTotal< 12000 || cartTotal > 150000) { laybuy = false; }
  if (cartTotal < 5000 || cartTotal > 150000) { zip = false; }
  if (cartTotal < 100 || cartTotal > 200000) { klarna = false; }

  if (cartTotal < 100) {
    // You can use STDERR for debug logs in your function
    console.error(
      'Cart total is not high enough, no need to hide the payment method.'
    )
    return NO_CHANGES
  }

  // Find the payment methods to hide
  const hideAfterpayPaymentMethod = input.paymentMethods.find((method) =>
    method.name.includes('Afterpay')
  )

  const hideLaybuyPaymentMethod = input.paymentMethods.find((method) =>
  method.name.includes('Laybuy')
  )

  const hideZipPaymentMethod = input.paymentMethods.find((method) =>
  method.name.includes('Zip')
  )

  const hideKlarnaPaymentMethod = input.paymentMethods.find((method) =>
  method.name.includes('Klarna')
  )
  
  if(hideAfterpayPaymentMethod) {
    PAYMENT_METHODS_TO_HIDE.push({
      hide: {
        paymentMethodId: hideAfterpayPaymentMethod.id,
      }
    })
  }

  if(hideLaybuyPaymentMethod) {
    PAYMENT_METHODS_TO_HIDE.push({
      hide: {
        paymentMethodId: hideLaybuyPaymentMethod.id,
      }
    })
  }

  if(hideZipPaymentMethod) {
    PAYMENT_METHODS_TO_HIDE.push({
      hide: {
        paymentMethodId: hideZipPaymentMethod.id,
      }
    })
  }

  if(hideKlarnaPaymentMethod) {
    PAYMENT_METHODS_TO_HIDE.push({
      hide: {
        paymentMethodId: hideKlarnaPaymentMethod.id,
      }
    })
  }

  // The @shopify/shopify_function package applies JSON.stringify() to your function result
  // and writes it to STDOUT
  return {
    operations: PAYMENT_METHODS_TO_HIDE 
  }
}
```
### Preview the function on a development store
To start app preview, in the terminal, `cd` into the app root and run:
`npm run dev`
Follow the prompts to choose which dev store you want to view your project on.
Press `p` to preview in your browser
Your browser will open, you'll be prompted to login/authenticate and then to install the app on the dev store.

Go  to https://partners.shopify.com/
Choose "Apps" from the lefthand panel
Click on the app you've just created
In the lefthand panel choose "Extensions"
In the "Development store preview" section, click the "Turn on" button

### Create the payment customisation with GraphiQL
Create a payment customisation on the dev store where you installed the app. You can do this using the [`paymentCustomizationCreate`](https://shopify.dev/docs/api/admin-graphql/current/mutations/paymentCustomizationCreate) GraphQL mutation.

First, install the [Shopify GraphiQL app](https://shopify-graphiql-app.shopifycloud.com/) on the dev store. (Shopify's instructions say that if GraphiQL is already installed, you should do so again to select the necessary access scopes for payment customisations.) Select the `read_payment_customizations` and `write_payment_customizations` access scopes for the Admin API.

In the GraphiQL app, in the **API Version** field, select the **2023-07** version.
Find the ID of your deployed function in the `.env` file at the root of your app. Your function's ID is the value of the `SHOPIFY_PAYMENT_CUSTOMIZATION_ID` environment variable that's defined in the `.env` file. (The actual name of this variable will depend on what you named your Function e.g. this time my variable is called: `SHOPIFY_CONDITIONALLY_HIDE_PAYMENT_OPTIONS_ID`)
Execute the following mutation and replace `YOUR_FUNCTION_ID_HERE` with the ID of your function:
```grapql
mutation {
  paymentCustomizationCreate(paymentCustomization: {
    title: "Hide payment method by cart total",
    enabled: true,
    functionId: "YOUR_FUNCTION_ID_HERE",
  }) {
    paymentCustomization {
      id
    }
    userErrors {
      message
    }
  }
}
```
You should receive a GraphQL response that includes the ID of the created payment customisation. If you get errors, check step 3 of Shopify's tutorial for suggestions on how to fix them: https://shopify.dev/docs/apps/checkout/payment-customizations/getting-started#step-3-create-the-payment-customization-with-graphiql

Note: You will need to repeat everything in this GraphiQL section on the live store later when you install the app there.

### Activate the Function on the dev store
From the Shopify admin, go to **Settings** > **Payments**.
Check the **Payment customisations** section. You should find the **Hide payment method by cart total** payment customisation that you created with GraphiQL.
Click **Activate**.


After any changes:
`npm run dev `
again to build it

When installing on live store remember to do the mutation in GraphiQL

note: any console.logs appear in the dashboard 

