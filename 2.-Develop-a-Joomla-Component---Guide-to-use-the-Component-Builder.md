# Introduction
## What will this guide cover?
This guide will continuously grow and try cover the complete building process of a component.

## What are we going to build?
We're going to build an archive component, so that f.e. a museum can manage their objects and know where everything is. The component will have the following features:
* Object: Add, manage, delete

## Prerequisites
First of all, you will need the Component Builder installed and ready to use.

## Tips and tricks
Here some important things to think about when using the _Component Builder_:
* If there are numbers used, start with 1 and not with 0. You can have functionality problems, if you don't think about that point. And they can become some kind of annoying to resolve.

# Our first component
## A new component
To start off, we begin by making a new component.
* Go to `Component Builder --> Joomla Components --> New`
  * Tab Details
    * System name `Archiver` (This is the system name, used by the component builder
    * Name `Archiver` (This is the component name)
    * Name in code `Archiver` (This is the component name used in the code)
    * Version `0.0.1` (This is the component's version. This will be used for the update process)
    * Debug (line numbers) `No`
    * Custom Code Placeholders `No`
    * Use View Version & Date `No`
    * Short description `Archiver helps to get away with all archive objects.`
    * Copyright `Copyright (C) 2017. All Rights Reserved`
    * Company name `Component Builder Beginner`
    * Author `My Name`
    * Email `iForgotMyEmail@oh-no.com`
    * Website `https://www.find-me-here-or-not.ch`
    * Add License (whmcs) `No`
    * License `GNU/GPL Version 2 or later - http://www.gnu.org/licenses/gpl-2.0.html` 

  * Tab `Libs & Helpers`
    * Set everything to `No` 
* Save and close

## Compiler
To check what we did and how our component works and looks, we want to compile our component and install it.
* Go to `Component Builder --> Compiler`
  * Add to Git Folder `No`
  * Select Component `Archiver`
  * Click on `Compile Component`
  * Click on `Install`

## The first admin view
As you can see, until now, we're not able to install the component. The problem is that until now, we don't have any views connected to our component. So let's start to resolve this issue and build our first admin view.
* Go to `Component Builder --> Admin Views --> New`
  * System name `Archiver - Object` ( I like to name my views with their component name in front. Like that, I can easily distinguish between my admin views I'd like to use and at the same time, I am forced to have individual views for each component. So each component has it's own adaption to a certain situation.)
  * Name (single record) `Object`
  * Name (list of records) `Objects`
  * Short Description `The object view collects all object data`
  * Click on `Fields --> Add`, add the title and alias field like shown in this picture, and click on `Save`.
[img]
  * Save the admin view

## Add an admin view to our component
* Go to `Component Builder --> Joomla Components` and select `Archiver`
  * Tab `Settings`
    * `Admin Views --> Add` (_Important: If it doesn't load with all options chosen, close it and open it again._)
      * Select `Archiver - Object`
      * Enter it like shown on this picture, `Save`
[img]

## Check our first component (V. 0.0.1)
* Compile and install (See [Chapter Compiler](#compiler))
As you can see, the installation process now worked as we connected our first admin view to our component. You're able to use your first component. 

## References

# Our first update
As we continue our component, we will often have to adapt our tables to new fields, remove old unused fields and so on. To easily do that, and for the reason that we can update our components instead of always re-installing it with the problem of losing or always remembering to backup our data, we have to add that information to component builder.

## Preparation
To continue with the next step, we repeat everything mentioned to make a new admin view (Starts here: [The first admin view](#the-first-admin-view) ). This time we call the view `Place` instead of `Object`. **Don't compile yet!**

## Adjust the component settings for the update
Now as we added a new view, we have to adjust our component.
* Go to `Component Builder --> Joomla Components` and select `Archiver`
  * Add the new view if you haven't done it yet. Pay attention for the load of all fields. If they're not set, reopen the fields modal.
  * Change the current version to `0.0.2`
  * Click on `Add Update SQL`
  * Make a new entry for version 0.0.1 with the following content:

    CREATE TABLE IF NOT EXISTS `#__archiver_place` (  
        `id` INT(11) NOT NULL AUTO_INCREMENT,  
        `asset_id` INT(10) unsigned NOT NULL DEFAULT 0 COMMENT 'FK to the #__assets table.',  
        `alias` CHAR(64) NOT NULL DEFAULT '',  
        `title` CHAR(64) NOT NULL DEFAULT '',  
        `params` text NOT NULL DEFAULT '',  
        `published` TINYINT(3) NOT NULL DEFAULT 1,  
        `created_by` INT(10) unsigned NOT NULL DEFAULT 0,  
        `modified_by` INT(10) unsigned NOT NULL DEFAULT 0,  
        `created` DATETIME NOT NULL DEFAULT '0000-00-00 00:00:00',  
        `modified` DATETIME NOT NULL DEFAULT '0000-00-00 00:00:00',  
        `checked_out` int(11) unsigned NOT NULL DEFAULT 0,  
        `checked_out_time` DATETIME NOT NULL DEFAULT '0000-00-00 00:00:00',  
        `version` INT(10) unsigned NOT NULL DEFAULT 1,  
        `hits` INT(10) unsigned NOT NULL DEFAULT 0,  
        `access` INT(10) unsigned NOT NULL DEFAULT 0,  
        `ordering` INT(11) NOT NULL DEFAULT 0,  
        `metakey` TEXT NOT NULL DEFAULT '',  
        `metadesc` TEXT NOT NULL DEFAULT '',  
        `metadata` TEXT NOT NULL DEFAULT '',  
        PRIMARY KEY  (`id`),  
        KEY `idx_access` (`access`),  
        KEY `idx_checkout` (`checked_out`),  
        KEY `idx_createdby` (`created_by`),  
        KEY `idx_modifiedby` (`modified_by`),  
        KEY `idx_state` (`published`),  
        KEY `idx_title` (`title`),  
        KEY `idx_alias` (`alias`)  
    ) ENGINE=MyISAM AUTO_INCREMENT=0 DEFAULT CHARSET=utf8;
  * Save the component

## Check our first component update (V. 0.0.2)
* Compile and install (See [Chapter Compiler](#compiler))
As you can see, the installation process now worked as we expected, as we added the update for our database. Without that part, you wouldn't be able to use the place's view, as there weren't any table.

## References

