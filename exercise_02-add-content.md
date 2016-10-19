#### Drupal 8 Theming

# Exercise 2: 

## Populate some content

It’s hard to theme the content of a site when there is no content. So, before we really dive into the good stuff, lets first creating some content.


1. In the admin menu, click "Content", then "Add content", and then click "Basic page". 
    1. Title: `About`
    2. Body: `This is my awesome site that im making at BADCAMP in Berkeley, CA.` (Or filler text from wherever you want.)
    3. Check the box to **Provide a menu link** and leave all defaults.
    4. Click the **Save and publish** button.
2. Click "Content", then "Add content", and then click "Article". 
    1. Title: `An Interesting Article`
    2. Body: `We’re preparing to launch a new Drupal website full of interesting articles like this one.` -- (Or filler text from wherever you want.)
    3. Tags: `website, Drupal`
    4. Upload an Image of your choice with Alternate text of your choice.
    5. Click the **Save and publish** button.

## Auto Generate Content

The above process is fine for one or two items, but what if you need to test out what 50 nodes look like in a view? What if you need to know how the page is going to look with a couple dozen comments all at different levels? Are you going to create each one of those items by hand? hopefully not. Luckily, we have a handy module that has already been ported to D8 and is (mostly) able to take care of this work for us. Enter the "Devel" and "Devel Generate" module.

### For content

1. Enable the **Devel generate** module if you have not already.
1. Click "Configuration" in the Admin menu
2. In the "Development" Group select "Generate content" 
	1. Select "Content Type: `Article`
	2. How many nodes would you like to generate?: `100`
	3. How far back in time should the nodes be dated?: `1 year`
	4. (If comments enabled) Maximum number of comments per node: `5`
	4. Maximum number of words in titles: `10` 
	5. Leave the rest at their default values
	3. Click the **Generate** button.


### For vocabularies and taxonomy terms
1. Click "Configuration" in the Admin menu
2. In the "Development" Group select "Generate vocabularies"
	1. Number of vocabularies?: `2`
	2. Maximum number of characters in vocabulary names: `20`
	3. Click the **Generate** button.
3. Click "Configuration" in the Admin menu
4. In the "Development" Group select "Generate terms"
	1. Vocabularies: **Select any one vocabulary**
	2. Number of terms?: `10`
	2. Maximum number of characters in vocabulary names: `15`
	3. Click the **Generate** button.


### For users
1. Click "Configuration" in the Admin menu
2. In the "Development" Group select "Generate users"
	1. How many users would you like to generate?: `10`
	2. Which roles should the users receive?: **Select a role or leave unchecked depending on what role/setup you would like to test**.
	3. Password to be set?: **Set password or leave blank**
	4. How old should user accounts be?: `1 week`
	5. Click the **Generate** button.


### For menus
1. Click "Configuration" in the Admin menu
2. In the "Development" Group select "Generate menus"
	1. Generate links for these menus?: `Create new menu` & `Main navigation`
	2. Number of new menus to create?: `1`
	3. Number of links to generate?: `5`
	4. Maximum number of characters in menu and menu link names?: `12`
	5. Leave defaults for rest or tweak to your desired needs
	5. Click the **Generate** button.

	
## Questions you may have...
+ 

## Done ☺