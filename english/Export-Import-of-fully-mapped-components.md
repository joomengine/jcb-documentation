# Export & Import of Fully Mapped Components in Joomla Component Builder (JCB)

## 1. Overview of the Export-Import Feature

**Timestamp:** [00:00:00](https://www.youtube.com/watch?v=lkE0ZiSWufg&t=00h00m00s)

Joomla Component Builder (JCB) now includes an advanced feature that allows developers to **export a complete component**, including all related database objects and configuration data.

When exporting, JCB not only captures the main component’s metadata but also includes all **linked relationships**, ensuring a full and portable export.

### What Gets Exported

**Timestamp:** [00:00:34](https://www.youtube.com/watch?v=lkE0ZiSWufg&t=00h00m34s)

The export includes:

* **Admin Views** and their associated **Fields**
* **Field Types** linked to those fields
* **Site Views**, **Custom Admin Views**, and their related **Templates** and **Layouts**
* **Dynamic GETs** and other interconnected structures

Essentially, every relational layer within the component structure is exported, resulting in a **fully mapped component** package.

---

## 2. Exporting Components: Encrypted vs Non-Encrypted

**Timestamp:** [00:01:09](https://www.youtube.com/watch?v=lkE0ZiSWufg&t=00h01m09s)

To export a component:

1. In JCB’s main interface, click **Export Components**.
2. Select one or multiple components.
3. Choose between:

   * **Encrypted Export** – data is encrypted using an export key.
   * **Non-Encrypted Export** – data is encoded but not encrypted.

This distinction allows for **secure sharing** or **open collaboration**, depending on the use case.

---

## 3. How the Smart Export Builder Works

**Timestamp:** [00:01:40](https://www.youtube.com/watch?v=lkE0ZiSWufg&t=00h01m40s)

The export process is powered by JCB’s **Smart Export Builder**.

### Behind the Scenes:

* During the build process, the `smartExportBuilder()` method is triggered.
* It compiles all the component data from the database into one **structured array of objects**.
* This data is prepared in the function `getSmartExport()`, which extracts and organizes the exportable information.

---

## 4. Understanding the Export Key

**Timestamp:** [00:02:21](https://www.youtube.com/watch?v=lkE0ZiSWufg&t=00h02m21s)

The **Export Key** determines whether data will be **encrypted** or simply **base64-encoded**.

### How to Set an Export Key:

1. Open your component in JCB.
2. Navigate to the **Settings** tab.
3. In the bottom-right column, find the field **Export Key**.
4. Enter any string value.

> **If left empty:** The export will be **non-encrypted**.
> **If filled in:** The export will be **AES-encrypted**, protecting the component’s data layer.

Note: The encryption affects only **database values** — not attached files, folders, or images.

---

## 5. Exporting Multiple Components with Keys

**Timestamp:** [00:03:54](https://www.youtube.com/watch?v=lkE0ZiSWufg&t=00h03m54s)

If **multiple components** are exported simultaneously and **any one** of them contains an Export Key:

* The entire export package becomes **encrypted**.
* JCB loops through each selected component and stores all associated keys.
* A **key array** is built from all participating components.

---

## 6. Key Handling and Encryption Process

**Timestamp:** [00:05:12](https://www.youtube.com/watch?v=lkE0ZiSWufg&t=00h05m12s)

When keys are detected:

* They are **imploded** into a single string.
* Converted into an **MD5 hash (32 characters)**.
* Used with **AES encryption** to encrypt the exported data.

If **no keys** are found:

* JCB defaults to **Base64 encoding** instead.

This results in a secure `.zip` export file containing all relevant data, ready for import.

---

## 7. Exporting a Component – Demonstration

**Timestamp:** [00:07:13](https://www.youtube.com/watch?v=lkE0ZiSWufg&t=00h07m13s)

Example:
Exporting the `Learning Manager` component which contains an Export Key.

Steps:

1. Select `Learning Manager` → Click **Export Component**.
2. JCB generates a **unique key** for this export.
3. The exported `.zip` file (typically named `JCB_smartPackage.zip`) is stored in the **temporary folder**.

All selected components are bundled into this package.
If only one component had a key, **all components** in the export inherit the same encryption key.

---

## 8. Importing Components

**Timestamp:** [00:09:41](https://www.youtube.com/watch?v=lkE0ZiSWufg&t=00h09m41s)

To import a fully mapped component:

1. Set up a **blank Joomla site**.
2. Install **JCB** via *Install from URL* using the latest GitHub release.
3. Once JCB is installed, open **Components → Component Builder**.
4. Click **Import Components**.
5. Browse to the exported `.zip` package (e.g., `JCB_smartPackage.zip`).
6. Click **Upload and Continue**.

---

## 9. Import Options: Force Local Update & Use Key

**Timestamp:** [00:11:13](https://www.youtube.com/watch?v=lkE0ZiSWufg&t=00h11m13s)

During import, two key options appear:

### Force Local Update

If JCB detects that a similar object (e.g., field, view) already exists, it checks timestamps to determine which version is newer.

* Default behavior: skips import if the local version is newer.
* **Enable this toggle** to **force overwrite** even if timestamps match.

### Use Key

If the package is encrypted:

* Paste the **export key** from the original JCB installation.
* This key is **required** to decrypt and import the data successfully.

> Importing large datasets may take time depending on server memory and PHP limits.

---

## 10. Import Warnings and ID Remapping

**Timestamp:** [00:12:55](https://www.youtube.com/watch?v=lkE0ZiSWufg&t=00h12m55s)

During import, JCB automatically **remaps all IDs** (e.g., for views, fields, and relations).

### Common Warning:

> “Target field in Admin Views has mismatch in ID.”

This occurs if:

* A field is unpublished or deleted in the new database.
* Certain items can’t be remapped due to missing references.

**How to Fix:**

* Check affected Admin Views or Fields manually.
* Ensure that required fields or relationships exist and are published.

---

## 11. Verifying Successful Import

**Timestamp:** [00:14:55](https://www.youtube.com/watch?v=lkE0ZiSWufg&t=00h14m55s)

After successful import:

* All **custom folders, files, and images** are restored to their correct paths.
* Go to **Compiler** → Select a component.
* Check if its image loads properly.
* Compile the component and install it to confirm functionality.

If previously mapped correctly, the component will behave identically on the new installation.

---

## 12. Summary

| Action                 | Description                                        |
| ---------------------- | -------------------------------------------------- |
| **Export Component**   | Creates a `.zip` file with full mapping and assets |
| **Encrypted Export**   | Secures database data using AES and export key     |
| **Import Package**     | Restores all data, assets, and relationships       |
| **Force Local Update** | Overwrites even up-to-date items                   |
| **Use Key**            | Required to decrypt encrypted packages             |

---

## Tips & Best Practices

* Always **store your export key** securely. Without it, encrypted packages cannot be imported.
* For backups, consider exporting **non-encrypted** versions too.
* Test imports on a **local Joomla instance** before deploying to production.
* Enable **Force Local Update** only when sure that imported data should override existing records.
* Keep JCB and Joomla updated to avoid compatibility issues.

---

## Conclusion

**Timestamp:** [00:15:51](https://www.youtube.com/watch?v=lkE0ZiSWufg&t=00h15m51s)

The **Export-Import of Fully Mapped Components** feature in Joomla Component Builder greatly simplifies the process of **sharing**, **backing up**, and **migrating** complex JCB projects.
By preserving all linked structures and assets, developers can confidently move complete projects between installations with minimal effort.

---
