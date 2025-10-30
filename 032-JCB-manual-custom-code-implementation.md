# JCB MANUAL CUSTOM CODE

### Brief Explanation

[00:00:01](https://www.youtube.com/watch?v=KiAtJawZ3oo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m01s)
(_Click on these time links to see Youtube video_)

## 1. Introduction

**[00:00:01](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h00m01s)**

The *Automatic Import of Custom Code* is one of JCB's most innovative features, designed to make managing and reusing custom code across your component easy and efficient.

When enabled, this feature allows JCB to automatically detect and extract custom scripts that you've added directly into your compiled component (inside your Joomla installation), and import those scripts back into the JCB database on the next compilation.

This ensures that any manual edits you've made to your installed component's codebase are preserved and synchronized with your JCB component data.

---

## 2. How the Automatic Code Import Works

**[00:00:52](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h00m52s)**

Originally, this feature aimed to let you modify generated component code directly inside Joomla, then recompile in JCB without losing those edits.

However, it evolved into two complementary systems:

1. **Automatic code synchronization using hash references**.
2. **Manual code management through JCB placeholders**.

---

### 2.1 Why Line Numbers Aren't Used

**[00:01:43](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h01m43s)**

JCB does **not** rely on line numbers to locate where your custom code should be inserted. Since line numbers shift as code changes, this would cause insertions or overwrites in incorrect positions.

Instead, JCB uses **hash-based fingerprints**:

* A hash is calculated from several lines **above and below** your custom code block.
* This provides a stable, context-aware reference even if the file structure changes.

**[00:02:50](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h02m50s)**
The number of surrounding lines used for this fingerprint may vary but typically ranges from **6 to 10 lines** for stability.

---

## 3. Updating Code from JCB in the Editor

**[00:03:01](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h03m01s)**

Inside JCB's compiler system, the function responsible for scanning and syncing custom code is:

```php
searchfilecontent()
```

This function is part of the **Aget** compiler file. It:

* Reads your component's PHP or JavaScript source files.
* Detects placeholder tags.
* Collects the lines between those placeholders.
* Stores that code in JCB's database for reuse during recompilation.

**[00:04:27](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h04m27s)**
To prevent excessive memory usage, JCB ensures that the fingerprint array never exceeds 10 lines.

---

## 4. Insert and Replace Placeholders

**[00:05:43](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h05m43s)**

JCB uses **placeholders** in code to determine where custom code is inserted or replaced.

Two placeholder types are available:

### Insert Placeholder

```php
///***[INSERT<>$$$$]***///
Your custom code here
///***[INSERT<>$$$$]***///
```

### Replace Placeholder

```php
///***[REPLACE<>$$$$]***///
Code to replace
///***[REPLACE<>$$$$]***///
```

**[00:07:25](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h07m25s)**
After compilation:

* `INSERT<>` becomes `INSERTED$$$`
* `REPLACE<>` becomes `REPLACED$$$`

This indicates the code has been imported successfully.

---

### Important Note

**[00:08:49](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h08m49s)**
Do **not** modify the numerical ID following a placeholder. This number identifies the database entry of your stored code. Changing it will cause JCB to lose track of that custom script.

To re-trigger updates manually, **add the diamond symbol (<>)** back into your placeholder - this signals to JCB that the code block has been modified and must be reimported on the next compilation.

---

## 5. JCB Manual Custom Code Option

**[00:11:52](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h11m52s)**

Alongside hash automation, JCB provides a **Manual Mode** for custom code management.
This option allows developers to define reusable custom code snippets within JCB itself, assign placeholders, and dynamically inject values during compilation.

---

### 5.1 Creating a Manual Custom Code

**[00:12:47](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h12m47s)**

1. Open the **Custom Code** section in JCB.
2. Create a new custom script and select **"JCB Manual"** as the method.
3. Copy the provided **placeholder**, for example:

   ```
   (((customcode)))
   ```
4. Paste this placeholder into your **field**, **view**, or **layout** where the code should appear.

---

### 5.2 Example: Reusable JavaScript Code

**[00:13:52](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h13m52s)**

Let's say you have a drag-and-drop field for uploading images, containing JavaScript for UI behavior. Instead of duplicating the script across multiple fields, you can:

* Move the script to JCB's Custom Code area.
* Replace dynamic text like `image`, `teaser`, etc., with **arg placeholders**.
* Use `(((customcode)))` to call it wherever needed.

---

### 5.3 Using ARG Placeholders

**[00:15:19](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h15m19s)**

Custom code can include **arg values**, acting as variables passed during compilation.

Example placeholder usage:

```php
(((customcode|image,image,teaser)))
```

In your script, JCB replaces `arg0`, `arg1`, `arg2` with these passed values during compilation.

**Rules for ARG placeholders:**

* Arguments must be **single-word** (no commas or plus signs).
* You can include `$` if needed.
* The number of arguments must **match** the number of placeholders in the code.

---

## 6. Editor Changes vs Custom Code Updates

**[00:18:39](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h18m39s)**

* **Static custom code** (no arguments): can be edited directly in the Joomla editor, and JCB will reimport those changes.
* **Dynamic code** (with ARG placeholders): cannot yet sync external edits back into JCB automatically.

To ensure stability, JCB currently avoids reimporting changes from external edits when ARGs are used, as the values may vary across multiple usage points.

**[00:22:22](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h22m22s)**
Future updates aim to unify both systems - allowing JCB to reimport dynamic code changes from the editor safely.

---

## 7. Component and View Placeholders

**[00:23:43](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h23m43s)**

Additional placeholders for dynamic naming include:

* `(((view)))` → replaced with the current view name (lowercase).
* `[[[Component]]]` → replaced with your component's name (uppercase).

Example use case:

```js
console.log('Loaded view: (((view))) for [[[Component]]]');
```

On compilation, JCB replaces these automatically based on the context.

---

## 8. Compilation and Testing

**[00:25:11](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h25m11s)**

After setting up custom code and placeholders:

1. Compile your component.
2. Install the generated package.
3. Inspect the code area where your custom code should appear.

   * Confirm that ARGs have been replaced.
   * Check that the script appears in the intended position.

The example component used in the tutorial was **"Registry"**, demonstrating field-level script injection during compilation.

---

## 9. Summary and Best Practices

* Use **Manual Custom Code** for reusable snippets that require dynamic placeholders.
* Use **Automatic Hash Import** for direct edits inside compiled components.
* Always maintain consistent placeholder syntax (`///***[INSERT<>$$$$]***///`).
* Avoid editing database ID markers.
* To update stored code manually, **add the diamond symbol (<>)** to trigger re-import.
* Keep ARG values simple and aligned with your placeholders.

---

### Tip

If you often reuse complex JavaScript or PHP snippets across views, fields, or layouts - store them in JCB's **Custom Code Manager**. It dramatically reduces redundancy and keeps your component consistent during updates.

---

Would you like me to format this as a **publish-ready JCB documentation page** (with front matter, intro, and consistent style used in previous manuals from your project)?
That would make it ready for inclusion in your JCB Docs series.

