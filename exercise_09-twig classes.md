#### Drupal 8 Theming

# Exercise 9:

Drupal has a number of handy functions specifically designed for the manipuation of html elements.


## Manipulating Classes with Twig

### Inpspect the `attributes` array.
1. Add `{{ kint(attributes) }}` in your theme's **node.html.twig**. Review the array and its children.

### Add a class.
2. Change `<article{{ attributes.addClass(classes) }}>` to
```<article{{ attributes.addClass(classes).addClass('myclass') }}>```. Observe the new value in kint as well as the new class in your site's markup.


### Add multiple classes to the body tag.
1. Remove all kint() statements from **node.html.twig**.

2. Copy the core html.html.twig into your theme.

    ```
    $ cd MYDRUPAL
    $ mkdir themes/acme/templates/html
    $ cp core/modules/system/templates/html.html.twig themes/acme/templates/html/html.html.twig
    ```
3. Clear Cache

3. Above the DOCTYPE declaration and below the comments, add the following code.

    ```
    {% set myclasses = ['red', 'green', 'blue'] %}
    ```

5. Find the line `<body{{ atrributes }}>` and change it to

    ```
    <body{{ attributes.addClass(classes).addClass(myclasses) }}>
    ```

    You should now see classes `red`, `green` and `blue` attached to the body tag.

### Create a new custom variable.
1. Look in the comments of your theme's **html.html.twig**. Note that `node_type` is one of the variable available to this template.

2. Below ```{% set myclasses = ['red', 'green', 'blue'] %}``` add ```{% set node_type_class = 'page-' ~ node_type %}```

    The `~` is used to concatenate strings.

3. Looking at the `<body>` tag on a node page produces a class like `page-article` but on the front page we see `page-`, let's fix this.

    Wrap ```{% set node_type_class = 'page-' ~ node_type %}``` in an **if** statement. The result is:

    ```
    {% if nodetype %}
      {% set node_type_class = 'page-' ~ node_type %}
    {% endif %}
    ```

    Now the appropriate class only appears on node pages.

-------------------



## Questions you may have...
+ How do I remove a class?
+ Where can I find other cool twig functions?
+ What happened to preprocess functions and the template.php file?



## Done ☺
