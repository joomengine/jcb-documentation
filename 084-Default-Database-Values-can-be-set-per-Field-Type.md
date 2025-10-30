# Default Database Values Can Be Set Per Field Type

This guide explains how to use the new Joomla Component Builder (JCB) feature that allows you to define **default database values** for specific field types. This improvement streamlines component development by automatically applying commonly used database settings whenever you create a new field of the same type.

---

## Overview

When creating fields in JCB, developers often reuse similar database configurations for the same field types (for example, `VARCHAR(255)` for text fields or `INT(11)` for numbers). Previously, these values had to be set manually for every new field, which could be repetitive and time-consuming.

To solve this, JCB now allows you to define **default database values per field type**. Once set, these defaults automatically populate whenever you select that field type during field creation.

> **Note:** This feature is **not active by default**. You must manually set the default values for each field type you want to standardize.

---

## Step-by-Step Guide

### 1. Creating a Field

[00:00:16](https://www.youtube.com/watch?v=wGFqV63KzeA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m16s)

1. In your Joomla Component Builder interface, go to **Fields** and click **New**.
2. Choose the desired **Field Type** - for example, `Text` or `List`.
3. Configure the **properties** as usual:

   * Set the label
   * Define options (if applicable)
   * Remove any unused parameters

Normally, you would now define the **Database Values** manually every time. With this new improvement, that step can now be automated.

---

### 2. Understanding the Default Database Values

[00:00:43](https://www.youtube.com/watch?v=wGFqV63KzeA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m43s)

Even though you might be using the same database structure for a given field type, JCB used to require re-entering these settings for each new field. The new feature lets you define a **one-time default** that will automatically populate for that field type.

This helps standardize your database schema across multiple fields and components, while reducing repetitive setup work.

---

### 3. Enabling and Setting Default Database Values

[00:01:20](https://www.youtube.com/watch?v=wGFqV63KzeA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m20s)

To configure default values:

1. Open the **Field Types** area in JCB.
2. Select the field type you want to modify - for example, `Number`.
3. In the **Database Values** section, enter your preferred configuration.

**Example:**
For a "Number" field:

```text
Type: INT
Length: 11
Null: No
Default: 0
```

Click **Save** to store your configuration.

Now, whenever you create a new field of type "Number," these database values will automatically appear.

---

### 4. Testing the Defaults

[00:01:49](https://www.youtube.com/watch?v=wGFqV63KzeA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m49s)

To verify that your default settings are working:

1. Create a **new field**.
2. Select the field type you configured (e.g., `Number`).
3. Observe that the database values are automatically filled with your defaults.

You can still modify them for special cases, but the base configuration is already in place - saving time and ensuring consistency.

---

### 5. Applying Defaults to Other Field Types

[00:02:28](https://www.youtube.com/watch?v=wGFqV63KzeA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m28s)

You can repeat the same setup for other field types. For example:

| Field Type    | Typical Database Type | Example Default |
| ------------- | --------------------- | --------------- |
| **Telephone** | `VARCHAR`             | `VARCHAR(64)`   |
| **Text**      | `VARCHAR`             | `VARCHAR(255)`  |
| **Integer**   | `INT`                 | `INT(11)`       |
| **Date**      | `DATETIME`            | `NULL`          |

By defining these standards once, your field creation process becomes much more efficient and consistent.

---

### 6. Example Workflow

[00:02:54](https://www.youtube.com/watch?v=wGFqV63KzeA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m54s)

Let's take the `Telephone` and `Text` examples:

* For **Telephone**, set the database type to `VARCHAR(64)`.
* For **Text**, set the database type to `VARCHAR(255)`.

Once saved, these configurations automatically apply each time you create new fields of these types.

---

## Tips and Best Practices

* **Keep it consistent:** Define sensible, standard defaults that reflect how you typically use each field type.
* **Use naming conventions:** Match database types to Joomla field expectations (e.g., `INT` for numeric values, `VARCHAR` for short text).
* **Review before saving:** Default values apply globally per field type - double-check your setup before saving.
* **Override when needed:** You can still customize the database values in individual fields when exceptions arise.

---

## Conclusion

[00:03:13](https://www.youtube.com/watch?v=wGFqV63KzeA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m13s)

This feature makes it easy to maintain a **consistent and efficient workflow** when designing components in Joomla Component Builder. Setting **default database values per field type** eliminates repetitive setup work and ensures your database structures stay uniform across all components.

By taking a few minutes to configure your most-used field types, you can significantly speed up component development in JCB.
