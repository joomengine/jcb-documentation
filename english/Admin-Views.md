# **Joomla Component Builder - Admin Views**

### Based on [Admin Views Tutorial](https://www.youtube.com/watch?v=CdSKSCTzmRA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

(*Click on timestamps to view sections in the original tutorial video.*)

---

## **1. Overview**

[00:00:00](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h00m00s)

In this lesson, we explore how to set up **Admin Views** in Joomla Component Builder (JCB).
Admin Views are the **foundation of your component's database structure** - every Admin View corresponds to a **database table** that defines how your component's data is stored and managed.

Before this stage, you should already understand:

* The [JCB! Fields](./JCB-Fields.md) overview that explains how each field definition governs storage, rendering, and sharing
* **Field Types** and **Basic Fields** (previous tutorials)
* The **General Planning** structure of your component

Admin Views bring those fields together to form the actual backend interface and logic of your component.

### What Are Admin Views?

Admin Views form the foundational interface layer of every JCB-built Joomla component. Each Admin View is tightly bound to a
database table and automatically generates the required **forms**, **models**, **controllers**, **list and edit views**, as well as
permission handling and field validation. Because Admin Views produce the entire CRUD stack, every JCB component must include at
least one Admin View to be considered valid and to compile correctly. They ensure your component stays aligned with Joomla's
native MVC architecture and provide a consistent administrative experience out-of-the-box.

### Why Are Admin Views Important?

Admin Views serve as the data anchor for a component:

* Link directly to Joomla database tables
* Automatically attach multiple fields while respecting their visibility and edit permissions
* Enable subforms that reference other Admin Views for nested data structures
* Respect Joomla ACL per view **and** per field
* Remain reusable across multiple components thanks to namespace-aware compilation

This makes Admin Views the heart of every component, defining its schema, edit experience, and administrative backbone. Whereas
Custom Admin Views or Site Views focus on layout and rendering, Admin Views define the structural data definition and baseline logic.

### Versioning and Sharing Admin Views

When you need to update Admin Views in any JCB project you can:

1. Select the views you want to update inside JCB.
2. Click **Reset** to pull the latest version from this repository.
3. Or **Fork** this repository and point your JCB instance to that fork if you need your own baseline.

This workflow keeps shared Admin Views maintainable while giving you the flexibility to customise per project. Remember that Admin
Views are more than UI patterns—they are declarations of how your component manages data. Reviewing the shipped demo component is
an effective way to see best practices in action.

---

## **2. Naming Conventions**

[00:00:35](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h00m35s)

Each Admin View in JCB uses three name identifiers:

| Type            | Description                                | Example                          |
| --------------- | ------------------------------------------ | -------------------------------- |
| **Single Name** | Used for editing a single record           | `preacher`                       |
| **Plural Name** | Used for listing records                   | `preachers`                      |
| **System Name** | Unique name to differentiate similar views | `com_sermondistributor_preacher` |

> **Tip:**
> If you create two components that both have a "preacher" Admin View, use the **System Name** to differentiate them (e.g., include the component name).

This naming system enables **version control** and allows you to reuse Admin Views across different components.

---

## **3. Creating an Admin View**

[00:02:49](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h02m49s)

1. In the JCB dashboard, go to **Admin Views** → **New**.
2. Fill in the **Single Name** (e.g., `preacher`) and **Plural Name** (`preachers`).
3. Optionally add a **Short Description** and **Full Description**.
4. Set the **Type**:

   * `Read/Write` → fields editable
   * `Read Only` → view-only access

> **Note:**
> Fields like **Modified By** are automatically updated and cannot be manually edited.

---

## **4. Assigning View Icons**

[00:04:16](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h04m16s)

Icons appear on the admin dashboard for each view.

1. Hover over the icon field to see recommended dimensions.
2. Choose **Add Icon** or **Icon** → browse the `/images` folder.
3. Select an image that visually represents your view (e.g., category, preacher).

> **Tip:**
> For consistent design, use matching icons across all related views (e.g., if categories apply to all entities, use the same icon for each).

---

## **5. Permissions Setup**

[00:06:15](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h06m15s)

JCB integrates Joomla's Access Control List (ACL) but extends it with **granular, per-view permissions**.

### Common Permission Types

| Permission                        | Description                           |
| --------------------------------- | ------------------------------------- |
| **core.edit** / **view.edit**     | Edit access (global or view-specific) |
| **core.create** / **view.create** | Allow new records                     |
| **core.delete** / **view.delete** | Allow deletion                        |
| **core.edit.state**               | Change publish/unpublish state        |
| **core.edit.own**                 | Edit only one's own records           |
| **core.access**                   | View-only access                      |
| **core.batch.use**                | Control access to batch operations    |

**Core** = global setting (applies to all views)
**View** = specific setting (applies only to the given view)

> **Best Practice:**
> Use **view-prefixed permissions** (`view.edit`, `view.delete`, etc.) for large components where each view has distinct rules.

Permissions can also target **individual fields** via the **Permission Switch** in the Field configuration.

---

## **6. Tabs**

[00:19:26](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h19m26s)

Tabs organize fields in the backend form layout.

* **Automatically Created Tabs:**

  * *Publishing* (default system fields)
  * *Permissions* (if permissions are enabled)

* **Custom Tabs:**
  You can create tabs like *Details*, *Sermons*, *Settings*, etc.

Each field must specify its **Tab Number** (1, 2, 3, etc.) in the field settings.
JCB will place the field inside the corresponding tab.

---

## **7. Linked Views**

[00:20:53](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h20m53s)

Linked Views connect two Admin Views (parent-child relationship).
Example: *Preacher → Sermons.*

### Steps to Create a Linked View

1. In the **Parent View** (`preacher`), open the **Linked Views** tab.
2. Select the **Child View** (`sermons`).
3. Set:

   * **Tab** (e.g., Sermons tab)
   * **Parent Key** → `id` (from parent)
   * **Child Key** → related field (e.g., `preacher`)
4. Enable **Add New Button** if you want to allow new child entries from within the parent view.

> **Tip:**
> Make sure the database relationships match - the child table should store the parent's ID.

---

## **8. Field Configuration**

[00:32:30](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h32m30s)

Once the view is created, assign fields to it:

1. Go to **Fields** tab in the Admin View.
2. Use the search bar to find your field.
3. Configure options:

   * **Show in Admin List** - display in list view
   * **Order** - display position
   * **Sortable / Searchable / Filterable / Clickable** - enable these features

> **Example:**
> The *Name* field can be made **clickable**, opening the edit view directly.

> **Joomla Integration Tip:**
> Always include a **Title** and **Alias** field for frontend-ready views (important for SEO, history, and tags).

---

## **9. Field Alignment**

[00:37:54](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h37m54s)

Control where a field appears in the edit form:

| Position                | Description                    |
| ----------------------- | ------------------------------ |
| Right / Left **in** tab | Inside the current tab         |
| Right / Left **of** tab | Outside tab area               |
| **Above** tab           | Always visible at top          |
| **Below** tab           | Appears below all tabs         |
| **Full width**          | Spans across full layout width |

Full-width fields appear below left and right sections.
You can also **add permission controls** to individual fields.

---

## **10. Field Titles and Aliases**

[00:41:39](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h41m39s)

* Each view should have **only one Title** and **one Alias**.
* The system ignores duplicates.
* Set **Filter**, **Sortable**, and **Clickable** options as needed.

---

## **11. Conditional Fields**

[00:43:47](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h43m47s)

Conditions define when a field should appear based on the values of others.

### Example:

> Show *Custom Script* field only when *Add JavaScript* = Yes.

Use:

* **Target Field:** the field to show/hide
* **Action:** `Show` or `Hide`
* **Condition Field:** controlling field
* **Value:** trigger value

This system extends Joomla's basic "ShowOn" logic and compiles into custom JavaScript automatically.

---

## **12. Isolate and Chain**

[00:45:55](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h45m55s)

Used when **multiple conditions** must be true.

* **Isolate** - separate conditions (only one triggers)
* **Chain** - all conditions must be true

> **Example:**
> Show "Dropbox Auto Note" only if:
>
> * Source = Dropbox
> * Built Option = Automatic

JCB's compiler generates all necessary JavaScript logic automatically.

---

## **13. Adding Custom Code (CSS, JS, AJAX, PHP)**

[01:00:18](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=01h00m18s)

You can insert **custom scripts** directly within your Admin View:

### CSS

Add custom CSS for:

* **Single (Edit)** view
* **List** view

### JavaScript

Choose between:

* **File inclusion** (adds to JS file)
* **Footer inclusion** (inline script block)

### AJAX Integration

[01:01:48](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=01h01m48s)

JCB generates an `ajax.json.php` controller and `ajax` model automatically.

1. Define your **AJAX task** and **method** (public).
2. Add input values like `view`, `type`, or `user`.
3. Use `checkDropboxListing` (from the tutorial) as a working example.

AJAX logic ensures secure token validation and can run global events such as updating lists or external data.

---

## **14. PHP Hook Methods**

[01:10:41](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=01h10m41s)

You can inject PHP code in these model/controller methods:

| Method                       | Purpose                                |
| ---------------------------- | -------------------------------------- |
| `getItem()`                  | Modify fetched data before rendering   |
| `save()`                     | Run custom code before save            |
| `postSaveHook()`             | Run code after save (controller-level) |
| `batchCopy()`, `batchMove()` | Customize batch operations             |

> **Tip:**
> Write your logic inside the PHP block and use `parent::save($data)` after your modifications.

---

## **15. MySQL Dump Test Data**

[01:15:06](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=01h15m06s)

JCB can **generate test data dumps** to preload your component with sample records.

1. Go to the **MySQL Dumps** tab.
2. Select the table to dump (e.g., `sermon`).
3. Click **Export** → generates SQL structure and inserts.
4. Replace table prefixes (`cb_` → `#__`) for Joomla compatibility.
5. Save to your component for reuse during reinstallation.

> **Benefit:**
> Saves time during testing since you can reinstall your component with demo data preloaded.

---
