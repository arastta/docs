How to enable Google reCAPTCHA?
===============================

Arastta is fully compatible with Google’s  reCAPTCHA and we encourage you to enable it on your Store as a measure against bot.

To enable and configure reCAPTCHA for your store, follow the steps provided below:

###STEP 1: Generate the Public and Private keys

In order to activate reCAPTCHA you will need to generate two keys. They are randomly generated strings called **Public** and **Private key**.  You can generate them on the official [reCAPTCHA](http://www.google.com/recaptcha) website.

Select the Get reCAPTCHA option at the top right corner.

![Getting recaptcha](_images/google-recaptcha-1.png)

This will direct you to a registration form that you must fill to continue:

![Registering a new website to be serviced by recaptcha](_images/google-recaptcha-2.png)

**Label**: This will make it easier to identify the website

**Domains**: Put your domain name here. Your registration will be restricted to the domains you enter in this field.

**Owners**: The email account of the owner of the domain.

![Generating the private and public keys](_images/google-recaptcha-3.png)

Once you have entered the correct information hit the **Register** button. Now you will be presented with the newly created keys.

###STEP 2: Enable reCAPTCHA

Login to the admin dashboard of your Arastta website and navigate to the **System>Settings** section of the main admin panel.

![Navigating to the Settings Menu in Arastta](_images/google-recaptcha-4.png)

Access the **Security** tab and scroll to the bottom of the page.

![Pasting the keys in order to Enable repcaptcha](_images/google-recaptcha-5.png)

Copy your **Public** key in the **Site key** field and your **Private** key to the **Secret key** field and change the status to **Enable**.

Congratulations, your Arastta store is now safer against bots and abuse thanks to Google’s human verification service reCAPTCHA.