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

2. Copy classy's **html.html.twig** into your theme.

    ```bash
    $ cd MYDRUPAL
    $ mkdir themes/acme/templates/html
    $ cp core/themes/classy/templates/layout/html.html.twig themes/acme/templates/html/html.html.twig
    ```
3. Clear Cache

3. Above the DOCTYPE declaration and below the comments, add the following code.

    ```twig
    {% set myclasses = ['red', 'green', 'blue'] %}
    ```

5. Find the line `<body{{ attributes.addClass(body_classes) }}>` and change it to

    ```twig
    <body{{ attributes.addClass(body_classes).addClass(myclasses) }}>
    ```
   
    You should now see classes `red`, `green` and `blue` attached to the body tag.

### Create a new custom variable.
Let's create a special body class for the user role.

3. Use `{{ kint(user) }}` to inspect the user variable in **html.html.twig**.  Observe the path to get the roles array.

4. Use `{{ kint(logged_in) }}` to see the value of this variable when logged in and logged out. 

2. Below ```{% set myclasses = ['red', 'green', 'blue'] %}``` add 

```twig
{% if logged_in %} 
    {% set roles = user.account.roles %}
{% endif %}
```

3. Change the body tag to   

```twig
<body{{ attributes.addClass(body_classes).addClass(myclasses).addClass(roles) }}>
```

3. Compare the `<body>` tag for logged in and logged out users. What are the results when you remove the `if` statement?

-------------------


## Questions you may have...
+ How do I remove a class?
+ Where can I find other cool twig functions?
+ What happened to preprocess functions and the template.php file?
+ Why do we copy our template files from the classy theme?
+ How did you know the `user` variable was available?



## Done ☺
