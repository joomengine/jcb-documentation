# GENERAL PLANNING

### Be Prepared to Build Components in Component Builder

[00:00:00](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

When you want to build a component in Component Builder you need to be prepared. You would need to know what to build and what the database structure is that you want to set up. If you want a good understanding of the table and of the database and how to have it mapped, these are essential things you need to know. If you do not know that, I can give you pointers on some of the things you will need. At the same time, I will try to explain why you need to know these things.

### Use Demo Components To Build Back End Views

[00:00:49](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m49s)

We are using Sermon Distributor, which is a component that I have developed for Distributing Sermons. [00:00:58](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m58s) Use the demo component that is demonstrating how to build components. You need to know what you are going to call it. (This one is called Sermon Distributor.) You would need to know back end views. [00:01:19](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m19s)  The back end views in Joomla must be tightly connected to the database. 

### The Purpose of Conventions

[00:01:40](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m40s)

By illustrating the best convention of implementation, Component Builder will allow you to break these conventions, but later you would regret doing so and possibly have to redo a lot of things. [00:01:51](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m51s) The purpose of these conventions is to add up implementation in other areas, like your custom field types and so forth.

### Back End Views Need To Be Set Up

[00:02:16](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m16s)

When Sermon Distributor is going to be built, [00:02:20](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m20s) back end views need to be set up, because we want these features inside the component. That is sermons. We have a list view [00:02:33](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m33s) of the sermons as well as an editing view of the sermons. They share a common database table [00:02:51](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m51s) although they represent two views: a list view and an edit view. [00:03:27](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m27s) The editable view is in relation to the back end connection of the database itself. The back end usually forms the connection to the database. The front end is more dynamic. These things will take quite a lot of explanation if you are new to coding, PHP, JavaScript and CSS. [00:04:21](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m21s)

### Drawing Data From Dynamic Get Feature in Component Builder

[00:04:44](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m44s)

The site views and custom back end views are mostly the same kind of implementation, both drawing their data from the Dynamic Get feature in Component Builder. Think of these three as working as a team, while the back end views stand as the database for these. You need to set these up first. Add them to all the necessary fields that will then be mapped to the database [00:05:16](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m16s) columns, which then through the Dynamic Get connect to formulate a data model. This can be reused in your custom back end and in your site views.

### Back End Views Maps Directly to the Database

[00:05:40](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m40s)

Back end views are very tightly connected to database structures. If you look at Component Builder itself, you have what is called components, and if you open one, it has fields in it. If you want to go to the database, [00:06:02](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m02s) and open Component Builder, you would see the fields there. All these names [00:06:31](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m31s) are actually mapping directly into the database. These names are alphabetical. They directly map to the database and is in a way editing the database through this view. When it comes to the components, your back end views are all being limited to this kind of structure and is not a 58limitation on Component Builder's behalf. It is the way Joomla [00:07:13](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m13s) wants to implement it. Your class, your model, your controllers, and everything else behave correctly because of that implementation, even if it is a major limitation. If you want to 58go beyond that kind of infrastructure you would probably need to look at another way of using Component Builder. We only implemented it this way so that your back end views direct maps to the database. We know that from time to time there are back end views that do not have their own database, but rather take saved information in the database, either from other third-party components or even your own component, because we know that you would like to take that information and remodel it into a spreadsheet, [00:08:17](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m17s) a chart, or any other kind of way. We added this custom back end views which behave on the same dynamics as the site views. We are trying to give you the best of both worlds. First by being that strong tightening manage data sets, which relates directly to the view and the list view and so forth. Then at the same time giving the option of adding a custom back end view, which can be dynamic and in which you can do custom scripting. [00:09:08](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m08s)

### Use Dynamic Get Option to Get Data From Tables

[00:09:19](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m19s)

You need to know your back end views and then any possible custom views that combine back end view. We haven't done so yet. Possibly take statistics, sermons, preachers, and series, because these statistics are taking only t58he downloads, whereas preachers have in them a field called hits. Sermons also have a field called hits. When someone opens one, without downloading it necessarily, so does series. [00:09:55](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m55s) But statistics only count the downloads of the sermons. We could possibly add an extra custom back end view called "analysis." In "analysis" we can use the Dynamic Get option to get data from all those tables. [00:10:29](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m29s) Let us shortened it by removing statistics and then do modelling. [00:11:15](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m15s) Modelling the data could make us end up with a whole new data structure which we can place into a table or a chart in that view. That would mean that it is now dynamic and no longer directly connected to the database. 

### Analysis View Used To Get Data; Mapped Fields

[00:11:39](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m39s)

These above views won't have an edit view. There will be a single view displaying rows of analysis data from multiple back end database tables. This can also be done on the front of the site. [00:11:59](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m59s) We can put this whole Get Feature under Get and we can give it a name, calling it Get Analysis. [00:12:17](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m17s) The analysis view is used to get the data, then it takes that data and displays it on a page. The same can be done to the front. [00:12:37](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m37s) The same Dynamic Get can be used in the front again. That is how Component Builder works. The fields are a discussion on their own, but what I have typed out is very basic and elementary. It is what you need to know before coming to Component Builder. You need to know what you want to achieve, [00:13:05](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m05s) what you want to build, and if possible, have mapped the fields under each of the following. In sermons, we will have "name" and we will have "preacher." [00:13:23](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m23s) We will have "series," and we will have "files." They should be under sermons. Under "preacher" we will also have "name," and maybe we will have "email," and "description,"  - name, preacher, series and files. and  "website." [00:13:45](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m45s) For series we will add a name, which would be "description" and "statistics," since we are only counting downloads. We will have a file name,  a counter, and a sermon. [00:14:26](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&tn=00h14m26s) If you start in Component Builder you can start by creating a new component and add "name" and all this information. 

### Fields are Compulsory

[00:15:20](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m20s)

Initially, you would skip most of this just getting started. Set up the fields that are compulsory; the ones with the stars and this component image that tells you the dimensions: 300pix X 300pix. Place it in the image folder and then access it. [00:15:44](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m44s) (This version update is a nice feature which we will look into later.) You will add all these compulsory fields. You would hardly do anything at this stage at settings. You just leave "scripts" blank; "read me" also blank, then add views after you've saved the component. Once you have added "name," added these, and clicked save, [00:16:13](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m13s) you are basically able to start adding views to it.

### Adding Views Are Different Than Creating Views

[00:16:20](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m20s)

The way to add a view to a component is different from the way to create a view. Add the view through the settings tab. You can create new views through this area, and you can also see your already connected views.

### Add Fields To Views

[00:16:44](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m44s)

If you start building a component, you might feel lost if you do not know where you are going.  This will help you know if you need to set up these views. [00:16:48](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m48s) You need to add these fields to those views. (This kind of information and knowing how to construct it is something that you need to know beforehand.) You can always add more fields and more views. [00:17:23](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m23s) Component Builder cannot decide that for you. You have to create all of these fields before you can add them to a view. This line is seen as one view although when it's compiled, it will represent two views. It is in Component Builder's component back end views. 

### Name Fields Can Be Reused; Default Fields Shows Which Fields Are Added Dynamically

[00:17:51](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m51s)

These fields will need to be created before they can be added to this view. The name field which you can create once can be reused three times. The hits are already added by default so you don't need to add a hits field. [00:18:17](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m17s) The default fields are showing you which fields you don't need to add but are added dynamically. To each back end view, there is a custom back end view. The purpose is that it doesn't directly relate to a single database. This gives you the option of pulling from multiple databases. It is a quick overview of how to get started with a component, modelling the data and displaying it. [00:18:57](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m57s)

### Create Admin Views and Fields

[00:19:11](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h19m11s)

We will start in the fields. It seems turned around. You might feel we must start at the component, and then build the views, then build the fields. [00:19:24](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h19m24s) After having created the component, you can click your own admin views. The first thing you need to create is the admin views. Click new and create an admin view. Again it is just like it was with the component; you are able to set the bare bone information. I usually start at the bottom and work my way up. [00:20:02](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h20m02s) I create all the fields, and when I see that there are duplicate fields, I remove them because I know that we had used them. I create fields which I know to be unique. When I come to certain fields, I won't create them initially, like these custom fields. [00:20:42](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h20m42s) I would separate the custom fields. How do I know it's a custom field? Because the preacher is. I want to pull IDs from the preacher view and mark those custom fields again. I want this field to link to that name; a list of those names. [00:21:45](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h21m45s) The same goes for the series.

### Creating Normal Fields and Back End Views

[00:21:54](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h21m54s)

In Joomla, you can create what is known as custom fields. Component Builder makes provision for you to do so. This is what I would call an advanced field. We will look at advanced custom fields after we've looked at creating normal fields and creating actual back end views. [00:22:15](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h22m15s) Only then will you understand the implementation of this custom field since it will be linking to back end views value. It is not just linking to a bunch of values, it is linking directly to this back end views value called name, so we can't really create it until we know how this is going to look.

Building a component needs these kinds of things [00:22:51](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h22m51s) to be thought through and mapped out. Some of us might not need to write it down, some of us do. You must come to Component Builder at least knowing partially what you want to achieve and what you want to build. That means you can do a lot of paper planning and do a lot of structuring of your component long before actually getting to Component Builder itself. That is what this [ tutorial was trying to illustrate. [00:23:33](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h23m33s) If you haven't done this, you might get lost and not know where you are heading when you start mapping the fields, the views, and the things in Component Builder itself.

### Next Tutorial

[00:23:50](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h23m50s)

In the next tutorials, we will start looking at field types, and how to use field types to create fields. [00:23:56](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h23m56s) We will progress to eventually ending up with having this component fully functional and working. We will be illustrating all of these fields as they relate to these back end views that are linked to database tables.  [00:24:22](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h24m22s) Hopefully that will give a good enough insight and understanding of how all this should be done.
