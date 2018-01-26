#### [Drupal 8 Theming](README.md)

# Exercise 1: Local Setup

## What is theming in Drupal and Drupal 8

Theming in Drupal is taking the processed data from Drupal, and outputting it our desired html structure so that web browsers can display our content. Themes make Drupal websites beautiful, and can make the difference between a user friendly site or a difficult to use site. A good theme will show off all the best aspects of your website, while maintaining all the speed and flexibility that Drupal brings to the table.  

By the end of this workshop, participants should be able to understand and use common theme components for Drupal 8 and understand the major changes between Drupal 7 and Drupal 8 theming.

## I. Enable theme debugging and other local settings.

### If using ADD, delete site-specific folder.
Acquia Dev Desktop assumes a multi-site installation. For consistency across systems, we'll use the standard approach.
    
  1. Delete **MYDRUPAL/sites/MYDRUPAL.dd** folder

### Make files writable.
1. Using your terminal, or through your display, locate your **settings.php** file. The file is usually found at **MYDRUPAL/sites/default/settings.php**. 

2. Change permissions for the `sites/default` folder if needed using the following terminal command, or through your display:

	**MYDRUPAL** should be the path to your drupal sites root directory. Make sure to adjust your terminal commands accordingly.
	
	```bash
	$ cd MYDRUPAL
	$ chmod -Rf 775 sites/default/
	```

### Allow local settings and services, disable caches and enable debugging
3. Open up the **settings.php** file in your preferred code editor and uncomment the following lines (~ lines 782-785 in Drupal 8.4+):

	```php
   # if (file_exists($app_root . '/' . $site_path . '/settings.local.php')) {
   #   include $app_root . '/' . $site_path . '/settings.local.php';
   # }
    ```

2. Download this repo's [settings.local.php](settings.local.php) and place it at MYDRUPAL/sites/default/settings.local.php

2. Download this repo's [local.services.yml](local.services.yml) and place it at MYDRUPAL/sites/default/local.services.yml

3. After this step:
	
	* CSS and JS should not be cached.	
	* Changes to twig, js and css files will be seen on page refresh.
	* Theme debugging information will be available in source comments. 

## II. User Composer to download [Devel](https://www.drupal.org/project/devel), [Search Kint](https://www.drupal.org/project/search_kint) and [Admin Toolbar](https://www.drupal.org/project/admin_toobar) modules.
 
  _Composer is the only recommended way of installing modules for Drupal 8. While it is still possible to download modules as packages, users who do so will encounter conflicts and dependency issues. For information on installing a drupal 8 modules with composer, please see [Using Composer to manage Drupal site dependencies](https://www.drupal.org/docs/develop/using-composer/using-composer-to-manage-drupal-site-dependencies#adding-modules)._

 
  0. Open terminal and navigate to your site root.
 
    ```bash
    $ cd MYDRUPAL
    ```
 
  1. Download devel and its dependencies.
 
    ```bash
    $ composer require drupal/devel 
    ```
    
  2. Download Admin Toolbar and its dependencies.

    ```bash
    $ composer require drupal/admin_toolbar
    ```
 
  2. Download Search Kint and its dependencies.
  
      ```bash
      $ composer require drupal/search_kint 
      ```

  1. Enable the modules using drush or through the UI and clear registry.
    
    ```bash
    $ drush en devel kint search_kint admin_toolbar admin_toolbar_tools -y
    $ drush cr
    ```
  2. Go to your http://MYSITE/admin/module and verify the above modules are enabled. 

*As we work on the exercises, you can use the following to see what data you have available to you inside of a function. You replace `$VARIABLE_NAME` with the actual variable that you want to view the contents of.*

_In .theme file:_

    
    kint($VARIABLE_NAME);
    ksm($VARIABLE_NAME);
    
    
_In .twig files:_


    {{ kint(VARIABLE_NAME) }}
    {{ dsm(VARIABLE_NAME) }}
    <pre>{{ dump(VARIABLE_NAME) }}</pre>


## III. Clearing the Registry

Throughout these exercises you'll be asked to clear cache or registry in order to see changes. 
 
**Ways to clear registry (aka "Clear Cache"):**

* use ``$ drush cr`` in the terminal*
* go to Configuration > Performance and Clear All Caches. 
* with admin\_toolbar\_tools enabled, hover over the Drupalicon and choose Flush all Caches. 

*Note that if you use Acquia Dev Desktop, you may have to run your drush commands through the Terminal Link in its UI.

## Questions
+ What is drush and what is `drush cr`?
+ Why can't I use `drush dl`?
+ My terminal says `bash: $: command not found`. What happened?
+ Why don't we use settings.php ?

## Done ☺
On to [Excercise 2 - Add Content](exercise_02-add-content.md)!