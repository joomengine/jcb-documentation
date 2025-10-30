# How to Change the License Template in Joomla Component Builder (JCB)

This guide explains how to modify, create, and apply a custom license template within **Joomla Component Builder (JCB)**. It is ideal for developers who have customized existing components (such as Sermon Distributor) and want to properly manage license text across compiled files.

---

## Introduction

[00:00:00](https://www.youtube.com/watch?v=AveBf6YZzmo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

When you've modified one of JCB's demo components significantly (about 40% or more), it is appropriate to update its **license template**.
This determines what license text appears in the headers of your component's generated files.

The license template is managed inside the JCB compiler system and can be easily customized with your own `.txt` file.

---

## Step 1 - Locate the License Template Files

[00:00:34](https://www.youtube.com/watch?v=AveBf6YZzmo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m34s)

All available license templates are stored within:

```
administrator/components/com_componentbuilder/compiler/
```

This folder contains several `.txt` template files.
Each file defines a different license format that JCB can apply across your component files.

You can add your own `.txt` file here and select it as a license template within JCB.

---

## Step 2 - Viewing the Available Templates

[00:00:57](https://www.youtube.com/watch?v=AveBf6YZzmo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m57s)

Inside the `compiler` folder, you'll typically find about five `.txt` templates. Avoid using `.html` templates, as those are not suitable for license use.

Choose one `.txt` file to serve as your current template, or create a new one based on an existing file.

---

## Step 3 - Editing an Existing Template

[00:01:50](https://www.youtube.com/watch?v=AveBf6YZzmo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m50s)

You can edit a default template directly; however, this is **not recommended** because your changes will be overwritten during a JCB update.

Instead:

1. Open the default license file in the compiler folder.
2. Modify it as needed - for example, remove lines or adjust credits.
3. **Leave the following placeholders intact:**

   * `@copyright`
   * `@license`

These placeholders are dynamically replaced during compilation with the values from your component's configuration (author, version, license, etc.).

> **Tip:** Only change what's unique to your project. The overall codebase remains shared between JCB and Joomla, so your copyright applies mainly to your modifications.

---

## Step 4 - Understanding Placeholder Variables

[00:05:00](https://www.youtube.com/watch?v=AveBf6YZzmo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m00s)

JCB's compiler supports many **placeholder variables** that can be inserted into your license template.
These are found in the helper compiler's "infusion" section.

Common placeholders include:

| Placeholder                              | Description                     |
| ---------------------------------------- | ------------------------------- |
| `COMPANYNAME`                            | Your company name               |
| `CREATIONDATE`                           | Original creation date          |
| `BUILDDATE`                              | Date the component was compiled |
| `AUTHOR`, `AUTHOREMAIL`, `AUTHORWEBSITE` | Developer information           |
| `COPYRIGHT`                              | Copyright notice                |
| `LICENSE`                                | License name and text           |
| `VERSION`, `ACTUALVERSION`               | Component version numbers       |
| `COMPONENT_NAMES`                        | Component name list             |
| `SHORT_DESCRIPTION`, `DESCRIPTION`       | Component descriptions          |

> ⚙️ **Note:** Avoid using placeholders meant for scripts (e.g., custom helper scripts).
> They are not suitable for license text and will break formatting.

---

## Step 5 - Saving a New Template (Recommended Method)

[00:07:03](https://www.youtube.com/watch?v=AveBf6YZzmo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m03s)

To preserve your edits across updates:

1. Open your preferred `.txt` license file.
2. Select **"Save As…"** and rename it (for example, `default_q.txt`).
3. Save the new file in the same `compiler` directory.

Return to JCB, refresh the component configuration, and your new license template will appear as an option in the "License Template" dropdown.

When you select it and recompile your component, JCB will use your new license template across all files.

---

## Step 6 - Verify the License Update

[00:08:03](https://www.youtube.com/watch?v=AveBf6YZzmo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m03s)

After recompiling:

1. Open one of your component's generated files (e.g., from the Sermon Distributor component).
2. Scroll to the file header.
3. Confirm that the license text now reflects your new template.

JCB automatically replaces the license content during compilation, applying your new template to every file.

---

## Step 7 - Final Notes and Good Practices

[00:09:02](https://www.youtube.com/watch?v=AveBf6YZzmo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m02s)

* **Escaping and Unescaping:** Ensure proper escaping in your template text to avoid code formatting issues.
* **Keep the Copyright & License Tags:** These help users and developers understand how your component may be used.
* **Open Source Compatibility:**
  While you have freedom to customize, remember that JCB and Joomla are open-source projects. Some parts may not legally be relicensed as proprietary.

> **Best Practice:** Always maintain transparency about which parts of your component are your original work and which are derived from open-source code.

---

## Summary

Changing the license template in Joomla Component Builder allows you to:

* Customize license headers for your components.
* Add your own branding or wording.
* Keep updates safe by saving under a new filename.

With careful editing and by respecting placeholder variables, you can tailor your license template without disrupting future JCB updates.

---
