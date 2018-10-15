#### [Drupal 8 Theming](README.md)

# Exercise 3: 

## Contrib themes

This is where most themers will start their career. Let someone else do the work for you and download something generic that can be modified to fit your needs. Contributed themes can be a great resource for learning new techniques and functionality, which you can implement in your custom themes.

You can find themes at [http://drupal.org/project/themes](http://drupal.org/project/themes), as well as some external sites. Make sure the theme is compatible with Drupal 8.

If you run into problems, check the theme's issue queue and search the forums. If your problem hasn't already been addressed, post a question, and someone will try to help you out.


## Install our first contrib...
1. Download and add the latest recommended release of *Radix*:  http://drupal.org/project/radix 

    Remember if you're using Lando, `composer` becomes `lando composer`; please see the [README](https://github.com/chapter-three/drupal-8-theming/blob/master/README.md) for more details

    `$ composer require drupal/radix`

2. Also, download and add the latest recommended release of the *Mayo* theme: https://www.drupal.org/project/mayo

    `$ composer require drupal/mayo`

3. Read `README.txt` inside of the *mayo* folder to know what to expect. 
	
4. Enable the *Mayo* theme:
    1. Click on **Appearance** at the top.
    2. Find *Mayo* near the bottom and click **Install and set default**.

5. [Clear cache](clear-cache.md).


> ### Typical structure of a theme
>**MYTHEME.info.yml** - A theme must contain an .info.yml file to define the theme. Among other things, the .info.yml files define metadata, style sheets, and block regions. This is the only required file in the theme.
>
>**MYTHEME.libraries.yml** - The .libraries.yml file is used to define JavaScript and CSS libraries that can be loaded by the theme.
>
>**MYTHEME.breakpoints.yml** - Breakpoints define where a design changes in response to different devices. While the theme can use this file, its info can also be used by Drupal core to make adjustments to data it sends to the theme.
>
>**MYTHEME.theme** - The .theme file is equivalent to the old Drupal 7 template.php file. It is a PHP file that contains conditional logic and data (pre)processing of the output.
>
>**screenshot.png** - If a screenshot.png file is found in the theme folder, it will be used on the Appearance page. You can also define a screenshot image in .info.yml file.
>
>**logo.svg** - New to Drupal 8, logos are best saved as svg files and placed in the main level of your theme. Logos can also be uploaded at Appearance > Settings.
>
>**css/** or **styles/** - Drupal 8 core themes organize CSS files following the SMACCS style guide. For CSS files to be loaded, they must be defined in your .libraries.yml file. You can override or remove core and module CSS in your themes .info.yml file.
>
>**js/** or **script/** - JavaScript files are stored in the 'js' folder. For a theme to load JavaScript files, they must be defined in .libraries.yml file.
>
>**img/** or **images/** - It is good practice to store images in the 'images' subfolder.
>
>**templates/** - Templates provide HTML markup and some presentation logic. It is customary to place template files into subcategory folders, such as **templates/node/** for node based templates.

## ... then we configure our theme
1. Revisit the Appearance page and click **Settings** under the _Mayo_ theme.
2. Play with some of the configuration settings.
3. Try to complete the following tasks:
    1. Tweak the color scheme by utilizing the color wheel.
    2. Change the base font selection to be `Verdana, Geneva, Arial, ...`
    3. Set both sidebars to appear on the left side on big screens.
    3. Set sidebar to use round corners.

4. Many settings are theme-specific. Visit the settings pages of other themes, like *Seven* to compare.


## Questions you may have...
+ How do I choose a theme?

## Done ☺
Woo hoo! Time for [Exercise 4 - Dot Info File](exercise_04-dot-info.md)! :)

