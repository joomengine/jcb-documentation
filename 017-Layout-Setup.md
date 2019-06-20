# LAYOUT SETUP

### Layouts

With setting up layouts there are some nice ways to reuse code across multiple templates or site views. We need to know which site view is calling the layout and on which basis we can use global settings related to that specific site view. [00:00:31](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m31s)

### How Layouts Work With Dynamic Gets

I've added a little string in the dynamic get since each dynamic get targets only a specific site view. Open sermon (preacher.id) which would primarily be used in preacher side view. Look at the custom script, where I added a view key called preacher. Since this dynamic get is only used in the preacher view, when the layout is called and you in your component, you'd only pass one item, not the whole list of items. [00:00:59](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m59s) This specific item calls from preacher, on which basis you can do a certain implementation to ensure that the layout displays the way you expected. [00:01:24](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m24s)

### How Templates Call Layouts

Open the template that calls the layout. We want to see the initial setup. One of the templates that illustrates this well is the sermon list. [00:01:54](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m54s) Open sermon list where you'd see that I'm looping through the items then adding some parameters to the item object. One of them is the params, the other takes the description, making sure that it's escaped and no longer than 90 characters. [00:02:26](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m26s) I add that back to the description without the full name, then add the item to the 'JlayoutHelper::render(study class render)(sermonlist item)' as the layout name which will populate the script between the list items that will be placed in an unordered list on the sermon list page. [00:02:46](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m46s)

### Sermon List - Item Layout

Let's look at this specific layout: 'JlayoutHelper::render(study class render)(sermonlist item)'. [00:03:15](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m15s) Look for sermon list item in layouts. In sermon list item you will see that I'm using the global; the item being passed is placed inside the displayed data. Display data is the item object. [00:03:43](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m43s) Since the parameters are placed in it, you can use the get method with the specific global field name, set in the components global settings.

### Using The View Key

Since I'm targeting a specific view, I use the view key, adding it to the string, checking the value for this specific view in the global of the component. [00:04:02](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m02s) On that basis I'm able to make this view dynamic; and can use it through multiple layouts based on that view key. If others want to use the layout in their components extending this one might not work too well, but since we use it for our own component and implementation, it's not too big of a deal. [00:04:31](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m31s) At the same token I am able to check what the view key is. Is it preacher, series, or category? On that basis I ask different questions and have different implementation of certain values like series name, preacher name, and category.

### Layout To Template Custom Scripting

In the template, go back here and go to custom scripting. (See video.) [00:05:11](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m11s) There is the ''[[[sview]]]' placeholder. The ''[[[sview]]]' placeholder will be replaced with the actual view's name. This is a template since we use a template here. [00:05:32](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m32s) I'm adding the template (this sermon list) to multiple site views, not to one site view. A template can be build and reused in multiple site views simply with this place holder,''[[[sview]]]' which is called site view.


### Dynamic Custom Views using Template

Since this template again need to be dynamic, so wherever it is added, it should dynamically add that site view's name. [00:05:57](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m57s) Then get from the global parameters that site view 'sermon_list_style'. It is going to add: 'preacher', or it's going to add 'series', or it is going to add 'category' . Then it displays: 'category', 'sermons', 'list', 'style'. 

### Above In The Code

Looking to that in the code. With 'category', 'preacher' and 'series' open. [00:06:30](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m30s) Then 'sermon-grid', 'sermon-list', 'sermon-table' is added to them all. If 'sermon-list' in 'series' is opened, it will be seen that 'name' has been changed to 'series'. If 'sermon-list' in 'preacher' is opened, it has been changed to 'preacher'. [00:06:53](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m53s) If  it is opened in 'category', it can be seen that 'category' has been added to it. Consequently the place holder has been dynamically updated by Component Builder. 

### Config.xml

Where is it getting these values? [00:07:20](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m20s)  Go to the component in the back end, and open it's 'config file' and scroll down. An area called 'preacher_custom_config' can be seen, which is a tab, and the tab's name is 'preacher'. [00:07:48](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m48s) In this tab there are: 'value_preacher_display', 'preacher_box_contrast', 'preacher_list_style'. Scroll down, and see 'preachers_sermon_count', 'preacher_email', 'preacher_website', and then 'preacher_sermon_display', and 'preacher_sermon_list_display'. Now if we take that 'sermon_list_display', and search for it across the file.  [00:08:13](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m13s) Make it cap sensitive. There are 3 matches: 'Category' 'Series' and 'Preacher' which are the 3 different views that make use of that 'series list style'. [00:08:33](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m33s)  The 'series list style' is then being implemented on the basis of that dynamic updating of the string. It gets the style, then does a switch statement and sets it accordingly. This is a nice to have tool to make a template more dynamic. [00:08:57](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m57s) As already mentioned a template can be build and reused in multiple site views simply with this place holder,''[[[sview]]]' which is called site view.

### Layout Concept

The layout  concept is more or less the same as with templates.[00:09:27](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m27s) It has a layout area in which you put your script and here (see video) the key replacing is used. If certain dynamic gets are selected , the liberty is taken of showing that we are starting with display data. But this snippets here(see video), might not correspond to what you're doing because you can really pass anything to a layout. We are just assuming that if you're using that dynamic get, you possibly passing it in this  way or that way. [00:10:06](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m06s) You can't copy and paste this necessarily. At least you can know when you look at a specific dynamic get, that that are the values in it and how you can try figure out which ones to use. This again will be only really something you can use if you are actually aware of that PHP will do the implementations. [00:10:34](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m34s) If you are not familiar with it, it is not necessary to use layouts. The whole front end may be build in the site view. It will work although it might be a  lengthy script. Layouts and templates has been added simply for convenience. 

### Layout Custom Script Area

In layouts is the same concept of adding custom scripting which will be placed in the head of the file. Remember that the global data or the data being passed is in 'display data' [00:11:14](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m14s) This is a HTML area but you can go into PHP and check some values and on the basis of that, do the necessary implementations. That is setting up a layout. 

### A Note: Use Layout in a Layout

A layout can be used in a layout. You can pass any value. [00:11:42](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m42s) Keep in mind that 'this' does not exist on the layout page. The display data needs to be used as the 'global' or as the 'main object' from which to start your implementation.
