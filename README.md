# Drupal 8 Theming Training

## Description

Are you struggling with Drupal 8 theming? New to Drupal or Drupal 8? 

Let's take it from the top!

This hands-on training will take you step-by-step through the process of creating a custom theme in Drupal 8. There will also be time for Drupal Q&A.


Along the way, we'll cover:

- Setting up Your local development environment 
- Working with YAML files
- Adding assets responsibly
- Getting, modifying and display Drupal data in the template
- Cool Twig tips and Tricks
- Preprocessing template functions and hooks
- Basic OOPHP principles
- Kint, theme_debug and other changes to debugging
- Leveraging new Drupal 8 site building paradigms to make theming easier
- Where to find help


## Notes:

* All terminal commands are run from the Drupal root. 

* `$` indicates a prompt. You do not need to type it into the terminal window.

* `MYDRUPAL` refers to the Drupal root directory or base URL.

* You'll have an easier time if you configure your editor to use spaces instead of tabs. 

* Feel free to ask any of the "Questions you may have ..." someone probably asked the question before!

* See a mistake or typo? Submit a pull request on Github! 

* Common hiccups are:
  * Syntax errors
  * Too many or not enough spaces in .yml files
  • Cache not cleared
  * PHP memory limit not high enough (>= 256) 
    * settings.php
       - `ini_set('memory_limit', '512M');`
    * php.ini 
      - `'memory_limit' = '512M'`


## Exercises
 
[Exercise 1 - Local Setup](https://docs.google.com/document/d/1ilmBEeIJb_c3YQLroryZZBu3neMY4UdN_8AZCLTnvTw/edit#heading=h.s8eqm5cz2t56)

[Exercise 2 - Add Content](exercise_02-add-content.md)

[Exercise 3 - Contrib Themes](exercise_03-contrib-themes.md)

[Exercise 4 - Dot Info File](exercise_04-dot-info.md)

[Exercise 5 - Libraries](exercise_05-libraries.md)

[Exercise 6 - Intro to Twig](exercise_06-intro-to-twig.md)

[Exercise 7 - Regions](exercise_07-twig-new-region.md)

[Exercise 8 - Dot Syntax](exercise_08-twig-dot-syntax.md)

[Exercise 9 - Twig Classes](exercise_09-twig-classes.md)

[Exercise 10 - Twig Filters](exercise_10-twig-filters.md)

[Exercise 11 - Twig Blocks](exercise_11-twig-block.md)

[Exercise 12 - Include SVG](exercise_12-twig-include-svg.md)

[Exercise 13 - Preprocess Function](exercise_13-preprocess.md)

[Exercise 14 - Template Suggestions](exercise_14-new-template-suggestions.md)

[Exercise 15 - Add Classes with PHP](exercise_15-preprocess-add-classses.md)

[Exercise 16 - Form Alter](exercise_16-form-alter.md)

[Exercise 17 - Responsive Images](exercise_17-responsive.md)

[Exercise 18 - Custom Theme Settings 1](exercise_18-theme-settings1.md)

[Exercise 19 - Custom Theme Settings 2](exercise_19-theme-settings2.md)

## Style Guides for Contributors

###### Path to files and directories.

**MYDRUPAL/themes** Path to files and directories.

###### Name of file or directory
**node.html.twig**

###### Code.

```bash
 $ cd drupal
```

###### Url
*http://MYDRUPAL/admin/config*


## Done ☺
