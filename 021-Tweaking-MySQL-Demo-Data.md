# TWEAKING MySQL DEMO DATA

### MySQL tweaking in the component area

[00:00:00](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

Open a component (in this instance, 'Editting a component'). Go to 'settings', and you'll find a 'MySQL' tweak. What is its function? If you have multiple versions of a component and partly demo relating to a certain version of it and implementation of items and you do not want those items included in another version, there is the 'MySQL' tweak area where a specific view can be selected. [00:00:43](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m43s)

Note: This feature may only be used if you're using this area where we added database connection between the view 'dummy data' and 'view' itself. [00:01:07](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m07s)

If 'Field types', one of Component Builders own views, is opened and connected to the database through 'MySQL'; if 'yes' is added and table selected, then Field types are selected in the database and allows it all to be taken into the 'Build' file. (See video.) 

### Tweaking Feature

[00:01:33](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m33s)

Some of the versions distributed with Component Builder does not have all the field types. They are limited to a certain few field types. To explain what has been done, return to the tweaking feature. With Component Builder open, go to settings. [00:01:57](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m57s) In this tweak feature, added values may be seen; certain of them, like Custom Admin, had been set to 'no'. Do not include the add MySQL (to view table) if set in the view. [00:02:19](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m19s) If 'MySQL' was selected in the view it can be controlled which item's actual 'ids' should be included through this feature. As in the Admin View these two 'ids' (33,42) had been included from the database. They are the 'ids' in the Admin View table. It is ID based. There is the feature including all. (See video.) 

### ID Based

[00:02:46](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m46s)  

It is a function used to indicate what is needed here. (See video.) If 'ids' between 1 and 50 are used, this  arrow notation with an equals open bracket (=>) can be used to notate that between 1 and 500 you want to add. [00:03:15](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m15s)  Here, 1,2,3,4or1=>4, a comma is placed, 20, another comma and 40=>90, so in the same comma delimited list, this notation can be added to show that 1 to 4 has to be included, after 20 is added and all the ids will be grabbed. [00:03:41](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m41s) It eliminate any other ids and only use the ones that had been notated. Here is another example of using 1,4,23,199: it goes on from 597=>604,682=>684. (See video.) [00:04:08](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m08s) It is in the same comma delimited list, id based; include these by clicking 'yes'. That is what it can be used for. If dummy data or example data had not been included in the component build structure, this area is redundant and not necessary to use it at all. [00:04:46](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m46s) Ignore it if there aren't any data selected.

This feature helps with the management of dummy data between versions in your applications.