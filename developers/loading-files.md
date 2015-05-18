Loading Files
=============

In Arastta's MVC structure, your module's controller is the glue connecting your language, model, and template files to each other. The controller is responsible for grabbing the text contained in the language file and making them accessible as PHP variables in the view's template file. In addition to inheriting the functions available in the controller's parent class, Controller, you can also load any of Arastta's default model files and their functions in the controller.

Language
--------

The controller brings the text stored in the language file, and turns them into variables that can be echoed in the template file to displayed text. This is especially useful for managing translations of your module. Instead of modifying your .tpl file every time you have a new translation to change each piece of text inside, you just need to modify the text in your language file, and the variables will remain the same in the controller and the template.

By default, Arastta will try to automatically load the language file based on the **route** variable. The following code will load the language file manually. Inside the parentheses you will need to include the path to the language file from inside the language folder.

```
$this->load->language('module/my_module');
```

It is important to remember that the admin controller will only load the admin language file, but not the catalog language file; and likewise the catalog controller will only load the catalog language file. Once the language file is loaded into the controller, you can store its text into a PHP variable with the use of the $data array. The $this->language->get('text') will grab the text from the $_['text'] variable inside of the language file.

```
$data['text'] = $this->language->get('text');
```

The $this->language->get('text') will grab the text from the $_['text'] variable inside of the language file we just loaded above. Every element of the data array will be converted into its own variable. The $data['text'] will become $text for the template file inside view. The $text variable can be echoed in the view's .tpl file wherever needed:

```
<?php echo $text; ?>
```

Instead of calling every language string/variable via get() function, you can also load them all at once using the following code:

```
$data = $this->language->all();
```

If you want to keep the $data variable set before then you can send it to the $this->language->all($data); function.

### Setting the heading title

The following code will set text from the language file as the heading title of the page:

```
$this->document->setTitle($this->language->get('heading_title'));
```

This will grab the text for the variable $_['heading_title'] stored in the module's language file.

> If you need the text to be stored as a php session variable, use $this->session->data['text'] instead of $this->data['text'].

Model
-----

Loading model files into your controller file will allow your module to utilize Arastta's built-in functions. The functions inside the model files interact with the store's database and to add/pull important information for your module. We recommended that you to take advantage of these functions, rather than making your own DB queries. Take some time to explore the model folders in both the admin and catalog files, to see which files may benefit your module's purpose. For example, if your module needs to pull product information from the store's database, it will be useful to load the admin/model/catalog/products.php file, since it already has a multitude of helpful, built-in functions that interact with the store's products in the database.

Your module can load any model file its controller file using the following code, granted that they are in the same admin or catalog folder as the controller.

```
$this->load->model('setting/setting');
```

You will need to specify the path to the file you want to load from the admin folder within the parentheses. The code above will load the settings class so we have access to the functions within the ModelSettingSetting class in our model's controller file. Use the following format in your code to call a function from a loaded model file:

```
$this->model_setting_setting->editSetting('my_module', $this->request->post);
```

The underscores refer to the file designations for model/setting/setting.php. If you have a model file included for your module your code would follow the format mentioned above, since the model file is uploaded to model folder.

```
$this->load->model('module/my_module.php');

$this->model_module_my_module->myFunction();
```

The code above will load the my_module.php stored in *admin/model/module/my_module.php*.

> Instead of using spaces in file names for your module, use underscores.

Template
--------

In the controller you will need to load your module's template file in view. To do so:

```
$output = $this->load->view('module/my_module.tpl', $data);
```

Library
-------

The Arastta directory contains a collection of library files that can be accessed by both the admin and catalog controller files. These files are located under system/library in the root folder of the Arastta store. In the code examples seen inloading the language file, both $this->load->language and $this->document give access to functions within the language.php and document.php files in the library folder. If you want to access a function in a library file you need to call it using $this->[insert library file name]->function() in the controller class.