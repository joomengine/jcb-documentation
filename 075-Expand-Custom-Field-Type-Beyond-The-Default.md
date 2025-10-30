# Expand Custom Field Type Beyond the Default

> *Tutorial Timestamped Documentation based on JCB*
> *Video Reference: [YouTube Tutorial - Expand Custom Field Type Beyond the Default](https://www.youtube.com/watch?v=Mu9H0zgH9Lw)*

---

## 1. Introduction

**[00:00:00](https://www.youtube.com/watch?v=Mu9H0zgH9Lw&t=0s)**
This tutorial introduces an exciting new option available in **Joomla Component Builder (JCB) version 2.9.3 (Beta)**.
It allows you to expand **custom field types** directly within JCB - **without modifying the core Joomla files**.

Previously, extending Joomla's field types required manual changes to the `/libraries/joomla/form/fields` directory. With this update, you can create new field types using the JCB interface alone.

---

## 2. Understanding JCB's Field Type System

**[00:00:36 → 00:02:15]**
In JCB, the **Field Type** list includes all Joomla core field types.
Among these is the **Custom** field type - a flexible, dynamic option capable of extending:

* `List`
* `Radio`
* `Checkbox`

The **Custom** field type acts as a foundation for creating new, specialized field types.

With version 2.9.3, JCB adds the ability to **extend the Custom Field itself** - enabling deeper customization *without editing the core.*

---

## 3. Joomla Field File Structure

**[00:02:48 → 00:04:59]**
To understand how this works, look at Joomla's field definitions:

```
administrator/
└── components/
    └── libraries/
        └── joomla/
            └── form/
                └── fields/
```

Each file in this folder (like `list.php`, `radio.php`, etc.) extends a base Joomla form field (e.g. `JFormFieldList`, `JFormFieldRadio`).

You can view methods like `getLabel()` and `getInput()` within these classes.
Previously, extending one meant editing these files directly. JCB now allows you to **replicate and extend** these fields safely within the builder.

---

## 4. Field Types vs. Fields

**[00:05:33 → 00:06:07]**

> 🔹 **Field Type** - The structure or blueprint of a field (e.g., list, radio, custom).
> 🔹 **Field** - An instance used in your component that's built upon a field type.

This distinction is critical when customizing. You'll modify or extend *field types*, but the result will be seen in your actual *fields* within components.

---

## 5. Creating a New Custom Field Type

**[00:07:13 → 00:09:35]**

### Step 1 - Open the Custom Field Type

In JCB:

* Go to **Component → Field Types**
* Open the **Custom** field type.

### Step 2 - Define the "Name" with `@`

Give your field a unique name using an **`@` symbol**.
This is how JCB identifies custom field types that extend others:

```
list@mine
```

The placement of `@` can be anywhere in the name (beginning, middle, or end).

> **Note:** Without the `@`, JCB will treat it as a standard field type and not a custom extension.

### Step 3 - Keep Required Properties

You must preserve key values:

* **Type** - Must remain unique (e.g., `mylist`)
* **Extends** - Defines which Joomla field type it inherits from (`list`, `radio`, etc.)
* **Label**, **Name**, and **Description** can be customized.

Avoid using reserved type names like `list` or `radio` directly - they already exist.

---

## 6. PHP Field Array and Dynamic Code Segments

**[00:11:04 → 00:13:50]**
Each line in the **Custom Field Type PHP editor** represents a line of code.

JCB provides up to **16 PHP code segment placeholders** (`typephp`, `typephp_a`, `typephp_b`, … `typephp_x`).
These segments allow you to inject PHP into various logical parts of your field class - for example:

* `typephp` → default PHP section
* `typephp_a` → secondary logic
* `typephp_b` → alternative method or block

This flexibility makes it possible to insert code into multiple parts of your field class (e.g., `getInput`, `getOptions`, `addOptions`).

---

## 7. Example: Extending `List` Field Type

**[00:14:17 → 00:22:46]**

To demonstrate, the tutorial creates a field called **`list@mine`**, extending Joomla's List field.

### Step-by-Step:

1. Add new PHP code lines to define a method such as `getOptions()`.
2. Use the **Type PHP** identifiers (`typephp_1`, `typephp_2`, etc.) for each line.
3. Include comments and logic placeholders for readability.
4. Save the field type under a new name (e.g., **My Custom List Field**).

> **Tip:** When creating reusable field types, keep the implementation generic. Avoid hardcoding project-specific values.

---

## 8. Reusing Custom Field Types

**[00:22:10 → 00:24:52]**
Once created, your new field type can be reused across multiple components.
Ensure:

* It's **Adjustable** (checked)
* Not **Mandatory** unless necessary
  Then **Save & Close** to finalize the new custom field type.

---

## 9. Adding a Field Using the Custom Type

**[00:24:52 → 00:27:17]**

1. Go to **Fields → New Field**
2. Select your new field type (`list@mine`)
3. JCB automatically loads the associated settings and code template.
4. Adjust the database column type (e.g., `VARCHAR`) based on expected data.
5. Add to an Admin View (e.g., *Demo Admin View*) and assign its position.

Then **Compile** your component.

---

## 10. How JCB Compiles Custom Field Types

**[00:27:50 → 00:29:54]**

During compilation, JCB calls the function
`setCustomFieldTypeFile()` within the compiler.

This function:

* Collects all placeholders (like `{component}`, `{table}`, `{view}`)
* Replaces them with actual runtime values
* Merges PHP code segments into a generated file
* Outputs it as part of your compiled component

---

## 11. Testing the New Field

**[00:29:54 → 00:31:01]**
After installation:

* Go to your component in Joomla's backend.
* Create a new item in the view where you placed the custom field.
  If you see your new label and field structure, the compilation succeeded.
  If HTML or options are missing, ensure your PHP code returns a proper HTML output or options array.

---

## 12. Improving and Expanding Your Field

**[00:31:01 → 00:33:53]**
You can refine your field by:

* Adding additional PHP code lines for readability.
* Returning structured HTML or option arrays.
* Testing placeholders dynamically (`{component}`, `{table}`, `{id}`, etc.).

Example shown: adding simple **Option 1** and **Option 2** to the field output to demonstrate `getOptions()` returning dynamic values.

> Tip: Always keep `extends` set (e.g., `list`) - it determines inheritance.

---

## 13. Placeholder Replacement System

**[00:37:21 → 00:41:22]**
Placeholders (e.g., `#component#`, `#table#`, `{id}`, `{text}`) are replaced dynamically during compilation.
They are defined within the **replace array** in the compiler and correspond to the **table**, **component**, and **field** definitions in JCB.

You can view or dump this replace array to inspect available placeholders.

---

## 14. Final Notes

**[00:42:04 → 00:42:44]**

* Always add an `@` in your field name to ensure JCB recognizes it as custom.
* You can start by duplicating the **default Custom Field**, renaming it, and expanding from there.
* Never edit Joomla's core `/libraries/joomla/form/fields` directly.
* JCB will safely generate new PHP field files under your component during compilation.

---

## Summary

| Concept              | Description                                              |
| -------------------- | -------------------------------------------------------- |
| **Version Required** | JCB 2.9.3 Beta or later                                  |
| **Purpose**          | Create extended custom field types without core edits    |
| **Base Fields**      | List, Radio, Checkbox (or any Joomla field type)         |
| **Identifier**       | Must contain `@` (e.g., `list@mine`)                     |
| **Compiler Role**    | Replaces placeholders and builds field files dynamically |
| **Reusable**         | Yes - can be used across multiple components             |
| **Best Practice**    | Keep field generic and well-commented for reuse          |
