#### Drupal 8 Theming

# Exercise 10: 

## Advanced Twig

### Using filters

Lets use our node title to test some filters.

1. Near your other variable declaration in your theme's **node.html.twig** add:

    ```
    {%  set title_string = node.getTitle() %}
    ```
 

2. Test it with the following filters.

    ```
    clean_class: {{ title_string|clean_class }} <br/>
    upper: {{ title_string|upper }} <br/>
    length {{ title_string|length }} <br/>
    ```


## Questions you may have...
+ How did you know to use `node.getTitle()` ?

## Done ☺