# ADDING TEMPLATES AND LAYOUTS TO A SITE VIEW

### Relationship Between Templates/Layouts In Views

[00:00:00](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

Now that we added a dynamic get to a site view and looked at how to access the data sets through the examples snippets, we need to understand how layouts and templates link into site views; to know what the site view in the code, the templates, and the layout in the code itself is and how Joomla do load these things. 

### Preacher View Example

[00:00:33](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m33s)

If we go to our example, (component, sermon distributor, view, preacher, and template or Tmpl) there are default.php, default_preacherbox.php, default_preacherpanel.php, and default_preachersmall.php files. [00:00:58](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m58s) There is a whole list of them. They are all templates. They are called templates because of the method by which they are included in the default file.

### Preacher Site View Example

[00:01:18](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m18s) 

The Default file is the main file. We call this the site view. (See video.) Everything in this file is built in the side view. Open the site view. This code here is in the default view. This is added to that default file. (See video.) It says default view.

### Location Of Templates

[00:01:50](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m50s)

It adds to templates with this snippet, 'thisloadtemplatepreacherpanel'. These snippets are at the bottom of the site view. If you scroll down, you will see the layout snippets and after them the template snippets. [00:02:19](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m19s) Scroll down to the one you created by looking at the names. It shows  'preacher', 'grid', 'list', 'table', 'panel', 'box', 'small'. These are the snippets needed. [00:02:37](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m37s) You might change this, perhaps stay in the PHP instead of going out into the HTML. What happens if you look at the code. From time to time go out of the PHP '?>', into the PHP with that tag '<?php', out of the PHP with that '>?', go in again '<?', go out again '>?', and then stay out. [00:03:04](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m04s) Here is pure HTML; this part is 'uikit class' and the implementation. (See video.) Go back into  PHP, out again, and HTML is found here. That is how PHP can be used in the view. [00:03:20](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m20s)

### Default View In Code

[00:03:31](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m31s)

Look at this in the code. (See video.) Open the 'default.php' file, and see what is placed there. End with PHP'>?' and go into PHP'<?' again. [00:03:45](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m45s) Here is the same text as in the editor. It gets placed here and through these snippets includes the template. A global setting is used. Check how the global setting is set in the component's global settings. Check the type of display that had been set. On that basis, either this or that template is shown, etc. (See video.) [00:04:22](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m22s) In the template view you have access to the same global fields, class fields, and public class methods that you have in the default view. In the default view, we have access to 'this preacher'; the same applies to templates. When templates are opened, 'this params', and 'this preacher' website is used. The same global class fields or values are used depending on how it is called. [00:05:07](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m07s) Go back to the interface. Component Builder  adds this template to this site view because of this code snippet. (See video.) Place the code snippet in there, and look in the template list for a template, 'loadTemplatepreacherpanel'. It will add it to this site view. (See video.) [00:05:35](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m35s) By doing this, templates can be added to the site view.

### Quick Layout Example Within View

[00:05:52](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m52s)

Layouts work somewhat differently. Is there a layout in this site view? Mostly templates had been used. (Templates and layouts can be used in the site view.) [00:06:06](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m06s) As most templates had been used, the layouts may have been used in the templates view. In case a layout must be added to the view without doing it inside a template, it doesn't matter; it's only a way of bundling the scripts in a more concise manner so that it is not so overwhelming when looking at the code but that you have it broken up. The layout structure is mostly used when you are dealing with part of the display area used across other display areas. [00:06:53](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m53s) At the moment a piece of code is used in more than one view or template. [00:07:12](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m12s) Template can be used in 'templates' but not inside layouts. Layouts can be used inside layouts. These are conventions set forth because of how Joomla implements the structure. These are not limitations because of Component Builder. [00:07:44](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m44s) Joomla allows adding templates to the default site view but not adding templates to a layout. 

### Explanation Templates / Layouts Within Joomla

[00:08:02](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m02s)

Templates have access to the global values, or the class values, whereas layouts do not. It is important that this value must be passed to the layout. The reason is that if you look at these snippets, we're passing it 'this items'. But you can pass it just 'this' or a specific value. [00:08:29](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m29s) If you have custom classes, you can pass it the specific value from the custom class.

When a layout is set up this area is where the dynamic get used in the layout is selected. (See video.) It won't add the dynamic get to the site view or the model. [00:08:53](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m53s) It only helps to view the snippets and set up this snippet. (See video.) If the wrong code is selected in the layout, it will change the way it looks, but it can be overridden. The snippet can be copied and placed in the code where it should be used. [00:09:18](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m18s)

The area passing the information to the layout can be changed because the layout does not have access to it. It should be passed through the values you want to use in it. This script renders a layout. (See video.) Component Builder needs to add a layout to the components layout folder. [00:09:51](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m51s) It checks for a layout with that 'name' in the layouts list. These layouts must be set up before they can be included in other views and templates. Note that the layout concept and implementation together with the template are the same in the custom admin view. It works exactly the same. [00:10:19](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m19s) By adding the snippet to the default view Component Builder is able to add the layout to the component and the layout template to the site view. [00:10:50](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m50s)

When looking at the code it can be seen how Component Builder builds site views. In the default view 'preacherbox' be seen in both areas; the same applies to ' preacherpanel', 'preachersmall', 'table', 'grid', and 'list'. [00:11:10](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m10s) This is how the code can be added in smaller portions.