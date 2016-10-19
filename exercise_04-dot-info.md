#### Drupal 8 Theming

# Exercise 4: 

## The .info.yml file

To create a new theme for Drupal 8, The only real requirement is to make sure you have implemented the .info.yml file (YaML, like Camel). Drupal 8 runs off of YaML files much the way that Drupal 7 ran off of .info files.

As long as you have your .info.yml file in place with a few keys in place, you have a theme (although if thats all you have in place, it's not going to be a pretty theme).

### Create the theme folder and "YaML" file
1. Locate the _/themes_ folder in your Drupal installation. In Drupal 8, Contrib and Custom modules and themes, are saved at the root level _/module_ and _/themes_ folders.
2. Create a new folder and call it `acme`
3. In that folder create a new file. It should be called _acme.info.yml_
4. Add the following lines to that file

	```
	name: Acme
	description: My first Drupal 8 theme.
	type: theme
	base theme: classy
	core: 8.x
	version: VERSION
	
	regions:
 	  header: Header
 	  primary_menu: 'Primary menu'
 	  secondary_menu: 'Secondary menu'
 	  breadcrumb: Breadcrumb
 	  help: Help
 	  hightlighted: Highlighted
 	  content: Content
 	  sidebar_first: 'Left sidebar'
 	  sidebar_second: 'Right Sidebar'
 	  footer: Footer
 	  page_top: 'Page top'
 	  page_bottom: 'Page Bottom'
	```
5. Go to /admin/appearance and under the Acme theme choose "Install and set as default".

## Things we might find in a .info.yml file
The following keys are items that we will often find in a *.info.yml file. Some are optional, Some are requiered. These keys provide meta-data about your theme, and define some of the basic functionality.

1. `name` **Required** 
The human readable name will appear on the Appearance page, where you can activate your theme.

2. `description` **Required** The description is displayed on the Appearance page.

3. `type` **Required** The type key indicates the type of extension, e.g. module, theme or profile. For themes this should always be set to "theme".
    
4. `base theme` The theme can inherit the resources from another theme by defining it as a base theme. Not declaring this, will default to using "Stable" as the base theme.
    
5. `core` **Required** The core key specifies the version of Drupal core that your theme is compatible with.
    
6. `version` For modules hosted on drupal.org, the version number will be filled in by the packaging script. You should not specify it manually, but leave out the version line entirely.

7. `regions` Regions are declared as children of the regions key. You are required to have a content region. The regions we just declared are also the default regions that are enabled by core if you do not declare any regions in your .info.yml file. 

### Other items
1. `regions_hidden` will allow you to remove default regions from the output if you don't specifically declare any regions.

1. `screenshot: IMAGE_NAME.png` With the screenshot key you define a screenshot that is shown on the Appearance page. If you do not define this key then Drupal will look for a file named 'screenshot.png' or  'screenshot.svg' in the theme folder to display.
    
2. The `libraries` key can be used to add asset libraries to all pages where the theme is active.
	
	```
	libraries:
		- THEMENAME/global-styling
		- THEMENAME/LIBRARY-NAME
	```
Theme libraries contain css and/or javascript. Theme libraries are declared in another type of YaML file (THEME.libraries.yml). We will go over libraries in later exercises.

3. The `libraries-override` and `libraries-extend` keys can be used to take control over the components of a library, remove items or the complete library, or add additional elements to a library.

4. The `stylesheets-remove` and `stylesheets-override` key are used to stop the addition of css compontents for core and contrib modules or to introduce new versions of those components to those libraries. Similar to `libraries-override` and `libraries-extend` but specific to stylesheets.

	```
	stylesheets-remove:
      - core/assets/vendor/normalize-css/normalize.css
      - '@classy/css/components/tabs.css'
	```
	The stylesheets-remove key removes a link to a stylesheet added by another theme or module. The full path to CSS file should be provided (instead of just the filename), to accommodate cases where more than one file with the same name exists. In cases where a Drupal core asset is being removed (for example, a CSS file in jQuery UI) the full file path is needed. In cases where the file is part of a library that belongs to a module or theme, a token can be used. Note that when using the token it needs to be quoted because @ is a reserved indicator in YAML.
5. `ckeditor_stylesheets` will allow you to have custom ckeditor styles attached to your theme
6. `quickedit_stylesheets` will allow you to have custom styles and javascript attached to the quickedit functionality


## Questions you may have...
+ What happens if I don't declare any regions?
+ Why are some regions in `''` and others not?

## Done ☺