# EASY TRANSLATION VIA EXCEL


### New Implementation Added To JCB To Do Translation Via Excel Spreadsheet

[00:00:00](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on this time links to see Youtube video_)

I"d like to give you a quick overview of the new implementation that we've added to JCB that allows you to do translation via a [00:00:19](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m19s) excel spreadsheet. It is to make it easy for you to build your component, extract your language strings and give it to someone else. Have them do the translation in whichever language you like. Have them give the spreadsheet back to you and import it into JCB without the necessity of struggling with INI files any of that. [00:00:47](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m47s) 

### Need To Know - JCB Doesn't Work With Placeholders - Works Directly With English String

[00:00:47](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m47s)

That was what we wanted to achieve. The other thing that you need to know Is that JCB Doesn't really work with placeholders when it comes to these translation strings. It works directly with the English String and the reason we did that, is because the placeholders which in the INI file is the... [00:01:13](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m13s) Let me just show you quickly. If you look at these for example: BACK. This English word might be ended up being used in multiple views, the same English word, but with a different placeholder. [00:01:37](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m37s) What we did instead as we said to ourselves to ensure that you always translate this specific English string only once, we will only add the string and wherever it reoccurs, we will replace it. The string itself. This should be an advantage. I can understand that you might want to have it differently. But this is how we've gone about doing this. 

### 1. Need To Translate Create New Once

[00:02:06](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m06s)

When you think about Create New, Create New is used in many places over in relation to these placeholders. But you only need to translate Create New once. We will add it. The compiler will add it correctly in every other place where it belongs. [00:02:32](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m32s) That's the first thing you need to keep in mind. 

### 2. Translate Strings: Back, Cancel or Close Once - It is Used In Many Components

The second thing which is almost as important, is that you often have strings that are across multiple components. The string 'back' for example again or 'cancel' or 'close'. It is not only used in one component is used in many components. And so we also said to Ourselves we want to still just translate close once. [00:03:00](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m00s) Then in every other component where it's used, it will automatically be used. When we go to JCB, if you have a fresh install of JCB, and you scroll down and your open Language Translations, you will see that there is no values there. Same as if you opened Languages there's also no values there. 

### JCB Populate Dynamically The Language Translation, English Strings - Where Does It Get Them?

[00:03:26](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h30m26s)

If you want to have JCB populate the translation, the English strings. Where does it get them? It gets them from your fields and from your site views, [00:03:38](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m38s) and from any other place, either your admin view, or any other place where you use Translation strings. Then it populates dynamically the Language Translation. You don't ever need to click New to create any, it creates it for you. 

### The Way To Populate The Language Translation

[00:03:59](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m59s)

The way to do that if you would go to the compiler [00:04:04](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m04s) You select the component that you would like to compile. You click compile and you need to do that only once. You can just clear that out again. You don't need to use it. If we go back to Language Translations, suddenly there's a whole bunch of strings, and it also tells you that it hasn't been translated and all. We got almost 249 strings. Like I said close will only be shown up once. [00:04:37](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m37s) It is so with every other string. If we then open Demo, you will see that you cannot edit the English string. We've had request that people would like to edit the string. It doesn't really make sense because if the string is being used in a field, how would we be able to know that their relationship needs to change? [00:05:06](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m06s) For example if you update a string, JCB needs to know in that field it needs to update the label. There's no way for us to determine that. You'd change the string and it won't be useful. Because JCB on compilation will detect that this string doesn't exist, and it will just create it again. 

### The Way To Change A String - Where it was Created - Fields, Site View, Admin View 

[00:05:34](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m34s)

The way that you would change a string which is found, is you need to go and change it in either the Fields where it was created or in Site View or in Admin View. In this case we know that this word Demo is the components name.
 
* Example Change Demo String

If you want to change that Demo string, for example, I'll quickly demonstrate that. I'm going to change Demo to Demoo. Save and close. [00:06:14](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m14s) I'll compile it again and cleared out and then go back to our Language Translation. You will see the Demo is gone, because Demo is no longer being used anywhere, in no other component either so the system will automatically remove it. If you go to the end of the string, you will see the new ones have been added. That's how you would [00:06:48](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m48s) change a English string, is you'd go back to where you set it, and then from there have it changed. I'm going to changed it back. Compile it again. Clear it out again. Go back to Language Translations. You will see that it removed the other one and it added the correct one back. 

### Allow Language To Be Set Dynamically - Create Or Use As You Like

[00:07:23](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m23s)

I would like to translate only this one Demo string. If I want to do that  you will see that there's no Language available. We decided to allow the Languages to be set dynamically meaning that you would manually create them and use them as you like. There is an area called Languages. You'd click New, then you'd give the Language Name and its Tag. The Language Tag, we've given you an example but if you do not know how this should look, there are ways for you to find out. 

### Joomla Translation Packs

[00:07:57](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m57s)

One of the easiest ways is to go to Joomla's Translation area. If you go to https://community.joomla.org/translations.html. I would say select the one that's the newest(Joomla 3.x Translation Packs). You'll see there's a whole bunch of languages. Clicking on any of these will take you down to that language. This is (af-ZA) [00:08:24](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m24s) the little tag that you would be looking for. If you want to do for example Dutch, then this (nl-NL) is the Tag that you would use. You would use the Dutch as the Name, and then (nl-NL) as the Tag. I'm going to set up for example, I'm going to setup Afrikaans, it is my native language. [00:08:54](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m54s) I'm going to use Afrikaans as the language we want to create. Then (af-ZA) is the Tag. You can create any of the languages you want to use. We might at some point add a few major languages here and ship it like that, but you could just create a language. You cannot create a translation for that language, unless you've done this. You must first create the language. [00:09:28](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m28s) It is just the way it works.

### Focus On Translation String Area

[00:09:31](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m31s)

We can go back and let's take a string that would look different in Afrikaans. Let's take Author. If there's more components which the word Author is used in, it'll all be linked in here and it all be done automatically. You wouldn't need to do any of that. You will only need to focus on this Translation String area. Author in Afrikaans is skrywer or outeur [00:10:11](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m11s) We will use the outeur which is more correct. Then you will select the Language (Afrikaans) for which that string belongs. Then save and close. From now on in any component where the word author is used, if the Afrikaans translation with relation to the other strings is enough, [00:10:35](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m35s) it'll dynamically add this language to the component and you would not need to translate it again. This is all been the way it's been working up till now. None of this is new. 

### New Area - Export And Import Strings From Spreadsheet - Dynamically Been Added

[00:10:51](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m51s)

The area that is new, is that you can export these strings to a spreadsheet, and then you can import them [00:11:04](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m04s) from the spreadsheet and it will dynamically be added. I'm going to select a few strings. You don't need to select any of the already translated strings, but if you do, it will also be used if it doesn't really matter. I'm just going to select a few. Click export data. This will create a Excel Spreadsheet, [00:11:32](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m32s) which you can then save. I have open the spreadsheet and you will see that it has a bunch of IDs, then it has English. It got the the tag of the language, and it got the value that we already set. I'm going to set the value for these others in the spreadsheet. You got your Language [00:12:00](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m00s) file back from your translators. They  translated it to this column. You can have multiple language, every language will have its own column. 

### Important - Top Header Is Language Tag/Langauge Is Created And Published

[00:12:13](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m13s)

All you need to ensure that this top header is the language tag. That's really what's important and that this language is created and published in your system. Do not let them change the English string. [00:12:29](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m29s) When you import this file the system will look for the ID and the string, to identify that this value exists. If it doesn't exist it will simply ignore it. If you change author, even though the ID remains, the same, it will not find it and it will simply ignore this line. 

### Demonstration 

[00:12:51](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m51s)

In the way I'll demonstrate this is, I'm just going to change Back to having two k's. Save this document [00:13:00](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m00s) and let's go back and import it. The import is simple, we just click on Import Data. Then we select the file from our system, click Upload File and it should dynamically mapped the columns in your spreadsheet to the table columns. You would have your language strings if you got multiple language. It should automatically mapped in. If you are having multiple languages and you only want to import for the one language, [00:13:35](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m35s) then all you need do is, add this Ignore This Column next to the language you do not want to import. Then you click continue. You will now see that it has added translations except for back. At first I didn't add these so I had to quickly go and add a little fixed to the import. I didn't realize that [00:14:06](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m06s) at the moment it would stop at the first failure and not import further. But I've just fix that and should within the next update this should be resolved. 

The point is once you've imported it, you'll see that it is added the translations to those [00:14:27](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m27s) Strings and it's also mapped it to the correct language. But back was not imported because the English string didn't  correspond. If we go back to our spreadsheet and fix this little error, and make a little tweak to one of the other strings, just for example sake, and then go back to importing this file after saving it of course, Save. [00:15:02](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m02s)  Again Import Data, Browse. You'll see that back is been done. The other one that we also played with was disclosing new. We added the double t there. You are able to export this language strings, translate them in a spreadsheet and easily import that spreadsheet, which would automatically update [00:15:38](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m38s) your values. 

### Changing The Percentage

[00:15:38](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m38s)

If you have updated more than 50% of the English strings to a specific language, it will automatically be added to your component. You can change this percentage by going to Options in JCB and then changing Add Language: 'Select percentage any language should be translated before the system should add the language to the component during compilation'. [00:16:12](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m12s) If more than 50% of your English strings have been translated, it starts adding it to the component. If not, it will just ignore it. That is giving you a quick demonstration of the new Import/Export Option in translating the strings in your system and knowing that if you have translated any of these strings, [00:16:41](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m41s) you need to do it once and it will dynamically be available to every other component that uses that field or that view and therefore these English strings. 