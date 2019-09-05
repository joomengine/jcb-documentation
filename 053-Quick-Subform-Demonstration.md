# QUICK SUBFORM DEMONSTRATION

### Request On The Forum

[00:00:00](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

I recently had this request on the Forum, regarding some help with subforms.

 "How to generate a subform itself from within JCB. Where to find the XML detail in relation to repeated subform fields in view. How the data of the subform is populated. How posted data of a subform is validated. [00:00:32](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m32s) How data of a subform is processed and persisted. I assume that the above is done as part of JCB and would not require manual construction of XML files. I did google but found an answer to no avail." 

At the moment we have only made tutorials about Repeatable Fields. [00:01:01](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m01s) Repeatable Fields as such has been discontinued. A tutorial about subforms has not been made yet. 

### Subforms - Create Fields You Want To Use

[00:01:13](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m13s)

Subforms have fields in them. For example, go to component and open this(Demo) Admin view. This is a subform(Follow on video). Each of these little fields is a field in the subform. It is only an ID which you need to add to create the subform. [00:01:44](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m44s)  First create a Custom field that grabs values out of the Admin view. This(Icon) is a list field, to create a list field and this is a checkbox, etc.   First, create these fields. 

### First Create A New Field 

[00:02:06](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m06s)

That is the first thing to do, create a field you want to use in the subform. For instance, I am going to use existing fields just as a demonstration. There are Description, Mobile, Name, etc.  [00:02:27](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m27s) First we want to create a new field. First, open it that we have both open to get the IDs. Then click New, then select Subform, and it populates the XML. 

### Look At The Tutorials - YouTube - Joomla Component Builder

[00:02:51](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m51s)

If you have not looked at all the tutorials that are available on YouTube, then a lot of this will not make sense. For those that may be just seeing this video and not watched any of the other tutorials, please go to YouTube and type in Joomla Component Builder and try to find the playlist. Start at the top working through way down.  I know those tutorials will make you quite able to build amazing things. 

### Formsource

[00:03:51](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m51s)

This formsource(Optional) - it reads as follows: 'You can add a path to an XML file containing the fields'. So a custom  XML file can be added to your component. How to add custom files to a component, is a whole another topic. It is also possible within the Joomla Component to add files and folders, etc. That means this specific source can still be used but you do not need to. If you use the fields option then you need to remove the source option. [00:04:23](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m23s) Either the one or the other of these options should be used. Currently, the fields are set to mandatory. By going to the field types it can be changed to be optional and then you can select other fields or Formsource. The compiler will, in any case, detects a formsource will behave correctly. 

### Adding IDs

 [00:04:57](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m57s)

IDs need to be added which we find in Fields. It should have 'Name', it is just '199'. [00:05:04](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m04s) Add 199 and a comma and then add something else.A Website '280', an Email '100'. We have that in place. 

### Adding A Description, Maximum, Filter, Showon

[00:05:33](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m33s) 

Then add a Description, a Maximum, a Filter and a Showon. The validation of these fields, that is an area that I have not looked into. Perhaps they moved away from Repeatable Fields because every field is validated on its own merit. [00:06:05](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m05s) For example, the Name field, if you create a Name field, you want this to be a string and it has this filter string value. Since this is part of the XML it will be validated on this. I have not looked at the code. That is what I suppose it will do. In most cases, I suppose that it does not and try and do some custom scripting but I am not going to illustrate that now. [00:06:44](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m44s) There are many tutorials to show you how to do custom scripting in a component and even to do custom scripting in any area of the component through the custom code area implementation. 

 [00:07:15](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m15s)  Save this and give it a Name: Options (test) so that it can be seen. For this (DataType), I would make 'TEXT'. The default means that JCB (the Store method) already will detect that this is a Subform and will add the needed [00:07:39](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m39s) PHP in storing the file and in loading the file into the form again. So that takes care of that. So you don't need to select JSON, it will by default do the correct implementation. In the Data Type so you need to make sure either to click TEXT or MEDIUMTEXT depending on what this value is going to be. Save and close. 

### Adding Options(test) Subforms To Any Admin View 

[00:08:19](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m19s) 
 
Add this field Options(test) to any admin view, for instance, to Look View, to see it in action. The Look view is part of the Demo component. I am going to dump it here. Look at the above tab, full width, details, description. Let's just add it to details, full width, make it 2nd, and say Options(test). [00:08:49](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m49s)  Save and close. We have added it to a view. Now I am just going to compile this component which the view belongs to. At this stage, it is demo and installs it. Open that Demo component, and open Looks. Enter Name here, enter the website address, enter an email. Click the green plus button and the values are there. [00:09:26](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m26s)  Let's just save one. 'Children'.  (_Please follow on video_) Save. It saved the values and loaded it back, it has done all of that. 'Hi, there' then save and close. [00:10:45](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m45s) If we open it again, it shows it up again. We can shuffle it, put number four on top. Save and close. Open again and so it is loading it also correctly. 