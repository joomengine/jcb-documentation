# Automated Database Updates in Joomla During Component Development

## Overview

**Timestamps from transcript included for reference**

Joomla Component Builder (JCB) automates database table creation and updates during component development by adhering to Joomla's native SQL file conventions. This automation ensures that your component stays synchronized with database changes-whether you're adding new views, creating new fields, or restructuring existing ones.

[00:00:00](https://www.youtube.com/watch?v=zN2M15fzf_M)

When you compile a JCB component, such as **Sermon Distributor**, JCB generates a file structure consistent with Joomla standards. Inside the compiled component (`com_sermondistributor`), navigate to:

```
admin/sql/
```

Here, you'll find the **install.mysql.utf8.sql** file-Joomla's standard script for creating the initial database tables during installation.

---

## Understanding Joomla's SQL Behavior

[00:01:17](https://www.youtube.com/watch?v=zN2M15fzf_M)

* The `install.mysql.utf8.sql` file runs **only once**-on the first installation.
* Even if you modify or add new data later, Joomla will **not re-run** this file.
* JCB automatically keeps this file updated with any new views (tables) or fields (columns) you add.
* However, these updates only matter for **new installations**, not for sites where the component is already installed.

For existing installations, Joomla uses **update SQL files** located in the `updates` folder.

---

## How JCB Handles Updates

[00:02:44](https://www.youtube.com/watch?v=zN2M15fzf_M)

1. **Install the Component**
   Install your component to initialize the database schema.

2. **Add a New Field**
   Example: In the Admin View "Sermon," add a field named **Mobile Phone** in the fourth position (left tab).

3. **Add a New View (Optional)**
   You can add an entirely new view at this stage.
   JCB will detect **both changes** (the new field and the new view) and prepare an **SQL update file** that includes both.

[00:03:34](https://www.youtube.com/watch?v=zN2M15fzf_M)

4. **Compile the Component**
   After saving your changes, run the **compiler** again.
   JCB automatically increments the component version-e.g., from `2.0.0` to `2.0.1`-and generates a new SQL update file.

5. **Check the Generated Files**
   Extract your compiled component and open:

   ```
   admin/sql/updates/
   ```

   You'll find the new versioned SQL update file, e.g. `2.0.1.sql`.

---

## Inside the Update File

[00:04:53](https://www.youtube.com/watch?v=zN2M15fzf_M)

Each new update file may contain:

* SQL statements to **add new fields** to existing tables.
* SQL statements to **create new tables**.

For example:

```sql
ALTER TABLE `#__sermondistributor_sermon` ADD `mobile` VARCHAR(255) NOT NULL;
CREATE TABLE `#__sermondistributor_look` (...);
```

When you install this updated component:

* The **Mobile** field appears in the `Sermon` table.
* The **Look** table is newly created.

---

## Version Management

[00:06:09](https://www.youtube.com/watch?v=zN2M15fzf_M)

JCB automatically increments the component version with every compile that includes database changes. Inside JCB:

* Open your component's **Updates** area.
* You'll see versioned entries with corresponding SQL changes.
* Update the **update server URL** manually, as it cannot be dynamically determined.

This URL is referenced in the component's **update server XML** file, ensuring Joomla can fetch updates properly.

---

## Workflow for Reliable Database Updates

1. **Make a change** (new field, view, or relationship).
2. **Save & Close** the affected item.
3. **Compile the component** to trigger version increment.
4. **Install or update** the component in Joomla.
5. **Verify database changes** in phpMyAdmin or another DB tool.

---

## When JCB's Automation May Not Work as Expected

[00:07:24](https://www.youtube.com/watch?v=zN2M15fzf_M)

One known scenario involves **importing or exporting** components between JCB instances.

When you import a component:

* JCB recreates all structural data but **does not restore the component's change history** or **asset IDs**.
* Without this history, JCB cannot detect what has changed, so it won't generate proper SQL updates.

---

## Restoring History After Import

[00:08:02](https://www.youtube.com/watch?v=zN2M15fzf_M)

To re-establish change tracking:

1. Open each **Admin View** and click **Save & Close**.
2. Open each **Field** in the view and **Save** it again.

Doing this creates baseline history entries in JCB.
From that point, JCB can detect subsequent changes properly.

[00:08:36](https://www.youtube.com/watch?v=zN2M15fzf_M)

After saving:

* Compile the component.
* Begin making new changes as usual.

This ensures the component's lifecycle and database updates behave naturally again.

---

## Best Practices

* **Always save** after editing views or fields before compiling.
* **Do not skip** saving after import; it's essential for version tracking.
* **Review the SQL updates folder** after each compile to verify new files.
* **Use clear versioning** (e.g., 1.0.0 → 1.0.1 → 1.1.0) to maintain update clarity.
* **Keep backups** of your component and database before major updates.

---

## Conclusion

[00:09:51](https://www.youtube.com/watch?v=zN2M15fzf_M)

JCB's integration with Joomla's SQL update convention ensures that database structures evolve smoothly as your component grows.
By following proper save-compile-update workflows, you can maintain robust, version-aware, and auto-updating components without manual SQL management.

[00:10:16](https://www.youtube.com/watch?v=zN2M15fzf_M)

This automated process streamlines Joomla component development, minimizing errors and aligning perfectly with Joomla's standard database update behavior.

---
