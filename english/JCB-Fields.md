# JCB Fields

Joomla Component Builder (JCB) revolves around **fields**. They shape your database schema, drive the Joomla forms that administrators and site users interact with, and coordinate how information moves through every extension you compile. This chapter consolidates the latest guidance on how fields behave, where they are used, and how to keep them maintainable across projects.

---

## What Are Fields?

Fields are the **foundation** of every JCB project. Each field simultaneously describes your data and how JCB should render, validate, and persist it inside a compiled extension.

A field definition is more than a label and input type. It controls the full lifecycle of a value:

- **Database structure** – Define the storage engine, type, length, defaults, nullability, unique constraints, and indexes that JCB should create when installing or upgrading your component.
- **Rendering** – Bind the field to a field type so Joomla knows how to display it: classic inputs such as `text`, `list`, and `calendar`, but also richer experiences like subforms, modal selects, or toggle switches.
- **Validation & permissions** – Combine Joomla ACL checks, required flags, filters, and validation rules to decide who can interact with the value and which formats are accepted.
- **Model integration** – Extend saving and retrieval through custom PHP hooks (`onGet`, `onSave`, `onBeforeLoadForm`, etc.) without forking core files.
- **Presentation details** – Configure classes, HTML attributes, inline scripts, language strings, and layout overrides directly inside the field definition.

Because all of these decisions live in one record, the field becomes a single source of truth that JCB can reuse everywhere the data appears.

---

## Where Are Fields Used in JCB?

Fields travel with the structures that consume them. Once defined, a field can be mapped to:

- ✅ **Admin views** – The edit and list views in Joomla's administrator interface.
- ✅ **Site views** – Frontend forms and detail screens.
- ✅ **Modules** – Configuration forms that power module positions.
- ✅ **Plugins** – Event-driven integrations that expose options in the plugin manager.
- ✅ **Component configurations** – Global settings available through Joomla's component options panel.

JCB automatically assembles the appropriate XML, language strings, and PHP integrations for each context so you do not need to duplicate definitions manually.

---

## What Can a Field Do?

A single field record in JCB can instruct the compiler to:

- Generate **database schema** definitions for installer SQL and incremental updates (`int`, `varchar`, `json`, custom types, nullable flags, indexes, etc.).
- Enforce **permissions** by mapping fields to Joomla ACL groups or access checks.
- Adjust **rendering options** with HTML classes, layout overrides, conditional display logic, and JavaScript behaviors.
- Hook into **model events** to transform data before save, after load, or while preparing the form.
- Reference **field types** that bring advanced behaviors (Model Selects, Subforms, Toggle Switches, Encrypted Fields, and more).

This centralisation makes field management efficient and highly reusable. Planning a component often starts by sketching the fields and their relationships—JCB then scaffolds the rest of the MVC structure around those decisions.

---

## Reuse, Sharing, and Versioning

Fields are standalone entities. Define them once and map them into multiple admin views, modules, or plugins as needed. When you export or share a component, JCB packages every referenced field so collaborators receive the same structure and behavior.

You control updates through JCB's repository-aware workflow:

1. Use **Reset** in the JCB UI to sync a field with the canonical definition stored in this documentation repository.
2. **Fork** the repository if you need bespoke behavior, customise the field, and point JCB to your fork.
3. Publish or import fields via repositories just like snippets and packages, ensuring teams stay aligned without emailing SQL dumps.

Versioning in Git keeps a full history of how each field evolves, making audits or rollbacks straightforward.

---

## Field Workflow at a Glance

1. **Plan** – Identify the entities your component needs and capture their attributes as fields. Use [General Planning](./General-Planning.md) for guidance on mapping requirements to database tables.
2. **Create** – Build the field in JCB, selecting the appropriate field type, database settings, validation, and presentation options. Refer to [Basic Fields](./Basic-Fields.md) for a step-by-step walkthrough.
3. **Map** – Attach the field to admin views, site views, modules, or plugins. [Admin Views](./Admin-Views.md) and [Adding Site Views](./Adding-Site-Views-to-a-Component.md) explain how these mappings affect generated MVC code.
4. **Compile** – JCB generates Joomla-compliant XML definitions, models, controllers, and installer SQL based on your field configuration. Cross-check behavior using [Field Types](./Field-Types.md) and [Advanced Fields](./Advanced-Fields.md) as references.
5. **Maintain** – When upstream improvements land, reset fields from the repository or merge updates from your fork. Recompile to propagate changes safely.

---

## Extending Field Behavior

Because fields sit at the intersection of database design and form rendering, they are the ideal place to centralise advanced logic:

- **Custom PHP hooks** let you transform values, generate derived data, or call external services during save and load operations.
- **Styling hooks** inject CSS classes or inline attributes that align your component with site-wide design systems.
- **Scripting hooks** attach JavaScript behaviors, enabling progressive enhancement without editing compiled files.
- **Dynamic defaults** can look up values from other tables or apply context-sensitive logic during form preparation.

Use these capabilities judiciously so fields remain reusable. When you need a variation, create a new field or fork the repository entry rather than overloading a single definition with conditional code.

---

## Keep Exploring

Use this chapter as your orientation point and then dive deeper into specialised topics:

- [Basic Fields](./Basic-Fields.md) – Create fundamental fields, configure storage, and inspect compiled output.
- [Advanced Fields](./Advanced-Fields.md) – Explore dynamic field relationships, repeatable structures, and custom scripting.
- [Field Types](./Field-Types.md) – Understand the underlying Joomla field type architecture and repository workflow.
- [JCB Fields Type Extended](./JCB-Fields-Type-Extended.md) – Step through advanced examples of extending or overriding field types.
- [Default Database Values per Field Type](./Default-Database-Values-can-be-set-per-Field-Type.md) – Automate defaults based on field type definitions.

> **Reminder:** Fields define both structure and behavior — they are where your data comes alive.

---

## Index of Field Resources

| Topic | Why it matters | Key chapters |
| --- | --- | --- |
| Planning entities & schema | Translate requirements into tables, relationships, and reusable fields. | [General Planning](./General-Planning.md), [Admin Views](./Admin-Views.md) |
| Selecting field types | Pair fields with the correct rendering and storage behavior. | [Field Types](./Field-Types.md), [Basic Fields](./Basic-Fields.md) |
| Advanced behaviors | Add dynamic relationships, subforms, and interactive controls. | [Advanced Fields](./Advanced-Fields.md), [JCB Fields Type Extended](./JCB-Fields-Type-Extended.md) |
| Validation & automation | Reuse PHP hooks, default values, and ACL rules across views. | [Easy Validation Rules for Fields](./Easy-Validation-Rules-for-Fields-in-JCB.md), [Default Database Values per Field Type](./Default-Database-Values-can-be-set-per-Field-Type.md) |
| Sharing & versioning | Keep teams aligned by syncing reusable field libraries. | [Proposed Collaborative Workflow](./Proposed-Collaborative-Workflow-in-JCB.md), [How to Install JCB Packages](./How-to-install-jcb-packages.md) |

Return to this overview whenever you need to explain how fields underpin JCB or when onboarding teammates who are learning the workflow for the first time.
