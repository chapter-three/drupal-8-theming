#### Drupal 8 Theming

# Exercise 11: 

## Twig blocks and Drupal blocks

Twig introduces another "block" concept within Drupal. However, a **Twig "block"** is not the same as a Drupal block.

A Twig _block_ is an element in the template file that can be overridden, indepentenly from its inherited (parent) template. This means, I can reuse the majority of a parent template and just change the one part I need to change. In Drupal 7, you would have to copy the whole template into a new file and be stuck trying to manage two independent templates.
Twig _blocks_ are used for inheritance and act as placeholders and replacements at the same time.

[Twig block official documentation](http://twig.sensiolabs.org/doc/tags/extends.html)
http://twig.sensiolabs.org/doc/tags/extends.html

	
### Twig block structure

In the following example we have two twig blocks one named "content" and the other name "other_content"

	{% block content %}
		{{ variable_to_print }}
	{% endblock %}

	{% block other_content %}
		{{ string_to_print }}
	{% endblock %}
	
### Using twig block inheritence

In Drupal 8 core, we will use the original example Drupal block, "Powered by Drupal" block, to show you an example of using twig blocks. The "Powered by Drupal" Block utilizes the default block template. This template contains a twig block inside of it named "content". 

We are going to copy the default block twig template into our theme, rename it and set it to only alter the value of the twig block. This way our new template will follow the default template, but only change the value inside of out twig block.

1. First thing is to make sure that the "Powered by Drupal" block is displayed. Go to the block admin page and place the "Powered by Drupal" block into any of your theme's regions.

2. **Save** the configuration, and visit a page on the front end of your site. **Make sure you can see the block somewhere on your site**.

3. Locate and copy the **block.html.twig** template located at **MYDRUPAL/core/themes/classy/templates/block/block.html.twig** and copy it into your **/templates/block** folder of your custom theme.

    ```
    $ cd MYDRUPAL
    $ mkdir themes/acme/templates/block
    $ cp core/themes/classy/templates/block/block.html.twig themes/acme/templates/block/block.html.twig
	```

4. Open that file in your preferred code editor. You should see the following code:
	
	```
	{%
	  set classes = [
	    'block',
	    'block-' ~ configuration.provider|clean_class,
	    'block-' ~ plugin_id|clean_class,
	  ]
	%}
	<div{{ attributes.addClass(classes) }}>
	  {{ title_prefix }}
	  {% if label %}
	    <h2{{ title_attributes }}>{{ label }}</h2>
	  {% endif %}
	  {{ title_suffix }}
	  {% block content %}
	    {{ content }}
	  {% endblock %}
	</div>
	```
	
5. We are going to copy and rename this file using information from our debug setup. View the source code on a page where the "Powered by Drupal" block is visible. Locate the code for the block. You should see some additional code that looks like this:

	```
	* block--system-powered-by-block.html.twig
	x block.html.twig
	```
	
	These are the template suggestions for different components of the page. These come from our theme and twig debug enabling. Twig is telling you exactly how you can name your new template files to make sure they effect that component. The `x` at the start of a name refers to the template that is currently being used to build that component. Starting from the bottom of the list, the names are in order of priority override.
	
6. So that it only effects the "Powered by Drupal" block, rename the `block.html.twig` file to `block--system-powered-by-block.html.twig`


7. Open the `block--system-powered-by-block.html.twig` file and replace all the code in it with the following code:

	``` 
	{% extends '/core/themes/classy/templates/block/block.html.twig' %}

  	{% block content %}
    <div class="d8-power">{{ 'I am powered by Drupal 8, haha!'|t }}</div>
  	{% endblock %}
  	```

7. Clear cache. 

	We only override the content inside the twig block name **"content"**, The rest of the items are still controlled by the default block.html.twig template file. If we had to make a change to all Drupal blocks, like add a wrapping div or a class to all blocks, we could make that change in our default template and it would still apply to our overridden template.


## Questions you may have...
+ What is the `|t` in our twig template?
+ What is the `{% trans %}` component in twig?

## Done ☺
