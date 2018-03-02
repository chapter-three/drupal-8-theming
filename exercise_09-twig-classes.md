#### [Drupal 8 Theming](README.md)

# Exercise 9:

Drupal has some handy functions specifically designed for the manipulation of HTML elements.


## Manipulating Classes with Twig

### Inspect the `attributes` array.
1. Add `{{ kint(attributes) }}` in your theme's **node.html.twig**. Review the object and its properties and methods. Note that `addClass()` is an available public method.

### Add a class.
2. Change `<article{{ attributes.addClass(classes) }}>` to
```<article{{ attributes.addClass(classes).addClass('myclass') }}>```. Observe the new value in kint as well as the new class in your site's markup.


### Add multiple classes to the body tag.
1. Remove all kint() statements from **node.html.twig**.

2. Copy classy's **html.html.twig** into your theme.

    ```bash
    $ cd MYDRUPAL
    $ mkdir themes/custom/acme/templates/html
    $ cp core/themes/classy/templates/layout/html.html.twig themes/custom/acme/templates/html/html.html.twig
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

1. Note that `logged_in` is one of the variables available in **html.html.twig** according to its comments. 

2. Use `{{ kint(user) }}` to inspect the user variable in **html.html.twig**.  Search the kint for `account`. Note that the method `getAccount()` is public. If we look back at Exercise 8, we see that we can use {{ user.account}} because of that sweet, sweet Twig magic.

4. Use `{{ kint(user.account}}`. Search for `roles`. Look at that! Our friends at D.O. also made `getAccount()` public. Now we can do the thing. 

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
We're getting pretty good at this!. Let's see what [Exercise 10 - Twig Filters](exercise_10-twig-filters.md) has to offer...
