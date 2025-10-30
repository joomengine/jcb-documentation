# How to Ensure That a Field Is Not Escaped When Added to List Views

[Watch Tutorial](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

---

## Overview

Sometimes, when working with **List Views** in **Joomla Component Builder (JCB)**, you may want to add **custom styling** or **HTML formatting** directly into a field output.
However, by default, JCB **escapes all field values** for security reasons - meaning HTML is rendered as plain text.

This guide demonstrates how to safely disable field escaping for specific fields, allowing you to include HTML output such as colored labels or stylized dates in your list views.

---

## 1. Understanding Field Escaping

**Timestamp:** [00:00:06](https://www.youtube.com/watch?v=bfl0l3AoLKU&t=00h00m06s)

By default, Joomla automatically **escapes** field values in list views to prevent malicious code injection (XSS).
When you want to display **HTML-based styling** (e.g., `<span class="danger">Overdue</span>`), this escaping prevents the HTML from rendering properly.

If you notice that your styled content appears as text rather than HTML, escaping is likely enabled on that field.

---

## 2. Example Scenario: Adding Extra Styling to Fields

**Timestamp:** [00:00:31](https://www.youtube.com/watch?v=bfl0l3AoLKU&t=00h00m31s)

In this tutorial, the **Job Order Admin View** is used as an example.
Within the `getItems()` method (before translation fix and decryption), a PHP snippet is added to apply color-based styling depending on time-sensitive values.

However, this is **not the ideal location** to modify the data for HTML rendering because escaping will still occur later in the compilation.

---

## 3. Working with Configuration Values

**Timestamp:** [00:00:58](https://www.youtube.com/watch?v=bfl0l3AoLKU&t=00h00m58s)

The setup involves **configuration fields** that define "warning" and "danger" time thresholds (for example, *3 weeks* and *1 week*).
These configuration values are used in logic that determines when a field's display should change visually - for instance, changing a job date to red when overdue.

This logic typically involves:

* Fetching the current date.
* Comparing it with configured time thresholds.
* Adding corresponding CSS class names like `"warning"` or `"danger"`.

---

## 4. Looping Through Data and Applying Styling

**Timestamp:** [00:01:44](https://www.youtube.com/watch?v=bfl0l3AoLKU&t=00h01m44s)

Next, iterate through the dataset and determine which records should be visually marked.
For example, you might:

* Add a red class for overdue jobs.
* Add a yellow class for upcoming deadlines.

The code uses a **helper class method** called `fancyDate()` to format SQL dates (e.g., `2025-04-02`) into readable formats like "2 April 2025".

However, once the component is compiled and loaded, the HTML tags applied by this method are **escaped** and displayed as plain text (e.g., `&lt;span class="danger"&gt;Overdue&lt;/span&gt;`).

This happens because the **Joomla escape method** (`htmlspecialchars()`) runs on all list field outputs by default.

---

## 5. Preventing HTML Escaping

**Timestamp:** [00:03:27](https://www.youtube.com/watch?v=bfl0l3AoLKU&t=00h03m27s)

To allow HTML output in your list view:

1. Open your **component's backend view** in JCB.

   * Navigate to **Admin Views → Fields**.
   * Locate the relevant field (e.g., `job_status`).

2. Edit the field and scroll to the **advanced configuration area**.

3. In the **code section**, add the attribute:

   ```php
   escape="false"
   ```

4. Save your changes.

**Timestamp:** [00:04:09](https://www.youtube.com/watch?v=bfl0l3AoLKU&t=00h04m09s)

During compilation, JCB will now instruct Joomla not to escape that field's output, allowing your HTML to render correctly.

---

## 6. Recompiling the Component

**Timestamp:** [00:04:37](https://www.youtube.com/watch?v=bfl0l3AoLKU&t=00h04m37s)

After adding the `escape="false"` attribute:

1. Recompile your component in JCB.
2. Install or update the generated ZIP in your Joomla site.
3. Refresh your list view to see the formatted HTML display.

You should now see proper visual output - for example, dates highlighted in red or warning labels showing with their intended styles.

---

## 7. Key Takeaways

**Timestamp:** [00:05:15](https://www.youtube.com/watch?v=bfl0l3AoLKU&t=00h05m15s)

* Joomla escapes field outputs by default to enhance security.
* To display HTML safely, set `escape="false"` on that specific field in JCB.
* This setting tells Joomla to output the field value *as-is*, without running it through the escape filter.
* Use this feature selectively, ensuring that only trusted, system-generated content is displayed unescaped.

---

## Tips for Safe Use

* **Avoid unescaped user input.** Only disable escaping for fields whose content is system-controlled (e.g., generated programmatically or from trusted sources).
* **Use helper classes** like `fancyDate()` to format and sanitize data before output.
* **Test thoroughly** to confirm that your HTML renders correctly and doesn't introduce layout issues.

---

## Conclusion

You have now learned how to make a Joomla Component Builder field render HTML output directly in the list view by disabling escaping.
This technique is useful for visual indicators such as colored statuses, badges, or other styled data representations within your Joomla admin interface.

---

**Video Reference:**
[How to Ensure That a Field Is Not Escaped When Added to List Views](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

---
