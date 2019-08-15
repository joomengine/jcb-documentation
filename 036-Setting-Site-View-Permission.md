# SETTING SITE VIEW PERMISSION

[00:00:00](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

How to set the Site View Permission. The site view permission is related to the front end of any site view. Since it is usually by default set to 'Not Allowed', that is because there is the problem where that data is controlled by the Global settings of the component. Unless you write some custom script to add that Global settings to the database for permissions, it does not have those permissions set and because it is not set, it is by default always set to 'Not Allowed'.
 
[00:00:49](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m49s) Sermon Distributor is used which is one of the demo components that are available. (Access to this demo component may be purchased)  It has Site views and in the options tab, there is a permission tab. If a search is done for 'Site'. Categories site access, plural and category site access, singular may be seen. There is also preacher site access and preachers, series and series list, and sermon. [00:01:38](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m38s) All these various site accesses literally indicates whether the public will have access. By default, it is set to inherit, and inherit will show 'Not Allowed'. Now there is something that I have done to try and accommodate this problem in JCB.

[00:02:02](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m02s) Let's close here and look at some of the code I have done. Open Component Builder, then components and Sermon Distributor. Go to Settings, then Site Views. Click add, you will see that we have here a value called Default View.

### The Default View

[00:02:40](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m40s)

The Default View is that view to which the component will direct you if a view is accessed that a user do not have access to. Usually, the default view is set to not have access control. So the Default View does not have access control, which means that it is open to all. [00:03:12](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m12s) On this view it may be explained how to get access to the rest of the component because it can be seen in what user group the user is and by that determines some messages. There can only be one default view, even if more than one is selected. The first one, the compiler gets to become the Default View, the next one will be ignored. [00:03:52](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m52s) There can only be one at the moment. It shows 'Select only one'. If you have access for categories and it is not yet set, it will throw the user back to, for example, to 'Preachers'. What is the advantage of this? It simply negates the error page. So that you do not get a loop where the permission never gets resolved. It goes into a loop and then crashes the site. This prevents that but it does not solve the problem with the permission structure completely. But it is at least a first step towards trying to resolve it. This(See video) is the default page. Do not give the default page permission structure if any of the other pages are accessed, it will divert to the default page.

### Adding Custom Scripting - Showing After Installation

[00:04:48](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m48s) 

 To address this problem some custom scripting can be added which will show in the demo component after installation. If the PHP tab is opened, you will see that it has a queued message in the PHP (post-flight) installed blocks. [00:05:19](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m19s)It gets the factory, get the application. 
This is an info message comes up after installation:
'First set the component global setting and the permissions in the options area or the front end of the component will not work as expected. Please note that each view on the front end has access and permissions. So if you would like the public to access those views, they must be given the access and permission.'  [00:05:54](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m54s) You can change this(See video) into a link, and even add custom script here, that updates this component's permission structure, and adds the public to have access to the site views. It some of the ways to resolve the permission restraints of site views. 

### Site Root - In The Code

[00:06:38](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m38s)

Let's look at it at code level. Here is the access file of Sermon Distributor, and if a search is performed: 'Site'. [00:07:00](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m00s) It may be seen that it has the site access values set for the component. If the front end of the component is opened and then categories, it can be seen that it is asking whether the user has that access, and if it does not, it does a redirect, then redirects to the default page. Open the default page. [00:07:32](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m32s) The ideal for the default page, is that if the default page is not the site root, it cannot access the default page. It will add this error, and redirect to the site root, which being the websites homepage. This had been done to prevent this permission structure from interfering with your user experience. 

[00:08:04](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m04s)
Now if we go back to the Sermon Distributor component, and again open the Site views, this time I changed it so that it does not have access. It is saved that way. Go to the compiler, compile Sermon Distributor and install. Let's go back to the code. It may be seen that it does not have any of that checks in the Preachers file only in the category file. [00:08:57](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m57s)  It still redirects to Preachers, which in effect means that this one will no longer give any errors, but it will show these ('COM_SERMONDISTRIBUTOR_NOT_AUTHORISED_TO_VIEW_CATECORIES'), 'errors'); errors, which relates to the fact that they cannot see the categories. An advancement that we might consider, is to add a field to the component, where the user can change these errors to show maybe a message of how to purchase access. 

**Custom Code Implementation**

[00:09:35](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m35s)

At this stage, JCB does have the option to customize any section of code by using what is known as the Custom Code Implementation. For more detail on this feature, please go to Youtube where it is explained how to change this whole code block and how to use your own implementation upon these measures. [00:10:10](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m10s)

This was a demonstration of how to manage the different permission structures for JCB regarding the site front-end and if you do not need that control, simply just put it off.

 