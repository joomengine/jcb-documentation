# VDM Package Import Option — Joomla Component Builder Documentation

*(Based on video tutorial: “VDM Package Import Option”)*

---

## Overview

[00:00:00]
The **VDM Package Import Option** in Joomla Component Builder (JCB) allows developers to easily import prebuilt component packages from the official JCB GitHub repositories or other trusted community sources.

This feature is especially beneficial for users who want quick access to maintained **JCB packages**, such as:

* The **Advanced Demo Component**
* The **Sermon Distributor Component**

It simplifies access to these ready-made components and automates importing them directly into your JCB installation.

---

## 1. Accessing the VDM Packages Import Tab

[00:00:20]
A new **tab named "VDM Packages"** has been added under the **Import Components** section in JCB.

### Steps

1. Go to **Components → Joomla Component Builder → Import Components**.
2. Select the **VDM Packages** tab.

JCB will now connect to GitHub to retrieve a list of all available packages.
This process may take a few moments as it fetches live data.

[00:01:01]
If GitHub repositories are updated with new packages, they will appear automatically within this list.

**Currently available packages** include:

* Hello World
* Demo Version

> **Tip:** More packages will be added over time. Ensure you have a stable internet connection to allow JCB to fetch the latest packages from GitHub.

---

## 2. Resetting Sermon Distributor or Similar Packages

[00:01:24]
If you already have the **Sermon Distributor** component installed and wish to reset or update it:

* You may **reinstall** or **import** the package again.
* This will overwrite the existing component structure, **resetting every field and Field Type** to the original values.

[00:01:52]

> **Warning:** Importing a package over an existing one will **reset all data**, including custom fields, configurations, and field types.

[00:02:07]
To protect your previous work, ensure **Joomla’s Version History** is enabled for the JCB component.
This allows you to roll back changes if necessary.

---

## 3. Installing Packages via "Get Package"

[00:02:22]
Once the package list loads, follow these steps:

1. Select the desired package (e.g., Sermon Distributor).
2. Click **Get Package**.

This initiates the download from GitHub. The process might take a few minutes depending on package size and connection speed.

[00:02:55]
When prompted:

* Confirm the package details.
* Click **Continue** to proceed.

JCB will then install the package (for example, “Sermon Distributor 2.0.2”) and display installation details.

> **Tip:** Always review the displayed information to confirm that you are installing the correct version from a trusted source.

---

## 4. The “Quiet” Switch

[00:03:28]
The **Quiet** switch allows you to toggle between detailed and minimal installation feedback.

* **Quiet = Yes** → Minimal output; hides ID mapping details.
* **Quiet = No** → Verbose output; displays all ID references and actions.

[00:03:50]
Note that earlier versions of JCB contained a typo (“Quite”)—this has been fixed in **JCB version 2.7.1**.

[00:04:19]

> **Tip:** Enable “Quiet = No” only when debugging import behavior or verifying data mapping changes.

---

## 5. Force Local Update — Overwriting Existing Data

[00:04:33]
When importing a component, you may encounter items that already exist locally.
JCB uses timestamps to decide whether to replace or keep local data.

### Force Local Update Options

* **No (Default):** Keeps newer local data and skips importing older records.
* **Yes:** Forces overwrite of all existing data, regardless of version or timestamp.

[00:05:15]
After enabling **Force Local Update**, click **Continue**.
You’ll see a detailed printout showing which IDs were found, updated, or newly imported.

[00:05:44]
If you disabled Quiet mode, you’ll see a complete log of the import actions.

---

## 6. Post-Import Actions: Compiling and Installing

After successful import:

1. If the package uses a licensing file (e.g., `vdm.txt`), verify or replace it if necessary.
2. Save and close the imported component.

[00:06:28]

### Compile the Component

* Go to **Components → Joomla Component Builder → Components**.
* Select **Sermon Distributor** (or your imported package).
* Click **Compile**.

Once compiled, JCB generates a **Joomla installable package (.zip)** that includes all external scripts defined in the package.

[00:06:54]
Some packages, such as the Sermon Distributor, also include **external scripts** (e.g., MIME type checkers).
These are automatically fetched from GitHub during compilation.

> **Security Note:** Always verify that external code strings (`EXTERNALCODE`) are safe before compiling, to prevent importing malicious code.

[00:07:17]
Finally, install the compiled package in Joomla via the **Extension Manager**.
Your component (e.g., Sermon Distributor) will appear in the Components menu, fully functional and ready for use.

---

## 7. Suggested Feature — Community Package Sharing

[00:07:39]
A proposed future enhancement is a **Community tab** in the Import Components area.

This would allow:

* Community members to share **JCB packages** openly.
* Maintainers to curate highlighted bundles for specific use cases.

[00:08:04]
Each package determines its own **metadata and documentation links**.
For example, clicking on a package like `googlePlusProfileFeed` could redirect users to its associated project page.

[00:09:06]
There are ongoing discussions about whether JCB should include contribution mechanisms to support this ecosystem.

[00:09:33]
Another idea is integrating the Import Components section directly into the **JCB Dashboard**, improving accessibility.

[00:09:54]
Until then, developers can manually import any GitHub package using its repository link and package key.

---

## 8. Summary

The **VDM Package Import Option** streamlines how developers access and install JCB components.
Key takeaways:

* Quickly import **ready-made JCB packages** directly from GitHub.
* Use **Quiet** and **Force Local Update** options to control import verbosity and overwrite behavior.
* **Compile and install** your imported component easily through JCB.
* Expect future enhancements, including community-driven package sharing.

This feature greatly simplifies development and sharing within the Joomla Component Builder ecosystem.

---
