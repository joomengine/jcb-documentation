# AUTOMATED DATABASE UPDATES IN JOOMLA DURING DEVELOPMENT OF A COMPONENT

### Demonstration - Creating, Updating And Adding Database Tables

[00:00:00](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

This is an explanation as well as a demonstration of how JCB deals with Joomla's implementation regarding the creation of Database tables, as well as updating them or even adding more. Joomla has a way of doing this through specific file conventions within your components file structure package. JCB is also been designed to detect changes in your component's development and create those files for you. [00:00:37](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m37s) The best way to illustrate this is to compile a component. We have Sermon Distributor. Let's compile that and go to the zip file, unzip it. Have a look at it, and see those files extracted in this(com_sermondistributor) we have an Admin folder and in the Admin folder a SQL folder. Here(installmysql.uft8.sql) is the first file of interest that is what Joomla uses to build a database upon the first install of the component. 

### Runs Only On Fresh Install - Thereafter It will Not Run Again

[00:01:17](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m17s) 

NB. It runs this file only on a fresh install of the component, thereafter it will not run it again, even if that file gets updated, even if more values get added and usually it does, JCB updates this file as you create new views which means a new table, and if you add Fields which means a new column or field in the database. [00:0So1:46](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m46s) This file will update but it is for those clients of yours that is going to install the component for the first time. Those who already have the component installed, this file will mean nothing. All the files in this update folder are what would be relevant. If you have a client which has version 1.3.2 installed on his system, and he gets this package from you this 2.0.0 package, it will start with 1.3.2 file, then 1.3.3 and so forth.[00:02:14](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m14s) It will start with a file which is the same version as the version that is currently installed on the Joomla website. [00:02:34](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m34s) That means JCB builds these files in that expected way.

### Making Changes - JCB Updates

[00:02:44](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m44s)

Now let's go make a change to the component and see how JCB updates these files. I am going to install the component so we have it in the database. We can look at the database at the moment to see how things change.  I am going to open the Admin Views and add a field to the Admin View called Sermon. [00:03:07](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m07s) It is going to be any generic field to at least see it in action. I am going to call it Mobile Phone and put it in the fourth position, the left tab, although that is not really important. We added a field. 

### Add A New View - JCB Combines These Values In One Update

[00:03:34](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m34s) 

Now you could at this point also add a new view and JCB will detect both of them and will add both to the update file. You could even make this change, run the compiler, have this new update, then make another change, run the compiler, and it will follow along incrementing the version value of the component as you go.[00:04:01](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m01s)  To illustrate, maybe let me add a view, that is already in another view and then see how JCB combines these values into one update. For instance, grab a view that is not already part of this component. [00:04:26](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m26s) Save and close. There are a view and a new field. If the component is compiled now, it will do all those things that have been explained. There you see that it is incremented into 2.0.1 and if we go to the zip file, again extract it, open it, Admin, SQL, Updates. [00:04:53](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m53s) There is a new file. Let's open this file, and just examine it a little. Here is the command to add that new field and here is another one to create that new table. All of that has been placed into this 2.0.0 file which as I said is the current version of this installed component. If we look at the database at this point there is no 'Look' table. If we look at the Sermon table and Structure then we see that there is Mobile field. [00:05:36](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m36s)  Let's install it and see the change. It has been successful, go back to the table. Just refresh this and the field is added. If we go back to the new table that it was supposed to create There is the new table. It has done both of those as expected. 

### Component Automatically Incremented Its Version Number

[00:06:09](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m09s) 

Secondly, let me show you where it made some changes in JCB in relation to this component. You will see that the component has automatically incremented its version number. If we open this component updates area, it has dynamically stored that same values that we saw on the file, next to the correct version, and it has created a new version entry. You have to manually update this URL as there are too many variations here that could not be implemented dynamically. [00:06:49](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m49s) This URL is what is being used in your updates server file if your component is set to have an update server file. At this point, you can now continue even adding another view or even another field and it will do the same, it will increment and update your database upon installation. There are some places where that behavior may not function as expected. 

### Some Places That The Behavior May Not Function As Expected

[00:07:24](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m24s)

One that I am aware of occurs when you import or export a component from one JCB to another. Those of you that have used this can export a component and then import it again. That effectively creates all the data in relation to JCB, but it does not recreate the history and the asset IDs and everything else which is related to its integration within the Joomla interface or database.<<<<<<<<

### Example - Only Way To Start History - Open It - Save And Close It

[00:08:02](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m02s)

That means, for example, there is no history regarding the Admin views. The only way to start any history for that view would be to open it and to save and close it. Now that specific area will have a history track. The same applies to the admin views. You have to open them and save them. This one(Edit the admin fields) not the admin view itself but the fields of the admin view. [00:08:36](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m36s) Open them, save them again. This will create its first entry and serve as a reference point to the last time to which those values were changed. If you compile the component at that point it will add the two component's ID's to that specific entries, and use it as a reference point. After having compiled it, first save them, then compile the component and only then start making changes.

 You will bring the component into the motion of what would be the natural flow of development which would create a component, add views, then add fields to it, all along with saving, closing, saving, that generates the history values that we need to detect changes. If you import a component none of those values exist and so it will not behave as expected.

 That is just a heads up. I suppose many of you might not even have this issue but if you do, you will know at least where to look and what to do to fix it. [00:09:51](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m51s) That is a quick overview of JCB's implementation to correspond to Joomla's conventions in creating tables and updating them dynamically through the SQL files in the updates folder. I hope that [00:10:16](https://www.youtube.com/watch?v=zN2M15fzf_M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m16s) this is going to be helpful to those who may not have understood this before.