The directories, folders and files of the JCB Demo component, found in the JCB Demo installation package named com_demo_v2_0_0__J3.zip are presented here for your convenience. Other topics are presented that will facilitate the process. For simplicity, it is recommended you install only Joomla! and the JCB component without installing the JCB Demo component using the Joomla! installer. This allows you to focus on the following:

* JCB
* JCB Demo package import
* JCB areas containing the Demo component code
* JCB functionalities and features used while building the Demo component
* JCB interaction with the Joomla! API

Take notice of the last bullet above. There will be directories, files and code in the JCB Demo component package you may ponder over; you will wonder how they got there. JCB leverages the Joomla! API to accomplish this. To see how this is done, go the extra mile and cross reference everything as was done here. The process is tedious, but will reinforce your understanding of the many areas of JCB where the component's directories and files were created automatically by JCB. This includes the code snippets you have written and placed in various areas of the JCB component during the build process while using JCB's standard features and functionality to enhance your code snippet, but did not write any code for. This process also allows one to understand that JCB reuses and extends Joommla!'s core code classes, methods and properties supplied by the Joomla! API as much as possible.

The JCB Demo component analysis presented in this chapter will introduce you to a typical MVC directory structure and the files it contains, for a component that should be easy to understand. However, the MVC paradigm applies to all components, regardless of complexity, so the analysis can be applied to any component. As the complexity increases, developing with the following greatly reduces the time required to build a component:

* A local development environment like [WAMP](http://wampserver.aviatechno.net/?lang=en&prerequis=afficher) with native [XDEBUG](https://xdebug.org/) capabilities.
* Joomla! Component Builder.
* [NetBeans](https://netbeans.org/) or a similar Integrated Development Environment (IDE) with native XDEBUG and GitHub functionality.
* [Chrome](https://www.google.com/chrome/) plus its [Developer Tools](https://developers.google.com/web/tools/chrome-devtools/) and [developer extensions](https://chrome.google.com/webstore/category/ext/11-web-development) or, others like [Firefox](https://www.mozilla.org/en-US/firefox/new/) with similar features and add-ons.
* Joomla! Debug, especially its Stack Trace, and XDEBUG compatibly including links to the source in each trace
* [Joomla J!Dump](https://extensions.joomla.org/extension/j-dump/) which works well for dumping within Joomla! components instead of using PHP echo and var_dump.
* Developer Tools in Chrome is a very good source for debugging JavaScript in real time with features similar to NetBeans debugger.
* Developer Tools in Chrome has many other features to assist you with debugging and tweaking your site on-the fly.

There are [many other possibilities](https://docs.joomla.org/Setting_up_your_workstation_for_web_development), especially with the IDE, but this combination integrates well, and much of its features are native to the applications comprising it. This also applies to any other components used as examples in the videos and chapters accompanying them in this manual. The directory tree will also look more complex as you progress, and contain many additional files. However, they all share one thing in common which is the [MVC Paradigm](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller); all follow its basic directory structure and naming conventions, including the files contained in the dorectories. This also includes the locations of the files. The code and necessary constructs specific to a Model, View or Controller for each to function and interconnect with each other and the Joomla! API at the most basic level are common to all, if developed using the MVC paradigm in its strictest sense.

Unzip com_demo_v2_0_0__J3.zip and using the shell or command line, list its directories, sub-directories and all the files contained in them, by changing to the root of the directory and typing for example dir > demoDirectory.txt /s if using the Microsoft Windows command line. Other operating systems have a similar command in their shell. Then, browse through the directories and files using the file manager for your operating system like Windows Explorer or better yet, an Integrated Development Environment (IDE) like [NetBeans](https://netbeans.org/) or a similar Integrated Development Environment (IDE) with native XDEBUG and GitHub functionality. An IDE is recommended since it has many features facilitating this analysis. Some of these include:

* A file manager to browse through the directory tree and files
* The ability to open one or several files at a time in separate windows
* Using the IDE to quickly locate base classes in the Joomla! API that are reused and extended by JCB
* Searching through a development site or file to produce a list of all occurrences where the search word or phrase occurs
* Availability of many other tools in the IDE, including [downloadable plugins](http://plugins.netbeans.org/) to extend its capabilities
* Extensive debugging capabilities; NetBeans has native support for [XDEBUG debugging](https://netbeans.org/kb/docs/php/debugging.html) and [GitHub versioning](https://netbeans.org/kb/docs/ide/git.html)
* [Interaction with Chrome](https://chrome.google.com/webstore/detail/netbeans-connector/hafdlehgocfcodbgjnpecfajgkeejnaa?hl=en) or Firefox browsers e.g. Chrome's NetBeans and XDEBUG extensions plus [Firebug Lite](https://getfirebug.com/releases/lite/chrome/)

Debugging tools are an essential part of any developer's IDE. Spending hours trying to locate a run-time bug by reading through hundreds or perhaps thousands of lines of code to find a single misplaced character is exasperating and non-productive. [Good debugging skills](https://docs.joomla.org/How_to_debug_your_code) usually allow one to locate the offending line or lines of code in minutes. It's usually easy to correct an issue, it's almost always difficult to find where it occurred, especially with all the interconnections one finds in a component using the MVC paradigm, much less ones using the Joomla! API extensively such as JCB does. It also may be used to facilitate your analysis and your development efforts. Some of the functionality offered by a good IDE debugger are:

* Single stepping through code while it executes
* Adding breakpoints and watches to suspend execution and examine contents of variables
* Stack traces that show the path of each script and resource used during execution
* Watches to examine the contents of variables based on their contents
* A dump of all variables in play while single stepping through the code
* Easily examining classes, methods, and properties including their source on the fly during execution

There are [many other features](https://netbeans.org/kb/docs/php/debugging.html) and functionalities not mentioned here. Effective debugging is indispensable during the development cycle of a component. It enhances the JCB build process and allows you to quickly identify and resolve issues in the component after JCB has compiled it successfully, but the component has run-time errors. Also, make use of Joomla's! built in debugging enabled in its configuration settings. The stack trace it displays, including links if using XDEBUG, are also indispensable. Plus, it integrates with an IDE like NetBeans using the [Chrome NetBeans extension](https://chrome.google.com/webstore/detail/netbeans-connector/hafdlehgocfcodbgjnpecfajgkeejnaa?hl=en).

Getting XDEBUG to work with your browser and IDE can be a daunting task. [This guide](https://quantumwarp.com/kb/articles/87-netbeans/928-debugging-with-netbeans-xdebug-and-xampp-in-windows) and [another one](https://articlebin.michaelmilette.com/making-xdebug-work-with-netbeans-on-windows/) have excellent tips on using XDEBUG with NetBeans and other IDE's and include using it with a browser. They also have instructions on how to troubleshoot the default port it uses and how to differentiate if the default port (9000) used by XDEBUG is the issue such as it is blocked by your firewall and needs a rule to punch through it or the required lines in the php.ini aren't there or are incorrect, or some other reason. It is also recommended to use [this excellent tool](https://xdebug.org/wizard.php) as it creates the necessary php.ini lines you will need to replace what NetBeans puts there which is just a stub except for the line that loads the correct DLL. The two links before that one are for understanding XDEBUG and what must be done to install it properly plus excellent troubleshooting instructions. The php.ini lines both suggest are not needed usually so use the php.ini lines generated by the tool in the last link in this paragraph.

WAMP allows switching between 5.x and 7.x versions of PHP. To facilitate XDEBUG WAMP uses a different XDEBUG DLL in the php.ini that WAMP switches between when different PHP versions are used. WAMP current version allows switching between that last 5.x version and three 7.x versions. So, do not change what was installed by WAMP at the end of php.ini. Comment out all the lines underneath using a semicolon (;) in each php.ini used by WAMP for each PHP version it allows you to switch to which is very nice for let's say looking at latest Joomla! version, e.g Joomla! 4 alpha.

Not using the correct DLL is the most common error when using XDEBUG and WAMP sets this up correctly. The other error that is very common is not having the  [Visual C++ Packages](http://wampserver.aviatechno.net/?lang=en&prerequis=afficher) installed for the corresponding version of PHP that was compiled. Let WAMP do this for you. The previous link appears to be the best one to use for a comprehensive installation of WAMP that is a one-page-stop for everything you need. Since there are many versions of WAMP, although you should be using the current one, it will not hurt to install all of the Visual C++ Packages. It takes some time and you must install the 32 and 64 bit versions and I suggest doing it in date order starting with the earliest and ending with the latest. Read through the page completely so you install everything that is required. Follow all the recommendations that are also on the page.

You can install all of the Visual C++ Packages as you will have then have whatever version of the package is needed for whatever version you have of PHP. Do not worry that two are French. They work fine but you may need to be sure you click the OK button instead of Cancel as they are in French. Other than that all else on the page installs in English. The dependency the PHP version has with each Visual C++ Package version depends on the version of the Visual C++ Package that was used to compile the PHP version. Like anything worth the effort, do the work and read the information in the sites I have mentioned previously.

Often, XDEBUG will work if you just install it and let the installation took care of everything. Try doing that first and if everything works correctly you have the right Visual C++ Package installed and php.ini had the correct XDEBUG section that works with it. If you switch PHP versions and it stops working then you will need to ensure the environment is set up correctly for that version. This will not occur if you install all the Visual C++ Packages 32 and 64 bit. But it seems like many have issues with it as they depended on the install to do everything, including their environment, despite switching to another version of PHP.

XAMPP will install XDEBUG without much effort from you but WAMP is a much better environment to work in. The same applies for LAMP and MAMP. It is beyond the scope of this manual to go into Linux and Mac operating systems also but the same concepts apply and many of the links also refer to these operating systems.

It should be mentioned for those wishing to take the quick path you can browse com_demo_v2_0_0__J3.zip directly using Windows File Explorer as one example and skim through the tree and files without extracting it. However, this is a [Joomla! component install package](https://docs.joomla.org/File_Structure_and_Naming_Conventions) so it will not match the directory structure. If you are familiar with the Joomla! installation package requirements and structure this should not be a problem. For some, this is all they require, especially if they are very experienced PHP developers, have used the Joomla! API extensively and found JCB was not very difficult to learn by using the JCB Component Builder after it is installed, plus browsing through its code.

If you have not reached this level yet, creating the text file and performing the same analysis done here is an excellent exercise. Do the same for your own components and when ready, import the more complex JCB freely distributed components into JCB and do the same. Make notes in your text file as you browse through the directories and files on your development site for later review or revisiting concepts that perhaps were not very clear at the time. Follow along as you go through the directory tree on your system. Locate and open the files in each one shown below and view its contents. Good study habits will enable you to progress quickly to become an advanced developer of Joomla! components built using the MVC paradignm, JCB and the Joomla! API. It, along with the other tools mentioned here, allows you to save a lot of time, develop more components and most importantly, adhere to the [MVC paradigm](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) which is a time-saver in itself.

Beneath the directory structure and files presented next you will find a short explanation of their relation to the component, the areas of the JCB component that builds each and JCB's interaction with the Joomla! API. You'll see how JCB reuses and extends Joomla!'s abstract base classes, including their methods and properties to implement the many features and functions built into JCB which are utilized by you while building a component. As you peruse the directory structure and files, links are available allowing you to quickly go to the explanatory text below the directory structure for that file, including a reference to where in JCB it originated from and any interaction between JCB and the Joomla! API.
***
\administrator  
***
	\components	
		\com_demo	
			\assets	
				\css	
					\admin.css
					\dashboard.css
					\index.html
					\look.css
					\looks.css
				\images
					\icons
						\index.html
					\import.gif
					\index.html
				\js
					\admin.js
					\index.html

			\controllers
				\demo.php  
[demo.php](https://github.com/vdm-io/Joomla-Component-Builder/wiki/4a.-JCB-Demo-Component-Directory,-Folders-and-Files#administratorcomponentscom_democontrollersdemophp)  

				\import.php  
[import.php](https://github.com/vdm-io/Joomla-Component-Builder/wiki/4a.-JCB-Demo-Component-Directory,-Folders-and-Files#administratorcomponentscom_democontrollersimportphp)  

				\index.html  

				\look.php  
[look.php](https://github.com/vdm-io/Joomla-Component-Builder/wiki/4a.-JCB-Demo-Component-Directory,-Folders-and-Files#administratorcomponentscom_democontrollerslookphp)  

				\looks.php  
[looks.php](https://github.com/vdm-io/Joomla-Component-Builder/wiki/4a.-JCB-Demo-Component-Directory,-Folders-and-Files#administratorcomponentscom_democontrollerslooksphp) 

			\helpers
				\html
					\batch.php
					\index.html
				\PHPExcel
				\demo.php
				\headercheck.php
				\index.html
				\PHPExcel.php
			\language
				\en-GB
					\en-GB.com_demo.ini
					\en-GB.com_demo.sys.ini
					\index.html
				\index.html
			\layouts
				\look
					\details_above.php
					\details_fullwidth.php
					\details_under.php
					\index.html
					\metadata.php
					\more_left.php
					\more_right.php
					\publishing.php
				\batchselection.php
				\index.html
			\models
				\fields
					\index.html
				\forms
					\index.html
					\look.js
					\look.xml
				\rules
					\index.html
				\demo.php
				\import.php
				\index.html
				\look.php
				\looks.php
			\sql
				\updates
					\mysql
						\1.0.5.sql
						\index.html
					\index.html
				\index.html
				\install.mysql.utf8.sql
				\uninstall.mysql.utf8.sql
			\tables
				\index.html
				\look.php
			\views
				\demo
					\tmpl
						\default.php
						\default_main.php
						\default_vdm.php
						\index.html
					\index.html
					\view.html.php
				\import
					\tmpl
						\default.php					
						\index.html					
					\index.html
					\view.html.php
				\look
					\tmpl
						\edit.php
						\index.html
					*\index.html
					\submitbutton.js
					\view.html.php
				\looks
					\tmpl
						\default.php
						\default_batch_body.php
						\default_batch_footer.php
						\default_body.php
						\default_foot.php
						\default_head.php
						\default_toolbar.php
						\index.html
				\index.html
				\view.html.php  

***
\components  
***
	\com_demo
		\assets
			\css
				\index.html
				\look.css
				\looking.css
				\looks.css
				\site.css
			\images
				\index.html
			\js
				\index.html
				\site.js
			\index.html
		\index.html
		\controllers
			\index.html
			\look.php
		\helpers
			\category.php
			\demo.php
			\headercheck.php
			\index.html
			\route.php
		\language
			\en-GB
				\en-GB.com_demo.ini
				\en-GB.com_demo.sys.ini
				\index.html
			\index.html
		\layouts
			\look
				\details_above.php
				\details_fullwidth.php
				\details_under.php
				\index.html
				\metadata.php
				\more_left.php
				\more_right.php
				\publishing
			\index.html
		\media
			\css
				\index.html
			\images
				\index.html
			\js
				\index.html
			\uikit-v2
			\index.html  

		\models
			\forms
				\index.html
				\look.js
				\look.xml
			\index.html
			\look.php
			\looking.php
			\looks.php
		\views
			\look
				\tmpl
					\edit.php
					\index.html
				\submitbutton.js
				\view.html.php
			\looking
				\tmpl
					\default.php
					\index.html
				\index.html
				\view.html.php
			\looks
				\tmpl
					\default.php
					\default.xml
					\index.html
				\index.html
				\view.html.php

		\controller.php  
		\demo.php  
[demo.php](https://github.com/vdm-io/Joomla-Component-Builder/wiki/4a.-JCB-Demo-Component-Directory,-Folders-and-Files#com_demodemophp)  

		\index.html  
		\router.php
***
Always keep in mind, JCB is doing most of the tasks related to items below referring to Joomla directories, files, classes, methods and properties. You do not have to, for example, put an index.html file in the root of every directory; you are not required to add the check for direct access to the file; you do not have to write code for the admin or site views unless you extend JCB with your own custom code.

Some of the links below and seen previously in this document may be outdated and many Joomla! classes in use have early origins and are stated as such in the documentation. Locations of class files vary by release, and finding them and reviewing the code within each is made a bit more elusive with Joomla! 4 namespace changes but the standardization is worth it. There is current backwards compatibility and hence, lists of aliases do exist as seen next.

There is a class map of aliases for classes that do not conform to Joomla 4! namespace naming convention. When writing your own components, this file should be looked at:  
* \libraries\classmap.php  

The path on the right has the current locations along with the new standard naming convention aliased to it on the left. There are a few more areas where this occurs that is included below the list. Take a look at this example that calls a class method:  
* JLoader::registerAlias('JControllerLegacy', '\\Joomla\\CMS\\MVC\\Controller\\BaseController', '5.0')  

The physical path in Joomal! version 3.8.12 is:
* \libraries\src\Application\BaseController.php

The Joomla! class in the file in this example is named BaseController which extends JObject.  
***
Note, the following applies in general for any component:  
**index.html**  
File containing one line of HTML that causes the background of the page to be white which blocks the directory view. Must be in root of each folder.  
 
**All Joomla class files must begin with this code:**  
// No direct access to this file  
defined('_JEXEC') or die('Restricted access');  
***  
## \demo.php  
Sign in as a Super Administrator to the admin area. JCB's Editing the Site View in the admin area of the site is where you add the code for the site view entry point for the JCB Demo component; its path is /demo.php. This code has been inserted for you. You will need to supply code for your own components and the code in the JCB Demo component provides the basic elements for any component allowing CRUD (Create, Read, Update Delete) on database table records, in this case, look.

Super Administrator can:
* Login to admin as super administrator and create a look.
* Add a registered user.
* Create a Joomla! menu item for the demo component looks, access should be registered.
* Ensure when creating a look for a registered user the look ownership is changed to the one who should own the look, if applicable. Otherwise, they will not be able to view or edit it from the site area.  
 
Registered Users can:
* Edit the look record in the demo_look table, reusing the adminForm form to do so. To display, the registered user id of the logged in user must match the created_by value in the record.
* Login as the registered user and select the looks option from the main menu.
* Observe the site view looks displays with the Name and Description of the registered user's look and an edit toolbar underneath.
* Click the edit toolbar and display the admin view look, displaying only the buttons representing the form actions defined for that user group which are Save, Save and Close, Close.
* Click the More button, enabled when the record was entered by the Super Administrator using the admin area of the site. This allows the Registered User to access additional fields on the form.

Editing the Admin View - System Name Look - Settings - Permission Implementation - Settings  
Only if you add permissions here will this view have permissions. [Please watch this tutorial](https://youtu.be/CdSKSCTzmRA?list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=6m19score.edit) for more info.

By default, the site view looks is not authorized for any user besides the Super Administrator although it displays on the main menu after logging in to a Registered User and above. If access is given in Joomla!'s ACL to the JCB Demo component for the Registered Group of Joomla! users, the view will display after logging in as a Registered User. For this to happen, the Joomla! ACL must allow access to the component as follows using the admin area main menu option:  

Components - Demo - Looks - Options - Permissions tab - Registered  
* Looking (Site) Access Allowed  
* Looks Access  	Allowed  
* Looks (Site) Access  	Allowed  
* Looks Edit Own  	Allowed  

The first option only allows access to the site. The view will display a look but that's all. The second allows access and therefore all looks will display and can be accessed (but not edited) as long as the third access is also granted. The fourth allows editing the look if the user's id matches the one in the look_demo table. More details about the Joomla! ACL on this can be seen in [this video](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=36).

Be sure to add a filter using the admin area of the site, main menu option by selecting:

Components - Component Builder - Dynamic Gets - Looks - Tweak  
* Where Table Key a.created_by equal = $this->user->id

This Tweak is applied to to the Dynamic Get in JCB for the Demo component:
* Site view looks - Dynamic Get - getListQuery

It extends it to only include records from the table that were created by the user having the same id as the current user. This is available from: 
* Site view looks - $this variable - user id form element

The change takes effect once you use JCB to compile the component and install it again using the Joomla! extension installer. The same Tweak is required in:
* Site view looking - Dynamic Get - getItem.  

Doing the above also ensures only certain actions are allowed for certain users. In our case, a Registered User should only be allowed to:  
* Save  
* Save and Close  
* Close  

The filter allows them to edit only their own look records in the demo_look table. If you need to see all of the demo records, using all the edit features and available buttons, and more, login to the site area as a Super Administrator to see all records in the admin view. If you perform the previous instructions a Registered User's actions will be restricted to display only the following buttons in the looking view:  

* Save button  
* Save and Close button  
* Close button  

If you add more permissions such as Create, two more buttons will appear, Save and Copy plus Save and New. You can remove buttons by changing the permissions back to inherited which should then display as not allowed. Remember they must have been defined first, as mentioned previously, to appear in the list of Permissions. After adding the appropriate actions and permissions to the view and compiling it, the changes will take effect. Note, you can change the JCB Demo component Joomla! ACL permissions and see the effect since components do not need to be compiled by JCB for these settings to change since the change is being done within Joomla!.

Continuing with the edit functionality:  
* Edit the look record in the demo_look table. It is important you understand this is reusing the admin view look, edit look. If you use Chrome Developer tools to view the page source and go to the form tag you will see it is using the admin form in the looks view:  
<form action="/comdemo/index.php?option=com_demo&amp;view=looks&amp;Itemid=104" method="post" name="adminForm" id="adminForm">  

* The registered user id of the logged in user must match the created_by value for it to display and allow the user to edit the record. Use the Published tab in any Joomla! to change this for a Joomla! User for example to ensure they are the creator of a specific look record in the demo_look table.  

The above still allows all user types except public and guest user groups to view all looks, whether they created them or not. To restrict the looks view to only list records owned by a specific user, besides the changes to the Joomla! ACL, one must filter the look records in the demo_looks table by the created_by column. Note, these will take effect without compiling the JCB Demo and other components built using it. The reason is the Joomla! ACL or the global options permissions of the JCB Demo component are being changed for Joomla!'s Registered User Group and not individual permissions within the JCB component. The latter allows for granularity but normally you should use default values whenever possible. As granularity increases so does required maintenance.

* First, login as the registered user and select the looks option from the main menu.  
* The site view looks displays with the Name and Description of the registered user's look and an edit toolbar underneath.  

Then, click the edit toolbar and display the admin view look, displaying only the form actions defined for that user group:  

* Save  
* Save and Close  
* Close  

The role of libraries should be mentioned at this point since they format the elements seen in all views, templates, and layouts. The code in the JCB Demos's looking view allows one to:  
* Look - using the looking site view at a  
* Look - using the look site view using  
* Looks - which is the site view that lists looks

The admin view look allows editing in the admin and site areas. All views use the demo_look table records which stores all look records.

It's vital to understand the UIkit library and gain some familiarity with [FooTable](https://fooplugins.github.io/FooTable/docs/getting-started.html) and [Bootstrap](https://getbootstrap.com/docs/4.1/getting-started/introduction/) since JCB implements them. UIKit components are used quite a bit in the JCB freely distributed components. To construct a view in JCB, you must familiarize yourself with it. It has a small but powerful footprint. It is suggested to have the following link close by in your browser tabs as you code your site views using its button component as the example.

https://getuikit.com/docs/button

JCB uses the following version of UIkit:
/*! UIkit 2.27.4 | http://www.getuikit.com | (c) 2014 YOOtheme | MIT License */

UIkit JavaScript for the button component is located at:
\media\com_componentbuilder\uikit-v2\js\components\button.js

A button is called a component in the UIkit and there are many others that encapsulate client side code into more generalized functions that can be treated as objects with individual methods and properties. They are identified with the prefix "ui-". An example is the uk-comment class found in the UIkit CSS file located at:  
* \media\com_componentbuilder\uikit-v2\css\uikit.css  

JCB adds this and other classes by adding the UIkit files to:  
* \media\com_demo\uikit-v2 in the Joomla! Demo installation package.  

For details see the link and list of UIkit components and code required to implement them as was done below in the area in JCB labeled Site View's Default View. Much of the code is straightforward PHP. Use the view's $this reference to the current object to get the value of an element on the page. For example, the template for the JCB Demo component exposes the logged in user's id in $this. The value of the id is obtained using $this->user->id and a good explanation of what $this is can be found [here ](http://www.php.net/manual/en/language.oop5.basic.php). Other values are also available and observe the code reuse of Joomla! API classes, plus standard HTML. As seen in the example, JCB also uses tags like ComponentHelper.  
* Looking Site View  

The code to do this is located in JCB in the view prefaced by:  
* Custom Script - Add PHP (after getting the items) * - Yes - PHP getItems Method - Target (array) $items values *  

## [JCB - Editing the Site View](/administrator/index.php?option=com_componentbuilder&view=dynamic_get&layout=edit&id=36)  

Next, we look at demo.php in the root of the JCB Demo component directory and step through its contents, summarizing the actions that lines of code within each perform including the locations of class files behind each.
- [Add unobtrusive JavaScript support to keep a tab state.](https://api.joomla.org/cms-3/classes/JHtmlBehavior.html#method_tabstate)  
\libraries\cms\html\behavior.php
- [Get a document object and set the component css/js.](https://api.joomla.org/cms-2.5/classes/JFactory.html#method_getDocument)  
\libraries\src\Factory.php  
\components\com_demo\assets\css\site.css  
\components\com_demo\assets\js\site.js  
- [Require helper files.](https://api.joomla.org/cms-3/classes/JLoader.html#method_register)  
\libraries\Joomla\JLoader.php
\helpers\demo.php  
\helpers\route.php  
- [Import joomla controller library](https://docs.joomla.org/J2.5:Developing_a_MVC_Component/Basic_backend#Basic_backend)  
\libraries\Joomla\Controllers\controller.php  
- Get an instance of the controller prefixed by demo  
[Method to get a single controller instance.](https://api.joomla.org/cms-2.5/classes/JControllerLegacy.html#method_getInstance)  
- Perform the request task. Initially, this is the default.  
[Perform the request task.](https://api.joomla.org/cms-2.5/classes/JFactory.html)  
[Get the request.](https://docs.joomla.org/Retrieving_request_data_using_JInput)  
- Redirect if set by the controller.