# EXPORT IMPORT OF FULLY MAPPED COMPONENTS

### Various Linked Concepts to A component is Exported 

 [00:00:00](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
 
A new feature has been added to the advanced Component Builder for Joomla which can become very useful in the future. It allows you to export a component out of JCB, and not only the component's information, but everything attached to it. [00:00:34](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m34s) If the component has Admin Views linked to it, and those Admin Views have fields linked to it, and those fields have field types linked to it, and those component has site views, and Custom Admin views, and those Site Views and Custom Admin Views has templates and layouts, and dynamic gets, and all these various linked concepts to a component, is exported. 
 
### Two Ways To Export A Component - Encrypted And Non Encrypted

[00:01:09](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m09s)
 
The way to export a component is to simply click on 'Export Components'. Select the component or components that should be exported. There are two ways how a component gets exported. One is an encrypted way, and the other is non encrypted. 

### Smart Export Builder

[00:01:40](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m40s)
 
Let me show that in the code. There is a method called 'smartExportBuilder'. The 'SmartExportBuilder' gets fired at the very end of the compilation or rather the build. Where all the data has now been extracted from the database  and it's now one big array of objects. In this function called 'getSmartExport', is where this data extrusion takes place. 

### Export Key

[00:02:21](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m21s)

During this process an account is taken of a specific value. That value's name is 'export key'. So in this 'foreach' we are looping through the components that have been selected. If more than one have been selected, then it will check whether there is an 'export key' for that component. It is set in the user interface. When a component is opened, it has a tab called settings.[00:03:00](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m00s) At the bottom of the right-hand column it has a new field called 'Export Key'. Any value may be placed in here. If this value is left empty, and only this(sermonDistributor) component gets exported, then the component will not be encrypted. If a value is added to this (Export Key) field and this component is exported, it will encrypt that component's data; the database values. [00:03:32](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m32s)It will not encrypt attached files or folders or images that are part of this component. It will only encrypt the data from the database. 

### Export Key - Encrypt All Components

[00:03:54](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m54s)

 If multiple components are selected, and any one of them has a key, then it will encrypt all the components. It will be explained again in the code how this is done. Return to the code. It needs to be asked: Does this component have an export key? [00:04:16](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m16s) If it is 'true' and it has a 'string', this  key is encrypted in a database. First check if it is possible to encrypt it, and then encrypt the key. Then add it to the key array with the component's ID. An array is being build from each component's key. [00:04:41](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m41s) If a component does not have a key, it simply ignores this script and it continues building its data set. Then once all the data set of all components are finished, then in the 'smartExportBuilder' it may determined if any keys had been found.  

### If Any Key - Implode The array

[00:05:12](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m12s)

If any keys has been found, the array is going to be imploded and converted to a 'md5' string. We will then use this 'md5' string with an 'Aes' encryption cipher to lock the data. [00:05:37](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m37s) There is the data(See video). Above here   the whole data set has already been changed to a serialized string. There is a string in this(data) variable and here is the whole string encrypted. In this(data) variable is the encrypted value. If there are not any keys, even if that means if none of the components that was selected had any keys set, then it will default simply to do a 'base64_encode'. [00:06:09](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m09s) That as well,gets written to the file that is part of the package. That is how it exports the data. [00:06:43](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m43s) So it exports the data and then checks whether there is any keys. So if there is, for example: Export five components, and all five components have keys, all five keys will create a very long string, and then that whole string will be changed into an 'md5' string which is 32 characters. That 32 characters is then used to encrypt the data.

### Exporting A Component - Generating A Key

[00:07:13](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m13s)

This key which is used to do the encryption, will be shown in the interface after the data has been exported. Go back to the user interface and export a component. The(Learning Manager) component has a key. There are other components that has no keys at this stage.

 Learning Manager is used as a demonstration. [00:07:52](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m52s)

Click 'export component' and as may be seen it generated a key, which can then be used to import this package into another JCB. It may be imported it into the same JCB, but it is obviously not necessary. It could also be used as a backup.  It is storing the compiled package in the temporary folder at this stage. [00:08:55](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m55s) Here is a exported component at the moment, if the data sets are not too large and the memory settings on PHP and so forth are allowing this kind of compilation, all components can then be selected and exported. The result will be same. Since only one component is set with a key, all of them will be encrypted with the same key. All of them will be stored in this package. All the components have been exported into this one package. 

### Importing Components - JCB_smartPackage.zip

[00:09:41](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m41s)

To demonstrate the importing of this(JCB_smartPackage.zip) data set, a blank website is used. [00:09:49](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m49s) This blank website, has no special JCB components. First, JCB has to be installed from GitHub. On GitHub the releases should be opened. [00:10:14](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m14s) The link is copied to the latest release. Go back, paste that in here(Install From URL) and install it. The installation was successful. Go to Component Builder, and open the components. As may be seen [00:10:43](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m43s) there is only the demo component. If all these components need to be moved to the new install, click on 'Import Components'. Browse to that package that have just been exported and upload it.

 
### Two Features - Force Local Update - Use Key

[00:11:13](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m13s) <<<<<<<<<<<<<<<<

We have two features here. This force local update, what it will do, is on normal circumstances if you do a import, the import function looks at the data that are currently in this JCB install. For example we're talking about field types, fields, admin views and site views. [00:11:42](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m42s) If it finds a site view that is being installed, that is already in the current database, it looks at the last modified date, and then by that determines whether the current installed version is newer. If it's newer it will by default ignore the new data and not install it. Sometimes you might get a package where you would like to force that it updates the current data even though it may be all the data. So this is why we have the switch, you can then click yes to force the update. [00:12:20](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m20s) We have a key for this package, so we'll leave this to yes. I'll just come over here(Joomla Components) and copy that key. This key will then always be necessary if you're importing this package. That will be it and we'll click continue. It might take a time since this is quite a huge dataset. You could just patiently wait. At last it is installed, it tells us that the install is being successful. You might get these warnings. 

### Warnings - Remapped

Now what these warnings is really telling you, [00:13:01](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m01s) is that during the install you realize that lots of ids will change. We are working with a database that creates ids as the new item is added. Since these are the ids is used to link into the various components, views and places, all these ids must be remapped. We have been able to  [00:13:30](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m30s) find a very well formulated algorithm to resolve this problem. So it remaps all the ids. Sometimes there are certain ids that wasn't possible to remap. We are telling you about them. You could see that the target field in the admin views has a mismatch in the field with id.244. You can go back to the old install, and try and find out what happened there. [00:14:04](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m04s) Most of the time when I have reviewed this, usually it is because that specific field is no longer published or is no longer available for some reason. So this is just giving you a heads up of any changes that may have occurred. You can go to these various places and manually fix them. Most of the time these warnings will not show and everything will just say all is right. If there is warnings and errors just simply read the messages slowly and closely. I'm sure you'll be able to resolve it [00:14:43](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m43s) quite easily. 

### Mapped Components

Now just to show you that it actually does work, I didn't mention before but it actually moves all the customer files, custom folders, as well as all the images per admin view, site view and wherever to the new install, so it moves it into its right place. So if that is true we should be able to go to the compiler, select any of the components. [00:15:19](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m19s) It should load that components image here, I should be able to just click compile. It should be able to simply compile that component after compilation. I could click installing the component. If this component was correctly mapped previously, and I were to go to that component, I would see that everything about the component is right and it works well. [00:15:51](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m51s) That is this new feature in action. I really hope that it will be as useful to you as it's going to be to me, and that you will have fun with it. I must tell you I suppose that at some point we could even start looking at selling mapped components. I have a number of components that was made for specific purposes, but could be easily adapted for others. [00:16:22](https://www.youtube.com/watch?v=lkE0ZiSWufg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m22s) I'm starting to look at the idea of selling mapped components. It's a little difficult because it's basically selling the rights to it in a way that you could resell it. So I'm not sure what would be the price tag of that.
