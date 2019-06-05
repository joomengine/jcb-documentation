# TEMPLATE SETUP

**Creating Templates**

In the previous tutorial we where looking at setting up of templates and layout to a site view. Now inside of the side view we see that we are loading preacherpanel, preachersmall, preacherbox. Let's go look at how to create those templates. I'll go to templates, [00:00:27](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m27s) here they are already created. 

**New - Copying Templates**

You can click on new to start with a new template. You could also copy an old one by selecting the template you would like to copy. Click on batch and then there is a copy feature here and click process and it'll copy it for you. [00:00:49](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m49s) Here I have preacher panel open. In preacher panel it's the same concept it's an HTML area. If I want to use php I need to go into the php. Then I can go out again. I can also add this text placeholders, which helps us to ensure the text itself is translatable. You can just do your normal English text like that 'sermon count', and [00:01:16](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m16s)  'total downloads'. 

**Language String**

Component Builder will add these strings to the language file for you. You don't need to be concerned. At this stage it only does your British English language file. If you need to add more languages, you need to look up the documentation of adding languages to a third-party extension, [00:01:44](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m44s) and do that same implementation. Here(Layouts Code Snippets) we see that you can add layouts to this template by using any of the snippets to this template.  You can add other templates to it. You can use templates inside of templates. You could have use layouts as well so more or less the same behavior as in site view. 

**Adding Custom Script/Code to Template**

You also have your snippet box, [00:02:15](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m15s) which you can make use of adding script quickly to your page. We see that the script that I just looked at in the preacher panel, if we go to the code, preacher panel, it is exactly the same script that you seeing here(code).  [00:02:46](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m46s) 

**Adding JavaScript To Template**

There are a few exciting points here. One of them is a side note in your details tab, in the template area here at the bottom. You can add JavaScript with your normal script tags. You can just add your JavaScript in there.  [00:03:13](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m13s) It will work and be loaded into the page through this little snippet. That's a nice thing to know. You still have access as I said before to all the global 'this' field values, like you can see there. [00:03:35](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m35s) You can access those quite easily. That is how to set up a template, is the same kind of conventions as setting up a site view. Except that this is not the main view, it is a template used somewhere in a main view through adding this code snippet with Joomla class get template method. [00:04:02](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m02s) Then basically load template as the method that is being used with that name. Then it adds it to your component site view as well as adds the code to it and everything else. That is a template. next up we will look at a layout. [00:04:29](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m29s) It really get excited there.
