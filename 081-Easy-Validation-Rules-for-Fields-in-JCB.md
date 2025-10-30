# Easy Validation Rules for Fields in Joomla Component Builder (JCB)

**Tutorial Source:** [YouTube - Easy Validation Rules for Fields in JCB](https://www.youtube.com/watch?v=gYcZvL3u2To)
**Timestamp References:** Included throughout this documentation.

---

## Overview

Adding **validation rules** to fields in **Joomla Component Builder (JCB)** ensures that data entered into your forms meets specific conditions before being stored in the database.

With the newer versions of JCB, this process has become **extremely simple**, thanks to the **dedicated Validation Rules area**.
You can now easily create, customize, and assign validation rules to any field in your components — without needing to manually edit PHP code in your component files.

---

## What Are Validation Rules?

> [00:00:36](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h00m36s)

A **validation rule** checks whether a field's value meets certain criteria before saving.
It runs on the **server side** and typically returns either:

* `true` → Value is valid, form proceeds to save.
* `false` → Value is invalid, form rejects submission with an error message.

These rules are useful for ensuring values such as emails, numbers, unique fields, or existence in a database are valid before saving.

---

## 🧭 Where to Add Validation Rules in JCB

> [00:01:41](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h01m41s)

You can access validation rules in two ways:

1. From within a **Field configuration** (e.g., the "name" field).
2. Directly via the **Validation Rules menu** in JCB.

Every field can have one or more validation rules applied.

---

## Step-by-Step: Creating a Custom Validation Rule

### Step 1: Open or Create a Field

Open any field (e.g., the `name` field). You'll see existing validation rules such as:

* `exists`
* `unique`
* Joomla core validation types like `email`, `url`, etc.

> [00:02:04](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h02m04s)

These can serve as examples or templates for your own rule.

---

### Step 2: Create a New Validation Rule

> [00:02:28](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h02m28s)

1. Click **Create New Validation Rule**.
2. When prompted, click **OK** — you'll be redirected to the *New Validation Rule* form.
3. Enter a **unique rule name** (e.g., `myvalidation`).
4. Optionally, add a **description** to explain its purpose.

> **Tip:** Choose descriptive names such as `validateusername` or `checkcustomcode` to make your code easy to recognize later.

---

### Step 3: Base It on an Existing Rule (Optional)

> [00:03:25](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h03m25s)

You can choose a **Joomla core rule** as a base.
This dropdown list helps you inspect existing implementations (like `email`, `url`, etc.) for reference.

Selecting one doesn't store any data — it just loads the code into your editor as a starting point.

For example, select **email** to view Joomla's built-in email validation logic.

---

### Step 4: Write Your PHP Validation Code

> [00:04:12](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h04m12s)

Write your PHP code inside the editor.
You can extend the base logic, or build a completely custom check.

Validation rules are standard Joomla `FormRule` classes that:

* Extend `Joomla\CMS\Form\FormRule`
* Override the `test()` method

Example structure (from Joomla core):

```php
class JFormRuleMyValidation extends FormRule
{
    protected $regex = '^[A-Za-z0-9_]+$';
}
```

> **Note:** You must know some PHP to modify these rules effectively.

---

### Step 5: Save and Close

> [00:04:37](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h04m37s)

After saving, JCB automatically adds your new rule to the **Validation Rules list**, and it becomes available for assignment in any field.

---

## Assigning the Validation Rule to a Field

> [00:05:01](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h05m01s)

1. Return to your field (e.g., `name`).
2. Scroll down to **Validation** options.
3. Click the **"+"** to add a rule.
4. Select or paste the new rule name (e.g., `myvalidation`).

> [00:05:48](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h05m48s)
> Even if the field is used in multiple places, the validation applies globally wherever that field is used.

---

## Compiling and Verifying the Validation Rule

> [00:06:18](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h06m18s)

When you **compile** your component, JCB automatically:

* Creates a file in `/admin/models/rules/`
* Adds your PHP logic to that file

For example:

```
admin/models/rules/myvalidation.php
```

This file will extend Joomla's `FormRule` and contain your code.

---

### Step 1: Verify Rule File

Open the compiled file (`myvalidation.php`) and confirm your PHP code is included.

> [00:06:42](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h06m42s)

---

### Step 2: Check XML Form Reference

> [00:07:05](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h07m05s)

JCB also automatically links the rule in your XML form file, e.g.:

```
admin/models/forms/customview.xml
```

Inside the field definition:

```xml
<field name="name" type="text" label="Name" validate="myvalidation" />
```

At the top of the XML file, you'll see a reference to the rules path:

```xml
<fields rules="components/com_yourcomponent/models/rules" />
```

---

### Step 3: Config File Setup

> [00:07:56](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h07m56s)

JCB automatically adds the rule path to your **component config file**, ensuring that:

* The rule is recognized globally.
* Configuration fields can also use the same validation.

Example:

```php
'formrules' => JPATH_ADMINISTRATOR . '/components/com_yourcomponent/models/rules',
```

---

## Managing Validation Rules

> [00:08:41](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h08m41s)

You can access all created rules from:

> **Components → JCB → Validation Rules**

Here you can:

* Edit existing rules.
* Add new ones.
* See where each rule is used across fields.

> [00:09:05](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h09m05s)
> Each rule can be tweaked, and any change will automatically propagate to all fields that use it once recompiled.

---

## Key Takeaways

* JCB automates the entire validation rule process — from creation to integration.
* You can base new rules on Joomla core rules.
* All custom rules are stored in `/admin/models/rules/`.
* They are referenced automatically in XML forms and config files.
* Recompiling the component updates all related fields automatically.

---

## Example Workflow Summary

1. Open any field (e.g., `name`).
2. Click **Create New Validation Rule**.
3. Define a unique rule name and add your PHP code.
4. Save & assign the rule to the field.
5. Compile your component.
6. Verify generated file and XML references.
7. Reuse and edit validation rules easily via the JCB interface.

---

## Conclusion

> [00:09:25](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h09m25s)

JCB's **Validation Rule** system streamlines validation logic across your component.
You can now create, reuse, and maintain validation rules efficiently — with full automatic integration during compilation.

This ensures clean, reliable data validation that follows Joomla's standards while remaining easy to extend and maintain.
