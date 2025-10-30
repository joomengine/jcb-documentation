# Library Manager – Anticipated Functionality

## Overview

[00:00:00](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

The **Library Manager** is a forthcoming feature in Joomla Component Builder (JCB), designed to dynamically handle external and internal library integrations such as Bootstrap, UIkit, and FooTable. This tutorial outlines the **anticipated structure and behavior** of the Library Manager, how developers will configure libraries, and how they will interact with component options.

The feature is currently under development. The user interface (UI) has been prototyped, and its foundational principles are being refined before compiler integration.

---

## 1. Introduction to Library Configuration

[00:00:34](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m34s)

Each library in JCB, such as **Bootstrap**, is represented as an entity that connects to multiple snippets and cannot have its base name changed once added to the **Community Snippets Repository**.

* Once a library becomes part of the community repository, its name becomes **immutable** to prevent inconsistencies.
* Even if you edit the name and click "Save," it will automatically revert to the original.

This ensures that shared libraries remain consistent across developers' environments.

---

## 2. Adding External Library Resources

[00:01:46](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m46s)

For example, the **Bootstrap 4** library uses these external URLs by default:

```text
https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-alpha.6/js/bootstrap.min.js
https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-alpha.6/css/bootstrap.min.css
```

The "Always Add" option ensures these assets are automatically included wherever the library is applied.

In the future, when **Joomla 4** is released, developers may prefer using **native Joomla libraries** through its internal API instead of remote URLs. To accommodate this, a **Custom Script** option has been introduced.

---

## 3. Two Key Functions: `prepareDocument` and `setDocument`

[00:02:30](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m30s)

There are two main functions responsible for adding libraries to views:

1. **`prepareDocument()`** – Uses the document variable directly to attach scripts and styles.
2. **`setDocument()`** – Uses a global document variable, depending on class inheritance.

When using the **Custom Script** option, you can target these methods to add the required assets dynamically.

---

## 4. Conditional Library Loading

[00:03:39](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m39s)

The **Conditional Option** introduces a dynamic approach to file inclusion:

* You can set rules such as **Include** or **Exclude** based on field conditions.
* The conditional logic mirrors JCB's **field conditional system**, using **Isolate** or **Chain** logic.
* Conditions rely on **config fields**, which are pre-created in your component.

For example, linking a radio field named `Bootstrap v4` allows toggling whether Bootstrap assets should be included.

---

## 5. Linking Option Fields

[00:05:40](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m40s)

When selecting an **Option Field**, such as a Yes/No toggle:

* If the field "Add Bootstrap" is set to **Yes**, the linked Bootstrap CSS and JS files will load.
* This offers a **conditional method** for including assets.

However, as of now, JCB does not automatically create these conditional fields in all systems. The developer may choose to manually add or script their generation.

---

## 6. Creating and Linking Local Files

[00:07:03](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m03s)

To include custom or local files:

1. Click **Edit** in the library.
2. Select **Add New Files**.
3. Use the green plus icon to attach a file or URL.
4. Example local path:

   ```
   /media/bootstrap4/js/bootstrap.min.js
   ```

These files can be conditionally added using custom fields. For example, create a new field `Add More` (radio), and when set to **Yes**, the corresponding file (e.g., `bootstrap.min.js`) will load.

---

## 7. Dynamic Integration and Custom Scripts

[00:09:33](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m33s)

Previously, such functionality was **hardcoded in the compiler**-for instance, automatically detecting UIkit v2 usage. The new system aims to make this behavior **dynamic and developer-driven**.

You can still leverage global library buttons such as:

* **Library Files, Folders & URLs**
* **Library Config**

These can be referenced inside your scripts using global variables like:

```php
$this->fooTableStyle
```

This allows conditional or custom inclusion through both `prepareDocument` and `setDocument`.

---

## 8. Global vs. Page-Level Conditions

[00:10:50](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m50s)

A planned enhancement is **dual-level conditional logic**:

* **Global Value** – Applies library inclusion rules across the entire component.
* **Page Value** – Allows per-view overrides.

This is especially useful when a specific view already loads the same library, and you wish to exclude it to prevent duplication.

For instance, a menu item might require Bootstrap globally, but an individual view could override it if another component already includes Bootstrap.

---

## 9. Always Add vs. Conditional Add

[00:12:15](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m15s)

* **Always Add** ensures the file is included on all pages using the library.
* **Conditional Add** only includes specified files when defined conditions are met.
* Files without explicit conditions are always added automatically.

Example default Bootstrap URLs:

```text
http://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-alpha.6/js/bootstrap.min.js
http://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-alpha.6/css/bootstrap.min.css
```

---

## 10. Community Collaboration and Ongoing Development

[00:13:09](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m09s)

Development discussions for this feature are ongoing in **GitHub Issue #92: UIkit v3 or Bootstrap Option**.

Developers are encouraged to:

* Record short tutorials explaining ideas or improvements.
* Contribute to the GitHub discussion threads.

---

## 11. Implementation Outlook

[00:13:57](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m57s)

When released, this feature will include:

* Predefined configurations for **Bootstrap**, **UIkit**, and **FooTable**.
* Support for dynamic library loading without compiler modifications.
* Clear separation between global and per-view inclusion behavior.

Once implemented, users will be able to adapt and extend these libraries locally without disrupting community consistency.

---

## 12. Final Notes

[00:16:04](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m04s)

This tutorial introduces the anticipated direction of the new Library Manager. The aim is to make library handling in JCB **dynamic, modular, and extensible**, empowering developers to integrate frameworks efficiently while maintaining structural integrity.

---

### Key Takeaways

* Libraries will have **immutable names** for community stability.
* **Conditional logic** allows smart inclusion/exclusion of files.
* **Global and per-view control** ensures flexibility in resource management.
* **Custom scripts** provide ultimate control for advanced users.
* **Community feedback** continues to shape the design and implementation.

---
