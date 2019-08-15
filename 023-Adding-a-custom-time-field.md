# ADDING A CUSTOM TIME FIELD

### Fields

[00:00:00](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

* How to set up a Time Field

In programming, time must always be linked to a date. Since time is stored as an integer, if you want a field where a time is set, (for instance 5:15), a normal text field can be used and a Regex method created. [00:00:21](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m21s) This could be done via a custom form filter. [00:00:51](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m51s)

* How to set up a Custom Form Filter

To illustrate: Use 'sermondistribitor' component, go to 'modules', and 'rules' can be seen. There a 'rule' can be created. It is used as the filter name. [00:01:23](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m23s) Create a file in Component Builder and place it in the Custom folder and put any name in. (See video) One of these files can be used to illustrate how to include it. 

### Joomla Form-rule Example

[00:01:54](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m54s)

Here is some documentation on how to create a rule. Go to Component in Joomla: 'Libraries', 'Form', and 'Rules'. [00:02:21](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m21s) Any of these rules may be opened. See what had been done and follow the same convention. 'JformRule' is extended. Give it a unique name. Make sure it isn't one of these in 'JformRule'. [00:02:43](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m43s)  Component Builder already constructed the XML document used in the construction of 'Form'. 'Component', 'Sermon distributor','Models', and 'Form' are opened, as is series.xml as it already includes the Rule path. [00:03:17](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m17s) That Rule path is this 'Rule.' (See video.) To apply a filter, add 'filter='. In Component Builder there is a way to add this; but it would be the same name, 'Tel', as the filter name. [00:03:48](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m48s) Here is a 'test' that sees whether this is acceptable. (See video.) A Regex may be done to validate whether the input field on the server site is acceptable. [00:04:10](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m10s) This is the server site verification of the input.

### Component Builder New Text Field

 [00:04:15](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m15s)

When 'new' in Component Builder Fields is clicked, 'New Fields' will be opened, and 'text' is selected. [00:04:44](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m44s) 'Filter="string"' as well as 'validate' is found there. The 'rule' name is placed in 'validate'. The custom rule name might be, for example, time, and would ensure that only time had been submitted on the server site. 

### Script JavaScript

[00:05:00](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m00s)

The next step is ensuring the user only types in numbers and a colon, not anything else, and would be able to do JavaScript in the view footer. [00:05:37](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m37s) JavaScript targeting the field by either adding a unique class name or going to the 'form' may be added. For example, This 'name' is a field. (It uses firebug.) It selects the 'name' field and the 'id' may be seen in firebug. With JavaScript, the input of the 'id' can be targeted. [00:06:02](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m02s) If the 'id' has input and it is not what is expected from 'time', the user can be informed or the box may be emptied with a note underneath. That, however, would be a JavaScript implementation on top of the text field. If time is needed and it does not matter that a date is involved, a field like that had already been build. [00:06:36](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m36s) The calendar field can not be used in the repeatable fields.

### Time-Date(Custom Component)

[00:06:46](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m46s)

A field had been created making it possible to still do that. For example: If 'Events' is opened on the Registry Dashboard there is a function where dates may be set. [00:06:58](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m58s) There a date can be selected, the time adjusted, before 'Done' is clicked. [00:07:26](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m26s) With that selection the field is updated. If that is the kind of field you're looking for, the implementation is different when this kind of field is used. (See video.) For example, Fields are opened, 'text' selected in the 'Type' column, and a hint is added. (You can pause the video and look at the field XML.) [00:08:08](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m08s) Since the field is used in a repeatable field, the JavaScript is different; you worked with a repeatable field where you could add as many fields as you like. However, you wanted the date field to be active on each of those and you could not target a repeatable field by adding JavaScript in the area unless the field's ID was known. [00:08:41](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m41s) Instead of doing it here, the necessary Javascript has been added to make the field functional in the repeatable fields structure.

### JavaScript Repeatable Field Time-Date

[00:08:46](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m46s) 

If Field is opened, select 'Event Dates'. One of the values (in the XML Field Definition), '1196', is the ID of the date field. (You can pause the video and follow what is being done.) [00:09:24](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m24s) In 'Scripts' some styles are included as well as some JavaScript. There is a loop looping 50 times. Looking at the Repeatable Field, only 50 fields are allowed to be added in the loop that is targeted through the dynamic PHP. [00:09:52](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m52s)  Each of those fields is targeted. There is a row added. Check whether the row exists. If it does use the 'jQuery DateTimepicker', which is brought to the page by the script. It has some tweakable options. [00:10:19](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m19s) That's how that kind of date selecting picker method is added in a Repeatable Field. [00:10:43](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m43s)

### Multiple Date Fields

[00:10:51](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m51s)

If you open 'Dates', there is a start and an ending date. In Cost Adjustment, there is also a target date. [00:11:14](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m14s) In the script there is a 'field type' array used to target the different fields in their different pop-ups. If only one field is targeted, the extra iterating method or variable is needed. Instead of retyping it for every field, there is a loop added in the PHP. It is just less code. [00:11:44](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m44s)

Further documentation might be necessary but time does not allow. It would be encouraged, however, if it can be done as a community project. [00:12:14](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m14s) Everywhere in Component Builder, in any of its list views, there is a Help Menu that opens a website with a Wiki option. [00:12:39](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m39s) It's a Readme website. Here is the URL for anyone who wants to get involved in in the community to improve the documentation per list view as well as per function. (See video.) As you can see I've done a bit in writing documentation for every list view, explaining the buttons. [00:13:11](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m11s) This help button here; you can add your own help by going to the help documentation. Here is the list of already set up help. If you open one of these, you will see the URL we're using. [00:13:46](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m46s) As we develop this component further we would eventually add more help documentation in the component. It will map to this website because that way everybody can benefit from the improvements. [00:14:10](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m10s) The website URL is [Readme](http//projects.vdm.io/projects/Joomla-component-builder/wiki) You can go there and navigate from there. If you want to get involved in the editing of the tutorial or the documentation, contact me, and I will help you setup documentation. [00:14:40](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m40s)