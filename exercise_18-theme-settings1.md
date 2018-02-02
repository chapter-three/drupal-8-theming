#### [Drupal 8 Theming](README.md)

# Exercise 18: 

## Creating a theme settings file

Often we need to create small, simple little settings for our theme that can make it more reusable and customizable across sites. We can create new theme settings on our theme's settings page that we can use to help other users configure and customize our theme. For this, we will utilize two additional files. **acme.settings.yml** and **theme-settings.php** file.

1. Go to MYDRUPAL.LOCAL/admin/appearance/settings/acme in your browser to see what settings are available by default.

2. Create a new file called **acme.settings.yml** in your theme root and open in your preferred code editor.

    ```bash 
    $ cd MYDRUPAL
    $ touch themes/custom/acme/acme.settings.yml
    ```

3. Add the following code:

	```
	features:
  	  copyright_holder: ''
	  search_placeholder: 'Search site'
	```

5. Create a new file in your theme directory called **theme-settings.php** 

    ```bash 
    $ cd MYDRUPAL
    $ touch themes/custom/acme/theme-settings.php
    ```
    
6. Add the following code to that file.
	
	```php
	<?php
	
	function acme_form_system_theme_settings_alter(&$form, $form_state, $form_id = NULL) {

		$form['copyright_holder'] = array(
       		'#type' => 'textfield',
       		'#title' => t('Copyright Holder'),
       		'#default_value' => theme_get_setting('copyright_holder'),
       		'#description' => t('This appears in the footer'),
       		'#weight' => -10,
   		);
   		$form['search_placeholder'] = array(
       		'#type' => 'textfield',
       		'#title' => t('Search Placeholder'),
       		'#default_value' => theme_get_setting('search_placeholder'),
       		'#description' => t('This appears in the footer'),
       		'#weight' => -10,
   		);
	}
	```
      
7. Clear cache, then go to our **Appearance** page. Click on **Settings** for your custom theme. You should see two new options for the settings we added. 

8. Feel free to customize those values. We will use them in the next exercises.

## Questions you may have...
+ What is `features` in the ***.settings.yml**?
+ Where do I find documentation for creating forms?


## Done ☺
One more to go! [Exercise 19 - Custom Theme Settings 2](exercise_19-theme-settings2.md)
