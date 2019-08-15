# INSTALLATION OF JOOMLA COMPONENT BUILDER

###  How To Build a Component

[00:00:00](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

We are in Component Builder at the Dashboard in the back end of a Joomla website. I would first like to show you the tremendous power of what it is able to do, and then we'll step back, and little by little show you how to build a component.

First I will show you the components that I have build and how I have been able to manage them. As you can see, this is the Component Builder for Developers. There is the Component Builder for Developers and how to's. Then there are the three Component Builders, and all three of them are living inside the same Component Builder. The only difference between them is the database in certain things that they compile. But they all are using the same admin views, infrastructure, information, settings, and so forth. [00:01:10](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m10s) It is that simple to have one component, and have it in different versions made available to your clients. Which is all made possible in Component Builder by simply copying one and then making changes to that copied component.

###  Use a Compiler

[00:01:55](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m55s)

I am going use the Compiler and I am going to compile the public one because I will use that to show you how to build your own component. I will compile it, which starts up the compiler and all the script, taking all the data in the database [00:02:14](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m14s) and placing it into the code. Then we would run the application. If it had compiled, it tells how many lines are written and how many hours are saved. Based on calculating the nine numbers and not calculating the actual interaction that we've had, you can install the component if you've done it right. Click in there; or you could download and install it elsewhere, or use this URL which is at the moment relating to my offline Environment. Once you've done whatever you wanted to do, click this [00:03:18](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m18s) if you need it. But if you're running in the online Environment and you use some of these links to install it elsewhere, then play.

###  Clear Your Temporary Folder

[00:03:37](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m37s)

Please remember to clear your temporary folder because if you don't this component can be downloaded in your temporary folder. For example, open that website and go to its temporal folder. You'd see the component in a zip file; anyone that can access this file can download it. I'll be mentioning this a few times because part of why you might be interested in using my application is because you want to ensure that what you do remains yours, and this is part of what you need to know to ensure that. [00:04:22](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m22s)

###  A Blank Test Website

[00:04:47](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m47s)

Now I'm going to open a test website and I'm going to run everything there. I'm in the installing area which is basically a blank test website just installed. I'm going to use this link there. I paste a URL and click install. It should say the following to you when you have done that.

### Need To Add Database Information From Paid Versions

[00:05:19](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m19s)

Just a side note. (This is if you've started working with Component Builder as a free version and you've purchased one of the paid versions.) The difference between them is only the data that is in the database. The features and functionality are all the same. If you have installed the free version, you would need to add the database information from the paid versions.

### How To Access The Database Information In Your Component

[00:05:49](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m49s)

To continue on how to access the database information in your component.
I'm going to the zip file here in my file system. The zip file open here would go to the admin. [00:06:02](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m02s) Now go to SQL. You'd see an install file. Open this install file. You want to guarantee that you would see it. It's the file that we are using to build a database. Look at all the tables at the very bottom of the file. [00:06:28](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m28s) After the tables there will be dumped information. Now with the free version, it's basically the field types that we've added, also some help menu information if I'm correct. With the paid version there will be many more details here. 

###  1. Uninstall The Free Version - Install The Purchased Version

[00:07:05](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m05s)

There are two ways for you to do this. The first would be simply to uninstall the free version and install the one that you have purchased when you do updates. It will never update this information. Joomla only uses this when it does a fresh install because that's the only time you create the tables. I didn't add this data to install since that would be too much. [00:07:29](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m29s)

### 2. Requires MySQL

[00:07:41](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m41s)

The second way to do this requires knowing My SQL. You can cut and paste this into My SQL, and replace this with the prefix of your tables. But first, remove the data that are in the tables. Let me show you. Here we are in My SQL and there are the Database [00:08:03](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m03s) Tables of Component Builder. If you look at our archive you see that this is going to target the field types. So you go to field types. If you're importing the new data, go to operations, truncate the table like that, [00:08:30](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m30s) then go to My SQL. You go back to that file and replace all those with the prefix. Make sure you don't grab the wrong stuff by accident. [00:09:15](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m15s) Let's go back to our data. You would see how I have updated the field there. Select and copy, then [00:09:49](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m49s) go to My SQL and paste it. Click go. [00:10:29](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m29s)

So that is how you would add the data without uninstalling the whole component. But since this is more advanced, I would suggest another way. Go to the extensions manager and click on [00:10:53](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m53s) this manage area here. Select component and uninstall it. Then reinstall the one that you can download from VDM.IO. Once you have it installed it should look like this in the back end. [00:11:20](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m20s) You should have no components. The only things that will remain are the field types and only a few of them. Now I'm going to uninstall the free one, then install the paid one. As you can see it not only removed the component but it also removed any traces of it that was integrated into Joomla. If you install it again it doesn't start creating duplicate values in the database. Let's install the paid version.

### More Field Types

[00:12:15](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m15s)

Now if we go back to the component and to field types, you'd see that it has more field types and it has a few fields setups as well. This is the version called Developer which only has the demo component in it. I'm going to use this version to show you how to build sermon distributor [00:12:44](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m44s) from scratch.

We'll continue with field types in the next tutorial.
