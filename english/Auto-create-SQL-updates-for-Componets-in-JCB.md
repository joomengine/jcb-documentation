# Auto Create SQL Updates for Components in JCB

This tutorial demonstrates the **Auto SQL Update Generation** feature in **Joomla Component Builder (JCB)** - a major improvement that automatically creates SQL update scripts when new tables or fields are added to a component.

**Video Source:** [Watch on YouTube](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

---

## 1. Understanding How JCB Manages Tables

[00:00:00](https://www.youtube.com/watch?v=bRPJTRat158&t=00h00m00s)

Every component in Joomla is built around a **set of views**, and each view is linked to a **database table**.
When you install a component, JCB automatically creates the necessary tables for these views. This is why when you create or edit items in the component backend, data is properly stored and retrieved from the database.

---

## 2. Table Creation During Installation

[00:00:38](https://www.youtube.com/watch?v=bRPJTRat158&t=00h00m38s)

When you install a JCB-generated component, the system:

* Builds database tables for each view.
* Sets up field structures for data storage.
* Registers the component so Joomla recognizes and interacts with it properly.

If later you modify the component (for example, adding new tables or fields), you traditionally needed to include **SQL update scripts** manually. This ensures the database schema updates correctly during reinstallation or upgrades.

---

## 3. The Old Method - Manual SQL Updates

[00:01:47](https://www.youtube.com/watch?v=bRPJTRat158&t=00h01m47s)

Previously, JCB required developers to:

1. Open the **Version Updates** tab.
2. Manually add new **SQL statements** (e.g., `CREATE TABLE`, `ALTER TABLE`).
3. Increment the component version manually.

During installation, JCB checked the version difference and executed any pending SQL updates.
While effective, this process was **time-consuming and error-prone**.

---

## 4. Introducing Auto SQL Generation

[00:02:35](https://www.youtube.com/watch?v=bRPJTRat158&t=00h02m35s)

With this new feature, **JCB automatically detects and generates SQL update scripts** when:

* A new **view** (and thus a new table) is added.
* A new **field** is added to an existing table.

Let's walk through a practical example.

---

## 5. Adding a New View

[00:03:14](https://www.youtube.com/watch?v=bRPJTRat158&t=00h03m14s)

### Steps:

1. Open your component in JCB.
2. Add a new **Admin View** called **"Help Documents"**.
3. Adjust the defaults (set its order, label, etc.).
4. Click **Save**.

When saved, this automatically defines a new database table for the view.

Next:

* Go to **Compile → Select your Component → Compile** again.
* The system will detect structural changes and **increment the version number automatically** (e.g., from `1.4.1` to `1.4.2`).

---

## 6. Behind the Scenes: Auto Version Increment

[00:03:51](https://www.youtube.com/watch?v=bRPJTRat158&t=00h03m51s)

During compilation, JCB:

* Checks the **component's change history**.
* Identifies structural updates (new tables or fields).
* Automatically generates the SQL required for these changes.
* Increments the **component version** accordingly.

Once the new component is installed, the new "Help Documents" view appears and its corresponding table is fully functional.
The **Version Updates** tab confirms that:

* Version `1.4.1` added the new table.
* Version `1.4.2` was automatically created and linked with the generated SQL update script.

This reduces manual SQL management and ensures database integrity during upgrades.

---

## 7. Adding a New Field to an Existing View

[00:05:44](https://www.youtube.com/watch?v=bRPJTRat158&t=00h05m44s)

JCB can also auto-generate updates when modifying existing tables.

### Example:

1. Open the **Preacher View**.
2. Add a new field, e.g.,
   **Name:** `Image`
   **Type:** `media` (selectable image upload).
3. Click **Save & Close**.
4. Recompile the component.

Upon compiling, JCB detects the new field addition, updates the schema automatically, and increments the version number again.

---

## 8. Component History and Update Tracking

[00:07:23](https://www.youtube.com/watch?v=bRPJTRat158&t=00h07m23s)

To ensure auto SQL updates function correctly, JCB needs **component history**.

### Important Notes:

* New components automatically record history as you save each view and field.
* Imported or demo components **might lack history**.
  → In this case, open each view and **click "Save"** to initialize history tracking.

History allows JCB to compare current and previous versions, so it knows what SQL changes to generate.

---

## 9. Verifying Auto SQL Update Functionality

[00:08:14](https://www.youtube.com/watch?v=bRPJTRat158&t=00h08m14s)

After recompiling and reinstalling:

* The version increments again (e.g., to `1.4.3`).
* New SQL statements are added automatically:

  * For the **Help Documents** table.
  * For the new **Image** field in the Preacher table.

You can confirm this under the **Version Updates** section:

* Version numbers are incremented correctly.
* Corresponding SQL scripts are present for each change.

---

## 10. Summary & Best Practices

[00:09:55](https://www.youtube.com/watch?v=bRPJTRat158&t=00h09m55s)

The **Auto SQL Update** feature simplifies JCB component evolution by:

* Automatically tracking schema changes.
* Generating precise SQL update scripts.
* Managing version increments seamlessly.

### Recommended Workflow:

1. Always **save each view and field** before compiling.
2. **Recompile** after any structural change.
3. **Check the "Version Updates"** tab to verify SQL changes.
4. **Test installation** to ensure the new fields and tables are working.

---

## 11. Conclusion

This automation makes JCB even more powerful - capable of **writing your SQL updates for you**.
It saves time, prevents errors, and ensures your components remain consistent and upgradeable.

> "Auto SQL generation makes JCB one of the most advanced Joomla development tools - handling database evolution dynamically and intelligently."

---
