# Introduction
## What will this guide cover?
This guide will continuously grow and try cover the complete building process of a component.

## What are we going to build?
We're going to build an archive component, so that f.e. a museum can manage their objects and know where everything is. The component will have the following features:
- Object: Add, manage, delete

## Prerequisites
First of all, you will need the Component Builder installed and ready to use.

## Tips and tricks
Here some important things to think about when using the _Component Builder_:
- If there are numbers used, start with 1 and not with 0. You can have functionality problems, if you don't think about that point. And they can become some kind of annoying to resolve.

# Our first component
## A new component
To start off, we begin by making a new component.
- Go to `Component Builder --> Joomla Components --> New`
  - Tab Details
    - System name `Archiver` (This is the system name, used by the component builder
    - Name `Archiver` (This is the component name)
    - Name in code `Archiver` (This is the component name used in the code)
    - Version `0.0.1` (This is the component's version. This will be used for the update process)
    - Debug (line numbers) `No`
    - Custom Code Placeholders `No`
    - Use View Version & Date `No`
    - Short description `Archiver helps to get away with all archive objects.`
    - Copyright `Copyright (C) 2017. All Rights Reserved`
    - Company name `Component Builder Beginner`
    - Author `My Name`
    - Email `iForgotMyEmail@oh-no.com`
    - Website `https://www.find-me-here-or-not.ch`
    - Add License (whmcs) `No`
    - License `GNU/GPL Version 2 or later - http://www.gnu.org/licenses/gpl-2.0.html`
[img]
  - Tab `Libs & Helpers`
    - Set everything to `No`
[img]
- Save and close

## Compiler
To check what we did and how our component works and looks, we want to compile our component and install it.
- Go to `Component Builder --> Compiler`
  - Add to Git Folder `No`
  - Select Component `Archiver`
  - Click on `Compile Component`
  - Click on `Install`

## The first admin view
As you can see, until now, we're not able to install the component. The problem is that until now, we don't have any views connected to our component. So let's start to resolve this issue and build our first admin view.
- Go to `Component Builder --> Admin Views --> New`
  - System name `Archiver - Object` ( I like to name my views with their component name in front. Like that, I can easily distinguish between my admin views I'd like to use and at the same time, I am forced to have individual views for each component. So each component has it's own adaption to a certain situation.)
  - Name (single record) `Object`
  - Name (list of records) `Objects`
  - Short Description `The object view collects all object data`
  - Click on `Fields --> Add`, add the title and alias field like shown in this picture, and click on `Save`.
[img]
  - Save the admin view

## Add an admin view to our component
- Go to `Component Builder --> Joomla Components` and select `Archiver`
  - Tab `Settings`
    - `Admin Views --> Add` (_Important: If it doesn't load with all options chosen, close it and open it again._)
      - Select `Archiver - Object`
      - Enter it like shown on this picture, `Save`
[img]

## Check our first component (V. 0.0.1)
- Compile and install (See [Chapter Compiler](#compiler))
As you can see, the installation process now worked as we connected our first admin view to our component. You're able to use your first component. 

## References
