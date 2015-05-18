Security
========

Arastta is not responsible for the securing your website, therefore it is up you to ensure your server's level of safety. The following suggestions aim to improve your Arastta store's security.

These additional steps can be taken immediately after Arastta is installed to your server; or whenever you store becomes active. See [Installation](docs/installation) for more information on how to install your Arastta store.

Delete the install folder
-------------------------

Deleting the install folder is advised by Arastta immediately. Arastta will delete the install folder after he installation is done, but even if it still exists there then Arastta will warn you in the administration.

Directory protection
--------------------

### Admin folder

The admin directory is where you have access to your store's administration. People with access to your store administration will have access your editing your products, customer information, store settings, and more valuable information. Therefore, it is very important that the admin login be difficult to find and access.

#### Rename admin

Renaming the admin directory to something unrelated to the the admin is necessary to prevent unwanted eyes from discovering it's location. You can access your admin login through entering your store's location, then the path to the admin. For example, if the admin folder was changed to "cookiemonster", the admin login would be at "www.yourstore.com/cookiemonster".

#### .htaccess & .htpasswd

A .htaccess and .htpasswd file in the admin folder will prevent hackers from accessing your store, even if they discover the admin login location. Using .htaccess, you can deny all IP addresses from viewing your store, except the admin's IP address. A .htpasswd in the admin folder will require an additional password for the allowed administrator to access this directory.

### Catalog

The catalog can be protected with the traditional .htaccess file. Using file match can be useful for protecting important file types for your store, such as php and txt, rather than all of them. The following code can be used for .htaccess in your catalog folder:

```
<FilesMatch "\.(php|tpl|txt)$">
Order Deny,Allow
Deny from all
Allow from "your ip address"
</FilesMatch>
```

This will deny access to all template, php, and txt files.

### System folder

The system folder contains two files that need to be protected: logs/error.txt and start_up.php. The logs/error.txt can be renamed if necessary.

#### .Htaccess

The .htaccess will work to protect these files and the subfolders of System from being accessed by anyone except the designated administrator. To do so, insert the code below into your .htaccess:

```
<Files *.*>
Order Deny,Allow
Deny from all
Allow from "your ip address"
</Files>
```

File permissions
----------------

The following files need to be set to 644 or 444 to prevent anyone else from writing to them:

- config.php
- index.php
- admin/config.php
- admin/index.php
- system/startup.php
