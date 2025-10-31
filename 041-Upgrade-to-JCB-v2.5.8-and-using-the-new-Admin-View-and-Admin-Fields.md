# **Upgrading to JCB v2.5.8 and Using the New Admin View and Admin Fields**

**Video Tutorial Reference:** [Watch on YouTube](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

---

## **Overview**

With the release of **JCB v2.5.8**, Joomla Component Builder (JCB) introduced a major update replacing the old **Repeatable Field system** with the new **Subform Field layout** throughout the Admin View and Admin Fields.
This upgrade improves performance, simplifies data management, and aligns with Joomla 4 standards.

This document explains the transition process, what changes to expect, and how to use the new Subform-based Admin View effectively.

---

## **1. Removal of Repeatable Fields**

[00:00:00](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h00m00s)

In previous JCB versions, Repeatable Fields were used to manage multiple sets of related data across Admin Views, Custom Buttons, and Conditions. Joomla has deprecated these fields due to structural limitations and performance concerns.

In JCB 2.5.8:

* All Repeatable Field structures are replaced by **Subform Fields**.
* The change improves data storage, reliability, and future compatibility.

**Tip:** The pop-up modal Repeatable Fields are gone. Subforms now provide inline editing and a more stable data structure.

---

## **2. Migration of the Admin View to Subform Layout**

[00:01:59](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h01m59s)

The entire Admin View area has been converted to use the Subform layout.
This includes:

* Permissions
* Fields
* Conditions
* Linked Views
* Custom Buttons
* MySQL (Add Tables) connections

Each of these previously used repeatable structures. They are now fully integrated into the Subform format, eliminating the need for modal pop-ups.

---

## **3. Field Organization and New Tabs**

[00:03:13](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h03m13s)

The field organization in the Admin View has been improved:

* The **Fields** and **Conditions** buttons are now under a unified **Fields Tab**.
* A new **Settings Tab**, renamed **Details**, holds other previous repeatable elements.

These adjustments make the interface cleaner and better organized. The upgrade handles all of this automatically, with no manual input required.

---

## **4. Automatic Conversion Scripts**

[00:04:19](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h04m19s)

JCB 2.5.8 includes automated scripts that convert all old Repeatable Field data into the new Subform structure.
These scripts are available on GitHub under the **staging branch**.

The conversion process is handled by the **`convertRepeatable`** function, which:

* Scans for fields such as `ajax`, `custom_button`, and `addtables`.
* Converts old JSON data to Subform-compatible arrays.
* Updates database entries accordingly.

This ensures seamless migration without user intervention.

---

## **5. Model Updates for Conversion**

[00:06:30](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h06m30s)

To guarantee that every field is properly converted, updates were made to the following models:

* `admin_field_conditions.php`
* `admin_view.php`

Within the `getItem()` method of these models:

1. The system checks whether fields have been converted.
2. If not, it converts them during loading.
3. Once converted, they are flagged so the conversion does not run again.

These model changes ensure that the upgrade does not cause conflicts and that the process completes automatically.

---

## **6. Compiler Adaptation**

[00:09:09](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h09m09s)

The JCB compiler has been updated to use the new Subform data structure.
Even if you do not manually open any Admin Views before compiling, the compiler will automatically check and convert data where necessary. This ensures components compile correctly using the latest field format.

---

## **7. Installing the Upgrade to v2.5.8**

[00:11:50](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h11m50s)

To install the upgrade:

1. Download **JCB v2.5.8** from GitHub or your local source.
2. Go to **Extensions → Manage → Install** in Joomla.
3. Upload and install the new JCB package.
4. Wait for the process to complete.

After installation, JCB will begin updating its internal data structures automatically.
Once finished, open any Admin View and refresh to confirm that new tabs and Subform layouts are visible.

---

## **8. New Field and Conditions View**

[00:12:55](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h12m55s)

The Field and Conditions views have been redesigned to use the Subform layout.
All data has been updated and stored in Subform values.

Performance improvements are noticeable, but large datasets may still take longer to load.
It is recommended to avoid more than **50 Admin Fields per view**, as each field line can contain up to 13 subfields.

---

## **9. Editing Fields and Conditions**

[00:14:15](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h14m15s)

Editing is now more direct:

* Use **Edit Linked Fields** or **Edit Field Conditions** buttons.
* Save your work before proceeding.
* Make changes and save or close the window when done.

Only the fields linked to the current Admin View are loaded, which makes editing faster and more focused.

---

## **10. Creating New Fields**

[00:15:42](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h15m42s)

To create a new field:

1. Open **Admin Fields**.
2. Click **Create** or **Create Admin Fields for This Admin View**.
3. Confirm the save, then click the plus icon (+) to add a field.
4. Save and close when done.

Creating a field adds it to the available field list. You can then link it to any Admin View.

There are also shortcut buttons for quick access to **Admin Fields** and **Conditions** directly from the Admin View list.

---

## **11. Creating a New Admin View**

[00:17:35](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h17m35s)

When creating a new Admin View:

1. Fill in the following fields:

   * Single Record Name
   * List Record Name
   * Short Description
   * System Name
2. Save once to generate an ID for the view.
3. Open **Fields and Conditions** to create and link fields.

Saving once is necessary before you can attach fields, as the Admin View must have an ID assigned.

---

## **12. Summary of Key Changes**

| Change                             | Description                                    |
| ---------------------------------- | ---------------------------------------------- |
| Repeatable Fields → Subform Fields | Upgraded to a modern, reliable data structure. |
| New Admin Layout                   | Tabs for Fields, Settings, and Conditions.     |
| Automatic Migration                | Scripts and compiler handle data conversion.   |
| Performance Enhancements           | Faster load times, better scalability.         |
| Joomla 4 Compatibility             | Subforms align with Joomla 4 core standards.   |

---

## **13. Conclusion**

The upgrade to **JCB 2.5.8** marks a significant milestone in improving performance, reliability, and compatibility.
By fully adopting Subform Fields, JCB becomes more stable and future-ready for Joomla 4 and beyond.

---
