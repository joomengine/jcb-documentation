# Joomla Component Builder - Basic Fields

### Tutorial Reference

[Video: Basic Fields](https://www.youtube.com/watch?v=9NO2rKnC6Ug&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)
---

## Overview

[00:00:00](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=0s)

In this tutorial, we explore how to create **fields** in Joomla Component Builder (JCB).
Fields are fundamental to any component as they define the **data structure**, **form inputs**, and **database mappings** of your custom component.

There are two categories of fields in JCB:

1. **Common (Basic) Field Types** - These are standard Joomla fields such as text, list, radio, editor, color, category, etc.
2. **Advanced (Custom) Field Types** - These are specialized or dynamic fields that interact with other component data. These are covered in later tutorials after admin and site views are introduced.

> **Tip:** Before creating custom fields, it's important to understand how fields and views are connected within JCB.

---

## Creating a New Field Type (Text Field Example)

[00:01:04](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=64s)

To create a new field:

1. Go to **Joomla Administrator → Components → Component Builder → Fields**.
2. Click **New Field**.
3. Choose **Text** as your field type.

Once selected, JCB will automatically load default field settings defined by the selected field type.

### Understanding MySQL Data Types

[00:01:29](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=89s)

Each field corresponds to a MySQL column type, such as:

* `VARCHAR`
* `TEXT`
* `MEDIUMTEXT`
* `LONGTEXT`

You can change these data types in JCB.
This flexibility allows developers to design more **complex and scalable** database structures.

> **Note:** This feature is meant for developers with SQL experience. JCB empowers advanced customization rather than limiting you to "no-code" constraints.

---

## Database Index and Null Options

[00:03:15](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=195s)

Each field can have:

* **Length:** Character limit for the field.
* **Default Value:** Predefined value if no data is entered.
* **Index Type:** `KEY` or `UNIQUE KEY`.

> Setting a field as **Unique** means no duplicate values can exist in that column.
> Joomla usually manages uniqueness (for example, in aliases), so this is rarely needed.

The **Null Switch** determines whether the database column can be empty.

---

## Store Method (Default, JSON, Base64, Encryption)

[00:04:28](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=268s)

The **store method** defines how data is stored in the database:

* **Default:** Standard method for most fields.
* **JSON:** Used for storing arrays (e.g., multiple selections in list fields or checkboxes).
* **Base64:** Encodes data-often used for storing custom code or scripts.
* **Encryption:** For advanced security needs (optional, complex to implement).

> **Example:**
>
> * A checkbox field with multiple values should use JSON.
> * Tag fields are handled differently and don't require JSON encoding.

JCB automatically ensures checkbox data is stored as valid JSON, even if Joomla does not handle it correctly natively.

---

## Inspecting Compiled Fields in the UI

[00:07:42](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=462s)

When JCB compiles your component, it includes detailed comments in the XML and PHP model files indicating **where each field is implemented**.

If a field is not working as expected, open the compiled files to locate and inspect the relevant code lines. This helps developers debug or customize behavior precisely.

---

## Example: Email Field Creation

[00:10:28](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=628s)

Let's create an **email field** as an example:

| Setting      | Value          |
| ------------ | -------------- |
| Field Type   | `Text`         |
| Name         | `email`        |
| Label        | `Enter Email`  |
| Data Type    | `VARCHAR(255)` |
| Required     | No             |
| Store Method | Default        |
| Validation   | `Email`        |

> **Validation Tip:**
> Joomla includes built-in validation types (like `email`, `url`, `number`).
> Custom validation can be added by writing a PHP validator and mapping it via the JCB custom files system.

---

## Targeting Fields with CSS and JavaScript

[00:14:10](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=850s)

Each field in JCB has a unique **HTML ID** following this structure:

```
#jform_FIELDNAME
```

For example, to target the `email` field:

```css
#jform_email {
  color: red;
}
```

Or with jQuery:

```javascript
jQuery('#jform_email').val('example@domain.com');
```

### Adding Scripts or Styles in Fields

You can add custom **CSS** or **JavaScript** directly in the field configuration under the **Script** area.
These scripts follow the field wherever it is used in views, allowing reusable dynamic behavior.

---

## Repeatable Fields with Custom Scripts

[00:17:49](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=1069s)

Joomla's default system doesn't support certain field types (like Date) inside **Repeatable Fields**.
However, JCB allows advanced customization using inline PHP and JS in the **field script area**.

Example (simplified):

```php
<?php
// Inside the field script
JHtml::_('jquery.framework');
?>
<script>
  jQuery(function() {
    jQuery('#course_date_fields_date').datepicker();
  });
</script>
```

> **Important:**
> This script is attached to the repeatable field, not the text field itself, ensuring it applies across all repeated items dynamically.

---

## List Field (Static Options)

[00:20:26](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=1226s)

To create a **List** field:

* Field Type: `List`
* Options Format: `value|label,value2|label2,...`

Example:

```
0|Select an option,1|Option One,2|Option Two
```

If the value and label are the same, you can omit the pipe (`|`).

> **Dynamic Lists:**
> Later tutorials will show how to make lists populate dynamically from other tables using JCB's advanced field features.

---

## Radio Button Example

[00:24:38](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=1478s)

Radio buttons work similarly to list fields but are ideal for **two to four options**.

Use the same syntax:

```
1|Yes,0|No
```

Avoid quotation marks inside values. Use HTML entities instead (e.g., `&quot;`).

---

## Color Field Example

[00:26:54](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=1614s)

The color field allows color picking with a default value.

* Type: `Color`
* Label: e.g., "Select Color"
* Name: lowercase identifier (e.g., `text_color`)

If you change the type manually, JCB ignores it because the color field is **locked** to its predefined settings.

---

## Showon Attribute Example

[00:27:46](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=1666s)

The **Showon** attribute allows conditional visibility of fields.
For example, to show a field only when another field has a certain value:

```
view:1
```

Or for multiple values:

```
view:[1,4]
```

> JCB also extends Joomla's default *showon* with its own **advanced conditional system**, allowing more complex dependencies between fields.

---

## Category Field Example

[00:29:18](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=1758s)

To add Joomla's native **Category** support:

* Field Type: `Category`
* Extension: Your component's name (e.g., `com_example`)

You can also target a specific view:

```
com_example.viewname
```

> This automatically integrates Joomla's category management system into your component.

---

## Editor Field Example

[00:32:10](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=1930s)

The **Editor Field** embeds the Joomla content editor (TinyMCE or alternative) into your form.

You can configure:

* Which editor to load
* Whether to show or hide editor buttons
* Filter options

These settings follow Joomla's standard form behavior.

---

## Media Field Example

[00:33:26](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=2006s)

The **Media Field** allows image selection.

* Default Directory: `/images/`
* Custom Directory: `/images/yourfolder/`
* Optional Preview: Hover preview can be enabled
* Supports `showon` and standard attributes

> Joomla currently limits Media fields to the `/images/` directory.

---

## Notes Field Example

[00:34:42](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=2082s)

**Notes** are non-input elements used to display informational text between fields.
You can position notes before or after other fields using the **Field Information** section.

---

## Translation and Language Strings

[00:36:31](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=2191s)

Each field attribute can be marked as **Translatable**.
When enabled, JCB automatically:

1. Converts the label or value into a language constant.
2. Adds it to your component's language file.
3. Replaces the XML label/value with the language string.

Example:

Label: `Acronym`
→ JCB converts it to `COM_EXAMPLE_FIELD_ACRONYM_LABEL`.

> **Tip:** This ensures your component supports multi-language translations seamlessly.

---

## Summary

[00:38:59](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=2339s)

You have now learned how to create and configure **basic fields** in Joomla Component Builder, including:

* Text, Email, List, Radio, Color, Category, Editor, Media, and Notes fields.
* Data storage methods (Default, JSON, Base64).
* Conditional visibility (Showon).
* Adding scripts and translations.

---
