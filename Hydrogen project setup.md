1. In your Shopify admin, go to the "Sales Channels" section and add a new channel, selecting Hydrogen as the option.
2. Install the Shopify GitHub app
3. Requirements:
	1. You may need a [Shopify account(opens in a new tab)](https://www.shopify.com/) from the outset.
	2. [Node.js(opens in a new tab)](https://nodejs.org/en) version 16 or higher
	3. [npm(opens in a new tab)](https://www.npmjs.com/) version 7 or higher 
4. `npm create @shopify/hydrogen@latest`
5. From the hydrogen channel on your Shopify admin. Click “Connect existing repository” and select your repo for your hydrogen app. This will generate a PR to start continuous deployments. Once that PR is merged, oxygen will automatically create a new deployment in your production environment.

For training you can use sample data from Mock.shop (no login required). For real stores, it's best to use the store data.
## Other non-hydrogen headless setup

 Connect any web or mobile app with the headless sales channel
 existing Hydrogen React, iOS, or Android apps or create new apps 
	 
  1. Install the Headless channel  (Shopify admin and access the sales channels section. From here, create a new headless sales channel to serve as the foundation for your custom storefront.
2. Set up the storefront
    After installing the Headless sales channel, it's time to create the storefront itself. Select the headless sales channel from the list and choose the storefront you wish to work with.
  3. Manage Storefront API permissions
    Next, you need to configure the permissions for your storefront. Beside Storefront API permissions, select the "Edit" option and specify the desired permissions for your storefront. When you’ve made your selections, save the changes.