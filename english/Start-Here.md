# Start Here: Onboarding Guide for Joomla Component Builder

## What this page does

Joomla Component Builder (JCB) packs years of community knowledge into one documentation set. This page curates the most important links and concepts so that a newcomer can move from “I have Joomla experience” to “I can ship a JCB component” without getting lost in the library. Use it together with the [Home](./Home.md) index: Start Here gives you the narrative path, while Home provides a chapter-by-chapter reference.

---

## Step 1 – Understand the landscape

1. **See the big picture of a component** so you understand what JCB ultimately packages. [Joomla Components in JCB](./Joomla-Components.md) explains how every view, helper, script, and configuration ends up inside the compiled extension.
2. **Review Joomla's MVC structure** to see how administrator and site applications mirror each other, how controllers, models, and views are named, and how packages are assembled. [Component Structure and MVC Implementation](./Component-Structure-and-MVC-Implementation.md) bridges the gap between Joomla theory and JCB's automation.
3. **Clarify the JCB workflow mindset**—what the tool automates, what remains in your control, and how Dynamic Get, views, and fields relate. [Joomla Component Builder – Beginner-Friendly Guide](./Intro-to-JCB.md) summarises prerequisites, environment expectations, and the overall build loop.
4. **Map the database-to-interface relationship** so you know how admin views, site views, and fields combine to deliver data to users. Chapters [General Planning](./General-Planning.md) and [Field Types](./Field-Types.md) outline how to plan entities, choose field types, and prepare for compilation.

> 🧭 **Outcome:** you should be able to describe the main Joomla directories, explain how JCB mirrors them, and articulate the planning steps before touching the builder interface.

---

## Step 2 – Prepare your toolchain

1. **Set up a local Joomla environment** using the OctoJoom toolchain, which provisions Joomla's official Docker containers and Traefik for you. Follow [Setup Local Development Environment with OctoJoom](./Setup-Local-Development-Environment-with-OctoJoom.md) for a guided walkthrough, or replicate the same containerised requirements manually.
2. **Install Joomla Component Builder** using the [Installation walkthrough](./Installation-of-JCB.md) (single public package, compiler usage, clearing temporary files).
3. **Verify PHP and server requirements** so compilation succeeds. The [PHP Settings reference](./PHP-Settings.md) lists recommended configuration values and troubleshooting tips.  
4. **Import demo data (optional)** to explore working examples. The [Using the JCB Demo Component](./Using-the-JCB-Demo-Component-While-Building-Your-Local-Development-System.md) guide explains how to load and inspect it.

> 🧭 **Outcome:** you have a working Joomla site with JCB installed, demo data available, and confidence that server settings will not block builds.

---

## Step 3 – Build your first component

1. **Start with a guided example:** follow [Hello World with Joomla Component Builder](./Hello-World-with-Joomla-Component-Builder.md) to create a simple component from scratch, including admin and site views, menu links, and permissions.  
2. **Reinforce the foundations** by revisiting [Basic Fields](./Basic-Fields.md) and [Admin Views](./Admin-Views.md) to understand how fields populate lists and forms.  
3. **Practice compilation and installation** by iterating through small changes, recompiling, and reinstalling within Joomla using the instructions in the Hello World tutorial and [Field Types](./Field-Types.md#5-compiling-and-installing-your-component).  
4. **Document your learning**—update component notes, track field names, and keep a changelog. This habit will ease later export/import or collaboration tasks.

> 🧭 **Outcome:** you can create a functioning component, compile it, install it, and recognise how admin data flows to the site frontend.

---

## Step 4 – Explore core building blocks

| Concept | Why it matters | Key resources |
| --- | --- | --- |
| **Planning views and fields** | Translating requirements into database tables, relationships, and permissions. | [General Planning](./General-Planning.md), [Adding Admin Views](./Adding-Admin-Views-to-a-Component.md), [Adding Site Views](./Adding-Site-Views-to-a-Component.md) |
| **Field types and validation** | Selecting the right inputs and enforcing correct data. | [Field Types](./Field-Types.md), [Advanced Fields](./Advanced-Fields.md), [Adding Rule Validation](./Adding-your-own-rule-validation-to-a-field-in-JCB.md), [Easy Validation Rules](./Easy-Validation-Rules-for-Fields-in-JCB.md) |
| **Dynamic data retrieval** | Combining records across tables without manual SQL. | [dynamicGet](./dynamicGet.md), [Add dynamicGet to a Site View](./Adding-dynamicGet-to-a-Site-View.md), [Automatic Custom Code Import](./Automatic-import-of-custom-code-during-compilation-in-JCB.md) |
| **Templates and layouts** | Controlling presentation and reusing markup. | [Templates & Layouts](./Adding-Templates-and-Layouts-to-a-Site-View.md), [Template Setup](./Template-Setup.md), [Layout Setup](./Layout-Setup.md) |
| **Custom code and helpers** | Extending generated components safely. | [Manual Custom Code Implementation](./JCB-manual-custom-code-implementation.md), [Helper Structures](./Adding-Helper-Structures-to-any-JCB-component.md), [Additional Helper Methods](./How-to-Add-More-Helper-Methods-to-Your-Components-Helper-Class.md) |

> 🧭 **Outcome:** you know where to deepen knowledge on each pillar as soon as your project requires it.

---

## Step 5 – Choose your learning pathway

### 1. Project planning & collaboration
- [Component Settings Deep Dive](./Component-Settings.md)
- [Component Settings](./Component-Settings-Overview.md)
- [Collaborative Workflow](./Proposed-Collaborative-Workflow-in-JCB.md)
- [Export/Import Fully Mapped Components](./Export-Import-of-fully-mapped-components.md)
- [Automated Backup System](./Automated-backup-system-in-JCB.md)

### 2. Data management & automation
- [Tweaking MySQL Demo Data](./Tweaking-MySQL-Demo-Data.md)
- [Auto-create SQL Updates](./Auto-create-SQL-updates-for-Componets-in-JCB.md)
- [Automated Database Updates](./Automated-database-updates-in-Joomla-during-development-of-a-component.md)
- [Reuse Custom Code](./Reuse-Custom-Code.md)

### 3. User experience & site delivery
- [Custom Admin Views](./Custom-Admin-Views.md)
- [Setup Site Edit View](./Setup-Site-Edit-View-in-JCB.md)
- [Quick Hello World (accelerated build)](./The-Quick-Hello-Word-with-JCB.md)
- [Custom Dashboard Option](./The-custom-dashboard-option-in-JCB.md)

### 4. Extensibility & ecosystem
- [Community Snippets Overview](./General-overview-of-how-community-snippets-work.md)
- [Forking JCB Snippets](./Tutorial-on-forking-JCB-snippets-so-you-can-share-your-snippets-with-the-rest-of-the-Community.md)
- [Making a Snippet Pull Request](./Tutorial-on-making-a-pull-request-at-Joomla-Component-Builder-Snippets.md)
- [JCB Packaging Engine](./JCB-Packaging-Engine.md)
- [Publish Your JCB Packages](./Add-your-own-JCB-packages-to-the-JCB-Communty-Directory.md)

> 🧭 **Outcome:** pick the pathway that matches your immediate project stage and follow the linked tutorials in sequence.

---

## Step 6 – Maintain and scale your builds

1. **Global configuration management:** master component-level settings via [Global Settings](./Global-Settings-of-Component-Builder.md) and learn how menu parameters interact in [Manage Component Config Options](./Manage-a-Components-Global-Config-Option-Field-in-Relation-With-Menu-Params.md).  
2. **Deploy upgrades confidently:** study [Auto-create SQL updates](./Auto-create-SQL-updates-for-Componets-in-JCB.md) alongside [License Template Changes](./How-to-change-the-License-Template-in-JCB.md) to automate schema migrations and package metadata.  
3. **Handle translations and localisation:** combine [Easy Translation via Excel](./Easy-Translation-via-excel.md) with [Translation Manager](./Translation-Mananger-in-JCB-explained.md) to streamline multilingual work.  
4. **Monitor performance and stability:** leverage [Automated Backup System](./Automated-backup-system-in-JCB.md) and [Dynamic File Inclusion Concept](./Dynamic-File-and-Folder-Inclusion-concept.md) to keep generated code maintainable.

> 🧭 **Outcome:** you have a checklist for long-term maintenance tasks that go beyond the first release.

---

## How to navigate the documentation efficiently

- **Use Start Here + Home together:** Start Here points you to the right topic; Home lists every chapter with timeline references for quick scanning.
- **Understand how the documentation is produced:** [Developing with Joomla Component Builder](./Developing-with-Joomla-Component-Builder.md) outlines the transcription project and gives tips for studying alongside the videos.
- **Search within the repository:** use your editor's search or command-line tools (`rg "keyword" english/`) to find specific features, field names, or helper references across the Markdown files.  
- **Leverage the sidebar:** [`_Sidebar.md`](./_Sidebar.md) mirrors the Home index and can be pinned in GitHub or wiki views for persistent navigation.  
- **Track revision status:** chapter titles include progress notes while the editing project is underway. Prioritise fully edited lessons like [Field Types](./Field-Types.md) when you need polished guidance.  
- **Keep personal notes:** maintain a `docs/notes.md` or issue tracker in your project repo to record how you applied tutorials—this shortens the feedback loop when troubleshooting.

---

## Where to get help and stay updated

- **Community discussions:** join ongoing conversations and ask questions in the [JCB Discussions board](https://github.com/vdm-io/Joomla-Component-Builder/discussions).  
- **Video playlist:** follow the full [YouTube tutorial playlist](https://www.youtube.com/playlist?list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE) alongside the written chapters.  
- **Beta testing updates:** keep an eye on [Beta Testing](./Beta-Testing.md) for release notes and calls for testers.  
- **Contribute back:** when you craft helpers, layouts, or snippets, consider sharing them via the snippets workflow or package directory linked above.

> 🧭 **Outcome:** you know where to ask questions, watch demonstrations, and contribute improvements as you grow into the platform.

---

## Ready for your next step?

Revisit this page whenever you need to re-orient yourself or onboard a teammate. Start from Step 1 if you need a refresher on architecture, jump to Step 4 to drill into a feature, or head straight to Step 6 when preparing a release. Happy building!
