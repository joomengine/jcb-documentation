# Using the JCB Demo Component During Local Development

## Overview

The official JCB demo package (`com_demo_v2_0_0__J3.zip`) is a full component blueprint that demonstrates how Joomla Component Builder (JCB) assembles administrator and site applications, language files, libraries, and installer scripts. Use it as a living reference while you build your own components: import the blueprint, review how each JCB area was configured, and study the compiled ZIP to see the generated MVC code and helper structures.

## Prerequisites and Recommended Tooling

Set up a lean environment before importing the demo component. Start with a clean Joomla installation that only includes JCB—skip installing the demo package through the Joomla installer so you can bring it in manually. The following tools mirror the setup used to compile the reference material:

- **Local stack with debugging support** – WAMP ships with Xdebug and lets you switch between PHP 5.x and 7.x, but any stack with native Xdebug integration works.
- **Integrated Development Environment (IDE)** – NetBeans offers built-in Xdebug integration, Git tooling, powerful search, and a tree view that makes browsing the generated component easier. VS Code or PhpStorm are suitable alternatives if you replicate the same capabilities.
- **Modern browser developer tools** – Chrome DevTools or Firefox Developer Edition provide JavaScript debugging, DOM inspection, and network tracing that complements the PHP debugging workflow.
- **Joomla diagnostics** – Enable Joomla’s debug mode for stack traces, language debug output, and SQL profiling when you troubleshoot runtime behaviour.

> 💡 If you are new to setting up a PHP debugging environment, review the [official Joomla workstation guide](https://docs.joomla.org/Setting_up_your_workstation_for_web_development) for additional options.

## Import the Demo Blueprint

1. Download the `com_demo_v2_0_0__J3.zip` package from the official JCB repository.
2. Inside JCB, open **Components → Import** and import the ZIP as a package. The import installs the component blueprint, its fields, and any reusable assets exactly as they were configured for the demo project.
3. Compile the demo component from JCB and install the resulting package in Joomla to generate the administrator and site applications.

> ✅ Importing the package directly inside JCB is the cleanest approach. Installing the ZIP via Joomla first creates a compiled component without the underlying blueprint and makes it harder to study how the component was built.

## Inspect the Component Inside JCB

After the import, explore how the blueprint is assembled:

- **Admin Views and Fields** – Review how each admin view maps directly to a database table, how list/edit layouts are generated, and which fields are marked as required. Pay special attention to the Sermons, Looks, and Preachers views because they showcase many-to-many relationships.
- **Site Views and Dynamic Gets** – Examine how list and item views reuse Dynamic Get queries. The demo illustrates both filtered queries and global “All” views that drop filters to return complete record sets.
- **Templates, Layouts, and Assets** – Open the Layouts and Templates tabs to see how reusable markup is version-controlled. Trace how placeholders and params feed template switches, grids, and table layouts.
- **Custom Code and Helpers** – Look at the helper classes, router helpers, and custom code areas to see where JCB injected snippets and how hashes track manual modifications.
- **Component Configuration** – Review the component’s config XML definition to understand how global parameters (such as toggles for list/table/grid layouts) control the frontend output.

Document any conventions you want to reuse in your own projects—naming standards, field prefixes, or reset/fork strategies translate directly to production builds.

## Explore the Compiled Package

Unzip the compiled component and inspect the directory tree with your IDE. Every folder maps back to a concept inside JCB:

| Location | Purpose |
| --- | --- |
| `administrator/components/com_demo` | Administrator MVC stack: controllers, models, tables, layouts, helpers, SQL updates, and dashboard templates. |
| `components/com_demo` | Site MVC stack with list and item views, assets, and routing helpers. |
| `media/com_demo` | Media assets (CSS, JS, and images) registered through the Assets manager. |
| `administrator/language/en-GB` & `language/en-GB` | Language strings compiled from the blueprint. |
| `libraries/vdm_io` (if present) | External library folders pulled in by the Files & Folders configuration. |

Within each MVC folder, compare the generated files to the settings you saw inside JCB. For example, the `administrator/components/com_demo/views/looks` folder contains:

- `view.html.php` – the controller for rendering the list view.
- `tmpl/default.php` and related layouts – markup tied to template selections in the blueprint.
- `models/looks.php` and `tables/look.php` – generated based on field definitions.

This cross-reference reinforces how JCB mirrors Joomla’s MVC conventions and how configuration choices manifest in the compiled code.

## Use Debugging and IDE Tooling Effectively

Efficient debugging closes the loop between blueprint and runtime component:

- **Single-step through requests** – Attach Xdebug to your IDE and step through controllers, models, and helpers while loading administrator pages. Use watches and breakpoints to inspect variable contents.
- **Trace database interactions** – Combine Joomla’s SQL debug output with IDE searches to locate where queries originate and how Dynamic Gets shape the statements.
- **Inspect JavaScript and CSS** – Use browser developer tools to profile AJAX requests, inspect DOM changes triggered by FooTable, and tweak CSS on the fly.
- **Search across the codebase** – IDE search and “find usages” features reveal where helper methods, language strings, and templates are referenced.

## Troubleshoot Xdebug Quickly

If Xdebug does not connect immediately:

1. Use the [xdebug.org wizard](https://xdebug.org/wizard.php) to generate the correct `php.ini` directives for your PHP version.
2. Confirm that the Visual C++ redistributables required by your PHP build are installed—WAMP’s installation guide lists every version you need. Install both 32-bit and 64-bit packages in chronological order when in doubt.
3. Verify that your firewall allows traffic on the configured Xdebug port (default `9003` in modern releases). Adjust IDE and PHP settings if you customise the port.
4. Restart your web server after every configuration change and test using a minimal PHP script to confirm the debugger is active before returning to Joomla.

## Key Takeaways

- The demo component is a reference implementation that demonstrates how JCB orchestrates Joomla’s MVC layers, asset management, and packaging automation.
- Import the demo via JCB so you retain the full blueprint alongside the compiled extension.
- Study both the configuration inside JCB and the generated PHP, XML, and layout files to understand how JCB maps definitions to code.
- Maintain a robust debugging toolchain—IDE integration, Xdebug, Joomla debug mode, and browser tools dramatically reduce the time spent diagnosing issues in compiled components.
