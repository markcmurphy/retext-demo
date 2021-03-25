# Customize page containers

B3 renders client-facing pages and elements by mounting fixed containers to your BigCommerce theme using JavaScript. You can change the placement of select B3 elements by using `window.b3themeConfig.useContainers = {}` to specify which DOM node B3 mounts the container on.

To specify which DOM node a B3 container mounts on, insert `window.b3themeConfig.useContainers = {}` into your theme's `assets/js/global.js` file. Within `window.b3themeConfig.useContainers = {}`, create a property that uses the name of the B3 container as the key and the selector for the theme element it will mount on as the value. When done, the object will resemble the following:

```jsx
window.b3themeConfig.useContainers = {
	/* B3 will append the dashboard container to the first returned DOM node with a class of "page" that is a descendant of an element with the class of "container" */
	'dashboard.container': '.container .page',
}
```

For a list of B3 container names and their default placements, see the [BundleB2B Developer Guide](https://developer.bundleb2b.net/storefront/containers.html).

## Customize styles

You can customize the styling of many B3 elements using CSS.

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

      },
    };
```

For diagrams of B3 element names and their placements, see the [BundleB2B Developer Guide](https://developer.bundleb2b.net/storefront/containers.html).

## Customize display text

B3 allows you to customize display text for many of the application's elements, such as buttons, headers, and labels. 

To overwrite the default text that B3 renders, insert `window.b3themeConfig.useText = {}` into your theme's `assets/js/global.js` file. Within `window.b3themeConfig.useText = {}`, create a property for each element you would like to overwrite using B3 element names are used as keys and strings containing the new display text as values. 

When done, the object will resemble the following:

```jsx
window.b3themeConfig.useText = {
/* B3 will now use the call to action "Place Quick Order" instead of the default "Quick Order Pad" for the button that is appended to the secondary navigation menu */
	'nav.button.quickOrderPad': 'Place Quick Order',
}
```

For B3 element names and default text values, see the [BundleB2B Developer Guide](https://developer.bundleb2b.net/storefront/text.html).

# Overwriting and injecting JavaScript

B3 has lifecycle methods for many modules that allow you to inject custom JavaScript functions at different times during page render. Each supported module has the following four global keys:

For diagrams of B3 element names and their placements, see the [BundleB2B Developer Guide](https://developer.bundleb2b.net/storefront/containers.html).

## Customize display text

B3 allows you to customize display text for many of the application's elements, such as buttons, headers, and labels. 

To overwrite the default text that B3 renders, insert `window.b3themeConfig.useText = {}` into your theme's `assets/js/global.js` file. Within `window.b3themeConfig.useText = {}`, create a property for each element you would like to overwrite using B3 element names are used as keys and strings containing the new display text as values. 

When done, the object will resemble the following:

```jsx
overwrite: false,
callback() {},
beforeMount() {},
mounted() {},
```

- `overwrite` is a `boolean` that specifies whether to overwrite B3 functions for that module. Default is `false`.
- `callback()` is a `function` that will call all enclosed functions regardless of the value of `overwrite` after all other B3 code has run. Default is `noop`.
- `beforeMount()` is a `function` that calls all enclosed functions before the module renders. Default is `noop`.
- `mounted()` is a `function` that calls all enclosed functions after the module has rendered. Default is `noop`.

To overwrite and/or inject custom functions for a supported B3 module, insert `window.b3themeConfig.useJavaScript = {}` into your theme's `assets/js/global.js` file. Within `window.b3themeConfig.useJavaScript = {}`, create a property for each of the module you'd like to customize that uses the module name as the key and the four global keys above as the value. 

When done, your object will resemble the following example that demonstrates the call stack of each function:

```jsx
window.b3themeConfig.useJavaScript = {
	quickorderpad: {
        overwrite: false,
        callback() {
          console.trace("quickorderpad.callback() runs after all other quickorderpad functions")
        },
        beforeMount() {
					console.trace("quickorderpad.beforeMount() runs before quickorderpad mounts")        
},
        mounted() {
          console.trace("quickorderpad.mounted() runs after quickorderpad mounts");
}
```

The output to the browser console of the above example is the following:

![Docs%20Draft%20a609bfb87efc4b189a43113b01be4cc9/Untitled.png](Docs%20Draft%20a609bfb87efc4b189a43113b01be4cc9/Untitled.png)

For a full list of available modules, see the [BundleB2B Developer Guide](https://developer.bundleb2b.net/storefront/js.html). 

# B3 REST API

You can find instructions on how to get your B3 authentication token on the [B3 Developer Guide - RESTful API call](https://developer.bundleb2b.net/storefront/api-call.html) page. 

For the complete list of API endpoints, please see [B3 Open API (v2) specifications](https://developer.bundleb2b.net/openapi/).

# Resources

- [https://developer.bundleb2b.net/storefront/quick-start.html](https://developer.bundleb2b.net/storefront/quick-start.html)
- [https://developer.bundleb2b.net/openapi/](https://developer.bundleb2b.net/openapi/)
- [B3 Developer Guide - RESTful API call](https://developer.bundleb2b.net/storefront/api-call.html)
- [B3 Open API (v2) specifications](https://developer.bundleb2b.net/openapi/)
- [BundleB2B Developer Guide](https://developer.bundleb2b.net/storefront/text.html)
- [BundleB2B Developer Guide](https://developer.bundleb2b.net/storefront/containers.html)
- [BundleB2B Developer Guide](https://developer.bundleb2b.net/storefront/containers.html)