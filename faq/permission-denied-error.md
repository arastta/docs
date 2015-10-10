I get "Permission Denied" error in back-end?
===============================

"Permission Denied" error
-------------------------

Arastta has a simple permissions system in the admin area. Normally when installing new extensions, there is code that automatically adds the Top Administrator group to have permissions on the extension. However, when adding new pages or pages that don't use the extension install system, the permission step will need to be done manually.

If you are getting this error, you can:

1. Go to the admin menu: **Arastta => System => Users => User Groups**
2. Edit  the Administrator  group
3. Be sure to check all the checkboxes for both Access and Modify areas
4. Save

Now you should be able to reach that page you originally tried to load.

![user groups backend access permission tab](_images/user-group-access-permission.png)
