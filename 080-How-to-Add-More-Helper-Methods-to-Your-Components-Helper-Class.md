# How to Add More Helper Methods to Your Component's Helper Class

Learn how to add and manage helper methods in your Joomla Component Builder (JCB) component helper class - both for the **admin** and **site** areas. This guide also covers how to include custom helper classes and trigger them globally using JCB's event system.

---

## Overview

Helper classes in Joomla Component Builder allow you to store reusable PHP methods that can be accessed throughout your component - in both **admin** and **frontend (site)** contexts.
This tutorial demonstrates how to:

* Add helper methods directly within JCB.
* Differentiate between admin, site, and shared ("both") helper functions.
* Call helper methods in your component's code.
* Include and register custom helper files.
* Use **global events** to trigger helper logic automatically.

---

## 1. Accessing the Helper Class Interface

**Timestamp:** [00:00:14](https://www.youtube.com/watch?v=VpSXsxZuhmM&t=00h00m14s)

1. Open your **component** in Joomla Component Builder.
2. Navigate to the **"Libs & Helpers"** tab.

   * Here you'll find multiple target areas for helper methods:

     * **Site Helper** - frontend-only logic.
     * **Admin Helper** - backend-only logic.
     * **Both** - shared methods available to both frontend and backend.

> **Tip:** Use "Both" when you want the same helper available everywhere. This is ideal for general-purpose utilities (e.g., formatting dates, validation).

---

## 2. Adding Helper Methods

**Timestamp:** [00:00:44 – 00:01:43](https://www.youtube.com/watch?v=VpSXsxZuhmM&t=00h00m44s)

To add a new helper method:

1. In the **Site Helper** section, click **Add Method**.
   Example:

   ```php
   public static function fancyDate($date)
   {
       // Example site-only method
       return date('F j, Y', strtotime($date));
   }
   ```

   This creates a method called `fancyDate` available to the **frontend** only.

2. In the **Admin Helper**, you could add something like:

   ```php
   public static function showAdminMessage()
   {
       return 'This is admin only';
   }
   ```

3. In the **Both** section:

   ```php
   public static function sharedMethod()
   {
       return 'This method is available in both admin and site areas.';
   }
   ```

> **Compile your component** after adding the helper methods to ensure they are written into the generated helper class files.

---

## 3. Verifying Generated Helper Methods

**Timestamp:** [00:02:10 – 00:03:01](https://www.youtube.com/watch?v=VpSXsxZuhmM&t=00h02m10s)

Once you compile and install the component:

* In the **admin area**:
  Navigate to
  `administrator/components/com_demo/helpers/demo.php`
  You'll see your `showAdminMessage()` and `sharedMethod()` functions inside.

* In the **frontend (site) area**:
  Go to
  `components/com_demo/helpers/demo.php`
  You'll find `fancyDate()` and `sharedMethod()` functions.

> Methods under **"Both"** appear in **both helper files**, ensuring shared logic across admin and site environments.

---

## 4. Calling Helper Methods in Your Code

**Timestamp:** [00:03:40 – 00:04:28](https://www.youtube.com/watch?v=VpSXsxZuhmM&t=00h03m40s)

Helper methods can be called using Joomla's registered helper class.

Example - calling the `fancyDate()` method in your site view:

```php
use Joomla\CMS\Factory;

// Call helper method
$dateFormatted = DemoHelper::fancyDate($item->created);
```

This example formats a date value using the `fancyDate()` method defined earlier.

> Helper classes are automatically registered by JCB during component generation - no manual inclusion is needed for these built-in helpers.

---

## 5. Adding a Custom Helper Class File

**Timestamp:** [00:05:06 – 00:06:01](https://www.youtube.com/watch?v=VpSXsxZuhmM&t=00h05m06s)

If you prefer to add an **entirely new helper file** (not managed by JCB):

1. Use JCB's **File and Folder Inclusion** system.

   * You can choose **basic** or **advanced** inclusion depending on the file location.
   * Define the correct path relative to the ZIP output.

2. Add your PHP helper file manually.
   Example:
   `administrator/components/com_demo/helpers/own.php`

3. Inside, define your helper class:

   ```php
   class OwnHelper
   {
       public static function doSomething()
       {
           return 'Custom helper logic here.';
       }
   }
   ```

---

## 6. Using Global Events to Load Helpers Automatically

**Timestamp:** [00:06:01 – 00:09:26](https://www.youtube.com/watch?v=VpSXsxZuhmM&t=00h06m01s)

You can automatically trigger events every time a helper class is loaded using **Global Events** in JCB.

### Steps:

1. In your JCB component settings, open **Component → Helper → Global Event (Admin)**.
   Add a snippet like:

   ```php
   $this->triggerEvent('onDemoAdminHelperLoad', array('document' => $document));
   ```

   This runs every time the **admin helper** is loaded.

2. After compiling, check your generated helper file:

   * The global event will appear as a snippet in the admin helper class.
   * The document object (`$document`) is passed, allowing you to manipulate page output or scripts globally.

3. To register your **custom helper class**, extend the event:

   ```php
   require_once JPATH_COMPONENT_ADMINISTRATOR . '/helpers/own.php';
   $this->triggerEvent('onDemoAdminHelperLoad', array(new OwnHelper));
   ```

Now your custom helper methods are available automatically whenever the helper class loads.

---

## 7. Extending to the Site (Frontend)

**Timestamp:** [00:09:57 – 00:10:32](https://www.youtube.com/watch?v=VpSXsxZuhmM&t=00h09m57s)

You can replicate the same process for the **site helper**:

1. Use the **Global Event (Site)** in JCB.
2. Move your custom helper file to the frontend helper folder:
   `components/com_demo/helpers/own.php`
3. Include it with:

   ```php
   require_once JPATH_COMPONENT_SITE . '/helpers/own.php';
   ```

Now your frontend helper file will also load automatically whenever the component executes.

---

## 8. When to Use Global Events

**Timestamp:** [00:11:02 – 00:11:33](https://www.youtube.com/watch?v=VpSXsxZuhmM&t=00h11m02s)

Global events are best suited for:

* Modifying the Joomla **Document Object** before a page loads.
* Including additional scripts or CSS dynamically.
* Running setup code across all views.

However, for simple helper methods, it's usually better to add them directly to the main helper class (admin/site/both) instead of using an external file and global event.

> **Best Practice:**
> Keep helper logic centralized in the component's own helper file unless there's a strong reason to modularize with global events.

---

## Summary

| Task                   | Location in JCB                  | Purpose                            |
| ---------------------- | -------------------------------- | ---------------------------------- |
| Add helper methods     | Libs & Helpers → Admin/Site/Both | Define reusable PHP functions      |
| Call helper methods    | In views/models                  | Execute logic from helper class    |
| Add custom helper file | File & Folder Inclusion          | Include standalone helper classes  |
| Use global events      | Component → Helper               | Trigger helper logic automatically |

---

## Final Notes

Adding helper methods is a fundamental technique in Joomla Component Builder development. It enables you to centralize functionality, reuse logic efficiently, and maintain cleaner component code.

Experiment with both built-in helper areas and global events to determine the structure that best fits your project.
