# AUTOMATIC IMPORT OF CUSTOM CODE DURING COMPILATION IN JCB

### Custom Code

[00:00:00](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)
 
A very smart new feature has lately been added to Component Builder that's called custom code. It is stored next to Dynamic Get. You'd hardly ever need to go in here unless you want to look at what is already been stored and make changes in the UI. Most of the time the changes will be done in the editor. 

**What is the purpose of this new feature?**
[00:00:39](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m39s)

The feature is there for those who are used to coding in another editor. For example, they create a component in Component Builder, then once it is created, they do a compile and install it onto the same website as Component Builder to test it. [00:01:13](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m13s) Then during testing, code is added into that compiled version that is installed onto the website. The new feature is able to, on compilation to extract that custom code, store it in this custom code area, and add it back into the component on the fly. Since there are some limitations, a demonstration of some rules and guidelines is necessary. [00:01:45](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m45s) This is still in beta and quite a few improvements still need to be done. I would like it to be tested and would appreciate some feedback from you. 

I'm going to compile the demo component since most of you might already have this component installed and can then use this as sort of a test area. I'm going to install it on to this current site and explain how to add custom scripting to that component by going to an editor. 

### Editing Code In The Editor 

 [00:02:28](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m28s)
 
Here in the editor can this root directory of the website be seen. Go to the back end of the components. Open administrator, components and then the demo component. To demonstrate: On the main index page some custom scripting is added.

### Conventions Used(Insert Code - Replace code)

 [00:03:04](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m04s) 

There are some conventions and regulations that should be considered when the way to add custom scripting is explained. Let me first show you the conventions. To insert Custom scripting you will use a tag like this(see video). You will use asterisks(&ast;) instead of the X's that are in the code. The code has the X's in it but the actual way would be with the asterisks(&ast;). So that will be to insert a new code. Use that place holder(///&ast;&ast;&ast;[INSERT<>$$$$]&ast;&ast;&ast;///) in the beginning of the area, then after a new line,  insert the code, and then at the end of the code, insert this one(///&ast;&ast;&ast;[INSERT<>$$$$]&ast;&ast;&ast;///), to close the code. [00:03:50](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m50s) There are two ways of adding code. One is to insert code and one is to replace existing code. So 'insert' code would simply at the same line insert that code into the existing code, where is 'replace' code will remove the old code and add the new code in its place, So these are the two conventions. Once Component Builder adds the code back, the tag will change to 'inserted', and will have this(23) new number at the end. [00:04:28](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m28s)This number is referencing the id of the code in the system. 

**NB. Do not change this number.** Component Builder would interpret that it does not have one, and it needs to be created. It will be an error. It will add this at the end. After compiling it and adding this string in, it won't compile it again, because of these opening and closing [00:04:56](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m56s) brackets not being there. (Greater and Lesser than signs). They are the ones that activate it and makes it be parsed again. When Component Builder places the code back, it looks like this(///&ast;&ast;&ast;[INSERT<>$$$$]&ast;&ast;&ast;///). If it needs to be changed at a later stage, just add this diamond(<>), and it will then update the existing code in the database with the changes that had been made.  

### Limitations For Inserting And Updating

 [00:05:30](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m30s)

There are a few limitations. Code can not be added closer to each other than about 6 lines. If there are going to be code closer to each other and it ends and starts within the parameter of 6 lines, you will end up with a problem, especially at the end. [00:06:14](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m14s) The reason is Component Builder doesn't only use the line in which this is found to remember where to place it, but actually creates a fingerprint of the code above this insertion and the code below this insertion, to accurately insert it in the future. If that code changes, Component Builder will give notice and will not insert the code. That is due to the nature of JCB. It is constantly being improved and therefore its code moves around quite a lot. [00:06:48](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m48s) It had been impossible to automate this, because code may accidentally be overwritten which has never been intended.

The only way to solve this was to create what is called a "fingerprint", a few lines above the insertion of the replacement and a few lines below the replacement. To insert new code this will be used(///&ast;&ast;&ast;[INSERT<>$$$$]&ast;&ast;&ast;///). To replace new code or if it is initially done, use that(///&ast;&ast;&ast;[REPLACE<>$$$$]&ast;&ast;&ast;///) [00:07:25](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m25s) At the end of the code add these corresponding placeholders(///&ast;&ast;&ast;[INSERT<>$$$$]&ast;&ast;&ast;///) and(///&ast;&ast;&ast;[REPLACE<>$$$$]&ast;&ast;&ast;///) . This little block(see video)is placed into the comments of this tutorial. If any of you need to copy it get it from here. When Component Builder adds it back, it will look like this(///&ast;&ast;&ast;[INSERT<>$$$$]&ast;&ast;&ast;///23) if it is inserted and like this(///&ast;&ast;&ast;[INSERT<>$$$$]&ast;&ast;&ast;///25) when it is replaced. Just add that diamond(<>) in there for it to be updated in the database. 

* ### Showing Example With Replace(see video)

[00:08:00](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m00s)

Let's see this in action. Here is Demo Components main document open. Some replacement tags are added. No changes are made but a few lines are added here - ///. Maybe another comment - 'hi it worked', [00:08:34](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m34s) let's do - echo 'hi it worked' and that should do it. This is going to replace this area. 

### Recompiling The Demo Component With Replace  

[00:08:58](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m58s)

Let's go to the compiler and compile the component. So in the compiler, I'm going to compile a component again. It is successfully compiled. Now before it is installed a check may be done to see whether it actually did get the code from the component.

### Checking The Custom Code Tab Before Installing 

 [00:09:24](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m24s) 

The way it's done is to open Custom Codes in a new tab. There the component demo and the path in which the change was made may be seen, and it was a replacement. If it is opened, the code that we want to be replaced can be seen and the hashtag for the start, the fingerprint and the hashtag for the end. All that needs to be done in this area is to click 'Install'. That will be the compiled version. 

### Looking at The Replaced Code In Editor

 [00:10:03](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m03s)

Now let's go back to the code. It inserted the code in the correct place, moved the other code down the right quantity of lines and it changed it from 'replace' to 'replaced'. It added the ID after it that targets it. If it is not needed in here, like that(See video). [00:10:32](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m32s) Click save then go back to the compiler and compile it again. Install it again. Go back here, refresh this. Do not forget to add in the diamond. If the code is changed, make sure that it is added back in otherwise it will look for it. So we add that back in. It successfully updated the code in the database. Install it and it will get updated in the code. That is how to replace a certain section. 

### Inserting Custom Code Via Editor

 [00:11:32](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m32s)

Let's look at inserting. Remember, don't put code close to each other within at least eight lines. So 1, 2, 3, 4, 5, 6, 7, 8. From this line, another set may be inserted or another section of code may either be inserted or replaced. [00:11:58](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m58s) The reason is that the fingerprint that it creates above the insertion, is sometimes up to 8 lines long. It could happen that it uses from the selected area(see video) and turn out to be an error when changes are made. It will interpret that this code has also been affected and will not find it. That is one of the limitations that these code insertions that is done either by replacing or inserting a portion of text script, can only be inserted up to eight lines apart. Let's do an insertion over here(see video). It is inserted and a comment placed in. Then save and compile. 

### Checking The Custom Code Tab For New Entry Before New Installation 

[00:13:46](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m46s)

Before we install it, it is important to check whether everything was done as expected. The insertion has been grabbed and added to the database. [00:14:04](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m04s) It has the hash# target. With insertion, we only need where it starts not where it ends and so that can be closed. Now simply install that component. Go look at the code. It did add the replacement script, change it from 'replace' to 'replaced'. It has added the inserted script from 'insert' to 'inserted'. [00:14:34](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m34s) If a change needs to be made to it, just add these diamonds (<>). Make the change. Save the file and compile. Check whether the work was updated. Install the component. Take a look at the code again. It is added back. [00:15:18](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m18s) 

If for some reason this code above it changes, there is another part of this implementation that will give notice on compilation that there has been a change to the fingerprint and it could not find the insertion area.  It will still add the code on the line number, but it will be escaped. So that it doesn't change or influence any of the code that still there. The same applies to the replacement code. [00:15:50](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m50s) Since it is replacing code, it is a little bit more tricky. So it will still be added into the line, but the old code will not be removed. It needs some fine-tuning. Any feedback would be appreciated.

**Component Builder can now automatically extract Custom code from a component while in development.** [00:16:21](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m21s) A switch has been added, that when you are ready to distribute your component, you can say that you are aware that it is no longer in production. When it is compiled, it will not add these placeholders anymore. Please give your comments at Github.  [00:16:51](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m51s)
