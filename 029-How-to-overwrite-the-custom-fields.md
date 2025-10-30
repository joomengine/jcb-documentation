# How to Overwrite the Custom Fields

**Joomla Component Builder (JCB) Documentation**
*(Based on the tutorial "How to Overwrite the Custom Fields")*

---

## Overview

[00:00:00](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h00m00s)
In Joomla Component Builder (JCB), certain **default fields** are automatically added to every admin view. However, there are situations where you may want to **customize or reposition these default fields**-for example, showing the *Created By* or *Created Date* fields in a different tab or list view.

This guide explains how to safely overwrite these fields, update their placement, and maintain compatibility with JCB's compiler.

---

## 1. Understanding Default Fields

[00:00:12](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h00m12s)
When creating or editing an Admin View, JCB automatically includes a set of default fields:

* `id`
* `asset_id`
* `state`
* `access`
* `ordering`
* `created_by`
* `date_created`
* `modified_by`
* `date_modified`
* `checked_out`
* `checked_out_time`
* `version`
* `hits`
* `metakey`
* `metadescription`
* `metadata`

These fields exist in every Admin View-even if you don't explicitly add them.
By default, **only the ID and State fields** appear in the List View.

---

## 2. Displaying More Default Fields

[00:01:20](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h01m20s)
In some cases, clients may request additional details in list or edit views (for example, *Created Date* or *Created By*). JCB allows you to **overwrite these default fields** by recreating them manually.

### Example

[00:01:45](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h01m45s)

In the "Experts" view:

* The `id`, `state`, and `ordering` fields are displayed by default.
* The ordering column is shown as up/down icons rather than numeric values.

If you wish to display more fields-like *Created By* or *Created Date*-you can overwrite the default ones by creating new fields with **the same names**.

---

## 3. Overwriting Default Fields

[00:02:23](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h02m23s)
To overwrite any default field:

1. Create a new field in your **Admin View**.
2. Use the **exact same field name** as the one used by JCB.
   Example names:

   * `created_by`
   * `created_date`
3. Define its **type**, **label**, and **description** according to your design.

### Example – "Created By" Field

[00:02:57](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h02m57s)

* Field type: `user`
* Name: `created_by`
* Label: *Created by*
* Description: *The user who created this record*

### Example – "Created Date" Field

* Field type: `calendar`
* Name: `created_date`
* Label: *Created Date*
* Description: *The date when this record was created*

> **Tip:**
> Always match the field names exactly. JCB identifies overwrites by comparing names-if they differ, your changes won't take effect.

---

## 4. Reviewing the Compiled Code

[00:03:46](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h03m46s)
To confirm how JCB compiles your overwritten fields:

1. Open your component's **administrator folder**.
2. Navigate to `models/forms/`.
3. Find the XML form matching your Admin View (e.g., `joborder.xml`).
4. Open it and scroll through to locate your field definitions.

You'll see both default and overwritten field definitions in XML format.
These are the values JCB uses when building your component.

> **Important:**
> Do **not** rename the XML nodes for default fields directly in the compiled files.
> JCB relies on the field name to detect overwrites-modifying them may break this link.

---

## 5. Adding Overwritten Fields in JCB

[00:05:06](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h05m06s)
Once you've created the custom fields in your Admin View, you need to **add them to the field list** and assign their positions.

1. Go to **Admin Views → [Your View] → Fields tab**.
2. Click **Add Field** and select the newly created ones (e.g., `created_date`, `created_by`).
3. Assign them to appear in a specific **tab** and determine whether they should display in list or form views.

---

## 6. Managing Field Placement in Tabs

[00:05:41](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h05m41s)
JCB organizes the edit form fields into numbered **tabs**.
Each tab corresponds to a logical grouping of form elements.

* The **15th tab** is reserved for system-related fields (the default placement for "Created By," "Modified By," etc.).
* You can reassign the tab number to display these fields elsewhere.

### Example

[00:06:14](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h06m14s)

* Set `Tab Number = 3` to move *Created By* to the third tab in the edit form.
* Save and compile the component.
* After installation, the *Created By* field will now appear in the third tab.

To restore it to the default system tab:

* Change `Tab Number = 15`
* Save, compile, and reinstall your component.

> **Note:**
> Choosing tab 15 ensures JCB places the field in its default "Publishing" section.
> Any other tab number overrides that location.

---

## 7. Compiling and Testing the Component

[00:08:03](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h08m03s)
After making all changes:

1. **Save** your view configuration.
2. **Compile** the component using the JCB compiler.
3. **Install or update** it in Joomla.
4. **Refresh** your Admin View to verify the new field placement.

[00:08:49](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h08m49s)
You'll now see that:

* The fields appear where you've placed them.
* The overwritten defaults (e.g., *Created By* and *Created Date*) function normally.
* Their default instances are suppressed, avoiding duplication.

---

## Key Takeaways

* JCB automatically includes default system fields in each view.
* You can safely **overwrite** these fields by creating custom versions with the same names.
* Use the **tab number** to control placement.
* Always **compile and test** your component after overwriting.
* Do **not** modify compiled XML directly - perform changes within JCB.

---

## Summary

Overwriting default fields in Joomla Component Builder provides flexibility in how information is displayed across your component's backend views. Whether you need to reposition fields, show additional metadata, or customize their labels, following this structured method ensures your changes persist through future compiles and updates.

---
