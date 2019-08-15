# COMPONENT FTP AND MORE

### Adding README Script

[00:00:00](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

Next, we are going to add the README script to a component in the component view. The README script is commonly used as the components homepage. For example: If you go to the demo components page on Github, you'd see that it has this image, some details, and some layout. (See video.) This all is done with the README file. We can open it and look at the 'Raw'. It is the same text that we looked at previously. [00:00:53](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m53s) Inside component builder you can add this README and README text. These are placeholders. (###version###).

### Place Holders

[00:01:10](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m10s)

Now (#) is part of the markdown for a header. You need to be acquainted with Markdown to know what is placeholders and what isn't. This script has been added in order for you to get an idea of placeholders. [00:01:27](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m27s) These placeholders are automatically updated from the details that are in these fields. The actual placeholder names can be seen. If you change the version here it will update there automatically. (See video.)

### Component-Builder Link Back Info

 [00:01:59](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m59s)

This is a place to give information to those who are using your application. You can add links to it, add links to help menus, instructions on installing it, or anything else that you like to share through the README file. Although it is not compulsory, it will be appreciated if this commenting area can be left as it is in order for more people to get involved in the community. Help us to sustain this project. [00:02:36](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m36s) 

### Markdown Info

[00:02:46](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m46s)

If you want to know more about markdown, you can open this link: https://www.markdownguide.org/cheat-sheet/

### Admin - Site Views Adding Editing

[00:03:06](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m06s)

This admin view area and the site view area is a place where you can create new admin views.  Realize that if you create a new admin view it's not necessarily linked to this component. You still need to link it in settings under admin view. This is a place to create admin views or edit existing admin views that are linked to this component. The same applies to site views. It's an easy way to gain access to editing the site views that are already linked to this application.

### FTP Info - Updating Component

[00:03:57](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m57s)
 
The FTP server had been added to make it possible to move the component to your server and to add the feature of automated updating that is in Joomla. The update server is a Joomla concept. For example: If a component like 'Sermon Distributor' is opened and we look at the XML file of this component in the back end, you'd see that Component Builder had built the whole file. [00:04:39](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m39s) But at the very bottom you'd see an updates server. It is being added only if you set it. If this is set to 'no', it won't add an update server. [00:05:03](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m03s) If you add 'yes,' you can set the link to where the update server is going to be hosted. It will automatically take that link and add it into your XML file. Component Builder can also build that file for you. This is what it would look like. (See video.) [00:05:31](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m31s) This FTP Binary is usually 21, the default value FTP binary would be 15, and a username and a password. [00:06:04](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m04s) These FTP details should log in directly to this folder that you have up here. (See video.) Component Builder logs into your server, move this file in there, then disconnects. (See video.) This information will make it possible for him to perform that.

### FTP Info - Sales Server

[00:06:32](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m32s)

The same applies to the sales server which is nearly the same concept. You will add the same kind of string, although usually the update server and the sales server isn't the same place. [00:06:47](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m47s) The update server lets the user know that there is an update. Whereas the sales server lets the user know where this component zip file would be stored on the server. In the case of WHMCS or another component through which you are selling your extensions, you can use the folder on your server that is looking for the files. You can use that folder, create an FTP account in that folder, then set those details in this field. (See video.) If 'compile' is clicked, Component Builder shows 'add backup folder' and 'save sales server.' Click 'yes'. If you compile it now, it will move the 'zip file' to 'sales server' as well as creating a backup.  [00:07:30](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m30s)

### Component Builder Global Options

[00:07:49](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m49s)

The 'backup' and the 'Git' folder is set up in your Components Global options. If you open 'Global Options', you will see this area showing that this field is encrypted.  If you go to global settings in Component Builder it shows the encryption settings. [00:08:18](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m18s) Once you added your own key it will encrypt. You must not change it because it will not be able to decrypt, as it is used to encrypt and as well to decrypt the data. Consequently, everything that has been encrypted needs to be redone. In this case, this login FTP login information. This is the basic encryption which has been mentioned when we talked about storing types. There are basic encryption and advanced encryption. We are dealing with the basic encryption which is also called 'basic key.' [00:09:01](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m01s)

### Component Builder Folder Paths

[00:09:13](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m13s)

'Compiler folder' and 'custom folder' are not flexible. To move them at this stage is difficult, so leave them blank. At 'Backup Folder Path' you should add a backup folder. This should be related to the root of your server, as well as to a 'Git' folder. [00:09:41](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m41s) The 'Git' folder would be where component builder creates a folder with all the components files without zipping them. You can go to that folder and create a 'Git create' and a 'Git repository'. From that folder, you can push it to Github or any other Git server respectively. It's able to create a folder from which you can do Github or any other kind of repository work which is separate from your backup folder and from the temporary folder in which it compiles the component. [00:10:17](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m17s) You can move it out of your Joomla install. The function of the folder paths does the Git Repository when you compile the component; it will not delete the. Gitfolder, just replace all the files in it. First, remove the old ones then add the new ones. Git will see that only changed files will be noticed, and see which ones you need to recommit and do a normal commit to get into your repository.

If you don't know Git, it probably doesn't make sense to you. There are courses about Git on Lynda.com: https://www.google.com/search?q=lynda.com+courses&oq=lynda.&aqs=chrome.2.69i60j69i57j0l2j69i60j0.7499j0j7&sourceid=chrome&ie=UTF-8
as well as Udome.

That's a backup folder and the sales server. [00:11:18](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m18s) The same applies with these FTP credentials which should be the direct folder in which these zip files should be stored. Unfortunately, Component Builder cannot store it in subfolders at this point. The FTP details will log in to that FTP account; in the folder which has the access, you'll place the file. The FTP details should go directly to the folder, not sub-folders or other folders. In the Component Builder in the back end, there is a file called 'compiler'.  [00:12:14](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m14s) If you open the file, you'd see a function called 'buildme'. All the placeholders that you can use in the 'buildme' file are here and will be replaced with the relative information.

### Component Builder Compiler.PHP FTP Info

[00:12:32](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m32s)

There is a function called move file to FTP server. This move file to FTP server, calls another function, 'getFTP' here. (See video.) It takes the signature, checks whether we already made such a connection before, and then loads that object. Here I'm using a parse string function to convert the string into the variables. All the variables in that string are converted to arrays or variables respectively. [00:13:12](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m12s)  That is then used to make use of Joomla's own client FTP class. Click in NetBeans 'control spacebar' libraries/Joomla/client/FTP.PHP if you want to know where that is. We will be using Joomla's built-in FTP client; we pass the host, the port, the option, the username, the password, and make a connection. Then we send it to do this move file, which then takes the file content and moves it to the server. The data itself is not being leaked or compromised. [00:14:04](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m04s) It's all handled here so you can follow its events in Component Builder; from 'relations' to the update server and the sales server.

### Update Server Extra Info(Versions)

 [00:14:23](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m23s)

This update server, an XML file, is quite important. This XML file is built up from versions and download links to those versions. While you are developing your component your users wouldn't need any change of updates, etc. [00:14:47](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m47s)  The moment you put your component on the web you need to consider when you might make a change in the application and how your user will be able to adapt to that change. The biggest changes you can make is to add new views or fields to the component. [00:15:03](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m03s) You also need to consider the database. We created Version Updates which gives you the ability to add SQL scripting that should be executed upon the updating.
* **Table Alteration 1.2.9 version**
If you have the new version, 1.2.9, there needs to be a table alteration. [00:15:43](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m43s) You need to know if MySQL commands it. You need to put that MySQL command in MySQL - Update Dump according to the Joomla conventions. The table name must have that '#_ _' in front of it; Joomla will dynamically add the prefix. You might do a MySQL script here. If you are making a change and the new release is 1.2.9 and 1.0 didn't have the specific field of view, you must realize that you're updating this one and the SQL must come next to that specific version. [00:16:23](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m23s) The update must be placed at the version, which needs the update. If you make a change don't place it here because it won't update correctly. (See video.) You need to place the update next to the version that should be updated. [00:16:44](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m44s) Over here you'd put the link to the respective downloads. (See video.) For example, here we have version 1.2.9 and a version 1.3.0. [00:16:59](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m59s) We added the 1.3.0 link. (See video.)

I'm using GitHub as my distributing platform of the application. You could use any URL which will be used in your updates server. [00:17:18](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m18s) In the update server go to the update server link and copy that. You'd see URLs for the download. As we move on it 1.3.0, 1.3.1, 1.3.2. it gets these details. It gets them from this version update area. [00:17:48](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m48s) The last version in this list being 1.3.2, must be the same as the one that you set here. (See video.) We are at the current version and it will do the necessary adjustments to it. [00:18:07](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m07s)

That is all the concepts necessary regarding the component area. We've looked at adding admin views. [00:18:26](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m26s) We will look at site views, adding them, as well as your custom admin views. We might look at the MySQL tweak we briefly mentioned. But the for the most part the component area and all its features. [00:18:48](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m48s) It all stacks on each other from the fields, the admin views, and the components themselves. If you have come this far setting up your component you are now ready to start building the front and the site area. [00:19:06](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h19m06s) You wouldn't have been able to do that effectively until now. It is necessary to do the admin views first and then the site views.