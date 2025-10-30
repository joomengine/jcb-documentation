# Adding None Database Fields to an Admin View

### Overview

Joomla Component Builder (JCB) introduces a **"None DB"** field option that enables you to add fields to your **Admin View** without saving them to the database. This enhancement allows for flexible, script-driven interfaces where some fields exist only for logic, interaction, or computation, without altering database structure.

---

## 1. When to Use None Database Fields

**[00:00:00](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)**

This new JCB function allows developers to **add a field to a view without creating a corresponding database column**. This is particularly useful when:

* The field **retrieves or manipulates data** from another table.
* You want to **change page behavior dynamically** based on user selection or conditions.
* You need a field only to **combine or process multiple values** before saving to a single database field.
* The field is used for **temporary or computed data**, not for persistent storage.

For example, you might want to use two fields on the admin page to capture different inputs, combine them in your `save` function, and only store one merged value in the database.

---

## 2. How It Works in Practice

**[00:00:41](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m41s)**

When using a **None DB field**, you can handle its data through:

* **Custom PHP code** inside the Admin View's save method.
* **JavaScript logic** that manipulates the form before submission.

Example workflow:

1. Create a `None DB` field to accept temporary input.
2. Use JavaScript to gather its value during form submission.
3. In your PHP save logic, merge that input with another field's value.
4. Store the merged data into a real database field.

This allows **full flexibility** in how form data is processed and saved.

---

## 3. Implementation Example: Hidden Behavior and External Tables

**[00:01:16](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m16s)**

Another common use case is when a field's values are used to **populate or update another table**. In this setup:

* The **None DB** field collects user input.
* On save, your script writes that data into another table.
* After saving, the form can **hide these fields** based on logic or value conditions.

This method is ideal for **multi-table interactions** or **conditional display logic** in complex admin interfaces.

---

## 4. Integration with Subforms

**[00:01:34](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m34s)**

The None DB feature is also helpful for working with **subforms** or **reusable form field types**.

For example:

* You might have a subform whose data is only used for processing during save.
* Using **None DB fields** ensures these temporary fields are not written into your main table.

Before this feature, JCB automatically assumed that **every field in an Admin View** should be stored in the database. Now, developers can build **dynamic, non-persistent form structures**.

---

## 5. Setting Up the None DB Field Option

**[00:02:24](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m24s)**

In your JCB Admin View Field configuration, locate the new **"None DB"** option next to the usual *"Show in list"* and *"Default"* settings.

| Setting           | Description                                                                  |
| ----------------- | ---------------------------------------------------------------------------- |
| **Show in list**  | Determines if the field appears in the admin list view.                      |
| **Default (1/0)** | Controls the default database value (previously the only toggle).            |
| **None DB**       | Marks the field as non-database; its value will not be stored automatically. |

This **third option** allows you to define fields that are used solely in logic or display contexts.

---

## 6. Example: Conditional Validation with a None DB Field

**[00:02:49](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m49s)**

You can use **None DB** fields for internal validation logic.
For instance, the tutorial uses a field named **"Not Required"**, which is manipulated through JavaScript to adapt form validation dynamically.

* The field stores temporary values used to decide if other fields are required or hidden.
* These values never need to be stored permanently, making `None DB` ideal.

**[00:03:18](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m18s)**
When you enable **None DB**, JCB will display two notices:

1. "This field will be removed from being saved in the database."
2. "Only use the None DB option if you plan to target this field with JavaScript or PHP to move its value into another field that gets saved."

These warnings help prevent misuse.

---

## 7. What Happens Behind the Scenes

**[00:04:21](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m21s)**

When a field is marked as **None DB**, JCB:

* **Excludes** it from database migrations and SQL schema creation.
* **Removes** any form-related save logic that writes to the database.
* **Clears** incompatible configuration options (like filters, indexes, and DB default values).

After saving, the field's value **exists only in memory** (via form POST data or scripts) and disappears unless you explicitly handle it.

---

## 8. Tip: Using Automated Field Counters

**[00:05:08](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m08s)**

JCB automatically assigns a **field counter** when managing multiple fields within your script logic. Each time you add or modify a field, it updates and increments the counter for consistency in form scripts and field indexing.

---

## 9. Summary

The **None DB** field type provides developers with **greater control** over form logic and data handling within JCB.
It is best used for:

* Conditional logic fields.
* Calculated or display-only values.
* Data transfer between tables.
* Advanced UI interactions or subforms.

If your use case doesn't involve these scenarios, you can safely continue using standard database fields.

---

### Key Takeaways

* Use `None DB` when a field's data shouldn't persist in the database.
* Always handle its value manually using **JavaScript** or **custom PHP**.
* Remember: these fields are **excluded** from database schema generation and must be **explicitly processed** during save.

---

**Tutorial Reference:**
*"Adding None Database Fields to an Admin View" – JCB Official Tutorial*
*Video Duration: ~5 minutes*
*Based on latest Joomla Component Builder version and Admin View UI.*
