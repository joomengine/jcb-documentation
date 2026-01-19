# Layout Setup

> **Video Tutorial:** [Watch on YouTube](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
> (*Click timestamp links below to jump to specific sections in the tutorial.*)

---

## Introduction to Layouts

[00:00:00](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h00m00s)

In **Joomla Component Builder (JCB)**, layouts are used to **reuse display code** across multiple templates or site views. This helps maintain consistency and reduces duplication. The [JCB Layouts overview](./JCB-Layouts.md) explains how to initialise, reset, push, and fork layout repositories inside JCB so that the techniques in this walkthrough stay version-controlled across projects.

Layouts let you:

* Share display logic between site views.
* Dynamically adapt to the context (view, data, and global parameters).
* Simplify template management by separating logic from display.

Before creating or using layouts, understand **which site view is calling the layout**, since global settings can vary per view.

---

## How Layouts Work with Dynamic GETs

[00:00:34](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h00m34s)

Each **Dynamic GET** targets a specific **site view**.
For example, the `sermon (preacher.id)` dynamic get is designed for the **Preacher** view.

Inside the custom script, you can define a **view key** - in this case, `"Preacher"`.
This ensures:

* Only the relevant item is passed to the layout (not the full list).
* The layout adapts its display based on the calling view.

```php
// Example snippet from a layout context
$viewKey = 'preacher';
$item = $displayData; // the specific item passed from Dynamic Get
```

You can then customize the layout's output based on the `$viewKey`.

---

## How Templates Call Layouts

[00:01:39](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h01m39s)

Templates can call layouts using `JLayoutHelper::render()`.

Example - from the **sermon list** template:

[00:01:54](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h01m54s)

The template loops through items, prepares parameters, and passes the data to the layout.

```php
foreach ($this->items as $item) {
    $item->params = $this->params;
    $item->description = JHtmlString::truncate($item->description, 90);
    echo JLayoutHelper::render('sermonlist.item', $item);
}
```

[00:02:46](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h02m46s)

This `JLayoutHelper::render()` call will output each list item based on the selected layout.

---

## Sermon List - Item Layout

[00:03:08](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h03m08s)

Inside the **sermon list item layout**, JCB passes the `$displayData` object, which represents the current `$item`.

Example:

```php
$item = $displayData;
$title = $item->get('title');
```

This allows layouts to access all fields, parameters, and global settings through `$displayData`.

---

## 🗝 Using the View Key

[00:03:56](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h03m56s)

Layouts can use a **view key** to determine which view they are rendering (e.g., Preacher, Series, or Category).

By checking this key, you can create dynamic behavior:

* Show or hide specific data depending on the view.
* Use different global settings based on `$viewKey`.

This allows flexible reuse of the same layout across multiple contexts.

---

## Layout-Template Integration via Custom Script

[00:05:11](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h05m11s)

In templates, JCB uses placeholders like `[[[sview]]]` to dynamically insert the **site view name**.

Example:

```php
<div class="[[[sview]]]-list">
    <!-- Dynamic view-specific layout -->
</div>
```

This lets one template be reused for multiple site views without duplicating files.

---

## Dynamic Custom Views Using Templates

[00:05:46](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h05m46s)

The placeholder `[[[sview]]]` ensures dynamic insertion of the site view name.
It draws values from the **component's global parameters** - for example, `sermon_list_style`.

The template will then automatically adjust based on the current view (Preacher, Series, or Category).

---

## config.xml and Global Parameters

[00:07:17](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h07m17s)

These settings are defined in your component's **config.xml** file.

Inside, you'll find parameters like:

* `preacher_list_style`
* `series_list_style`
* `category_list_style`

These determine the display behavior per view.

By searching for `sermon_list_display`, you'll see how JCB uses the same logic for each view dynamically.

---

## Layout Concept Explained

[00:09:26](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h09m26s)

Layouts work like templates but offer **more flexibility**:

* You can include PHP and dynamic logic.
* You can reuse them across multiple site views.
* They can handle any data passed in via `$displayData`.

 **Tip:** If you're unfamiliar with PHP, it's fine to handle display logic directly in the site view. Layouts are meant for cleaner, modular development.

---

## Layout Custom Script Area

[00:11:02](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h11m02s)

Each layout in JCB includes a **custom script area** (in the head of the layout file).
This lets you:

* Add inline PHP or JavaScript.
* Modify `$displayData` dynamically.
* Access global settings.

```php
<?php
$global = $displayData;
$paramValue = $global->get('my_field');
?>
```

---

## Using a Layout Inside Another Layout

[00:11:32](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h11m32s)

Layouts can **include other layouts** using:

```php
echo JLayoutHelper::render('sub.layout.name', $subData);
```

**Important:**

* `$this` is not available inside layouts.
* Always rely on `$displayData` for passing data between them.

---

## Summary

| Concept            | Purpose                  | Key Reference                                                       |
| ------------------ | ------------------------ | ------------------------------------------------------------------- |
| **Layouts**        | Reusable display code    | [00:00:00](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h00m00s) |
| **Dynamic GET**    | Pass data to layouts     | [00:00:34](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h00m34s) |
| **Templates**      | Call layouts dynamically | [00:01:39](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h01m39s) |
| **View Key**       | Identify site view       | [00:03:56](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h03m56s) |
| **config.xml**     | Define global options    | [00:07:17](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h07m17s) |
| **Custom Scripts** | Add dynamic logic        | [00:11:02](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h11m02s) |
| **Nested Layouts** | Layouts inside layouts   | [00:11:32](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h11m32s) |

---

## Pro Tips

* Use **meaningful view keys** to manage logic per site view.
* Keep all **layout files modular** - one per display concept.
* Reference **global parameters** in `config.xml` to standardize look and feel.
* When in doubt, check `$displayData` to see what data is available.
* Reuse layouts to maintain **DRY** (Don't Repeat Yourself) principles.

---
