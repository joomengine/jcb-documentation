# ADDING CUSTOM ADMIN VIEWS TO A COMPONENT

Cost-benefit projection will be used as our component. 

### Settings - Custom Admin View

Go to 'settings' and then to 'Custom Admin Views' . It will be seen that two 'Custom Admin Views' has been added.  [00:00:20](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m20s)  

### Multiple Switches Due To Being Dynamic

It has more switches than the Site view because its implementation is more dynamic. You can choose an icon, because in the back end you possibly want to have an icon when you are on the right of the page.[00:00:45](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m45s)  Then it can be selected where this should show in the main menu.  

### Icon - Main Menu - Dashboard - Submenu

The main menu drops down from Joomla's 'menu item list'. This is the specific dashboard you need to go to each time when you start with a component where all the icons are displayed. Then the 'Sub-menu' is the one on the left,  which can be seen when you are in a view.[00:01:14](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m14s) These are all placements where this Custom View possibly may be added.
 
### Targeting Item

Remember, the company results has not been added to any of the views individually, it was added to items. That's why all of these are set to 'No'. [00:01:41](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m41s) That means an item is targeted in a view. 

### Select Target View

All that need to be done is to select the view which is targeted, which is 'Company'. Use one of these options: 'Has Metadata', 'yes' or 'no', and 'Add Access', 'yes' or 'no'.  [00:02:02](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m02s) Simply by selecting 'Company' it ensures that the correct view is targeted. If this is closed for a moment and open that component.
 
  ### Showing Within The Component

To give a example of what happened with the settings: Open the 'Cost-Benefit Projection Dashboard'. If 'Companies' is opened, you will see that it has a button for 'Company results'. [00:02:27](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m27s) Now if you remember that when Custom Admin View had been set up, we ensured that an 'item id' had been targeted. By selecting 'Company', the companies 'item id' is targeted, and that is what makes it work. Click 'Chart' to view these this little charts that shows up in the icon itself. [00:02:55](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m55s). If you click on it the Custom View shows up and that icon shows up next to it, and shows that all works well. A 'Combined Results' button shows up in the toolbar, the reason for that is that 'Combined Results' which were selected, should have 'Cogs' as a icon.  [00:03:25](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m25s) Then list of records, 'Metadata', 'Access', and 'Company' is set to 'yes'.

### Order Before Selection

This 'Order Before', selections is only really necessary when a 'main menu' and 'sub-menu' are selected. Because then it may be decided before what item this menu should be creating.[00:03:55](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m55s) 'Dashboard(list of records)' has been selected  and consequently it places that in combined results. The records need to be selected that you want to look at and then click on the 'Combined results'. It will grab those ids and since the data is modeled in the controller and the model, it gives back to the view these results through the custom implementation that has been done.  [00:04:25](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m25s) 

### How Buttons are Implemented - Important

* Quick refresher

If you go to Component Builder, and Custom Admin views, and open 'Company Results'. You will see that in the Custom Buttons, PHP has been added.  'Button' was also added  . A request has been made to Component Builder as to what kind of buttons is needed. A single item is targeted  It shows 'editCompany' and 'gotoCompany', these buttons [00:04:55](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m55s) are related to the inside of the view. On exiting 'Editing the Custom Admin Views', it even shows in 'Combined results', that 'buttons' also has been added. But again those buttons 'Vcard', 'companies', 'gotocompanies', corresponds to the controller. Going to the view itself, [00:05:27](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m27s) it shows that, it not responding to this(see video) button but actually to the buttons inside called 'Companies' and 'Edit'. These are the buttons you were building in the custom view. Whereas the buttons we are looking at in here(see video), is related to opening the Custom View itself. That is just a quick refresher. 

 ### The Combined Result Button

The same applies to the Combined Results. The Combined Results is the button that is set up here(See video) 'Custom Admin View'. [00:06:02](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m02s) Whereas once the other buttons is combined, and Combined Results is clicked, it shows that two buttons has been added, 'Dashboard' and 'Companies'. Those two buttons had been set up in the view itself. It is possible to know what area controls what set of buttons. This area controls the buttons before opening the view. Whereas in the view, the buttons you have set up there, is for when you have opened the view. That is setting up a Custom Admin View to your component. [00:06:38](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m38s)

If you are uncertain you can undo everything and simply change it and compile a component, and go look in the code, and see what has been done and look in the Joomla interface, and see what is being displayed. Do some experimenting until you get that what you expected .[00:07:10](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m10s)

 NB. This 'order before' is only necessary when 'add' is selected to 'Main-menu' or to 'Sub-menu'. If that is used there will be a icon area displayed in the component(Cost Benefit Projection) and at the top will the menu items be shown.(Companies). Once it is opened the Sub-menu appears on the left.[00:07:34](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m34s)  There is 'Main' menu and 'Dashboard (list of records)'. Now 'Dashboard (list of records)'need to be placed at the top of the components toolbar and then 'Submenu' at the left. [00:07:58](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m58s) 

The Custom Admin View simply needs to be placed in the Sub-menu and is independent from any other dataset and then the Sub-menu method can be used. If you want a feature in the main menu, these are all the features that can be set. [00:08:25](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m25s) Whereas the 'Dashboard (list record)' feature helps to link it to a specific set of data structures. These IDs can be selected, and when you click on this combined results, the IDs of the selected items gets passed to the controller. For example: Look in 'Companies', 
in 'Components', in 'Component Builder' in 'Custom Admin Views' in 'Combined results' and then in 'Custom Buttons'. [00:08:54](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m54s) We're using the 'Main get' called 'Companies data' (getlistquery).

The implementation of those IDs can be seen in the Data query. Reach into the input object(PHP in Editing the Dynamic get). Get the 'cid', selected 'IDs', and saying 'tt' can be 'CMD'and then 'explode' 'cid', [00:09:35](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m35s) Make sure it is 'intervals', and place it in 'ids'. This actually gets 'this' value from the 'post object', and places that into 'ids'.[00:09:59](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m59s)  Validation needs to be done to ensure that the person who's trying to access the data has the right to do it. Once that is passed , those 'ids' is used to get the data. 

 [00:10:20](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m20s) In the filter '$ids' are used, and check whether all the 'ids' are in a 'id' and that in the code. Then look at the code, it's on the models 'Combine Results'. It uses the checking method. It checks the 'ids',(See video)  puts it in an array and check if it's in an array then 'implodes' it. Checks whether it gets those ids. [00:10:45](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m45s) That's how  the dataset is filtered with the results of the selection. That's just a glimpse in the back end at the use of those features.[00:11:07](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m07s)  It is some custom scripting which were added to the Dynamic get method to take those 'ids' and to use them in intended way. This may be ignored ,this is only the way VDM has implimented this.   

If you want to drop that down, pause the video, and copy some of this area. Probably it would be the only part that will be useful for your purpose. Use the 'ids' in your code as it suits you best.[00:11:39](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m39s) Keep in mind that this PHP as seen in the code, runs before the 'Get methods'. It basically is a filtering option(see video). The 'getListQuery' starts, then that code that has been written, is entered in here(See video) and then the rest of the code which is build by Component Builder is being done. A filter option may be used with whatever you [00:12:07](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m07s) collected.

 That was a glimpse into adding Custom Admin Views to Component Builder. The tremendous leverage and design choices you can make in ensuring that your component is dynamic has been shown. [00:12:32](https://www.youtube.com/watch?v=sPEkbuNXwds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m32s)  