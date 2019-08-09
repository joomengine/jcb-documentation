# THE NEW LIBRARY MANAGER AREA

### Libraries Dynamic In JCB
 
[00:00:00](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

I'm very excited to announce the actual Library manager implementation. We're busy with a pull request, we should have it released within the next hour or so. I'm very excited about this, this new improvement is really going to make [00:00:22](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m22s) Libraries very dynamic in JCB. Not it has not been dynamic. It's just not everybody realizes how easy it is to add new libraries. What I want to do is quickly, not to elaborate, show you how it used to be done, and then I want to jump into how it work now. You'll see why the new implementation is so much easier, so much better and [00:00:50](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m50s) everybody's going to enjoy it. 

### How It Used To Work

[00:00:53](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m53s)

Let's get started on how it used to work. If we go to Joomla Component and we open Demo component. There are three libraries that are already built into JCB that works out of the box and those three libraries can be selected with the Add Uikit, Add FooTable. The other libraries that are being added, is when it detects [00:01:22](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m22s) some code in the certain areas of the script. I'm not going to elaborate on that, it's going to take too long. Point is this two you could select here simply by selecting. 

### New Feature Added - Dynamic

[00:01:34](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m34s)

There's a new feature called Dynamic. That is part of what we will need to look at. Dynamic means that it is added in on the basis of the views that are linked to the Component. [00:01:50](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m50s) The old way you had to come to the component and sort of tell it here, I want UiKit and I want FooTable added and you could tell him what version you would like, or if you want it with the UiKit you could set that it adds both versions. Now with improvements you'd set this to Dynamic which turns off the global adding of the Uikit Component and then falls back unto the new implementation which I will demonstrate with in a moment. Let's leave it on this the way it was [00:02:29](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m29s) That was the first way of actually implementing some library. 

### Second Way - Scale It

[00:02:35](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m35s)

The second way which was the way that you could scale it. If you go to Settings, there is 'Component files folders' that you could add, you could click 'Edit component files folders for this joomla component' and say I want to add a library that isn't already part of JCB. Let's say you wanted to add Bootstrap. You would say  there is a folder in your component on the administrator components, [00:03:05](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m05s) component builder, custom folder, and inside that folder you would place the folder for Bootstrap. I don't have it here. Let me quickly do that. I'm going to refresh this page. I quickly went and added a folder to this custom folder called Bootstrap. Let me refresh this. I'm going to click add and then there we have it, select Bootstrap. [00:03:36](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m36s) I want Bootstrap to be added to the media folder. Since we do not do any changing of the folder name, we will just leave that as it is. So I move this folder into the media folder. That's the way you would have done that in the past. Save and close. Having added the files to the component, you will then have to go to the View. [00:04:03](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m03s) If we go to Site View, and this Looks View, you will have to in the Looks View set that it uses, this is the new implementations I'm going to undo that, and just say in the Add PHP (custom document script) area, you would add this snippet in here, so you add a script. Now that you add the Bootstrap v4 folder to media. [00:04:36](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m36s) But when it gets installed to Joomla, it creates a component folder and put the files in there. If you do not know how that will work out, add the folder, install it onto Joomla website and go look in the media folder to get the correct path. And save and close. That's how you would in the past have extended JCB to use other libraries then what's built into JCB. I illustrated that simply so you'll know that we could have done this before, but it was a little bit more complicated [00:05:13](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m13s) as the way it's going to work now. 

### New Changes Made - Can Remove Files

[00:05:17](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m17s)

With the new changes we've made, you can remove the files. If you have done this, this manual way you can  remove these files. Save and close. [00:05:35](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m35s) You don't need to add them this way anymore. They will be added in another way. 

### Starting At Libraries

[00:05:43](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m43s)

I'm going to demonstrate the other way by starting at the Libraries area. Closing out of the Component, I'm going to Libraries. You see that with the upgrade there's now a Bootstrap 4 Library, Uikit 3, Uikit 2, FooTable 2 and FooTable 3 and a No Library. [00:06:06](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m06s) Which is really only necessary when you create a Snippet which doesn't belong to any Library, just your own Snippet that you want to use. The Snippets are now directly linked to these Libraries. 

### These Six Libraries Should Not Be Changed - Behavior Can Be Changed

[00:06:22](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m22s) 

These six Libraries which been shipped with JCB, should not be changed in relation to its Name, or it's Type. [00:06:33](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m33s) But you can change its behavior. The behavior is the file behavior. There are an a various file behaviors. Let's open Bootstrap to show you some of those. 

### Bootstrap Set To Always Add

[00:06:44](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m44s)

The moment Bootstrap is set on 'Always Add' and it is linking in a content distributed network link 'https://maxcdn.bootstrapcdn.com/4.0.0-alpha.6'js/bootstrap.min.js'. It says that it should add it as a link. You can change that, you can say no I don't want to add it as a link. [00:07:04](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m04s) You can edit this. Without making any changes to the link you can change Type to Local. And what JCB will then do is during compilation it will download these files and add them into the component as Local files, which would then be used instead as the link, which I think is quite nice. 

### Library Level - Add Files And Folders From The Same Custom Files

[00:07:32](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m32s) 


You could also do the same thing with Custom Files and Folders as we did previously. You could add Files from the same Custom Files and also Folders. Those are the same kind of implementation except it's now done on a Library level so that even Library gets added to a View, as I will show you in the moment. You automatically use this files so that means [00:08:01](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m01s) you don't need to do it per Component. You will do it per Library and as you link the Libraries to Views, it'll automatically incorporate these files into your component, which makes it a little bit less effort, you just set it up once and thereafter you could just reuse. 

### Behaviors: Conditions, Custom Script, and Do not Add

[00:08:19](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m19s)

I'm going to change Libraries Files & Folders to Local. It will says Local (get). There are few Behaviors, there are Conditions, Custom Script, and Do not add. 

### Conditions Under Development

[00:08:31](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m31s)

The Conditions is still under development. [00:08:34](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m34s) All its functionality is already here, so you'll see all the links are showing up here, but as related to its implementation in the compiler. It's not ready yet. For now skip the Conditions option until you see that when you compile that it doesn't give you a warning. At this moment if you compile JCB, they will give you a warning that the Conditions options are not available yet. In fact we're planning to have them released with the next release which would be 2.6.7[00:09:09](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m09s) So any version if you looking at this tutorial after 2.6.7 then the conditions options already working. 

### Conditions - Demonstrate Briefly

[00:09:17](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m17s) 

I'm going to demonstrate it briefly. The Conditions options works in two ways. The one is you first need to add some Configuration Fields. Configuration Fields are Fields that will be added to the global options of the Component. If those Fields are tripped, it will have an effect on whatever way you set it. [00:09:41](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m41s) To show you that, if you look in Site View you'd see there is an Options area. If we click on the Options area, that's now in Component Builder Configuration. You would see there is Uikit2 Settings. It has a bunch of buttons. That's the kind of buttons that you can build. First go and create the Fields in JCB as you would normally create any other Field. Then in Editing the Library, click on 'Create' Linking the Configuration Fields. [00:10:15](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m15s) In A New Libraries Config, I'm going to select under Field: Add More, maybe as an option. I want to created under the Tab Name called Bootstrap. Bootstrap is going to be the Tab Name, Add More is going to be the radio button. [00:10:37](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m37s) Save and close. Just as a demonstration. If I change this to Conditions, and I click on adding a Conditions. Then I want to add these two local files (URL) bootstrap.min/js-Local, (URL) bootstrap.min/css-Local. I want them to be included when Add More is set to Yes. That's how this configuration of conditions will work [00:11:06](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m06s) in a relationship. You won't see any Option Fields if you haven't created Option Fields in the Configuration. So if you want to use this area, when it is eventually ready, you will have an include and exclude option based on buttons. Then you select the files that you want to be added or not not be added, [00:11:32](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m32s) based on these selections. Now these buttons is part of your component parameters. And so within your code when you start developing your templates and your layouts, you can draw upon these parameters in your PHP and say if it is this switch says that, then I want this HTML to load, otherwise I want that HTML to load. So you could have Bootstrap alongside Uikit [00:12:02](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m02s) with the same implementation. That is giving a idea of where this Conditions Area is supposed to come into play. 

### Custom Scripting

[00:12:10](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m10s)

The area that I have really like more is the Custom Scripting area. Which really is giving us the same behavior as what we did in the Site View. We will add the same files here. The only thing that will change, it will add [00:12:38](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m38s) 'component' like that. Wherever we have the component name, because we want this to be Dynamic. So that if it gets added to any component, you'll dynamically update those names as related to the fact that it will use Bootstrap v4. It really is using this name Bootstrap v4[00:13:05](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m05s) And it's putting a little dash - between them and making it lowercase. These two files bootstrap.min/js, bootstrap.min/css are based upon those names. So you need to use bootstrap.min/js name and bootstrap.min/css name. It will dynamically detect that this is a CSS file and put it in a CSS folder. The same goes with the JS a file. This is how you do Custom Scripting for Bootstrap v4 and that will be very similar to 'Always Add'. [00:13:39](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m39s) Because Always Add would write that script for you. You just add the files you always want to add and the behavior is like this. I'm trying to give you as much liberty as possible so that you can use Libraries in any way you like. Write your own Conditions or your own Custom Script or just let JCB add it always. 

### How Always Add Works?

[00:14:07](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m07s)

I'm going to demonstrate how this adding always is going to work in a moment. I'm going to save and close out of here. [00:14:15](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m15s) We have Bootstrap Always Add, and Uikit v3 Always Add, and Uikit v2 we using a Build-in option, as same for the FooTable v2 and the FooTable v3. The Build-in options are only available for these 4 Libraries. Not for Bootstrap but for those 4 Libraries. Any other Libraries that you add will not have a Build-in option unless we build one and then it will become available.  That is showing you a little around the Libraries. 

### Linking Libraries To A View

[00:14:50](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m50s)

Let's link the Library to a View. I'm going to go to Site View. I'm going to go and open Looks [00:14:57](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m57s) as the Site View. I'm just going to select Bootstrap v4. That's all. The moment I select Bootstrap v4, the Snippets that will show up here will then be the Bootstrap v4 Snippets. Since we do not anymore ship Snippets with JCB you'll have to install some Snippets. 

### Installing Library Snippets

[00:15:19](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m19s)

Let me show you that quickly. You can go to Snippets, you don't really need to go to Snippets. The Uikit Snippets are still being shipped, [00:15:32](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m32s) but not the Bootstrap v4 Snippets. You then click on Get Snippets, select Bootstrap v4 and it will then load all the Bootstrap v4 Snippets that are available to the community. You can then either use bulk import or you could import individual Snippets for Bootstrap v4. Once it's ready it will show you which ones are new. I'm going to add Bootstrap v4 - (Alert)Alerts - Heading, Get snippet. [00:16:02](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m02s) Say yes I want to do that. It's installing it. I'm also going to take that one Bootstrap v4 - (Alert)Alerts - Danger, It says would you like to add it? Yes OK. I've install two Bootstrap Snippets. The way to install all of them since there's so many, Is the use the bulk option. So you could actually come here to Bulk. You will see that it has the Get All New Snippets and you can click on it and it will install all of the the Bootstrap Snippets. [00:16:37](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m37s) That is the quick way of getting Libraries Snippets into your system and installing them just by clicking on Get Snippet. It will do that for you. 

### Site View - Looks - Libraries - Bootstrap

[00:16:54](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m54s)

Let's go back to Site Views. Again open the Looks area. If I select Libraries, Bootstrap [00:17:05](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m05s) then you'll see those two Snippets that I've installed and I can click between them. That's just for you to get the snippet and to be able to add it into your code wherever you would like it to be. I'm going to do that. 

### Demonstration - Adding The Library

[00:17:24](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m24s)

I'm just going to demonstrate adding the library. Selecting the Library, [00:17:29](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m29s) is what will add the Library to the Component and to this View. You can select multiple Libraries for one View. But there could be a problem with that if you, for example, want Uikit v2 and Uikit v3 on this page but you want to have it only use the one or the other, based on certain switches in the global options of the component. 

### Uikit v2 Set To Fall Back To Build-in Option, Uikit v3 Set To Fall Back To Always Add

[00:18:04](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m04s)

Uikit v2 was set to fall back to the internal Build-in option,  and Uikit v3 was set to fall back to Always Add. If we just look at that, Uikit v3 - Always Add and Uitkit v2 - Build-in. You want to have both Libraries unto the page, but you wanted to work within some Custom Implementation. The way to do that is to click on New and use the Bundle option. [00:18:32](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m32s) Select those two libraries, Uikit v2, Uikit v3, like that. Decide how you want to do it. It will be possibly a Custom Script or it will be a Conditions one. Which you will then have to create. Let me just say this, so we could call this Uikit and save. [00:19:06](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h19m06s) Once you've saved it once, you should add the files. You would go to folders and then add Uikit v3 and Uikit v2 [00:19:39](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h19m39s) and you want to add them to the media folder. You'll have to still link the files, remember selecting those Libraries doesn't inherently clone its files. You'll need to still manually add the files. We've got Uikit v3 and [00:20:07](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h20m07s)  Uikit v2.  Save and close. Now we have the files, and here in Conditions they are, as folders. It shows you all the files and folders that are found inside of those two folders that you've added. [00:20:35](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h20m35s) I think it's little difficult you cannot see which version is which here. This might be a good option to add maybe the folder name here. I think that will be in the next release, we will make that change. But I think the other option which is also ideal for this kind of implementation is a Custom Scripting. Which you could still create the Config Fields. [00:21:04](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h21m04s) When this Uikit v2 is selected, it will load the Uikit v2 files. But you must understand if you create the buttons, it will be added to the component. 

### Using Custom Script In Behavior

[00:21:19](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h21m19s)

But if you use Custom Script, and in the Behavior, you write the custom script, you will need to, let me just show you in the file, you will see that it puts the parameters [00:21:36](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h21m36s) in $this->params. You will need to go down to >get('uikit'), the switch, the button name, that you have created to the Config Fields. You then get the value, put it into a variable, and then based on that variable [00:21:59](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h21m59s) you would either add the file or not add the file. You'll write this script(see video). Just copy this is an example, all the way up there, and go to Editing the Library, paste. This is what the custom script should look like, but that means that you created in the Library Config, you created buttons [00:22:30](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h22m30s) with those names and that the values are related to these values. 

### HeaderCheck

[00:22:38](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h22m38s)

The HeaderCheck option is something that if you go into the file, you go look at the PHP, you might understand how to use this, and so the HeaderCheck at this stage always being loaded. If you don't want to use the HeaderCheck then you don't use it. But you could go and and try and figure out how the HeaderCheck works and then use it. [00:23:06](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h23m06s) That is making a bundle. Let me save this as an example. 

### Uikit Bundle

[00:23:13](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h23m13s)

We got this Uikit and it is a bundle. If we go back to the Site View and we open Looks again. We will now instead of creating Uikit v2 and Uikit v3, we will just create select Uikit bundle instead and that bundle will give me [00:23:32](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h23m32s) Uikit v2 Snippets. If we have any v3 Snippets installed, it will also load that for me. I will be able to work with both Libraries by selecting Uikit bundled Library option. JCB when it compiles, it will use the Custom Script that you wrote in the Bundle to add it to the view. Let me show you that. I'll save and close. Let's go back to the Library. Do something silly to the code [00:24:10](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h24m10s) so that you will see it's implementation. I am going to add these bunch of lines/////////. Save and close. Let's compile and install. Let's look at the code. Now you will see that its added in this Library files. It's also added in the [00:24:43](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h24m43s) originals, because we haven't set that button to show. Let me just show you what I mean. In the component you need to change the version of the old library implementation. You need to change that. You need to change this from Add Uikit v2 to Dynamic. [00:25:10](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h25m10s) Save and close. If we compile it, you will see it will not add the that code to the file twice. You're just add that Uikit bundled code that we wrote. Let's look at the code. We see that it only added the code that we wrote. [00:25:38](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h25m38s)  Remember in the file we added this(see video) as Custom Script. We need to remove this in the view where we added this in. In the view we added these custom script. We didn't need to add the spaces. We do have a little bit of a discrepancy there. [00:26:08](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h26m08s) 

I'm going to escape ///$this just that you can see we don't need to add $this in this way anymore. We can go to Details and close Uikit v2 and v3. We still want that Bundle in there as well. We don't need to do custom script anymore. We can [00:26:35](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h26m35s) select Bootstrap v4. Save and close. I'm going to run the compiler again. There we go. If you look at it(see video), here we see that there is that escaped code that we removed. Here is the code that JCB added. 

### Implementing the get option For The Libraries

[00:27:02](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h27m02s)

Remember I said to you that in JCB, we are linked in. If we look at the Bootstrap v4 Library, [00:27:12](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h27m12s) we set Always Add and we linking it from a link. We just set Local(get). If we look at the code, we see that it wrote for us this path: */media/com_demo/bootstrap-v4/js/bootstrap.min.js'. Let's check if it did add the path correctly. We want to go to the media area of the [00:27:43](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h27m43s) program and go to demo. We see it created the Bootstrap folder and added the files according to the path that is also set. That it is implementing the get option [00:28:07](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h28m07s) for the Libraries. All you did is you just linked it to this view. 

### Linking To Views

[00:28:15](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h28m15s)

This does give another situation where to every view that you want a specifically Library to be available, you need to link it to that view. Which wouldn't be a problem, if you created a view now and just add your Library and then add the Snippets. Then I mean then you're starting a fresh and you will select the right views you want to use. Since you haven't done this before, all the components, [00:28:46](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h28m46s) if you want to use a Library in the view, you have to go and add it, or you just have to in the components area fall back on the old way of implementing the Libraries that are built into JCB. 

### Old Implementation Still Works

[00:29:01](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h29m01s)

That means the old implementation still work if you set it in Libs & Helpers to Add both Uikit v2 and v3 [00:29:19](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h29m19s) and also to add FooTable v2. Those implementations still work, and doing that will add it to every Custom Admin Views, Site Views, Template, Layouts. So that that's the old way and that still works. 

### Need To Link Custom Admin View, Site View, Template, Layout to Specific Library which is Available

[00:29:38](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h29m38s)

It's just that when you want to start using Bootstrap v4, you'll have to link it to the Custom Admin View or Site View or Template or Layout, [00:29:53](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h29m53s) where you want that specific Library to be available. If you link in Bootstrap v4 then it will be available to this Layout and to every view where this Layout is used. That's the quick demonstration of the new Libraries implementation. We call it a Library Manager. [00:30:19](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h30m19s) Because of the diverse ways of you linking in the files and so forth. We really hope that you understood and then are able to enjoy this new implementation. We want to make it possible for you to add Libraries, and then share that Snippets with the rest of the community. Those of you that are interested in doing that, please watch some of the previous tutorials about Snippets and the Snippet Manager. Because [00:30:50](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h30m50s) I think doing this will not only help everyone else in the community but also get your name out there and get people connected with each other.  
