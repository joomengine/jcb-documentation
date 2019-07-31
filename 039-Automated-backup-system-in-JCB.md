AUTOMATED BACKUP SYSTEM IN JCB

### Extension API - Backup Feature

[00:00:00](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

This is a demonstration of the new automated backup feature that has been added to JCB. It is part of an extension which is called the API which gives the option of querying JCB via a URL, to perform certain functions. First would be to generate a backup. We are not exactly sure what kind of features should be added to this API. A discussion about this had been opened on GitHub.[00:00:42](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m42s) For more info: My email address is behind this link(See video). Check the features that we want to add to the API. Currently the first one is the backup feature. 

### Button Called Backup

[00:01:07](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m07s)

JCB already has in its component area an export component feature, which we extended to automate. It has been  left as a button called 'Backup'. It is the same feature except it can manually be triggered. It can either be triggered by a 'CronJob' or being triggered by Backup button.[00:01:36](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m36s) What the backup feature does, it takes all your components and export them, encrypt them and store them on a local folder, and then emails the key to a trusted email address which you have set up. [00:01:58](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m58s) The components that are in trash will not be part of this Backup. Only components that are published or unpublished or archived, will be in the Backup, everything else will be ignored. Basically when the Backup runs either manually or automated via a 'CronJob', [00:02:26](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m26s) it will take those components, use the specific keys as it would with the exporting of that components, then encrypt and store them in that folder. 

### New Features - Mail Configuration, DKIM, Encryption Settings, CronJob Tabs Added
 
[00:02:40](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m40s)

There are some things that need to be set up for all this to function as expected. First of these are in the options area of JCB. There are some new features. Open that. There is a 'Mail Configuration', 'DKIM' and a 'CronJob' tab added and also this field called API user. 

### API User

[00:03:09](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m09s)

The API user will primarily be used for the ID that is used in the permission structure. When you are in the components area and trigger this feature manually, it uses this current 'Login user', to determine whether the components has been encrypted and backed up, whether he has the permission to do that. [00:03:44](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m44s) As the permission structure of JCB is expanded, you might end up having components, that certain individuals who are in certain groups, may not have access to. There might be components and fields and views that they may have access to or some that may not have access to. We are laying some of the foundation to make sure that there is not some loophole where either by triggering a batch update or an export of components or backup.  [00:04:17](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m17s) They can not extrude certain components which they by default do not have access to. This is just to explain why an API user is still needed. A user is still necessary, which; if it has automated the backup, that this user ID allows him to make the backup. So that means the API user should be a user which has the permission to all the components fields and everything in the JCB component. [00:04:52](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m52s) It is secure because the component gets compiled and stored locally. We might consider adding the option to push the component back up to an FTP server, but that part is not fully functional yet.[00:05:14](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m14s) Proposals have been made to do that, so that the backup should not be on the same system, but that it is secured on another system in case of a collapse. [00:05:41](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m41s) A FTP option will be added as well, which will work similar as your components, when a component is compiled it gets send off to a sale server. That is the same features that we will make use of. 

### CronJob Tab

[00:06:17](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m17s)

In the 'CronJob' tab, is some basic instructions for those who are familiar with CronJobs and if not, Google around, find some tutorials, read up, make sure that you are able to set up a CronJob. [00:06:40](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m40s) There are various ways to trigger this URL. The system currently detects whether your system can run 'curl' request and if not, it will fall back on the 'weget' option. Assuming that JCB is installed in an environment that allows these two functions to work and if not, simply take the URL, and run it in a CronJob in a manner that is applicable to your system. [00:07:16](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m16s)  This URL triggers the backup to start. When the backup is finished, it gives the same message that you will get if you run the backup by clicking 'Backup' (See video). There is a green message that pops up, indicates: 'Yes the backup was done and the email was sent'. [00:07:42](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m42s) Those are the only messages that gets returned on this URL. Currently that response gets thrown away. It may be added to a log, depending on how regularly this 'CronJobs' is running. Currently there is not any date.  [00:08:06](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m06s) It might make sense for us to add a date. In case you run into a firewall, Joomla website has a firewall installed like RS firewall, then it is necessary to adapt the 'curl' request to behave like a real browser. This post on https://stackoverflow.com may be of some help. 

### Cronjob Backup Folder Path

 [00:08:36](https://www.youtube.com/watchv=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m36s) 
 
Currently the 'Cronjob Backup Folder Path' is set here(See video). It currently backups to a local folder. As mentioned previously an FTP option is going to be add here. Joomla does not by default encrypt fields in the Global Configuration of the component. 

### Email (Backup Key)
 
[00:09:13](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m13s) 

Currently it stores it into a local folder, and it Emails the backup key to the email address that have been set in here(See Video). Make sure that email address is secure and that it is safe because the keys are being sent to it. 

### Package Name Placeholders

[00:09:33](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m33s)

Here is a naming structure for your file by default. It adds only up till the day, so it will  make backups all through the day, but overwrite the file every time unless you add an hour, then it will only per hour overwrite it. If a minute is added , it will never overwrite it, because it will be a different minute every time. That is to rename the package and to see how much of the backups you want to keep. 

### Mail Configuration Area

[00:10:13](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m13s)

In the mail configuration area, it may be seen that it is currently set to use the Global Mail Configuration which is the Joomla default.
**NB. Use a very secure method of sending the emails.** Either SMTP overwriting the SMTP settings. If the Global ones are used, then overwrite or insure that the Global Email settings in Joomla is also using SMTP that runs through an SSL, and that it is secure. 

### DKIM
 
[00:10:54](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m54s)

The DKIM is also a added feature which can increase trust and security of your emails. 

### Company Details

[00:11:10](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m10s)

Then there is the Company details, which at this stage is important to add, since it will also become part of the backup package. We will look at that again when we restore a backup to show you where this information comes up. [00:11:28](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m28s) That is some of the settings that first need to be set within the Global Configuration(See video). Once it is set, Company settings, CronJob settings,  Local path, the Email, the Name, and the API user, you can save and close this area and then look at a component to see this feature in action. [00:11:54](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m54s) Since this is a default JCB install, there is only one component; The Demo Component. 

### Set An Export Key

[00:12:10](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m10s)

Usually the Demo Component does not have an encryption key. Open it. It had been set on a previous occasion. Set an Export key in at least one of the components that will be part of the backup. If any one of the components that are being backup have an Export key, it will encrypt all the components with that Export key. If multiple ones have an Export key, it will combine those keys to be used as the encryption key.[00:12:47](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m47s)  It hashes those keys so the actual key is not what is being used. The actual key that is being used is the one that will be emailed to that trusted email address. Save and close the Demo Component. 

### Backup Manually

[00:13:07](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m07s)

Run a manual backup. As explained before it is similar to the CronJob except that it is triggered by using the Backup button. It will indicate: 'The backup has been done successfully'. [00:13:36](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m36s) The owner details was set. If for some reason you forget to set the owner details in the options area, it will show: 'The email with the new key was sent'. To make sure that the backup works, check the folder in which you had set the backup to be placed. Check whether the backup is there, and also check the email address and see if they had received the key.[00:14:06](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m06s)  As expected the backup is in the folder. The backups been done, double click into the backup, and make sure that it has all the expected files. At this stage it looks like it does. If you have a lot of custom files [00:14:38](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m38s) that has been added into the component, there will also be an extra custom folder in the Zip Document and not only in Image one. Test this backup by importing it. But first check if the email has been received . It can be seen that it had send the email as expected, with the corresponding key. Use this key to test the backup. [00:15:08](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m08s) Be sure that it sends the key to a secure Email Address, and that the email that sends the Email from Joomla is using a secure SSL by SMPT. <<<<

### Testing Backup

Now let's test this backup. [00:15:35](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m35s) A backup will only makes sense if we lost our data. I'm going to take the demo component, and throw that in trash. Then go to trash and empty the trash. There is no components. [00:16:10](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m10s) Click on import components. Now we need to browse to the Directory, where that component was backed up. We'll click on the Directory tab. There we have the components path to the backup package. We click on 'Get File'. Now we will take that key that was sent to us via the email, and we will force the update, and will add that key. [00:16:45](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m45s) We'll click continue. 

### Package Owner Details

I just step back for a moment because I realized I didn't explain what you'd seeing here. Like I said before your Package Data of the owneris desplayed here, and the Package Details is being displayed here. If you have more than one component backed up, all of those components will show here on the 'Components Being Imported'. Here you will see the the Package Owner [00:17:17](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m17s) Details, and get the key from this link here(Testing Company). 

I will again do this import. Let's click continue. Wonderful so we have the component back. It's all being restored. That is what the purposes of the backup is, is when something goes wrong [00:17:40](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m40s) you can come back to where it was when the backup was made. We can test with a backup if it is been successfully restored by going to the compiler, and then selecting the component. Clicking on compile. As you can see is been completely successfully built. We can now click on install the demo component, and then we can go to the demo component, and see that everything is working. [00:18:18](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m18s) Adding a new look. There is all the various fields as it usually are available in the demo component. That is automated settings for JCB, and setting them up and you making use of them.
