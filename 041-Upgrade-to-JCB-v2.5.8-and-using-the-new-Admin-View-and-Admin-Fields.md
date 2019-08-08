# UPGRADING TO JCB v2.5.8 AND USING THE NEW ADMIN VIEW AND ADMIN FIELDS

### JCB removing Repeatable Fields

[00:00:00](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)(_Click on this time links to see Youtube video_)

For example, Joomla is installed here with JCB Joomla Component Builder 2.5.6. Here is quite a lot of Components that has been imported from another JCB and all of them is functioning. For convenience sake Joomla has decided to get rid of this Repeatable Field, which pops up into a little model. It is being systemically removed from JCB.[00:00:54](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m54s)  It has already been done in other areas of JCB. Like in the Language Translation area. If any of these Language strings is opened(a'-ZA.ng-NA)Demo-used in 21), it may be seen that we already have the Repeatable Field set up.  

[00:01:21](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m21s) This would have been as simple as changing the Field Type within JCB. The reality is that the Compiler as well as one other feature which is the Joomla Components, can be exported and imported in JCB Packages. These features are mapping into these Component concepts, the Field structures, how data is stored in a 'json' by the Repeatable Fields, are different from how it is stored in the Sub Form Fields. 

### JCB 2.5.8, Whole Admin View Moved To Sub Form Layout
 
[00:01:59](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m59s)

There is few issues open on GitHub concerning this. [00:02:10](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m10s) We have taken on the task of supporting it all. With this next release which is JCB 2.5.8, the whole Admin View area will be moved over to the new Sub Form layout. If an Admin View - 'Look' is opened, it has the old Repeatable Field concept as could be seen in all the tutorials that had been given. [00:02:43](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m43s)  Permissions is one of those tabs, the Fields, the Conditions, the Linked Views. Then there is a list of the Fields that are linked to the Admin View and some Custom Buttons that can be set up, and it is also a Repeatable Field, as well as linking MySQL(select 'Table'). This is also a repeatable Field in a model.  

### Heads Up - Moving And Changing Of Fields

[00:03:13](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m13s)

All of these different Fields are going to be moved to Sub Fields, because of space and statistics, some of these Fields will be moved into tabs. It will be done in a way that you will not feel lost. Up front this Fields Button are going to be moved to the Fields Tab and so are the Conditions going to be moved there.[00:03:45](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m45s) There will be a new tab called 'Settings'. The Settings tab will be called Details. The rest of the Repeatable Fields that are remaining on this side will be placed there. That's just a heads up on what is going to happen. There is not much for you to do except to upgrade. 

### Add Number Of Scripts That Will Convert Fields and Tables etc.

[00:04:19](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m19s) 

A number of scripts had been added that can be looked at on GitHub. While this recording had been done this changes could have be seen at the 'Branch: staging',(See video) and if we would to go to the script, the script may be seen that will convert  the Fields and all the Tables and everything. 

### Convert Repeatable Function

[00:04:47](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m47s)

Scrolling down to that area a function inside of a method may be seen. It is more like an anonymous function. This is what converts the Repeatable Fields.[00:05:04](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m04s) This function will be used repeatedly as had been done with a upgrade to version 2.5.5 and then there is another upgrade 2.5.7 which was not released because  this change had been made, and we still need to convert the Repeatable Fields. That will continue to run until 2.5.9. [00:05:31](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m31s)(See video) The way it does this, the '$convertRepeatable' function target all these(ajax, custom_button, addtables etc.) fields inside the Admin View, and it passes it over to '$convertRepeatable', which is going to do the work and '$convertRepeatable' function as may be seen over here. If you are uncertain of doing this you can come and look at '$convertRepeatable' function here.[00:06:07](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m07s) It will be noticed, as with this website that we are working on, that there are thousands of values.  

### Model - admin_view.php - Changes Would take Place

[00:06:30](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m30s)

I have found that it sometimes does not convert every single value, and because of that, another change was necessary, which goes beyond and ensures that this upgrade will not cause any internal conflicts. That is within the Back end, within the Model. There are a few places where these new Fields will exist. [00:07:02](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m02s) One of them is 'admin_field_conditions.php' and the other one is 'admin_view.php'. If this 'admin_view.php' is opened, these  models in which these Field changes will take place is seen. It may be seen that within the 'getItem Method' at the very end of this method in the Admin View, a function was added which would check if this these Fields were updated during the upgrade. [00:07:27](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m27s) If it were not updated, while the field is busy loading and you are opening the page, it will check whether it has been updated. [00:07:52](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m52s) If it is not updated it will do the update, and add it to the update object and then check every Field, all the way down. If it detects that there has been any one of those Fields found ready to be updated, then it will run the update.[00:08:14](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m14s) After that it will never do it again. The way the array is constructed, will no longer be seen once it has been moved to a Sub Form Storage, seen that the Sub Form array structure is different. Once any of the items are opened, it will automatically be converted and ensure that it is converted.

### Checks - Converts - Updates

[00:08:46](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m46s)

Another thing that had been done, because you most probably will not open every view or every Admin View. Even in the new admins fields the same had been done. In the Admin fields, it has been ensured that that update is there, and the same with the Admin field conditions, it is there as well.[00:09:09](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m09s)

But there is one more place where these checks are added and that is in the Compiler. Even if you did not open any of these views and went straight to the Compiler, and try to compile any of your Components, the Compiler  has now been adapted to instead use the new Sub Form Structure within its compilation.  

* ### Checking

[00:09:38](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m38s)

Within the Get file where most of these sub forms are now needed, we have in the 'getAdminViewclass' method and it may be seen that we are checking whether it is still in a Repeatable Field. If it is, we convert it. [00:10:04](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m04s) Again store it to the update object while it is getting this one Admin view at the very end. Every where it is doing it, it checks, if it is not being converted. 

* ### Converts

[00:10:15](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m15s)
 
It converts it and sets it back to the data set, and this string '$objectUpdate->addpermissions=json_encode($bucket);is used to ensure that it gets stored in the database. So it does everywhere where values may have been missed. 

* ### Updates- never need to be updated again

[00:10:35](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m35s)

If any updates are found at the very end of this function, a update should be run, and after that view has been updated, it will never need to be updated again. These are the kind of mechanisms that had been put in place if you have a JCB with a huge amount of data which is to much for a normal install. Then all these Admin views will be updated and adapted as you start using JCB and there should not be any conflicts. [00:11:27](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m27s) If you do experience conflicts, open an issue on GitHub, so that I can do the necessary adjustments.   

### Installing The Upgrade v2.5.8

[00:11:50](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m50s)

Getting back to the Install. Open this Admin View - 'Look', and then install the upgrade.  Select it, it has not been released yet, so this is a pre-demostration.  A file is selected from my computer(See video). Since it is quite a huge data set it may take a while for the installation to be completed. [00:12:47](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m47s) In this case the upgrade to version 2.5.8 has been successful. 

### New Field And Conditions View

[00:12:55](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m55s)

If that Admin View is opened and then refreshed, the changes will be seen(see video). There is now a Settings Field and as may be seen, all the data has been updated and moved to Sub Form values. The same with Tabs. Going to Field and Conditions, it may also be seen how the new Field and Conditions View looks like. [00:13:32](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m32s) Due to many reasons it is not advisable to keep the Sub Form Fields within the Admin View, especially when there are more than 50 Admin Fields, because it causes a tremendous slow down on page load. Taken into consideration that each of these lines, are 1 - 13 fields and the limit is set to 800, which may be a time consuming process to load all that into the page. 

### How The Field And Conditions View Works?

[00:14:15](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m15s)

How does it work? Either click on the Edit button - Linked Fields, or the Edit button - Field Conditions to go and edit these and change their values. If one specific field is edited, click on any of these pencil editing links. For example: If I click on 'Name'  it will ask whether I have saved all the values in this current view, and if it has been done; click 'OK'.[00:14:46](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m46s) It will open the Name Field and now any edits may be done in here and then save and close, or just close again, if only some information was needed. 

### How To Edit Custom Fields

[00:15:00](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m00s)

Back into Editing the Admin View area. The same applies to the Custom Fields. Click on any of those to edit them or click on this Edit button. It will again ask if I have saved all the work, then if it has been, click 'OK' and it opens these values(See video) . A nice new tweak which had been added, is that it only loads the Fields that are linked to this Admin View(Match Field) so that the specific Fields can be targeted, which makes sense.    Those are the fields that needs to be targeted with this conditional option. 

### Creating Field - Available

[00:15:42](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m42s)

Then a field can also be created . Creating a field will not necessarily add it to the Admin View, it will just make it available to you, if it were added by going to Admin Fields .[00:15:57](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m57s) The Edit (Linked Fields)button is the same as 'Edit admin fields conditions for this admin view' but it is a shortcut, because sometimes you might have a lot of fields, and it is way down there to get to conditions. Some shortcuts had been added up here(See video). There is also the tutorial on how to use this but the tutorial still was made when we had the old Fields layout. It should still make sense but just keep in mind that things had changed a little. You could click on any of these links to open that area where the fields are now found and make the changes. [00:16:27](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m27s) That is the new Admin Fields.

**To move away from Repeatable Fields to start using Sub Forms for all the Repeatable concepts is what this upgrade is all about.** 
 

### Shortcut Buttons - First Button, Admin Fields - Second Button, Conditions

[00:16:53](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m53s)

There is one heads up concerning something that is a little different to how things were done previously. Close and go out of this Admin View. It may be mentioned that here(buttons below a view) is a shortcut to get to the Admin Fields without opening the Admin View and then the Admin Fields. If the right button is used, it will automatically open the Admin Fields. Changes may be made and it is linked to the Look Admin View and the same applies to the Conditions. The second button is for conditions. 

### Create New Admin View: Adding - Single Record Name, List Record Name, Short Description, System Name

[00:17:35](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m35s)

What has changed? If a new Admin View is created, a Single Record Name, the List Record Name, the Short Description, the System Name are added. That is all that should be added to save the Admin View for the first time. [00:17:51](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m51s) The Admin View at this stage, cannot be linked to any fields until it has an ID. At this stage since the Admin field does not have an ID; It is still new, because we have not clicked save even once. No Fields can be linked to it. What needs to be done is to add some Name(test), and save it once. If the has been done; go to Fields and Conditions; and will give a 'Create' option. [00:18:57](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m57s) The buttons 'Create' and 'Create admin fields for this admin views' is the same button. Click on any of them to Create Fields. If you Create a field, then give a 'OK' to indicate that everything is saved . Then click on the plus '+'. The first field is opened and you can start to add fields, and tweak them as you would before. [00:19:22](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h19m22s) That is the new Sub Form Fields for Admin Views. That is what this upgrade is all about. This will in future make a transition into Joomla 4 easier. 
