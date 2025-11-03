# Joomla Components in JCB

Understanding how Joomla Component Builder (JCB) treats a **component** makes the rest of the toolchain easier to follow. This overview explains the role of a component, the assets it gathers, and how it anchors collaboration workflows.

---

## What is a JCB component?

A component is the **top-level bundle** that JCB compiles into an installable Joomla extension. It acts as the central container that connects every entity you configure elsewhere in the builder.

A component can include:

- **Admin Views** – data tables, edit forms, ACL rules, and toolbar actions that power the backend experience.
- **Site Views** – list and item layouts that ship to the frontend.
- **Custom Admin Views** – bespoke management screens that sit outside the CRUD scaffolding.
- **Modules and Plugins** – optional extensions that are packaged alongside the main component; document how their event triggers align with Site View flows using the [JCB! Joomla Plugins](./Joomla-Plugins.md) notes.
- **Custom Code** – helper methods, class overrides, and reusable snippets injected into the generated output.
- **Files and Folders** – media assets, scripts, language packs, or other resources that need to be copied into Joomla's filesystem.
- **Database Tweaks** – schema updates, install/upgrade SQL, and demo data.
- **Helper Classes** – PHP utilities that other parts of the component can call.
- **Global Configuration** – the XML parameters that surface in Joomla's component options screen.
- **Placeholders and Overrides** – automated replacements and layout overrides to keep code dry.
- **Dashboards** – dynamic overview screens for administrators.
- **Routing Rules** – site and administrator routing definitions.
- **Version Targets** – Joomla 3/4/5 compatibility settings and packaging instructions.
- **Documentation Assets** – README files, wikis, changelogs, or authorship metadata that help teammates orient themselves.

When you compile, JCB assembles these moving parts into a single versioned package. Every other entity you create in JCB eventually belongs to one or more components.

---

## Why components are central

Components define the boundaries of your Joomla extension. Within a component you decide:

- **Packaging** – which views, modules, plugins, and helpers are installed together.
- **Database lifecycle** – how tables are installed, migrated, and seeded.
- **Filesystem layout** – where assets land during installation.
- **Compatibility** – which Joomla versions and branches the package supports.
- **Distribution flow** – update servers, changelogs, versioning, and authorship metadata.
- **Language coverage** – which language files and translation overrides are included.
- **Collaboration details** – Git repository links, author information, and notes that help a team coordinate their work.

> Think of the component as your **single source of truth**. Fields, views, layouts, and snippets only become a coherent extension once you bind them to a component and compile.

---

## Version control and collaboration

Components participate fully in JCB's synchronisation tooling:

- **Branch-aware configuration** lets you prepare different outputs for Joomla 3, 4, or 5.
- **Reset and init workflows** help teams clone baseline configurations and keep forks aligned.
- **Component-level versioning** records changelog entries so you can track what changed between releases.
- **Forking and sharing** make it easy to maintain white-label variants or community editions from the same source definition.
- **Update pushes** allow maintainers to send improvements upstream or distribute them across shared repositories.

Because components encapsulate every dependency, they are ideal for distributed teams, client projects, and open-source releases alike.

---

## What to read next

Use this page as a hub before diving into the deeper tutorials:

- [Component Structure and MVC Implementation](./Component-Structure-and-MVC-Implementation.md) – map the generated code to Joomla's architecture.
- [Component Settings Overview](./Component-Settings-Overview.md) – understand global options, version targets, and packaging metadata.
- [Adding Admin Views to a Component](./Adding-Admin-Views-to-a-Component.md) – define the data tables and backend screens that live inside your component.
- [Adding Site Views to a Component](./Adding-Site-Views-to-a-Component.md) – surface data to the frontend once the component structure is in place.
- [JCB! Joomla Plugins](./Joomla-Plugins.md) – connect Site View interactions to the plugin automation bundled with your component.
- [JCB Packaging Engine](./JCB-Packaging-Engine.md) – learn how JCB builds the installable archive after you configure your component.

---

## Index of component-related topics

- [Adding Custom Admin Views to a Component](./Adding-Custom-Admin-Views-to-a-Component.md)
- [Component Scripts](./Component-Scripts.md)
- [Component Settings](./Component-Settings.md)
- [Develop a Joomla Component](./Develop-a-Joomla-Component---Guide-to-use-the-Component-Builder.md)
- [Developing with Joomla Component Builder](./Developing-with-Joomla-Component-Builder.md)
- [Dynamic File and Folder Inclusion Concept](./Dynamic-File-and-Folder-Inclusion-concept.md)
- [Global Settings of Component Builder](./Global-Settings-of-Component-Builder.md)
- [Proposed Collaborative Workflow in JCB](./Proposed-Collaborative-Workflow-in-JCB.md)

Bookmark this reference whenever you need to explain what “a component” means inside JCB to teammates or clients.
