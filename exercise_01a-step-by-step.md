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

### Disable caches and enable debugging

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
	
2. Add the following to the bottom of **local.services.yml** Indentation is important in .yml files. Each line should be indented 2 spaces more than the previous one.
	
```
services:
  cache.backend.null:
    class: Drupal\Core\Cache\NullBackendFactory
    
```