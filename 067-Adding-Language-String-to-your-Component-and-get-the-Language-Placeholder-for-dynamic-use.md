# ADDING LANGUAGE STRING TO YOUR COMPONENT AND GET THE LANGUAGE PLACEHOLDER FOR DYNAMIC USE

### Quick Tip How To Add String To Your Component 

[00:00:00](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(Click on these time links to see Youtube video)

How to add a language string to your component without a language string being immediately added to the Jtext object function which translates it. Let me demonstrate. With a normal language string, you would use Jtext and add your string in there(See Video). When JCB compiles it, it adds that string to your language file. When your component runs, that string is translated because it has a placeholder in its place. You can then have multiple places where the string is used. It is there and works well. The new feature [00:00:59](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m59s) is mostly used when you are dealing with a class and you are working with an array in the class. If you want to have a class method or rather fields that is an array of strings, but you can not use this [00:01:20](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m20s) in the array of a class value. That is one place but there are many places where you could see this in action. 

### Want The Placeholder To Be Generated

[00:01:32](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m32s)

What you would want to do is you want the placeholder to be generated. You want the string to be added to the language file. But you only want a placeholder as a string to be added to your Script because later in the script, you are going to add it to the Jtext option to translate this placeholder. Often you would run into such a case, well I have. The way we have addressed this with a new name `JustTEXT`. [00:02:16](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m16s) This part looks exactly the same as the `Jtext`.

This almost seems like this is a class but it is not really. It is something that the JCB compiler will pick up. It will convert this, let me show you how it will look when it has been converted. You will see why it makes sense. There are these extra field properties, and it has these keys(listclass, escape, display and validate). I want to use the key to get the string. If we go a little lower in the script, [00:02:49](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m49s) you will see I am looping through that array and the value description. I am only passing it to the Jtext to translate it. That means I want to do this translating later and all I want in this array above is the placeholder string. 

### Looking At The Code

[00:03:11](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m11s)

Let me show you that in the code how it comes out.  In the code you will see the extra field properties. You will see it is simply a string. It took away the bracket if you looked at it the way it was. I am going to paste in the one from the code that you can see what it has done. You can see [00:03:40](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m40s) this is what we added in JCB, and what it did in compilation. It added the placeholder string which we can then use down here in our Jtext to translate it to get the specific translated string. That is a way to get the placeholder and to get the string into your language file. [00:04:09](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m09s) That is just a little tip. I know that it is not very obvious. I hope it will come in handy to those of you who want to add language strings to JCB, but you do not want to have it immediately be part of the Jtext object call. You want to have the actual placeholder available for use dynamically. This is the way you can do that.