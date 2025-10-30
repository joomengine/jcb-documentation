# Adding Language Strings and Dynamic Placeholders in JCB

## Overview

[00:00:00](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

This guide explains how to **add a language string** to your component in Joomla Component Builder (JCB) and how to generate a **language placeholder** for **dynamic use** — particularly useful when working within classes or arrays where the direct `JText` call cannot be used.

---

## Understanding Language Strings in JCB

When developing Joomla components, you often use the `JText` function to translate strings dynamically. Normally, when JCB compiles your component:

* The string inside `JText` is added to your language file.
* The placeholder replaces the string in the compiled code.
* The Joomla system translates that placeholder whenever it's displayed.

Example:

```php
echo JText::_('COM_MYCOMPONENT_HELLO_WORLD');
```

During compilation, JCB automatically ensures that `COM_MYCOMPONENT_HELLO_WORLD` is written into the component's language file with its translation text.

---

## When You Need Only the Placeholder

[00:00:59](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m59s)

Sometimes, you may need **only the language placeholder**, not the full translation at compile-time — for instance, when working inside a **class array**.

Example scenario:
You have a class with an array of field properties (like `listclass`, `escape`, `display`, or `validate`) and you want to reference the translated string later in runtime, not immediately when JCB compiles it.

In such cases, you can't directly use `JText` inside the array, because that would attempt to translate immediately. You need only the **placeholder string** to exist in the compiled code, ready for later translation.

---

## Using the `JustTEXT` Feature

[00:01:32](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m32s)

To handle this use case, JCB introduces a special keyword:

### `JustTEXT`

This feature:

* Adds the string to your language file (as JCB normally does).
* Inserts **only the placeholder** (not the translation) into your PHP script.
* Allows you to translate it **later in the code** when you decide to call `JText` on it.

This is especially useful for dynamic translation workflows or when looping through arrays where translation occurs after certain conditions are met.

---

## How JCB Compiles It

[00:02:16](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m16s)

`JustTEXT` looks similar to a class or function call, but it's not actually a PHP class or function.
It's a **marker** recognized by the JCB compiler, which processes it during compilation and replaces it appropriately.

For example:

```php
JustTEXT::_('COM_MYCOMPONENT_VALIDATION_ERROR');
```

After compilation, JCB outputs:

```php
'COM_MYCOMPONENT_VALIDATION_ERROR'
```

This means the placeholder string is inserted, not translated yet. You can later use it like:

```php
JText::_($value);
```

— where `$value` was the placeholder created by `JustTEXT`.

---

## Applying It in Your Class Arrays

[00:02:49](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m49s)

Consider this common example within a class that defines field properties:

```php
$extra_field_properties = array(
    'listclass' => JustTEXT::_('COM_MYCOMPONENT_FIELD_LISTCLASS_DESC'),
    'escape'    => JustTEXT::_('COM_MYCOMPONENT_FIELD_ESCAPE_DESC'),
    'display'   => JustTEXT::_('COM_MYCOMPONENT_FIELD_DISPLAY_DESC'),
    'validate'  => JustTEXT::_('COM_MYCOMPONENT_FIELD_VALIDATE_DESC')
);
```

After compilation, this becomes:

```php
$extra_field_properties = array(
    'listclass' => 'COM_MYCOMPONENT_FIELD_LISTCLASS_DESC',
    'escape'    => 'COM_MYCOMPONENT_FIELD_ESCAPE_DESC',
    'display'   => 'COM_MYCOMPONENT_FIELD_DISPLAY_DESC',
    'validate'  => 'COM_MYCOMPONENT_FIELD_VALIDATE_DESC'
);
```

Later in your logic, when looping through this array, you can translate the values dynamically:

```php
foreach ($extra_field_properties as $key => $description) {
    echo JText::_($description);
}
```

This gives you clean, flexible translation handling while keeping placeholders intact until needed.

---

## Compilation Result Example

[00:03:11](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m11s)

When JCB compiles, you'll notice:

* The `JustTEXT` entries are converted to plain string placeholders.
* The strings are still included in your language `.ini` file.
* You can use those placeholders later anywhere within your component.

Example snippet before and after compilation:

**Before Compilation:**

```php
'display' => JustTEXT::_('COM_MYCOMPONENT_FIELD_DISPLAY_DESC'),
```

**After Compilation:**

```php
'display' => 'COM_MYCOMPONENT_FIELD_DISPLAY_DESC',
```

These placeholders remain available for later use with `JText::_()`.

---

## Summary

[00:04:09](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m09s)

To summarize:

* Use `JText::_()` normally when you want **immediate translation**.
* Use `JustTEXT::_()` when you want **only the placeholder** added, and the **translation deferred**.
* Both methods ensure your strings are safely written to the language file.
* `JustTEXT` gives you more control when handling **arrays**, **dynamic content**, or **class-based logic** that processes strings later.

---

### Pro Tip

If you have logic where language strings are used conditionally (for example, inside loops, arrays, or custom functions), `JustTEXT` keeps your code flexible and your translations organized — without forcing early interpretation during compilation.

---
