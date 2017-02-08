#### Drupal 8 Theming

# Exercise 19: 

## Apply our theme settings to our custom variables

Now that we have created some custom theme settings and we have the ability to customize them through the UI, lets put them to use. We will capitalize on the functionality we created in Exercise 9. We will alter our **preprocess_page()** "copyright_holder" variable to be customizable with one of our new theme settings.

### Customize the copyright holder

1. Navigate to your theme root

2. Back in our _acme.theme_ file, locate the **acme\_preprocess\_page()** function.

3. Locate the section where we added in Exercise 9. It looks like this:
	
	```
   $variables['copyright'] = t("Copyright @date",
      array('@date' => date('Y'))
    );
	```
4. We are going to change this to use our variable `copyright_holder` if it has a value.

5. Add the following block of code below ```$variables['copyright'] = t("Copyright @date", array('@date' => date('Y')));```
	
	```
	$variables['copyright_holder'] = '';
	$name = \Drupal::config('system.site')->get('name');
	$copyright_holder = theme_get_setting('copyright_holder');
	
	if (!empty($name) || !empty($copyright_holder)) {
		$name = !empty($copyright_holder) ? $copyright_holder : $name;
		$variables['copyright_holder'] = $name;
	}
	```
6. In your `page.html.twig` add the following below `copyright` section
```
    {% if copyright_holder %}
    <div class="copyright">
      {{ copyright_holder }}
    </div>
  {% endif %}
  ```
  
7. Clear caches and see if it worked. Change the value on the theme settings page if you haven't already (otherwise nothing will really change).

We have declared our copyright_holder in our theme's settings, and it will override the site name as being the default copyright holder. A simple example, but powerful.

## Questions you may have...
+ How can I get one of the default theme settings, like the logo?


## Done ☺
