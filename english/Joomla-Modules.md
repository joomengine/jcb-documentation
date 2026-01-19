# JCB Joomla Modules

Joomla Component Builder (JCB) can compile fully fledged modules alongside your components. Use this primer to understand how they slot into your build workflow, what features they inherit from Joomla, and how JCB keeps them versioned with the rest of your project.

---

## What Are Joomla Modules?

**Joomla Modules** built in JCB are standalone display blocks that integrate directly into your component and render content into predefined module positions within Joomla.

Each module is compiled alongside the component it's linked to. Modules are commonly used for:

- Listing items or statistics on the frontend
- Admin dashboard panels or notices
- Dynamic UI widgets and structured content rendering

Modules in JCB support:

- Fields (for admin-configurable parameters)
- Custom Code (shared logic or snippets)
- Custom Scripting (PHP logic rendered in module output)
- Component-aware compilation
- Joomla version targeting (3.x / 4.x / 5.x)

They follow the native Joomla module structure and install as part of the component.

---

## Why Are Modules Useful in JCB?

Modules offer reusable, positionable functionality across your Joomla site:

- Provide compact dynamic views tied to component data
- Accept field-based parameters to drive module behaviour
- Include embedded PHP or Custom Code logic
- Designed to be lightweight and fast-loading
- Automatically compiled with their linked component

Treat modules as portable UI widgets. Because they live inside the component definition, they inherit its versioning, update channels, and distribution workflow.

---

## Versioning and Sharing

When you need to update Joomla Modules in any JCB project:

1. Select the modules to update.
2. Click **Reset** to pull the latest version from the source repository, or **Fork** to customise while keeping upstream changes accessible.
3. Recompile your component so the refreshed modules ship in the next installable package.

This ensures maintainability while still allowing full customization.

> JCB modules are tightly integrated with your components — making it easy to deploy dynamic widgets, status panels, and reusable display logic across your Joomla site.

---

## Where Modules Fit in the Workflow

- **Plan modules alongside views:** define which component data needs to surface in module positions and what configuration fields administrators require.
- **Reuse shared logic:** reference Custom Code blocks or helper methods so modules mirror the behaviour of related site views.
- **Target the correct Joomla version:** align module settings with the component's release targets to avoid compatibility drift.
- **Document placement guidance:** note recommended module positions in your component README or changelog so implementers know where to publish them.

---

## Index of Joomla Module Resources

Use these entries as you expand your module library:

- _Coming soon:_ individual module walkthroughs will be listed here as they are transcribed and edited.
- [Joomla Components in JCB](./Joomla-Components.md) – shows how modules ship together with the rest of the component bundle.
- [JCB Packaging Engine](./JCB-Packaging-Engine.md) – explains how modules are bundled into the installable package during compilation.

Check the repository regularly for new module examples you can reset or fork into your projects.
