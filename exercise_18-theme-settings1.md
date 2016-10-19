#### Drupal 8 Theming

# Exercise 18: 

## Creating a theme settings file

Often we need to create small, simple little settings for our theme that can make it more reusable and customizable across sites. We can create new theme settings on our theme's settings page that we can use to help configure and customize our theme.
For this we will utilize two additional files. a _MYTHEME.settings.yml_ and a _theme-settings.php_ file

1. Navigate to your theme root

2. Create a new file called _acme.settings.yml_ and open in your preferred code editor.

3. Add the following code:

	```
	features:
  		comment_user_picture: true
   		comment_user_verification: true
   		favicon: true
   		logo: true
   		name: true
   		node_user_picture: true
   		slogan: true
	copyright_holder: ''
	search_placeholder: 'Search site'
	```

4. Navigate back to your theme root

5. Create a new file in your theme directory called _theme-settings.php_ file and open in your preferred code editor.

6. Add the following code to that file.
	
	```
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
+ What is `features` in the *.settings.yml?
+ Where do I find documentation for creating forms?


## Done ☺