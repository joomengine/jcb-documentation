# HOW TO USE EMAIL HELPER IN YOUR COMPONENTS

* ### Example Of Email Helper Class

[00:00:00](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

The Email Helper Class is a class added to Components Helper area and, therefore, available on every page with which Emails can be sent. For example: Take a look at the Helper Class by going to a component that has it included and at 'Helpers'. [00:00:25](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m25s) The filename is usually the component name: 'Email'. As may be seen, it is in the basic abstract class. It takes Joomla's E-mailer, 'Jmail', and gets an instance of it, adds it to mail, and then loads in the variables that are required. [00:00:48](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m48s)

### Setting Up Email Helper Class

[00:01:02](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m02s)

If this feature is going to be used, the first thing to do when looking at a component on Component Builder Dashboard is to open 'Learning Manager' in Editing the Component area. Go to Libs & Helpers. [00:01:22](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m22s) The 'add email helpers' has been set to 'on'. It places the Helper class in the component but is not implemented anywhere else. So if 'yes' is clicked, it is still necessary to create fields that have to be loaded to the config area.

### Settings - Config Area

[00:01:47](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m47s)

In 'Settings' this 'config' area, Adding Custom Config Fields, is found. It gives the ability to add configuration options to the components option area. [00:01:55](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m55s) Click 'config - add', scroll down until the mail configuration and a whole lot of fields may be seen. These fields correspond to the Joomla's default fields. If you want to create these fields, some info is needed in order to create these fields. For example, what their names and content should be. Go and look at the Joomla Global Configuration XML and all the settings in that file may be seen. [00:02:39](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m39s) DKIM implementation is available there.

### In Code Field Names

[00:02:45](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m45s)

It will be necessary to look in the code to get these field's names. There is a difference between 'name', 'label', and 'description'. [00:03:13](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m13s)  For instance 'name' is the value that will be used in the code. In the code, for example, the word 'mailer' means that the name of the field is called 'Mailer'. The same applies to the name 'field', etc. These are the fields that must be set.

### Component Global Options - Mail Configuration

[00:03:35](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m35s)

In the component, there is an 'Options' area, a Mail Configuration, and a DKIM area. [00:03:45](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m45s) It has the 'mailer' status. It is either set to 'Off', so that no emails will go out, or to 'On'.

### Switch Global Mailer Options

[00:03:55](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m55s)

If it is set to 'On' it may be decided whether there is a need to override the global variables. The global variables are set in Joomla's components global area.

### Joomla Global Configuration - Server

[00:04:10](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m10s) 

Open Global Configurations, the Server, and the Mail Settings. These the main or the Global Settings is found that will be used in any component that does not add these settings in their config. [00:04:40](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m40s)

If those fields had not been created and added to the component, but the button used in order to add the Helper class to the component, it will fall back to these settings in the Joomla default area. These 'Main Settings' are the values that should be overridden.

### Component Builder Email Switch Options

[00:05:08](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m08s)

If, in some way, the component should use other PHP, send mail or SMTP values, then the Global must be set on the Learning Management System Configuration page in the Mail Configuration area. (See video.) That is the function of this area. If Global is used, it will fall back to the Joomla Global. Otherwise, it can be overridden on this level and sent out as you prefer.

### DKIM Settings (Encryption)

[00:05:40](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m40s)

The DKIM area is the more advanced area which allows encryption and authenticates emails that have been sent.  This is helpful showing people receiving these emails that it is not spam. Because of the advanced nature of this, some research on this will be helpful. These are the values that usually would be required: Private key, Public key, etc. (See video.) If this 'Enable DKIM' is set to 'No', it will not be used. Please ensure that the values when it is set to 'Yes' is added, otherwise, it still will not be used. [00:06:25](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m25s) So these values have to be created since Component Builder will not do it.

### Default Global In Code

[00:07:15](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m15s)

On the code level, it gets the 'mailer' function from the configuration and checks whether it is Global. (See video.) If it is, it implements Joomla's values. If it's not global, it implements your component's values. [00:07:38](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m38s)  Read through the code. The most important area is this 'send' area where the various options in the signature to send out mail may be observed. [00:08:04](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m04s) It is able to send large quantities of mail but nonetheless your servers limitations should be considered. To avoid spams to be sent, these values have not been overridden. The Joomla default Helper 'jmailer' has been used which has been extended from another class. (See video.) [00:08:35](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m35s) More information about the 'jmailer' Class may be found at Joomla.

### DKIM Values In Code

[00:08:40](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m40s)

These are the DKIM values that would be needed in the component to be able to use the DKIM encryption. (See video.) Do some research on this and check how this function implements these features. It gets added to the '$mailer' and most of the work is done in the '$mailer'. [00:09:05](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m05s) It adds the data to the mailer and the mailer takes care of the rest and it is sent out.

### Error Checking For Emails In Code

[00:09:12](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m12s)

If, for instance, an error occurred, it verifies whether the component Helper Class (this file 'learningmanagerhelper') has a 'storemessage' variable or method. [00:09:31](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m31s) It can be seen that the 'storemessage' method is in the Helper Class. I wrote this custom method. It may be written anywhere, but the signature should be the same. [00:10:00](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m00s) These 'learningmanager' areas are dynamically updated to your component. (See video.) It uses the component name 'learningmanager' and the component name 'learningmanager'. But 'storemessage' cannot be changed, but takes the 'send email', the 'recipient', the 'subject', the 'body', the 'text only', the 'mode', and indicates that it is 'email'. There may be different types, and, looking at the method, the type could be anything. [00:10:30](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m30s) Different things have to be done on the various types. If the SMS didn't fail, the message must be stored. This kind of feature isn't only used when something didn't work, but also when it did work. If it had been sent, it will be stored. [00:10:57](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m57s) It's a way to store the message so that the users, if they login, can see messages sent to them. That is the function of the Store Message. Custom Method can be updated and changed. (Pause the video, copy it.) If you had written it, make sure that the part, 'storemessage', is the same. [00:11:35](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m35s) That is implementing the Learning Manager Emailer in your component.

### Implemented Example

[00:11:39](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m39s)

Here follows an example of how it is implemented in at least one area. Here is this component, Job Tracking System. It has the function of Add Email Helper. Set it to 'On'. The Admin View in which the email method is used is the 'Job Order' view. In this case, the client must be emailed when a job order had been created. [00:12:21](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m21s) 

This is how it is implemented. (See video.) Here is the Job Order. When Email is selected it may be updated to any preferred email. For example, 'testing@vdm.io'. [00:12:45](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m45s) Once the email has been sent, it will be confirmed in the top right. [00:13:11](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m11s) It is this button that sends the document to the client.

### Above Example In Code

[00:13:40](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m40s)

Go to the code. (Editing the Admin View.) In the 'Job Order' is a JavaScript area. The Send Email function may be seen. It collects a set of values and transfers it to the 'sendEmail server' function, which sends it as a 'json' request to the server. [00:14:20](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m20s) The 'sendEmail' is the 'task'. When it gets a response, it gives the notification.
  
There is a PHP area in the 'Job Order'. How to use the Ajax class had been explained in previous tutorials but we will make a brief mention of it again. [00:14:47](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m47s) Here is the input where the controller has to be set up. In the controller, there is 'sendEmail' class defined in this field. (See video.) [00:15:12](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m12s) There are three variables. They should be filtered, transferred to these methods, and logged in 'User' by selecting 'Yes'. Looking at the code, this is the task: 'sendEmail'. It triggers the task and checks for those values, then transfers it to this method, 'sendMail', which is in the model. Go to Models and Ajax. Scroll down to the 'sendEmail'. [00:15:47](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m47s) This is a Custom Script. In closing this, the Ajax method can be seen. This is another Custom method which I wrote. It's called sendEmail. It gets the 'mail', the 'HTML', and the 'type'. It does the necessary cleansing, etc. [00:16:14](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m14s) The Email Helper is requested. Then the 'Send' method is used, the variables are transferred, then set the 'result'. If the result is 'true', the user is notified, otherwise, he receives the 'error'. [00:16:38](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m38s)

This email body is of great help to build the email. It ensures that it contains the necessary HTML, etc.[00:17:15](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m15s) The HTML and subject can be passed to it. It adds the subject to the email and the necessary places as well as the body($body[]_$html) and is sent in an appropriate way. A custom method is passed which gets the data from the Ajax and then sends it. [00:17:43](https://www.youtube.com/watch?v=tp6mMUTOF2Y&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m43s) That's the tutorial on how to implement sending emails through your component, using the Email Helper Class. The Email Helper Class is available on GitHub in the Component Builder.