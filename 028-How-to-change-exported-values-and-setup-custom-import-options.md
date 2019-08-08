# HOW TO CHANGE EXPORT VALUES AND SETUP CUSTOM IMPORT OPTIONS

[00:00:00](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

* ### Example Components

A short explanation of how to change the values that are being exported and to have a Custom Import option with an import of the data. Component Builder allows you to have a Import and Export function by default in all the List Views of the components. [00:00:35](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m35s) The component called IP Data is used to take a IP address and translate it to determine from which country it came and then a costing update is performed on your website based on that IP Data.

 * ### Example IP Tables

Select IP Tables which is on the IP Table Dashboard. [00:01:07](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m07s)  The 'CNTRY' value may be seen, that is the country, and the 'REGISTRY', which indicates to who the IP table belongs and the range,'IP from'/'IP to' is being reflected. 

### Export Feature

[00:01:26](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m26s)

If 'Export Data' has been clicked without selecting any values, it will give this warning: 'Please first make a selection from the list'. [00:01:35](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m35s) Only values that had been selected may be exported. If all have to be exported, change this value to 'all'. In some instances, if the table is too long, it is not possible to export all the values at once.

Exporting the data in large quantities is not advisable in Joomla.  If quantities exceeds 3000 items, rather go to MySQL and get a dump file. [00:02:16](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m16s) Although it is often seen that the Listview is being used for up to 10000 items, quite complex inheritance in structure is involved. But in this instance having the import and export in mind, makes it quite different. If for example this need to be exported but for some reason this 'ZZZ' or 'AUS' value should instead be replaced by the country name, the following would be a simple implementation of how to perform it. 

### Exported Example In XLS Format

[00:02:51](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m51s) 

Click 'Export', save this(Opening Ip_tables). It has been exported, all these AUS values are displayed, and some other values from the database as expected. But if it is suppose to be a different value when it is exported, then take the next step.

 ### Export Data In Code

[00:03:26](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m26s)

Component Builder has this 'getExportdata' method in the model. This 'getExportdata' method has this extra value called '$_export' set to 'true'.[00:03:52](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m52s) A reason why this had been added, is to target this(See video) method with custom scripting. But the difficulty is that this part($group to $query) is custom scripting and it is also been added into the actual 'getlistquery'. [00:04:21](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m21s) It is the same custom scripting. In the compiler the same custom script is added into the 'getlistquery' as into 'getExportdata. The way to know where it gets executed, is through this value '$_export'. [00:04:49](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m49s) This value is not set in the 'listquery', it is only set in the Export Data. 

### Admin View - PHP - (GetListQuery)

[00:04:54](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m54s)

The custom scripting is done in the 'Editing the Admin View' area. With the Admin View open, go to PHP and then  scroll down until the method ' Add PHP (getListQuery - JModellist)' can be seen and then it should be set to 'Yes'. [00:05:43](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m43s) The code, that is put there, is added both to the 'getListQuery', as well as to 'exportquery'. If the values need to be changed that had been exported, but not the values that's being shown in the component, it have to be done in the same area. It will be noticed that the same code appears in two distinct places(See video). [00:06:22](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m22s) If some value needs to be changed, that may be done simply by adding another 'lookup', and add this '$_export=true'. To see where all this '$_export=true' is appearing, go to any List model and search and it may be seen in different places(See video). [00:06:55](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m55s)

Go to the 'getExportdata' area. In the previous tutorial it had been explained how to add some customization to the values in the 'listview', some HTML, Here(See video) should be determined if the 'export' is 'set' or is it 'true'? 

NB. Don't add this feature here. [00:07:25](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m25s) 

The adding of this customization of coloring is avoided because it should not be running during the export process. Only the values is needed. Again it can be seen that the export values are used. [00:07:53](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m53s) That is the places where the export function is involved, and by using this '$_export' it is possible to identify whether it's an export or not. If it is, changes can be made to the values as necessary. Going back to the back end just to show that this(PHP area) is the place where the query had been done.[00:08:30](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m30s)

In the area 'Add PHP(getitems Method-before the translation fix & decryption)', it can be verified whether a export had been done and this can be taken(see video) instead of the exclamation, if export is '(isset($_export)' and export is 'true''(isset($_export)&&$_export)', then in the area below may be done what is necessary. That is if the values need to be changed before translation or before decryption or it may be made after. [00:09:18](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m18s) So after all was done and the values need to be changed on an export, it may be added.

### Import Features Explained

[00:09:32](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m32s)

If a different import type than usual is needed, then to import values, these (figures in the assign column) need to be updated. [00:09:40](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m40s) If the ID is left in, it updates, if the ID is removed, it creates.  If for instance the IDs is not used but rather these values instead, then a custom import concept needs to be created. Although a attempt had been made to make it simple it turned out to be still complex. 

### Custom Import Tab(default import code)

[00:10:13](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m13s) 

Go to Custom Import in the Editing Admin View. There is a warning. Below it,'yes' should be selected in the Custom Import option and it will load (See video) the actual script into these areas that are used by default in these various concepts. [00:10:38](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m38s) If this(PHP) does not make sense, rather not attempt to do it but do a search on courses like lynda.com and Udome etc. [00:11:09](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m09s) Changes may be made to this, for example: take out a portion, then do a search, put something in like 'your name'. Save and compile it. Do a search to see where it appears. [00:11:31](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m31s)

The Default Import method is not completely removed when this kind of changes is performed. There is a way that these changes can be done, and have two Import Methods next to each other. It is not that easy but it is possible and it all depends on what is being done in this HTML and PHP view area. [00:11:59](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m59s) So it depends on what is done in the view. Currently this is set up to do a normal import as is usually done. Changing this will also change the normal Import concept. That is how to change the Custom Import concept. Please read through the code. Maybe compile it. [00:12:33](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m33s)  See how the default import and concepts work and make changes accordingly.

 I have used this area quite a lot for various applications, because occasionally there is a user that requires of you or a client to import these sets of CSV files , which may consists of 4000 or 40000 lines and only specific values need to be selected. [00:13:06](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m06s) In that case this area is definitely what you looking for as it will make it possible to adapt the Import Concept to accommodate those kind of complexity. That is how to change Export values and create Custom Import values for any field view in the back end of your component.