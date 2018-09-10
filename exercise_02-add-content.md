#### [Drupal 8 Theming](README.md)

# Exercise 2: 

## Auto Generate Content

You can easily create one or two items of content in Drupal, but what if you need to test out what 50 nodes look like in a view? What if you need to know how the page is going to look with a couple dozen comments all at different levels? Are you going to create each one of those items by hand? Hopefully not. Luckily, we have a handy module that has already been ported to D8 and is (mostly) able to take care of this work for us. Enter the "Devel" and "Devel Generate" module.

1. Enable the **Devel generate** module if you have not already.

### For vocabularies and taxonomy terms
1. Click "Configuration" in the Admin menu.
2. In the `Development` group select `Generate vocabularies`.
	1. Number of vocabularies?: `2`
	2. Maximum number of characters in vocabulary names: `20`
	3. Click the **Generate** button.
3. Click "Configuration" in the Admin menu
4. In the `Development` group select `Generate terms`.
	1. Vocabularies: **Select "Tags" and one other vocabulary**
	2. Number of terms?: `10`
	2. Maximum number of characters in vocabulary names: `15`
	3. Click the **Generate** button.


### For content

1. Click "Configuration" in the Admin menu.
2. In the `Development` group select `Generate content`.
	1. Select Content Types `Article` and `Basic Page`
	2. How many nodes would you like to generate?: `25`
	3. How far back in time should the nodes be dated?: `1 year`
	4. (If comments enabled) Maximum number of comments per node: `5`
	4. Maximum number of words in titles: `10` 
	5. Leave the rest at their default values
	3. Click the **Generate** button.


### For users and menus
1. Feel free to generate users and menus using the same procedure.

## Questions you may have...
+ Can I generate content from the command line?

## Done ☺
[Exercise 3 - Contrib Themes](exercise_03-contrib-themes.md) is next!