#### [Drupal 8 Theming](README.md)

# Exercise 7: 

## Adding a new region (Let's use Twig)

The client wants a new region for special messages at the top of the footer, so we’ll give them a new region called `Footer top`. Eventually, it would be great to style this region to look a little nicer, but for now, lets just put the content in place.

1. Update **acme.info.yml** to include the new Footer top region:

	```
	regions:
	  ...
	  footer_top: 'Footer top'
	  ...
	```

2. Now that Drupal knows that a new region is available, we need to print that region to the page by modifying **page.html.twig**.
3. Navigate to the Classy theme in **MYDRUPAL/core/themes/classy/templates/layout** and locate **page.html.twig**.
4. Make a copy of **page.html.twig** and put it in the **acme** theme folder. We like to keep it organized, so we'll put it in **MYDRUPAL/themes/custom/acme/templates/page**.

    ```bash
    $ cd MYDRUPAL
    $ mkdir themes/custom/acme/templates/page
    $ cp core/themes/classy/templates/layout/page.html.twig themes/custom/acme/templates/page/page.html.twig
    ```


5. Edit your theme’s new version of **page.html.twig**:
Look for and copy the following lines of code around line 81:

	```twig
	...
	
	{% if page.footer %}
	<footer role="contentinfo">
      {{ page.footer }}
	</footer>
	{% endif %}
	
	...
	```

6. Above this footer callout code, paste your copy.
7. In your pasted code, Replace `footer` with `footer_top`, It should look like this when you’re finished:


	```twig
	...
	
	{% if page.footer_top %}
	<footer role="contentinfo">
      {{ page.footer_top }}
	</footer>
	{% endif %}
	
	{% if page.footer %}
	<footer role="contentinfo">
      {{ page.footer }}
	</footer>
	{% endif %}
	
	...
	```

8. Flush your cache and try putting a block in the new region.

## Questions you may have...
+ Can I add more regions? Can I remove ones I don’t need?
+ How do I style my new region?


## Done ☺
Sometimes you feel like a nut; sometimes you [Exercise 8 - Dot Syntax](exercise_08-twig-dot-syntax.md).

