# HOW TO ENSURE THAT A FIELD IS NOT ESCAPED WHEN ADDED TO LIST VIEWS

[00:00:00](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

* ### Example Extra styling In Fields

Occationally there is a need to add extra styling to a List View [00:00:06](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m06s) The problem though is that by default all of these field values are being escaped. 

How is this kind of styling added to a field?

### Settings - Editing View - PHP Area

[00:00:31](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m31s)

In the Job Order Admin View area, in PHP, there is a method called 'Add PHP(getitems Method - before translation fix & decryption)'. This happens before the translation fix or the decryption of any field. This is not the ideal place. 

### Settings Values In The Code - Add PHP Area

[00:00:58](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m58s)

Usually this would be added after that was done, but in this case it was done before. [00:01:15](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m15s) A value is set up when 'danger' or 'warning' need to be applied, simply by using the getDate and modifying it by the danger time and the warning time from the job tracking configuration values. This is a configuration field that has been added to the component and it's names are: 'warning time' and 'danger time' where the default is 3 weeks, 1 week. This is the dates that is going to be used.

### Looping Through Data Till Target Found - Adding Styling

[00:01:44](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m44s)

Look through the data and identify data that is part of the target. Add this value to it, that then in turn turns this red(See video). [00:02:19](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m19s) Check the dates and depending on its values, add HTML value to the date, and use a custom method in a Helper Class called 'fancyDate', where the default sequel date is converted to a more appropriate date, 2nd of April etc.  [00:02:39](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m39s) The problem is though, if this is done and the component is compiled and items added , then it escapes those values and prints it around the value(see video). [00:02:59](https://www.youtu[00:00:39](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m39s)be.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m59s) Obviously that is not the desired outcome. There is a way to prevent it. The value here is to create 'date', as well as the 'job status'.  

### Field Adding Escape=False To Code to Prevent Escape

[00:03:27](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m27s)

In the back end of the component, 'Job order', the area called 'Fields' can be opened. Scroll down to 'Job status'. [00:04:09](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m09s) Scroll further down and at the bottom it can be seen that this line 'escape= "false"' had been added. So you would simply add this line: 'escape= "false"' [00:04:37](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m37s) In the structure of the component where that field is loaded, Component Builder as it compiles, will command the escape method not to escape it, and consequently the HTML will be displayed instead of it being printed out. [00:05:15](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m15s) This has been a quick demonstration of how to make use of the not escape method. 