# Adding a Custom Time Field

*Using Joomla Component Builder (JCB)*

### Video Reference

[00:00:00](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(*Click on these time links to watch the YouTube tutorial.*)

---

## 1. Overview

In Joomla Component Builder, a **custom time field** allows you to capture specific time values (e.g., `05:15`) in your components. Because time is stored as an integer in databases, you cannot use a standalone time format - it must either be stored as part of a datetime or validated via text input.

This guide walks you through:

* Creating a **text field** for time entry
* Adding a **custom validation rule (Form Rule)**
* Implementing **server-side and JavaScript validation**
* Integrating **time fields in repeatable structures**

---

## 2. Setting Up a Time Field

[00:00:21](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h00m21s)

If you want users to enter a time such as `05:15`, you can:

1. Create a **text field** in JCB.
2. Validate it using a **regular expression (Regex)** to ensure proper time format.

> **Tip:** Regex can be applied via a **custom Joomla form rule**, ensuring server-side validation beyond JavaScript.

---

## 3. Creating a Custom Form Rule

[00:01:23](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h01m23s)

To validate the time format properly, you'll create a custom Joomla Form Rule.

### Steps:

1. Go to your **Joomla libraries** folder:
   `libraries/src/Form/Rule/`

2. Review existing rules (e.g., `EmailRule.php`, `UrlRule.php`) to understand their structure.
   [00:02:21](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h02m21s)

3. Create a new file, for example:
   `/libraries/src/Form/Rule/TimeRule.php`

4. Extend `Joomla\CMS\Form\FormRule`:

   ```php
   class JFormRuleTime extends FormRule
   {
       protected $regex = '^(?:[01]\d|2[0-3]):[0-5]\d$';
   }
   ```

   [00:02:43](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h02m43s)

5. In your **component's model XML** (e.g., `models/forms/item.xml`), add:

   ```xml
   <field name="event_time" type="text" label="Event Time" validate="time" filter="string" />
   ```

This connects your form field with your new validation rule.

---

## 4. Adding the Field in Component Builder

[00:04:15](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h04m15s)

Within **Component Builder**:

1. Navigate to **Fields → New**.
2. Choose **Type:** `text`.
3. Under **Validation**, enter the name of your custom rule (`time`).
4. Set **Filter** to `string`.

[00:04:44](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h04m44s)

This setup ensures that data is filtered and validated correctly on both the client and server.

---

## 5. Enhancing with JavaScript Validation

[00:05:00](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h05m00s)

To improve user experience, you can add JavaScript validation to the field to restrict invalid characters.

Example steps:

1. Add a **unique class or ID** to your field.
2. Include JavaScript in your **view's footer script area** (accessible in JCB's View Scripts section).
3. The script should allow only numbers and a colon (`:`).

[00:05:37](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h05m37s)

You can use the field's ID (e.g., from your browser's Inspector) to target it directly:

```js
document.getElementById('jform_event_time').addEventListener('input', function() {
  this.value = this.value.replace(/[^0-9:]/g, '');
});
```

If invalid data is entered, the input can be cleared, or a message can be shown.

---

## 6. Using Time-Date Field in Repeatable Fields

[00:06:46](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h06m46s)

When working with **repeatable fields**, standard calendar fields do not work directly because of how dynamic instances are handled.
To overcome this, JCB includes a **custom DateTime picker** integrated through JavaScript.

[00:08:08](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h08m08s)

### Key Steps:

1. Use a **custom JavaScript file** added in JCB's **Scripts** section.
2. Loop through each repeatable instance using JavaScript or PHP to attach the picker dynamically.
3. Example (simplified):

   ```js
   for (let i = 0; i < 50; i++) {
       let field = document.getElementById('time_field_' + i);
       if (field) {
           jQuery(field).datetimepicker({
               format: 'H:i',
               step: 15
           });
       }
   }
   ```

[00:09:52](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h09m52s)

---

## 7. Handling Multiple Time-Date Fields

[00:10:51](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h10m51s)

When your component includes several time fields (e.g., start, end, or target times), JCB allows you to manage them efficiently by:

* Defining an array of targeted field types.
* Using a PHP loop to initialize their date-time pickers dynamically, reducing redundant code.

[00:11:44](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h11m44s)

---

## 8. Community Documentation and Help Resources

[00:12:14](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h12m14s)

Joomla Component Builder provides built-in documentation links accessible via the **Help menu** in every list view.

You can access the official **Wiki** and contribute to improving the documentation:

* **URL:** [Readme Documentation](http://projects.vdm.io/projects/Joomla-component-builder/wiki)

If you wish to contribute or request help documentation for your component, contact the project maintainers.

[00:14:40](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h14m40s)

---

## 9. Summary

* Use **text fields** with custom **form rules** for time input.
* Implement **Regex-based validation** in PHP and **character restriction** in JavaScript.
* For **repeatable fields**, ensure dynamic initialization using JavaScript loops.
* Explore **Component Builder's script integration** for full control.
* Leverage the **JCB Wiki** for learning and contributing.

---
