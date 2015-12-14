Product Feeds
=============

Arastta includes several useful [Product Feeds](docs/user-manual/marketplace/feeds) in the core, but you may find you require a custom format and decide to create your own. Writing Arastta product feeds is very similar to [writing Arastta extensions](docs/developers/mvc-structure), and can be a very good way to learn how the [fundamentals of Arastta](docs/developers/loading-files) actually work. Just as the rest of Arastta, feeds follow the MVCL design pattern. This documentation guide will describe how you use each of the MVCL components to create the [admin](docs/user-manual/admin-panel) and [frontend](docs/user-manual/store-front) parts of your product feed.

Admin feed functionality
------------------------

When a store owner uses your product feed, they will want to edit the product feed's configuration options in the admin in order to select whether it is enabled or disabled and any specific options you make available. As the developer, you will need to create the admin page where the product feed may be edited.

All admin files are located in the admin/ folder. You will find four folders within the admin/ folder:

1. controller
2. view
3. language
4. model

All product feeds will require at least a single file in each of the view and controller folders. Some will require a file in each of the model and language folders. Usually the files have the same name, except the view file has a different suffix (.tpl). We will go through these files one by one.

### Controller

The first file you make will be the controller for your product feed's admin interface page. Arastta identifies existing product feeds automatically, simply by reading the admin/controller/feeds folder of your store. Any product feed files existing in this folder will automatically be shown on the [Product Feeds](docs/user-manual/marketplace/feeds) page, and on the [User Permissions](docs/user-manual/system/users/groups), page. You may call your controller file my_feed.php.

The controller file will have a function defined as public function index(). This is a publicly accessible 'page', which will be shown when the [Edit button](extension/module/edit/) is clicked, and where the view form will submit to. The submitted data will be processed in this function and saved to the `settings` database table through the controller's config object.

You may also have a function defined as public function install(). This function will be triggered when the install link is clicked on the [Extensions > feeds](docs/user-manual/appearance/modules/overview) page. Similarly, a function defined as public function uninstall() will be triggered when the uninstall link is clicked. You can use these functions to create and remove any structures (such as database tables or config settings) required by your feed. It is good practice to create an uninstall function to clean up any changes your feed has made.

### View

The second required file for your feed's admin interface is the view file. This will be created in the admin/view/template/feed folder, and will have the suffix .tpl. This is standard for Arastta view files. In this file you will create a form for the user to fill out and submit. It will be submitted to the feed controller's index function. The easiest way to create your view file is to copy and paste an existing, similar view file, and edit the form to contain the correct fields for your feed's configuration options. You may call your view file my_feed.tpl.

### Language

The third file you will usually create for any feed is the language file(s). You will need one language file per language that your feed is compatible with. The language file will live in the admin/language/<language name>/feed folder. It simply contains a PHP [associative array](http://php.net/manual/en/language.types.array.php) called $_, which contains the internal name as the key and the translation as the value. You may call your language file my_feed.php, the same as your controller and model files.

### Model

It is uncommon for feeds to require a model file on the admin side. However, if your feed relies on its own database table, or a custom query to create data of a particular format, then you may find yourself writing a model file. An example of this may be if you are writing a visitor counter feed, where each visitor is stored in a database table with their IP address and number of visits. You may then create a model file, with a function to define and create this extra table in the Arastta database. The model file will live in the admin/model/feed folder. You may call your model file my_feed.php, the same as your controller and language files.

Frontend feed functionality
---------------------------

The frontend of your feed follows the same pattern as the admin interface just described. What you will include in each of your frontend files will largely depend on what your feed is supposed to do. A feed can access any model files that already exist in Arastta, you do not need to write your own database queries if the same query already exists. For example, the catalog/product model contains many useful queries for fetching products. Using these model functions should be preferred over reinventing the wheel.

A key difference in the frontend of your feed, is that your view file will be in the catalog/view/theme/(themename)/template/feed folder. This is a significantly deeper folder structure to the admin view file because of themes. An Arastta store may have many different [frontend themes]([http://themes.arastta.pro/](http://themes.arastta.pro/)) available, but only one admin template. (themename)

On the frontend part of your feed you will have access to the configuration options saved by your feed, through both the controller's config object, and the $settings variable passed to the feed controller's index function. You can control aspects of the frontend display on the basis of these settings.
