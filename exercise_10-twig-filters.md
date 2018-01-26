#### [Drupal 8 Theming](README.md)

# Exercise 10: 

## Advanced Twig

### Using filters

Lets use our node title to test some filters.

1. First, we want to get the node title as a string.

2. Try `{{ kint(node) }}` in your theme's **node.html.twig** file. Under `Available methods` observe  `getTitle()`. It is a public function so we can use it in our twig template. 

1. Near your other variable declaration in your theme's **node.html.twig** add:

    ```twig
    {%  set title_string = node.getTitle() %}
    ```
 

2. Test it with the following filters.


    ```twig
    clean_class: {{ title_string|clean_class }} <br/>
    upper: {{ title_string|upper }} <br/>
    length: {{ title_string|length }} <br/>
    ```


## Questions you may have...
+ Why didn't you use `label` ?

## Done ☺