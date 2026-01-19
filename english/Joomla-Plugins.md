# JCB Joomla Plugins

## What Are Joomla Plugins?
**Joomla Plugins** created in JCB are event-driven extensions that allow you to inject custom logic at key points in the Joomla application lifecycle. They are perfect for scenarios such as:

- Command-line (CLI) tasks
- Scheduled cron operations
- Authentication filters
- Data transformations or validation layers
- System-level integrations with external services

Each plugin can bundle PHP classes, helper libraries, language strings, and the plugin XML manifest. JCB also lets you attach custom fields so that the plugin ships with configuration parameters a site maintainer can adjust directly in Joomla.

---

## How Plugins Fit Into Your Component
When you link a plugin to a component inside JCB, that plugin is compiled whenever the component is built. The packaging engine automatically:

1. Collects the plugin files, helper classes, and language strings.
2. Generates any configuration fields you defined for the plugin.
3. Ships the compiled plugin alongside your component install package.

This tight coupling means you can guarantee that background automation, authentication hooks, or API synchronisation logic are distributed with the exact component version that needs them—without touching Joomla core files.

> **Tip:** Use plugin parameters to expose switches or credentials that should remain editable after deployment while keeping the implementation details inside the compiled code.

---

## Event Triggers and Execution Contexts
Joomla plugins subscribe to specific events (for example, `onUserLogin`, `onContentPrepare`, or CLI callbacks). Within JCB you can:

- Declare the events your plugin should listen to and implement the corresponding methods.
- Decide whether the plugin should run in the **site**, **administrator**, or **CLI** application by configuring the plugin group and context.
- Reuse shared helper classes from the component, ensuring consistent business rules across web and automation entry points.

Because plugins run independently of Joomla's MVC views, you can place business logic, integrations, or scheduled jobs directly in the event listeners while leaving the component controllers focused on request handling.

---

## Building, Testing, and Shipping Plugins in JCB

### During Development
- Start by scaffolding the plugin in JCB, then add your PHP logic and helper includes.
- Use JCB's field manager to define configuration options that appear in Joomla's plugin editor.
- Trigger plugin events locally using Joomla's test tools or CLI entry points to confirm the logic behaves as expected.

### At Compile Time
- Include the plugin in your component export so that every build ships a current copy.
- Verify the generated plugin XML manifest lists all files, language strings, and configuration fields.
- Check that helper classes referenced by both the component and plugin are autoloaded correctly.

### After Installation
- Enable the plugin from Joomla's Plugin Manager and adjust any parameters you exposed during development.
- Monitor Joomla's logs or CLI output to verify that your event listeners run without errors.

---

## Versioning and Sharing
When you need to update Joomla Plugins in any JCB project:

- Select the plugin(s) you wish to refresh.
- Click **"Reset"** to pull the latest version from this repository.
- Or **Fork** this repository and point your JCB instance to your fork.

This ensures your plugins are version-controlled and up-to-date, while still allowing full customization per project.

> Plugins are an essential part of a robust Joomla architecture—offering silent, background-driven functionality with full JCB integration.

---

## Documentation Checklist
To help collaborators understand how plugins complement a component, make sure your project notes include:

- A summary of each plugin, its event triggers, and the problem it solves.
- Any configuration parameters, default values, or required credentials.
- Dependencies on helper classes or external services.
- Testing steps (CLI commands, cron frequency, or user flows) that exercise the plugin.

Keeping these points close to the component's main documentation ensures new developers can immediately see how automation and event-driven logic accompany the visible features of your build.
