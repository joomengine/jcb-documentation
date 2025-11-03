# Easy Translation via Excel in Joomla Component Builder (JCB)

### Overview

**Video Reference:** [00:00:00](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

This feature introduces a **new implementation** in JCB that allows translations to be performed using an **Excel spreadsheet**, making multilingual component development simpler and faster.
You can now **export language strings**, send them to translators, and **import** the translated values back into JCB - without manually editing `.ini` language files.

---

## 1. Understanding How JCB Handles Language Strings

### 1.1. JCB Works with English Strings, Not Placeholders

[00:00:51](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m51s)

JCB does **not** rely on placeholders (like `COM_MYCOMPONENT_BACK`). Instead, it directly uses the **English string** (e.g., "Back").

* The same word (e.g., *back*) may appear in multiple contexts or views.
* JCB intelligently ensures that you **translate each unique English string only once**, regardless of how many times it appears.

**Example:**
The word *"Create New"* is used in many admin and site views, but JCB only requires you to translate it once.

---

## 2. Translating Shared Strings Across Components

[00:02:36](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m36s)

Common words like `Back`, `Cancel`, or `Close` appear across multiple components.
JCB automatically reuses their translations globally, so once translated, they apply everywhere.

---

## 3. How JCB Populates the Translation Strings

[00:03:26](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m26s)

When compiling your component:

* JCB gathers English strings from **fields**, **site views**, and **admin views**.
* These are dynamically populated in the **Language Translations** area.
* You do not need to manually click "New" - the compiler handles it.

**Pro Tip:** If you run the compiler once and then revisit "Language Translations," you'll see all strings listed, ready for translation.

---

## 4. Editing and Managing Strings

[00:05:34](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m34s)

If you need to change a string, **edit it at its source**:

* Go to the **Field**, **Admin View**, or **Site View** where the string was created.
* Update the English string (e.g., changing "Demo" to "Demoo").
* Recompile your component.
* The old string will be automatically removed, and the new one will appear in Language Translations.

---

## 5. Setting Up Languages

[00:07:23](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m23s)

You must first create the language(s) you want to translate into:

1. Go to **Languages** in JCB.
2. Click **New**.
3. Enter the **Language Name** (e.g., Afrikaans) and **Tag** (e.g., `af-ZA`).
4. Save and publish it.

If you're unsure of the correct language tag, visit [Joomla's translation page](https://community.joomla.org/translations.html) to find the proper code (e.g., `nl-NL` for Dutch).

---

## 6. Adding Translations

[00:09:31](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m31s)

To translate a string:

1. Open **Language Translations**.
2. Select the English string (e.g., "Author").
3. Choose your target **Language** (e.g., Afrikaans).
4. Enter the translated value (e.g., "Outeur").
5. Save and close.

From now on, every instance of "Author" will use the Afrikaans translation automatically.

---

## 7. New Feature - Translation via Excel

[00:10:51](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m51s)

You can now **export and import translations** through Excel for easier collaboration.

### Exporting Strings:

1. Go to **Language Translations**.
2. Select the strings you want to translate.
3. Click **Export Data**.
4. Save the generated Excel file.

The file includes:

* **IDs**
* **English strings**
* **Language tags**
* **Current translations**

You can send this file to a translator who fills in the translations per language column.

---

## 8. Importing Translated Spreadsheets

[00:12:13](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m13s)

When importing:

* Ensure the top header matches the **language tag** (e.g., `af-ZA`).
* The corresponding language must already exist in JCB.
* **Do not modify the English strings** - JCB matches by both **ID** and **string**.

### Import Steps:

1. Click **Import Data**.
2. Choose and upload the Excel file.
3. JCB will automatically map spreadsheet columns to database fields.
4. Review and confirm the import.

If you have multiple languages but only wish to import one, add the column header **"Ignore This Column"** above the ones to skip.

**Note:** If JCB cannot match an English string (due to changes), that line will be ignored.

---

## 9. Troubleshooting Import Errors

[00:14:06](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m06s)

If the import halts due to a mismatch or format issue, JCB will skip the problematic entries.
Later versions include fixes for smoother importing.

After successful import:

* Translations are automatically linked to their strings.
* Changes appear immediately in the **Language Translations** view.

---

## 10. Automatic Language Inclusion

[00:15:38](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m38s)

If **more than 50%** of a component's strings have been translated, JCB automatically adds that language to the compiled component.

You can adjust this threshold:

1. Open **JCB → Options**.
2. Under **Add Language**, modify the **translation percentage** threshold.
3. Save changes.

This ensures that only sufficiently translated languages are included in builds.

---

## 11. Summary

This new **Excel-based translation workflow** dramatically simplifies managing multilingual Joomla components:

* Export your strings easily.
* Send to translators in Excel.
* Import translations in seconds.
* Automatically synchronize across all components.

You only need to translate each unique string once - JCB takes care of everything else dynamically.

---
