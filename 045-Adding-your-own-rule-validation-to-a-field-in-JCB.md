# Adding Your Own Rule Validation to a Field in Joomla Component Builder (JCB)

This guide explains how to **create and apply a custom validation rule** to a field within a Joomla Component Builder (JCB) component. It follows the workflow shown in the JCB tutorial video and reflects the current JCB v2.6.0 workflow.

---

## Overview

Validation rules ensure that field values meet certain conditions **before being saved** to the database. JCB supports Joomla's built-in validation system and allows developers to add **custom rules** using JFormRule classes.

In this guide, we will:

* Add a custom validation property to a field type.
* Create a custom validation rule file (`strlenTen`).
* Integrate the rule into the Hello World component.
* Test the rule and display custom validation messages.

---

## 1. Open the Admin View and Locate the Target Field

[00:00:32](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m32s)

1. Open **Joomla Component Builder (JCB)** and select your **Hello World** component.
2. Go to the **Admin Views** tab and open the **Greetings** view.
3. Locate the **Greetings** field (usually of type `Textarea`).
4. Check the field attributes - if the `validation` option is missing, it can be added manually in the Fieldtype configuration.

> 💡 *Tip: If your JCB version doesn't have the "validation" property available, you can edit the field type directly to add it.*

---

## 2. Add the Validation Attribute to a Field Type

[00:01:55](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m55s)

1. In JCB, go to **Fieldtypes** in the Admin View.
2. Select a **Fieldtype** to modify (e.g., `Textarea`).
3. Add a new attribute:

   * **Name:** `validate`
   * **Adjustable:** ✅ Yes
   * **Required:** ❌ No
   * **Translatable:** ❌ No
   * **Description:** *(A rule to validate this field before saving.)*
4. Save and close.

Now, when editing a field using this fieldtype, you'll see a **Validate** option available.

---

## 3. Set a Custom Validation Rule

[00:03:03](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m03s)

1. Go back to your **Admin View → Greetings**.

2. Edit the `Greeting` field.

3. In the **Validate** property, enter your custom rule name - for example:

   ```xml
   validate="strlenTen"
   ```

4. Save and close.

> JCB supports Joomla's built-in validation rules (like `email`, `url`, etc.), but custom rules can be defined as **form rules** by adding your own PHP class.

---

## 4. Create a Custom Validation Rule File

[00:04:14](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m14s)

1. In your local JCB installation, open the **Custom** folder:

   ```
   administrator/components/com_componentbuilder/custom/
   ```

2. Create a new PHP file named `strlenTen.php`.

3. Add the following rule code (from the tutorial):

   ```php
   <?php
   defined('_JEXEC') or die('Restricted access');

   class JFormRuleStrlenTen extends JFormRule
   {
       public function test(&$element, $value, $group = null, &$input = null, &$form = null)
       {
           return strlen($value) > 10;
       }
   }
   ```

4. Save the file.
   This file defines a simple rule that checks if the input string has **more than 10 characters**.

---

## 5. Register the Rule in JCB's Custom Files

[00:06:03](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m03s)

1. In JCB, open your **Hello World** component again.
2. Go to **Settings → Add Custom Files & Folders**.
3. Click **Create component files and folders for this Joomla Component**.
4. Locate your custom file (`strlenTen.php`) in the list.
5. Set its **Target Path** to:

   ```
   admin/models/rules/
   ```
6. Enable **Update this file** = **Yes**.
7. Save and close.

> JCB automatically handles file placement during compilation, using the `admin/models/rules` path for rule files.

---

## 6. Add License and Component Tags

[00:07:34](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m34s)

Add these placeholders to your rule file for automatic branding during compilation:

```php
###BOM###
/**
 * @license ###LICENSE###
 * @package ###component###
 */
```

* `###BOM###` - ensures the correct file header format.
* `###component###` - replaced with the actual component name.
* `###LICENSE###` - replaced with your component's license text.

---

## 7. Compile and Test the Rule

[00:08:54](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m54s)

1. Go to the **Compiler** in JCB and compile your component.
2. Install the generated package in Joomla.
3. Navigate to:

   ```
   administrator/components/com_hello_world/models/rules/
   ```

   You should now see your file `strlenten.php` (automatically lowercased).
4. Open the file - note that your license header and component tags have been applied.

### Test in the Admin View:

* Go to **Components → Hello World → Greetings → New**.
* Enter a short string (less than 10 characters).
* Click **Save** - you'll see:
  `Warning: Invalid Field: Greetings`

If this doesn't trigger:

* Ensure the validation name and filename are **all lowercase** (`strlenten`).

---

## 8. Add a Custom Validation Message

[00:12:33](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m33s)

You can show a custom error message instead of Joomla's default.

### Option A - Add Message Inside PHP Rule:

Edit `strlenten.php`:

```php
$element->addAttribute('message', 'Field must have more than 10 characters!');
return false;
```

### Option B - Add Message in XML Field Definition:

[00:13:45](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m45s)

1. In JCB, go to **Fieldtypes** → `Textarea`.
2. Add a new attribute:

   * **Name:** `message`
   * **Changeable:** ✅ Yes
   * **Translatable:** ✅ Yes
   * **Optional:** ✅ Yes
   * **Description:** *(Displayed when validation fails.)*
3. Save and close.
4. In your **Greetings** field XML, add:

   ```xml
   message="COM_HELLO_WORLD_GREETING_GREETING_MESSAGE"
   ```
5. Compile and reinstall your component.

> The XML method is preferable when you only need one translated error message.

---

## 9. Verify the Final Behavior

[00:15:00](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m00s)

1. Open **Greetings → New** in Joomla Admin.
2. Enter a short string and save - you should see your custom message:

   ```
   Warning: Field must have more than 10 characters!
   ```
3. Enter a valid string (>10 chars) and save - the record saves successfully.

---

## 10. Summary

[00:16:56](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m56s)

You have successfully:

* Added a new `validate` property to a field type.
* Created a **custom Joomla rule class** (`JFormRuleStrlenTen`).
* Registered it in JCB as a custom file.
* Compiled and tested it inside your component.
* Added a **custom translatable error message**.

---

### Best Practices

* Always name rule files in **lowercase**.
* Place all custom rule files in:

  ```
  administrator/components/com_componentbuilder/custom/
  ```
* Keep your JCB **custom file mapping updated** when file names change.
* Use XML-based messages for multilingual components.

---
