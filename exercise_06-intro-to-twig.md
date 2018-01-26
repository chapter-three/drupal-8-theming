#### [Drupal 8 Theming](README.md)

# Exercise 6: 

## Intro to Twig 

Twig is a modern, advanced, templating language for PHP. Twig is also the new templating engine for Drupal 8. It replaces the old and antiquated phptemplate engine. Twig is fast, secure, and incredibly flexible, but one of its best attributes, is that it does not allow some of the bad habits in Drupal theming that phptemplate allowed in the past. (I'm refering to stuff like database queries and data preprocessing in the template files). We've all done it at some point, and yes, we are all ashamed.

**If debugging is not enabled, please see "Exercise 1"**

## Basic Twig

There are 3 Basic Syntaxes of Twig. Mostly, we will use just 2 of them.

###The “Say Something” Syntax: {{ ... }}
The double-curly-brace (`{{`) is always used to **print** something. If whatever you need to do will result in something being printed to the screen, then you’ll use this syntax. I call this the “say something” tag, ya know, because it’s how you “speak” in Twig.

+ Print a variable

  ```twig
  {{ content }}
  ``` 

###The “Do Something” Syntax: {% ... %}
The curly-percent (`{%`) is the other syntax, which I call the “do something” syntax. It’s used for things like **if** and **for** tags as well as other things that “do” something. The `{%` is really easy because there are only a handful of things that can be used inside of it. If you go to Twig’s website, click Documentation, and scroll down, you can see a full list of everything in Twig. The “tags” header shows you everything that can be used inside of a “do something” tag, with more details about how each of these works. The only ones you need to worry about now are **if** and **for**. We’ll talk about a bunch more of these later.

+ Run a function (in this case, check if the variable 'logo' is set, if so print the logo)

  ```twig
  {% if logo %}
      {{ logo }}
  {% endif %}
  ```

+ Run a loop and print a value (in this case, for each product item in products array, print out the product item content)

  ```twig
  {% for product in products %}
      <h2>{{product}}</h2>
  {% endfor %}
  ```

###The Comment Syntax: {# ... #}
Actually, There is a third syntax, used for comments: `{#`. Just like with the “say something” and “do something” syntaxes, write the opening {# and also the closing #} at the end of your comments:

+ An example comment

  ```twig
  {# This is a comment for you to enjoy :) #}
  ``` 


## What's in a twig template

3. Open your theme's **node.html.twig** file in a text editor and add one of the following lines somewhere at the end of the twig template `{{ dump(date) }}` or `{{ kint(content_attributes) }}`

4. Visit a node page and lets see what it gives us.

## Use Twig
### Print out the bundle type for the node:

1. Inspect the **node.html.twig** template, review the comments and variables.

2. When editing the Acme theme's **node.html.twig**, locate the line with the ``{{ content }}``

3. Add a line to output the the node's bundle type (from step 1) before the ``{{ content }}``: 

	```twig
	<strong>{{ node.bundle|upper }}</strong>
	```

4. Clear cache, visit (or refresh) a node.

##Questions you may have

+ Can I modify a variable through Twig?


## Done ☺

Get your [Excercise 7 - Regions](exercise_07-twig-new-region.md) on.
