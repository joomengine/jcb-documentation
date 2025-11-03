# How to Install JCB Packages

This tutorial explains the complete process of installing a **Joomla Component Builder (JCB)** package.
It assumes that JCB is already installed on your Joomla system.

---

## 1. Accessing the JCB Package Installation View

[00:00:00](https://www.youtube.com/watch?v=PGmEoliopv8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

There are **two ways** to access the installation view for JCB packages:

1. **From the JCB Dashboard:**
   Click the **"Import JCB Packages"** icon. This opens the import view directly.

2. **From Joomla Components Menu:**
   Go to **Components → Joomla Component Builder**, and on the top right corner, click **"Import JCB Packages"**.

[00:00:35](https://www.youtube.com/watch?v=PGmEoliopv8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m35s)
This will take you to the same import area that contains several tabs-such as **VDM Packages** and **JCB Community Packages**.

If you do not want to see certain tabs, you can manage their visibility under the **Global Options** section using the **"Manage JCB Package Directories"** setting.
You can choose between:

* **Show All**
* **Show None**
* Or manually select which repositories to display.

Currently, there are two active repositories, but this area is expanding and expected to include more in the future.

---

## 2. Ensuring Package Integrity

[00:01:20](https://www.youtube.com/watch?v=PGmEoliopv8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m20s)

When you reach the **"Backup Local Data First"** page, you can select a JCB package to import from one of the following sources:

* Your **local computer**
* A **server directory**
* A **remote URL**

Be aware that **locally imported packages** do not undergo checksum validation.
You must personally ensure the integrity of the package file.

If you download a package from a **trusted external source** (like the JCB community or verified repositories), the risk is minimal.
However, if you are importing from an **unknown or third-party source**, always verify its authenticity.

The **VDM Packages** and **JCB Community Packages** sections are managed to maintain integrity and stability using checksum verification.

---

## 3. Adding Your Own Package to the Community Repository

[00:02:28](https://www.youtube.com/watch?v=PGmEoliopv8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m28s)

You can contribute your own JCB packages to the **Community Repository**.
A separate tutorial explains how to do this, ensuring that your shared package becomes accessible to all JCB users.

Earlier releases required access keys, but the unified public edition no longer hides packages behind licensing.

Select the desired package (such as the **Joomla Component Builder itself**) and click **"Get Package."**

[00:03:38](https://www.youtube.com/watch?v=PGmEoliopv8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m38s)
JCB will automatically download the package from GitHub into your development environment, validating it using a **checksum process**.

---

## 4. Validating the Checksum

[00:04:09](https://www.youtube.com/watch?v=PGmEoliopv8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m09s)

To ensure the package is authentic:

1. JCB will display the checksum used during validation.
2. Visit the URL shown (e.g., `https://raw.githubusercontent.com/...`) to compare the official checksum.
3. Verify that the checksum matches and that the certificate is signed by **DigiCert Inc** or an equivalent trusted source.

This quick manual check guarantees that your package is legitimate and unchanged from the original source.

Once verified, proceed with the import—no package key is required.

---

## 5. Choosing Merge or Clone Import Options

[00:05:19](https://www.youtube.com/watch?v=PGmEoliopv8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m19s)

When importing, you must decide between **Merge** or **Clone (New Instance)**:

* **Merge:**
  Updates your existing component if the package version is newer.
  You can also enable **"Force Local Update"**, which only works if "Merge" is selected.

* **Clone:**
  Creates a completely new instance of the component, duplicating all fields, views, and related items.

If you're importing an updated version of an existing component, **Merge** is recommended.
For experimentation or side-by-side versions, use **Clone**.

---

## 6. Viewing Detailed Import Information

[00:06:05](https://www.youtube.com/watch?v=PGmEoliopv8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m05s)

Enable the **"See All Import Information"** option (set to *Yes*) if this is your first import.
This displays detailed logs showing:

* Every field and view created
* Files that were moved
* Database items updated

It helps verify that all imported items match what was described by the package author.
This is especially important for **packages not distributed directly by VDM**.

---

## 7. Components Included in the Package

[00:07:04](https://www.youtube.com/watch?v=PGmEoliopv8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m04s)

Before proceeding, check that the **"Component Being Imported"** field matches what you intended to install.

While VDM distributes single-component packages, JCB allows importing packages containing **multiple components**-useful for backups or bulk development setups.

[00:07:32](https://www.youtube.com/watch?v=PGmEoliopv8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m32s)
You can even import a **full backup package** that includes every component you've built.
JCB successfully handles large imports (tested with 20+ components) though it may take some time to complete.

---

## 8. Import Process and ID Remapping

[00:08:04](https://www.youtube.com/watch?v=PGmEoliopv8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m04s)

The import duration depends on the size of your package.
During this process, JCB dynamically **updates all internal IDs** across:

* Fields
* Views
* Relationships

[00:08:41](https://www.youtube.com/watch?v=PGmEoliopv8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m41s)
This ensures the new package integrates correctly without conflicts.
Because JCB exports a complete "snapshot" of the original component, the importer must **remap every identifier** to maintain consistency and functionality.

---

## 9. Reviewing Imported Files and Validation

[00:09:32](https://www.youtube.com/watch?v=PGmEoliopv8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m32s)

Once completed, a detailed list of imported fields, views, and files will appear.
Scroll through this summary to confirm that everything matches expectations.

For third-party packages, take time to:

* Verify that all file paths are legitimate
* Check that no suspicious files were added

The files are grouped by type-for example:

* **Custom folders**
* **Administrator files**
* **Compiler files (for both Joomla 3 and 4)**
* **Helper scripts**

When this process finishes, your imported component will appear in your JCB environment-**fully mapped, verified, and ready for development**.

---

## 10. Verification and Final Notes

[00:11:07](https://www.youtube.com/watch?v=PGmEoliopv8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m07s)

Open any of the imported **views** to confirm that:

* All fields are correctly mapped
* Field types are recognized and linked
* All ID relationships remain valid

[00:11:37](https://www.youtube.com/watch?v=PGmEoliopv8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m37s)
At this stage, your component is **fully functional, stable, and ready for further use or customization** within JCB.

---

### Summary

Installing JCB packages involves:

1. Accessing the Import view
2. Selecting the source and verifying integrity
3. Choosing Merge or Clone
4. Reviewing import information
5. Verifying checksum and imported content

Following these steps ensures every component installed is secure, correctly mapped, and ready for immediate use in Joomla Component Builder.

---
