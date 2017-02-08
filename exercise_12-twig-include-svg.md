#### Drupal 8 Theming

# Exercise 12: 

## Indclude an SVG inline.
Often we want to include SVGs in our project because they load fast and can be easily manipulated using CSS. In this example, we use the Twig `include` function to add svg code to our template inlne. This method can be used to include any snippet of HTML that needs to be accessed across templates.


1. Create a folder called **images** in your theme root. 
	``` 
	mkdir themes/acme/images
	```
	
2. Copy the svg code from an from your machine or use the example below. 

    ```
    <svg>
      <rect x="10" y="10" height="100" width="100"style="stroke:#ff0000; fill: #0000ff"/>
    </svg>
    ```
    
2. Paste the svg code into a file called **mysvg.svg** inside your newly created **images** folder

3. Paste the following code into .twig file.
    
    ``` 
    {% include active_theme_path() ~ '/images/mysvg.svg' %}
    ```
    
4. View a page that include the template you modified.    
	
	
## Questions you may have...
+ What other types of files can be included?


## Done ☺
