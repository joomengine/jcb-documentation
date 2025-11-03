# Advanced Fields - Joomla Component Builder (JCB)

### [Video Tutorial](https://www.youtube.com/watch?v=VpzYbifqv0M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

(*Click the timestamps below to watch specific sections in the tutorial.*)

---

## Overview

Joomla Component Builder (JCB) supports a variety of field types, including **basic**, **dynamic**, and **custom advanced fields**.
This guide focuses on **advanced fields**, explaining how to extend Joomla's field functionality by building custom PHP-driven fields, handling global parameters, repeatable field sets, and linking data dynamically across views.

Advanced fields allow you to:

* Dynamically populate options using PHP logic
* Reference global component settings
* Extend Joomla's default field types
* Create repeatable structures
* Restrict or filter data dynamically (e.g., user or preacher lists)

---

## 1. Setting Up a Local Folder Field

[00:00:38](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h00m38s)

### Purpose

This field type dynamically lists files from a **local directory**, based on your component's global settings.

### Steps

1. Create a **custom field** in JCB and set its type to extend the `list` field.

2. In the **XML field definition**, write custom PHP to:

   * Read the folder path from your component's **global settings** (e.g., `localfolder`).
   * Check if the folder exists; if not, create it using Joomla's `JFolder` class.
   * Retrieve all file names and populate them into an **options array**.

3. Return this array to Joomla for rendering as a drop-down list.

```php
$options = [];
$files = JFolder::files($path);
foreach ($files as $file) {
    $options[] = JHtml::_('select.option', $file, $file);
}
return $options;
```

**Tip:**
When enabling **multiple selections**, ensure that the field is stored as `JSON`. JCB will automatically detect multiple values and store them correctly.

---

## 2. Building a "Sermon Preacher" Custom Field

[00:05:32](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h05m32s)

This example demonstrates a field that displays a list of **preachers** from the `preachers` list view.

### Key Conventions

* **Type name**: plural view name (e.g., `preachers`)
* **Editing name**: singular (e.g., `preacher`)
* **Multiple**: set to `false` (single selection)
* Use a descriptive **label** and **tooltip** for user clarity.

---

## 3. Understanding `JFormField` Extensions

[00:07:02](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h07m02s)

Custom fields in JCB typically **extend Joomla's native `JFormField` classes** such as:

* `JFormFieldList`
* `JFormFieldUser`
* `JFormFieldRadio`
* `JFormFieldCheckbox`

These are defined in **`administrator/components/com_componentbuilder/compiler/joomla_3`**.
You can explore or add new ones if your project requires unique behaviors.

---

## 4. Extending List Fields Dynamically

[00:09:16](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h09m16s)

When targeting data from another table (e.g., `preachers`), use placeholders to make your component **name-agnostic**.

### Placeholder Syntax

* `###component###` → replaced by the actual component name during compilation.
* Always use **lowercase view names**.
* Use **key** (stored in DB) and **value** (displayed in UI) fields properly.

### Example

| Property    | Description                   |
| ----------- | ----------------------------- |
| Table       | `#__###component###_preacher` |
| Key Field   | `id`                          |
| Value Field | `name`                        |
| Field Name  | `preacher`                    |

**Result:** When compiled, the list field dynamically shows all preachers for selection.

---

## 5. Adding Custom PHP in Field Definitions

[00:15:59](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h15m59s)

You can inject PHP directly in field definitions to fine-tune logic.
**Use single quotes only** inside your PHP to avoid escaping issues.

```php
$options[] = array('value' => $file, 'text' => $file);
```

---

## 6. Compiling and Code Replacement

[00:16:51](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h16m51s)

When compiling, JCB replaces placeholders (like `###ID###`, `###name###`, and `###component###`) with actual component data.
This ensures reusable code across multiple components.

**Tip:**
You can inspect compiled files under:

```
administrator/components/com_componentbuilder/helpers/compiler
```

---

## 7. Dropbox File List - External Data Example

[00:22:31](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h22m31s)

Example of integrating a custom helper method (`getDropboxlinks`) to fetch data from external sources like Dropbox.
It dynamically builds a dropdown list based on retrieved links.

---

## 8. Component Helper Classes

[00:23:32](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h23m32s)

Each JCB component includes **helper classes** located in:

```
/administrator/helpers/
```

and

```
/site/helpers/
```

These can contain static functions used across custom fields.

Common built-in helper methods include:

* `getVar()` and `getVars()` - Retrieve component variables.
* `isPublished()` - Check if an object is published.
* `jsonToString()` - Convert JSON objects to strings safely.

You can extend these helpers with your own logic.

---

## 9. Custom User Fields

[00:31:02](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h31m02s)

### Purpose

Display and filter Joomla users dynamically.

### Features

* Restrict users by **group** using global settings.
* Exclude specific users already assigned to other records.
* Ensure **one record per user** logic using PHP inside `type_phpx`.

```php
$excluded = $this->getExcludedUsers();
$options = array_diff($allUsers, $excluded);
```

**Important:**
Define the group or restriction logic in your **Global Options**.
Access it in PHP using:

```php
$group = ComponentHelper::getParams('com_example')->get('user_group');
```

---

## 10. Naming Conventions

[00:38:08](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h38m08s)

When naming custom field types:

* **No underscores or spaces**
* Use only lowercase
* File names and field types must match

Example:
Field type `studentusers` → File name `studentusers.php`

---

## 11. Repeatable Custom Fields

[00:40:38](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h40m38s)

### Concept

Repeatable fields are containers holding multiple sub-fields.

### How to Create One

1. Create the fields you want to repeat.
2. Note their **field IDs** from the right-hand column.
3. Add a new field of type **repeatable**, and list the IDs (comma-separated) in the **"Fields"** input.

**Note:** You cannot nest repeatable fields, but you can include advanced custom fields inside them.

---

## 12. Custom Icons for Buttons

[00:44:41](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h44m41s)

Use Joomla's [Icomoon font icons](https://docs.joomla.org/J3.x:Joomla_Standard_Icomoon_fonts) to customize buttons.

Example:

```xml
<field name="add" label="Add" icon="checkmark-circle" />
```

---

## 13. Radio Buttons in Repeatable Fields

[00:47:39](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h47m39s)

When using **radio buttons** in repeatable fields:

* Remove the **CSS "button" class**.
* Use the **dot-style radio** (`Searchable Yes/No`) instead of button-style to avoid rendering issues.

---

## Summary

| Concept                   | Key Insight                                           |
| ------------------------- | ----------------------------------------------------- |
| **Custom Field Types**    | Extend Joomla's list fields for dynamic data          |
| **Global Integration**    | Access component-level settings using helpers         |
| **Repeatable Structures** | Combine multiple fields in one repeatable container   |
| **Dynamic PHP Logic**     | Populate dropdowns or filter data dynamically         |
| **Naming Rules**          | Lowercase, no underscores, consistent with view names |

---

### Final Notes

* Always **compile** your component after adding or editing custom fields.
* Test your field logic by inspecting the compiled PHP files.
* Use JCB's placeholders (`###component###`) to maintain flexibility when renaming components.
* For more examples or troubleshooting, refer to the JCB forums or GitHub discussions.

---
