---
date created: 2023-08-05
last updated: 2023-08-05
programming language: javascript
library or framework: react, nodejs
programme:
platform: shopify
tags: shopify-functions
---
⬆ [[_Shopify_]]

## Extension-only apps
Extension-only apps are custom apps that don't have embedded app pages. Because they're made up entirely of extensions, extension-only apps can be hosted on Shopify. Extension-only apps have a Shopify-populated app URL, which you can optionally change, to build embedded app pages or list your app on the Shopify App Store.

Checkout UI extensions, Shopify Functions and Post-purchase functions can all be created in extension-only apps using the	Shopify CLI.

*Source: https://shopify.dev/docs/apps/app-extensions/extension-only-apps*

## Simplified Deployment
Use Simplified Deployment (because from September 5, 2023, all apps will be automatically opted in to use simplified deployment anyway.)

*Source: https://shopify.dev/docs/apps/app-extensions/extension-only-apps*

https://shopify.dev/docs/apps/checkout/payment-customizations/getting-started

2023-08-05 

18:57 npm init @shopify/app@latest
project name: clientname-extensions
choose: Start by adding your first extension
npm run generate extension
Type of extension? Payment customization - Function
Name: conditionally-hide-payment-option
Choose JavaScript
19:08 finished above

Set up github repo

2023-08-06 17:27
cd to  root of app and npm run deploy -- --no-release
npm run shopify app config push (need to run this command every time we edit .toml file )

edit  /extensions/conditionally-hide-payment-option/input.graphql
can see what's available in  /extensions/conditionally-hide-payment-option/schema.graphql
cd into /extensions/conditionally-hide-payment-option/ and run `npm run shopify app function typegen` to generate these GraphQL types (old? now just `npm run typegen` ?)
https://shopify.dev/docs/apps/checkout/payment-customizations/getting-started

edit code in  /extensions/conditionally-hide-payment-option/src/index.js 

In partner dashboard find extensions in left panel and then turn on "Development store preview"

install on test store
go to settings > checkout on test store a bottom of page find "checkout rules" add rule and enable it
note: any console.logs appear in the dashboard


npm run dev to build it

When installing on live store remember to do the mutation in GraphiQL

---
🏷 Tags: #🌱

🖇 Related links:
