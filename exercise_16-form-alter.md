#### [Drupal 8 Theming](README.md)

# Exercise 16: 

## Simple form altering

A big part of Drupal are forms. For example, content entry forms to add and manage content, search forms to find content, and settings forms to control the numerous parts of our site. Default forms are pretty awesome, but sometimes they just aren't enough. Now and then we need to alter a label, default value, or add libraries for styling or cool javascript functionality.

Form API and Drupal form alters are still in Drupal 8 and are still incredibly powerful tools to control Drupal. When using a form_alter for theming it is best to keep it to simple alterations such as changing labels, adding/removing classes, editing div structure, and adding HTML5 placeholders like in our following examples. Anything else should really be done in a module form alter.

**For this exercise, make sure the search block is in a region and visible.**

### Simple form altering with `hook_form_alter` function

1. Navigate to your theme root

2. Locate and open your **acme.theme** file, and add the following code.

	```php
	function acme_form_alter(&$form, \Drupal\Core\Form\FormStateInterface $form_state, $form_id) {
		if ($form_id == 'search_block_form') {
   			// Add placeholder text
   			$form['keys']['#attributes']['placeholder'] = t('Search');
   		}
	}
	```
2. Clear cache, and observe your search block. 

### Simple form altering with `hook_form_FORM_ID_alter` function 

This function is refined to only affect the form with the matching **FORM_ID** in the function name.

1. Replace the above function with the following code:
	
	```php
	function acme_form_search_block_form_alter(&$form, \Drupal\Core\Form\FormStateInterface $form_state, $form_id) {
		// Add placeholder text
    	$form['keys']['#attributes']['placeholder'] = t('Search this site.');
	}
	```

### Adding a javascript via a library to a form 
Let's say we want to leverage one of the libraries from core or contrib when our form is visible. 

1. Search and remove any other instances of kint() in your theme. Make sure the search_kint module is enabled.

1. View your site as an anonymous user by opening a new browser or private window. Verify that `form.js` is not included.

2. Add the following to the `acme_form_search_block_form_alter` function in **acme.theme**

    ```php 
    kint(\Drupal::service('library.discovery')->getLibrariesByExtension('core'));
    ```

3. Search for `form.js` in the the search form provided by kint. You'll see it highlighted under parent `drupal.form`. 

7. Navigate back to your theme root directory and open your **acme.theme** file.

9. Add the following code to your `acme_form_search_block_form_alter` function:

	```php
	// Attach a library from our theme to a form.
   	$form['#attached']['library'][] = 'core/drupal.form';
	```

10. Clear your caches.

If everything worked, the form.js file will be loaded for whenever the search block is present even for anonymous users.
	



## Questions you may have
* What is the benefit of using **hook\_form\_FORM\_ID\_alter** rather than just **hook\_form\_alter**?
* What else can I do with form alters?
* Can I use `[#attached]` in any function?

## Done ☺
You're on fire! Don't stop now! [Exercise 17 - Responsive Images](exercise_17-responsive.md)
