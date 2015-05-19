OpenCart Compatibility
======================

Arastta is based on OpenCart 2.0.1

While making Arastta, we've tried our best to keep the compatibility with OpenCart extensions and themes. However, we had to break *some parts* in order to offer the best with Arastta.

Not Compatible
--------------

Extensions that **change via vQmod/OCmod** the following parts *won't work* directly with Arastta:

* Admin - Login page
* Admin - Dashboard page
* Admin - Left side menu
* Admin - Extension Installer page
* Admin - Layouts page
* Front - Account page
* Front - Checkout page (1)
* Front - Header search

(1) Not applicable for One-Page-Checkout extensions as they don't change but replace the checkout page.

Extensions that **add or remove** features to the following parts *won't work* directly with Arastta:

* Admin - Manufacturer related extensions
* Front - Manufacturer related extensions
* Front - SEO related extensions
* Front - Cache related extensions
* Front - Email related extensions

Compatible
----------

The following addons *will work* directly with Arastta:

* Themes
* Languages (OC 2.0.2)
* Payment gateways
* Shipping methods
* Modules
* Order totals
* Reports
* vQmod - OCmod

Even there are some addons that may not work, it's not hard to make them compatible as Arastta is based on the OpenCart's MVC structure so it will take just a couple of minutes for developers to make them compatible. Feel free to ask any related question via [forums](http://arastta.org/forum).