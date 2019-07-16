# CUSTOM ADMIN VIEWS

[00:00:00](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
 
Similar to Site Views, Custom Admin Views has some nice features, although some aspects when adding it to Component Builder is different. In the next video we will look at adding Site Views as well as Component Custom Admin Views to the component. As Sermon Distributor is not using Custom Admin Views yet, it has not been discussed, but there is another component that can serve as an example: Cost Benefit Projection. [00:00:33](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m33s)  It's a tool used to show companies the cost benefits of intervention of certain diseases and causes in the company. [00:01:04](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m04s) In it is 'Company results' and 'Combined results'. It respectively displays custom data in the back end of the component to certain people who has permission to view the data. In the component itself click on 'Companies'; an icon underneath each of these companies' names can be seen. [00:01:36](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m36s) There is a 'new' button called 'Combined Results'. These buttons are dynamically added by Component Builder, which will be explained in the next tutorial.

### Component Builder Custom Admin View

[00:01:55](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m55s) 

This is how a Custom Admin View will look. (See video.) All the displayed information serves only as an example. [00:02:07](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m07s) If 'ClientM' is opened, this large area is displayed where a lot of HTML and PHP can be placed. There are some custom buttons that may be added. All of this in the white area is done in the Custom View. There is a menu on the left side. All of this is done inside the custom area of the component  which is now the custom admin view.(See video.) [00:02:44](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m44s) It has different value sets. From here an edit button can be added. Since it has been linked it to a specific client or company or one item in that list,  you can click on 'edit'. [00:03:10](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m10s) From here the companies data can be accessed and edited. The convenience is that if 'close' has been clicked it opens the exact result page again. All the implementation that has been done is displayed there. [00:03:35](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m35s)

Returning to the Companies list and the Dashboard. Take a look at Component Builder and open 'Company Results'. On this page the PHP and HTML and a lot of templates are directly loaded. [00:04:05](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m05s)

### Add Custom Button Sample

[00:04:12](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m12s) 

I have a custom button area where I can add custom buttons. Click on custom buttons (add). There is 'icons' to select, the 'name' of the button and 'controller method' which you'd like to use to make the button work. [00:04:25](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m25s) Here I say 'gotocompanies'; this one is 'editcompany'. (See video.) Here decide what kind of target you are looking at. Is this a  single, a list, or both? [00:04:52](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m52s) Set those respectively, then click save. It only saves it to the form, not to the database.

### Adding Script For The Controller Methods

[00:05:05](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m05s) 

In the php controller method, add scripting to respectively implement the buttons click method. [00:05:16](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m16s) You can do that to the model as well. Add script in the controller and in the model, if you want to separate your code a bit, add scripting called from the controller. If you're not adding any script to the model, add none with two spaces (//) in front so that it won't warn that you did not add script there. As you can see the 'gotocompanies'  take you back to the companies view. [00:05:47](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m47s) The 'editcompany', on the other hand, implements Joomla's convention of opening an item to edit it by the correct channels. This is Joomla knowledge at work here; we are checking a token, etc. [00:06:13](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m13s) This snippet may be reused. (See video.)

### Area For Custom Scripting

[00:06:17](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m17s) 

We have an area for custom scripting. A lot of custom scripting goes on in that view. It has its respective places. If you want to know where, if you're not certain by the naming conventions we have used, if you want to know what's happening at some snippet, compile your components, search for the snippet, and you'll see where it comes up. That is how you setup custom admin view. 

### Combining Multiple Data Example

[00:06:58](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m58s)

The combined results is this one here. (See video.) If you click it, it will say that you need to select some items. Select the items and click combined result again, and it will do a combined resolve, taking both companies, adding it's data together, and giving you a nice layout structure of it's data sets. [00:07:16](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m16s)

If we go back to the implementation of the combined concept it looks similar to the other. Again there are a lot of HTML and PHP; the custom buttons go back to companies. [00:07:41](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m41s) It's same implementation and some custom scripting. I set up both of these custom views by adding the data, making use of the templates as well as layout implementation in both of these. You can set up layouts and templates and use them in site views. You can also use them in admin views.  [00:08:11](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m11s)