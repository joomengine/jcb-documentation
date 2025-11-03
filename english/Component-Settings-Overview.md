# Component Settings

> **Video Source:** [Component Settings](https://www.youtube.com/watch?v=V2WkTjNFjvo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)
---

## Introduction

[00:00:00](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h00m00s)

Once you've added your admin views to the component, JCB provides additional configuration areas known as **Component Settings**. This is where you manage **global configuration fields**, **custom admin menus**, **folders**, and **compiler integration**.

Custom admin menus control the structure of backend menus, while the **component settings** area defines configuration options that apply globally across your component.

> If you need a refresher on everything a component bundles together, start with [Joomla Components in JCB](./Joomla-Components.md). It frames how these settings fit into the wider packaging process.

---

## 1. Compiler Overview

[00:00:51](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h00m51s)

JCB includes an internal **Compiler View**, which exists outside of the standard component structure.
This compiler view requires:

* A **model**
* A **controller**
* A **view**
* Helper and script files

Inside the JCB infrastructure, there's a folder called **custom**. This is where you place files and folders that should be included in your component's compilation.

> **Tip:** Do not remove default content in the `/custom` folder. JCB uses these files automatically during compilation depending on your setup.

[00:02:02](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h02m02s)
The compiler has its own **default files** and an **empty structure** that can be extended with custom logic, including controller and model integrations.

---

## 2. Adding Custom Files and Folders

[00:03:50](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h03m50s)

Custom files and folders allow you to import manually created content into your component at compile time.

**Steps:**

1. Place the files you want to include inside the `custom` folder.
2. Specify the file paths within the Component Settings.
3. Rename them properly using the correct naming convention.
4. JCB will automatically:

   * Create necessary folders in the compiled component.
   * Move your files into those folders.

[00:04:16](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h04m16s)
The process ensures folder creation happens before file copying, maintaining structural integrity.

---

## 3. Creating Custom Admin Views

[00:04:54](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h04m54s)

Use the **Custom Admin Menus** section to define new backend menu items not generated automatically by JCB.

**Example Workflow:**

1. Create a new custom admin menu named **"Compiler"**.
2. Set the **code name** to `compiler`.
3. Choose an appropriate **icon**.
4. Specify its placement, e.g., "before component".

[00:05:17](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h05m17s)
You can configure whether it appears as:

* An admin menu
* A dashboard item
* A submenu

> **Pro Tip:** The compiler view itself can be included in the build through the custom file/folder import feature.

---

## 4. Configuring Global Settings (Config Area)

[00:07:27](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h07m27s)

The **Config Area** in the Component Settings defines your **global configuration fields**, accessible under "Options" in the backend component menu.

### Example: Sermon Distributor Component

In the Sermon Distributor demo, the config section includes multiple **tabs and switches**, such as:

* **Check-in Timer:** Automates periodic check-ins for records.
* **Version Control:** Enables or disables versioning and sets how many versions to retain.

[00:09:07](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h09m07s)

---

## 5. Adding Contributors

[00:09:21](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h09m21s)

Within Component Settings, you can add a **Contributors** section for development credits.

* Add contributor fields or leave empty ones for later entries.
* Control visibility (backend/frontend).
* Define permissions automatically.

This is useful for documenting who helped develop the component.

---

## 6. Including UIkit

[00:10:33](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h10m33s)

You can enable **UIkit** integration directly within the component's settings.
When enabled, UIkit is included automatically throughout your component's admin and site views.

---

## 7. Adding Fields to Config

[00:11:06](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h11m06s)

To add a new field to your component's configuration:

1. Go to **Fields** in JCB.
2. Create a new field (remember its **system name**).
3. Reference it in the Config tab using that same name.

> **Convention:** Fields grouped under the same tab name will appear together in the same configuration section.

Example: The *Dropbox Update Method* fields in the demo component define settings like `local folder` and `download link`.

[00:12:56](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h12m56s)

---

## 8. Spacer HR Field

[00:13:24](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h13m24s)

The **Spacer HR** field is a simple but useful feature for organizing your config layouts.

* Adds visual dividers between field groups.
* Uses automatic naming increments to avoid conflicts.
* Can include **default values** that populate upon installation.

> Default values are stored in the database and loaded automatically during component installation.

---

## 9. Linking Config Tabs to Site Views

[00:14:55](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h14m55s)

If a **Config Tab** name matches a **frontend view name**, JCB will automatically link them.

### Example:

* Config tab: `preachers`
* Site view: `preachers`

This allows global settings to be overridden in specific menu items, similar to Joomla's built-in article settings.

[00:17:07](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h17m07s)

---

## 10. How It Works in the Site View

[00:19:57](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h19m57s)

Each site view has a corresponding **`default.xml`** file that defines available parameters.
When a Config Tab matches the site view name, JCB automatically adds those parameters to the XML.

If something doesn't appear as expected, inspect this file in your site view template.

---

## 11. Quick Overview of Site View Creation

[00:20:45](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h20m45s)

When creating a site view:

* If you **set "Add as Menu" to Yes**, JCB will generate the `default.xml` file automatically.
* If set to **No**, the menu XML file will not exist.

Setting tabs to the same name as your view ensures field mapping and unique configurations for each menu item.

---

## 12. Using Parameters in Code

[00:21:50](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h21m50s)

In your component's PHP view files (`view.html.php`), parameters can be accessed via Joomla's `get()` methods.

```php
$params = $this->state->get('params');
$displayType = $params->get('preachers_display', 'list');
```

This retrieves:

* Menu parameters
* Component parameters
* Global fallbacks (if menu is set to "Use Global")

> **Important:** Field names in config must be **unique**. Reused names can cause conflicts when retrieving params.

---

## 13. Practical Example - Display Modes

[00:25:59](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h25m59s)

In the Sermon Distributor example:

* If `preacher_display = 1` → show **Table**
* If `preacher_display = 2` → show **Grid**
* Otherwise → show **List**

These values are managed globally and accessed dynamically in the frontend view.

---

## 14. Advanced: MySQL Tweak

[00:28:44](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h28m44s)

JCB's **MySQL Tweak** feature lets you **exclude or modify dummy data** during export.
This is particularly useful if you manage **multiple versions** of the same extension at different pricing tiers.

You can control which data gets included when compiling each version.

---

## Conclusion

[00:29:17](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h29m17s)

In this tutorial, we explored:

* Custom admin menus and compiler inclusion
* Adding custom files and folders
* Creating and linking config fields
* Managing global parameters
* Using conventions to link backend settings with frontend menus

Understanding these **component-level settings** allows you to create **powerful, flexible**, and **professionally structured** Joomla components.

---
