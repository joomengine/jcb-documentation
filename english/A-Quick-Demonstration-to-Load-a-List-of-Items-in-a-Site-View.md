# A Quick Demonstration to Load a List of Items in a Site View

This tutorial demonstrates how to build and configure a **List View** in Joomla Component Builder (JCB) using both **Dynamic GET** and **AJAX (FooTable)** methods. It also covers how to integrate the list into a Site View, adjust templates, and manage configuration fields - following the exact Joomla Component Builder workflow.

>  **Goal:** Load a list of items (sermons, in this case) in a Joomla Site View without filters, complete with pagination and layout control.

---

## Overview
In Joomla Component Builder, **Site Views** define what users see on the frontend. You can use **Dynamic GET queries** to pull data from your database tables and display it in lists, grids, or tables.  
This tutorial extends the Sermon Distributor example component to demonstrate loading **all sermons** in a single site view, with flexible display options.

---

## Step 1: Review Existing Site Views  
[00:00:35](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h00m35s)

Begin by examining your existing Site Views inside JCB.  
In this example, the Sermon Distributor component already includes several views:

- Sermons  
- Preachers  
- Series  
- Categories  
- API  

For this tutorial, we'll modify the **Preachers** view because it's a **List Query**, suitable for demonstration.

---

## Step 2: Understand the Two List-Building Methods  
[00:01:05](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h01m05s)

There are **two main approaches** to load a list of items in a site view:

1. **Dynamic GET (standard method)**  
   - Built directly within JCB.  
   - Good for small to medium datasets (~100 items per page).  
   - Uses pagination.  

2. **AJAX (advanced method using FooTable)**  
   - Loads large datasets (up to 10,000 items).  
   - Uses asynchronous loading via JavaScript and JSON endpoints.  
   - Ideal for responsive and editable tables.

> **Tip:** If your dataset exceeds ~100 records per page, prefer the AJAX + FooTable approach for better performance and user experience.

---

## Step 3: Review the AJAX FooTable Example  
[00:02:35](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h02m35s)

FooTable dynamically loads data into an HTML table with only minimal JavaScript:

- A **URL for the column headers** (JSON source)  
- A **URL for the item data** (JSON endpoint)  

```html
<table id="sermons-table" class="footable"></table>
<script>
  $('#sermons-table').footable({
      "columns": "path/to/columns.json",
      "rows": "path/to/items.json"
  });
</script>
````

This method supports:

* **Responsive layouts**
* **Instant editing**
* **Pagination within the table**

> ⚙️ Joomla also provides similar table libraries, but FooTable remains a reliable, lightweight solution that integrates smoothly with JCB.

---

## Step 4: Build a Dynamic GET Query

[00:06:00](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h06m00s)

Navigate to **Dynamic GETs** in JCB.
You'll see existing queries - for example, fetching sermons or preachers. Each "List Query" retrieves multiple records from the database.

We'll create a new one called **`Sermons All`**.

1. **Duplicate** an existing Sermons GET query.
2. Rename it to **`Sermons All`**.
3. Remove unnecessary filters (like `preacher_id`).
4. Keep only the **access level** filter for good practice.

This ensures that all sermons are loaded, respecting Joomla access permissions.

---

## 🔗 Step 5: Understanding Helper Routes

[00:08:01](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h08m01s)

JCB auto-generates helper classes (e.g., `/helpers/route.php`) that build frontend URLs dynamically.
Each list or item link uses route helpers like:

```php
SermondistributorHelperRoute::getSermonRoute($slug);
SermondistributorHelperRoute::getSeriesRoute($slug);
```

These static methods:

* Create SEO-friendly URLs based on the item's slug (`alias:id`).
* Append the correct `Itemid` for menu context.
* Use `JRoute::_()` to convert URLs according to Joomla's SEF settings.

> **Note:** You rarely need to manually modify these - JCB handles their generation dynamically.

---

## Step 6: Create the Site View "All Sermons"

[00:14:27](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h14m27s)

Now that we have a working query, create a new **Site View** called **"All Sermons"**:

1. Duplicate the existing **Preachers** or **Sermons** site view.
2. Rename it to **All Sermons**.
3. Update the **Dynamic GET** source to `sermons_all`.
4. Update `params` keys and references from `preacher` to `all`.
5. Adjust context values to use `sermon` for permissions.
6. Remove preacher-specific areas (like hit counters or preacher info).

This ensures the new view cleanly represents all sermons without filters.

---

## Step 7: Adjust Templates and Layouts

[00:19:08](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h19m08s)

In your JCB **Templates** area, locate and update the following layouts:

* `sermons_table`
* `sermons_grid`
* `sermons_list`

Within each:

* Replace any `SView` placeholder with `all`.
* Update params for sermon description, category, and hits.

> **Tip:** If params aren't defined yet in the component config, they'll fall back to `0` - meaning no data loads. You'll fix this in the next step.

---

## Step 8: Extend Component Configuration Fields

[00:31:52](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h31m52s)

The component's configuration defines global display options such as:

* List style (table/grid/list)
* Show/Hide description, hits, downloads, etc.

To support the new "All Sermons" view:

1. Go to **Component Config** in JCB.
2. Duplicate the relevant "Preacher" fields.
3. Rename each to use the prefix `all_` (e.g., `all_display`, `all_hits`, `all_description`).
4. Mark them as **Global**.
5. Add them under a new tab: **All**.

This ensures your "All Sermons" view has its own customizable options.

---

## Example: Adding Config Fields

Example duplicated field:

```
Label: Show Sermon Description
Name: all_description
Type: Radio (Yes/No)
Default: Yes
```

Add others for:

* `all_table_grid_list`
* `all_hits`
* `all_icon`
* `all_colour`

After saving, JCB will include them in your component's `/config.xml`.

---

## Step 9: Compile and Install the Component

[00:25:38](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h25m38s)

1. Click **Compile Component**.
2. Install the generated ZIP file through Joomla's Extension Manager.
3. Verify the new **All Sermons** site view appears in your menu item options.
4. Set appropriate **permissions** under *Options → Permissions* (e.g., allow public access).

---

## Step 10: Test the Frontend Display

[00:29:38](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h29m38s)

After creating and publishing sermons, refresh the frontend.

You should now see:

* All sermons listed in a paginated table.
* Correct series, category, and hit data.
* Working pagination (up to 100 items per page).
* Configurable layouts (grid/table/list) via backend options.

---

## Step 11: Verify Config Options

[00:37:10](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h37m10s)

Open your component's backend → **Options**.
You'll now see a new **All** tab with settings such as:

* Display Style (Table / Grid / List)
* Show Hits
* Show Description

Adjust and test these to confirm the view updates dynamically.

---

## Summary

You've successfully:

* Created a **Dynamic GET** query to load all items.
* Built a **new Site View** called *All Sermons*.
* Updated **templates and params** for the new view.
* Added **component configuration fields** for custom layout control.
* Compiled and tested your component in Joomla.

This same process can be used to create similar "All Items" views for any entity in your JCB-built components.

---

## Developer Notes

* Dynamic GETs are stored under `/admin/models/get/` after compile.
* Template overrides can be added under `/site/views/[view]/tmpl/`.
* Config fields map to XML definitions in `/admin/config.xml`.
* Use `JRoute::_()` for SEF-compliant links.
* Pagination defaults are managed through Joomla's core `pagination.php`.

---
