# ADDING CUSTOM ADMIN VIEWS TO A COMPONENT

[00:00:00](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on this time links to see Youtube video_)

Cost-benefit projection will be used as our component. 

### Settings - Custom Admin View

[00:00:14](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m14s)

Go to 'settings' then to 'Custom Admin Views'. Two 'Custom Admin Views' had been added.

### Multiple Switches Due To Being Dynamic

[00:00:28](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m28s)

It has more switches than the Site view because its implementation is more dynamic. You can choose an icon, because in the back end you might want an icon when you are on the right of the page. [00:00:45](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m45s) It can be selected where it should show in the main menu.

### Icon - Main Menu - Dashboard - Submenu

[00:00:51](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m51s)

The main menu drops down from Joomla's 'menu item list'. This is the dashboard you need to go to every time you start with a component where all the icons are displayed. The 'Sub-menu' is the one on the left; it can be seen when you are in a view. [00:01:14](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m14s) These are all placements where this Custom View could be added. (See video.)
 
### Targeting Item

[00:01:29](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m29s)

The company results hadn't been added to any of the views individually; it was added to items. That's why all of these are set to 'No'. [00:01:41](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m41s) It means an item is targeted in a view.

### Select Target View

[00:01:47](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m47s)

Select the targeted view, which is 'Company'. Use one of these options: 'Has Metadata', 'yes' or 'no', and 'Add Access', 'yes' or 'no'.  [00:02:02](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m02s) By selecting 'Company' it ensures that the correct view is targeted; close this and open that component. (See video.)
 
### Showing Within The Component

[00:02:10](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m10s)

This is an example of what happens with the settings: Open the 'Cost-Benefit Projection Dashboard'. If 'Companies' is opened, there is a button for 'Company results'. [00:02:27](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m27s) When Custom Admin View had been set up, we ensured an 'item id' to be targeted. By selecting 'Company', the companies 'item id' is targeted. That is what makes it work. Click 'Chart' to view these charts showing up in the icon itself. [00:02:55](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m55s). If you click on it, the Custom View shows up and that icon shows up next to it, showing that all works well. (See video.) A 'Combined Results' button shows up in the toolbar because 'Combined Results', which were selected, should have 'Cogs' as a icon. [00:03:25](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m25s) List of records, ('Metadata', 'Access', and 'Company') is set to 'yes'.

### Order Before Selection

[00:03:35](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m35s)

These 'Order Before' selections are only necessary when a 'main menu' and 'sub-menu' are selected. Because it may decide before what item this menu should be creating. [00:03:55](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m55s) 'Dashboard (list of records)' had been selected and consequently places it in combined results. The records that you want to look at need to be selected; click on 'Combined results'. It will grab those ids. Since the data is modeled in the controller and the model it gives these results back to the view through the custom implementation that has been done. 
 
### How Buttons are Implemented - Important

[00:04:25](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m25s)

* Quick refresher

Go to Component Builder and Custom Admin views; open 'Company Results'. PHP have been added in the Custom Buttons, as was 'Button'. A request has been made to Component Builder as to what kind of buttons are needed. A single item is targeted. It shows 'editCompany' and 'gotoCompany'. These buttons are related to the inside of the view. [00:04:55](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m55s) On exiting 'Editing the Custom Admin Views', it shows in 'Combined results' that 'buttons' had been added. Again these buttons, 'Vcard', 'companies', 'gotocompanies', corresponds to the controller. [00:05:27](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m27s) In the view itself it shows that it is not responding to this button but to the buttons inside called 'Companies' and 'Edit'. (See video.) These are the buttons you were building in the custom view. Whereas the buttons we are looking at in here are related to opening the Custom View itself. (See video.)

 ### The Combined Result Button

[00:05:53](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m53s)

The same applies to Combined Results. Combined Results is the button set up here. (See video.)  Once the other buttons are combined, and Combined Results clicked, it shows that two buttons had been added: 'Dashboard' and 'Companies'. Those two buttons had been set up in the view itself. It is possible to know what area controls what set of buttons. This area controls the buttons before opening the view. In the view, the buttons you set up there is for when you opened the view. [00:06:38](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m38s)

If you are uncertain you can undo everything, change it, compile a component, look in the code, and see what has been done; look in the Joomla interface, and see what is being displayed. Do some experimenting until you get that what you wanted. [00:07:10](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m10s)

Note: This 'order before' is only necessary when 'add' is selected to 'Main-menu' or to 'Sub-menu'. If it is used there will be an icon area displayed in the component (Cost Benefit Projection) and the menu items will be shown at the top. Once it is opened the Sub-menu appears on the left. [00:07:34](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m34s) There is 'Main' menu and 'Dashboard (list of records)'. Dashboard (list of records)' needs to be placed at the top of the components toolbar and 'Submenu' to the left. [00:07:58](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m58s)

The Custom Admin View needs to be placed in the Sub-menu and is independent from any other data set. The Sub-menu method can be used then. If you want a feature in the main menu, these are the features that can be set. [00:08:25](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m25s) The 'Dashboard (list record)' feature helps to link it to a specific set of data structures. These IDs can be selected. When you click on combined results, the IDs of the selected items is passed to the controller. For example: Look in 'Companies', 'Components', 'Component Builder', 'Custom Admin Views', 'Combined results', and in 'Custom Buttons'. [00:08:54](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m54s) We're using the 'Main get' called 'Companies data' (getlistquery).

The implementation of the IDs can be seen in the Data query. Reach into the input object (PHP in Editing the Dynamic get). Get the 'cid', selected 'IDs', and saying 'tt' can be 'CMD' and then 'explode' 'cid'. [00:09:35](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m35s) Make sure it is 'intervals' and place it in 'ids'. This gets 'this' value from the 'post object', and places it into 'ids'.[00:09:59](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m59s)  Validation have to be done to ensure the person who's trying to access the data has the right to do so. Once it is passed, the 'ids' are used to get the data. [00:10:20](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m20s)

In the filter '$ids' is used; it checks whether all the 'ids' are in an 'id' in the code. Look at the code; it's on the models 'Combine Results'. It uses the checking method. It checks the 'ids',  places them in an array; checks if it's in an array then 'implodes' it. It also checks whether it gets those ids. [00:10:45](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m45s) That's how  the dataset is filtered with the results of the selection. [00:11:07](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m07s) Some custom scripting were added to the Dynamic get method to take the 'ids' and use them in intended way. This is the way Llewellyn implemented this.

If you want to drop it down, pause the video, and copy some of this area. It would be the only part useful to your purpose. Use the 'ids' in your code as it suits you. [00:11:39](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m39s) Keep in mind that this PHP, as seen in the code, runs before the 'Get methods'. It is a filtering option. (See video.) The 'getListQuery' starts, then the code that has been written is entered here then the rest of the code built by Component Builder is done. (See video.) A filter option may be used with what you collected.  [00:12:07](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m07s)