# Template Setup

**Tutorial Reference:** [Watch on YouTube](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)
(*Click timestamps below to jump to specific moments in the video*)

---

## Overview

Templates in **Joomla Component Builder (JCB)** are more than convenient snippets—they are modular, reusable view structures that wrap your component's presentation layer. They provide the high-level skeleton that renders data for both **site views** and **custom admin views**, mirroring Joomla's MVC templating approach while remaining fully overrideable.

Use templates to:

1. Coordinate the HTML and PHP that wraps each view.
2. Delegate repeated markup to layouts or even other templates.
3. Keep business logic in models/controllers while letting templates focus on presentation.
4. Share consistent UI building blocks across components or projects.

In this tutorial, we'll cover:

1. Understanding what JCB templates are and why they matter
2. Creating new templates
3. Copying and modifying existing templates
4. Managing language strings
5. Adding custom scripts and JavaScript
6. Understanding how templates integrate with site views
7. Syncing templates with repositories for collaborative reuse

---

## What Are JCB Templates?

JCB Templates act as **modular wrappers** around your component output. Within a template you can:

* Include other templates to nest more complex structures.
* Render layouts (`JLayoutHelper::render()`) to reuse fragments.
* Mix PHP logic and HTML safely, just like Joomla's native templates.

Because templates are loaded through `$this->loadTemplate('name');`, they have full access to the view object and any helper methods you expose. That parity with Joomla's default approach means any developer already familiar with Joomla templating can quickly adapt to JCB's workflow.

---

## Why Use Templates in JCB?

Templates give you a clean separation of concerns:

* **Consistency:** reuse the same structural wrapper across multiple views for visual alignment.
* **Maintainability:** update one template and instantly refresh its presentation wherever it is loaded.
* **Extensibility:** override or extend templates per project, just as you would with Joomla's core template overrides.
* **Composability:** nest layouts, call helper logic, or include other templates for complex UIs.

Templates are especially valuable when you are:

* Building a suite of components that should share the same design system.
* Maintaining custom admin dashboards that need repeatable panels or grids.
* Creating frontend experiences that mix multiple dynamic fragments on a single page.

---

## Managing Templates in the JCB Interface

Templates are managed directly from the **Templates** tab inside JCB's GUI. Here you can:

1. Click **Init** to connect to a repository.
2. Choose the repository that stores reusable templates.
3. Select individual templates to **import**, **reset**, or **push** back to the source.

This repository-driven workflow keeps teams in sync. You can fork the official library, maintain a private collection, or contribute updates upstream—all without leaving the interface.

---

## Creating Templates

[00:00:00](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

In the previous tutorial, we explored how to set up templates and layouts for a **site view**. Inside a typical site view-like `preacherpanel`, `preachersmall`, or `preacherbox`-you'll find templates loaded to define how data is displayed.

To view or modify these, go to:
**JCB → Templates**

Here, all available templates are listed, each corresponding to a layout used in one or more site views.

---

## Creating or Copying Templates

[00:00:27](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m27s)

To create a new template:

1. Click **New** in the JCB Templates area.

   * You can also copy an existing one by selecting it and using the **Batch → Copy** feature.
   * Click **Process** to complete the copy.

[00:00:49](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m49s)

Open the **Preacher Panel** template (used in the tutorial example).
This area contains the **HTML view** of your layout. If you prefer using PHP, toggle into the PHP editor mode. You can switch back and forth as needed.

**Tip:** Use text placeholders (`{placeholder}`) in your template to make content translatable and dynamically replaced when rendered.

---

## Language Strings

[00:01:20](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m20s)

JCB automatically adds your text strings to the **language file** of your component.
By default, it manages **British English (en-GB)** entries.

If you need additional languages:

* Follow Joomla's standard approach for adding language overrides.
* Copy the English file to your target language (e.g., `fr-FR.com_yourcomponent.ini`).
* Translate each line accordingly.

[00:01:44](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m44s)

### Layout Snippets

Within **Layout Code Snippets**, you can:

* Embed **layouts** inside templates.
* Nest **templates within templates**.
* Reference existing layouts for modular, maintainable code.

This behavior is consistent with how layouts and templates are handled in Joomla site views.

---

## Adding Custom Script or Code to a Template

[00:02:13](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m13s)

Each template includes a **Snippet Box**, which allows you to quickly insert scripts or inline logic.
For example, you can add a small PHP or JavaScript block relevant to your template's data display.

The **Preacher Panel** example in the video shows how inline script can enhance a view's interactivity.

**Best Practice:** Keep business logic in your view's model or controller, and use snippets only for minor UI behavior.

---

## Adding JavaScript to a Template

[00:02:46](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m46s)

In the **Details** tab of your template, you'll find a note about adding JavaScript.

To include JS:

1. Wrap your code in `<script>` tags.
2. It will automatically load into your component's frontend page.

[00:03:13](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m13s)

You still have full access to all **global "this" field values**-meaning your JS can interact dynamically with JCB's runtime data.

[00:03:35](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m35s)

Templates use the same setup conventions as **site views**, except that they are **not standalone views**. Instead, templates are included **within** a main view via Joomla's `getTemplate()` method.

---

## Loading Templates Dynamically

[00:04:02](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m02s)

To load a template from within a view:

```php
echo $this->loadTemplate('preacherpanel');
```

This method includes the specified template file and renders it with all available variables.

[00:04:29](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m29s)

This is how your template becomes part of the main component view, ensuring that all scripts, code snippets, and translations are automatically integrated.

---

## Summary

* Templates in JCB are modular layout pieces that can include HTML, PHP, and JavaScript.
* You can **create**, **copy**, or **extend** templates easily from the JCB interface, and keep them synced through repository imports/exports.
* Language strings are managed automatically for English but can be extended.
* Code snippets and JS can be safely added for UI customization.
* Templates are linked to main views via the Joomla `loadTemplate()` method.

---
