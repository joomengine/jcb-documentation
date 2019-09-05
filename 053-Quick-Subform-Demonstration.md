# QUICK SUBFORM DEMONSTRATION

### Request On The Forum

[00:00:00](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

I recently had this request on the Forum by Marco, regarding some help with subforms.

 "How to generate a subform itself from within JCB. Where to find the XML detail in relation to repeated subform fields in view. How the data of the subform is populated. How posted data of a subform is validated. [00:00:32](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m32s) How data of a subform is processed and persisted. My assumption is that the above is done as part of JCB and would not require manual construction of xml files. I did googled but found an answer to no avail." 

At the moment we have only made tutorials about Repeatable Fields. [00:01:01](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m01s) Repeatable Fields as such has been discontinued. A tutorial about subforms has not been made yet. 

### Subforms - Create Fields You Want To Use

[00:01:13](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m13s)

Subforms have fields in them. For example, go to component and open this(Demo) Admin view. This is a subform(Follow on video). Each of these little fields is a field in the subform. It is only an ID which you need to add to create the subform.[00:01:44](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m44s)  First create a Custom field that grabs values out of the Admin view. This(Icon) is a list field, to create a list field and this is a checkbox, etc.   First create these fields. 

### First Create A New Field 

[00:02:06](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m06s)

That is the first thing to do, create a field you want to use in the subform. For instance, I am going to use existing fields just as demonstration. There are Description, Mobile, Name, etc.  [00:02:27](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m27s) First we want to create a new field. First open it that we have both open to get the IDs. Then click New, then select Subform, and it populates the XML. 

### Look At The Tutorials - YouTube - Joomla Component Builder

[00:02:51](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m51s)

If you have not looked at all the tutorials that is available on YouTube, then a lot of this will not make sense.<<<<<<<<


 For those that maybe just seeing this video and not watched any of the other tutorials, please go to YouTube and type in Joomla Component Builder and try to find the playlist. Start at the top working through way down.  I know those tutorials will make you quite able to build amazing things. 

### Formsource

[00:03:51](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m51s)

This formsource(Optional) - it reads as follow: 'You can add a path to an XML file containing the fields'. So a custom  XML file can be added to your component. How to add custom files to component, is a whole another topic. It is also possible within the Joomla Component to add files and folders , etc. That means this specific source can still be used but you do not need to. If you use the fields option then you need to remove the source option. [00:04:23](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m23s) Either the one or the other of these options should be used. Currently the fields are set to mandatory . By going to the field types it can be changed to be optional and then you can select other fields or formsource. The compiler will in any case detects a formsource will behave correctly.<<<<<<<<<< 

### Adding IDs

 [00:04:57](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m57s)

We need to add the IDs so we can come here(Fields) and I want to have Name, it's just 199. [00:05:04](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m04s) I add 199 and a comma and then let's add something else. Let's add Website 280. Let's do an Email as well and it's 100. We have that in place. 

### Adding A Description, Maximum, Filter, Showon

[00:05:33](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m33s) 

We can add a description. We can add a maximum, a filter, a showon. I'm just going to leave this. The validation of these fields, I think that is an area which I haven't looked into. But if I'm correct and also the reason why they moved away from Repeatable Fields, is that every field is validated on its own merit. For example [00:06:05](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m05s) the Name field, if you create a Name field, you're saying I want this to be a string and it has this filter string value. Since this is part of the XML it will be validated on this. I can be mistaken. I haven't looked at the code. That's what I anticipate it will do. Most cases I would say anticipate that it doesn't and try and do some custom scripting. I'm not going to illustrate that now. [00:06:44](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m44s) You need to know little bit more about JCB which there are tons of the tutorials to show you how to do custom scripting all around it component and even to do custom scripting anywhere and any area of the component through the custom code area implementation. I'm going to talk more about that. Make sure it got all the spelling right. [00:07:15](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m15s) I'm going to save this, just give it a Name: Options (test), so I can see it. This Data Type I would make TEXT. The default means that JCB (the Store method) already will detect that this is a Subform and will add the needed [00:07:39](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m39s) PHP in storing the file and in loading the file into the form again. So that takes care of that. So you don't need to say Json, it will on its own by its default do the correct implementation. In the Data Type so you need to make sure either to click TEXT or MEDIUMTEXT depending on what this value is going to be. Anyway I think for 50 text is quite enough. Save and close. 

### Adding Options(test) Subforms To Any Admin View - See Video

[00:08:19](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m19s) 
 
Let's see we got that field. I'm going to add it to any admin view for now. I'm going to add it to Look View, that we can see it in action. The look view is part of the Demo component. I'm just going to dump it in here. Let's see above tab, full width, details, description. I think let's just add it there. Details also full width, make it the 2nd, and I say [00:08:49](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m49s) Options(test). Save and close. We've added it to a view. Now I'm just going to compile this component which the view belongs to. Which at this stage it is demo and install it. Now let's go open that Demo component, and open Looks. And here we go, enter name here, enter website address, enter email. We click the green plus button [00:09:26](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m26s) and our values are there. Let's just save one. Children. We can do I think that's the only one. (see video)Let's do that and by enter those values I'm just going to grab joomlamount.com up here, [00:09:55](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m55s) paste it in there a few times. I'm going to put Joomla@vdm.io in Email. To get sort of a feel for it. Save. It saved the values, it loaded it back, it's done all of that. 'Hi there' then save and close. [00:10:45](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m45s) If we open it again, it shows it up again. We can shuffle it, put number four on top. Save and close. Open again and so it is loading it also correctly. That's a quick demonstration Marco I hope this helps [00:11:09](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m09s) and getting you able to use subforms with JCB. It's as easy as that.
