#### [Drupal 8 Theming](README.md)

# Exercise 8:

## Manipulating variables in the template

Look at the comments at the top of the **node.html.twig** template. The comments detail the variables that are available to this particular template. In twig, we can use certain filters to manipulate the output of variables.

### Use `kint()` to inspect the content variable.

1. Add `{{ kint(content) }}` to the bottom of your **node.html.twig** field.

2. Go to an Article node page.

3. Inspect the content variable. Note that body, field_tags, and field_image are available.

    _Make sure your [php memory limit](https://www.drupal.org/docs/7/managing-site-performance-and-scalability/changing-php-memory-limits) is high (>= 256), or you may see a white screen of death._


### Print content without certain fields.

1. Delete the kint statement.

1. Verify that the article you're looking at has Tags. 

1. In **node.html.twig**, change ```{{ content }}``` to ```{{ content|without('field_tags') }}```

2. View an article node page. Now all fields are printed except for the tags field.

### Print fields individually.

1. Find ```{{ content | without('field_tags') }} ``` from the previous step and change it to ```{{ content | without ('field_tags', 'field_image') }}```

    This removes the tags and the image fields.


2. Add the following directly above `{{ content | without ('field_tags', 'field_image') }}`.

  ```twig
    <div class="sidebar">
      {{ content.field_image }}
      {{ content.field_tags }}
    </div>
  ```

  You should now see your Tags and Image fields inside a div with class `sidebar`. 
    
3. Add a little styling to **css-stuff.css** to get the full effect.

  ```css
  .node__content {
    display: grid;
    grid-template-columns: 1fr 3fr;
  }
  ```


### Explore.
The `.` syntax in twig is a shorthand for some PHP methods and functions. Below is  a list of methods Twig will check in the order they will be checked in.

>```twig
>{{ sandwich.cheese }}   
>```

>```php
>// Array key.
>$sandwich['cheese'];
>// Object property.
>$sandwich->cheese;
>// Also works for magic get (provided you implement magic isset).
>$sandwich->__isset('cheese'); && $sandwich->__get('cheese');
>// Object method.
>$sandwich->cheese();
>// Object get method convention.
>$sandwich->getCheese();
>// Object is method convention.
>$sandwich->isCheese();
>// Method doesn't exist/dynamic method.
>$sandwich->__call('cheese');
>```

1. Spend a few moments trying to print out variables and their children.

## Questions you may have...
+ What if I only want the body text without the surrounding markup?
+ Why do you keep telling me to delete my kint statements?

## Done ☺
Next stop: [Exercise 9 - Twig Classes](exercise_09-twig-classes.md)
