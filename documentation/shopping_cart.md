# Service Portal Shopping Cart in Istanbul
New in the Istanbul release, shopping carts have been added to the Service Catalog offering in Service Portal. Following is a guide on how to enable or disable the Cart and a brief overview of how the Cart is structured.

## Enabling or Disabling the Cart

The Shopping Cart should be enabled on instances by default upon upgrading to Istanbul. That said, there are a couple of things you can do to manually turn on and off the cart.

 * Enable the "Show Add to Cart" widget option on the SC Cat Item widget. You should see an "Add to Cart" button on all catalog items that can be added to your carts. The `no_cart` field on catalog items is supported.

![Show Add to Cart option](/assets/cart/show_add_to_cart.png)

 * To display the Cart dropdown widget in your Stock Header, navigate to the Portal Editor in the SP Configuration portal. Select the SP Header Menu instance and ensure that the `enable_cart` option is set to true.

![Enable Cart header option](/assets/cart/enable_cart_header.png)

## Technical Overview

There are 3 primary components that make up the new Cart offering - the Shopping Cart widget, the `sc_cart` page, and the SPCart script include.

### SC Shopping Cart Widget

The client-side and some of the server-side logic that drives the shopping cart can be found in the SC Shopping Cart widget. This widget requires that a template be provided via a widget option - this is because although the cart in the header menu and the cart on the `sc_cart` page may look very different, they are actually both just different instances of the same widget, and are each given their own template to render: `large_shopping_cart.html` and `small_shopping_cart.html` (these templates can be found in the `sp_ng_template` table).

### SC Cart page

The full-screen dedicated cart page (which users are automatically directed to upon checkout if two-step checkout is enabled, or if users press the 'View Cart' button) can be found at ?id=sc_cart. This page contains two things - a full-screen view of the SC Shopping Cart widget (described above) and an instance of the Saved Bundles widget.

Bundles is a new concept introduced in Istanbul which allows users to take the contents of their cart and save them (including the quantities and order variables of those items). Then, later on, users can load those bundles back into their cart. This is useful for users that find themselves frequently ordering the same collection of items, such as a hiring manager that orders a new phone and laptop every time they onboard a new teammate.

To save the contents of your cart as a bundle, simply click the 'Save as Bundle' button on the `sc_cart` page, select which items in your cart you would like to include in the new bundle, and provide a name for your bundle. Later, when you'd like to load those items into your cart, simple click 'Open' next to the bundle you want to load. The contents of your bundle will be added to your cart.

![Create a New Bundle](/assets/cart/bundle.png)

### SPCart Script Include

Much of the server-side logic that drives the Cart behaviour is contained in a script include called SPCart. It is simply an extension off of the Cart script include with some additional logic baked in. By using this API, customers can create their own Cart widgets and integrations with more ease, and to add new functionality, customers can create their own script include and extend the SPCart object, in the same way that the SPCart include extends the Cart include.

# OK, but what is NOT supported?

The following things are not supported by the Service Portal shopping cart:

 * Cart Layouts - Any alternative layouts that you may have defined in the platform Service Catalog will not be respected in Service Portal.
 * Cart UI Macros and UI Formatters
