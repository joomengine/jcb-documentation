# JCB! Joomla Plugins

## What Are Joomla Plugins?
**Joomla Plugins** created in JCB are event-driven extensions that allow you to inject custom logic at key points in the Joomla application lifecycle.

These plugins are automatically built when linked to a component and compiled. They support both backend and CLI contexts, and are ideal for scenarios like:

- Command-line (CLI) tasks
- Scheduled cron operations
- Authentication filters
- Data transformation or validations
- System-level integrations

Each plugin can contain raw PHP, helper classes, and plugin XML configuration. Fields may also be used to generate configurable plugin parameters.

---

## Why Are Joomla Plugins Useful in JCB?
Joomla Plugins extend the runtime behavior of your component:

- Hook into Joomla's native event system
- Perform background logic or validations
- Execute scheduled tasks via CLI
- Access Joomla core APIs without modifying core files

Plugins are automatically compiled with the component they are linked to, ensuring that any custom logic tied to system events is deployed alongside your component.

They are excellent tools for modular logic injection, background automation, and clean separation of concerns.

---

## Site Views and Plugin Events
While plugins run independently of Joomla's MVC views, the requests that trigger them usually originate from **Site Views**. Every public-facing interaction—whether a visitor loads a page, submits a form, or triggers an AJAX endpoint—passes through the component's site controllers before firing Joomla's global events. Mapping Site Views carefully therefore helps you:

- Understand which plugin events will run during specific frontend workflows.
- Decide where to expose configuration switches or parameters that toggle plugin-powered behavior.
- Keep frontend output and backend automation in sync because both are compiled from the same component definition.

When documenting a component, pair each Site View with the plugin events it can raise (for example, `onContentPrepare` for rendered articles or `onUserLogin` for access flows). This practice gives collaborators a single diagram that links **what a visitor sees** with **what the plugin automates**.

---

## Versioning and Sharing
When you need to update Joomla Plugins in any JCB project:

- Select the plugin(s) you wish to refresh.
- Click **"Reset"** to pull the latest version from this repository.
- Or **Fork** this repository and point your JCB instance to your fork.

This ensures your plugins are version-controlled and up-to-date, while still allowing full customization per project.

> Plugins are an essential part of a robust Joomla architecture — offering silent, background-driven functionality with full JCB integration.

---

## Index of Joomla Plugins
Use the component dashboard to see which plugins are linked to each build, then document any bespoke behavior alongside the relevant Site Views so new contributors understand both halves of the workflow.
