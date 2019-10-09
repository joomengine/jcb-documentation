# DYNAMIC ROUTER IMPLEMENTATION EXPLAINED

### New Implementation - Help For Router Complexity

[00:00:00](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

I would like to demonstrate the new implementation which is not such a major thing but something we have done to deal with some of the router complexity. If a component is built and has a front end for your component, and you have Site Views. [00:00:17](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m17s)  Your Site Views usually are getting its data from a Dynamic Gets which you link up to the Site View. This Dynamic Gets returns a result set and it is from this result set that we should get information by which we combined with the view name, build what is called a  search engine friendly URL. 

### Search Engine URL Is Done With Router - JCB Builds Router

[00:00:49](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m49s)

Your search engine friendly URL is done with the router. JCB also builds the router and it sort of guesses what should be these values(See video). Let me compile a component and show what it guessed, and then see how we would need to change it. The component that we are working with is Sermon Distributor and it is going to be compiled and installed on this website. [00:01:16](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m16s) The router does not work. I am not going to demonstrate the actual front-end. 

### Code - 'com_sermondistributor' - router.php

[00:01:26](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m26s)

This is explained in the code. In the website, there is a root directory 'Joomla mount', 'admin' and then 'components'. In there is Sermon Distributor and there is a file called '`router.php`'.  

### parse - switch(segments[ ]) - First Value 

[00:01:44](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m44s)

Open` router.php`. There is a function called '`build`', a class method as well as a function called '`parse`'. In this function called `parse`, there is a '`switch`' which makes decisions based on the '`segment's`' first value. [00:02:08](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m08s) Usually that would be the view name in this first value. It determines which view are we looking at, is it, `preacher`? and so we are going through the list. By default without us making any changes, JCB builds that for us. 

### Preachers - Getting All Items From Database With No Input From URL

[00:02:33](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m33s)

If we look at `preachers`, which is a listview and open the model, `preacher.php`. Here are `preachers`, we can scroll down and see that in its query, it has `getItems` and here it got a `getListQuery`.  [00:02:51](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m51s) It is getting all the items from the database with no input from the URL whatsoever. It does not do any of that and then it just gives it back. It does not need a URL value. [00:03:18](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m18s) So that means it most probably will only set this value `$ vars['view']='preachers';`. All of this(follow on video) will be redundant because it is a listview, there is not an alias. We are not looking at an individual item so there is not an `id`, this code can be removed. [00:03:44](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m44s) It is a default being generated. 

 Preachers are the listview, but then there is a view called `preacher`, and it says that it needs to get the `id` from the `sermon` table which is an error. [00:04:09](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m09s)If I open the `preacher`, and look at the `getlistQuery`, there it is getting an `id` from the URL. It is asking that it should be `= to preacher`. [00:04:34](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m34s) It is the main table, `sermondistributor` , but it is not looking for the `sermon id`, it is looking for the `preacher` value in the sermon table. That is why JCB fell back onto the table name. Yet it should go to the preacher table and see whether [00:04:59](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m59s) that preacher value is `=` to this `id`. It creates an error.  You should understand the logic of what you see in the code, if not, then this feature in JCB, will not be useful for you. 

### getVar Class - See What It Is Going To Do - How It Is Getting The Values

[00:05:31](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m31s)

This is an error because we want to get the value, the `id` of the `preacher` is the one we need to check. It is doing it wrong, this value here should be `preacher` not `sermon`. You can look at the `getVar` class here at the bottom. Here you can see what is it going to do, and how it is going to get the values. [00:05:56](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m56s) You can also use the `getVar` class for your own purposes. At this point, we see at least one of the router case within the parse method. In the case loop, there's at least one router area that needs to be changed. I know by having looked at this before, that there is more than one, it is also `categories`. [00:06:25](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m25s) This one should also change(see video), it should be set `true` because this is a category lookup. 

### Another Change To Be Made - Series

[00:06:38](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m38s)

Now the other place also needs to change is '`sermon`' it should also be '`series`' [00:06:43](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m43s) So this is where the guessing which JCB does dynamically did not match the complexity of our Dynamic Gets. As time goes on we might improve its guessing and get better ways of guessing correctly within the dynamics of the Dynamic Gets to build this case more effectively.  [00:07:14](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m14s) Since it had not been done yet, the quickest way for us to resolve this and which most probably will be the most dynamic option, is to add a way to replace the snippet of code and target the specific view. You will never need to know what is the view when you do this because they are placeholders but only need to remember where you have added the Dynamic Get. 

To illustrate this within the JCB interface. With this new dynamic implementation, the snippet in this area is targeted(follow on video). [00:07:53](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m53s) The whole method is not replaced, because it is standard, there is not much to do in improving that. The 'Build' function is working well. I have not seen any issues with that. At the end of the day, it seems like only the `parse` method needed a bit of an improvement.

### The Interface Where You Can Make Changes In Dynamic Gets

[00:08:19](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m19s)

Let us return to the interface to show where the changes can be made to have the `category` rendered correctly as well as the `preacher` and the `series`. Basically, make the changes so that `sermon` will say `series`, and this one will say `true`,  and this one `preacher` would also say, `preacher`.[00:08:48](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m48s)

 That is all that needs to be done and the router will work without any errors. Here in the interface, are the Site Views that need to be changed, which are Preacher, Series, and Category. [00:09:15](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m15s)  If Preacher is opened, you will see that it has a Dynamic Get called 'Sermons' (preacher id) and it is a (getListQuery). This is the one that should be changed. [00:09:35](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m35s) The Dynamic Get, as well as Series', the same applies to that. There are Sermons (series id) (getListQuery) that also need to change. It is not changed in the view. The idea was that if it gets changed in the Dynamic Get it will automatically write the correct code to whatever view is added because we have added some Custom Placeholders within the script. 

### Sermon (series id) - Heads Up For Placeholders

[00:10:06](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m06s)

The first one is Sermon (series id). In Custom Script scroll down to the bottom, there is a new tab option here, Add PHP (parse Method)-in Router'. [00:10:29](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m29s) Click 'Yes', and it will dynamically load what can be considered the most basic implementation of that short snippet. It looks very familiar, it got these placeholders. It has a specific sview placeholder because we are dealing with the Site View and it has to have this 's' in it to replace it with the site view name. [00:10:55](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m55s) 

So wherever this is going to be used, this Dynamic Get would be replaced with that specific site view's value. That is to give a heads up about the placeholder and that is what makes it dynamic, that you can use it in any site view and it will automatically write this because the display of the page is based on the database request which is built in the URL by the name of the view as well as the ID of the element. If multiple variables are being passed [00:11:32](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m32s) to the URL, you can update that and replace multiple values. In this one, the default option will resolve the issue because remember these two values were not the same. 

### JCB Change view to sermon

[00:11:56](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m56s)

JCB's Dynamic Build changed 'sview' value to Sermon instead of leaving it the same. There is a very good reason for that. Usually, this would be the correct response but in this case, it was not. (Due to its complexity, I am not going to explain it), so you want these two values to be the same and it is the site view's name. We could just save it close. 

### Sermon (Preacher id) 

[00:12:20](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m20s)

The next one we are going to do is Sermon (Preacher id). It was also having the same issue. We are going to just add the Custom option to ensure that these two values remain the same. 

### Resolving Category 

[00:12:39](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m39s)

Last but not least is the Category that behaves incorrectly and it is only because it did not detect that this is a category. [00:12:47](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m47s) That is primarily because it is using the Sermon table to start instead. In the Sermon table, we have a Joint here to the category that loads the category. [00:13:12](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m12s) 

In the Tweak, the (JRequest) ID is used, and this is a category ID. It should go and look for the category and build the parse method based on the category. In Custom Script we are also going to add a 'true' to this getVar, which tells the getVar method that this is a category. [00:13:33](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m33s)  This name in effect is going to be ignored because it is not going to look for the value of this table, it is going to the category table and look for the value there. This will resolve this issue. Save and close. [00:13:59](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m59s) 

Now we have done some customization to our Router just by adding those values to the Dynamic Get. If we compile our component now, it will automatically fall back to those values. Just install it again. [00:14:21](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m21s) Let's go look at the code. It did exactly what we wanted, it added `preacher` there. This category is `true`, and we see the series is `series`. At least we know that the router will behave correctly. This is the first step of our improvement to the router. [00:14:49](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m49s) 

 There was also the idea of adding some custom scripting into the built method. We will look at that and I invite you to get involved in this on GitHub. If you know how to improve this, please [00:15:16](https://www.youtube.com/watch?v=hYycPLbaMos&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m16s) get in contact with me and let's work together. This is what we have done so far. But like alliterative developing concepts we will continue improving this to the point where it serves us well and holds up with changes in Joomla. 