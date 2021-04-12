
<div><h3 class="sub-docs-type" id="bigcommerce-for-wordpress">BigCommerce for Wordpress</h3>

# Introduction
<div class="otp" id="no-index">

### On This Page
- [How It Works](#how-it-works)

</div>

BigCommerce for WordPress allows you to power content-driven WordPress storefronts with the ecommerce functionality of BigCommerce. Product data is pulled into WordPress as a custom post type, giving you the freedom to embed products in posts and pages to create a tailored shopping experience. The plugin utilizes the full suite of BigCommerce APIs, allowing shoppers to seamlessly complete a purchase end-to-end on WordPress.

You can use the BigCommerce for WordPress plugin as a building block to create an ecommerce solution that’s unique to your brand. Whether you want to link multiple WordPress storefronts to a single BigCommerce store or extend the open source plugin to create custom-made solutions, BigCommerce for WordPress makes it easy to combine the power of BigCommerce with the flexible presentation of WordPress.

## How It Works

BigCommerce for WordPress connects your WordPress site to your BigCommerce store via API, and pulls all of the relevant data into a variety of database tables, some custom, some default WordPress. Products are a post type: product data is stored in the post table and product meta is stored in the post_meta table.

Orders data is stored on the BigCommerce servers and is accessible in your WordPress site via API with custom code and via a nice UI in the BigCommerce admin.

Most store options and settings are managed inside the BigCommerce UI, including Shipping, Taxes, and Payment Gateways.

### Templating

All templates that render on the front end are found in the `/wp-content/plugins/bigcommerce/templates/public` directory. To
Override any template, create a `bigcommerce` directory in your theme and copy the template file to that directory.

For example, copy

`wp-content/plugins/bigcommerce/templates/public/single-bigcommerce_product.php`

to

`wp-content/themes/<theme-name>/bigcommerce/single-bigcommerce_product.php`

Then, edit `wp-content/themes/<theme-name>/bigcommerce/single-bigcommerce_product.php` to override the default content.

**Note**: Most templates are used for rendering content inside of the content area of your theme's template. Only a few take over the entire page template. These may need modifications to match your theme.

### Shopper Experience

When a customer visits the store, the products they see are stored locally in WordPress. A cart is optional–when the customer clicks add-to-cart, they can either be directed to a cart page or delivered directly to the checkout page.
When a shopper proceeds to checkout, they land on the BigCommerce checkout page in an embedded iframe, which can be styled to match your WordPress site. This creates a seamless experience for the shopper because they remain on your WordPress site and domain for the entire shopping experience. BigCommerce embedded checkout also allows you to leverage the built-in security and PCI-compliance of the BigCommerce checkout.

# Customizing B3

With B3, you can customize the placement of B3 app elements, customize display text, customize styling, and customize checkout configurations. You also have access to the lifecycle hooks for many B3 modules to inject your own JavaScript functions.

Additionally, you can use the B3 REST API to create, read, update, and delete items such as orders, companies, addresses, payments, sales reps, and users. This API allows you to build your own services or integrate B3 with third-party business tools such as Salesforce.

## Prerequisites for customizing B3

- [Stencil CLI](https://developer.bigcommerce.com/stencil-docs/installing-stencil-cli/installing-stencil)
- [Node.js 12 and npm](https://nodejs.org/en/download/releases/)
- [Stencil API token](https://support.bigcommerce.com/s/article/Store-API-Accounts#creating) to push BigCommerce theme via Stencil CLI
- A code editor
- Access to your BigCommerce Store Dashboard with Store Owner permissions


### Channels

Channels allow you to manage products in BigCommerce and sell them on other storefronts, like one or more WordPress sites, or in marketplaces, like Amazon and Facebook. A key concept is that the products listed on other channels are managed centrally from your BigCommerce store, so inventory is tracked neatly across all channels. This means that if all of your product ends up being sold through Amazon, your Facebook store will also be sold out.


## Customize styles

You can customize the BigCommerce styling of many B3 elements using CSS.

To specify which DOM node a B3 container mounts on, insert `window.b3themeConfig.useStyles = {}` into your theme's `assets/js/global.js` file. Within `window.b3themeConfig.useStyles = {}`, create a property that uses the B3 element name as the key and one or more comma-separated CSS declarations as the value. 

Since the CSS is written in a JavaScript object, properties with two names, like `background-color`, must be written with camel case syntax: `backgroundColor: "lightblue"`

When done, the object will resemble the following:

```jsx
window.b3themeConfig.useStyles = {
/* B3 will use the specified styles for the "Trade Partner Application" button that is appended to the secondary navigation menu */
      'tpa.entryButton': {
        fontFamily: 'Karla,Arial,Helvetica,sans-serif',
        fontSize: '1rem',
        listStyle: 'none',
        boxSizing: 'border-box',
        lineHeight: 'inherit',
        transition: 'color .15s ease',
        display: 'block',
        color: '#333',
        fontWeight: 700,
        padding: '1rem .78571rem',
        textDecoration: 'none',
        textTransform: 'uppercase',
      },
    };
```

For diagrams of B3 element names and their placements, see the [BundleB2B Developer Guide](https://developer.bundleb2b.net/storefront/containers.html).

### WordPress as a Channel

When using the WordPress plugin for BigCommerce, each connected WordPress site is considered another channel. This means that your WordPress store is aware of inventory levels, because those are monitored centrally in your BigCommerce store, and when an order is placed, it appears in the BigCommerce Order View UI along with orders received on other channels. Orders are labeled with the channel they originated from, to help you track sales data across multiple channels.

While merchants traditionally sell primarily through their BigCommerce store and supplement with channels, it is possible to mask the main BigCommerce store and treat any given channel as the primary store. This would allow you to use WordPress as your primary store.
