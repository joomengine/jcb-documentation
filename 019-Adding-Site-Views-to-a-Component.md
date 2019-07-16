# ADDING SITE VIEWS TO A COMPONENT

Using Sermon Distributor As Example

[00:00:00](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

Let's look at adding Admin Views and Site Views to Component Builder's component. We will look at the different switches and the features installed for you. First, login. Open Component Builder under Component Builder, then go to components. 

### Settings - Views

[00:00:25](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m25s)

Open Sermon Distributor and go to settings. There is a place for Admin Views. (Adding the Admin Views has already been illustrated.) There's Custom admin views and Site views. Click on 'add custom admin view'. There aren't any added to the component; Sermon Distributor does not have Custom Admin Views. [00:01:01](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m01s)

### Adding Site Views Important _Glitch_

[00:01:11](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m11s) 

It has quite a few Site views. You might open it and see some of the buttons are not selected. Although you selected and saved it previously it doesn't show. This is a glitch in Joomla's own JavaScript. [00:01:25](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m25s) Re-open. (For now Admin view has the same issue.) Close and open it again, and it will all be selected. Keep a look out for this; if you make changes and save it with those buttons unchecked, it will not include those values since it will be stored as null and you might get unexpected results. [00:01:56](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m56s) Unfortunately this is not something that can be changed at this stage.

### Site View Options(Menu-Metadata-Default View-Access)

[00:02:21](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m21s)

Go to site view. Close it and open it again. Everything is selected. It has four options. Select the site views and add as many as you like.

* Menu

Add menu means that this site view will be added to the add menu aspect of Joomla. [00:02:46](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m46s) Go to create menu and to add menu item. There is a 'select Type'; if you click on it there is list articles, etc. If you say 'yes' an XML file will be created which allows Joomla to notice that your component needs to be in the list. [00:03:12](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m12s)

* Metadata

Add metadata means that this page will make use of the metadata being passed to it. Usually this means that in your model where you've set up your data, a metadata is in the 'items' array or in the 'this' array by the global setting or via the actual item. [00:03:47](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m47s) If you set 'yes' here, and did not set up the data in the in the model correctly, it won't work. Click 'yes' here. (See video.) Try your best to set up the data in the model, then compile and look in the view .html.php file to see how it collects the meta data. It will still add the script needed to load the metadata into the document. If it doesn't collect it correctly, you'd see it too. [00:04:22](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m22s)

* Default View

You can only have one default view. (Don't click more than one.). The default view is effective so that when you make a change and the system doesn't know where you want to go it takes you back to the default view. [00:04:53](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m53s) Default view can either be your site default view being 'home page' or, if you are in this component, on 'preachers', for example.

* Access

Let's say some of these views you have set don't have public user or access, for example, to sermon. If you try to access the page, the system throws you back to the default view, and gives a message that you don't have access. That's what the default view is primarily used for at the moment. It can become more useful as we continue to improve Component Builder. [00:05:37](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m37s)

Add access makes sure that a user has certain access rights. In an item you can set the access rights and the view rights. It has multiple implementations. One is access groups, the other is groups. If you want access on this specific view to be monitored, tick that and Component Builder will ensure the access table is there. [00:06:10](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m10s)

After creating the Site view this is how you can add it. Check it and see how it works. [00:06:32](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m32s)
