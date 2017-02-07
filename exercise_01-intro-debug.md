#### Drupal 8 Theming

# Exercise 1: 

## What is Theming in Drupal and Drupal 8

Theming in Drupal is taking the processed data from Drupal, and outputting it our desired html structure so that web browsers can display our content. Themes make Drupal websites beautiful, and can make the difference between a user friendly site or a difficult to use site. A good theme will show off all the best aspects of your website, while maintaining all the speed and flexibility that Drupal brings to the table.  

## What's our goal for today?

By the end of this workshop, participants should be able to understand and use common theme components for Drupal 8 and understand the major changes between Drupal 7 and Drupal 8 theming.

## Enable Theme debugging and other Local Settings.

### Make files writable.
1. Using your terminal, or through your display, locate your **settings.php** file. The file is usually found at **MYDRUPAL/sites/default/settings.php**. 

2. Change permissions for the `sites/default` folder if needed using the following terminal command, or through your display:

	**MYDRUPAL** should be the path to your drupal sites root directory. Make sure to adjust your terminal commands accordingly.
	
	```bash
	$ cd MYDRUPAL
	$ chmod -Rf 775 sites/default/
	```

### Allow local settings and services.
3. Open up the `settings.php` file in your preferred code editor and uncomment the following lines (~ lines 752-755 in Drupal 8.2.6):

	```php
# if (file_exists($app_root . '/' . $site_path . '/settings.local.php')) {
#   include $app_root . '/' . $site_path . '/settings.local.php';
# }
	```
4. Copy the file **MYDRUPAL/sites/example.settings.local.php** to **MYDRUPAL/sites/default/settings.local.php** using the following terminal command, or through your display:

	```bash
	$ cd MYDRUPAL
	$ cp sites/example.settings.local.php sites/default/settings.local.php
	```

5. Create the **local.services.yml** file from **default.services.yml**. Copy the default file and rename it using the following terminal command, or through your display.
	
	```bash
	$ cd MYDRUPAL
	$ cp sites/default/default.services.yml sites/default/local.services.yml
	```

6. Locate the following line in **settings.local.php**: (line 39)
	
	```php
	$settings['container_yamls'][] = DRUPAL_ROOT . '/sites/development.services.yml';
	```
	
	change it to:
	
	```php
	$settings['container_yamls'][] = DRUPAL_ROOT . '/sites/default/local.services.yml';
	```

### Disable caches and enable debuggging

1. Inside **local.services.yml**, locate debug line twig configuration (line 58) and change it to **true**
	
	```
	parameters:
	[...]
	  twig.config:
	[...]
  	    debug: true
	```
	Remember spaces are significant in .yml files
 
2. Uncomment the following lines in **settings.local.php** (line 67) and (line 76)
	
	```php
	$settings['cache']['bins']['dynamic_page_cache'] = 'cache.backend.null';
	```
	```php
	$settings['cache']['bins']['render'] = 'cache.backend.null';
	```
	Note: Disabling the render cache is fine in the early stages of development but you'll want to turn it on during testing.
	
2. Add the following to the bottom of **local.services.yml**
	
	```
	services:
  	  cache.backend.null:
    	class: Drupal\Core\Cache\NullBackendFactory
    ```

## Enable devel and kint debugging.
1. Download the devel module and install devel. For information on installing a drupal 8 module, please see **[Drupal 8 Module Installation](https://www.drupal.org/documentation/install/modules-themes/modules-8)** (https://www.drupal.org/documentation/install/modules-themes/modules-8). Enable the Kint module. 

2. No additional settings are needed after installation. 

3. As we work on the exercises, you can use the following to see what data you have available to you inside of a function. You replace `$VARIABLE_NAME` with the actual variable that you want to view the contents of.

In .theme file: 

`kint($VARIABLE_NAME);`
`ksm($VARIABLE_NAME);`

In .twig files:

`{{ kint(VARIABLE_NAME) }}` (works but may produce error)
`{{ dsm(VARIABLE_NAME) }}`
`<pre>{{ dump(VARIABLE_NAME) }}</pre>`

## Enable Admin Toolbar
1. To get admin_menu-like drop-downs on hover, download and enable the Admin Toolbar (admin_toolbar) and Admin Toolbar Tools (admin_toobar_tools) module. 

## Clearing the Registry

Through out these exercises you'll be asked to clear cache or registry in order to see changes. 
 
**Ways to clear registry (aka "Clear Cache"):**

* use ``$ drush cr`` 
* go to Configuration > Performance and Clear All Caches. 
* with admin_toolbar_tools enabled, hover over the Drupalicon and choose Flush all Caches. 
* go to /rebuild.php

## Questions
+ What is drush and what is `drush cr`?

## Done ☺
