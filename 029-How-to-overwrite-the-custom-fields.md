# HOW TO OVERWRITE THE CUSTOM FIELDS

 ### Using Default Fields With Custom Code

[00:00:00](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

It may happen that you would prefer to use some of the default fields in a different manner than that of Component Builder's way of implementation. What is the default fields? [00:00:12](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m12s) If you add a new Admin View or go to an Admin View that already exists, there is this note above Adding Fields. It indicates that the 'ID', the 'asset_id', the 'state', the 'access', the 'ordering', the 'created_by', the 'date_created', 'modified_by', 'date_modified', 'checked_out', 'Check_out_time', 'version', 'hits', 'metakey',  'metadescription', and 'metadata' has already been added to the view. [00:00:41](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m41s) These are the default fields that gets added to the view even if you do not create them. In fact, it is not necessary to create them. Sometimes you might want to display some of these fields in a different area of the application. Currently, the ID field and the State field are the only fields being shown by default in the List view. [00:01:20](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m20s)

* ### Example Of Default Fields Displayed in List view 

In the Experts area the 'Id field', the 'Status field', and the Ordering field are shown. The Ordering field does not show the order number. To be able to move and order it, click on "Up/Down". [00:01:45](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m45s) All that is done by default. The other values are not displayed in the ListView. Once a client requested that it should be possible to see the date on which something had been created as well as the identity of the person who created it. Component Builder then must be adapted so that those things could also be overwritten.

This is what has been done: If a field is created in Component Builder, as a field would normally be created and any of these names should be given to it, 'Created by' or 'Created date', but exactly the same name. [00:02:23](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m23s) Then it will overwrite the default.

* ### Example Create_By Field In View

In this specific Job Order view, there is a field 'Created-by'. It may be opened in a new tab. There is also a field 'Created-date'. [00:02:57](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m57s) In this field the 'Name', 'Created_by', and 'User' are the types of field that are used. The label is 'Created by', and the user that 'Created this' is the description. [00:03:26](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m26s) That's all that is needed for a user type. In the 'Created-date'(which is a calendar type,) 'Created', the date, it was created, the label and some of its defaults are used.

### Compiled In Code

[00:03:46](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m46s) 
 
If these values are unknown it can be seen in the compiled field. [00:03:51](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m51s) Open 'Administrator' in the back end of the component and open the relevant component. If 'Models' is opened, there is a place called 'Forms'. When it is opened, a list of forms may be seen that correspond to the back end views that you have created. In this instance, this 'Job Order' is the one. [00:04:19](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m19s) Open the XML, double click on it and scroll down. 'Modified by' and some of its default can be seen. So this value must be overwritten; these values must be updated or used. [00:04:45](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m45s) 

NB. This is the only part that should not be changed. If it is changed, it will not be known if an attempt has been made to overwrite one of the default fields because it uses the name as the identifier. Back in Editing the fields that were created was the first part. Close them again.

### Adding The Fields

[00:05:06](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m06s)

When any other field is needed go to fields. (If 'Settings' is selected in Editing the Admin view.) Those fields can be added. The 'Created-date' and the 'Created-by' is there. Both are added to be shown, as is the position and how it should be treated. It had been set in the 'left tab' of the '15th'.

### Adding In Tabs(default 15 tab)

[00:05:41](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m41s) 

If you would like the fields to be displayed in the same place as before, in the Edit view, add it to the '15th' tab. It is unlikely that so many tabs would be created.  
What is a tab? If you would go to the view, these are tabs 1 2 3 4 5 and 6. Since publishing may vary. [00:06:14](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m14s) It does not make sense to target it in any way directly as the 5th of the 4th. So a high number like 15 is chosen. If number 15 is selected, it will add these two fields in the same place it would have if it had to build it for you. But if for some reason the field should be displayed in a different tab, it may be selected, placed in the 3rd tab, and saved. [00:06:53](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m53s) Compile the components and install them. 1, 2, 3, will appear in the third tab. Indicate in what tab it should now be displayed. Now the 'Create' date no longer shows in the 'Publish' tab. It is only created by what shows up here. (See video.) [00:07:24](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m24s)  The field is moved to a different tab, and displays the field in the List view as well because the fields were added and set to be displayed and added to the third tab. It is moved back to number 15 which is its default place. Save, compile, and install it. [00:08:03](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m03s) Update the component. Refresh the page. It is no longer seen in 'Documents', 'Production', or 'Stock list'. It is back in 'Published', the correct place. There it will be set if it is not overridden, using the 15th tab as the target places it in its default place. If another tab number is used, it removes it from its default place and puts it where it is assigned.
That is how you can overwrite the Custom Added Fields in the back end view. [00:08:49](https://www.youtube.com/watch?v=FHQfIhWHYyQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m49s)  