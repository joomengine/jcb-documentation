# **Major Release of Joomla Component Builder (JCB) v2.6.0**

## Overview

**JCB v2.6.0** marks a significant upgrade that modernizes how components are structured and managed. The most notable change is the **complete removal of all Repeatable Fields** within the Joomla Component area. This improvement ensures better data handling, performance, and compatibility with Joomla 4 and beyond.

This documentation explains the key changes, provides upgrade guidance, and clarifies how the new system works to maintain backward compatibility while offering a more robust architecture.

---

## **1. Removal of Repeatable Fields**

[00:00:00](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h00m00s)

Repeatable fields were once widely used in JCB's Component Area to manage collections of related values. However, these fields have now been **entirely replaced** with **SubForm fields** and dedicated tables.

### Why the Change Was Necessary

[00:00:43](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h00m43s)

Previously, Repeatable Fields used JavaScript to combine multiple values into a single string for storage. While efficient, this approach had drawbacks:

* It stored data as a single string, limiting database normalization.
* Validation was less precise compared to structured SubForms.
* Joomla 4 officially deprecated Repeatable Fields, requiring a new solution.

### New Approach

[00:01:13](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h01m13s)

The new **SubForm** structure:

* Creates **dedicated tables** for previously repeatable datasets.
* Improves **data validation** and **integrity**.
* Reduces **page load weight** by handling complex data through relational structures.

This change required the addition of approximately **nine new database tables** to support the new architecture.

---

## **2. Impact Scope – Only the Component Area**

[00:02:03](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h02m03s)

The restructuring primarily affects the **Joomla Component Area**. However, because JCB is highly dynamic and interconnected, the impact extends to several other areas that depend on these data structures. The upgrade process ensures compatibility across the entire system.

---

## **3. Compiler and Package Import/Export Upgrades**

[00:02:20](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h02m20s)

The **Compiler** and **Package Import/Export** systems have been upgraded to align with the new SubForm data model. All import/export actions now handle data more reliably.

**Testing results** show a smooth transition with minimal user intervention needed. Users upgrading from older versions should experience no data loss or corruption.

---

## **4. Clear Browser Cache and Memory**

[00:02:47](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h02m47s)

After upgrading:

* **Clear your browser cache and memory**.
  Residual JavaScript from the old Repeatable Field system can conflict with the new scripts.
* Clear **browser history** specific to your JCB domain if you prefer not to clear all history.

This ensures new scripts load properly, preventing any UI or functionality issues.

---

## **5. Dynamic GET Builder Conflicts**

[00:03:29](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h03m29s)

Some users may encounter temporary issues with the **Dynamic GET Area**, which fetches data dynamically from Admin Views.

If this feature does not work as expected:

1. Clear the **browser memory**.
2. Reload the page and try again.
   Most issues are due to cached JavaScript conflicts and not bugs in the system.

---

## **6. Upgrading via Joomla's Management Area**

[00:05:13](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h05m13s)

To perform the upgrade:

1. Navigate to **Components → Joomla Component Builder → Updates**.
2. Confirm that the **v2.6.0** update is available.
3. Click **Update**.
4. Once complete, return to JCB and verify that it shows **"up-to-date."**

No manual migration steps are necessary - the upgrade process handles conversions automatically.

---

## **7. Editing Components After Upgrade**

[00:06:09](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h06m09s)

While the layout of the Component Edit area remains familiar, interaction patterns have changed.

### Key UI Updates

* **Modal-based editors** (used for updates, views, etc.) are now replaced by **dedicated views**.
* When editing updates, admin views, or site views, JCB will open these in full-page views for better control.
* You'll be prompted to save all changes before switching views.

This improves stability and editing precision across multiple areas.

---

## **8. Contributors and Component Files**

[00:07:00](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h07m00s)

* **Contributors**: Now editable directly within the main Component page.
* **Component Files and Folders**:
  These have been moved to a **joint table**, improving performance and simplifying file management.
  Use the "Edit component files/folders" button to manage these resources directly.

---

## **9. Admin Views – New Tab**

[00:07:42](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h07m42s)

**Admin Views** now have their **own dedicated tab** and can be edited directly from within the component.

Buttons such as:

* **Edit component admin views**
* **Linked Admin View – Edit**

allow you to access and modify admin views instantly without returning to the main component list.

During upgrades, JCB automatically checks each view for old field formats and converts them to the new SubForm layout. If a view hasn't been opened or compiled since upgrading, you can trigger this process manually:

> Go to **Compiler → Compile Component**
> JCB will re-scan all fields and apply necessary format conversions.

---

## **10. New Feature – Translation Checker**

[00:09:19](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h09m19s)

A **Translation Checker** (Warning System) has been introduced to help manage multilingual components.

### How It Works

* Counts the total number of language strings in your component.
* Shows how many are translated for each view:

  * Admin View
  * Admin System View
  * Site View
* Displays completion progress for each language.

This tool activates only when **languages are configured** and the component has been compiled **at least once**.

---

## **11. Translation and Backup Configuration**

[00:10:48](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h10m48s)

If you encounter a message about the **Backup folder**, it likely means the **Backup** and **Temporary** directories are the same.
This is **not an error**, but a **misconfiguration**.
To fix it:

1. Go to JCB's **Options → Folder Paths**.
2. Set a distinct path for the **Backup Folder**.

---

## **12. Adjusting Translation Requirements**

[00:11:39](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h11m39s)

You can set the **percentage threshold** for translation completion before JCB flags missing translations:

* Default: **50%**
* To adjust: Go to **Options → Translations → Completion Requirement**

This gives teams control over when a translation is considered sufficiently complete.

---

## **13. Final Notes and Best Practices**

[00:12:18](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h12m18s)

* Always clear browser memory after upgrading.
* If you encounter issues, **report them on GitHub** with your browser and JCB version details.
* As of v2.6.0, **Repeatable Fields have been fully replaced by SubForms**, making JCB more compatible, efficient, and future-proof.

### Productivity Enhancements

[00:13:19](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h13m19s)
You can now:

* Access **decoupled areas** directly (e.g., Admin Views, Dashboards) via shortcut buttons.
* Edit core structures without navigating through the main Component area.

---

## **Summary**

| Area                 | Change                 | Benefit                                          |
| -------------------- | ---------------------- | ------------------------------------------------ |
| Repeatable Fields    | Replaced with SubForms | Better data structure and Joomla 4 compatibility |
| Compiler             | Updated                | Smooth handling of new architecture              |
| Dynamic GET          | Refined                | Fewer conflicts with Admin Views                 |
| Translation Checker  | New feature            | Track and manage language progress               |
| Admin Views          | Separated into own tab | Easier access and direct editing                 |
| Contributors & Files | New joint table        | Simplified and optimized management              |

---

### **Upgrade Complete**

Your Joomla Component Builder installation should now be operating with **SubForms**, optimized performance, and new translation management tools.
If all fields and relationships appear correct, your upgrade to **JCB v2.6.0** was successful.

---
