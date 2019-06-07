# ADDING SITE VIEWS TO A COMPONENT

* Using Sermon Distributor As Example

Now let's look at adding admin views and site views to component builders component. Looking at all the different switches and the nice features that we have there installed for you. We first login. Then we have component builder open, under component builder. Then we will go to [00:00:25](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m25s) components. 

### Settings - Views

We will open Sermon Distributor and then go to settings. In settings you see there is a place for admin views. We have already illustrated adding the admin views. There's custom admin views and there is site views. I'll click on add custom admin view. There isn't any added to the component,[00:01:01](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m01s) sermon distributor does not have custom admin views. I'll illustrate it in another component for you. 

### Adding Site Views Important _Glitch_ 

Then site views. It has quite a few. You might sometimes open it and see, that some of the buttons are not selected. Although you selected it previously and save it and it doesn't show. This is a glitch [00:01:25](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m25s) in the Joomla's own JavaScript or whatever that is causing this. The only way I have found to solve it as yet is to simply re-open, like for now(you will see admin view has the same issue) if you close it and open it again, it has it all selected. This is a heads up. Keep a look out for this, because if you make changes and save it with those buttons anticked, your build will [00:01:56](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m56s) not include those values since it will be stored as null. You might get unexpected results. Always make sure that your old ticks are all in place, that just a heads up. It is not something I can change at this stage. It is a Joomla thing of the repeatable fields. 

### Site View Options(Menu-Metadata-Default View-Access)

If we go to site view [00:02:21](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m21s) and we close it again and open it again. You will see everything is selected. You will see that it has 1,2,3,4 options. You select the site views, add as many as you like. 

* Menu

Add menu means that this site view will be added to the add menu aspect of Joomla. [00:02:46](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m46s) If you go to create menu, you go to add menu item. Then there is a select Type, and when you click on select type, then there is list articles and whatever. If you say yes there you'll create a xml file which allows Joomla to notice that your component needs to be in the list. The xml file will look at it in a moment. [00:03:12](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m12s) That's what this switch here, add menu does. 

* Metadata

Add metadata, means that this page is going to make use of the metadata that is being passed to it. Usually that means that in your model you've set up your data, that there is a metadata in the 'items' array or in the 'this' array. [00:03:47](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m47s) Either by the global setting or via the actual item. This is meta implementation, even if you set yes here, and you did not set up the data in the in the model correctly it won't work, and the way for you to look at that, is click yes here. Try your best setting up the data the model, then compile and go look in the view .html.php file to see how it grabs the meta data, because it will still add [00:04:22](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m22s) the script that is needed to load the metadata into the document. If it doesn't grab it correctly, you'd see that as well. 

* Default View

Then whether you can only have one default view. So don't click more than one to yes but what the default view effectively is, is that sometimes when you make a change and the system doesn't know where you want to go [00:04:53](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m53s) It actually throws you back to the default view. Know that default view could either be your site default view being home page. Or it can be if your in this component, it could be, for example on this one it's preachers. 

* Access
???
Let's say some of these views you have set they don't have public user, don't have access for example to sermon, then if they try to access that page, the system will throw them back to the default view, and give him a message saying you don't have access. And so that's what the default View Primarily used for at the moment But I can see it being coming even more useful as we continue to improve in component Builder [00:05:37](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m37s) Then add access It's basically making sure that a Sydney user has the specific access rights You see in a in an item you can set the access rights As well as the view rights So it's multiple implementations Different implementations one's access groups the other one is just groups And so you can tweak whether you want access on this specific View to be monitored And If you tick that Then [00:06:10](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m10s) Component building will ensure that the access Table is there Ok So that is adding a site view to to your component Obviously after having created the site view Then this is how you can add it to check it See how it works Ok now next up we gonna look at [00:06:32](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m32s) Custom admin views being added Thank you for watching
