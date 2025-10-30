# Joomla Component Builder – Dynamic File and Folder Inclusion

### Tutorial Reference

**Video:** "Dynamic File and Folder Inclusion Concept"
**Transcript Source:** `055-Dynamic-File-and-Folder-Inclusion-concept.md`
**Purpose:** To explain how to dynamically include external files, folders, and code into your Joomla Component Builder (JCB) components.
**Video Timestamp Reference:** Each section includes timestamps for cross-reference with the tutorial.

---

## 1. Introduction to Dynamic Inclusion

**[00:00:00 → 00:01:17]**

Joomla Component Builder introduces a **dynamic file and folder inclusion system** that allows developers to include external files or folders—either local or remote—directly into their component package.

This feature enhances automation and flexibility when developing complex Joomla components that rely on shared or external resources.

### Key Concept

You can now:

* Include **external files or folders** (even from outside the Joomla root directory).
* Fetch and embed **remote files** (such as from GitHub or another website) directly into your component.
* Manage code snippets dynamically with **EXTERNALCODE**.

---

## 2. Accessing the Advanced Tab for Dynamic Files

**[00:02:03 → 00:02:35]**

Navigate to the **"Files & Folders"** area within JCB.
A new **"Advanced" tab** has been added to complement the existing **Basic tab**.

### What It Does

* Allows JCB to **grab files from anywhere in your system** and add them to your component package.
* Supports **files outside the Joomla root directory**, provided PHP has the necessary read permissions.

> **Tip:** Normally, you'll only need files inside your Joomla component directory.
> Use external inclusion only when your workflow specifically requires external dependencies.

---

## 3. Adding Files and Folders

**[00:02:53 → 00:04:21]**

You can configure JCB to package non-generated custom files or folders along with your component. This means you can keep such files where they belong during development and have JCB include them automatically during compilation.

### Path Settings

* **Use constants** in file paths (e.g., `_VDM_PATH_`).
* Do **not** wrap constants in quotes.
* JCB's compiler automatically interprets these constants correctly.

Example (inside JCB):

```
VDM_PATH.'/libraries/vdm_io'
```

Becomes dynamically resolved by the compiler without additional syntax.

---

## 4. Defining the Target Path and ZIP Relation

**[00:04:29 → 00:05:39]**

When setting up file or folder inclusion:

1. **Define the target path** within your component's ZIP structure.
   Example: `libraries/vdm_io`
2. This allows JCB to include non-standard folders (like libraries) into the component package.
3. On installation, these folders are automatically copied into their proper places.

> **Example Use Case:**
> Include Composer-managed library files directly into your JCB component without separate packaging.

---

## 5. Automatic Installation Scripts for Non-Standard Folders

**[00:05:53 → 00:07:59]**

If JCB detects that your target path is **outside** the usual Admin, Media, or Site directories, it adds a special installer script function (`setDynamicF0ld3rs`) to handle those folders correctly.

### Script Behavior

* Moves specified folders to the right destination during installation or updates.
* Ignores Admin, Media, and Site folders (these are handled natively by Joomla).
* Handles all other locations dynamically.

> **Warning:**
> This feature is powerful but potentially dangerous.
> You could unintentionally overwrite files anywhere in the Joomla installation.
> **Use with caution** and only when you control the deployment environment.

---

## 6. Security Reminder

**[00:09:13]**

Be mindful when importing JCB packages created by others.

> **Note:**
> Dynamic inclusion can theoretically move files anywhere on your system.
> Only import and install JCB packages from **trusted developers**.

---

## 7. Using `EXTERNALCODE` Snippets

**[00:09:49 → 00:12:38]**

The `EXTERNALCODE` keyword allows JCB to dynamically fetch and embed **external code snippets** into your component at compile time.

### How It Works

* Can reference **local file paths** or **remote URLs** (e.g., GitHub raw file links).
* Useful for including code shared in Git repositories or team snippets.
* JCB automatically creates and tracks a **hash signature** of the code for change detection.

#### Example:

```
EXTERNALCODE:https://gist.githubusercontent.com/username/raw/fancydate.txt
```

This snippet fetches the raw file contents and embeds it into your component helper or class area.

> **Note:**
> Currently, EXTERNALCODE does **not support constants** in paths—use absolute paths or full URLs.

---

## 8. Compilation and Hash Validation

**[00:13:19 → 00:15:11]**

When compiling a component with EXTERNALCODE:

* JCB fetches the external resource.
* It displays a **message confirming** that external code has been added.
* A **hash** is generated to monitor for changes in future compilations.

If the snippet changes:

* JCB shows a **warning** under "Warnings" after recompilation.
* You are prompted to verify that the code change is legitimate.

---

## 9. Post-Compilation Validation

**[00:16:16 → 00:18:49]**

After compilation:

1. Check that the included external code appears correctly in your component files (e.g., within the `helpers` directory).
2. If a change is detected in a later compilation, review the updated code for security and correctness.
3. Confirm that any modifications are expected (e.g., from your GitHub source).

---

## 10. Handling External Code Updates Safely

**[00:17:20 → 00:19:16]**

If an external snippet changes:

* JCB will automatically notify you during compilation.
* Check the affected file to confirm that only expected updates were made.
* JCB also ensures any injected malicious code is escaped as a string, preventing direct execution.

> **Best Practice:**
> Always verify the **hash change message** after every compilation involving external snippets.

---

## 11. Final Thoughts

**[00:20:15 → 00:20:54]**

The **Dynamic File and Folder Inclusion** and **EXTERNALCODE** features are advanced tools designed for professional Joomla developers who want:

* Modular, reusable codebases.
* Automated inclusion of shared libraries or scripts.
* A robust way to collaborate via GitHub while maintaining component integrity.

However, with great flexibility comes great responsibility:

* Always validate source integrity.
* Only share JCB packages with trusted collaborators.
* Keep inclusion paths and permissions tightly controlled.

---

## Summary of Key Features

| Feature                      | Purpose                                                       | Risk Level | Recommended Use                                  |
| ---------------------------- | ------------------------------------------------------------- | ---------- | ------------------------------------------------ |
| **Dynamic File Inclusion**   | Add external or internal files into your component.           | Medium     | When including static libraries or helper files. |
| **Dynamic Folder Inclusion** | Move external folders into Joomla directories during install. | High       | Use only if fully aware of file paths.           |
| **EXTERNALCODE**             | Fetch external code snippets from GitHub or URLs.             | Medium     | Ideal for version-controlled helper functions.   |
| **Compiler Hash Checking**   | Detects unauthorized or unexpected changes.                   | Low        | Always review warning messages.                  |

---

## Helpful Tips

* Use **JCB constants** for dynamic paths to ensure portability across environments.
* Keep external inclusions **version-controlled** via GitHub.
* Periodically **recompile and verify hashes** to maintain component integrity.
* Never use EXTERNALCODE from unverified or public sources.
