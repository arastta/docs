Developer quick start for beginners
===================================

This guide is written for developers already familiar with PHP, OOP and the MVC architecture

In the following, you'll see examples for the catalog side of the cart. The admin side is identical in function with the exception of the views which is noted in the relevant section

Understanding Libraries
-----------------------
All of the library functionality is accessible through Controller, Model and Views using `$this->library_name`. All of these can be found in the `/system/library/` folder. For example, to access the current shopping cart's products, you'll need to use the `Cart` class, which is in `/system/library/cart.php` and can be accessed using `$this->cart->getProducts()`

Commonly used items

* `customer.php` - Customer related functions
* `user.php` - Admin user related functions
* `cart.php` - Cart related functions
* `config.php` - All settings are loaded from this
* `url.php` - URL generation functions

Understanding the route parameter
---------------------------------

Arastta's framework relies on the `route=aaa/bbb/ccc` in the query string parameter to know what to load, and is the underpinning feature to finding the files you need to edit for each page. Most route's actually only use the `aaa/bbb` which should be seen as two parts, however some contain three parts `aaa/bbb/ccc` The first part `aaa` generally related to the folder within a generic folder such as the controller or template folders. The second part usually relates to the file name, without the relevant `.php` or `.tpl` extension. The third part is explained in the understanding controllers below.

Understanding languages
-----------------------

Languages are stored in `/catalog/language/` folder in the your language subfolder. Within this, general text values used across various pages are stored in the `default.php` file inside the folder, so for the English language on the catalog side, you'll find the values in `catalog/language/en-GB/default.php`. For specific page text, you'll need the `route` for the page (This is generally the case, but not always as you can specify any language file you like). For example, the search page has the route `product/search`, and therefore the language specific text for that page can be found in `catalog/language/en-GB/product/search.php` (Notice the file's name and subfolder match the route followed by `.php`.

To load the language in a controller, you use

```
$this->language->load('product/search');
```

Then you can use the language library function get to retrieve specific language texts, such as

```
$some_variable = $this->language->get('heading_title');
```

The language variables are assigned in the language file using a special variable `$_` which is an array of keys and text values. In your `/catalog/language/en-GB/product/search.php` you should find something similar to

```
$_['heading_title']     = 'Search';
```

The values in the global language file `en-GB/default.php` are automatically loaded and available to use without the `$this->language->load` method.

Understanding controllers
-------------------------

Controllers are loaded based on the `route` and are fairly straight forward to understand. Controllers are located in the `/catalog/controller/` folder. Continuing from the last example, the Controller for the Search page is in `/product/search.php` within this folder. Notice again that the route followed by `.php` is used.

Opening the controller file, you'll see a Pascal Case classname extending the `Controller` class, called `ControllerProductSearch`. This again is specific to the route, with Controller followed by the subfolder name and file name without the extension capitalised. The capitalisation is not actually required, but it's recommended for easy readability. It's worth noting that classnames don't take any values from the subfolder and file name other than letters and numbers. Underscores are removed.

Within the class are the methods. Methods in the class declared `public` are accessible to be run via the route - `private` are not. By default, with a standard two part route (`aaa/bbb` above), a default `index()` method is called. If the third part of a route (`ccc` above) is used, this method will be run instead. For example, `account/return/insert` will load the `/catalog/controller/account/return.php` file and class, and try to call the `insert` method.

Understanding Models
--------------------

Model's in Arastta are found in the `/catalog/model/` folder and are grouped based on function not the route, and therefore you will need to load them in your controller via

```
$this->load->model('xxx/yyy');
```

This will load the file in the subfolder `xxx` called `yyy.php`. It is then available to use via the object

```
$this->model_xxx_yyy
```

and as with controllers you can only call it's public methods. For instance, to resize an image, you would use the tool/image model and call it's resize method as follows

```
$this->load->model('tool/image');
$this->model_tool_image->resize('image.png', 300, 200);
```

Understanding variable assignment in views from the controller
--------------------------------------------------------------

In order to pass values to the view from the controller, you simply need to assign your data to the $this->data variable, which is essentially an array of key => value pairs. As an example

```
$data['example_var'] = 123;
```

Accessing this in a view is a little should be easy to understand if you're familiar with the extract() method which converts each key into a variable. So the `example_var` key becomes `$example_var` and can be accessed as such in the view

Understanding themes
--------------------

Themes are available to the catalog side only, and are basically a folder of templates, stylesheets and theme images. Theme folders are placed in the `/catalog/view/theme/` folder followed by the theme name. The folder name isn't of importance with exception to the default folder

The admin side uses `/admin/view/template/` (skipping the `/theme/theme-name/` from the path as it doesn't allow differing themes)

Template files reside in a `template` folder within the theme folder. Should any template not be available for the currently selected theme, the default folder's template is used instead as a fallback. This means themes can be created with very few files and still function fully. It also reduces code duplication and issues as upgrades are made

Understanding views (templates)
-------------------------------

As with language and models, the view file's are generally related to the route, though don't have to be at all. Templates on the catalog side are usually found in `/catalog/view/theme/your-theme/template/` unless it doesn't exist, in which case the default theme's templates will be used. For our search page example above, the file is product/search.tpl. For routes with three parts, it is generally in `aaa/bbb_ccc.tpl` though there's no hard set rule. In the admin, most pages follow this, with the exception that pages listing items, like the product listing page are in `catalog/product_list.tpl` and the product editing form is in `catalog/product_form.tpl`. Again, these aren't set, but a standard for the default cart

It's worth point out that the template file is in fact just another php file, but with a `.tpl` extension and is actually run in the controller file, therefore all of the things you can code in a controller can be run in a template file (though not recommended unless absolutely necessary)

Understanding the database object
---------------------------------

Queries are run using

```
$result = $this->db->query("SELECT * FROM " . DB_PREFIX . "table");
```

`DB_PREFIX` as the name suggests is a constant containing the database prefix if one exists

`$result` will return an object for SELECT queries, containing a few properties

`$result->row` contains the first row's data if one or more are returned as an associative array

`$result->rows` contains an array of row results, ideal for looping over using foreach

`$result->num_rows` contains the number of results returned

There are also a few extra methods the `$this->db` object has

`$this->db->escape()` uses `mysql_real_escape_string()` on the value passed

`$this->db->countAffected` returns the number of rows affected by an UPDATE query and so on

`$this->db->getLastId()` returns the last auto increment id using `mysql_insert_id()`

Understanding reserved variables
--------------------------------

Arastta has predefined variables to use in place of the standard `$_GET`, `$_POST`, `$_SESSION`, `$_COOKIE`, `$_FILES`, `$_REQUEST` and `$_SERVER`

`$_SESSION` is edited using `$this->session->data` where data is an associative array mimicking the `$_SESSION`

All of the others can be accessed using `$this->request` and have been "cleaned" to comply with magic quotes enabled/disabled, so

`$_GET` becomes `$this->request->get`

`$_POST` becomes `$this->request->post`

`$_COOKIE` becomes `$this->request->cookie`

`$_FILES` becomes `$this->request->files`

`$_REQUEST` becomes `$this->request->request`

`$_SERVER` becomes `$this->request->server`

<br/><br/>
**Credits**: Jay Gilford