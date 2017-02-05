#### Drupal 8 Theming

# Exercise 3: 

## Contrib themes

This is where most themers will start their career. Let someone else do the work for you and download something generic that can be modified to fit your needs. Contributed themes can be a great resource for learning new techniques and functionality, that you can implement in your own custom themes.

### Basic steps of installing a theme

1. **Download and extract the theme files or use Drush/Drupal console to download.** You can find themes on http://drupal.org/project/themes, as well as some external sites. Make sure the the theme is compatible with Drupal 8.

2. **Read directions and Enable the theme.** Make sure to Read any README files in your theme as well as the themes project page on drupal.org for any installation information. Visit the "Appearance" link in the main Administration menu of your site. 

3. **Make it active and/or your default theme.** Click 'Install' to enable the theme. Click 'Set as default' or Install and set as default' to make this the chosen theme for your site.

If you run into problems, check the themes issue queue and search the forums. If your problem hasn't already been addressed, post a question and someone will try to help you out.

## Install our first contrib...
1. Download and add the latest recommended release of _Radix_:  http://drupal.org/project/radix 
2. Also download and add the latest recommended release of the _Mayo_ theme: https://www.drupal.org/project/mayo
3. Read `README.txt` inside of the _mayo_ folder to know what to expect.
4. Enable the _Mayo_ theme:
    1. Click on **Appearance** at the top.
    2. Find _Mayo_ near the bottom and click **Install and set default**.
5. Clear your cache through ``drush cr`` or by going to Configuration > Performance and clicking **Clear all caches**.


### Typical structure of a theme
+ **MYTHEME.info.yml** - A theme must contain an .info.yml file to define the theme. Among other things the .info.yml files defines meta data, style sheets, and block regions. This is the only required file in the theme.

+ **MYTHEME.libraries.yml** - The .libraries.yml file is used to define JavaScript and CSS libraries that can be loaded by the theme.

+ **MYTHEME.breakpoints.yml** - Breakpoints define where a design changes in order to respond to different devices. While the theme can use this file, its info can also be used by Drupal core to make adjustments to data it sends to the theme.

+ **MYTHEME.theme** - The .theme file the equivalent to the old Drupal 7 template.php file. It is a PHP file that contains conditional logic and data (pre)processing of the output.

+ **screenshot.png** - If a screenshot.png file is found in the theme folder, it will be used on the Appearance page. You can also define a screenshot image in .info.yml file.

+ **logo.svg** - New to Drupal 8, Logos are best saved as svg files and placed in the main level of your theme. Logos can also be uploaded at Appearance > Settings.

+ **css/** or **styles/** - Drupal 8 core themes organize CSS files following the SMACCS style guide. For CSS files to be loaded, they must be defined in your .libraries.yml file. You can override or remove core and module css in your themes .info.yml file.

+ **js/** or **script/** - JavaScript files are stored in the 'js' folder. For a theme to load JavaScript files, they must be defined in .libraries.yml file.

+ **img/** or **images/** - It is good practice to store images in the 'images' sub folder.

+ **templates/** - Templates provide HTML markup and some presentation logic. It is customary to place template files into sub category folders, such as **templates/node/** for node based templates.

## ... then we configure our theme
1. Revisit the Appearance page and click **Settings** under the _Mayo_ theme.
2. Play with some of the configuration settings.
3. Try to complete the following tasks:
    1. Set it so that both sidebars appear on the left side on big screens.
    2. Change the base font selection to be `Verdana, Geneva, Arial, ...`
    3. Set sidebar to use round corners.
    4. Tweak the color scheme by utilizing the color wheel.


## Questions you may have...
+ How do I choose a theme?

## Done ☺