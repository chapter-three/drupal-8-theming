#### Drupal 8 Theming

# Exercise 19: 

## Apply our theme settings to our custom variables

Now that we have created some custom theme settings and we have the ability to customize them through the UI, lets put them to use. We will capitalize on the functionality we created in an earlier excercise. We will alter our **preprocess_page()** "copyright_holder" variable to be customizable with one of our new theme settings.

### Customize the copyright holder

2. In our **acme.theme** file, locate the `acme\_preprocess\_page()` function.

5. Modify the code to include the copyright_holder setting.
	
```php
$variables['copyright'] = t("Copyright @date @holder",
  array(
    '@date' => date('Y'),
    '@holder' => theme_get_setting('copyright_holder')
  )
);
```

6. Clear caches and see if it worked. Change the value on the theme settings page if you haven't already (otherwise nothing will really change).

We have declared our copyright_holder in our theme's settings, and it will override the site name as being the default copyright holder. A simple example, but powerful.

## Questions you may have...
+ How can I get one of the default theme settings, like the logo?


## Done ☺