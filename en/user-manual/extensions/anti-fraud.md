Anti-Fraud
==========

Arastta comes with anti-fraud extension type since 1.5 version and [MaxMind](https://www.maxmind.com) (a third party anti-fraud service) extension is available out of the box.

If you are not familiar with Fraud or Anti-Fraud terminologies, this (article)[https://en.wikipedia.org/wiki/Internet_fraud] can be a good start (especially Purchase Fraud section).

As mentioned above, there is one anti-fraud extension in Arastta by default and you can enable it by opening the right configuration menu (click on the cogs icon at the top right of the admin page). Then click on the **Extensions** > **View All...** menu.

![View All Extensions](_images/view-all.jpg)

All available extensions will be listed on the page and you can look for anti-fraud extensions in this list. An easy way to find anti-fraud extensions specifically is to filtering the extensions. To filter anti-fraud extensions, first, choose **Type** from the filter area at the top of the page.

![Extension Type](_images/extension-type.jpg)

Then you can click in the search field, a dropdown list will be opened which lists all available extension types and choose **Anti-Fraud**. The page will be refreshed and all anti-fraud extensions will be displayed in the list.

You can enable **MaxMind** extension, but before using it, make sure that you fill all the fields in extension's detail page.

MaxMind Configuration
---------------------

* **Risk Score**: You can refer to MaxMind documentation for [Risk Score](https://support.maxmind.com/minfraud-faq/minfraud-services/what-is-a-riskscore/) details
* **Fraud Order Status**: Order Status will be applied to the order in your store in case the score which is set in your MaxMind account is greater than the Risk Score set in the extension options.
