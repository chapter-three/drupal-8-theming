#### [Drupal 8 Theming](README.md)

# Exercise 15: 

## Adding classes in .theme

A major job of any theme is to give us control over classes. We use classes to control styling, layouts, and javascript. Drupal and Twig give us many different ways to do this.

In this exercise, we are going to use `hook_preprocess_html` to gain control over the classes attached to our body tag.

### Add classes to our body tag

1. Navigate to your theme root, and open your **acme.theme** file. 

2. Add the following code:

	```php
    function acme_preprocess_html(&$variables) {
    // Our code will go here
    }
	```

3. We want to add our own classes to the body tag. This first one will be for all pages, the second one will set a class for each region that has content. Once completed, save and clear caches. Then view the source code of a page and confirm that our new class is applied to the body tag.

	```php
    // Add 'my-class' to all pages.
    function acme_preprocess_html(&$variables) {
      $variables['attributes']['class'][] = 'my-excellent-class';
    }
	```

4. Next, add the following line at the top of your **acme.theme** below `<?php`. 

	`use Drupal\Component\Utility\Html;`

5. Then add the following code inside of your `preprocess_html` function, below the `my-class` line
	
	```php
	...	
	// This is the D7 equivalent of "global $theme"
	$theme = \Drupal::theme()->getActiveTheme()->getName();
	
	$regions = system_region_list($theme);
	
	foreach ($regions as $region => $region_name) {
	  $region_class = Html::getClass($region);
	  if (!empty($variables['page'][$region])) {
	    $variables['attributes']['class'][] = $region_class . '-active';
	  }
	}
	...
	```
	
	We are going to use the `Html` PHP Class and its `getClass` method to process our values and make sure they are properly formatted class names. This is the replacement to drupal\_html\_class() and drupal\_clean\_css_identifier(). Bacause we use this, we have to make sure to declare our dependecy on that Class. That is why we added the code in part 4. Otherwise, php would not know what you are talking about and we would get a delightful php fatal error.


Go back to your website and refresh. Check out our body tag. Do you see the active region classes. This may be helpful if you want to trigger javascript or css in one region based on if there is stuff in another region.

## Questions you may have...
+ How would I know to use `use Drupal\Component\Utility\Html;`?


## Done ☺