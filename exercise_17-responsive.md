#### Drupal 8 Theming

# Exercise 17: 

## Breakpoints and setting up responsive images

Using the Core Breakpoint module, you can now define your theme’s breakpoints in code. There is no UI for doing this, but we have a solid API from the Breakpoint module that allows modules and themes to define breakpoints and breakpoint groups, as well as resolution modifiers that come in handy when targeting devices with HD/Retina displays. To keep this exercise a little simpler, we wont wont worry about modifiers for HD displays. 

Find **toolbar.breakpoints.yml** for and observe how the breakpoints correspond to the administration menu styles.

**Make sure Breakpoint (breakpoint) and Responsive Image (responsive_image) modules are enabled**

1. Visit your modules page, under the "Extend" button in the admin menu.

2. Enable the Breakpoint and Responsive Image module if they are not enabled

### Create the breakpoints

1. Navigate to your theme root directory

2. Create a new file called **acme.breakpoints.yml** and 
    
    ```bash 
    $ cd MYDRUPAL
    $ touch themes/acme/acme.breakpoints.yml
    ```
3. Open the file in your preferred code editor and add the following.

	```
	acme.mobile:
  	  label: mobile
  	  mediaQuery: '(min-width: 0px)'
  	  weight: 0
  	  multipliers:
        - 1x
	acme.tablet:
  	  label: tablet
  	  mediaQuery: '(min-width: 601px)'
  	  weight: 1
  	  multipliers:
        - 1x
	acme.desktop:
  	  label: desktop
  	  mediaQuery: '(min-width: 961px)'
  	  weight: 2
  	  multipliers:
       - 1x
	```
	
3. Clear cache.

Together, all of these breakpoints are referred to as a **breakpoint group**.
The weight of these is crucial so that the proper image styles get swapped in depending on viewport size and screen resolution. A breakpoint’s weight should be listed from smallest min-width to largest min-width. Also, note the “multipliers” section. Breakpoint allows for different pixel density multipliers for displaying crisper images on HD/Retina displays: 1x, 1.5x and 2x.


### Create your Responsive image style

We now need to bring the breakpoint group information and the image styles all together. We do this with a **Responsive image style**. 

1. Navigate to **/admin/config/media/responsive-image-style** and "Add responsive image style"

2. Create the style using the following information:
	+ Label: `Acme Image`
	+ Breakpoint group: select `Acme` 
	+ For each breakpoint, choose: `Select a single image style` and set the image style that you want along with each breakpoint.
	   +   1X DESKTOP [(MIN-WIDTH: 961PX)] => Large (480x480)
	   +   1X TABLET [(MIN-WIDTH: 601PX)] => Medium (220x220)
	   +   1X MOBILE [(MIN-WIDTH: 0PX)] => Thumbnail (100x100)
	+ Fallback image style: Medium (220x220) .

We now have a Responsive image style, with the breakpoints matched to an image style. Now it is time to apply our Responsive image style to an image field

### Configure the display of our image field

1. Navigate to the Manage display page for the "Article" content type.

2. Change the format for the `Image` field to use `Responsive image`.

3. Select `Acme Image` as the Responsive image style we want to use.

4. Click **Update**, and then click **Save**

5. Clear caches, and then visit an article node with an image.

If you have responsive testing tools in your browser, use those to manipulate the size of your "Screen". If not just make your window smaller until you can start to see the images changing size.

## Done ☺