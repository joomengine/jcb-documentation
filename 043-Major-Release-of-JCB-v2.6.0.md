# MAJOR RELEASE OF JCB v2.6.0

### Removing All Repeatable Fields in Joomla Component Area

[00:00:00](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
_(Click on these time links to see video)_

I would like to demonstrate how to upgrade to JCB version 2.6.0. It is quite a major upgrade since we have removed all Repeatable Fields in the Joomla Component area. Joomla Component area has quite a lot of Repeatable Fields. On opening the component it may be seen that Repeatable Fields are little models that pop-up with values which had been used quite excessively in this view.[00:00:43](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m43s) The reason why this was done is because it is a very smart Field since it combines these values into one value. The JavaScript on the page grabs these values and converts it into one value, when on submission the form only submits one string, and not several Fields.[00:01:13](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m13s) There are some conventional reasons which makes the Repeatable Fields on a Sub Form level more desirable, due to its ability to validate the data more correctly. [00:01:34](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m34s) We had to remove these Fields because in Joomla 4 they no longer are supported. I had to decouple a number of these Fields into their own Tables because of the size of the values that is on the page, the page becomes immensely heavy. There had been about 9 new Tables added to JCB, to accommodate this. 

### Changes Only Effects The Component Area

[00:02:03](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m03s)

The real change is only going to effect the Components Area. But because JCB is very Dynamic Component that integrates with various levels of this Data Structures.  

### Upgrade: Compiler Import/Export Of JCB Packages

[00:02:20](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m20s)

The Compiler had to be upgraded , as well as the import and export of JCB packages. We have tested this and for the most part those involved with the testing, have found that this transition is a Major improvement to JCB and will be very easy and without any issues.
 
### Suggestion - Clean your Browser Cache and Browser Memory

 [00:02:47](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m47s)

If you run into glitches that does not work as expected, it is suggested that you clean your browser's cache as well as memory. It has been found that traces of the old Repeatable Field Structure and JavaScript surrounding that might clash with the new changes in JavaScript within the new update. To clear the browser memory and not just the cache, is quite important. Only after you have upgraded and started to work in different views, it will be seen that everything works as expected. 

### Dynamic Get Area Some Conflicts

[00:03:29](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m29s)
 
The Dynamic Get Area has been reported to have some conflicts at this stage. The Dynamic Get Area returns values  from the Admin Area where, if we target let's say Back end View, and we grab some information.[00:03:55](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m55s) These values are returned from the Admin Area where it goes to this Admin View, and builds this structure. [00:04:04](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m04s) With this demonstration everything is working as expected. If this area is tested before the upgrade, it should work without any problems. If it does not, it is suggested to clear the browser memory and to try again until it is working as mine.[00:04:35](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m35s)  All that has been done was that I cleared my browser memory, so that there is no traces of JavaScript.<<<

 I mean literally going to history and wiping everything for this domain. If you don't want to clear all of your history then it specifically targeting this domain that you are loading your JCB Component in. That is few heads up for [00:05:10](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m10s) the current 2.5.8. 

### Update in Managing Area

The upgrade should be quite simple. You should be able to go to updates in your managing area. See that the upgrade is there and ready. Click on it and click update. The upgrade is been done. [00:05:41](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m41s) If we now go back to Joomla Component Builder. We should see that it's up-to-date, and everything is been done without any errors. If we now go to the Joomla Components Area, you should see [00:06:00](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m00s) a view similar to this, with a lot of new shortcuts to these different decoupled areas that I mentioned. 

### Edit Component Update

If you open the Component, not much has changed in regards to where what is located, but how to interact with it is been moved. For example the Component Updates if you see it has a button 'Edit component update for this joomla component', if you click, it's going to ask if you first save everything before you continue. [00:06:30](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m30s) If you've done so, then click 'OK' and it opens the area where you then would do your updates. Usually it was in a model that popped up, and you could change it right there on the same page. Now you simply go to another view and is doing the same. The same goes with your Admin View, Custom View, Site View, and everything else. 

### Contributor Moved Down - Do On Page 

The contributor we've moved down so you could [00:07:03](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m03s) do them on the page. But for most of the other Repeatable Fields we've moved them to their own Tables. 

### Moved Component Files And Folders To Joint Table

The Files and the Folders we've moved to a joint table. If you were to click on 'Edit component files folders for this joomla component' you should be able to easily add some Files to your Component or Folders. All found within this [00:07:29](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m29s) Structure as it's explained here in the note. The same is true of all the other areas. 

### Moved Admin Views To Its Own Tab

We've moved the Admin Views to its own tab. You could access them via this button (In Settings - edit component admin views for this joomla component) or via this one(Admin View Tab) [00:07:54](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m54s) In Editing the Joomla Component area you would see your changes. You could also from here directly edit the Admin View that you've linked. It will be able to edit the Admin View directly out of your Component area. That's a nice new feature which [00:08:15](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m15s) I suppose will come in very handy. That is the new upgrade as it targets the majority of the changes in the Joomla Component Area. We do have a lot of data checks all around JCB at this stage. That if during the upgrade we might have missed a Field in not converting it to the new Sub Form layout. Then when opening a view, it runs through all those Fields, and make sure that it's been [00:08:54](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m54s)  changed and converted. If by any means you didn't get around to opening the views, and you go here to the Compiler, and would click compile. It does that again, it runs through all the Fields and it makes sure that it's in the right format. Therefore you're compiling should work just as before. 

### New Feature - Translation Checker

The new features we've added is this [00:09:23](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m23s) Translation Checker. Which checks how many strings there is within your component. And how many you've translated for this specific version. New language available for the Admin View, the Admin System View, the Site View. Again for the another Language, Admin View, Admin System View, and the Site View. Giving you a little feedback on your progress. Because we realized that this area of JCB is not [00:09:59](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m59s) may be utilized as much as it can be. We making some awareness. This area is available. 

### Becomes Active If Language Is Setup

It only comes and becomes active if you've got some Language setup. You need to have some Languages in your Languages area. And you need to have have compiled that component at least once before. [00:10:26](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m26s) Because the Language string stored in JCB found on the Language Translations is only generated once you've compiled it, at least your Component once. Then it links the Component Language strings to JCB. You can translate them into those Languages that you created. The other problem which you saw regarding to the Back-up folder, because I haven't setup a Backup folder for this JCB install. It'll tell me if I leave the set to yes and I compile. It'll tell me that it couldn't move that Backup file, because the Temporary folder and the Backup [00:11:11](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m11s) folder is the same place. It's saying it couldn't move the file to the same location. That means this is not an error. It's just a miss configuration. We haven't setup the Back-up folder to be a separate from the Temporary folder. If you need some more help regarding the Translation Manager, please go watch this tutorial. Here we do give you a notice the that you can in the options area of JCB, [00:11:42](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m42s) you can change the percentage of translation required before a translation is added. Currently it's set to 50%. You can change that to any percentage that you like. That is creating a Component with the new upgraded JCB and compiled that. We can go back to the Demo. We can see that the component was built. And everything is working as expected. [00:12:18](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m18s) 

If you run into any issues that you think is related to this upgrade. And you have already cleared your browser memory. Also note that I'm  using Firefox 64-bit. Then please [00:12:49](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m49s) open an issue on GitHub. We'll try to get back to you and see if we can get this resolved. So far my experience is that this upgrade is taken JCB into a very powerful position, where it is having no Repeatable Fields anywhere in the Component. All its Repeatable Fields have been converted, and is only Sub Forms. [00:13:19](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m19s) We've added some nice shortcuts like you seen to these decoupled areas. You can access them directly without going through the Component View itself. If you wanted to work on, for example, the Component Dashboard, you want to make some changes to the dashboard, or you want to work on the Admin Views, you can click on that buttob underneath the view and work on the Admin Views without going to the Component directly. [00:13:54](https://www.youtube.com/watch?v=MQrLBYhvGyA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m54s) Which I think is very nice convenience shortcut that will make our life a little easier. 
