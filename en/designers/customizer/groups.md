Groups
======

**Groups** are the good way of grouping the options (fields) which have similar functions. For example, if you have some options which customize the **footer** area of the theme, it will be a good practice to gather them under one group and users can access to the similar options easily.

Here is a minimum customizer.json file example with group:

```
{
"colors": {
	"title": "text_colors_title",
	"description": "text_colors_description",
	"control": {
		"footer_background-color": {
			"type": "color",
			"label": "text_colors_footer_background_label",
			"default": "#f5f5f5",
			"selector": "body"
		},
        "footer_color": {
                "type": "color",
                "label": "text_colors_footer_color_label",
                "default": "#666",
                "selector": "body"
        }
	}
}    
```

In this example, we grouped 2 different options under one group, called **colors**. And here is the other properties you can use for the group:

* **title** This is the variable you can use to name your group. You can write a title for your group with hardcode, or you can provide a translatable string (as seen in the above example: "text_colors_title").

* **description** variable can be used to provide an informative description for the group. Let users understand what sort of options are available under this group. You can use translatable strings here, too.

* **control** is the most important variable of the group where the options (fields) are registered for the group. You can get detailed information about the controls from the [**options**](docs/designers/customizer/options) doc.

