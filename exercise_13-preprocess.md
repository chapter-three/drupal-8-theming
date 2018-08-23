#### [Drupal 8 Theming](README.md)

# Exercise 13: 

## .theme file and preprocess_page

Don't make yourself responsible for updating every site on January 1st. Let the computer do the work for you and automatically set items, like the copyright date, to the current year. We will begin to dive into some more advanced elements of Drupal theming including preprocess functions and template variables. 

What is a preprocess function? A preprocess function is a function that allows us to manipulate (add, edit, or remove) our data before our template processes it. Hence, the "pre" in preprocess. It's powered by `hook_preprocess()` function. `hook_preprocess_HOOK()` allows modules to preprocess theme variables, but for a specific theme hook, like node, page, or menu\_link. For our example, we will manipulate the data before it goes to the `page` twig template **page.html.twig**, so we will use 
"hook\_preprocess\_**page**()"

### Create our .theme file

1. Create a file at the root of the Acme theme named **acme.theme** and open in your preferred code editor

    ```bash
    $ cd MYDRUPAL
    $ touch themes/custom/acme/acme.theme
    ```

2. Write the following code in your new **acme.theme** file:
	
	```php
	<?php
	function acme_preprocess_page(&$variables) {
		$variables['copyright'] = "It works!";
	}
	
	```
**Note that there is not a closing ?> at the end, but there should be a line of whitespace.**

4. Open up **page.html.twig** and near the closing footer element, print out our new variable using the following code:

    ```twig
      <div class="copyright">
      {{ copyright }}
      </div>
    ```
3. Clear cache and verify your copyright is on the page.


### What year is it?

Great, it’s printing our variable, but we’re still not much better off than simply adding a block to say the copyright date manually. Let's start adding some logic in **acme.theme**.

1. Open **acme.theme** and add some php around our new variable so that it can print the current year instead of our filler message:
	
	```php
	<?php
	function acme_preprocess_page(&$variables) {
	  $variables['copyright'] = t("Copyright @date",
	    array('@date' => date('Y'))
	  );
	}
	```
**Note that there is not a closing ?> at the end, but there should be a line of whitespace.**

##Questions you may have...
+ Where did you find that function name? I would never have guessed that.
+ Why don’t I close the PHP tags?
+ Why does the new variable have a t() function around it?
+ What’s the best way to add markup and styles to our variable?
+ Could I have done this on the twig template?
 
##Done ☺
[Exercise 14 - Template Suggestions](exercise_14-new-template-suggestions.md) is ready to bat.
