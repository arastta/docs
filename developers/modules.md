Modules
=======

Writing Arastta modules can be a very good way to learn how the [fundamentals of Arastta](developer/loading/) actually work. Just as the rest of Arastta, modules follow the MVCL design pattern. Before starting, it's important to understand the [MVC Structure](http://arastta.org/docs/developers/mvc-structure) of Arastta.

Admin module functionality
--------------------------

When a store owner uses your module, they will want to edit the module's configuration options in the admin in order to decide which layouts to display the module on, whether it is enabled or disabled, and any module specific options. As the module developer, you will need to create the admin page where the module may be edited and the configuration options added or adjusted.

All admin files are located in the admin/ folder. You will find four folders within the admin/ folder:

1. controller
2. view
3. language
4. model

All modules will require at least a single file in each of the view and controller folders. Most will require a file in each of the model and language folders. Usually the files have the same name, except the view file has a different suffix (.tpl). We will go through these files one by one.

### Controller

The first file you make will be the controller for your module's admin interface page. Arastta identifies existing modules automatically, simply by reading the admin/controller/module folder of your store. Any modules existing in this folder will automatically be shown on the [Modules](extension/module/) page, and on the [User Permissions](system/user/), page. You may call your controller file my_module.php.

The controller file is the place where you can load the language files to convert text into variables to be utilized in the template file. In the diagram above, you can see the $_['text'] variable being handled by the controller, then sent as $text to the view. You will also utilize multiple model files and their class functions here, including your module's model file if it has one. For more information on loading files see [Loading files in the controller](developer/loading/).

You may also have a function defined as public function install(). This function will be triggered when the install link is clicked on the [Extensions > Modules](extension/module/) page. Similarly, a function defined as public function uninstall() will be triggered when the uninstall link is clicked. You can use these functions to create and remove any structures (such as database tables or config settings) required by your module. It is good practice to create an uninstall function to clean up any changes your module has made. To see the specific code for an install(), uninstall(), visit [Install/Uninstall a module](extension/module/install/).

#### Accessed via URL

The controller is the only file in the MVC-L framework to be accessed by URL in Arastta. In the administration, the URL will look like /admin/index.php?route=module/my_module&token. The admin adds a token to the URL, whereas the link in the catalog will not have it. As a result, the controller file will have a function defined as public function index(). This is a publicly accessible 'page' that is loaded by the URL, which will be shown when the [Edit button](extension/module/edit/) is clicked, and where the view form will submit to. The submitted data will be processed in this function and saved to the `settings` database table through the controller's config object.

### View

The second required file for your module's admin interface is the view file. This will be created in the admin/view/template/module folder, and will have the suffix .tpl. This is standard for Arastta view files. In this file you will create a form for the user to fill out and submit. It will be submitted to the module controller's index function. The easiest way to create your view file is to copy and paste an existing, similar view file, and edit the form to contain the correct fields for your module's configuration options. You may call your view file my_module.tpl.

In the view, you will be able to access the text from the language that the controller file stored as a PHP variable. See Loading Files in the Controller for the code on how to do so.

### Model

It is uncommon for modules to require a model file on the admin side. However, if your module relies on its own database table, or a custom query to create data of a particular format, then you may find yourself writing a model file. An example of this may be if you are writing a visitor counter module, where each visitor is stored in a database table with their IP address and number of visits. You may then create a model file, with a function to define and create this extra table in the Arastta database. The model file will live in the admin/model/module folder. You may call your model file my_module.php, the same as your controller and language files.

Frontend module functionality
-----------------------------

The frontend of your module follows the same pattern as the admin interface just described. What you will include in each of your frontend files will largely depend on what your module is supposed to do. A module can access any model files that already exist in Arastta, you do not need to write your own database queries if the same query already exists. For example, the catalog/product model contains many useful queries for fetching products. Using these model functions should be preferred over reinventing the wheel.

A key difference in the frontend of your module, is that your view file will be in the catalog/view/theme/(themename)/template/module folder. This is a significantly deeper folder structure to the admin view file because of themes. An Arastta store may have many different [frontend themes](http://arastta.org/index.php?route=extension/extension&path=1) available, but only one admin template. (themename)

On the frontend part of your module you will have access to the configuration options saved by your module, through both the controller's config object, and the $settings variable passed to the module controller's index function. You can control aspects of the frontend display on the basis of these settings.
