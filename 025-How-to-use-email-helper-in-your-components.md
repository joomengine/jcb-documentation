# HOW TO USE EMAIL HELPER IN YOUR COMPONENTS

* ### Example Of Email Helper Class

The Email Helper Class is a class that gets added to Components Helper area and is therefore available on every page, with which Emails can be send. For example:  Take a look at the Helper Class by going to a component that has it included and at 'Helpers'. [00:00:25](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m25s) The filename is usually the component name: 'Email'. As may be seen, it is in the basic abstract class. That takes Joomla's E-mailer, which is 'Jmail' and gets an instance of it, and adds it to mail and then loads in the variables that's required. [00:00:48](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m48s)

### Setting Up Email Helper Class

If this feature is going to be used, the first thing to do when looking at a component (On Component Builder Dashboard) is to open 'Learning Manager'(In Editing the Component area) and go to Libs & Helpers. [00:01:22](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m22s) It may be noticed that the 'add email helpers' has been set to 'on'. It places the Helper class in the component, but is not implemented anywhere else. That means that if 'yes' is clicked, it is still necessary to create fields, that need to get loaded to the config area. 

### Settings - Config Area

[00:01:55](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m55s) In 'Settings' is this 'config' area (Adding Custom Config Fields),  which gives the ability to add configuration options to the components option area. So if this 'config - add' is being clicked, scroll down till that mail configuration and a whole lot of fields may be seen. These fields correspond to the Joomla's default fields. If you would like to create these fields and some info is needed in order to create these fields, like what should their names and content be, then go and look at the Joomla Global Configuration XML and all the settings in that file may be seen. [00:02:39](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m39s) There is DKIM implementation available. 

### In Code Field Names

It will be necessary to look in the code to get these field's names. There is a difference between 'name', 'label' and 'description'. [00:03:13](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m13s)  For instance 'name' is the value that will be used in the code. In the code  for example, that word 'mailer' means that the name of the field is called 'Mailer' and the same applies to the name 'field' etc. These are all the fields that needs to be set.

### Component Global Options - Mail Configuration

In the component there is a 'Options' area, there is a Mail Configuration and a DKIM area. [00:03:45](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m45s) It has the 'mailer' status. It is either set to 'Off', then no emails will go out, or to 'On'. 

### Switch Global Mailer Options

If it is set to 'On' it may be decided whether there is need to override the global variables. The global variables are set in Joomla's components global area. [00:04:10](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m10s) 

### Joomla Global Configuration - Server

If Global Configurations is opened, and then the Server, and then Mail Settings. These are the main or the Global Settings that will be used in any component that does not add these settings in their config. [00:04:40](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m40s)

If those fields had not been created and added to the component, but the button was used in order to add the Helper class to the component, the result will be that it will fall back to these settings in the Joomla default area. These 'Main Settings' are the values that should be overrided.

### Component Builder Email Switch Options

[00:05:08](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m08s) If in some way the component should use other PHP, Send mail or SMTP values than the Global it must be set on the Learning Management System Configuration page in the Mail Configuration area.(See video) That is the function of this area . If Global is used, it will fall back to the Joomla Global. Otherwise it can be overrided on this level and send out as you prefer.  [00:05:38](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m38s) 

### DKIM Settings (Encryption)

The DKIM area is the more advanced area which allows encryption and to authenticate emails that has been send.  This is helpful to show people that receive these emails that it not spam. Because of the advanced nature of this some research on this will be helpful. These are the values that usually would be required: Private key, Public key etc.(see video). If this 'Enable DKIM' is set to 'No', it will not be used. Please ensure to add the values when it is set to 'Yes', otherwise it still will not be used. [00:06:25](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m25s) So that values need to be created as  Component Builder will not do it.

### Default Global In Code

On the code level(See video), it gets the 'mailer' function from the configuration and checks whether it is Global. If it is, then it implements Joomla's values. If it's not global, it implements your components values. [00:07:38](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m38s)  Read through the code, the most important area is this 'send' area, there the various options in the signature to send out mail may be observed. [00:08:04](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m04s) It is able to send large quantities of mail but nonetheless your servers limitations should be considered. To avoid spams to be send, this values has not been overrided. The Joomla default Helper 'jmailer' is simply been used which has been extended from another class.(See video) [00:08:35](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m35s). 
More information about the 'jmailer' Class may be found at Joomla.

### DKIM Values In Code

These(see video) are the DKIM values that would be needed in the component to be able to use the DKIM encryption. Do some research on this and check how this function implements these features. It gets added to the '$mailer' and most of the work is done in the '$mailer'. [00:09:05](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m05s) It adds the data to the mailer and the mailer takes care of the rest and it is send out. 

### Error Checking For Emails In Code

If for instance an error occurres, then it verifies whether the component Helper Class, (this file 'learningmanagerhelper'). has a 'storemessage' variable or method. [00:09:31](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m31s) It can be seen that there is the 'storemessage' method in the Helper Class. This is a custom method that had been written by VDM. It may be written anywhere, but the signature should be the same. [00:10:00](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m00s) These(See video) 'learningmanager' areas is dynamically updated to your component. It uses the component name 'learningmanager' and the component name 'learningmanager'. But this 'storemessage' cannot be changed, but it takes the 'send email', the 'recipient', the 'subject', the 'body', the 'text only', the 'mode' and indicates that it is 'email'. So there may be  different types, and looking at the method, the type can be anything. [00:10:30](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m30s) Different things need to be done on the various types. If the SMS didn't fail, the message needs to be stored. This kind of feature isn't only used when something didn't work, but also when it worked. If it had been send, it will be stored. [00:10:57](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m57s) So it's a way to store the message, so that the users, if they login, can see messages sent to them. That is the function of the Store Message. This Custom Method can be updated and changed, (pause the video), copy it. If you had written it just make sure that that part 'storemessage' is the same. [00:11:35](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m35s)  That is implementing the Learning Manager Emailer in your component.

### Implemented Example

Here follows a example of how it is implemented at least in one area. For instance here is this component, Job Tracking System. It has that function: Add Email Helper. Set it to 'On'.The view(Admin View) in which the email method is used, is the 'Job Order' view. In this case the client needs to be emailed when a job order had been created. [00:12:21](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m21s) 

This is how it is implemented.(See video) Here is the Job Order. When Email is selected it may be updated to any preferred email. like for example: 'testing@vdm.io'. [00:12:45](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m45s)  Once the email has been sent, it will be confirmed in the top right. [00:13:11](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m11s)It is this button that sends the document to the client.<<<<<<<<<<<<<<<<<<<<<<<<<<<<<,




### Above Example In Code

So we will go to the code and I'll show you how I do it and [00:13:45](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m45s) I'll give you some pointers. I won't go into detail about how that is done. Let's go to the code. We are in the job order, first thing here is some JavaScript. There's the send email function and gets a set of values. And then it gives it over to the send email server function, which sends it as a [00:14:20](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m20s) json request to the server. The send email is the task and when it gets a response that's when you get the notification. That's simply the JavaScript of it. 
If we go to php, in previous tutorials we explain how to use the Ajax class. 

I'm going to touched on it briefly. [00:14:47](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m47s) You have your input here(ajax input). This is where you set up your controller. So you'll see in your controller there is send email class what was defined in this field here(see video). And you see that there is three variables, and they [00:15:12](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m12s) should be filtered in this way and they are pass over to these methods and you should be login user. So if you look at the code, again this is the task(sendEmail), down here it triggers the task. It checks for those values and then passes it over to this method(sendmail) which is in the model. We go to models, Ajax. Here is the the model(see video). Let's just scroll down to the sendemail. Here is the sendemail and this again [00:15:47](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m47s) is a custom script. So if I was to go back here, I close this, you'd see there's the ajax method, there is a lot, I mean look at that, you can see that scroll down way down is a lot of other custom methods. This is another custom method I've wrote, it's called sendemail, it gets the mail, the HTML, the type. It it does the necessary cleansing and whatever. [00:16:14](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m14s) 

Over here(see video) we're calling the email helper. We using the send method, we passing the valuables, and set the result in here. If the results is true, [00:16:38](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m38s) we will let the user know, otherwise we give him the error. I'm also using this email body to help me build the email because I want to make sure that it got all the necessary HTML and stuff. You can pause the video and type that out if you like. This is the email body that I usually use. It simply adds the subject to the email, [00:17:15](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m15s) the necessary places as well as the body in the necessary place that it gets send in a way that's more appropriate. That all is happening right here. That is what I'm passing in here. A custom method which gets the data from the ajax and then sends it off. [00:17:43](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m43s) That's a quick tutorial on how to implement sending emails through your component, using the email helper class. The email helper class is available on GitHub in the component builder. If you feel that our implementation lacks some professional help then please do make a commit to quest or send me an email. We'll gladly update an improved this class, although I think we followed all the necessary standard and requirements to make it useful to everyone. 
