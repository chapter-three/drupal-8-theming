#### [Drupal 8 Theming](README.md)

# Exercise 10: 

## Advanced Twig

### Using filters

[Twig filters](https://twig.symfony.com/doc/2.x/filters/index.html) allow you to make changes to markup right in the template. Let's use our node title to test some string filters.

1. First, we want to get the node title as a string.

2. Try `{{ kint(node) }}` in your theme's **node.html.twig** file. Under `Available methods` observe  `label()`. It is a public function so we can use it in our twig template. 

1. Near your other variable declaration in your theme's **node.html.twig** add:

    ```twig
    {%  set title_string = node.label %}
    ```
 

2. Test it with the following filters.


    ```twig
    clean_class: {{ title_string|clean_class }} <br/>
    upper: {{ title_string|upper }} <br/>
    length: {{ title_string|length }} <br/>
    ```


3. If you have time, try creating arrays, loops and object to test some of the other amazing filters for twig See: https://twig.symfony.com/doc/2.x/filters/index.html.

## Questions you may have...
+ When should one use Twig filters instead of CSS or PHP?

## Done ☺
¡No Pare! !Sigue! !Sigue! [Exercise 11 - Twig Blocks](exercise_11-twig-block.md)