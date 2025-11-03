# Manage a Component's Global Config Option Field in Relation with Menu Params

## Overview

This tutorial explains how to **manage global configuration option fields** in your Joomla Component Builder (JCB) component and how those same fields can be linked to **menu parameters** for specific site views.

You'll learn:

* How global options relate to menu view options.
* How to control where certain fields appear - either in **Global Config**, **Menu Params**, or **both**.
* How to use the `display` property in JCB to dynamically assign field visibility.

---

## 1. Understanding Global Configuration Options

**[00:00:18](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h00m18s)**

In Joomla, **Global Configuration Options** define default behaviors for your component. These can later be overridden by **menu parameters** for individual menu items.

> For example, you may want a setting to appear:
>
> * Only in your component's *Global Configuration* area.
> * Only in a *Menu Item's* parameters.
> * Or in *both*.

JCB allows you to achieve this distinction easily using a `display` property.

---

## 2. Reviewing Existing Configuration Fields

**[00:01:43](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h01m43s)**

Open your component in JCB (for example, **Member Manager**) and locate the **Global Config Fields** area.

1. Navigate to your component in **Components** → **Member Manager**.
2. Observe existing config fields - these are used in both the component's config and menu options.
3. If none exist, click **➕ (Add New Field)** to begin.

You'll notice that each field's behavior is largely determined by its **extra properties**, which we'll look at next.

---

## 3. Understanding the `display` Property

**[00:04:31](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h04m31s)**

Each field in JCB's Field Manager has an *Extra Properties* section.
A key property is **`display`**, which determines where the field appears:

| Property Value | Field Appears In                   |
| -------------- | ---------------------------------- |
| *(empty)*      | Both Global Config and Menu Params |
| `menu`         | Menu Params only                   |
| `config`       | Global Config only                 |

> **Tip:**
> Leaving `display` blank is equivalent to the legacy behavior - the field appears in both Global and Menu contexts.

Example:

```text
display = menu
```

This setting ensures that the field is visible **only** in menu parameters.

---

## 4. Demonstration: Field Visibility Control

**[00:05:10](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h05m10s)**

When the `display` value is set to **menu**, the field will **not appear** in the Global Configuration area, but **will appear** under a site view's menu parameters.

If you:

* Go to **Global Config** → your component → *members* tab → the field won't be visible.
* Go to **Menus** → *Add Menu Item* → select the corresponding view → the field **is** visible.

This confirms the field's correct placement.

---

## 5. Creating a New Field for Both Global Config and Menu Params

**[00:07:08](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h07m08s)**

Let's add a new field called **"Show Title"**.

### Steps:

1. Go to **JCB → Fields → New**.
2. Set:

   * **Name:** `show_title`
   * **Label:** `Show Title`
   * **Type:** `Radio`
   * **Description:** "Select if the title should be shown."
   * **Options:** Yes / No
   * **Default:** `1` (Yes)
3. Leave **`display`** blank to make it appear in both Config and Menu areas.
4. Save the field.

Next, add this field to your component's **Global Config**.

### Add Field to Config Tab:

1. Open your component (e.g., *Member Manager*).
2. Click the **Global Config (+)** button.
3. Create a tab with the same name as the target **site view** (e.g., `cpanel`).
4. Add your new field `show_title` to this tab.
5. Save and close.

Compile and install the component to apply the changes.

---

## 6. Verifying the Field in Joomla

**[00:08:37](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h08m37s)**

After installation:

* Open **System → Global Configuration → Member Manager**
  You'll see a **Cpanel** tab with the new **Show Title (Yes/No)** field.
* Create or edit a **menu item** linked to this component's site view.
  Under the **Member Manager** tab, the **Show Title** field also appears, including an option to *"Use Global"*.

> This allows Joomla menu items to **inherit or override** the component's global value.

---

## 7. Restricting a Field to Global Config Only

**[00:09:33](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h09m33s)**

To make a field appear **only in Global Config**:

1. Edit the field in JCB → **Fields Manager**.
2. Under *Extra Properties*, set:

   ```text
   display = config
   ```
3. Save, compile, and reinstall the component.

### Verify:

* The field **disappears** from the menu item parameters.
* It **remains visible** in the component's global configuration area.

---

## 8. Restricting a Field to Menu Params Only

**[00:10:30](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h10m30s)**

To move the field exclusively to the **menu area**:

1. Edit the same field again.
2. Set:

   ```text
   display = menu
   ```
3. Save, compile, and reinstall.

Now:

* The field is **only visible in Menu Params**.
* It is **hidden** from the Global Config screen.

> **Note:**
> In JCB version 2.9.15 and later, this behavior has been fixed to properly remove the "Global" reference when the field is menu-only.

---

## 9. Field Naming & Site View Alignment

**[00:12:02](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h12m02s)**

When assigning fields to config tabs, the **tab name must match** the **site view name**.

To find this:

1. Go to **Site Views** in JCB.
2. Open the desired site view (e.g., `cpanel` or `members`).
3. Use the **Name** value (not the title) as the **tab name**.

This ensures that menu parameters properly connect to the corresponding site view tab.

---

## 10. Scope and Behavior Notes

**[00:12:52](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h12m52s)**

* The `display` property only applies to **configuration fields** that belong to a tab matching a site view.
* It does **not** affect **admin views** or regular fields within backend forms.
* When a field is used across multiple components, its `display` behavior remains consistent in each.

---

## 11. Wrapping Up

**[00:14:18](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h14m18s)**

You've now learned how to:

* Create and configure global fields in JCB.
* Control their display between Global Config and Menu Params using the `display` property.
* Correctly assign fields to tabs that align with your site view names.

If you encounter issues or have feature requests:

* Visit the [JCB Forum](https://github.com/orgs/joomengine/discussions)
* Or open an issue on [GitHub](https://github.com/vdm-io/Joomla-Component-Builder/issues)

---

### **Summary Table**

| Goal               | `display` Setting | Visible In    |
| ------------------ | ----------------- | ------------- |
| Both Global + Menu | *(blank)*         | Both          |
| Global Config only | `config`          | Global Config |
| Menu Params only   | `menu`            | Menu Options  |

---
