# Translation Manager in Joomla Component Builder (JCB)

> **Video Reference:** [Translation Manager in JCB Explained](https://www.youtube.com/watch?v=zzAcVkn_cWU)
> (*Timestamps included throughout this documentation link directly to video sections.*)

---

## Overview

Joomla Component Builder (JCB) now includes a **powerful translation management system** that allows developers to automatically extract, manage, and maintain multilingual strings from their components.
This enhancement was developed collaboratively by contributors and integrated into the JCB core to ensure stability and long-term maintainability.

JCB automatically handles:

* English language file generation
* Extraction of `JText` placeholders from code, templates, and XML
* Management of translations for multiple languages
* Purging of unused strings
* Import/export for collaboration with translation teams

---

## 1. Automatic English Language File Generation

[00:00:49](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=49s)

JCB is built as an English-first component builder. Whenever you define **fields, templates, or views**, JCB automatically detects and extracts **translatable text**.

### How It Works

When creating a field, certain text areas-such as labels or descriptions-can be marked as *translatable*.
If you add a description like:

```xml
<field
    name="acronym"
    type="text"
    label="Enter Acronym"
    description="Enter a short acronym"
/>
```

JCB automatically converts `"Enter a short acronym"` into a **language placeholder** (e.g., `COM_EXAMPLE_FIELD_ACRONYM_DESC`) and adds it to the `en-GB` language file.

This happens throughout the compiler-for admin views, site views, and templates-ensuring that all visible text can be translated later.

---

## 2. Placeholder Conversion with `JText`

[00:01:25](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=85s)

In templates and layouts, whenever you wrap text in a `JText` call, like:

```php
<?php echo JText::_('COM_EXAMPLE_HELLO_WORLD'); ?>
```

JCB's parser automatically captures the English string and ensures it's added to the correct `en-GB` file during compilation.

**Tip:** You do not need to manually maintain English language files - JCB compiles and updates them for you.

---

## 3. Adding Additional Languages

[00:02:43](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=163s)

Developers requested multi-language support so that JCB can compile multiple translation files.
Now you can define **multiple language tags** (e.g., `fr-FR`, `de-DE`, `es-ES`) and JCB will generate separate `.ini` files automatically.

### Steps:

1. Open the **Translation Manager** tab.
2. Click **New Language**.
3. Enter:

   * **Language Tag** (e.g., `fr-FR`)
   * **Language Name** (e.g., French)
4. JCB will use Joomla's naming conventions for prefixes (links to reference may be added later).
5. On compile, all strings are extracted into the `en-GB` file and then translated versions are created based on your database entries.

---

## 4. Internal Code Flow for Language Extraction

[00:03:50](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=230s)

The main logic resides in the `a_Get.php` class, in a function called `setLangStrings()`.

### Key Process:

* Gathers all potential language strings (`sprintf`, `JText`, etc.)
* Converts them into a standardized array of language entries
* Builds a master `langContent` array categorized by area:

  * `admin`
  * `site`
  * `system`
  * `both`

At compilation, JCB places each language key/value pair into the proper file for the correct context.

---

## 5. Adding Strings to Language Files

[00:06:04](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=364s)

When compilation reaches the final stage:

* `setLangAdmin`, `setLangSite`, and `setLangSys` functions in the **Interpreter** handle the file creation.
* Each area (admin/site/system) receives its corresponding `en-GB` `.ini` file.
* All default and dynamically generated strings are added.

This ensures that no hardcoded language strings are lost during component compilation.

---

## 6. Multi-Language String Implementation

[00:07:09](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=429s)

The multi-language system checks the database for existing English strings and determines whether translations already exist.

### Process Summary:

1. JCB compiles the component and gathers all English strings.
2. It checks the **Translation Database Table**:

   * If a string exists, translations are retrieved.
   * If new, the string is inserted as an English entry.
3. Translations are grouped by:

   * Language tag
   * Component area
4. The `getMultipleLangStrings`, `setLangPlaceholders`, and `purgeLanguageStrings` methods perform this work.

These functions reside in `a_Get.php` (open-source).

---

## 7. Reintegrating Translations During Compilation

[00:09:13](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=553s)

After fetching translations, JCB injects them back into the compiled component.
During build, each string is evaluated and merged into the `.ini` files corresponding to its target language.

You can see this in action by compiling any component (e.g., "Document Manager").
JCB will automatically:

* Collect all English strings
* Match translations from the database
* Generate translated language files per language

---

## 8. Purging Unused Strings

[00:10:05](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=605s)

When field names or descriptions change, some old strings may no longer be needed.
JCB uses a **smart purge mechanism** to manage this.

### How Purging Works

1. JCB detects unused strings during compilation.
2. It checks if other components still reference them.

   * ✅ If another component uses it → string is kept.
   * ❌ If unused anywhere:

     * If translated → moved to **Archived** state.
     * If not translated → deleted.

This preserves valuable translation work while cleaning up obsolete entries.

---

## 9. Translation Tab in Component View

[00:12:14](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=734s)

Each component in JCB now includes a **Translation tab** under its settings.

### Features:

* Displays all English strings related to that component.
* Shows whether a translation exists.
* Lists how many components use each string.
* Allows viewing but not editing English source strings.
* Enables adding or editing translations in any number of languages.

Once saved, the translations automatically propagate to all linked components.

---

## 10. Accessing Translation Data

### A. Via Component

[00:13:21](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=801s)

Each component's Translation tab lets you:

* View component-specific strings.
* Import/export translation sets for collaboration.

  * Useful for sending language packs to translators.
  * Returned translated files can be imported and automatically linked.

*(This feature is under ongoing development.)*

### B. Via Global "Language Translations"

[00:14:03](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=843s)

Alternatively, open **Components → Language Translations** to manage **all component strings together**.

* Displays thousands of entries efficiently (even 8000+ lines).
* Supports filtering by active/archived status.
* Enables bulk management of translations across components.

---

## 11. Community Translation Sharing

[00:15:15](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=915s)

A future enhancement under consideration is a **community translation exchange**, allowing users to:

* Push English strings to a shared repository.
* Pull existing translations for reuse.

Community input is encouraged - open suggestions and issues on [GitHub](https://github.com/vdm-io/Joomla-Component-Builder).

---

## Pro Tips

* Always mark UI text as translatable when defining fields or writing templates.
* Use consistent and descriptive placeholder keys (e.g., `COM_YOURCOMPONENT_FIELD_LABEL`).
* Regularly check the Translation tab for new or missing strings.
* Before compiling large components, purge old strings to maintain efficiency.
* Export translations before major updates for backup and collaboration.

---

## Summary of Key JCB Classes & Methods

| Class       | Key Functions                                                      | Purpose                                  |
| ----------- | ------------------------------------------------------------------ | ---------------------------------------- |
| `a_Get.php` | `setLangStrings`, `getMultipleLangStrings`, `purgeLanguageStrings` | Extract and manage multilingual strings  |
| Interpreter | `setLangAdmin`, `setLangSite`, `setLangSys`                        | Write strings to respective `.ini` files |
| Infusion    | Merges default and dynamic language data                           | Final compilation of translation files   |

---

## Final Thoughts

The **Translation Manager** in Joomla Component Builder automates one of the most time-consuming parts of multilingual component development.
By centralizing all translation logic, string detection, and purging within JCB, developers can focus on functionality while maintaining fully translatable extensions.

---
