# Dynamic Router Implementation Explained

**Video Reference:** [Dynamic Router Implementation Explained on YouTube](https://www.youtube.com/watch?v=hYycPLbaMos)
---

## Overview

In this tutorial, we explore JCB's **new dynamic router implementation**, a system enhancement designed to reduce complexity and improve how URLs are built for your Joomla site views. This update primarily addresses issues in the **router's parsing and building processes**, especially for components that use **Dynamic Gets** in their **Site Views**.

---

## 1. Understanding Router Complexity

**[00:00:00 → 00:00:49]**

When a Joomla Component Builder component includes **Site Views** (frontend views), those views typically use **Dynamic Gets** to fetch data.
The router then uses this data-combined with the view name-to construct **search engine friendly (SEF) URLs**.

For example:

```
index.php?option=com_sermondistributor&view=preacher&id=12
```

can become:

```
/sermondistributor/preacher/john-doe
```

JCB automatically generates a `router.php` file for each component, attempting to "guess" the relationships needed for URL parsing and building. While often correct, it can make incorrect assumptions when Dynamic Gets become complex.

---

## 2. The Router File and Its Methods

**[00:01:26 → 00:02:08]**

After compiling your component, navigate to:

```
/components/com_sermondistributor/router.php
```

This file contains two key methods inside a router class:

* `build($query)` - Converts URL parameters into SEF segments.
* `parse($segments)` - Interprets SEF segments back into query variables.

Inside `parse()`, a `switch` statement evaluates the first segment, usually representing the **view name**.

Example:

```php
switch ($segments[0]) {
    case 'preacher':
        $vars['view'] = 'preacher';
        break;
    case 'preachers':
        $vars['view'] = 'preachers';
        break;
}
```

---

## 3. Understanding Default Router Behavior

**[00:02:33 → 00:03:44]**

The **List View (`preachers`)** retrieves data directly from the database without requiring URL input.
Therefore, the router only needs:

```php
$vars['view'] = 'preachers';
```

The rest of the auto-generated code (for IDs, aliases, etc.) is redundant and can be safely removed.

However, for the **Single View (`preacher`)**, the router may misinterpret Dynamic Get relationships-for instance, incorrectly pulling data from the `sermon` table instead of the `preacher` table.

---

## 4. Identifying and Correcting Router Errors

**[00:04:09 → 00:06:25]**

In the `preacher` model's query, JCB mistakenly builds logic referencing the `sermon` table when it should reference the `preacher` table.
The fix involves modifying what value the router checks during parsing:

**Incorrect:**

```php
$getVar('sermon', $id);
```

**Correct:**

```php
$getVar('preacher', $id);
```

You can verify what `getVar()` does at the bottom of `router.php` - it's responsible for retrieving and validating URL values dynamically.

The same adjustment applies to other misidentified site views like **Categories** and **Series**.

---

## 5. Implementing Fixes via Dynamic Gets

**[00:07:14 → 00:08:48]**

Rather than editing router code manually, JCB now allows you to dynamically inject fixes directly from the **Dynamic Get interface**.

### Steps:

1. Open **Dynamic Gets** in JCB.
2. Select the related **Site View** (e.g., `Preacher`, `Series`, `Category`).
3. Under each, locate the **Custom Script tab**.
4. Enable **"Add PHP (parse Method) in Router"**.
5. Adjust placeholders as needed.

This feature allows you to override and target specific views without rewriting the entire router.

---

## 6. Working with Custom Placeholders

**[00:10:06 → 00:11:32]**

When enabling the "Add PHP (parse Method)" option, JCB injects a default snippet that includes **placeholders**:

Example:

```php
case '[sview]':
    $vars['view'] = '[sview]';
    $vars['id']   = $this->getVar('[sview]', $segments[1]);
    break;
```

* `[sview]` automatically resolves to the **Site View name**.
* This makes the router dynamic across multiple Site Views.
* If the URL includes multiple variables, placeholders can handle them all dynamically.

**Tip:** Always ensure that your `[sview]` value matches your actual Site View name to prevent mismatched routing.

---

## 7. Adjusting Specific Site Views

**[00:11:56 → 00:13:59]**

You'll need to apply this custom router logic for the following Site Views:

* **Sermon (Series ID)** - Correct "sermon" → "series".
* **Sermon (Preacher ID)** - Ensure both values match (`preacher`).
* **Category** - Add `true` to the `getVar` call to identify it as a category lookup.

Example for Category:

```php
$vars['id'] = $this->getVar('category', $segments[1], true);
```

This ensures that JCB checks the `#__categories` table correctly instead of the main data table.

---

## 8. Compiling and Verifying the Changes

**[00:14:21 → 00:14:49]**

After saving and closing your Dynamic Get changes:

1. Recompile your component in JCB.
2. Install or update it on your Joomla site.
3. Reopen `router.php` to verify the modifications:

   ```php
   case 'preacher':
       $vars['id'] = $this->getVar('preacher', $segments[1]);
       break;
   case 'category':
       $vars['id'] = $this->getVar('category', $segments[1], true);
       break;
   case 'series':
       $vars['id'] = $this->getVar('series', $segments[1]);
       break;
   ```

If the code matches your intended logic, your router is now correctly handling SEF URLs.

---

## 9. Future Improvements and Collaboration

**[00:15:16 → End]**

This implementation represents the **first phase** of JCB's router improvements.
Future updates aim to make the dynamic guessing logic more intelligent.

Developers are encouraged to contribute via JCB's **GitHub repository** to refine these routing methods.

---

## Summary

| Problem                             | Cause                                       | Solution                                         |
| ----------------------------------- | ------------------------------------------- | ------------------------------------------------ |
| Incorrect router variable mapping   | JCB guessed wrong Dynamic Get relationships | Override with Custom Parse Method in Dynamic Get |
| Redundant router code in list views | Generated defaults not needed               | Remove redundant `id` logic                      |
| Category view not recognized        | Router didn't detect category context       | Use `getVar('category', $id, true)`              |
| Inconsistent SEF URL generation     | Placeholder mismatch                        | Use `[sview]` placeholders for consistency       |

---

## Final Notes

* Use **Dynamic Get → Custom Script → Add PHP (parse Method)** to fix routers dynamically.
* Avoid editing `router.php` manually unless necessary.
* Always recompile and reinstall to apply changes.
* Stay updated with new JCB releases for smarter routing logic.

---
