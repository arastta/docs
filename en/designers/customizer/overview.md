Customizer Overview
===================

Customizer is one of the most powerful features of Arastta which allows end-users (and even advanced ones) to easily customize and modify their theme's specific elements without any CSS and coding effort.

** How to implement Customizer feature into a theme?

It's very easy to make your theme customizable.  Just create a JSON file named _customizer.json_ in your theme's **root** directory. Here is where Second Theme's customizer file is located: `catalog/view/theme/second/customizer.json`

You can copy and paste this file in your theme's root directory and use it as a starter boilerplate. 

If you are familiar with JSON file format, it will be very easy to create the customizer file. Even if you are not familiar, it's still easy to create your own customizer.

Here is the start part of the default Arastta customizer file:

```
{
  "colors": {
    "title": "text_colors_title",
    "description": "text_colors_description",
    "control": {
      "container_background-color": {
        "type": "color",
        "label": "text_colors_container_background_label",
        "default": "#f5f5f5",
        "selector": "body"
    }
}    
```

Now, see below to understand what does the above code mean and what parameters are available to use:

* [Options (Fields)](docs/designers/customizer/options): These are the main functions of the Customizer feature which are composed of text fields, text areas, colour pickers, file upload and more.
* [Groups](docs/designers/customizer/groups): It's a good practice to categorize similar options (fields) under the groups. For example, you can group all the footer related options (fields) under a group named **Footer**. Thus, it will be more accessible for the theme users.