# Automatic Import of Custom Code During Compilation In JCB

[00:00:00](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Click on these time links to see Youtube video_)

---

## 1. Introduction to Custom Code

**[00:00:00](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h00m00s)**

The **Custom Code** feature in Joomla Component Builder (JCB) is a powerful addition that allows developers to seamlessly integrate their manually written code into the component workflow. This feature works alongside the **Dynamic Get** system and ensures that any custom modifications added to compiled components are automatically tracked, stored, and re-applied on subsequent compilations.

You will rarely need to edit these custom code entries directly in JCB's UI. Instead, most editing happens inside your preferred **code editor** (e.g., VS Code, PHPStorm, Sublime Text).

---

## 2. Purpose of the Custom Code Feature

**[00:00:39](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h00m39s)**

This feature is designed for developers who prefer to code directly in their editor. The typical workflow looks like this:

1. **Create** a component using JCB.
2. **Compile and install** it on the same Joomla site.
3. **Modify or add code** manually in the compiled files.
4. On the next **compilation**, JCB automatically:

   * Extracts that new or modified code.
   * Stores it in the **Custom Code** section.
   * Re-inserts it into the correct location within the component.

This system prevents you from losing your changes when recompiling.

> **Note:** The feature is still in **beta**, and users are encouraged to provide feedback for refinement.
> **[00:01:45](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h01m45s)**

---

## 3. Editing Code in Your Editor

**[00:02:28](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h02m28s)**

To test the feature:

1. Open your Joomla site's root directory in a code editor.
2. Navigate to `administrator/components/com_demo` (assuming you're using the **Demo Component**).
3. Open a main PHP file such as `index.php`.
4. Add some simple custom scripting or comments.

This modification will later be detected by JCB during compilation.

---

## 4. Custom Code Conventions

**[00:03:04](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h03m04s)**

Custom code uses specific placeholder tags that JCB can recognize and manage. These placeholders mark where your code begins and ends.

### a. Insertion Tags

To **insert** new code:

```php
///***[INSERT<>$$$$]***///
[Your custom PHP code here]
///***[INSERT<>$$$$]***///
```

### b. Replacement Tags

To **replace** existing code:

```php
///***[REPLACE<>$$$$]***///
[Your replacement PHP code here]
///***[REPLACE<>$$$$]***///
```

### c. After Compilation

Once compiled, JCB updates these placeholders:

* It changes `[INSERT<>$$$$]` to `[INSERTED<>$$$$23]`, where `23` is the **custom code ID** in JCB.
* **Do not modify this number.** It's critical for future compilations.

> **Tip:**
> If you later modify your code, re-add the diamond brackets `<>` to indicate that JCB should update the stored version.

---

## 5. Limitations of Custom Code

**[00:05:30](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h05m30s)**

There are a few important limitations when using custom code tags:

* **Spacing:** Custom code blocks must be at least **6-8 lines apart**.
* **Fingerprinting:** JCB creates a **fingerprint** (context snapshot) of a few lines before and after your insertion. If that context changes too much, JCB won't recognize where to re-insert the code.
* If the fingerprint changes, JCB will:

  * Skip reinsertion and display a **warning** during compilation.
  * Insert the code as **escaped**, preventing it from breaking your component.

> This fingerprinting system prevents accidental overwrites and ensures stable automated merging.

---

## 6. Demonstration - Replace Example

**[00:08:00](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h08m00s)**

1. Open the **Demo Component's** main file.
2. Add your replacement tags:

   ```php
   ///***[REPLACE<>$$$$]***///
   echo 'hi, it worked!';
   ///***[REPLACE<>$$$$]***///
   ```
3. Save your file and re-compile the component in JCB.

After compilation, check the **Custom Code** tab in JCB:

* You'll see your entry listed with its **path** and **fingerprint hashes**.
* The interface shows both **start** and **end** fingerprints for replacements.

---

## 7. Verifying Replacement in the Editor

**[00:10:03](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h10m03s)**

Once you reinstall the compiled component:

* The code will appear correctly inserted and tagged as **replaced**.
* An ID number (e.g., `23`) will be added to track it in the system.
* If you later edit this code, remember to add back the `<>` symbols before recompiling.

---

## 8. Demonstration - Insert Example

**[00:11:32](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h11m32s)**

Follow these steps to test **insertions**:

1. In your editor, move at least **8 lines** below any existing tag.
2. Add an insertion block:

   ```php
   ///***[INSERT<>$$$$]***///
   echo 'New insert block added!';
   ///***[INSERT<>$$$$]***///
   ```
3. Save and compile your component again.

Before reinstalling, open the **Custom Code** tab in JCB:

* You should see the new insertion listed.
* Only the **start hash** is required for insertions (no ending hash).

After installation, your code will appear with `INSERTED` status and a unique ID.

---

## 9. Updating Custom Code

**[00:14:34](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h14m34s)**

To update inserted or replaced code:

1. Edit your code in the editor.
2. Add the diamond symbols `<>` back to the tag.
3. Save the file.
4. Re-compile and reinstall your component.

JCB will automatically detect the change and update its stored version in the database.

---

## 10. Handling Fingerprint Warnings

**[00:15:18](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h15m18s)**

If the code surrounding your insertion or replacement changes:

* JCB may not find the original fingerprint.
* The system will **insert the code escaped** (disabled), so it doesn't break your component.
* This ensures your manually added code is never lost or misplaced.

For replacements, this process is more complex because the replaced code might not be removed automatically. Always review warnings in the compiler output.

---

## 11. Distribution Settings

**[00:16:21](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h16m21s)**

When your component is ready for **distribution**:

1. In JCB, switch the component to **"Production mode."**
2. On the next compilation, JCB will:

   * Remove all placeholder tags.
   * Exclude the custom code management markers.

This ensures your distributed component is clean and ready for deployment.

---

## 12. Summary

| Feature                    | Description                                                         |
| -------------------------- | ------------------------------------------------------------------- |
| **Automatic Extraction**   | JCB reads and stores your custom scripts on compilation.            |
| **Automatic Reinsertion**  | When recompiled, your scripts are added back in the correct places. |
| **Insert & Replace Tags**  | Use `INSERT` for new code, `REPLACE` for existing code.             |
| **Fingerprint Protection** | Keeps your manual edits safe by validating code context.            |
| **Production Switch**      | Removes tags for public release.                                    |

---

## 13. Key Takeaways

* Always space custom code blocks at least 8 lines apart.
* Never change the auto-generated ID after compilation.
* Use the diamond brackets `<>` when you want JCB to detect an update.
* Test your custom code with a **Demo Component** before production use.
* Monitor the **Custom Code** tab for all extracted and managed scripts.

---
