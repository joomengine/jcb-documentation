# HOW TO SETUP A STORE MESSAGE METHOD ALONGSIDE THE EMAIL HELPER CLASS

[00:00:00](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

* ### Example In Code
In a previous tutorial on the Email Helper, mention had been made of storing messages or emails once they had been sent. [00:00:24](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m24s) At this stage it is important to know that the Email Helper Class is added to the Helper folder of the component's back end. It's usually called the component's name, 'Jobtracking', and 'Email', the Email Helper class. To use it in the Custom Script three brackets may be used, '[[[component]]]email'. Send. [00:00:59](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m59s) That is how to construct script.

### Code Snippet In Method

[00:01:17](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m17s) 

At the bottom of this class, in the 'Send' method, there is a snippet. Insignificant as it may seem, it is beneficial; the result of the email that was sent is placed in 'sendEmail' and the result is transferred to the method as well. [00:01:47](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m47s) It does a search in the Helper class (which is usually a component name: 'Helper', which is the Helper Class) to a certain whether this method exists in that class.

This method will not exist unless it is manually written in the component area. The area where this method should be written is in the component (in the Component Builder Dashboard) in an area called Admin Helper.

### Adding Code To Admin Helper Area

[00:02:19](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m19s)

Open a component and go to Libs & Helpers. Scroll down. 'Add PHP(admin_helper)' may be seen and in which a function called 'storemessage' is where the component may be edited. [00:02:47](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m47s) This 'Storemessage' has a signature that exists of values that are transferred to the method.

It also has a signature in the Email Helper Class. [00:03:19](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m19s) Wherever it gives this '=null' with a value, it is the default value. If a value is not added to this position, there are one, two, three, four, five, positions, then it will default to '=null'. [00:03:51](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m51s) From there all the values receive the value '=null'. It is only necessary to add the first four values. Those values are all used in this method. (See video.) [00:04:17](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m17s) This script, "if(method_exists('Jobtracking Helper','storeMessage'))", asks whether the method had been created. If not, it simply skips it and returns the value of '$sendmail'. [00:04:52](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m52s) If it has been created, it will pass these variables corresponding to the signature. In that method, in the Helper Class (PHP), the necessary checks and balances must be done. Since the email address is known, a search may be done with the 'getVar' in the User Class. The recipient must equal 'email' and return the 'id'. [00:05:09](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m09s) That is how the 'getVar' operates. Having the user ID, the number can be verified and set to the message as 'User'. That is then set as the Email.

Now the message may be stored in any table and more exceptional tasks may be performed than only storing the message. This is the method by which it can be done. (See video.) [00:05:38](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m38s) 'Storemessage' is the method with which more custom scripting on top of the email integration can be done.