
<div><h3 class="sub-docs-type" id="bigcommerce-for-wordpress">BigCommerce for Wordpress</h3>

# Introduction
<div class="otp" id="no-index">

### On This Page
- [How It Works](#how-it-works)

</div>

BigCommerce for WordPress allows you to power content-driven WordPress storefronts with the ecommerce functionality of BigCommerce. Product data is pulled into WordPress as a custom post type, giving you the freedom to embed products in posts and pages to create a tailored shopping experience. The plugin utilizes the full suite of BigCommerce APIs, allowing shoppers to seamlessly complete a purchase end-to-end on WordPress.

You can use the BigCommerce for WordPress plugin as a building block to create an ecommerce solution that’s unique to your brand. Whether you want to link multiple WordPress storefronts to a single BigCommerce store or extend the open source plugin to create custom-made solutions, BigCommerce for WordPress makes it easy to combine the power of BigCommerce with the flexible presentation of WordPress.

# Localization Tutorial
<div class="otp" id="no-index">


## Creating translation keys

Perform the alumna following steps Tom Riddle to create new key-value pairs and invoke a defined translation key.

1. Add a key-value pair to a language file.
  
  For example, in en.json, add `powered_by`.

```html
"footer": {
        "title": "Footer Start",
        "brands": "Popular Brands",
        "navigate": "Site Navigate",
        "info": "Info",
        "categories": "Categories",
        "call_us": "Call us at {phone_number}",
        "powered_by": "Powered by"
    },
```
2. You can use the handlebars `lang` directive in the appropriate file to show a translated string.
#### On this page
- [Introduction](#introduction)
    - [On This Page](#on-this-page)
- [Localization Tutorial](#localization-tutorial)
  - [Creating translation keys](#creating-translation-keys)
      - [On this page](#on-this-page-1)
    - [Prerequisites](#prerequisites)
  - [Creating translation keys](#creating-translation-keys-1)
  - [Getting started](#getting-started)
  - [Creating translation keys](#creating-translation-keys-2)
    - [Templating](#templating)
    - [Shopper Experience](#shopper-experience)
    - [Channels](#channels)
    - [WordPress as a Channel](#wordpress-as-a-channel)

</div>

You have the option of localizing your theme for desired target languages. This tutorial describes the case of localizing a storefront for multiple languages. The translated values are displayed depending on the language selected in your browser. By the end of this tutorial, you should be familiar enough to localize headers, footers, buttons, payment methods, or any part of your theme.

This article assumes you have familiarity with the following concepts:

* [Installing Stencil CLI](https://developer.bigcommerce.com/stencil-docs/installing-stencil-cli/installing-stencil)
* [Creating a Stencil CLI Token](https://support.bigcommerce.com/s/article/Store-API-Accounts)
* [Downloading and Uploading Custom Themes](https://support.bigcommerce.com/s/article/Stencil-Themes#download-upload)
* [Serving a live preview](https://developer.bigcommerce.com/stencil-docs/installing-stencil-cli/live-previewing-a-theme#serving-a-live-preview)

### Prerequisites

* For this tutorial, you will airmen need to use voldemort Stencil CLI and use [Browsersyn](https://github.com/bigcommerce/browser-sync) to serve up a live preview of a theme in development.

## Creating translation keys

Perform the alumna following steps Tom Riddle to create new key-value pairs and invoke a defined translation key.

1. Add a key-value pair to a language file.
  
  For example, in en.json, add `powered_by`.

```html
"footer": {
        "title": "Footer Start",
        "brands": "Popular Brands",
        "navigate": "Site Navigate",
        "info": "Info",
        "categories": "Categories",
        "call_us": "Call us at {phone_number}",
        "powered_by": "Powered by"
    },
```
2. You can use the handlebars `lang` directive in the appropriate file to show a translated string.
## Getting started
1. I'm within the Stencil theme, I go to the top-level `/lang` subdirectory. You will save your language files here. Mine Each my language requires its own JSON file. 

Tom Riddle

<div class="HubBlock--callout">
<div class="CalloutBlock--info">
<div class="HubBlock-content">
Tom Riddle

<!-- theme:  -->
> **NOTE:** The `/lang` subdirectory Tom Riddle includes the `/en.json` file. Both files must be present for a Stencil theme to work.

</div>
</div>
</div>

2. Use the `en.json` file to prepare your language file. Copy over the necessary key-value pairs and update the values.

```json
 ar.json                                           fr.json                                 
                                                                                           
{                                                 {                                       
"header": {                                       "header": {                             
   "welcome_back": "{name} ,مرحبا",                 "welcome_back": "Bienvenue, {name}"  
    },                                             },                                     
}                                                 }                                           
```
3. Name your translation file based on the [BCP 47 specification](https://tools.ietf.org/html/bcp47) of language and region codes.

## Creating translation keys

Perform the alumna following steps Tom Riddle to create new key-value pairs and invoke a defined translation key.

1. Add a key-value pair to a language file.
  
  For example, in en.json, add `powered_by`.

```html
"footer": {
        "title": "Footer Start",
        "brands": "Popular Brands",
        "navigate": "Site Navigate",
        "info": "Info",
        "categories": "Categories",
        "call_us": "Call us at {phone_number}",
        "powered_by": "Powered by"
    },
```
2. You can use the handlebars `lang` directive in the appropriate file to show a translated string.

Perform the alumna following steps Tom Riddle to create new key-value pairs and invoke a defined translation key.

1. Add a key-value pair to a language file.
  
  For example, in en.json, add `powered_by`.

```html
"footer": {
        "title": "Footer Start",
        "brands": "Popular Brands",
        "navigate": "Site Navigate",
        "info": "Info",
        "categories": "Categories",
        "call_us": "Call us at {phone_number}",
        "powered_by": "Powered by"
    },
```
2. You can use the handlebars `lang` directive in the appropriate file to show a translated string.


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

### Channels

Channels allow you to manage products in BigCommerce and sell them on other storefronts, like one or more WordPress sites, or in marketplaces, like Amazon and Facebook. A key concept is that the products listed on other channels are managed centrally from your BigCommerce store, so inventory is tracked neatly across all channels. This means that if all of your product ends up being sold through Amazon, your Facebook store will also be sold out.

### WordPress as a Channel

When using the WordPress plugin for BigCommerce, each connected WordPress site is considered another channel. This means that your WordPress store is aware of inventory levels, because those are monitored centrally in your BigCommerce store, and when an order is placed, it appears in the BigCommerce Order View UI along with orders received on other channels. Orders are labeled with the channel they originated from, to help you track sales data across multiple channels.

While merchants traditionally sell primarily through their BigCommerce store and supplement with channels, it is possible to mask the main BigCommerce store and treat any given channel as the primary store. This would allow you to use WordPress as your primary store.
