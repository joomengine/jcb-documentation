# JCB! Layouts

JCB! Layouts are Joomla layout files you curate, version, and reuse through the Joomla Component Builder (JCB) interface. They let you share the same markup between multiple templates, admin views, and site views without repeating yourself.

> 📚 New to Joomla layout overrides? Start with [Layout Setup](./Layout-Setup.md) for a code-level walkthrough, then return here to master the repository workflow that keeps those overrides in sync across projects.

---

## What Are JCB Layouts?

JCB Layouts are **modular Joomla layout files** managed via the [JCB GUI](https://www.joomlacomponentbuilder.com).
They are equivalent to Joomla's native layout override files (`/layouts`) and follow the same design principles.

With JCB Layouts, you can define reusable, customizable HTML+PHP views:

- Rendered from anywhere in your component (administrator or site)
- Encapsulated in clean, template-driven blocks
- Fully namespace-aware and overridable like native Joomla layouts

This lets your components stay **cleaner, more maintainable, and DRY** (Don't Repeat Yourself).

---

## Why Use Layouts in JCB?

JCB Layouts help you:

- Extract reusable markup from views, fields, and modules
- Maintain structural consistency across your component
- Simplify changes by editing one file instead of many
- Allow for override support via Joomla templates

They are ideal for:

- Form row rendering
- Repeated output (like items in a loop)
- Conditionals and dynamic display logic

Pair these benefits with the [Adding Templates and Layouts to a Site View](./Adding-Templates-and-Layouts-to-a-Site-View.md) tutorial to see how templates, layouts, and Dynamic Gets weave together at runtime.

---

## How Do You Manage Layouts in JCB?

All layouts are version-controlled and managed inside JCB's GUI under the **Layouts** tab. The workflow mirrors other repository-backed assets in JCB:

1. Click **Init** inside the Layouts area to connect the project to a layout repository.
2. Choose which repository to load layouts from (official collections, a team fork, or your personal store).
3. Select the specific layout(s) you want to import.
4. Compile or preview your component—the layout is now available anywhere you call `JLayoutHelper::render()`.

Once imported you can:

- **Reset** a layout to sync with the upstream version.
- **Push** your custom layouts if you have write access to the repository.
- **Fork** the repository to manage your own layout collection without losing upstream improvements.

This gives you a structured way to integrate upstream updates while preserving your project's customisations.

> 🛠️ **Tip:** Treat the Layouts tab like source control. Reset before compiling to catch new upstream changes, and push once your updates are tested. For team projects, document which repository branch a layout points to so collaborators stay aligned.

---

## Using Layouts During Development

- Reference layouts from templates, admin views, or helper code using `JLayoutHelper::render('namespace.layout', $displayData)`.
- Pass only the data the layout needs; `$displayData` is your contract between the caller and the layout file.
- Chain layouts when you need subcomponents. Nested calls keep complex markup readable while still respecting Joomla's override hierarchy.
- Rely on Joomla's override directory structure (`templates/<template>/html/layouts/`) when you want site builders to customise your output without editing the component.

If you are building new site views, combine this guide with the revised [Site View architecture overview](./Adding-Site-Views-to-a-Component.md). The interplay between Dynamic Gets, templates, layouts, and custom code placeholders is what keeps large components maintainable.

---

## Index of JCB Layouts

When you import layouts from a repository, JCB records them in the Layouts tab. Use this space to keep a quick reference of what each layout is intended to render and where it originates. Example structure:

| Layout key | Purpose | Upstream repository |
| --- | --- | --- |
| `sermonlist.item` | Sermon list card markup shared by Preacher, Series, and Category views | `vdm-io/layouts-sermons` |
| `forms.fieldset.row` | Renders Bootstrap fieldsets for admin edit views | `your-org/layouts-forms` |

> ✏️ **Customise this table per project.** Recording layout scope next to the repository name makes it easier to decide when to reset, fork, or retire a layout as your component evolves.

For broader collaboration tips, revisit the [Proposed Collaborative Workflow in JCB](./Proposed-Collaborative-Workflow-in-JCB.md) article once your layout catalogue starts to grow.
