Orders
======

Managing orders
---------------

<div class="uk-alert-info uk-alert">
  <span class="uk-icon-info-circle"></span> You can switch between Basic and Advanced modes from the tabs below.
</div>
<ul class="uk-tab" data-uk-tab="{connect:'#doc-tabs', animation: 'fade'}">
    <li><a href="">Basic Mode</a></li>
    <li><a href="">Advanced Mode</a></li>
</ul>

When a customer goes through checkout, the information on their order is automatically transferred to the Orders section for you to keep track of. In the administration, you can view all of the orders made on their site, manually add orders, or edit the details of existing orders.

Viewing order details
---------------------

The Orders section is located under **Sales > Orders**. On this page, every order ever made from the store is listed in detail.

The following details are displayed for each order on the list:

- **Order ID**: a number assigned to an order by Arastta during the checkout confirmation
- **Customer**: the name of the customer that made the order.
- **Status**: update of the status of the order. After the order is initially created the status will be "Pending". The default options are Missing Orders, Canceled, Canceled Reversal, Chargeback, Complete, Denied, Expired, Failed, Pending, Processed, Processing, Refunded, Reversed, Shipped, and Voided.
- **Total**: the total price of the order.
- **Date Added**
- **Date Modified**

<ul id="doc-tabs" class="uk-switcher uk-margin">
    <li markdown="1">![orders](_images/basic-orders-1.png)</li>
    <li markdown="1">![orders](_images/orders-1.png)</li>
</ul>

With the orders included in the list, there is an option to edit, add new, delete, search, or print an invoice of an order.

### Searching for an order

The "Filter" button under Action helps you find orders based on the information specified in the blanks. It can help you locate orders by date added or customer. The "Filter" cannot search for orders by product purchased yet. For more information on the [Filter ](docs/user-manual/catalog/filters)tool, see Filter.

Manually adding/modifying an order
----------------------------------

Customer Orders will be automatically updated to the Order section after a customer confirms checkout. Though it is automatically updated, you may want to edit or add orders manually to add new information such as a gift-voucher, or add reward points. To manually add a new order, click the "**Add New**" button. To modify a pre-existing order, click "**Edit**" under Action.

### Customer details

The first section for modifying an order is called Customer Details. Typing in a customer name that has already made an account with the store will auto-complete the form by bringing up their information to fill in the blanks.

<ul id="doc-tabs" class="uk-switcher uk-margin">
    <li markdown="1">![orders customer details](_images/basic-orders-2.png)</li>
    <li markdown="1">![orders customer details](_images/orders-2.png)</li>
</ul>

### Products

In "Choose Product", begin typing the product name. A drop down list will appear with products containing that name. Selecting a product from this list will bring up specific product options for this order.

<ul id="doc-tabs" class="uk-switcher uk-margin">
    <li markdown="1">![orders products](_images/basic-orders-4.png)</li>
    <li markdown="1">![orders products](_images/orders-4.png)</li>
</ul>

### Vouchers

If a customer wants to add a gift voucher order, it will ask them for the following information.

<ul id="doc-tabs" class="uk-switcher uk-margin">
    <li markdown="1">![orders vouchers](_images/basic-orders-5.png)</li>
    <li markdown="1">![orders vouchers](_images/orders-5.png)</li>
</ul>

### Payment details

If an address has been added to the customer, select their address option under "**Choose Address**". Otherwise the customer address will need to be manually filled into the form.

<ul id="doc-tabs" class="uk-switcher uk-margin">
    <li markdown="1">![orders payment details](_images/basic-orders-3.png)</li>
    <li markdown="1">![orders payment details](_images/orders-3.png)</li>
</ul>

### Shipping details

This section tracks the shipping address for this particular order. If the shipping and payment address are the same, copy and paste the information above when adding it manually.

### Totals

Under Totals, other contributing payment factors, such as coupons and vouchers, are added/subtracted to the order total.

<div class="uk-alert uk-alert-danger uk-margin-small-left uk-margin-small-right"><i class="uk-icon-exclamation-circle"></i> Shipping and payment methods must already be set up to select a method in the order form. Otherwise, there will be nothing to select under Shipping Method and Payment Method.</div>

<ul id="doc-tabs" class="uk-switcher uk-margin">
    <li markdown="1">![orders totals](_images/basic-orders-6.png)</li>
    <li markdown="1">![orders totals](_images/orders-6.png)</li>
</ul>

The sections seen above (such as Coupon, Voucher, Rewards) are extensions that were enabled specifically for this form. There is an option to customize the order details included in the totals by editing, uninstalling, or enabling specific order total extensions.

Printing invoices
-----------------

To print an invoice, go back to the Orders page under **Sales > Orders**. Above the order list on the top right corner is the "**Print Invoice**" button. Select the order to be printed, and click "**Print Invoice**". This action will direct you to a printable page of the invoice. The invoice can be printed out and included in with the shipping.

PDF Invoices
-----------------

As an online store owner you should be aware of the importance and necessity of an efficient invoicing system and management in your eCommerce solution. So we have implemented PDF Invoice feature and from now on you and your customers can manage and download the invoices as PDF files.

Go to the Orders page under **Sales > Orders**. Above the order list on the top right corner is the "**PDF Invoice**" button. Select the order to be printed, and click "**PDF Invoice**". This action will download a PDF file including details of the selected order.

![pdf invoice](_images/pdf-invoice.png)
