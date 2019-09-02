# THE NEW LIBRARY MANAGER AREA

### Libraries Dynamic In JCB
 
[00:00:00](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

A very exciting announcement: The actual Library manager implementation is available. This new improvement is going to make Libraries very dynamic in JCB.[00:00:22](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m22s) Not that it has not been dynamic, it is just that not everybody realizes how easy it is to add new libraries. What I want to do is, without elaborating too much, show you how it used to be done, and how it works now. You will see why the new implementation is so much easier, so much better and everybody is going to enjoy it. 

### How It Used To Work

[00:00:53](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m53s)

How it used to work. If we go to Joomla Component and open Demo component. Three libraries are already built into JCB that works out of the box and those three libraries can be selected with the Add Uikit, Add FooTable. The other libraries that are being added, when it detects some code in certain areas of the script. [00:01:22](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m22s)  These two options can be selected here in the Add UiKit function. 

### New Feature Added - Dynamic

[00:01:34](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m34s)

There is a new feature called, 'Dynamic'. That is part of what we will need to look at. Dynamic means that it is added in, on the bases of the views that are linked to the Component. [00:01:50](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m50s) The old way of doing it had been to indicate in the component if UiKit and FooTable should be added and as well as the version you would prefer, or if you want it with the UiKit you could set that it adds both versions. Now with the improvements, this can be set to Dynamic which turns off the global adding of the Uikit Component and then falls back to the new implementation. Leave it on the way it was.  That was the first way of actually implementing some library. 

### Second Way - Scale It

[00:02:35](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m35s)

The second way which was the way that you could scale it. Go to Settings, there is 'Component files folders' that could be added and click 'Edit component files folders for this Joomla component' and indicate that you want to add a library that is not already part of JCB. Say for instance you want to add Bootstrap. You would say there is a folder in your component on the administrator components,  component builder, custom folder, and inside that folder, you would place the folder for Bootstrap. [00:03:05](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m05s) If it is not there then just refresh this page. I added a folder to this custom folder called 'Bootstrap'. Refresh this and click 'Add', then there we have it. [00:03:36](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m36s) Select Bootstrap to be added to the media folder. Since no change of the folder name is made, we will just leave that as it is and this folder is moved into the media folder. That is how it had been done in the past. Save and close. Having added the files to the component, go to the View. [00:04:03](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m03s)

 To Site View, and to this Looks View, there you would add this snippet in the Add PHP (custom document script) area, so you add a script. If you add the Bootstrap v4 folder to media and [00:04:36]when it gets installed to Joomla, it creates a component folder and put the files in there. (https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m36s) If you do not know how that will work out, add the folder, install it on the Joomla website and look in the media folder to get the correct path. Save and close. That is how you would in the past have extended JCB to use other libraries that were built into JCB. I illustrated that simply so you will know that we could have done this before, but it was a little bit more complicated as the way it is going to work now. 

### New Changes Made - Can Remove Files

[00:05:17](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m17s)

With the new changes which have been made, the files can be removed. If you have done this, the manual way, you can remove these files. Save and close. [00:05:35](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m35s) You do not need to add them this way anymore. They will be added in another way. 

### Starting At Libraries

[00:05:43](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m43s)

I am going to demonstrate the other way by starting at the Libraries area. Closing out of the Component, and go to Libraries. With the upgrade, there is now a Bootstrap 4 Library, Uikit 3, Uikit 2, FooTable 2 and FooTable 3 and a No Library. [00:06:06](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m06s) Which is only necessary when you create a Snippet which does not belong to any Library, only the Snippet that you would like to use. The Snippets are now directly linked to these Libraries. 

### These Six Libraries Should Not Be Changed - Behavior Can Be Changed

[00:06:22](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m22s) 

These six Libraries which have been shipped with JCB, should not be changed in relation to its Name, or its Type. [00:06:33](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m33s) But its behavior can be changed. The behavior is file behavior. There are various file behaviors. Let's open Bootstrap to show you some of those. 

### Bootstrap Set To Always Add

[00:06:44](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m44s)

The moment Bootstrap is set on 'Always Add' and it is linking in a content distribution network link 'https://maxcdn.bootstrapcdn.com/4.0.0-alpha.6'js/bootstrap.min.js'. It says that it should add it as a link. You can change that, that it should not be added as a link. [00:07:04](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m04s) You can edit this without making any changes to the link. You can change Type to Local and during compilation, JCB will download these files and add them into the component as Local files, which would then be used instead as the link.

### Library Level - Add Files And Folders From The Same Custom Files

[00:07:32](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m32s) 


The same can be done with Custom Files and Folders as we did previously. Files can be added from the same Custom Files and Folders. Those are the same kind of implementation except it is now done on a Library level so that even the Library gets added to a View. These files can be used automatically so it is not necessary to do it per Component. [00:08:01](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m01s) As it is done per Library and as the Libraries are linked to Views, will automatically incorporate these files into the component, which makes it easier, since it is set up once and thereafter it could be reused. 

### Behaviors: Conditions, Custom Script, and Do not Add

[00:08:19](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m19s)

 Libraries Files & Folders are going to change to Local. It will say Local (get). There are few Behaviors, there are Conditions, Custom Script, and 'Do not add'. 

### Conditions Under Development

[00:08:31](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m31s)

The Conditions are still under development. [00:08:34](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m34s) All its functionality is already here, all the links are showing up but as related to its implementation in the compiler, it is not ready yet. For now, skip the Conditions option until you see that when you compile that it does not give a warning. At this moment if you compile JCB, there will be a warning that the Conditions options are not available yet. We are planning to have them released with the next release which would be 2.6.7[00:09:09](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m09s) 

### Conditions - Demonstrate Briefly

[00:09:17](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m17s)
 
The Conditions options work in two ways. The one is you first need to add some Configuration Fields. Configuration Fields are Fields that will be added to the global options of the Component. If those Fields are tripped, it will affect whatever way you set it. [00:09:41](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m41s) If you look in Site View there is an Options area. If we click on the Options area, which is in Component Builder Configuration, there are Uikit2 Settings. It has several buttons. That is the kind of buttons that you can build. First, go and create the Fields in JCB as you would normally create any other Field. Then in Editing the Library, click on 'Create' Linking the Configuration Fields. [00:10:15](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m15s) In 'A New Libraries Config', select under Field: Add More, maybe as an option. I want to create under the Tab Name called 'Bootstrap'. Bootstrap is going to be the Tab Name, 'Add More' is going to be the radio button. [00:10:37](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m37s) Save and close. Just as a demonstration. If I change this to Conditions and click on adding Conditions and add these two local files (URL) bootstrap.min/js-Local, (URL) bootstrap.min/css-Local. I want them to be included when Add More is set to 'Yes'. That is how this configuration of conditions will work in a relationship.[00:11:06](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m06s)  No Option Fields will be seen if you have not created Option Fields in the Configuration. So if you want to use this area, when it is eventually ready, you will have an 'Include' and 'Exclude' option based on buttons. Then you can select the files that you want to be added or not, based on these selections. [00:11:32](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m32s) Now, these buttons are part of the component parameters. When you start developing templates and layouts in your code, you can draw upon these parameters in your PHP and be able to decide which HTML to load and have Bootstrap alongside Uikit with the same implementation. [00:12:02](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m02s) That is an idea of where this Conditions Area is supposed to work. 

### Custom Scripting

[00:12:10](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m10s)

The area that I like more is the Custom Script area which has the same behavior as in the Site View. We will add the same files here. The only thing that will change, we will add 'component' like that wherever we have the component name because we want this to be Dynamic.  [00:12:38](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m38s) So that if it gets added to any component, it will dynamically update those names as related to the fact that it will use Bootstrap v4.[00:13:05](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m05s)  It is using this name Bootstrap v4 and it places a little dash - between them and making it lowercase. These two files 
`bootstrap.min/js` and `bootstrap.min/css` are based upon those names. So you need to use bootstrap.min/js name and bootstrap.min/css name. It will dynamically detect that this is a CSS file and put it in a CSS folder. This applies to the JS a file as well. This is how you do Custom Scripting for Bootstrap v4 and that will be very similar to 'Always Add'. [00:13:39](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m39s) 'Always Add' will write that script for you. Just add the files you always want to add and the behavior is like this. You are given as much liberty as possible so that you can use Libraries in any way. Write your Conditions or your own Custom Script or just let JCB add it always. Save and close.

### How Always Add Works?

[00:14:07](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m07s)

How this 'Always add' is going to work. [00:14:15](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m15s) We have Bootstrap Always Add, and Uikit v3 Always Add, and for Uikit v2 we are using a Build-in option, the same as for the FooTable v2 and the FooTable v3. The Build-in options are only available for these 4 Libraries. Not for Bootstrap but for those 4 Libraries. Any other Libraries that you add will not have a Build-in option unless we build one and then it will become available. 
 
### Linking Libraries To A View

[00:14:50](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m50s)

Let's link the Library to a View. Go to Site View and open 'Looks' and select Bootstrap v4. The moment Bootstrap v4 is selected, the Snippets that will show up here will then be the Bootstrap v4 Snippets. Since we do not ship Snippets with JCB anymore, you will have to install some Snippets. 

### Installing Library Snippets

[00:15:19](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m19s)

This is how it is done. Click on Get Snippets, select Bootstrap v4 and it will then load all the Bootstrap v4 Snippets that are available to the community. It may be imported in bulk or individual Snippets may be imported for Bootstrap v4. Once it is ready it will indicate which ones are new. I am going to add 'Bootstrap v4 - (Alert)Alerts - Heading', Get snippet. [00:16:02](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m02s) Say 'Yes' and it will be installed. I am also going to take 'Bootstrap v4 - (Alert)Alerts - Danger', It askes if it should be added? Indicate 'OK'. Two Bootstrap Snippets have been installed. Since there are so many the best way to install all of them is to use the 'Bulk' option. There is 'Get All New Snippets' ,If it is clicked it will install all of the Bootstrap Snippets. [00:16:37](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m37s) That is the quick way of getting Libraries Snippets into your system and installing them just by clicking on 'Get Snippet'. 

### Site View - Looks - Libraries - Bootstrap

[00:16:54](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m54s)

Back to Site Views and open the 'Looks' area. If in Libraries, 'Bootstrap' is selected then those two Snippets may be seen that I have installed and click between them to get the snippet and to be able to add it into your code wherever you would like it to be. 

### Demonstration - Adding The Library

[00:17:24](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m24s)

By selecting the Library,  the Library will be added to the Component and this View. You can select multiple Libraries for one View. But there could be a problem with that if you want, for instance,  Uikit v2 and Uikit v3 on this page but you want to have it only use the one or the other, based on certain switches in the global options of the component.

### Uikit v2 Set To Fall Back To Build-in Option, Uikit v3 Set To Fall Back To Always Add

[00:18:04](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m04s)

Uikit v2 was set to fall back to the internal Build-in option,  and Uikit v3 was set to fall back to 'Always Add'. If we just look at that, Uikit v3 - Always Add and Uitkit v2 - Build-in. If you want to have both Libraries unto the page, but you want to work within some Custom Implementation. The way to do that is to click on 'New' and use the 'Bundle' option. [00:18:32](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m32s) Select those two libraries, Uikit v2, Uikit v3, like that. Decide how you want to do it. It will possibly be a Custom Script or it will be a Conditions one which you will then have to create. Let me just say this, so we could call this Uikit and save. [00:19:06](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h19m06s) Once you have saved it once, you should add the files and go to folders and then add Uikit v3 and Uikit v2  and add them to the media folder.[00:19:39](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h19m39s) These files still have to be linked,  selecting those Libraries does not inherently clone its files. The files still need to be added manually. We have got Uikit v3 and Uikit v2. [00:20:07](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h20m07s) Save and close. Now we have the files, and here in Conditions, they are, like folders. It shows you all the files and folders that are found in those two folders that you have added. [00:20:35](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h20m35s) It is not clear which version is which here and it might be a good option to add maybe the folder name here. Possibly it will be changed in the next release. The other option which is also ideal for this kind of implementation is a Custom Scripting which you could still create the Config Fields. [00:21:04](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h21m04s) When this Uikit v2 is selected, it will load the Uikit v2 files. If you create the buttons, it will be added to the component.

### Using Custom Script In Behavior

[00:21:19](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h21m19s)

If you want to use Custom Script, open the PHP-Setdocument()* by clicking on 'Behavior'. It can be seen in the file that it puts the parameters in `$this->params`. [00:21:36](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h21m36s) Go down to `>get('uikit')`, and get the button name, that you have created in the Config Fields. You then get the value, put it into a variable, and then based on that variable you would either add the file or not add the file. [00:21:59](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h21m59s)  You will write this script(see video). For example, I will copy this, and go to Editing the Library and paste it there. This is what the custom script should look like, but that means that you have created buttons in the Library Config, with those names and that the values are related to the values here(Please follow on video). 

### HeaderCheck

[00:22:38](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h22m38s)

The HeaderCheck option is something that if you go into the file, and look at the PHP, you might understand how to use this, and so the HeaderCheck at this stage is always being loaded. It is not necessary to use the HeaderCheck but you can try and figure out how the HeaderCheck works and then use it. [00:23:06](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h23m06s) That is making a bundle and is saved just as an example. 

### Uikit Bundle

[00:23:13](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h23m13s)

We got this Uikit and it is a bundle. If we go back to the Site View and we open 'Looks' again. We will now instead of creating Uikit v2 and Uikit v3, we will just select that Uikit bundle instead and that bundle will give me Uikit v2 Snippets. [00:23:32](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h23m32s)  If we have any v3 Snippets installed, it will also load that. Now it is possible to work with both Libraries by selecting Uikit bundled Library option. JCB when it compiles it will use the Custom Script that you wrote in the Bundle to add it to the view. Let me show you that. Save and close. I will go back to the Library and add a bunch of lines `/////////` to the code to see its implementation. [00:24:10](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h24m10s) Save and close. Compile and install. In the code, it may be seen that it has been added in this Library files. It has also been added to the originals because that button was not set to show. [00:24:43](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h24m43s)  In the component, you need to change the version of the old library implementation and change this from Add Uikit v2 to Dynamic. [00:25:10](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h25m10s) Save and close. If it is compiled, it will not add that code to the file twice. Just add that Uikit bundled code that we wrote. Looking at the code it only added the code that we wrote. [00:25:38](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h25m38s)  Remember in the file we added this(see video) as Custom Script.  This must be removed in the view where we added it in. We have added this custom script in the view and did not need to add the spaces. There is a little bit of a discrepancy there. [00:26:08](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h26m08s) 

I am going to escape `///$this` just that you can see that it is not necessary to add `$this` in this way anymore. Go to Details and close Uikit v2 and v3. That Bundle in there is still needed. It is not necessary to do a custom script anymore. [00:26:35](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h26m35s) Select Bootstrap v4. Save and close. Run the compiler again. If you look at it(see video), there is that escaped code that we removed and here is the code that JCB added. 

### Implementing the get option For The Libraries

[00:27:02](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h27m02s)

NB. In JCB, we are linked in. If we look at the Bootstrap v4 Library, we set 'Always Add' and are linking it from a link and set Local(get). It may be seen in the code that this path has been written for us: `*/media/com_demo/bootstrap-v4/js/bootstrap.min.js'`. To check if it did add the path correctly, go to the media area of the program and to demo.[00:27:43](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h27m43s) It created the Bootstrap folder and added the files according to the path that has been set. It implemented the get option for the Libraries when you linked it to this view. 

### Linking To Views

[00:28:15](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h28m15s)

This results in another situation that in every view that you want a specific Library to be available, you need to link it to that view which would not be a problem if you create a view and add your Library and then add the Snippets. That is to say, if you start afresh and select the right views to use. But since you have not done this before, all the components, that is to say, if you want to use a Library in the view, you have to go and add it, or you just have to fall back in the components area on the old way of implementing the Libraries that are built into JCB.<<<<<<<< 

### Old Implementation Still Works

[00:29:01](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h29m01s)

That means the old implementation still works if you set it in Libs & Helpers to Add both Uikit v2 and v3 [00:29:19](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h29m19s) and also to add FooTable v2. Those implementations still work, and doing that will add it to every Custom Admin Views, Site Views, Template, Layouts. So that's the old way and that still works. 

### Need To Link Custom Admin View, Site View, Template, Layout to Specific Library which is Available

[00:29:38](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h29m38s)

It's just that when you want to start using Bootstrap v4, you'll have to link it to the Custom Admin View or Site View or Template or Layout, [00:29:53](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h29m53s) where you want that specific Library to be available. If you link in Bootstrap v4 then it will be available to this Layout and to every view where this Layout is used. That's the quick demonstration of the new Libraries implementation. We call it a Library Manager. [00:30:19](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h30m19s) Because of the diverse ways of you linking in the files and so forth. We hope that you understood and then can enjoy this new implementation. We want to make it possible for you to add Libraries, and then share that Snippets with the rest of the community. Those of you that are interested in doing that, please watch some of the previous tutorials about Snippets and the Snippet Manager. Because [00:30:50](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h30m50s) I think doing this will not only help everyone else in the community but also get your name out there and get people connected.  