---
date created: 2024-01-21
last updated: 2024-01-21
programming language: 
library or framework: 
programme: 
platform: shopify
tags:
---
⬆ 
## Getting started

⚠️ Make sure you do your work on a feature branch and do all your testing on that feature branch. Don't merge your branch into master until you have approval for push live.

```bash
node -v
nvm install --lts

npm run shopify auth logout
# log out of Shopify in terminal in case you are logged in to the wrong account. Later when prompted by the CLI, log in to the Shopify partner account that owns the app you are about to work on.

git clone https://github.com/hannah-robinson/workflow-testing-app.git
cd workflow-testing-app
npm i # to install all the dependencies in the package-lock.json
npm run shopify version # to check that the npm install installed Shopify CLI correctly

git checkout -b feature-branch 
# DON'T MERGE YOUR BRANCH INTO MASTER UNTIL YOU HAVE APPROVAL FOR PUSH LIVE

# in app's root directory
npm run shopify app generate extension
# Follow the onscreen prompts in the terminal and choose:
# ?  Create this project as a new app on Shopify?
# ✔  No, connect it to an existing app
# ?  Which existing app is this for?   Type to search...
# > <app that has shopify.app.toml after it> (shopify.app.toml)

npm run dev
# You can see in the shopify.app.toml file (and the app's Confluence doc) which store is being used as the dev store for app testing. 
#  When you run this command, Shopify CLI will create the app's `.env` file for you and populate its contents
```

## Deploying

Get approval from PM/AM for push live. Only after you have approval for push live can you merge your work into master. 
After you've merged into master, deploy as below.

`cd` to the root of your app and run: 
`npm run deploy -- --no-release`
Follow the onscreen prompts in your terminal.
⚠️ NOTE: Doing this will deploy directly to all the instances of the live app affecting every store the app is installed on and will deploy ALL extensions in the master branch no matter whether or not they are ready for deployment. This is one reason it's so important to develop and test your extension on a feature branch

Update the Confluence page for this app with the name of the new extension and a description of what it does. If you've changed anything in any other extensions in the app, update these details too.

Some related Shopify documentation:
[https://shopify.dev/docs/apps/tools/cli/existing](https://shopify.dev/docs/apps/tools/cli/existing)

---
🏷 Tags: #🌲 

🖇 Related links: [[Deploying Shopify Functions and UI Extensions]]
[https://shopify.dev/docs/apps/tools/cli/existing](https://shopify.dev/docs/apps/tools/cli/existing)

