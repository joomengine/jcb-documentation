# Field Types in Joomla Component Builder

### [Video Tutorial](https://youtu.be/OhLzvThDXls)

*Use the timestamp links to jump to relevant sections.*

---

## 1. Overview

Joomla! Component Builder (JCB) generates complete Joomla components, including XML form definitions, models, views, and controllers.
Understanding **field types** is essential, as they determine what form elements are rendered in your component's admin and site views. Pair this chapter with [JCB Fields](./JCB-Fields.md) to see how individual field records consume these field types, define database schema, and stay versioned via repositories.

A **field type** defines how a field behaves and appears - for example, a text box, checkbox, date picker, list, or repeatable input.
These are stored in XML format and processed through Joomla's API to render the form dynamically.

Beyond local definitions, JCB also integrates with **Field Type repositories**. Field types are maintained separately—just like
[packages](How-to-install-jcb-packages.md) and [snippets](General-overview-of-how-community-snippets-work.md)—so you can share,
reuse, and synchronise them across projects or entire teams.

> **Key Concept:**
> All fields exist within views - either **list views** (plural) or **edit views** (single).
> JCB builds these automatically when you define them in your component.

---

## 1.1 Field Type Repositories & Global Syncing

JCB ships with full repository support for field types. A central, community-maintained repository keeps the canonical
definitions for every field type used across JCB projects. The official repository lives at
[`joomengine/joomla-fieldtypes`](https://github.com/joomengine/joomla-fieldtypes) and contains the latest versions of every core
type—ranging from **Text** and **List** to more advanced types such as **ModalSelect**, **Repeatable**, or **DynamicCheckboxes**.

### Why repositories matter

* **Global reset** – Any local field type can be reset to the upstream definition directly from the JCB GUI using the **Reset**
  button. This ensures the metadata, XML attributes, and demo values match the authoritative version.
* **Project bootstrap** – When you initialise a new JCB installation, you can immediately pull every field type from the global
  repository so that the component builder starts with the most up-to-date library.
* **Collaboration** – Teams can rely on a shared source of truth. Updates made in one project (and pushed to the repository) can
  be distributed to every other project through a pull.

### Repository operations

Field type repositories support the same workflow as snippets and packages:

| Action | Description |
| --- | --- |
| **Init** | Configure a local JCB installation to track a field type repository (community, organisational, or personal). |
| **Pull** | Import or refresh all field types from the remote repository. Use this when setting up a new environment or when new versions are published upstream. |
| **Push** | Publish your local updates back to the repository—ideal when you curate a custom library for your organisation. |

You can connect to the global community repository or point JCB to a fork/alternative remote, giving you full autonomy over the
definitions you distribute.

> **Tip:** Fork the official repository if you need custom defaults while still benefiting from upstream improvements. You can
> merge updates into your fork whenever new field types are released.

---

## 2. Views, Field Types, and Fields

[01:05](https://youtu.be/OhLzvThDXls?t=65)

When creating or editing a Joomla article, you're interacting with a **view**.
The `view=article` parameter in the URL indicates that you're working inside the **article view**.

Each form element (like title, alias, or editor area) corresponds to a **field**.
Behind each field is a **field type** that defines its behavior.

Common Joomla field types include:

* **Text** - For simple single-line input.
* **Editor** - For WYSIWYG content.
* **List / Radio / Checkbox** - For multiple choice or toggles.
* **User / Date / Tag / Textarea / Label**, and more.

These are all defined as **field types** in Joomla and mapped into your JCB component.

---

## 3. List and Edit Views

[01:57](https://youtu.be/OhLzvThDXls?t=117)

In Joomla:

* The **List View** displays a table of items (e.g., a list of articles).
* The **Edit View** (or single view) opens when you click an item to edit it.

JCB automatically creates both list and edit views for each dataset you define in your component.
Each view includes fields mapped to the view, so the fields you define in JCB are rendered properly when compiled.

---

## 4. All Fields Live in Views

Even though a list view looks like a table, it still contains **fields** - for example:

* The search box, filters, and table columns are all technically **fields**.
* The edit view displays individual input fields, grouped in tabs or sections.

In JCB:

* You define fields inside a view.
* When compiled, JCB uses Joomla's form XML syntax to create the form layout automatically.

> **Tip:**
> Field order and grouping can be managed directly within the JCB interface using drag-and-drop or tab assignments.

---

## 5. Compiling and Installing Your Component

[05:45](https://youtu.be/OhLzvThDXls?t=345)

When compiling your component in JCB, make sure to configure the **Global Settings** properly:

* Ensure Git repository options are set (if using automatic pushing).
* If not, deselect repository actions before compiling.

If you encounter a warning like "Could not move file to Git repository," it usually indicates that repository paths are unset - not an actual compile error.

[06:35](https://youtu.be/OhLzvThDXls?t=395)
Once compiled, click **Install** to deploy the component directly into your Joomla instance.
The demo component will install successfully, though it may not include demo images.

---

## 6. Exploring the JCB Demo Component

The demo component demonstrates:

* **Admin list and edit views**
* **Repeatable fields**
* **Custom radio buttons and alias fields**
* **Import features** (not standard in core Joomla components)

For an in-depth technical reference on the demo component, consult the
[JCB Wiki Appendix](https://github.com/vdm-io/Joomla-Component-Builder/wiki/Using-the-JCB-Demo-Component-While-Building-Your-Local-Development-System).

---

## 7. Admin Fields and Views

[08:04](https://youtu.be/OhLzvThDXls?t=484)

Inside **Admin Views**, JCB displays the fields mapped to that view.
You can:

* **Edit existing fields** directly in the view editor.
* **Add new fields** using the "Add Field" button.

This structure lets you manage many fields across multiple components efficiently.
JCB stores each field definition and links it to the corresponding view.

---

## 8. Field Types in Joomla's Core Library

[09:26](https://youtu.be/OhLzvThDXls?t=566)

Each Joomla field type corresponds to specific XML attributes that define its structure and behavior.
Example attributes for a checkbox field might include:

```xml
<field name="published" type="checkbox" default="1" label="Published" />
```

> **Important:**
> Unless you are creating or extending field types, avoid editing the defaults.
> JCB provides mappings for all common field types already.

---

## 9. Adding Custom Field Types

JCB allows developers to create **custom field types** mapped to Joomla's field library.

### Example use cases:

* Extending Joomla's repeatable field.
* Adding custom attributes or logic (e.g., "Show On" conditions).

The **"Show On"** option controls field visibility based on other field values - a JCB enhancement on top of Joomla's native functionality.

> **Pro Tip:**
> When adding new field types, always match Joomla's standard naming and property conventions to ensure compatibility.

---

## 10. Using Joomla Standard Form Fields

[12:29](https://youtu.be/OhLzvThDXls?t=749)

Refer to Joomla's documentation for a complete list of [standard form field types](https://docs.joomla.org/Standard_form_field_types).

Each field type includes:

* **Type name** (e.g., `checkbox`, `list`)
* **Mandatory / optional attributes**
* Example XML structure

JCB maps these definitions directly into your component forms.

---

## 11. The XML Structure for Joomla Forms

[14:05](https://youtu.be/OhLzvThDXls?t=845)

When defining attributes in a field type, JCB builds XML strings that Joomla uses to render forms.
Example:

```xml
<field name="title" type="text" label="Title" description="Enter a title" required="true" />
```

Adding new attributes in JCB automatically appends them to the XML string used during compilation.

[14:45](https://youtu.be/OhLzvThDXls?t=885)
Each field type in JCB shows which **fields** use it - for instance, multiple text fields can share the "Text" field type definition.

---

## 12. Example: Joomla XML for Text Field

[15:15](https://youtu.be/OhLzvThDXls?t=915)

The XML representation for a text field might look like this:

```xml
<field name="alias" type="text" label="Alias" description="Unique alias for the item" />
```

This structure is automatically generated by JCB during compilation and stored in the XML file used by Joomla's form API.

---

## 13. Compiler and XML Generation

[17:43](https://youtu.be/OhLzvThDXls?t=1063)

During compilation:

* JCB reformats labels into **translatable strings**.
* Adds metadata such as compiler line references and file sources.
* Inserts your field attributes into the correct XML context.

This means that even if you modify attribute values slightly, JCB still interprets them correctly when rebuilding the XML.

---

## 14. Demo Data and Field Value Population

When you create a new field in JCB, demo values (from the field type definition) are automatically pre-filled.
This speeds up field creation and ensures XML consistency.

For example:

* Creating a new **text** field populates with sample XML attributes.
* You can modify these before saving or leave them as defaults.

---

## 15. Best Practices

**Keep default field types intact.**
**Use Joomla naming conventions.**
**Group fields logically in views (tabs, sections).**
**Compile often** to catch XML or mapping errors early.
**Use demo data** to understand field structure before creating complex types.

---

## 16. Conclusion

JCB automates the complex XML, MVC, and API mappings Joomla! needs to build robust components.
Field types are at the heart of this process - understanding how they link to fields, views, and XML output will help you design efficient and scalable components.

---
