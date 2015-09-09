User Groups
======

Before you begin creating user profiles, you should visit **System → Users → User Groups** to set specific access and modification permissions. Also you can hide or show dasboard modules from the **General** tab for each group.

![system user groups backend](_images/system-user-groups.png)

Arastta lets you customize which admin side pages can be accessed by the specific user groups. You must check which pages can be accessed under **Access Permission**, and which page content can be modified under **Modify Permission**. The pages in the box office are displayed according to the top menu sections. For example, catalog/attribute is the Attribute section under Catalog in the top menu of the dashboard.

![user groups backend general tab](_images/user-group-general.png)

> Be aware that checking sections in **Access Permission** lets the user see the information on those pages. If a page in **Access Permission** is selected, but the page in **Modify Permission** is unselected; the user will be able to view the information on the page, but will be unable to modify this information.

For the Co-worker group, we chose to allow access and permit modification to the Catalog Section only, but not the rest of the admin panel.

![user groups backend access permission tab](_images/user-group-access-permission.png)

Arastta provides two user groups installed into the admin side, Administrator and Demonstration. The Administrator has every box checked under **Access Permission** and **Modify Permission**. It is an intuitive step that users assigned to the Administrator position would need access to all of the admin pages and permission to modify these sections. You can choose to leave the group unchanged, or unselect categories for this group. The Demonstration user group doesn't have any admin pages checked in **Access Permission** or **Modify Permission**, meaning users added in this group will not be able to access the admin side or modify any features of the shop.
