# TRANSLATION MANAGER IN JCB EXPLAINED

[00:00:00](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00ms)

JCB has again been expanded to include a language translation feature. One of our contributors had extended the code base for this and we are collaborating to insure that it remains stable. Those that have been following the process on GitHub, will know how much time and effort had been put into this. So this is a quick explanation of how this will work. 

### JCB Builds English File For You

[00:00:49](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m49s)

ACB (Advanced Component Builder) or JCB (Joomla Component Builder) is a English component and it builds the English language file for you. Everywhere in the fields, when a field is created, there are areas in the field that indicates that it is 'translatable' or 'not translatable'. 

### Placeholder - Jtext - English Language String

[00:01:25](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m25s)

If those values are entered in the XML field definition area, JCB on the fly will take this description('enter a acronym') for example and will convert it into a language placeholder and will add it to the  British language file. This is all being done automatically for every area of the JCB compiler. Even in templates and views that is now the front end.

 [00:01:56](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m56s) If   site views, templates and layouts are created, these 'Jtext' placeholders with the actual English language string in it can be added. The passer will automatically grab that text and add it to the language file. [00:02:25](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m25s) So currently JCB is building a complete English Language File for you but is only able to translate it. Presently it can not add multiple other languages.  

### Adding Of Other Languages

[00:02:43](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m43s)
 
There had been a request that if it were possible, to translate this language strings, and then when JCB compiles the component, it will automatically add these other languages. 
 It had been suggested that an area should be added where as many languages as preferred can be created in accordance with the conventions.[00:03:10](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m10s) 

Your language tags need to be in accordance with the correct prefixes used in Joomla. Maybe a link can be added on this page at some point just to take you somewhere, where you can find all the information to use the correct tagging for your language file. Here('Name'), you could add the language name, and may create as many languages as you prefer. [00:03:39](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m39s) When a component is compiled, JCB, as explained, grabs all the strings from everywhere, and adds them to the British English translation file. 

### Code - Language String

[00:03:50](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m50s)

In the code the following takes place. In the 'a_Get.php' class, is a function called 'setLangStrings'.  It gets the content from wherever JCB is handing it and it parses it to see whether it has either this 'sprintf' language string or that one 'Jtext'. It does some gymnastics to grab all the actual strings into an array. Then it parses this array. Once it has it, it converts it to a language string, and adds it back into the content and returns the content.[00:04:34](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m34s)  With this object array, it is adding the language string, and the language key to the 'langContent' array. So that is a first thing, this 'langContent' array which is all over the place and it just gets bulkier. The 'lang' is basically the target. [00:05:04](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m04s) It is the area which this 'lang' strings belong to, either the Site or the Site system or the Admin or the Admin system area. There are also such a thing as both while JCB compiles. Some strings, it knows must go to both. This 'keyLang' is the actual language string, the capitalized string, which is generated up here(see video). [00:05:34](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m34s) I trimmed and put it in its place. This array gets placed into the files at a certain point. That point is very much at the very end of the compilation when everything is being done. Now two strings are going to be added to the files. 

### Adding Strings To The Files

[00:06:04](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m04s)

First a function is called 'setLangAdmin'/ 'setLangSys' this is in the Interpreter. These methods may be seen here, 'setLangSite', here is 'setLangAdmin' and a bunch of strings that are always being added by default and then also all the other strings that have been built which then  moves them over to a string called language, the British English, and it is for the Admin area.[00:06:37](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m37s) So it does for all the various areas. In the infusion class, it brings it together. The values of this strings are grabbed and added to the value array.  The old multi language implementation running down from line 1097. 

### Multi Language String Implementation

[00:07:09](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m09s)

What is the function of the multi language string implementation? It searches the database to see whether there is such a English language string in the database and whether there has been any translations made for it. So it does not use the placeholders since the placeholders are so ambiguous between various components and a attempt had been made to share strings among components to prevent a overpopulated database. [00:07:43](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m43s) Currently when   a component gets compiled it gathers its English strings as explained, it checks the database whether these English strings already exist in the database, and if they do, it then checks whether they have translations already linked to them. If they do, then it starts grabbing that translation strings and adds them to this 'Language object' array, also by tag and by area and here(see video) this array is parsed. By this time all the languages are already in place and it is now possible to put them into the component.[00:08:22](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m22s) It is these functions; 'getMultipleLangStrings',  'setLangPlaceholders', 'purgeLanguageStrings' that does the work. So these are all found in the 'a_Get.php' class which is open source. By the point we get to this line 1109, we already have all the language strings in their various areas and various languages. 

### Adding Language Back To Component

[00:09:13](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m13s)

Now it can be added back into the component. That is what this(See video) part is doing. [00:09:19](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m19s) Return to the user interface to see this in action. I am going to compile a component, any component, for instance this(See video) document manager. While compiling it, keep in mind that it will be running through, and grabbing all the English strings, then eventually will check this Language translation table, whether those strings exist. If they do, they have been translated. It compiles it, and most of the work is done for you. 

### How Purging Works

[00:10:05](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m05s)

The question has been asked: What if some fields is changed , name or some description, and that other description, that old English string is no longer being used ? Well at the moment it will be purged. Now the purging works as follow. [00:10:29](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m29s) When it discovers that a string is no longer being used by a component, (it can be seen in the code) it asks the question: Is another component still using it? If another component is using it, it simply removes the current component from the string  and then it goes on, it does not remove it. [00:11:00](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m00s) If no other component is using it, for instance; no other component is any longer linked to the string, then it checks whether there has been any work done in it? Has there been translation done? It is quite a huge job to do translation, and should preferably not deleted. 

* ### Move Strings From Published To Archived State

[00:11:22](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m22s) 

So this is what needs to be done: As the string is archived, it gets moved from the published state to the archived state. In the archives may be seen all the strings that no longer are actively linked to a component, but has translations in it. If it does not have any translation, it is not linked to a component and it does not have translation, then the string may be removed from the database. [00:11:48](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m48s)(See video) These are the two functions to remove the string completely. It is like it never was there in the first place. That is how the purge works at the moment. It only purges that which is no longer linked, neither has any work done in it. 

### New Translation Tab

[00:12:14](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m14s)

In the document manager, in component in JCB, you will see there is a new tab called 'Translation' and in this tab appears all the English strings and shows whether any work has been done in it . It will indicate 'no translation' when no work has been done to it, and in how many components it has been used. Currently most of these strings are used in quite a few other components. From here you can click on any of these strings and it will give the list of all the components where it has been used. [00:12:57](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m57s) It displays the string but the string cannot be editted . Translations may be added by selecting the language and as many as preferred may be added to the string. Then in every one of these components, this translation will be active. 

### Two Ways To Get To The String

* ### Via The Component

[00:13:21](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m21s)

There are two ways to get to the strings. The one is like I showed you via the component. We are planning to add a button whereby you can import these and export these strings quite easily so that you could give them to other team members who can make translations, and give it back to you and then you can import it, and then it gets linked automatically. That is still under development. 

* ### Go To Language Translations

[00:14:03](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m03s) 

The other way to get to these translations is to go to Language Translations, where all the component strings are together. This could become a database with over 8000 lines but it works quite well. I already have a lot of components mapped. The ones that are displayed are usually the ones that are active. I got quite a few in archive as well. [00:14:36](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m36s) I have tested this against 8 or 9 components at the same time, sharing strings among each other. I expect this to become a very powerful tool as soon as we are able to speed up the translation method. There has been suggestions that we add this feature to a community area where you can push English strings, and can pull already translated strings from it. [00:15:15](https://www.youtube.com/watch?v=zzAcVkn_cWU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m15s) This is a great idea but how to manage it so that the system does not get abused, are still under the debate. Go to GitHub and open a issue if you have any suggestions.
