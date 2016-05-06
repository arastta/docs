Customizer
==========

Implementing Customizer to themes
---------------------------------

Customizer is one of the most powerful features of Arastta which allows end users (even advanced ones) to easily customize and modify their theme's specific elements without any coding effort.

And as a theme developer it's a good practice to provide a detailed customizer panel along with the theme. Thus, theme users can easily customize their themes. Below you can find basic instructions about how to modify theme's *customizer.json* file according to theme's needs.

First, you can copy *customizer.json* file of Arastta's default theme, which is located in `/catalog/view/theme/second/` directory, to your theme's same directory: `/catalog/view/theme/mytheme/`

Now open this file with your favorite editor program or IDE. If you are familiar with JSON file format, then it will be very easy to create your own file. But don't worry if you are not familiar with JSON format, since it's very easy to read, understand and modify.

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

You need to open and close your JSON file with curly braces. Then you can group parameters into sections by providing a name. In the above example you can see *colors* as the section. Then you need to open new curly braces and provide a **title** and **description** for your section.

![Customizer Parameters Section](_images/customizer_section.jpg)
