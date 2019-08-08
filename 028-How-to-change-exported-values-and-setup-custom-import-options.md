# HOW TO CHANGE EXPORT VALUES AND SETUP CUSTOM IMPORT OPTIONS

[00:00:00](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

* ### Example Components

This is a short explanation on how to change the values being exported and to have a Custom Import option with an import of the data. Component Builder allows you to have an Import and Export function by default in all the List Views of the components. [00:00:35](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m35s) The component called IP Data is used to take an IP address and translate it to determine from which country it came. Then a costing update is performed on your website based on that IP Data.

 * ### Example IP Tables

Select IP Tables. (It is on the IP Table Dashboard.) [00:01:07](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m07s)  The 'CNTRY' value may be seen: the country and the 'REGISTRY' which indicates to whom the IP table belongs, and the range, 'IP from'/'IP to' is reflected. 

### Export Feature

[00:01:26](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m26s)

If 'Export Data' had been clicked without selecting any values it will give a warning. ('Please first make a selection from the list'.) [00:01:35](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m35s) Only values selected may be exported. If all have to be exported change the value to 'all'. In some instances, if the table is too long, it might not possible to export all the values at once.

Exporting data in large quantities is not advisable in Joomla. If quantities exceeds 3000 items, go to MySQL instead and get a dump file. [00:02:16](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m16s) Although it is often seen that the Listview is used for up to 10000 items complex inheritance in structure is involved. But in this instance it is different, having the import and export in mind. If, for example, this must to be exported but for some reason this 'ZZZ' or 'AUS' value must instead be replaced by the country name, the following would be a simple implementation of how to perform it.

### Exported Example In XLS Format

[00:02:51](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m51s) 

Click 'Export' and save this. (Opening Ip_tables). It has been exported, all these AUS values are displayed, as are some other values from the database as expected. But if it is supposed to be a different value than when it is exported, take the next step.

 ### Export Data In Code

[00:03:26](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m26s)

Component Builder has the 'getExportdata' method in the model. This method has an extra value called '$_export' which is set to 'true'.[00:03:52](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m52s) Targeting this method with custom scripting is one reason why this had been added. But the difficulty is that this part ($group to $query) is custom scripting and has also been added into the actual 'getlistquery'. [00:04:21](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m21s) It is the same custom scripting. In the compiler the same custom script is added into the 'getlistquery' as into 'getExportdata. The way to know where it gets executed is through the value, '$_export'. [00:04:49](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m49s) This value is not set in the 'listquery' only in the Export Data.

### Admin View - PHP - (GetListQuery)

[00:04:54](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m54s)

The custom scripting is done in the 'Editing the Admin View' area. With the Admin View open, go to PHP and then  scroll down until the method 'Add PHP (getListQuery - JModellist)' can be seen. It should be set to 'Yes'. [00:05:43](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m43s) The code placed there is added to both 'getListQuery' and 'exportquery'. If the values that had already been exported must be changed, not the values being shown in the component, it must be done in the same area. Notice that the same code appears in two distinct places. (See video.) [00:06:22](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m22s) If some value must be changed, it can be done by adding another 'lookup' and this '$_export=true'. To see where all this '$_export=true' appears go to any List model, search, and it may be seen in various places. (See video.) [00:06:55](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m55s)

Go to the 'getExportdata' area. In the previous tutorial it had been explained how to add some customization to the values in the 'listview', some HTML. Here it should be determined whether the 'export' is 'set' or whether it is 'true'?

NB. Don't add this feature here. [00:07:25](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m25s)

Adding this customization of coloring is avoided because it should not be running during the export process. Only the values are needed. Again, see that the export values are used. [00:07:53](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m53s) Those are the places where the export function is involved. By using '$_export' it is possible to identify whether it's an export or not. If it is, changes to the values can be made as necessary. Going back to the back end to show that this PHP area is the place where the query had been done.[00:08:30](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m30s)

It can be verified whether an export had been done in the area: 'Add PHP(getitems Method-before the translation fix & decryption)'. This can be taken instead of the exclamation. (See video.) If export is '(isset($_export)' and 'true''(isset($_export)&&$_export)', then, in the area below what is necessary may be done if the values must be changed before translation or decryption. Otherwise it may be made after. [00:09:18](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m18s) After all is done and the values must be changed on an export, it may be added.

### Import Features Explained

[00:09:32](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m32s)

If a different import type than usual is needed, go to import values, where these figures in the assign column  must be updated. [00:09:40](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m40s) If the ID is left in, it updates; if the ID is removed, it creates. If, for instance, the IDs are not used but these values instead, a custom import concept must be created. Although an attempt had been made to make it simple it still turned out to be complex.

### Custom Import Tab(default import code)

[00:10:13](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m13s) 

Go to Custom Import in the Editing Admin View. There is a warning. Below it'yes' should be selected in the Custom Import option and it will load the actual script into these areas that are used by default in these various concepts. (See video.) [00:10:38](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m38s) If this does not make sense, do not attempt to do it but do a search on courses like lynda.com and Udome etc instead. [00:11:09](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m09s) Changes may be made to this. For example: take out a portion, do a search, then place something in like 'your name'. Save and compile it. Do a search to see where it appears. [00:11:31](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m31s)

The Default Import method is not completely removed when these kind of changes are performed. There is a way that these changes can be done and have two Import Methods next to each other. It is not that easy but it is possible. It depends on what is being done in this HTML and PHP view area and in the view. [00:11:59](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m59s) Currently this is set up to do a normal import as is usually done. Changing this will also change the normal Import concept.

That is how to change the Custom Import concept. Please read through the code. Maybe compile it. [00:12:33](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m33s) See how the default import and concepts work and make changes accordingly.

I have used this area a lot for various applications. Occasionally there is a user that requires you or a client to import these sets of CSV files which may consists of 4000 or 40000 lines. Only specific values have to be selected. [00:13:06](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m06s) In that case this area is definitely what you are looking for since it will make it possible to adapt the Import Concept to accommodate that kind of complexity. That is changing Export values and creating Custom Import values for any field view in the back end of your component.