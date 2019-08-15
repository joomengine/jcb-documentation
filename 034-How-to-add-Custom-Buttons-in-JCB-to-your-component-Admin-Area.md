# HOW TO ADD CUSTOM BUTTONS IN JCB TO THE COMPONENT ADMIN AREA

[00:00:00](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

How to add a button to the Components Admin List area or in the Edit area of the view. Possibly this had been touched on in previous tutorials but this tutorial will specifically deal with it. Here is a blank install of JCB, and this demo component had been installed or mapped.  It had been installed into this website. 

### Joomla Demo Dashboard - Look
 
[00:00:38](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m38s)
 
If 'Looks' is opened; it seems that everything is as it should, so an item can be created. (See video) (In Description;  'Give it some details'). Click save and close, and we have an item. There is a whole bunch of buttons and if you go into the test, there is also a bunch of buttons. [00:01:19](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m19s) All of them are usually there, those are the default buttons. The aim is to create buttons in these areas without custom coding, of course, it could be done with custom coding, but there is a way to do it in JCB. Go back to the Admin Views and open the Admin View called 'Look'. When the Custom Buttons area may be seen, click on that, and say 'yes' to 'Add Custom Button'. 

### PHP Controller Method - List View Controller Method

[00:02:05](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m05s)
 
You would see that it opens PHP (Controller Methods), and also PHP List View (Controller Methods). It is necessary to understand the MVC, the controller, the model, again the controller and the model. Each view has two controllers and two models. Because it has a List view and Edit view. [00:02:32](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m32s) The List view has its own controller and model. The Edit view has his own controller and model, so depending on where the button is placed. It will affect which model and which controller is needed. Assuming that you are familiar with Joomla API, not much will be explained about the PHP being placed in these blocks

### Custom Button

[00:03:07](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m07s)

At the Custom Button option, click on 'add'. At 'Icon'-(Joomla Standard Icomoom Fonts) any of the default Joomla icons may be selected and be used. Then the 'Name' of the button, call it 'test' for now. Then the 'name' of the Controller method may be called 'getTested'.[00:03:39](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m39s)  
To set the Target View Type: Decide whether this going to be an edit view, a single view target, a list view or both, where this button should show up. In this instance, 'list' is selected. If it is a List view, then it could be decided whether this is only a function. [00:04:02](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m02s) When it is a 'Selection', it means that it is necessary to select some items. Then click the button for it to submit those IDs of the selected items. If it is only 'function' it is not necessary to select anything. If the button is clicked, a function will be triggered, which does not require that any information should be given to it. [00:04:30](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m30s) Whatever the result, you need to be able to code that. 'Default' will be used. The 'Default' is very much like 'Selection' but it behaves differently.  The best way to do this is to select one of the options, compile the component and go look at the code. 

### PHP (Controller Method)

[00:05:05](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m05s)

To demonstrate where the code ends up. Save this as a selection in a Listview and save. At this stage, if no values are added to these blocks it will not work. [00:05:31](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m31s) In order to satisfy its requirement to have information, two forward slashes are added. A little method, called 'getTested', is added to redirect us to the dashboard. That is a Controller Method. It must be public. [00:05:58](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m58s) It may be verified whether it was submitted from the current website and then it can be redirected to the components dashboard.  A method is not necessary now since it gets redirected. Save and close. Compile this component. Select the demo component, compile it, then re-install it to see the changes. [00:06:29](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m29s) Go to the Component, then to 'Looks' and a new button called 'test' may be seen. If it is clicked, it will redirect us to the dashboard. So its function is to redirect, and in this way, anything can be redirected. That is the first way of implementing a button in the List view.  

### More Options

[00:07:05](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m05s)

Now let us go back to editing that functionality there, and show some more options('Look'). Go to Custom Buttons. Add another button. (See video) Target - call it 'single'. Name - call it 'Work'. The Controller method - 'getDone', and leave Type to 'Default' and then save. [00:07:50](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m50s)  In the Controller method there is a function called 'getDone'. In the(PHP controller method) a public function is placed. This time we will get the model and do something in the model. You can also get the item values. When this button is clicked, the item opens and it automatically submits the form. It is possible to grab the item's values. The values may differ from those in the database.  [00:08:36](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m36s) The values could be changed, by clicking that button, and it will submit these changed values. Yet those values have not been saved to the database. If those values need to be in the database, you have to put it there. The model has a save method, and you should do the necessary sanitation, and trigger the save method, and it should store the data.  For this purpose the data need to be grabbed, a verification is done and then return either an 'error' or a 'success'. 

### Checking Within Controller Before Trigger The Model

[00:09:33](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m33s)

First thing is to get the values. Having the data, check whether the values that are needed are there and available to be used. It is necessary to make sure that this is already a saved item. [00:09:51](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m51s) Then check whether the ID is more than 0. It is necessary to have a name, and then check for that. Some checking should be done within the controller before the model gets triggered, and run the intended function. Then the model needs to be triggered, then it should be decided what to call the method in the model. Something random is chosen and then a method can be created in the model area, then do whatever you prefer. 

### Logic In The Model Methods

[00:10:39](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m39s)

What is being done in the Model area? Do keep in mind that if the Model is unsuccessful, something needs to be done, if the data is set, but the Model is not being successful, something needs to be done, and if the data is not set, something needs to be done.[00:10:55](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m55s) Those are the areas in which some messages can be added that needs to be returned to the user, to inform them what is happening. In the Model, the task gets performed, and when the goal is achieved, return 'true', if it failed, return 'false', and then that would trigger the messages in the controller. This is just giving a basic overview of setting up some Model Controller connected with a button. 

### Adding Code

[00:11:30](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m30s)

Some of this code is going to be added in here, (It will be beneficial to study some more tutorials on how to create Model and Controller relationships in Joomla using its API, or you can open this Model and Controller of the specific view in your IDE and in there you can see how the code is added, and what is happening, and how is it done). [00:12:11](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m11s)   I have added some code that may be reused. If the work has been done, but if it has not been done the user will be informed that it has not been done. If the required values had not even being detected, then a major error is passed and quit out.[00:12:51](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m51s)  That is the Controller. Not much of the model is populated since the design is left to your logic. Return 'true' so to give this first message.

### Demonstration of Adding A-List Button

[00:13:08](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m08s)

Then the IDE is changed to false again to demonstrate the response. Play around with the code in the IDE to get the feel of how to approach it from that direction. Save this(See video), then go and compile it and install the newly compiled version. Open the component. Go to 'Looks'. The test button is still here, if it gets clicked, it still returns us to the dashboard. [00:14:01](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m01s) Let's open the test. Here is a new button  'Worked'. If it gets clicked, it will indicate that the work was done, because the method returns 'true'. Open the IDE. Look at the controller in the back end. [00:14:32](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m32s) First, open the list one(looks.php) which is the plural version. It may be seen that 'getTested' has been added, and there the little method may be seen. Then go to the edit singular one(look.php), and getdone. [00:15:00](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m00s)  Here is the method and all the functions.  JCB has added the script to the translation text. Everything here(See video) looks fine. Go to the model, open the 'Look' model, it may be seen that it has a new method added. [00:15:22](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m22s) So just after 'getTable', is the little method added.  So add this to 'false', and save. [00:15:47](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m47s) Go back to Joomla and then click that 'Work' button again and it says work was not done because the method returned false. So if that is changed to 'true' again, and saved then it should work. 

### Demonstration Adding A Button Inside Of Edit View

[00:16:10](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m10s)

Now let's test out another one. Make this to not execute, save this(see video), so we can get this 'error'. Go back to Joomla and click the 'Worked' button. Now it even kicks us out of the item and indicates that a major error has occurred. The reason is that it did not check it in, which is not ideal, but that need to be fixed by looking at some of the other controllers and see what is happening when this problem occurs. This is what has been expected. Change this back, and save. Go back to the view. Open that view again. Click the button. All is done and good. That is a quick demonstration of adding a List button, as well as adding a button inside of the edit view. 

### Demonstrate Button - Both List and Inside

[00:17:29](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m29s) 

As mentioned before one button could be added, both as a 'list' and an 'inside'. It can be demonstrated when going to that specific button. Open it and then instead of saying 'list in Target', say both. Click Save. [00:17:58](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m58s) It is important to add this method 'getTested', also to the single view like that, then save. [00:18:22](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m22s) Close out of editing the Admin view, compile and install it. First, go and look at the code to see where the button has been added, If 'Look' is opened in the 'View', a 'view.html.php' is opened, and you go to 'Add Toolbar'. It can be seen that it has added a custom button 'getDone' and 'getTested' to the view. [00:19:22](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h19m22s) It is the 'getDone' method that is going to be called by this specific button. It is going to look in the 'Look' controller and get this 'getTested' method.

### Adds A Permissional Switch

[00:19:43](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h19m43s)

It also adds a permissional switch to the button. If this specific user does not have the right to use the 'Worked' button, then it will not show the button. If those permission structures are carried through to the controller, it will stop it even from being executed, manually via URL. It is necessary to be familiar with this kind of security and implementation. [00:20:14](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h20m14s) Look at Joomla's way of implementation because it is important to check in the controller whether this user has the permission. It is necessary to know how to check that permission as well. (See Video) That is showing how the button gets added into the view, and where that code is. If in Joomla a component has been opened and 'Looks' were opened, 'Tested' will be seen to be still there. If 'Edit' is opened 'Tested' may be seen there as well, and if it is clicked, it will take us to the dashboard and perform the same function as it would have if we had clicked 'The Test'.[00:20:53](https://www.youtube.com/watch?v=VyBxWpJWb40&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h20m53s) That is to show that one button can be added to both the List view as well as the Edit view of the back end Admin area. 
