# **Adding Admin Views to a Component**

*(Based on the Joomla Component Builder Tutorial Video)*
[Watch Video](https://www.youtube.com/watch?v=39vY66X7GGU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

---

## **Overview**

In this tutorial, we'll explore how to **add admin views** to a component using **Joomla Component Builder (JCB)**.
You'll learn how to connect your created admin views to your component, configure visibility settings, enable key Joomla features like **Auto Check-In**, **Version History**, **Import/Export**, and **Front-End Editing**, and understand how these affect your workflow and generated component.

This section assumes that you have already:

* Installed Joomla Component Builder.
* Created one or more **Admin Views** with fields (see the previous tutorials on Field Types and Admin Views).

---

## **1. Connecting Admin Views to a Component**

[00:00:28](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h00m28s)

1. In JCB, open your **Component** (for example, *Sermon Distributor*).
2. Navigate to **Settings → Admin Views**.
   This is where you link your existing admin views to the component.
3. Click the **Add** button, then select an **Admin View** from the dropdown.
4. Repeat this process for each view you wish to attach.

**Tip:**
If you have many admin views, type the view's name in the search bar to locate it quickly.

---

## **2. Adding View Icons**

[00:01:39](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h01m39s)

When you assign an admin view, you can set an **icon** to represent it in the backend interface.

* JCB uses **Joomla Standard Icomoon Fonts** for these icons.
* When selecting an icon, you'll see a preview immediately.
* The icon you choose appears in the Joomla Administrator's component sidebar and dashboard.

**Tip:**
Choose icons that visually match your view's purpose (e.g., a document icon for "Articles," a user icon for "Authors").

---

## **3. Admin Menu Visibility**

[00:02:29](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h02m29s)

JCB gives you switches to control how each view appears in your component's admin menu.

* **Admin Menu:**
  Enable this if you want the view to appear in the Joomla sidebar (under your component's menu).

---

## **4. Dashboard Item Visibility**

[00:03:04](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h03m04s)

* **Dashboard (List of Records):**
  Adds a shortcut icon to the main dashboard for viewing records.
* **Dashboard (Add Record):**
  Adds a button that allows quick creation of new records directly from the component dashboard.

If you prefer not to show "Add Record" on the dashboard, set it to **No**.

---

## **5. Submenu Inclusion**

[00:03:41](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h03m41s)

You can include or exclude a view from the **submenu** (the collapsible navigation area inside each admin view).

* Enable this if the view should be accessible as a submenu option.

---

## **6. Auto Check-In Feature**

[00:03:57](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h03m57s)

This feature automatically checks in items that have been checked out for longer than a defined period.

* Enable **Auto Check-In** in your admin view settings.
* Configure the timeout duration in your component's **Global Settings** under "Auto Check-In Period."

**Example:**
If a user forgets to close an item, JCB's auto-check-in feature will automatically release the lock after a set time.

---

## **7. Enable Version History**

[00:05:06](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h05m06s)

The **History Component** integration allows Joomla to track every change made to records in your component.

**Steps to Use Version History:**

1. Enable **Keep History** in the Admin View.
2. Edit an item (e.g., "Preacher → A Capella Music").
3. Click **Versions** at the top toolbar.
4. You can:

   * View all previous saved versions.
   * Restore a prior version if needed.

**Tip:**
You can also define how many historical versions Joomla keeps for each item.

---

## **8. Add Metadata Support**

[00:14:23](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h14m23s)

If your view's data will appear on the front end, enable **Metadata** support.

* Metadata adds SEO-related data (title, description, keywords) to your pages.
* While less crucial for search engines today, it still improves content organization and social sharing previews.

Enable metadata for content views that represent unique or indexable front-end pages.

---

## **9. Enable Access Control**

[00:15:37](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h15m37s)

The **Access Switch** enables Joomla's standard access-level dropdown (e.g., *Public*, *Registered*, *Special*).

This helps restrict content visibility based on user roles or groups.

* Enable **Access** in your Admin View if you want per-item access control.
* Often combined with **permissions**, though typically not both at once.

---

## **10. Import/Export Data**

[00:16:38](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h16m38s)

JCB can automatically add **Import/Export** functionality to each admin view.

* Toggle **Export/Import Data** to "Yes" to enable it.
* After compilation, each admin list view will have:

  * An **Export** button (download CSV data).
  * An **Import** button (upload and map CSV data to database fields).

**Note:**
Encrypted fields require care - imported data won't automatically re-encrypt unless handled manually.

---

## **11. Edit/Create Site Views**

[00:18:20](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h18m20s)

This is one of JCB's most powerful features.
When enabled, it allows **front-end editing** of your admin data.

### **How It Works**

1. Enable the switch **Edit Create Site View** in your admin view settings.
2. Upon compiling:

   * JCB generates a **site view** version of your admin form.
   * This includes all fields, validation, and permission checks.
3. You can then add menu links or modules to expose the front-end editing interface.

**Example:**
A "Company" admin view, when enabled, generates a front-end page where logged-in users can:

* Edit company data.
* Add new records (if permitted).

Permissions are enforced automatically - if a user lacks permission to edit certain fields, those will not appear in their form.

**Important:**
JCB generates the front-end code but doesn't automatically create menu links.
You must manually link these site views via Joomla menu items or custom templates.

---

## **12. Ordering and Display**

[00:24:48](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h24m48s)

The **Order** column in the Admin View Settings determines:

* The order in which views appear in the admin sidebar.
* The order of submenu items and icons.

Adjust these numbers to organize your admin panel logically (for example, list views before edit views).

---

## **Conclusion**

Adding and configuring admin views is a critical part of JCB's workflow.
Through these settings, you can define how each view behaves in the backend and, optionally, how it integrates with your site's front end.

By following these steps, you'll ensure your component:

* Is user-friendly for administrators.
* Supports Joomla-native features like auto check-in and version history.
* Provides flexible access and import/export capabilities.
* Can extend seamlessly to the front-end for site-level editing.

---
