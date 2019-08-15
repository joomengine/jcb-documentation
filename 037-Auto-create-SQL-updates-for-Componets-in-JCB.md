# AUTO CREATE SQL UPDATES FOR COMPONENTS IN JCB

### Views Are Linked To Set Of Tables

[00:00:00](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)
 
I would like to demonstrate one of the latest features that have been added to JCB. A feature request had been made: "Auto-generate update SQL?". After a lengthy discussion, the decision was made to add the feature and now it is basically done. First, some background regarding it. When a component is created in Joomla, you have a set of views, and these views and the back end are linked to a set of tables.

### JCB Builds tables For Views On Installation
 
[00:00:38](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m38s) 

On the installation of the component, for example, as is done with JCB, it builds the tables for those views on installation. So if you go to the back end of the component, and create a new item, it stores the value in the database, that it can be retrieved.  [00:01:17](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m17s) As a developer make a change to this component which involves new tables, the extra script needs to be added to the components package upon installation. If it finds that there is already an existing component, it will update the database accordingly to the new settings, the new tables or any fields added. 

### Manually Adding New SQL Statements

[00:01:47](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m47s)
 
In JCB there used to be a way to do that, which still works. A way to manually add the new SQL statements that are needed to make the update, it was done under the Version Updates tab. You would click on Version Updates tab and would add your specific SQL query script, and upon installation, if the existing version is below this update, it will grab this and install it into the database creating the new tables. 

### Adding A New View/New Table To Component

[00:02:35](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m35s)

This Admin View has only 1, 2, 3, 4, 5, 6, views. I'm going to add another view to this component. These buttons are not ticked. It seems to be a Joomla problem because there are multiple columns in this view. If it is closed and clicked again it fixes that. I am going to add a new view called 'Help Documents' and make some minor changes to the defaults. [00:03:14](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m14s) Add it to the 7th position, click save and click save again. A new view has been added which means a new table to the database. We have not written any of the SQL, because with the new changes this is going to be done automatically the moment this component is compiled.  We are and This component is going to be compiled again. Its version is still 1.4.1. Then it gets compiled. 

### System Checking The History If There Is A New Table 

[00:03:51](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m51s)

The system is checking the history and it is making a lot of calculation to dynamically realize that there has been a new table increment version number. If this component is installed now, and if that component is opened that the new view can be seen. I'll see is here. If the view is opened it does not show any errors. [00:04:20](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m20s) If new is created, it automatically starts as expected. For instance, text: 'hi'. This targets the external sources. [00:04:43](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m43s) It may be seen that the database already stores the values, and the new table is therefore in the database and working as expected. This means that the JCB component has been updated. If this page is refreshed, it may be seen that the version number has been incremented. [00:05:14](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m14s) If the version updates are opened it can be seen when you scroll down, that 1.4.1 got this new creating of a help document table and a new version(1.4.2) got allocated. We do not know what is this (https//github.com/SermonDisributor) link and so we add this (https//domain.com/.zip) demo link here which you need to manually update still. That is by far a tremendous improvement. 

### Adding New Field To Existing View

[00:05:44](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m44s)

This also works not only with the adding of a new view, but also if a field is added to an existing view. To demonstrate: If a new field gets added to the Preacher view and any fields is selected, since it is going to be removed again. For example: Call it 'Image'.(See video) [00:06:27](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m27s)  Save and close. Now a new field has been added to preachers, and then return to the compiler, select the component and compile. Since it detected there has been a field changed, it incremented the version number. If the component is installed, it may be seen in the component in the Preachers view, that there is a new field, 'image'.[00:07:02](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m02s)  If an image is selected, and saved. _Oops, I actually missed it, the reason was that this component did not have any history.  A few changes are necessary._ 

### If Building A Component It Have History

[00:07:23](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m23s)

NB. If you are building a component from the ground, it will have history.  This is only going to happen when a component is installed via the import function in the components, or maybe when a demo component is used. It is advised to open all the views and save them at least once so that there is history recorded for that view. That is one of the drawbacks, there is currently no way to negate that issue.

 Since the history of each of these different items, being at the admin view and the fields need to be created the moment that the item is saved. It can not be done before then. [00:08:14](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m14s) Taking that in account, I will recompile it again and fix that. It should increment it to 1.4.3. I will install that again, then go back and refresh the Preacher. That image field is back. Select an Image. Click Save, and now it stores the data for this image. [00:08:49](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m49s) If the component is refreshed, and it has again incremented the version. If the update area is opened, it may be seen that it added this new 'alter' of the Preacher table, adding the image field. It also added the new [00:09:16](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m16s) version to this list.

This has been a demonstration of this new automated feature which is in its very beta phase. Please take a go at it, and if you find any bugs, look for other open issues, and start a comment. If you do not find any, then please open an issue and let us fix this issue. [00:09:55](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m55s)

I think this will be a tremendous improvement to JCB since it is even writing your update SQL for you, which makes it again one of the best Joomla component developing tools. 
