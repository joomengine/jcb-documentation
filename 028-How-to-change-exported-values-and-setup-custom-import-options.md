# How to Change Exported Values and Set Up Custom Import Options

**Tutorial Source:** [Watch the video](https://www.youtube.com/watch?v=fau5mZ6naLc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)
**Component Example:** *IP Data*
**Last Updated:** Compatible with the latest Joomla Component Builder (JCB) version (2025)

---

## Introduction

[00:00:00](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h00m00s)

Joomla Component Builder (JCB) provides built-in **Import** and **Export** functionality in all List Views of your components.
This feature allows you to:

* Export selected data from the component backend into formats like `.xls`
* Import data back into the component for mass updates or migrations

In this tutorial, you will learn:

1. How to **customize exported values** (e.g., replacing country codes with names)
2. How to **create custom import logic** (e.g., handling unique identifiers other than IDs)

---

## Example Setup: IP Data Component

[00:00:35](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h00m35s)

We'll use the **IP Data** component as an example.
This component tracks IP addresses, translates them into countries, and updates cost data based on IP regions.

### Example: IP Tables View

[00:01:07](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h01m07s)

In the *IP Tables* dashboard, typical fields include:

* `CNTRY` - the country code
* `REGISTRY` - organization that owns the IP range
* `IP From` and `IP To` - the IP range values

---

## Export Feature Overview

[00:01:26](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h01m26s)

When clicking **Export Data**, note the following behavior:

* If **no rows are selected**, JCB warns:
  *"Please first make a selection from the list."*
* To export **all records**, select *All* in the list view options.

> **Tip:**
> Avoid exporting very large datasets through Joomla (e.g., over 3,000 items).
> Instead, use MySQL to export via a **database dump file** for efficiency.

[00:02:16](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h02m16s)

While JCB List Views can handle up to 10,000 items, complex relationships can slow down the process - especially when exporting.

---

## Customizing Exported Values

[00:02:51](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h02m51s)

You may want to replace certain database codes (like "AUS") with full names ("Australia") during export.
This can be done programmatically in the **getExportData** method.

---

### Step 1: Locate the Export Function

[00:03:26](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h03m26s)

Open the model related to your Admin View.
JCB includes a method called:

```php
public function getExportData()
```

This method includes a variable:

```php
$_export = true;
```

[00:03:52](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h03m52s)

This variable is set **only** when an export operation occurs.
You can use it to **target custom code** that modifies the export output.

---

### Step 2: Understanding Custom PHP Injection

[00:04:54](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h04m54s)

To modify export behavior, go to:

**Admin View → PHP Tab → Add PHP (getListQuery - JModelList)**
Set **"Yes"** to enable PHP customization.

Code added here is injected into **both**:

* `getListQuery`
* `getExportData`

[00:05:43](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h05m43s)

> **Tip:**
> The same logic that modifies list view queries can also alter exported data.
> Use `$_export` checks to distinguish between them.

Example:

```php
if (isset($_export) && $_export) {
    // Modify or replace data before export
}
```

[00:06:22](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h06m22s)

You can verify occurrences of `$_export` across List Models to see where export-specific logic applies.

---

### Step 3: Avoid Display Formatting in Exports

[00:07:25](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h07m25s)

Don't include **HTML formatting** (like color or styling) in export data.
The export process should focus purely on **raw values**, not presentation.

---

### Step 4: Modify Data Before or After Translation

[00:08:30](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h08m30s)

You can also use:
**Admin View → Add PHP (getItems Method - before translation fix & decryption)**

Here you can add logic like:

```php
if (isset($_export) && $_export) {
    // Modify values before translation/decryption during export
}
```

This ensures the data is changed **only** during export and not in normal list view rendering.

---

## Import Features Overview

[00:09:32](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h09m32s)

JCB's **Import feature** allows data to be brought back into a component via CSV or XLS files.

[00:09:40](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h09m40s)

* If an **ID** exists in the file, JCB updates the record.
* If the **ID** is missing, JCB creates a new record.

If you want to import data based on **non-ID fields** (like a username or reference code), you'll need a **custom import script**.

---

## Creating a Custom Import Script

[00:10:13](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h10m13s)

### Step 1: Enable Custom Import

In the **Admin View**, go to the **Custom Import** tab and set:

```
Custom Import: Yes
```

This loads JCB's default import script into editable areas.

[00:10:38](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h10m38s)

> **Warning:**
> Only modify this if you're familiar with PHP and import logic.
> Otherwise, practice basic PHP or MySQL courses first (e.g., on Lynda.com or Udemy).

---

### Step 2: Edit and Customize

[00:11:09](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h11m09s)

You can:

* Add new logic (e.g., map fields differently)
* Insert extra validation
* Change how rows are matched and saved

Once edited, click **Save** and **Compile** the component.

---

### Step 3: Test and Verify

[00:11:59](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h11m59s)

After compiling:

* Perform an import test using your modified script.
* Check if your custom logic (e.g., name lookup or field mapping) works correctly.

> **Tip:**
> The **default import logic** remains available even when you enable custom import.
> This means you can maintain **two import modes** side by side.

---

## Advanced Usage Example

[00:13:06](https://www.youtube.com/watch?v=fau5mZ6naLc&t=00h13m06s)

If you need to handle **large CSV imports** (e.g., 4,000 to 40,000 lines) and only specific columns should be imported,
the Custom Import area gives you full control to script such selective imports.

This flexibility allows complex integrations like:

* Bulk product or user imports
* External database synchronization
* Conditional updates

---

## Summary

| Feature                   | Description                            | Key File / Setting              |
| ------------------------- | -------------------------------------- | ------------------------------- |
| **Export Customization**  | Modify data before export              | `getExportData()` in List Model |
| **Export Check Variable** | Used to detect export mode             | `$_export = true`               |
| **Avoid Formatting**      | Keep export data plain                 | Remove HTML formatting          |
| **Custom Import Enable**  | Load and edit import logic             | Admin View → Custom Import Tab  |
| **Dual Import Mode**      | Retain both default and custom imports | Custom + Default active         |

---

## Helpful Tips

* Always **backup** your component before changing export/import code.
* Test export data using small datasets first.
* Avoid running custom imports on production before validating in a test environment.
* Use **MySQL tools** for massive imports beyond Joomla's memory limits.

---

### Final Thoughts

This feature set makes JCB exceptionally powerful for large-scale data management.
By mastering custom **export and import scripting**, you can make your Joomla components behave like professional, data-driven systems adaptable to any client's needs.

---
